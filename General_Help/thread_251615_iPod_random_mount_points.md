---
title: "iPod random mount points"
date: 2006-09-05
forum: General Help
---

### Post by hanzomon4 on 2006-09-05
This post made by bugme describes my problem to a tee.

> **bugme said:**
> My iPod have the following partitions

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          10       80293+   0  Empty
/dev/sdb2   *          11        3000    24017175    b  W95 FAT32
/dev/sdb3            3001        3300     2409750   83  Linux
/dev/sdb4            3301        3648     2795310   83  Linux
```

When it is connected through USB, the last three partions are mounted as /media/ipod, /media/ipod-1 and /media/ipod-2. The problems is that the assignment of mount points to partitions are done randomly. Sometimes /dev/sdb2 is mounted on /media/ipod, sometimes on /media/ipod-2 and so on.

```
/dev/sdb3 on /media/ipod type ext2 (rw,noexec,nosuid,nodev)
/dev/sdb4 on /media/ipod-1 type ext2 (rw,noexec,nosuid,nodev)
/dev/sdb2 on /media/ipod-2 type vfat (rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)

```

Is the any way to force the system to always automount the partitions in the same order?

---

### Post by qpieus on 2006-09-05
Yes there is a way. See the howto called  "Create your own udev rules to control removable devices"

[http://ubuntuforums.org/showthread.php?t=168221]("http://ubuntuforums.org/showthread.php?t=168221")

Good luck! I want to try this too, but haven't got around to it yet....

---

### Post by hanzomon4 on 2006-09-06
Yes, it worked thanks.

---

### Post by qpieus on 2006-09-06
You're welcome. I'll have to give it a try, I have 2 external HDs that I could use this on.

---

