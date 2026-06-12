---
title: "Ubuntu overwrote all boot devices in BIOS!"
date: 2013-10-10
forum: General Help
---

### Post by MeMo_oMeM on 2013-10-10
This is really weird. I decided to take a clonezilla backup but could not make the USB-key image appear in the boot menu. Then I tried again with an external DVD drive, which also did not work. 

I also installed and ran "boot-repair", which did not change anything. 

I only see 3 "ubuntu"s in the boot device menu:

1. ubuntu
2. ubuntu
3. ubuntu 

I checked my BIOS settings and the boot device order also appears to include 3 entries that say ubuntu. None of my USB keys or external drives appear in the menu. I don't see any hard drive option too. Just Ubuntu.

I am really worried right now. I have to send the laptop out for a repair (very soon) and I cannot even get a backup. I also fear a scenario that I will not able to install/restore *anything* from now on. I hope this is not the case.

How come ubuntu writes on the BIOS and change its settings?? Which mechanism does that?

I will appreciate any suggestions to fix this. I already tried boot-repair and installed refit, but nothing was changed.

Thanks!

---

### Post by oldfred on 2013-10-10
Ubuntu does not write to BIOS.
But UEFI does read what systems to boot and adds them to its own memory. Do you have UEFI?
If you have UEFI and turn secure boot on, only secure boot systems will be shown in menu.
Some systems require a password to turn off secure boot.
       
Query to see if UEFI or BIOS
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

some systems have this - built in UEFI shell:

 Enter your UEFI menu, select "Boot maintenance manager", then "Boot options",

Others need shell lauched in terminal like mode.

 # from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

   [https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)
EFI/boot/bootx64.efi.efi" ---> Brings up 'EFI shell environment' with command prompt.

---

