---
title: "fdisk -l different from /etc/fstab"
date: 2007-06-05
forum: General Help
---

### Post by hellmet on 2007-06-05
I've never seen anything like this before, and I'm not sure if this is alright.

This is my fdisk -l ::

```
Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *         901        1681     6273382+   c  W95 FAT32 (LBA)
/dev/hdb2            1682        9729    64645560    f  W95 Ext'd (LBA)
/dev/hdb3               1         900     7229218+  83  Linux
/dev/hdb5            1682        1761      642568+  82  Linux swap / Solaris
/dev/hdb6            1762        5745    32001448+   b  W95 FAT32
/dev/hdb7            5746        9729    32001448+   b  W95 FAT32

Partition table entries are not in disk order

```

Here is my fstab::

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=179b5b40-6df6-45bc-9f4a-4962fdca03c4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=1821-C85C  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda6
UUID=597A-C4BE  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda7
UUID=26FE-4323  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda5
UUID=b3320a8a-900f-4f79-9a78-14107ea53269 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Why is there a difference in the name of the HDD??

hdb, sda??

I discovered this when I was trying to grub-install /dev/sda

---

### Post by adampyre on 2007-06-05
I had a problem earlier with my partition and noticed this. I came across a post that suggested that the names changed from s's to h's in a recent update? I think the kernel update? I am not 100% sure though. I don't think this is going to cause you any issues for the time being though....

---

### Post by merlinus on 2007-06-05
Yes, indeed -- from the kernel update to -16.

No problem, though, because fstab is using UUIDs.

-merlin

---

### Post by adampyre on 2007-06-05
Looking back at my post, it ws merlinus who answered my questions on this one. Thanks merlinus!

---

### Post by hellmet on 2007-06-06
Yea.. UUIDs save the day :D as I discovered recently.

---

