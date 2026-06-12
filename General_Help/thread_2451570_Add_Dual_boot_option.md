---
title: "Add Dual boot option"
date: 2020-10-06
forum: General Help
---

### Post by shepardofdark on 2020-10-06
Hi, 

I have a windows system with ubuntu 20.04 dual boot. After upgrading from 18.04 to 20.04, I switched to windows and was not able to go back to ubuntu. Things got worse when both OS corrupt and no bootable devices were recognized. I restored BIOS to its default setting, and now the boot option for ubuntu is gone. The partitions are still there, and the grubx64.efi is still there. 

What should I do?

---

### Post by oldfred on 2020-10-07
Windows runs updates when you reboot into it after a while.
It often turns fast start up back on which sets hibernation flag and prevents Linux NTFS driver from seeing NTFS partitions.

Windows in BIOS mode, is known to rewrite partition tables on major changes and "forgets" to include Linux logical partitions as it does not correctly see them. Partition is still there, but has to be restored to partition table.

Windows with some systems will also update UEFI and reset UEFI to defaults. You need to confirm if the settings you originally changed like fast boot, AHCI, and others are still the same. My motherboard needs 5 to 7 settings redone after every UEFI update, but I do that myself and have a list of settings to redo.

If only UEFI entry missing, you can use efibootmgr from live installer to add entry. If other boot issues often easier just to totally reinstall grub either chroot or Boot-Repair. If partition issues then other tools required.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

