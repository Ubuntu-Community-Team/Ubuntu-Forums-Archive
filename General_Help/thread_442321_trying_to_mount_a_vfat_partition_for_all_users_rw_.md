---
title: "trying to mount a vfat partition for all users rw [Resolved]"
date: 2007-05-13
forum: General Help
---

### Post by mrt on 2007-05-13
```
root@mike-desktop:/# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b462a0a9-fbd7-4a32-9e4a-6be9d9ea2235 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=67d426c2-4303-4cbc-9f4c-dd93d0bdabb7 none            swap    sw              0       0
/dev/scd1       /media/cdrw   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/dvd   udf,iso9660 user,noauto     0       0
/dev/sdb1       /media/shared   vfat rw,users  0 0
root@mike-desktop:/# 

```

I'm trying to mount /dev/sdb1 so all users can read/write to it.  The above does not work; it mounts fine but only root can write to it (users can read it).  What is wrong?  I've also tried "defaults" in place of "rw,users" and I also tried "chmod -R 777 /media/shared".

---

### Post by Ramses de Norre on 2007-05-13
Add **umask=0000** to the options.

---

### Post by aysiu on 2007-05-13
This line ```
/dev/sdb1       /media/shared   vfat rw,users  0 0
``` should read ```
/dev/sdb1       /media/shared   vfat iocharset=utf8,umask=000  0 0
```

---

### Post by mrt on 2007-05-13
thanks, but neither of those worked...any other suggestions?

---

### Post by aysiu on 2007-05-13
> **mrt said:**
> thanks, but neither of those worked...any other suggestions?
After you make changes to the /etc/fstab file, you should unmount and remount the partition for those changes to take effect: ```
sudo umount /dev/sdb1
sudo mount -a
``` If that doesn't work, try rebooting your computer.

---

### Post by mrt on 2007-05-13
> **aysiu said:**
> If that doesn't work, try rebooting your computer.

That was it.  I was using umount and "mount -a" to remount the partition after editing fstab, but apparently that wasn't enough.  After rebooting, the partition is writeable to users.  Thanks for your help guys!

Mike

---

### Post by Ramses de Norre on 2007-05-13
A **mount -o remount,umask=0000** would have done the same... Rebooting shouldn't be necessary for such a task.

---

