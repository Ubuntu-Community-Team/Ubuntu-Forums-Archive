---
title: "GRUB in UEFI Boot menu?"
date: 2015-08-03
forum: General Help
---

### Post by michael14 on 2015-08-03
Hi I have ubuntu installed and i am wondering, say if i were to want to remove Ubuntu in the future how would i go about removing GRUB? If i just delete the partitions of linux would it make GRUB bootloader in the UEFI boot menu disappear or would i have to mount the efi partition on windows, and go in and remove it like that or how.. Would it remove itself and would it hurt to just leave it there?

---

### Post by oldfred on 2015-08-03
It probably does not hurt to leave the /EFI/ubuntu folder in the ESP. Or the ubuntu entry in the UEFI boot options.
Probably easier to remove with Ubuntu live installer. 
Details in link in my signature, but just delete ubuntu folder in ESP and use efibootmgr to delete UEFI entry.

---

### Post by michael14 on 2015-08-05
> **oldfred said:**
> It probably does not hurt to leave the /EFI/ubuntu folder in the ESP. Or the ubuntu entry in the UEFI boot options.
Probably easier to remove with Ubuntu live installer. 
Details in link in my signature, but just delete ubuntu folder in ESP and use efibootmgr to delete UEFI entry.

Just wondering but would the recovery disk and command prompt thing doing bootrec /mbr  be the way to restore the bootloader on UEFI computers?

---

### Post by oldfred on 2015-08-05
With UEFI computers the /EFI/ubuntu folder & the /EFI/Microsoft folder are both in the ESP.  So they exist side by side and at any time you an change boot order in UEFI or with efibootmgr. 

You should also have a one time boot key often f10 or f12 but depends on your brand system that has the list of bootable devices directly without having to choose in UEFI.

Fixes are only required if you have corruption or accidentally overwrite something.

Of course good backups including the ESP partition and a repair CD or flash drive for the current version of every system you have installed is required. So keep Ubuntu live installer and make the Windows repair flash drive which you system should have suggested when you first booted.

---

