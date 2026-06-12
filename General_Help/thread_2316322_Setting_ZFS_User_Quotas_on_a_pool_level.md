---
title: "Setting ZFS User Quotas on a pool level"
date: 2016-03-07
forum: General Help
---

### Post by Chris_Shelton on 2016-03-07
Hi,

I want to be able to set user quotas on my setup, to limit users to say, 10GB storage space for example.

I know I can do this at a dataset level, by    [B]zfs set userquota@username=10G pool/dataset

[/B]But I want to be able to set a user quota across the whole system/pool (there is only one pool), rather than at each dataset level. Is this possible?

I have tried   **zfs set userquota@username=10G pool  **but that has not set the quota recursively to all underlying datasets.

Has anyone got any suggestions?


Thanks, Chris.

---

