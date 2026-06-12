---
title: "don't understand ext3 volume permissions"
date: 2007-04-07
forum: General Help
---

### Post by hungrybeast on 2007-04-07
I have a ~7GB ext3 partition on my hard disk that is owned by root. I would like to own it myself. It is the sda6 in this fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /home/user/fat  vfat    defaults,umask=0000      0       0
/dev/sda6       /home/user/ext3 ext3    defaults        0       0

```

Any help would be greatly appreciated. I do own the directory I mount it to.

---

### Post by PapaNerd on 2007-04-07
I'm curious why you would want to control the mount point ownership.  Presumably, if it is for security reasons, setting the permissions on the directory structure on that partition should be sufficient.

---

