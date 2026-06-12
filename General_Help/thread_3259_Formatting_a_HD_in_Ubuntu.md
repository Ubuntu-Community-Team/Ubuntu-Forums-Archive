---
title: "Formatting a HD in Ubuntu"
date: 2004-11-04
forum: General Help
---

### Post by princemackenzie on 2004-11-04
Here's the deal:

I have installed both ubuntu and win 2k on my main HD,  hda.  I have a much larger slave drive where I keep all my data (hdb).  Anyway, for ease of use, I wanted to format my second HD (hdb) to the FAT file system so both windows and ubuntu could read/write to it.  Previously, I had just mounted it so I could read the files in Ubuntu- but I badly need write support as well so I could share data between the two OSes.

So I copied all my data over to a borrowed external HD and tried to format it in win 2k... but it typical windoze fashion, it works for a while and then says "can not complete the format" even though it will happily reformat it as NTFS, but it will never work as FAT.  So my question is: how can I try to format the disk to the FAT file system inside ubuntu, so I could copy all the data over again before I have to give back this external HD?  I know the disk is working fine, too.

-Mackenzie

---

### Post by fng on 2004-11-04
A complete howto :)

boot into ubuntu

$> sudo fdisk /dev/hdb (or another hdx)
Set up the partitions that you like.
Change the type of the FAT-partition to WIN95 FAT32
write partition table

$> sudo mkdosfs /dev/hdb1 (or any other hdxx)

---

### Post by princemackenzie on 2004-11-04
works great until...

$ sudo mkdosfs /dev/hdb1
mkdosfs 2.10 (22 Sep 2003)
mkdosfs: Attempting to create a too large file system

also...

Disk /dev/hdb: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks      Id    System
/dev/hdb1               1        9729    78148161    b  W95 FAT32



Thanks for all your help!

---

### Post by TekMate on 2004-11-04
[QUOTE=princemackenzie]works great until...

$ sudo mkdosfs /dev/hdb1
mkdosfs 2.10 (22 Sep 2003)
mkdosfs: Attempting to create a too large file system

also...

Disk /dev/hdb: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks      Id    System
/dev/hdb1               1        9729    78148161    b  W95 FAT32



Thanks for all your help![/QUOTE]
 Use fat32 not fat if the drive is over 2gb fat won't work. What size is the drive?

---

### Post by princemackenzie on 2004-11-04
It is an 80 GB drive, and I selected fat32.

---

### Post by diebels on 2004-11-04
The size limit is quite small for fat32 too. About 30Gb I think. Try 30+30+20.

---

### Post by princemackenzie on 2004-11-05
Even if I make the partitions 20 GB, i still get the error saying its a too large file system.

Is there another way to do this?  Or am I just doing something wrong?   :confused:

---

