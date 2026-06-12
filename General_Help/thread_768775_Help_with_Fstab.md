---
title: "Help with Fstab"
date: 2008-04-26
forum: General Help
---

### Post by aktiwers on 2008-04-26
After installing 8.04 my partitions does not get mounted correctly.

Or in other words, they first mount when I go to Places=> and open each of them.

This is a pain, because it then mounts them different each time, resulting in Bittorrent clients to mess up, Playlist don't work and so on.

What should I change in fstab so it just get mounted automaticly on bootup and mounted with same name each time?

Here is my fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=70aa2514-9ab9-4798-8470-f37e0c93967c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=d6d3c5d9-fbe0-4b71-a410-eeac1257ce04 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

I guess sdb1 and sdb2 are the partitions I am talking about.

---

### Post by psmul on 2008-04-26
SDB1 = Swap
SDB2 = / (File System)

Your other drivers are not mentioned in fstab. Quite honestly i think i have the same problem :confused:

(correct me when im wrong, i is not ubuntu guru >.<)

---

### Post by aktiwers on 2008-04-26
> **psmul said:**
> SDB1 = Swap
SDB2 = / (File System)

Your other drivers are not mentioned in fstab. Quite honestly i think i have the same problem :confused:

(correct me when im wrong, i is not ubuntu guru >.<)

Ahh thanks you are right..  I looked fast at fstab there.
I gotta go now I will post the "fix" later

---

### Post by vanadium on 2008-04-26
I am not an expert, but I believe that currently partitions are being mounted on first use using gvfs, rather than in the traditional system using /etc/fstab. Anyway, a foolproof way to have them mount each time using the same name is to give your partitions a volume label. How you give a volume label depends on the type of file system, see

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Don't worry about that that thread is primarily about USB drives: labeling partitions is the same. I guess that now partitions on fixed disks are  treated the same way as removable drives.

---

