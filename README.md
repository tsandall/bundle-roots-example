This repository shows how to configure OPA to downlaod two
bundles. The bundles include manifests that declare their roots. The
following command starts OPA in server mode, declares a service to be
running on localhost:8000, and declares two bundles to be downloaded
from the service (rbac and example).

```bash
opa run --server \
	--set services.test.url=http://localhost:8000 \
 	--set bundles.rbac.service=test \
 	--set bundles.rbac.resource=rbac.tar.gz \
	--set bundles.example.service=test \
	--set bundles.example.resource=example.tar.gz
```

Inside another terminal start an HTTP server that serves this
directory. For example, using Python 2.7:

```
python2.7 -m SimpleHTTPServer 8000
```

The bundle files were created with the `tar` command:

```
tar czvf example.tar.gz -C example .
tar czvf rbac.tar.gz -C rbac .
```