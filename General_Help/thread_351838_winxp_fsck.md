---
title: "winxp fsck"
date: 2007-02-02
forum: General Help
---

### Post by jtmedin on 2007-02-02
Have 2 hds one with ubuntu one with winxp with 2 partitions. Of the 2 partitions one is ntfs & the other fat32. I have installed the ext2 installable file system for windows. Every time i boot windows & then boot ubuntu I get unable to mount the ntfs partition & then must run fsck. I run fsck & find an inode with the wrong count (or something like that) & end up doing about 3 fixes & then ubuntu boots. Anyone got any ideas? TIA

---

### Post by MoLE on 2007-02-03
Sounds like the Windows ext2 filesystem driver is corrupting your linux partition.  Which filesystem are you using for Ubuntu?  Default is ext3, which although built on ext2, is not exactly the same.  Your safest method for exchanging data between the two operating systems is via a Fat32 partition set aside for the purpose.

---

### Post by Polygon on 2007-02-03
i installed the driver like you did, and i experienced the same problems. Every so often ubuntu would think that partiton was corrupted and i should fsck it to fix it

its because ext3 file systems have a journal, and while ext2 filesystems are almost exactly the same as ext3, they dont have a journal, so writing to ext3 partitions while using the ext2 driver is going to cause problems

Your best bet is to have a fat32 partiton that serves as a neutral point between both operating systems, like the poster above me stated.

---

