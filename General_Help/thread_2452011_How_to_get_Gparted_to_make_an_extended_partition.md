---
title: "How to get Gparted to make an extended partition"
date: 2020-10-14
forum: General Help
---

### Post by cigtoxdoc on 2020-10-14
Four partitions on HDD.  sda1 is ntfs system reserved. sda2 is ntfs, and sda 4 is ntfs with a flag of msftres and go with Windows 10.  sda3 is ext4, 114 GB with a boot flag.  9.3 GB of it is ubuntu 20.10.

I want to divided sda 3 so that one part of it is for the ubuntu OS and the other two or three parts are for specific classes of files such as normal documents, data files, etc.  I have already done this on the laptop PC I am using where sda3 is an extended partition containing sda 5,6, 7, and 8.

Perhaps I am missing something, but step-by-step documentation seems to be missing.

Thank you,

John

---

### Post by CelticWarrior on 2020-10-14
If sda3 is already a primary partition it would need to be deleted *then *created the extend partition containing the other logical partitions you want in its place.

The avoid such issues we use GPT instead of the 40 years old "msdos" (MBR) partition table. It's an option for you although it implies deleting everything from that drive and reinstalling two OSes, unless you have BIOS and want to keep Windows in which case, due to Windows restrictions, you really need to have MBR for BIOS boot (and GPT for UEFI boot). Ubuntu can be installed in BIOS mode in GPT drives just by adding an unformatted 1MB-2MB "bios_grub" partition at the beginning of the drive.

---

### Post by joniess101 on 2020-10-15
> **CelticWarrior said:**
> If sda3 is already a primary partition it would need to be deleted *then *created the extend partition containing the other logical partitions you want in its place.

Does this work?

---

### Post by CelticWarrior on 2020-10-15
> **joniess101 said:**
> Does this work?

It surely does but obviously will delete Ubuntu.
Perhaps you need to rethink your idea as in such small space it makes no sense.

---

