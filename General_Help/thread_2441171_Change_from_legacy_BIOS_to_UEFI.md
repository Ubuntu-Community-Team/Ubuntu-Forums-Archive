---
title: "Change from legacy BIOS to UEFI"
date: 2020-04-20
forum: General Help
---

### Post by habana on 2020-04-20
My ubuntu only computer has GPT partitioning but legacy BIOS. There is a separate partition (1 MiB) with a bios_grub flag labelled as grub2core.img. My newish Gigabyte Mobo is set to allow Legacy BIOS. I wish to update the system to UEFI. 

[https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295) by oldfred advises the following:  Boot-Repair will convert a BIOS install to UEFI by uninstalling grub-pc, and installing grub-efi-amd64, if gpt partitioned.

I have installed and run boot-repair but there is no option to install the efi file. I assume this is because I am obviously running in legacy mode.

Am I right in thinking that i have to use a live usb booted in UEFI mode to do what I want to do? Will boot-repair recognize the boot partition and modify it accordingly?

---

### Post by CelticWarrior on 2020-04-20
You need an EFI partition, a small FAT32 formatted partition with the proper boot flags.

---

### Post by rbmorse on 2020-04-20
Honestly, it's easier and probably quicker to just backup your /home and other userdata and perform a fresh install of the O/S, especially if you have to resize the system partition to create space for the EFI partition (256 mb is more than enough).  Don't forget to delete (or at least remove the flags) the existing boot partition. You can only have one on a given physical drive.

---

### Post by oldfred on 2020-04-20
You missed the part that says you have to have an ESP - efi system partition.
FAT32 anywhere from Windows 100MB which is a bit small to 500MB anywhere in first 2TiB, but often as first or second partition.

Then Boot-Repair will when booted in UEFI mode let you uninstall & reinstall grub.
If you have the ESP, you can run a grub install command to install in UEFI boot mode. But if it errors out then system will probably not be bootable & you need an Ubuntu live installer to make repairs.

---

### Post by CelticWarrior on 2020-04-20
> **rbmorse said:**
> Honestly, it's easier and probably quicker to just backup your /home and other userdata and perform a fresh install of the O/S, especially if you have to resize the system partition to create space for the EFI partition (256 mb is more than enough).  Don't forget to delete (or at least remove the flags) the existing boot partition. You can only have one on a given physical drive.

+1

A fresh installation is also safer. As long as one has backups, it's always preferable to install new.

---

### Post by habana on 2020-04-20
Thanks everybody. I'd missed the bit where the EFI partition is so much bigger than the old BIOS partition. I will do a clean install of 20.04 next week - it is running well on an old PC. I have backups of the backups of the backups!

---

### Post by habana on 2020-04-22
Just a postscript to the above. I created an ESP with gparted. did a fresh install of 20.04 and my system now uses efi. All good.

---

