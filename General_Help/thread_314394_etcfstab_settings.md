---
title: "/etc/fstab settings"
date: 2006-12-07
forum: General Help
---

### Post by scottym on 2006-12-07
Could someone please tell me if these settings are ok for a single boot system:

## /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /usr            ext3    defaults        0       2
/dev/hda1       /home           ext3    defaults,       0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by aysiu on 2006-12-07
What do you mean by "ok"?

---

### Post by bodhi.zazen on 2006-12-07
> /dev/hda1 /home ext3 defaults, 0 1

should be ```
/dev/hda1 /home ext3 defaults 0 2
```If you want to check the fisle system at boot,

otherwise ```
/dev/hda1 /home ext3 defaults 0 0
```will do

Else I do not see any problems....

---

### Post by scottym on 2006-12-07
Thanks for the reply.

---

