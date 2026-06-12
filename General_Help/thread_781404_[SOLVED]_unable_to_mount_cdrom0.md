---
title: "[SOLVED] unable to mount cdrom0"
date: 2008-05-04
forum: General Help
---

### Post by tad1073 on 2008-05-04
I am unable to mount cdrom0. I get an error saying that /media/cdrom0 doesn't exist.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID= /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID= /home           ext3    defaults        0       2
# /dev/sdc1
UUID= /media/sdc1          ext3    defaults        0       2
# /dev/sda1
UUID= none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

---

### Post by tad1073 on 2008-05-04
bump

---

### Post by tad1073 on 2008-05-05
anyboby?

---

### Post by tad1073 on 2008-05-08
bump

---

