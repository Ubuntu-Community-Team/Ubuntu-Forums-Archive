---
title: "What is the suggested EFI system partition size for extreme future proof?"
date: 2023-08-27
forum: General Help
---

### Post by drugdoubles on 2023-08-27
Seem like different Linux distro has very difference answer, from like 100mb to like 500mb for now. Look like it would be even larger in future. What is your suggestion for future proof while I don't care using more MB for this? Thx!

---

### Post by Rubi1200 on 2023-08-27
Doesn't it depend on your system setup and/or future installation plans?

The ArchWiki has excellent information on the subject: [https://wiki.archlinux.org/title/EFI_system_partition](https://wiki.archlinux.org/title/EFI_system_partition)

---

### Post by #&amp;thj^% on 2023-08-27
> **Rubi1200 said:**
> Doesn't it depend on your system setup and/or future installation plans?

The ArchWiki has excellent information on the subject: [https://wiki.archlinux.org/title/EFI_system_partition](https://wiki.archlinux.org/title/EFI_system_partition)

+1
For myself I use a few different sizes, just depends on what I use **that system for ie:
```
sudo fdisk -lu|grep -i efi
[sudo] password for me: 
/dev/nvme0n1p1    2048   1050623   1048576  512M EFI System
/dev/nvme1n1p1     2048   2099199   2097152     1G EFI System
/dev/sda1     2048    249855    247808   121M EFI System
/dev/sdc1     2048   1050623   1048576   512M EFI System

```
This one is rather small for my use but i push it when needed>>" 121M EFI System"
I have had no issues with using this size>> "1G EFI System" in testing and used for back-ups. (Not recommended for newer users)

---

### Post by MAFoElffen on 2023-08-27
I think I have done over 15,000 Linux OS, and over 20,000 Windows OS installs now... plus other OS'es... On various platforms. (Yes, even installed Linux on Win Mobile phones. LOL)

I typically create EFI partitions of 500Mib to 750 MiB. 

The efi boot files are 'very small' in size. You don't get into anything of consequence until you start installing EFI applications, such as Memtest86+ (64bit and some vendors UEFI BIOS utilities. For those, I started bumping up some EFI partitions to 1GiB.

EFI partitions are formatted as vfat, aka FAT32... So eventually you will hit the limits of that filesystem (4GB file limit, 32GB partition limit). I have never created an EFI partition larger than 1GB.

As I see it, (which is more liberal than most) you can make it as large as you want within the limits of the filesystem... But why make it 'largest' when it is not going to use much of that at all, ever.

You increase the fsused% as you add more OS'es and instances of those OS'es... For example 3 installs of Windows OS releases and editions, and 3 installs of various releases or editions of Ubuntu... and it is still very little there.

---

