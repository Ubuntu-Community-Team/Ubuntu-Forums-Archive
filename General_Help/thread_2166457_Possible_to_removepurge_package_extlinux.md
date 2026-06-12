---
title: "Possible to remove/purge package extlinux?"
date: 2013-08-09
forum: General Help
---

### Post by byrongibson on 2013-08-09
The package *extlinux* is only partially installed on my system (12.04 x64 desktop), and due to errors related to that, it is blocking the daily upgrades of all other packages.  

I'm not sure how I got *extlinux*, but think it might have been when I installed *unetbootin* recently to make a backup USB, but no sure.  

It sounds like a required system package, but looking at it in Synaptic it does not have the Ubuntu logo by it, so I'm guessing it's safe to uninstall, but just want to verify before I try.

---

### Post by ian-weisser on 2013-08-09
```
$ apt-cache show extlinux
[...]
Description: collection of boot loaders (ext2/3/4 and btrfs bootloader)
 SYSLINUX is a collection of boot loaders which operates off Linux ext2/3/4 or
 btrfs filesystems, MS-DOS FAT filesystems, network servers using PXE firmware,
 or from CD-ROMs.
 .
 This package contains the ext2/3/4 and btrfs bootloader.


$ apt-cache rdepends extlinux
extlinux
Reverse Depends:
  unetbootin
[...]
```

Extlinux is indeed a dependency of unetbootin.

However, your much bigger problem seems to be the conflict that let to a partial upgrade. Partial upgrades are rarely desirable.
Backup your data.

Post the contents of your /etc/apt/sources.list, file plus the contents of each file in your /etc/apt/sources.list.d directory.

---

