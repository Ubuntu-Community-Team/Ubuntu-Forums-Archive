---
title: "remount ntfs partitions in read only mounting fails"
date: 2015-05-25
forum: General Help
---

### Post by kumareshy on 2015-05-25
Hello everybody,
       I have a very specific problem. I dual boot Ubuntu 14.10 and windows 8.1. Sometimes my parents hibernate windows and when I open Ubuntu, I set it to automatically mount my windows NTFS partitions, including the OS drive. But Ubuntu fails to mount my windows partition when it's hibernated. If I want to mount the partition, I have to manually set it to mount in read only mode. Is there any way to set it to automatically mount the drive in read only mode if it doesn't mount at first and gives some error message. This is the default option for the root drive of Ubuntu, i.e. ```
errors=remount-ro
```, but the same option does not work when I try it on the windows NTFS partitions in fstab.

---

