# Kubernetes WebUI Deployment

Authenticates the kubernetes webui with keycloak.

The dashboard itself is declared in puppet [here](https://github.com/ocf/puppet/blob/master/modules/ocf_kubernetes/files/kubernetes_admin_webui).
This repository only contains the keycloak reverse proxy to the webui service.
The upstream url is set as kubernetes-dashboard.kube-system.svc.cluster.local,
which resolves to the kubernetes-dashboard service in the kube-system
namespace. Authentication is handled by passing in a token in the
Authentication header, which has read/write rights to the repository for the
admin case, and just read rights for the non-admin case.
