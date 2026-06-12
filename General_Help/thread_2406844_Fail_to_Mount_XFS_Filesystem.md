---
title: "Fail to Mount XFS Filesystem"
date: 2018-11-26
forum: General Help
---

### Post by Ryupower on 2018-11-26
Hey!
Please move this if it is in the incorrect location.

Today, I tried mounting an XFS partition and I was shocked. I was told that it can't read XFS.

As far as I can remember, XFS is a Posix filesystem, and I think even Ubuntu can even be installed on it. So why on Earth would I be getting this?
Screenshot here.

---

### Post by deadflowr on 2018-11-26
> Please move this if it is in the incorrect location.
Done
*Thread moved to **General Help***

---

### Post by MoebusNet on 2018-11-27
I think it is possible that your partition was not properly dismounted last time you used it, leading to file system corruption. I've had this happen to me on JFS partitions before, so the same proinciple would seem to apply. You can repair the file system from terminal with the partition _dismounted_. This should tell you how: [http://manpages.ubuntu.com/manpages/trusty/man8/xfs_repair.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/xfs_repair.8.html)

Example: ```
xfs_repair /dev/sdb3
```

---

### Post by SeijiSensei on 2018-11-27
XFS proved remarkably fragile when I last tried it. For instance, power outages would leave the filesystem in a state of disrepair.  Only after running xfs_repair could I remount the file system, and every time this happened I experienced a loss of data.  I just use ext4 these days.

---

