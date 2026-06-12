---
title: "Mount windows partition"
date: 2005-04-11
forum: General Help
---

### Post by oldmarti on 2005-04-11
I mount my winxp partition like ubuntu unofficial guide. Here my fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/windows  ntfs    umask=0222      0       0
/dev/hdb5       /media/DiskD    vfat    umask=0         0       0

But some times when I start ubuntu, windows and DiskD are on my desktop, some time they missing (but they are mount, only on desktop missing)! Any ideas?
My ubuntu is 5.04, with apt-get upgraded today

---

### Post by erkki70 on 2005-04-11
Hi,
This has been on the forums several times already and the quick and dirty fix to mount your windows partition and make it appear every time can be solved by removing the first backslash before dev in your fstab (I believe I remember right!).
So instead of [QUOTE=oldmarti]
/dev/hdb1       /media/windows  ntfs    umask=0222      0       0
[/QUOTE]
try
```
dev/hdb1       /media/windows  ntfs    umask=0222      0       0
``` 

Hope this helps,
Cheers,
Erkki

---

### Post by oldmarti on 2005-04-11
Thank's!!! It's working now ;-))

---

