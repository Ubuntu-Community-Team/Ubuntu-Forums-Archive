---
title: "Fix bad superblock without formatting"
date: 2007-05-26
forum: General Help
---

### Post by Cless on 2007-05-26
Hi there guys!

Ok lets go straight to the problem! It all started when I, by a mistake, ran "sudo chmod - R 777 *" in /. The hole system got screwed up and I was not able to use the terminal or anything. I thought the best thing to do would be to format and install Ubuntu all over again. I did this and experienced no problems until I tried to mount my 3 other hard drives (ext3).

When i ran "mount -a", after adding the different drives in fstab, I got the following output: 
       wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The strange thing is that all of the drives auto mounts as "disk-1" etc in /media and I have read+write permissions on all of them.

So, I wonder if it is possible to fix the superblock and make my hdds mountable without having to format them? I'm hoping someone will be able to help me! ;)


Output of sudo fdisk -l:

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36481   293033601   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   83  Linux

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       19080   153260068+  83  Linux
/dev/hdc2           19081       19457     3028252+   5  Extended
/dev/hdc5           19081       19457     3028221   82  Linux swap / Solaris

Output of fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=163add6f-ed88-4f07-b64a-fec963722a6a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=8ef62812-619a-4e4d-824f-dfe432240218 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda	/media/seagate	ext3	defaults	0	0
/dev/sdb	/media/tristar	ext3	defaults	0	0
/dev/sdc	/media/goldfish	ext3 	defaults	0	0

---

### Post by confused57 on 2007-05-26
Maybe the section on checking for a bad superblock in this link will help:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by psusi on 2007-05-26
You screwed up your fstab entries.  They specify /dev/sda, sdb, and sdc, which are the entire disks, rather than partitions on those disks.

---

### Post by Cless on 2007-05-26
Haha, thanks psusi! What an easy solution! :D

---

