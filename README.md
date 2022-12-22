
```bash
cat <<EOF | kubectl apply -f -
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: acw-storage
  namespace: argocd
spec:
  project: default
  source:
    repoURL: $HTTPS_REPO_URL
    targetRevision: main
    path: .
  destination:
    server: https://kubernetes.default.svc
    namespace: default
  syncPolicy:
    automated: {}
EOF
```