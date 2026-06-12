---
title: "Problem with using pktgen and tap device"
date: 2007-06-14
forum: General Help
---

### Post by adit262 on 2007-06-14
Hi all,

I need to inject packets into a tap device (by opening /dev/net/tun and ioctl call). Im using the linux packet generator pktgen to do this.
Unfortunately, when i configure pktgen to use the tap device I do not get any packet information on tcpdump.

Are there any existing problems with pktgen such that it cant use tap devices?

Im using Ubuntu 7.04, pktgen v2.68, universal tap/tun driver v1.6

Thanks,
Adit

---

