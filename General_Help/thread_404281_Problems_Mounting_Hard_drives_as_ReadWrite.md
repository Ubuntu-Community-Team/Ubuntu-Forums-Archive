---
title: "Problems Mounting Hard drives as Read/Write"
date: 2007-04-08
forum: General Help
---

### Post by MK_MIke on 2007-04-08
Hello,

i'm having problem mounting 2 hard drives, i manged to get them to mount them but the problem lies in the fact i need the hard drives hdb2 and hdc1 both to able to read / write for all users. at the moment when i mount them only root has read / write access.

Any Ideas?


My fstab file:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=b2523932-034e-4868-beef-3c174dd22f4b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=f550eb52-8ade-41b1-b5e4-fd3af6fc4192 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1      /media/hdb2         ext3     defaults
/dev/hdc1      /media/hdc1         ext3     defaults


Thanks :),
Michael Knights

---

### Post by krussell on 2007-04-08
Hello :-)
Try replacing defaults with other options, like
/dev/hdb1 /media/hdb2 ext3 **defaults**

instead of **default** you can use: user,owner,rw

---

