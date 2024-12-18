---
page_title: "cloudflare_infrastructure_access_target Resource - Cloudflare"
subcategory: ""
description: |-
  The Infrastructure Access Target https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/use-cases/ssh/ssh-infrastructure-access/#4-add-a-target resource allows you to configure Infrastructure Access Targets for an account.
---

# cloudflare_infrastructure_access_target (Resource)

The [Infrastructure Access Target](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/use-cases/ssh/ssh-infrastructure-access/#4-add-a-target) resource allows you to configure Infrastructure Access Targets for an account.

## Example Usage

```terraform
resource "cloudflare_infrastructure_access_target" "example" {
  account_id = "f037e56e89293a057740de681ac9abbe"
  hostname   = "example-target"
  ip = {
    ipv4 = {
      ip_addr            = "198.51.100.1"
      virtual_network_id = "238dccd1-149b-463d-8228-560ab83a54fd"
    }
    ipv6 = {
      ip_addr            = "2001:db8::"
      virtual_network_id = "238dccd1-149b-463d-8228-560ab83a54fd"
    }
  }
}

resource "cloudflare_infrastructure_access_target" "ipv4_only_example" {
  account_id = "f037e56e89293a057740de681ac9abbe"
  hostname   = "example-ipv4-only"
  ip = {
    ipv4 = {
      ip_addr            = "198.51.100.1"
      virtual_network_id = "238dccd1-149b-463d-8228-560ab83a54fd"
    }
  }
}
```
<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `account_id` (String) The account identifier to target for the resource.
- `hostname` (String) A non-unique field that refers to a target.
- `ip` (Attributes) The IPv4/IPv6 address that identifies where to reach a target. (see [below for nested schema](#nestedatt--ip))

### Read-Only

- `created_at` (String) The date and time at which the target was created.
- `id` (String) The identifier of this resource.
- `modified_at` (String) The date and time at which the target was last modified.

<a id="nestedatt--ip"></a>
### Nested Schema for `ip`

Optional:

- `ipv4` (Attributes) The target's IPv4 address. (see [below for nested schema](#nestedatt--ip--ipv4))
- `ipv6` (Attributes) The target's IPv6 address. (see [below for nested schema](#nestedatt--ip--ipv6))

<a id="nestedatt--ip--ipv4"></a>
### Nested Schema for `ip.ipv4`

Required:

- `ip_addr` (String) The IP address of the target.
- `virtual_network_id` (String) The private virtual network identifier for the target.


<a id="nestedatt--ip--ipv6"></a>
### Nested Schema for `ip.ipv6`

Required:

- `ip_addr` (String) The IP address of the target.
- `virtual_network_id` (String) The private virtual network identifier for the target.

## Import

Import is supported using the following syntax:

```shell
$ terraform import cloudflare_infrastructure_access_target.example <account_id>
```
