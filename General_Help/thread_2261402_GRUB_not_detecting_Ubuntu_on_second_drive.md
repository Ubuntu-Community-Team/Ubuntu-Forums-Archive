---
title: "GRUB not detecting Ubuntu on second drive"
date: 2015-01-18
forum: General Help
---

### Post by Saint_PDT on 2015-01-18
So, I have a laptop with EFI bios. It has two drives. I had windows 8 on one and then installed Ubuntu on the second. Had no problems for a long time. Decided to get rid of Windows 8 and do a physical install of Kali on that drive. Well, GRUB failed during the Kali install and I couldn't boot into either drive. I formatted the Kali drive (via Kali live) so that a MBR could be created and changed from EFI to legacy boot in bios. Reinstalled Kali and all went well, GRUB installed fine, and I can boot into Kali with no problems.

When I do update-grub, it only detects Kali. Gparted shows the Ubuntu partition on /dev/sdb (Kali is in /dev/sda), but I can't mount them for whatever reason. Any ideas?

---

### Post by yancek on 2015-01-18
Try running sudo os-prober before running sudo update-grub.  Also, with both drives attached, post the output of:  sudo parted -l

---

### Post by grahammechanical on 2015-01-18
> [COLOR=#000000]changed from EFI to legacy boot in bios.[/COLOR]

Could that be the problem? When Windows 8 comes pre-installed on a machine with a UEFI boot system then windows 8 is installed in EFI mode. And that means that Ubuntu has to be installed in EFI mode. And perhaps it was because as you say there were no problems. That is until you removed Windows 8 and installed Kali in legacy (BIOS) mode.

Can you not use UEFI to boot the second hard disk and load Ubuntu? If you can get into Ubuntu that way then from Ubuntu run

```
sudo update-grub
sudo grub-install /dev/sdb
```

and use the UEFI to give sdb the boot priority. You may then find that the Ubuntu Grub does not see Kali.
> 

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[/FONT]
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by Saint_PDT on 2015-01-18
Sudo os-prober doesn't return anything.

output from sudo parted -l is

> root@Kali:~# sudo parted -l
Model: ATA TOSHIBA THNSNJ12 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   128GB  128GB  extended
 5      257MB   128GB  128GB  logical


Model: ATA WDC WD7500BPKX-2 (scsi)
Disk /dev/sdb: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  538MB  537MB  fat32              boot
 2      538MB   794MB  256MB  ext2
 3      794MB   750GB  749GB


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/Kali-swap_1: 5222MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  5222MB  5222MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/Kali-root: 123GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  123GB  123GB  ext4



Also, the output from sudo grub-install /dev/sdb gives me this..

> root@Kali:~# sudo grub-install /dev/sdb
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: error: embedding is not possible, but this is required for cross-disk install.



---

### Post by yancek on 2015-01-18
Grahammechanical was spot on.  You have  GPT partitioning with UEFI for your windows 8 so you need to install Ubuntu in UEFI mode.  You might check the link at the bottom of his post.  I don't use UEFI so can't help with it.

---

