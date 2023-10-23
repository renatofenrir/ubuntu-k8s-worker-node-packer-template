# ubuntu-k8s-worker-node-packer-template

Use this template to provision a Kubernetes worker node already shipped with the following dependencies:

- Docker (docker-ce="5:19.03.6~3-0~ubuntu-bionic" - by the time I came up with this template, it was the best build, feel free to PR)
- Cloud-init (latest release)


It also comes with a .gitlab-ci.yml pipeline definition file, so that you can build this template straight from a
gitlab runner. (Please note that you must install the Packer binary on the gitlab runner for this to work)

Additional notes:

Since this setup relies on the 'proxmox' builder to create templates, you will need to add this plugin to your setup, ideally
before starting the build process:

```
packer plugins install github.com/hashicorp/proxmox
```

More info: https://developer.hashicorp.com/packer/integrations/hashicorp/proxmox

Tested with packer version 1.9.4

On the scripts/install-deps.sh bash script, make sure to ADD YOUR OWN PUBLIC KEYS so that you can ssh into the VMs that are gonna
be cloned from this template without any issues in the future.
