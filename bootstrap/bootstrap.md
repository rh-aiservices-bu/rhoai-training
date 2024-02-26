```bash
# oc apply -f ./bootstrap/applicationset/applicationset-bootstrap.yaml

oc -n openshift-gitops get applicationset bootstrap

oc -n openshift-gitops get routes

# get the password for gitops:
oc -n openshift-gitops get secret openshift-gitops-cluster \
    -o jsonpath='{.data.admin\.password}' \
    | base64 --decode

oc  -n openshift-gitops  patch applicationset/bootstrap \
    --type merge \
    -p '{"spec":{"generators":[{"list":{"elements":[{"cluster":"in-cluster","name":"ic-test-app","path":"bootstrap/ic-test-app","repoURL":"https://github.com/rh-aiservices-bu/rhoai-training.git","targetRevision":"main","url":"https://kubernetes.default.svc"},{"cluster":"in-cluster","name":"rhoai-config","path":"bootstrap/rhoai-config","repoURL":"https://github.com/rh-aiservices-bu/rhoai-training.git","targetRevision":"main","url":"https://kubernetes.default.svc"}]}}]}}'

# oc  -n openshift-gitops  patch applicationset/bootstrap \
#     --type merge \
#     -p '{"spec":{"generators":[{"list":{"elements":[{"cluster":"in-cluster","name":"ic-test-app","path":"bootstrap/ic-test-app","repoURL":"https://github.com/rh-aiservices-bu/rhoai-training.git","targetRevision":"main","url":"https://kubernetes.default.svc"}]}}]}}'



```
