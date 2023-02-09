# MLOps Demo: Tenant GitOps

The primary goal of this repo is to create the tenant environment. A tenant is generally a team of application developers that require several namespaces for deploying and managing an application.

This repo creates an opinionated way for deploying and managing resources for a multi-tiered deployment of application components.

This repo is designed to be used alongside the [openshift-cluster-bootstrap-gitops](https://github.com/rh-intelligent-application-practice/openshift-cluster-bootstrap-gitops) repo. Like the openshift-cluster-bootstrap-gitops repo this repo is intended to deploy cluster level configurations but instead focuses on components that are specific to the MLOps Demo that are generally in the scope of a Cluster Admin.

## Prerequisites

### Client Tooling

The bootstrap script relies on the following command line tools. If they're not already available on your system path, the bootstrap script will attempt to download them from the internet, and will place then in a `.\tmp` folder location where the bootstrap script was run:

- [oc](https://docs.openshift.com/container-platform/4.11/cli_reference/openshift_cli/getting-started-cli.html) - the OpenShift command-line interface (CLI) that allows for creation of applications, and can manage OpenShift Container Platform projects from a terminal.

- [kustomize](https://kubectl.docs.kubernetes.io/installation/kustomize/) - a Kubernetes configuration transformation tool that enables you to customize un-templated YAML files, leaving the original files untouched.

### Access to an OpenShift Cluster

Before running the bootstrap script, ensure that you have login access to your OpenShift cluster. This OpenShift cluster may have been provisioned though [RHDS](https://demo.redhat.com), or it may also be your own custom built cluster running on dedicated hardware.

Make sure you are [logged into your cluster](https://docs.openshift.com/online/pro/cli_reference/get_started_cli.html) using the `oc login ...` command.  You can obtain a login token if required by utilizing the "Copy Login Command" found under your user profile in the OpenShift Web Console.

The scripts require a user with sufficient permissions for installing and configuring operators, typically the `opentlc-mgr` user account on a Red Hat Demo System hosted cluster.

## Running the Cluster Bootstrap

Execute the bootstrap script to begin the installation process:

```sh
./scripts/bootstrap.sh
```

Additional ArgoCD Application objects will be created and synced in OpenShift GitOps. You can follow the progress of the sync using the ArgoCD URL that the script will provide. This sync operation should complete in a few seconds.