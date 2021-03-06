| Field       | Description                 | Accepted Values   | Schema | Default    |
|-------------|-----------------------------|-------------------|--------|------------|
| nets                  | Match packets with IP in any of the listed CIDRs. | List of valid IPv4 CIDRs or list of valid IPv6 CIDRs  | list of cidrs |
| notNets               | Negative match on CIDRs. Match packets with IP not in any of the listed CIDRs. | List of valid IPv4 CIDRs or list of valid IPv6 CIDRs  | list of cidrs |
| selector    | Positive match on selected endpoints. If a `namespaceSelector` is also defined, the set of endpoints this applies to is limited to the endpoints in the selected namespaces. | Valid selector | [selector](#selector) | |
| notSelector | Negative match on selected endpoints. If a `namespaceSelector` is also defined, the set of endpoints this applies to is limited to the endpoints in the selected namespaces. | Valid selector | [selector](#selector) | |
| namespaceSelector | Positive match on selected namespaces. If specified, only workload endpoints in the selected Kubernetes namespaces are matched. Matches namespaces based on the labels that have been applied to the namespaces. Defines the context that selectors will apply to, if not defined then selectors apply to the NetworkPolicy's namespace. Match a specific namespace by name using the `projectcalico.org/name` label. | Valid selector | [selector](#selector) | |
| ports | Positive match on the specified ports | | list of [ports](#ports) | |
| notPorts | Negative match on the specified ports | | list of [ports](#ports) | |
| serviceAccounts | Match endpoints running under service accounts. If a `namespaceSelector` is also defined, the set of service accounts this applies to is limited to the service accounts in the selected namespaces. | | [ServiceAccountMatch](#serviceaccountmatch) | |

> **NOTE**: You cannot mix IPv4 and IPv6 CIDRs in a single rule using `nets` or `notNets`. If you need to match both, create 2 rules.
{: .alert .alert-info}
