---
title: "Reinstalling windows - gonna loose grub?"
date: 2007-08-29
forum: General Help
---

### Post by phillips321 on 2007-08-29
hi guys,

Bout to reinstall WinXP to my winblows partition, (i only use it for games).

I know that after a reinstall i will loose my grub boot loader.

How do i go about making sure that i can get it back? I dont want to over write my current menu.lst file.

Cheers

here's my partition table
```

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux (mounted /boot)
/dev/sda2              14         140     1020127+  82  Linux swap / Solaris (mounted swap)
/dev/sda3             141        3787    29294527+  83  Linux (mounted /)
/dev/sda4            3788       20023   130414592    7  HPFS/NTFS (mounted /media/windows)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19458   156288000    7  HPFS/NTFS (mounted /media/data)


```

---

### Post by merlinus on 2007-08-29
Reinstalling xp will not overwrite any linux files, and if necessary you will be able to reinstall grub without difficulty, either from the live cd or using supergrub.

-merlin

---

### Post by jamvegan on 2007-08-29
A how-to for you: [Recovering Ubuntu after installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"). :-)

---

