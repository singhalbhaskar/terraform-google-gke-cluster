# terraform-google-gke-cluster

## Description
### Tagline
This is an auto-generated module.

### Detailed
This module was generated from [terraform-google-module-template](https://github.com/terraform-google-modules/terraform-google-module-template/), which by default generates a module that simply creates a GCS bucket. As the module develops, this README should be updated.

The resources/services/activations/deletions that this module will create/trigger are:

- Create a GCS bucket with the provided name

### PreDeploy
To deploy this blueprint you must have an active billing account and billing permissions.

## Architecture
![alt text for diagram](https://www.link-to-architecture-diagram.com)
1. Architecture description step no. 1
2. Architecture description step no. 2
3. Architecture description step no. N

## Documentation
- [Hosting a Static Website](https://cloud.google.com/storage/docs/hosting-static-website)

## Deployment Duration
Configuration: X mins
Deployment: Y mins

## Cost
[Blueprint cost details](https://cloud.google.com/products/calculator?id=02fb0c45-cc29-4567-8cc6-f72ac9024add)

## Usage

Basic usage of this module is as follows:

```hcl
module "gke_cluster" {
  source  = "terraform-google-modules/gke-cluster/google"
  version = "~> 0.1"

  project_id  = "<PROJECT ID>"
  bucket_name = "gcs-test-bucket"
}
```

Functional examples are included in the
[examples](./examples/) directory.

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| additional\_networks | Additional network interface details for GKE, if any. Providing additional networks enables multi networking and creates relevat network objects on the cluster. | <pre>list(object({<br>    network            = string<br>    subnetwork         = string<br>    subnetwork_project = string<br>    network_ip         = string<br>    nic_type           = string<br>    stack_type         = string<br>    queue_count        = number<br>    access_config = list(object({<br>      nat_ip       = string<br>      network_tier = string<br>    }))<br>    ipv6_access_config = list(object({<br>      network_tier = string<br>    }))<br>    alias_ip_range = list(object({<br>      ip_cidr_range         = string<br>      subnetwork_range_name = string<br>    }))<br>  }))</pre> | `[]` | no |
| authenticator\_security\_group | The name of the RBAC security group for use with Google security groups in Kubernetes RBAC. Group name must be in format gke-security-groups@yourdomain.com | `string` | `null` | no |
| autoscaling\_profile | (Beta) Optimize for utilization or availability when deciding to remove nodes. Can be BALANCED or OPTIMIZE\_UTILIZATION. | `string` | `"OPTIMIZE_UTILIZATION"` | no |
| configure\_workload\_identity\_sa | When true, a kubernetes service account will be created and bound using workload identity to the service account used to create the cluster. | `bool` | `false` | no |
| deployment\_name | Name of the HPC deployment. Used in the GKE cluster name by default and can be configured with `prefix_with_deployment_name`. | `string` | n/a | yes |
| enable\_dataplane\_v2 | Enables [Dataplane v2](https://cloud.google.com/kubernetes-engine/docs/concepts/dataplane-v2). This setting is immutable on clusters. If null, will default to false unless using multi-networking, in which case it will default to true | `bool` | `null` | no |
| enable\_filestore\_csi | The status of the Filestore Container Storage Interface (CSI) driver addon, which allows the usage of filestore instance as volumes. | `bool` | `false` | no |
| enable\_gcsfuse\_csi | The status of the GCSFuse Filestore Container Storage Interface (CSI) driver addon, which allows the usage of a gcs bucket as volumes. | `bool` | `false` | no |
| enable\_master\_global\_access | Whether the cluster master is accessible globally (from any region) or only within the same region as the private endpoint. | `bool` | `false` | no |
| enable\_multi\_networking | Enables [multi networking](https://cloud.google.com/kubernetes-engine/docs/how-to/setup-multinetwork-support-for-pods#create-a-gke-cluster) (Requires GKE Enterprise). This setting is immutable on clusters and enables [Dataplane V2](https://cloud.google.com/kubernetes-engine/docs/concepts/dataplane-v2?hl=en). If null, will determine state based on if additional\_networks are passed in. | `bool` | `null` | no |
| enable\_parallelstore\_csi | The status of the Google Compute Engine Parallelstore Container Storage Interface (CSI) driver addon, which allows the usage of a parallelstore as volumes. | `bool` | `false` | no |
| enable\_persistent\_disk\_csi | The status of the Google Compute Engine Persistent Disk Container Storage Interface (CSI) driver addon, which allows the usage of a PD as volumes. | `bool` | `true` | no |
| enable\_private\_endpoint | (Beta) Whether the master's internal IP address is used as the cluster endpoint. | `bool` | `true` | no |
| enable\_private\_ipv6\_google\_access | The private IPv6 google access type for the VMs in this subnet. | `bool` | `true` | no |
| enable\_private\_nodes | (Beta) Whether nodes have internal IP addresses only. | `bool` | `true` | no |
| gcp\_public\_cidrs\_access\_enabled | Whether the cluster master is accessible via all the Google Compute Engine Public IPs. To view this list of IP addresses look here https://cloud.google.com/compute/docs/faq#find_ip_range | `bool` | `false` | no |
| labels | GCE resource labels to be applied to resources. Key-value pairs. | `map(string)` | n/a | yes |
| maintenance\_exclusions | List of maintenance exclusions. A cluster can have up to three. | <pre>list(object({<br>    name            = string<br>    start_time      = string<br>    end_time        = string<br>    exclusion_scope = string<br>  }))</pre> | `[]` | no |
| maintenance\_start\_time | Start time for daily maintenance operations. Specified in GMT with `HH:MM` format. | `string` | `"09:00"` | no |
| master\_authorized\_networks | External network that can access Kubernetes master through HTTPS. Must be specified in CIDR notation. | <pre>list(object({<br>    cidr_block   = string<br>    display_name = string<br>  }))</pre> | `[]` | no |
| master\_ipv4\_cidr\_block | (Beta) The IP range in CIDR notation to use for the hosted master network. | `string` | `"172.16.0.32/28"` | no |
| min\_master\_version | The minimum version of the master. If unset, the cluster's version will be set by GKE to the version of the most recent official release. | `string` | `null` | no |
| name\_suffix | Custom cluster name postpended to the `deployment_name`. See `prefix_with_deployment_name`. | `string` | `""` | no |
| network\_id | The ID of the GCE VPC network to host the cluster given in the format: `projects/<project_id>/global/networks/<network_name>`. | `string` | n/a | yes |
| pods\_ip\_range\_name | The name of the secondary subnet ip range to use for pods. | `string` | `"pods"` | no |
| prefix\_with\_deployment\_name | If true, cluster name will be prefixed by `deployment_name` (ex: <deployment\_name>-<name\_suffix>). | `bool` | `true` | no |
| project\_id | The project ID to host the cluster in. | `string` | n/a | yes |
| region | The region to host the cluster in. | `string` | n/a | yes |
| release\_channel | The release channel of this cluster. Accepted values are `UNSPECIFIED`, `RAPID`, `REGULAR` and `STABLE`. | `string` | `"UNSPECIFIED"` | no |
| service\_account | DEPRECATED: use service\_account\_email and scopes. | <pre>object({<br>    email  = string,<br>    scopes = set(string)<br>  })</pre> | `null` | no |
| service\_account\_email | Service account e-mail address to use with the system node pool | `string` | `null` | no |
| service\_account\_scopes | Scopes to to use with the system node pool. | `set(string)` | <pre>[<br>  "https://www.googleapis.com/auth/cloud-platform"<br>]</pre> | no |
| services\_ip\_range\_name | The name of the secondary subnet range to use for services. | `string` | `"services"` | no |
| subnetwork\_self\_link | The self link of the subnetwork to host the cluster in. | `string` | n/a | yes |
| system\_node\_pool\_enable\_secure\_boot | Enable secure boot for the nodes.  Keep enabled unless custom kernel modules need to be loaded. See [here](https://cloud.google.com/compute/shielded-vm/docs/shielded-vm#secure-boot) for more info. | `bool` | `true` | no |
| system\_node\_pool\_enabled | Create a system node pool. | `bool` | `true` | no |
| system\_node\_pool\_image\_type | The default image type used by NAP once a new node pool is being created. Use either COS\_CONTAINERD or UBUNTU\_CONTAINERD. | `string` | `"COS_CONTAINERD"` | no |
| system\_node\_pool\_kubernetes\_labels | Kubernetes labels to be applied to each node in the node group. Key-value pairs. <br>(The `kubernetes.io/` and `k8s.io/` prefixes are reserved by Kubernetes Core components and cannot be specified) | `map(string)` | `null` | no |
| system\_node\_pool\_machine\_type | Machine type for the system node pool. | `string` | `"e2-standard-4"` | no |
| system\_node\_pool\_name | Name of the system node pool. | `string` | `"system"` | no |
| system\_node\_pool\_node\_count | The total min and max nodes to be maintained in the system node pool. | <pre>object({<br>    total_min_nodes = number<br>    total_max_nodes = number<br>  })</pre> | <pre>{<br>  "total_max_nodes": 10,<br>  "total_min_nodes": 2<br>}</pre> | no |
| system\_node\_pool\_taints | Taints to be applied to the system node pool. | <pre>list(object({<br>    key    = string<br>    value  = any<br>    effect = string<br>  }))</pre> | <pre>[<br>  {<br>    "effect": "NO_SCHEDULE",<br>    "key": "components.gke.io/gke-managed-components",<br>    "value": true<br>  }<br>]</pre> | no |
| timeout\_create | Timeout for creating a node pool | `string` | `null` | no |
| timeout\_update | Timeout for updating a node pool | `string` | `null` | no |

## Outputs

| Name | Description |
|------|-------------|
| cluster\_id | An identifier for the resource with format projects/{{project\_id}}/locations/{{region}}/clusters/{{name}}. |
| gke\_ca\_cert | GKe cluster's ca cert. |
| gke\_cluster\_exists | A static flag that signals to downstream modules that a cluster has been created. Needed by community/modules/scripts/kubernetes-operations. |
| gke\_endpoint | GKe cluster's endpoint. |
| gke\_version | GKE cluster's version. |
| instructions | Instructions on how to connect to the created cluster. |
| k8s\_service\_account\_name | Name of k8s service account. |

<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->

## Requirements

These sections describe requirements for using this module.

### Software

The following dependencies must be available:

- [Terraform][terraform] v0.13
- [Terraform Provider for GCP][terraform-provider-gcp] plugin v3.0

### Service Account

A service account with the following roles must be used to provision
the resources of this module:

- Storage Admin: `roles/storage.admin`

The [Project Factory module][project-factory-module] and the
[IAM module][iam-module] may be used in combination to provision a
service account with the necessary roles applied.

### APIs

A project with the following APIs enabled must be used to host the
resources of this module:

- Google Cloud Storage JSON API: `storage-api.googleapis.com`

The [Project Factory module][project-factory-module] can be used to
provision a project with the necessary APIs enabled.

## Contributing

Refer to the [contribution guidelines](./CONTRIBUTING.md) for
information on contributing to this module.

[iam-module]: https://registry.terraform.io/modules/terraform-google-modules/iam/google
[project-factory-module]: https://registry.terraform.io/modules/terraform-google-modules/project-factory/google
[terraform-provider-gcp]: https://www.terraform.io/docs/providers/google/index.html
[terraform]: https://www.terraform.io/downloads.html

## Security Disclosures

Please see our [security disclosure process](./SECURITY.md).
