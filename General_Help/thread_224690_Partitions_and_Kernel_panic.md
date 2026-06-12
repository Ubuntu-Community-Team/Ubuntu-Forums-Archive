---
title: "Partitions and Kernel panic"
date: 2006-07-28
forum: General Help
---

### Post by Steven_B on 2006-07-28
A while back, I installed Ubuntu a second time in a new partition.  Along the way, I added an extended partition, and two partitions inside that.  I also removed my swap partition.  Both partitions are running Dapper with the K7 kernel.  The original boot now gets a kernel panic:
```
Attempt to access beyond end of device
hda2: rw=16, want=8, limit=2
Kernel panic - not syncing: I/O error reading memory image
```
Copying the new kernel files (in /boot) allows me to boot on the old partition, so I'm pretty sure it's a problem with the way the kernel is set up.  Unfortunately, whenever I upgrade the kernel, I have to re-copy the files.
I'm guessing that I need to re-configure and re-compile the kernel.
Looking at this thread [http://ubuntuforums.org/showthread.php?t=136966]("http://ubuntuforums.org/showthread.php?t=136966")
, it looks like the disappearance of the swap partition is the problem.
What configuration settings do I need to change?  If I upgrade the kernel, will it use the fixed configuration?

---

### Post by philippe_carlo on 2006-07-28
Is the swap partition correctly listed in /etc/fstab? I.e., when changin the swap partition, did you reflect that in /etc/fstab?

---

### Post by Steven_B on 2006-07-29
The swap partition is commented out in fstab.  Changing only the files in /boot allowed me to boot, so it is something wrong with the kernel configuration.

---

### Post by Steven_B on 2006-08-01
There's a kernel update in the repositories, and I'd like to not go through copying the kernel again.  How do I tell the kernel not to look for a swap partition?

---

