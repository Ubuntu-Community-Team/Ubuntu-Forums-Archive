---
title: "Why does the file manager show all of my Windows partitions except one?"
date: 2016-11-16
forum: General Help
---

### Post by delerious2 on 2016-11-16
When I boot up my Windows 10 computer using an Ubuntu 16.04 LTS Live CD and  then open the file manager, I can see all but one of my Windows partitions listed at  the bottom of the left pane.  I can see the Windows partition (C drive), the SYSTEM partition, and the HP_TOOLS partition.  However, it does not show the D drive (HP_RECOVERY partition).   I am curious as  to why it doesn't show the HP_RECOVERY partition but it does show all  of the other partitions.

---

### Post by ajgreeny on 2016-11-16
Does gparted on the live system see that "missing" partition?

---

### Post by DuckHook on 2016-11-16
Windows recovery partitions are often recorded in proprietary formats depending on the OEM. I am not familiar with HP's practices, so can only guess that this is also so in your case. Linux will usually be unable to read these proprietary formats and will report the partition as "unknown". Since the file manager is used for manipulating files, there is no point in its reporting a partition that it cannot access, so it doesn't. However, a partition utility like gparted, as suggested by ajgreeny, is designed to manipulate partitions, so it should report this partition even if Linux can't make out its format. It will be reported as "unknown".

gparted is not part of a default install these days and must be installed from the repositories. You could also use the command line utility *parted* instead:```
sudo parted -l
```The -l switch lists all partitions. Please be careful using either gparted or parted. You don't want to inadvertently hose your partition table or delete any partitions.

---

### Post by delerious2 on 2016-11-17
gparted showed the partition (and the hidden flag was not checked).

"sudo parted -l" also showed it, and it was not reported as "unknown" - it was reported as NTFS.

---

### Post by ajgreeny on 2016-11-17
Is it a dynamic partition? Windows often makes those but they are not usable by Linux.

---

### Post by delerious2 on 2016-11-17
It is a basic partition, not a dynamic one.

---

