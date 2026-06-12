---
title: "Multiple iSCSI connections to the same NAS"
date: 2021-04-25
forum: General Help
---

### Post by dstu69 on 2021-04-25
Hi,

I have 2 iSCSI connections to the same NAS from my Ubuntu server, one linked to /dev/sdb1 and the other to /dev/sdc1

The problems I'm facing are that very often, after reboot:
1. Only one of the 2 connects successfully
2. The order of the connections is inverted, causing the one that should go to /dev/sdc1 to occupy the /dev/sdb1 slot

Also, if I connect a USB drive to the server and reboot, it would also occupy /deb/sdb1

Bottom line, I'm wondering whether it's possible to define them as /dev/sdx1 and /dev/sdy1 permanently and keep those settings even after reboot and not just take the next available. I believe that it's called "Persistent block device naming", but I'm not sure how to do it yet

Thanks

---

