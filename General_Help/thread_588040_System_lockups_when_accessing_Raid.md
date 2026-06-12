---
title: "System lockups when accessing Raid"
date: 2007-10-23
forum: General Help
---

### Post by nikorc on 2007-10-23
I am having system/app lockup with anything that accesses raid5 device (5-500GB drives setup raid5).  Originally I had the raid 5 mounting as my /home but that was causing X server/system to lockup, I could lock it up just trying to use wine for first time.  I have since moved it to a different mount point (/md0) this helped with wine issue, but I still have processes that write and read from the raid this is still causing random lockup when the system is used.  I am not even sure of how to troubleshoot/debug what is going on in the back end during system hangs.  Some times its just a process that will not kill some times it locks up system where keyboard is dead (cap lock/num lock not toggling led light).
Had issue with Feisty and Getsy.

2 Maxtor
1 Seagate
2 Western Digital

All 500GB
linux software Raid 5
XFS

AMD X2 4400
2 GB Ram
Nforce 4 chipset

mount point: /md0 was /home but couldn't use wine had more system lock

---

### Post by fjgaude on 2007-10-23
The only thing that comes to mind is you are at the filesystem limit of two Terabytes with those five drives. What does dh -h show?

---

### Post by fjgaude on 2007-10-23
The only thing that comes to mind is you are at the filesystem limit of two Terabytes with those five drives. Perhaps XFS has a larger capapcity than ext3? What does dh -h show?

---

