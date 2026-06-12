---
title: "Ubuntu checking windows partitions while booting"
date: 2007-02-25
forum: General Help
---

### Post by laxmanb on 2007-02-25
Ubuntu is running dosfsck every time my computer boots up, and I'm finding it very annoying because it adds at least 2 minutes to the boot up time... how do i disable this??

---

### Post by taurus on 2007-02-25
You probably activate that option in /etc/fstab.  Can you post your /etc/fstab here?

```
cat /etc/fstab
```

---

### Post by laxmanb on 2007-02-25
Here you go...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by yabbadabbadont on 2007-02-25
```
/dev/hda1 /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/hda5 /media/hda5 vfat defaults,utf8,umask=007,gid=46 0 1
```
Just change the '1' at the end of those two lines to a '0'.

That is, change the one to a zero.

---

### Post by laxmanb on 2007-02-25
Thank You!

---

