---
title: "qemu -user-net gets no network"
date: 2005-10-16
forum: General Help
---

### Post by twelvegates on 2005-10-16
When I run a Archlinux image in qemu under Ubuntu eth0 of the guest doesn't get configured as usual. But in the guests system log there appears:
```
NETDEV WATCHDOG: eth0: transmit timed out
eth0 Tx timed out, list interupt? TSR=0x1, I=0x3 t=5986.
```
When I run the same image under Debian the guests eth0 gets configured as usual.
What's wrong when it is run under Ubuntu?

---

