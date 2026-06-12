---
title: "Missing mountpoints GParted"
date: 2007-12-08
forum: General Help
---

### Post by zkab on 2007-12-08
I have Ubuntu 7.10 and GParted complains of missing mountpoint for one of my SATA-drives.
I don't experience any problem with the drive ... but still why the message :confused:

GParted 0.3.3 gives for /dev/sda1:

1. Yellow warning sign
2. Warning message:
   Unable to find mountpoint
   Unable to read the contents of this file system
   Because of this some operations may be unavailable.
----------------------------------------------------------------------------------------------
fdisk -l gives:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60424   485355748+  83  Linux
/dev/sda2           60425       60801     3028252+   5  Extended
/dev/sda5           60425       60801     3028221   82  Linux swap / Solaris

/etc/fstab gives:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0e21f8c5-6e90-4434-96dc-d98a0b9ce7ee /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ca1df9d2-e38d-4ef4-830a-d63ea1be4426 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
----------------------------------------------------------------------------------------------

What is wrong ? It looks OK to me with my limited knowledge of Ubuntu.
/home (for /dev/sda1) is exported via NFS ... could that be the problem ?

---

