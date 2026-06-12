---
title: "Dual-boot Ubuntu 14.04 and Windows 8.1 on EFI system AND edit boot menu from Windows"
date: 2014-06-07
forum: General Help
---

### Post by Only1KW on 2014-06-07
I am trying to install Ubuntu on my system which already has Windows 8.1 installed and UEFI enabled.  I can install it (assuming I use the desktop version; the minimal installation fails to boot) and now have Grub installed which allows me to pick which OS I want to boot into.

Here is what I'd like to do: In some cases I need to give my system to others to use.  In those cases, I want my system to automatically boot to Windows without the user being aware Ubuntu is also installed, but then undo that when the system is returned to me.  It's easy enough to set Windows as the default option in Grub and set the timeout to zero, but how do I recover afterwards?  I'd prefer not to have to have a dedicated flash drive lying around for this purpose nor do I want to have to rebuild one every time I want to change it back.  I can't find a way to edit ext# partitions reliably from Windows 8.  Ubuntu won't allow me to create a /boot partition on a fat32 partition.  Ubuntu doesn't seem to be able to boot from the Windows 8 boot loader.  Any ideas on what I can do in this scenario?

---

### Post by oldfred on 2014-06-08
If UEFI, you can change boot order in UEFI. Then Windows boots.

Better UEFI let you reset boot order in UEFI menu.

Or you should be able to access efi directly.

This was to delete an entry but you can also reset boot order. See links:
 # from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

But if dual booting, you should always have a working repair DVD or flash drive for the current version of every operating system you have installed. Or a Windows repair flash drive and a Ubuntu live installer.

---

### Post by Only1KW on 2014-06-09
Sorry, I'm not sure I understand what you're recommending.  I understand I can change boot order in UEFI, but I am unable to make entries for both Windows and Ubuntu in UEFI.  Targeting and booting the EFI partition starts grub, and if I target and boot any other partition on the hard drive, the boot fails.  That still doesn't give me a way to automatically start Windows.

---

### Post by oldfred on 2014-06-09
Post link to BootInfo report.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

