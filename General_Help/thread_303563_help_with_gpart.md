---
title: "help with gpart"
date: 2006-11-20
forum: General Help
---

### Post by sybaritefury on 2006-11-20
I attempted to use gparted to turn a large NTFS partition into a smaller NTFS partition and use the leftover space for a ext3 partition. There was already a small ext3 partition on the drive.

Although gparted told me that both operations were successful, when I rebooted, it does not recognize the new partitions. I get "bad superblock" errors.

I've done a lot of reading in these forums and thought that gpart might help.  However, when I started gpart, it gave the beginning message "Begin scan..."   But it never said anything after that.  It is a large drive, the missing partition should be around 120G, but I left it to run overnight and it still had not updated the screen. I've got a fairly new processor.

Anyone have any idea what I might be doing wrong?  The drive is my second drive, /dev/hdb, and it will mount the (pre-existing) ext3 partition as /dev/hdb2.

---

