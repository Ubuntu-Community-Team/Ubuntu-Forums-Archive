---
title: "[SOLVED] Drives on Desktop at boot up"
date: 2008-06-18
forum: General Help
---

### Post by McTek on 2008-06-18
I just installed 8.04 and I want the other partitions to appear on the Desktop when I boot. How do I do that?
It did it in 7.10 out of the box.

---

### Post by etnlIcarus on 2008-06-19
> **McTek said:**
> I just installed 8.04 and I want the other partitions to appear on the Desktop when I boot. How do I do that?
It did it in 7.10 out of the box.I noticed the same thing. For manual setup of NTFS partitions, read [this](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G). For more manual fstab configuration, read [this](https://help.ubuntu.com/community/Fstab).

For example, I've added these two lines to my fstab:
```
/dev/sdc1	/media/shared_drive	vfat	iocharset=utf8,umask=000	0	0
/dev/sdb1 /media/windows_drive ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

Depending on the partitions you want mounted, you could probably use something very similar.

---

### Post by McTek on 2008-06-25
See thread at: [http://ubuntuforums.org/showthread.php?p=5262677#post5262677](http://ubuntuforums.org/showthread.php?p=5262677#post5262677)
This solved it for me.

---

