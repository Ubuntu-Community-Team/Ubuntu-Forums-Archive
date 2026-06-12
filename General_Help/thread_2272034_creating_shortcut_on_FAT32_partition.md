---
title: "creating shortcut on FAT32 partition"
date: 2015-04-03
forum: General Help
---

### Post by mephisto56 on 2015-04-03
I have created a shortcut on a FAT32 partition to the terminal opening vim with some options. But it's on a windows partions and I seem not to be able to mark it as trusted. When I try to open it the message reads 'untrusted application launcher'. How can I solve this? I already know I can move the shortcut to a linux partition so I'm hoping to learn the solution for a windows partition.

---

### Post by Mark Phelps on 2015-04-03
Windows filesystems don't handle Linux filesystem permissions.  Also, if this FAT32 partition is a really small one at the start of the drive, and your PC came with Windows preinstalled, you're most likely messing around with the Windows boot partition -- NOT a good idea if you want to continue to boot Windows.

---

### Post by mephisto56 on 2015-04-05
> **Mark Phelps said:**
> Windows filesystems don't handle Linux filesystem permissions.  Also, if this FAT32 partition is a really small one at the start of the drive, and your PC came with Windows preinstalled, you're most likely messing around with the Windows boot partition -- NOT a good idea if you want to continue to boot Windows.

Mark don't worry it is not the boot partition :) If it can't be done then so be it but maybe there was an option somewhere/somehow outside of the FAT32 partition to mark this particular file as "safe".

---

