---
title: "Why Auto fsck on every 30th reboot ?"
date: 2007-06-12
forum: General Help
---

### Post by xp_newbie on 2007-06-12
My Ubuntu 6.06 LTS is installed on an ext3 partition. The way I understand it, ext3 provides journaling which is supposed to eliminate the need of periodic fsck.

However, my system still performs this "traditional" (and annoying) fsck every X reboots. In my case, X=30.

I am surprised to see that on ext3 (on ext2 it was part of the package). Does anyone know why? Is it something "fixable"?

Also, why there is no mention of this fsck (and its results) in /var/log? Is there a place where I can find some logging of this activity?

Lastly, how do I change the number of maximum reboots between fscks from 30 to 100?

Thanks,
Alex

---

### Post by ingvildr on 2007-06-12
First journaling protects against i sudden power off, so it can rebuild the file system. Fsck just checks if the file system has been corrupted or is fragmented. Ext3 is pretty good at not getting fragmented but with ext4 and extents fragmentation will be a thing of the past. To answer the number of mounts question simply;
```
tune2fs -c 100 /dev/sdX
```
Where X is the name of your drive. As for the log i know /var/log/fsck contains files that log your last mount check, but i dont know how helpful that will be.

---

### Post by xp_newbie on 2007-06-12
> **ingvildr said:**
> First journaling protects against i sudden power off, so it can rebuild the file system. Fsck just checks if the file system has been corrupted or is fragmented. Ext3 is pretty good at not getting fragmented but with ext4 and extents fragmentation will be a thing of the past. To answer the number of mounts question simply;
```
tune2fs -c 100 /dev/sdX
```
Where X is the name of your drive. As for the log i know /var/log/fsck contains files that log your last mount check, but i dont know how helpful that will be.

ingvildr, thank you very much! You have been very helpful.

BTW, I checked /var/log and there is no file (or directory) named fsck (or fsck.log) there. Are you sure that such a log is always kept by the system? Is it possible that Ubuntu 6.06 does not keep such a log by default?

Thanks,
Alex

---

### Post by ingvildr on 2007-06-12
That could be the case considering i am on 7.04. Interesting that 6.06 doesn't have that directory, no idea why one version has it and one doesn't so i can't be much help there.

---

