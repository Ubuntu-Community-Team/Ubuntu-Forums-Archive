---
title: "bluetooth passkey-agent (Ubuntu 7.04 Feisty)"
date: 2007-08-17
forum: General Help
---

### Post by joyride76 on 2007-08-17
Hi all,

I'm try to pair my mobile to have an internet connection.

I'm able to get the mac of my mobile... but there is no way to have the pin exchange:

sudo rfcomm bind 0 00:0A:28:36:EB:21 1
rfcomm connect rfcomm0 00:0A:28:36:EB:21

On the syslog I found that the authentication doesn't start!
 hcid[5176]: link_key_request (sba=00:03:7A:2E:65:24, dba=00:0A:28:36:EB:21)

Have you any idea on what's happening or which kind of test may resolve the trouble?

Thanks 

Stefano

---

