---
title: "Grub installed to flash drive"
date: 2008-06-25
forum: General Help
---

### Post by Eviltechie on 2008-06-25
I installed xubuntu to a flash drive. It works fine, but grub got installed to my flash drive too. That means I can't use windows without my flash drive. Is there anyway to fix this without reinstalling windows.

---

### Post by cdtech on 2008-06-25
Sure.

What does your sudo fdisk -l show? You can install the GRUB bootloader into the MBR of any bootable disk.

---

### Post by Eviltechie on 2008-06-26
This is what it shows.


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       38914   302027776    7  HPFS/NTFS

Disk /dev/sdf: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cb3e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1         929     7462161   83  Linux
/dev/sdf2             930         977      385560    5  Extended
/dev/sdf5             930         977      385528+  82  Linux swap / Solaris

---

### Post by cdtech on 2008-06-26
If you cannot boot into Windows with your Flash drive disconnected, you'll need to fixmbr on your Windows OS. If you unplug the Flash drive you should be OK to boot into Windows after the fix and plug in the Flash before boot to boot into Linux.

---

