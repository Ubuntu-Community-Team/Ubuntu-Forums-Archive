---
title: "Changing mount name (lablel)"
date: 2007-11-02
forum: General Help
---

### Post by wheezer on 2007-11-02
Ok, I have two partitions on a new external drive.  The are showing up in nautilus as "disk, and disk-1:

How can I change them to "linuxbackup and winbackup?"  I've tried to find this solution, but as usual, there are 8 million posts, but no clear answers.

Thanks

--Noob

---

### Post by k_grdn on 2007-11-02
Hi wheezer,

To label your disk use:

mke2fs -L or mkfs.ext2 -L to label filesystems.

Or if it's the mount point you want to change unmount the volumes create dir's with the desired names i.e linuxbackup and mount the volume to that dir.

mount -t ext2 /dev/sda1 linuxback

Regards,

k_grdn

---

### Post by dcstar on 2007-11-02
> **k_grdn said:**
> Hi wheezer,

To label your disk use:

**mke2fs -L or mkfs.ext2 -L to label filesystems.**

Or if it's the mount point you want to change unmount the volumes create dir's with the desired names i.e linuxbackup and mount the volume to that dir.

mount -t ext2 /dev/sda1 linuxback

Regards,

k_grdn

These only apply to EXT2/3 filesystems, without knowing** exactly** what filesystems are being referred to then this may be incorrect.

For FAT and NTFS filesystems there are individual commands to label them, in Linux you may also need to download additional packages to get these tools:

[http://ubuntuforums.org/showpost.php?p=3675282&postcount=5](http://ubuntuforums.org/showpost.php?p=3675282&postcount=5)

---

### Post by wheezer on 2007-11-02
> **k_grdn said:**
> 
mke2fs -L or mkfs.ext2 -L to label filesystems.


I can't seem to make this work. Would you mind showing me a complete command syntax example?

Thanks!

---

### Post by nick_h on 2007-11-02
As dcstar said you need to find out what filesystem is on your drive first.

Then have a look at the [Rename USB Drive](https://help.ubuntu.com/community/RenameUSBDrive) guide.  It gives examples for FAT, NTFS, ext2/3 and Reiser.

---

### Post by wheezer on 2007-11-03
> **nick_h said:**
> As dcstar said you need to find out what filesystem is on your drive first.

Then have a look at the [Rename USB Drive](https://help.ubuntu.com/community/RenameUSBDrive) guide.  It gives examples for FAT, NTFS, ext2/3 and Reiser.

Thanks all.  That's what I needed. ( I am using Fat32 and Ext3)

---

