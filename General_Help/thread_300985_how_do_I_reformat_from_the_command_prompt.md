---
title: "how do I reformat from the command prompt"
date: 2006-11-16
forum: General Help
---

### Post by harty83 on 2006-11-16
I need to reformat a fat32 partition on a server I have that does not have a desktop gui. So, what should I do from the command prompt to reformat the fat32 partition?

Thanks!
Alan

---

### Post by taurus on 2006-11-16
You can use the gparted from the LiveCD to format it as vfat!

---

### Post by koenn on 2006-11-16
```
mkfs.ext2 /dev/hda1
```
replace hda1 with correct partition

[http://www.linux.com/howtos/Hard-Disk-Upgrade/format.shtml](http://www.linux.com/howtos/Hard-Disk-Upgrade/format.shtml)

---

### Post by taurus on 2006-11-16
> **koenn said:**
> ```
mkfs.ext2 /dev/hda1
```
replace hda1 with correct partition

[http://www.linux.com/howtos/Hard-Disk-Upgrade/format.shtml](http://www.linux.com/howtos/Hard-Disk-Upgrade/format.shtml)
Wait!  mkfs.ext2 will create ext2 filesystem not fat32!!!  He/she wants to format the partition to fat32...

---

### Post by speedman on 2006-11-16
cfdisk /dev/hdX

... and use the on-screen options.


Regards,

SM

---

### Post by koenn on 2006-11-17
> **taurus said:**
> Wait!  mkfs.ext2 will create ext2 filesystem not fat32!!!  He/she wants to format the partition to fat32...

Sorry, misread that. 
I interpreted > I need to reformat a fat32 partition on a server I have that does not have a desktop gui. So, what should I do from the command prompt to reformat the fat32 partition?
as
"I have partition formatted as fat32 but want top format it into something else " (& I assumed : in a linux type filesystem)

---

### Post by mbeierl on 2006-11-17
mkfs -t vfat /dev/xxx

should make a fat32 [partition] filesystem

---

### Post by speedman on 2006-11-17
> **mbeierl said:**
> mkfs -t vfat /dev/xxx

should make a fat32 partition.

Nope.  mkfs is for making a file system on a partition.  You need to create a partition with a tool like fdisk, or cfdisk before you make the file system - regardless of what type it is.


Regards,

SM

---

### Post by mbeierl on 2006-11-21
I thought from the post that he already has the partition, he just wants to format it again as fat32.  In that case, fdisk is not needed.

---

