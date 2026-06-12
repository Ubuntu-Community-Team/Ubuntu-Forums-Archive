---
title: "CD/DVD automounting issue"
date: 2007-01-19
forum: General Help
---

### Post by Soilman on 2007-01-19
CD/DVD writer will mount the CD if it is music. Will not mount data.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=ba8ceca7-def6-45db-8ec0-daab37b9f102 / ext3 defaults,errors=remount-ro 0 1
UUID=ccaa0553-62b6-489d-a656-41d5b8bfc768 none swap sw 0 0
UUID=ed0e6a94-1cb9-4acf-8865-bc7834b2f49e /mnt/data1 ext3 defaults,errors=remount-ro 0 2
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

As you can see from my fstab the CD is at /dev/hdb not the usual /dev/hdc 

Any ideas?

---

