# Github Action Minikube

Downloads and set up Minikube cluster and kubectl binary for Github Actions.

## Example 

```yaml
name: Minikube workflow
on: push
jobs:
  minikube:
    name: Start Kubernetes cluster on Minikube
    runs-on: ubuntu-20.04
    steps:
      - name: Start Minikube
        id: minikube
        uses: hiberbee/github-action-minikube@master
        with:
          kubernetes-version: 1.18.3
          network-plugin: cni
          addons: metrics-server,registry,ingress,dashboard
          nodes: 1
          cpus: 2
      - name: Cluster status
        run: minikube status
      - name: Cluster information
        run: kubectl cluster-info
      - name: Kubernetes service
        run: kubectl get services --all-namespaces

```
