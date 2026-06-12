---
title: "grub cannot find my Windows 7 installation"
date: 2016-01-01
forum: General Help
---

### Post by necbot on 2016-01-01
Grub cannot find my Windows 7 installation.  I ran ```
sudo grup-update
``` and ```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```, neither one works.  The Windows 7 installation is on one of my three hard drives.  I ran sudo fdisk -l and the output is...


```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   468862127   234431063+  ee  GPT


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00071eec


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907028991  1953513472    7  HPFS/NTFS/exFAT


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x6981befa


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdc2          206848   468858879   234326016    7  HPFS/NTFS/exFAT

```



My Windows installation is on /dev/sdc.  I can go into my bios and boot Windows 7 by selecting this disk as my boot disk so I don't think it is my Windows installation.  Any ideas?

EDIT:
I think I may have figured out my problem, but I still don't know how to solve it.  It seems my Windows installation was installed first using [COLOR=#333333][FONT=Ubuntu] BIOS/CSM/legacy mode and grub looks for  UEFI/UEFI mode.  I noticed that in the BIOS the disk with my ubuntu installation has a UEFI boot entry but the Windows 7 disk does not.  Is there a way to add a non-UEFI disk to grub?[/FONT][/COLOR]

---

### Post by Bucky Ball on 2016-01-01
!

```
sudo update-grub
sudo grub-install /dev/sda
```

... generally does it.

If you have one installed in UEFI and one in BIOS, I suggest you re-install Ubuntu in whatever Windows is installed in. No other way, really. I've heard Boot Repair can convert installs from one to the other but have no experience of doing that. 

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Boot Repair can provide a link to your boot info (there is an option on the first screen). Create the bootinfo and post the link here, please.

---

### Post by leunam12 on 2016-01-02
Is Windows hibernated maybe?

---

### Post by oldfred on 2016-01-03
UEFI and BIOS/CSM/Legacy boot modes are not compatible. Once you start booting in one mode you cannot switch, or grub menu can only boot other systems installed in same boot mode.
Some just use the one time boot key often f10 of f12 when system first starts booting to choose which system to boot.

Boot-Repair can convert an Ubuntu install from UEFI or BIOS if partitioned with gpt and you have correct partitions. For UEFI boot you must have the ESP - efi system partition and for BIOS boot you must have a 1 or 2MB unformatted partition with the bios_grub flag anywhere on the  gpt drive. If you keep efi partition you later can convert back to UEFI.

How you boot install media for both Windows & Ubuntu is how it installs. Or if you boot installer in UEFI mode it installs in UEFI boot mode on hard drive.

Windows 7 default install has been BIOS, but it can be copied to a flash drive and UEFI boot files moved to /EFI/Boot/bootx64.efi to make the Windows 7 installer also boot in UEFI mode.
Microsoft has said they will be updating everyone with Windows 7 or 8 to Windows 10. Or nag you to death if you turn off the update.

---

### Post by Seanan on 2016-01-04
I (before i tried to uninstall Ubuntu and messed my computer up, i did it wrong, lol) installed Ubuntu alongside Windows 8.1 on the same hard drive with Ubuntu desktop, have you tried that? Windows shows up fine in the grub bootloader then fine. If you have data on ubuntu you would want to keep i would suggest putting it on removable media and then removing your ubuntu installation (deleting it should remove the grub bootloader--Note: When deleting ubuntu just be careful not to delete anything else) and then reinstalling it alongside windows on the same hard drive using ubuntu desktop. Also you can make the partition size for ubuntu desktop small and then just put files in the hard drive you uninstalled ubuntu from.

Hope this works for you!

---

### Post by Seanan on 2016-01-05
bump

---

