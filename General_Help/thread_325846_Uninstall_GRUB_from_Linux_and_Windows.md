---
title: "Uninstall GRUB from Linux and Windows"
date: 2006-12-26
forum: General Help
---

### Post by Octarine on 2006-12-26
Ive somehow, by trying to fix an error in GRUB, got GRUB installed to both my Windows drive, and my Linux partition on a second drive.
I need help on how to uninstall GRUB so I can install a different bootloader, from both hard drives.

Setup is as follows:

Hda1 - 29Gb Windows NTFS

Hdb1 - 210Gb Data NTFS
Hdb2 - 21Gb Linux EXT2
Hdb3 - 500Mb Linux Swap

How Can I:

a) Remove GRUB from my Windows drive
b) Remove GRUb from my Linux Drive
c) Install Bootmagic to replace GRUB using the Linux Live CD.

I am using the ubuntu version of Linux 6.06

---

### Post by kidders on 2006-12-26
If you want to use a different bootloader, just forget grub is even there ... installing a new one should just overwrite whatever you already have.

---

