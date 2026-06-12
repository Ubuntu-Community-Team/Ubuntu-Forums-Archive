---
title: "disks moves around"
date: 2008-06-20
forum: General Help
---

### Post by kramer2718 on 2008-06-20
Call me crazy, but it seems as if my drives are moving around on me.  I have two SATA hds, an IDE hd and an IDE burner and an AMD processor.  Ubuntu server is installed.  Last time I booted, I could swear that fdisk -l showed that my larger SATA drive was sdc while my IDE drive was sdb.  Now it appears that my larger SATA drive is sdb while my IDE drive is sdc.  I installed ubuntu on one of the partitions of my IDE drive, so it wrote that portion of fstab and has always mounted itself no problem.  I usually manually mount my SATA drives, but when I tried to mount the larger one, I discovered that its fstab entry referred to it as sdc when it should have been sdb.  I'm sure that this worked last time I booted up.

Am I going crazy or is Ubuntu renumbering my drives for me.  Also, why does my IDE drive have to be an sdX shouldn't it be an hdX?

---

### Post by Zorael on 2008-06-20
They changed the kernel so that all devices are now sdx devices, some time ago now. Did you do a major upgrade, such as from Edgy -> Hardy?

While a lot of work, I'd still recommend a clean install so as to avoid a whole bunch of errors.

If it's still moving around for some reason, just make sure fstab mounts your filesystems by their UUIDs instead of their device nodes.
```
$ sudo blkid
```

---

