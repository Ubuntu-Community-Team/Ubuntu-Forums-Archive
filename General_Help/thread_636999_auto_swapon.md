---
title: "auto swapon"
date: 2007-12-10
forum: General Help
---

### Post by s-lime on 2007-12-10
Here is my fstab file.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=6926d4c0-c109-4d76-8d1d-7f644e8e42ce /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=3932a641-b20d-47c4-8f9f-6c45f11dd4ca none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
```

How can I achieve that /dev/hda5/ is swapon on every boot?

---

### Post by rsambuca on 2007-12-10
That should be set that way already.  What is the output of 

blkid

---

### Post by s-lime on 2007-12-10
Thanks... The UUID for swap was incorrect.

---

