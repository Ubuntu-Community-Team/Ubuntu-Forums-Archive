---
title: "ubuntu no seeing drives in server"
date: 2012-12-24
forum: General Help
---

### Post by dcody on 2012-12-24
Hello - trying to wipe a couple hdd with an old server that I have - I think I can manage that - but the system is not seeing the drives I put in to wipe. 

How do I tell the system to recognize the other drives. 
I did a fdisk -l and here is the output. Thanks. 


Disk /dev/sda: 160.0 GB, 159988580352 bytes
255 heads, 63 sectors/track, 19450 cylinders, total 312477696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00041e81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   304091135   152044544   83  Linux
/dev/sda2       304093182   312475647     4191233    5  Extended
/dev/sda5       304093184   312475647     4191232   82  Linux swap / Solaris

---

### Post by dcstar on 2012-12-24
> **dcody said:**
> Hello - trying to wipe a couple hdd with an old server that I have - I think I can manage that - but the system is not seeing the drives I put in to wipe. 


The kernel will automatically recognise any correctly connected and working drives on reboot.

If they are not listed then they do not satisfy those criteria.

---

