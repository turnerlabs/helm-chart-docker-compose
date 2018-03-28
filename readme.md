### helm-chart-docker-compose

A Helm chart that deploys a web app defined in docker-compose.yml to Kubernetes.

Note that this is an experimental proof of concept.


### example usage

```yaml
version: "2"
services:
  my-web-app:
    image: gcr.io/google_containers/echoserver:1.8
    ports:
    - 80:8080
    environment:
      MY_ENVVAR: foo
    labels:
      helm.docker-compose.healthcheck: /health
      helm.docker-compose.replicas: 2
      helm.docker-compose.imagePullSecret: my-pull-secret
      helm.docker-compose.tlsSecret: my-tls-secret
```

```
helm repo add turner http://dev.helm.turnerlabs.io
helm install turner/docker-compose -f docker-compose.yml --name my-web-app
```
