---
title: "Howto explore Kernel config files."
date: 2017-12-07
forum: General Help
---

### Post by smithbox on 2017-12-07
Hi all.

Before i compile, I need to know a few details about my current Kernel settings/configs:
```
4.8.0-59-generic #64-Ubuntu SMP Thu Jun 29 19:38:34 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```
Details about:
- netfilter modules ?
- net_cls support ?

What kind of command will show me such information, as example:
```
CONFIG_NET_CLS_RSVP6=m
CONFIG_NET_CLS_FLOW=m[SIZE=2]CONFIG_NET_CLS_CGROUP=y[/SIZE]
CONFIG_NET_CLS_ACT=y
CONFIG_NET_CLS_IND=y
```
```
CONFIG_NF_CONNTRACK_H323=y
CONFIG_NF_CONNTRACK_IRC=y
CONFIG_NF_CONNTRACK_TFTP=m
```[B]

Optimal would be one command including all Kernel settings.

[/B]Regards.

---

