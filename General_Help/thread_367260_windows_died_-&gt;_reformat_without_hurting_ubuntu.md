---
title: "windows died -&gt; reformat without hurting ubuntu install"
date: 2007-02-21
forum: General Help
---

### Post by harty83 on 2007-02-21
It seems that my windows installation has crashed so I need to reformat and reinstall.  How can I safely do this without hurting my ubuntu installation.

Here is a breakdown of my harddrive:
```
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20971520+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            2612        5833    25880715   83  Linux
/dev/sda3            5834        6081     1992060   82  Linux swap / Solaris
/dev/sda4            6082        7297     9767520    b  W95 FAT32

```

I guess reformatting will not hurt ubuntu, but rather grub.  Any suggestions on how to preserve grub with little worry of jacking up my system?

Thanks!

---

### Post by g3k0 on 2007-02-21
Reinstall windows then do this.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

