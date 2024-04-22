# RootDB - using podman play

This repo contains a kubernetes manifest for a pod running [RootDB](https://www.rootdb.fr/) using [podman play kube](https://docs.podman.io/en/latest/markdown/podman-kube-play.1.html).

It is 100% based on the [RootDB-Infra](https://github.com/RootDBApp/infra) repository.


## Start 

```
podman play kube --start  podman-kube.yaml
```

Once started you can access RootDB on [http://localhost:8091/](http://localhost:8091/)

## Shutdown

```
podman play kube --down  podman-kube.yaml
```

## Known/Common errors

### A new session cookie is set on every request

A new session cookie is set on every request. The result is that after a couple of page loades nginx will respond with a "400 Bad Request - Request Header Or Cookie Too Large" error.

Setting `SESSION_DRIVER` to `file` is a work around, however this fills up the filesystem with session files.

