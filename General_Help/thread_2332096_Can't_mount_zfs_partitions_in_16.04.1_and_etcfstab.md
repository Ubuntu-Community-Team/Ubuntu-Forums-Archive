---
title: "Can't mount zfs partitions in 16.04.1 and /etc/fstab"
date: 2016-07-28
forum: General Help
---

### Post by anewbie on 2016-07-28
I have two sets of zfs mount points; the regulars one mount ok (and early in boot process since /home is zfs partition); but the ones that are specified in /etc/fstab will not mount. There is an error which is something like zfs is not a legal file system (i think when /etc/fstab is process mod zfs has not yet been loaded).
-
Anyway I simply do not know enough about the initram process (or init boot process) well enough to debug this issue. Prior to 16.04.1 update this morning (it was a fresh install) I had been using zfs under 14.04.x via external ppa and that method had worked fine (with 16.04 i'm using zfsutils-linux and zfs-initramfs packages.

Appreciate any suggestions to resolve this issue.

---

### Post by anewbie on 2016-07-31
I should have noted that one of the reason the mount points were legacy is that I have to export one of the mount points after the mount (via bind). I suppose i could change them but the bind mount would still fail if the zfs volumes are not mounted by the time fstab is processed. Is there any method to fix this mess other than reverting to 14.04.x ?

---

