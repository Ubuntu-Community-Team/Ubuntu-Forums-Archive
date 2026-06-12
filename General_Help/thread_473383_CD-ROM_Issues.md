---
title: "CD-ROM Issues"
date: 2007-06-14
forum: General Help
---

### Post by es012 on 2007-06-14
I am having privilege issues with mounting my CD-ROM and a certain disk. Apparently the CD-ROM is only able to be accessed by group 400 when I put my Dreamfall: The Longest Joruney CD in the drive, therefore I cannot see whats on the disk or mount it to install via Cedega. I get ```
"The folder contents could not be displayed. 
You do not have the permissions necessary to view the contents of "cdrom0".
``` Funny thing is that the Ubuntu CD, a burned CD with pictures, the Battlefield 2 disk, along with various other disks all mount when inserted. So why is it not letting me mount Dreamfall? Is it something to do with copy protection? If so how do I go around it? Thanks.

---

### Post by cchester on 2007-06-14
Hi,

Let me know when you get a reply because I have a disc that does the same thing.

---

### Post by ashz on 2007-06-14
For something similar...

[http://ubuntuforums.org/showthread.php?t=196740](http://ubuntuforums.org/showthread.php?t=196740)

Cheers
ash

---

### Post by es012 on 2007-06-14
Well, from what I read in that thread my entry in fstab is correct. Here is my current fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=5aeb5ee3-8c3f-441c-8af9-c249bb8c0e81 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=6ce4c803-ec8f-4dbb-b266-682ba2a7f0a6 /home           ext3    defaults        0       2
# /dev/sda1
UUID=4C60346560345842 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=EEA8A7F0A8A7B60D /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=40F09025F09022E8 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=d013a07e-a551-42fc-a138-cbc9e3424a47 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```
My CD/DVD burner is at /dev/hdc and mounts to /media/cdrom0. Is that right? Are the permissions/parameters correct? Can I force permissions for all disks?

---

