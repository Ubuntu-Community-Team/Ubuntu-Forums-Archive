---
title: "How to mount NTFS with read/write access"
date: 2006-08-05
forum: General Help
---

### Post by Pulshion on 2006-08-05
i sucessfully mounted ntfs partition but it only allowes me to read. I have alot of data on that hard drive. Also i have about 2000 songs, where i would like to delete some. 

Right now this is my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1    /media/D ntfs  nls=utf8,umask=0222 0    0
/dev/hda1    /media/Fat32 vfat  iocharset=utf8,umask=000  0    0

```

Thanx
Dmitriy

---

### Post by newlinux on 2006-11-11
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009), if you haven't already figured this out,

---

