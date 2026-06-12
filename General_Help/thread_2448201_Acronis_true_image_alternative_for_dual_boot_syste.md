---
title: "Acronis true image alternative for dual boot system"
date: 2020-08-04
forum: General Help
---

### Post by glorsh66 on 2020-08-04
Recently I tried to make a copy of my system (Dual boot - Windows 10 + Ubuntu) using Acronis true image, and I had to rebuild grub. I know it's not a big deal for one time, but what if I need to make a image for installation on several machines. 
What are the best tools that work fine with the dual boot systems?
What features are really essential to me:
- Not include free space into a backup file.
- Hassle free work with the NTFS partitions

I know that there is DD - but I doubt that it will work fine with the NTFS partitions.

---

### Post by CelticWarrior on 2020-08-04
DD works fine with NTFS partitions. Likewise Acronis (Windows) works fine with any type of Linux partitions. Alternatively there's Clonezilla with an easy to use GUI.

Now, regardless of the tool used, it needs to be able to (and have that option explicitly selected) save the bootloader(s) as well as system partitions. Acronis has such option both for BIOS and UEFI systems. Of course, with UEFI, things are much easier, no special options required as long as users explicitly select the ESP (EFI System Partition) alongside with the system(s) partition(s). With BIOS the tool being used needs to be able to save the MBR alongside with the partition(s).

---

### Post by Impavidus on 2020-08-04
dd works fine with ntfs partitions, but always includes the free space in the backup. You can use an image of an installed system to install Ubuntu on a second machine (provided the hardware is sufficiently similar, no proprietary drivers etc.), but I don't think that works with Windows too.

---

