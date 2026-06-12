---
title: "Why is Grub used for choosing boot preference?"
date: 2014-02-25
forum: General Help
---

### Post by Blakeo on 2014-02-25
I remember when I did it on my old computer using old Ubuntu like version 10.10 it used to use the bios to choose between the bootloader.
Now it uses Grub by Ubuntu? Is there anyway to change it. Gives windows a strange name: windos.83293.ufi.loader.

---

### Post by grahammechanical on 2014-02-25
You are mistaken. I have been using Ubuntu since 7.04 and it was using Grub as a boot loader before then. We need a boot loader. The BIOS will at the most allow us to change which drive we boot from. It will not load an OS. It cannot do that on my machine. I need some kind of boot loader and in Ubuntu it is Grub (Grand Unified Bootloader).

You seem to now be using a machine with UEFI as the boot system instead of BIOS. It is my guess that you will find that even the UEFI boot system does not load an OS. Windows is loading because there is a Windows boot loader and the UEFI setting is pointing to the Windows boot loader. But a Windows boot loader will not load a Linux OS. So we need the Grub boot loader that will load Ubuntu and also point to the Windows boot loader so that we can load Windows.

Regards.

---

### Post by oldfred on 2014-02-25
Grub has always been both a boot manager (what system to boot) and a boot loader for Linux systems.
BIOS used to let you switch boot drives if you had more than one drive, but always booted from the MBR of that drive. 

The new UEFI is also a boot manager in that every system installs boot files into the efi partition and UEFI lets you choose which to boot. Somewhat like a mulitple drive configuration with BIOS.

But UEFI also now complicates installs as you can still install in the old BIOS mode also. And many users do not know that or how to know which mode they are in.

Some UEFI allow you to change the labels of what you are booting.
       Query to see if UEFI or BIOS
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

            # from live CD and use efibootmgr to list boot options in UEFI
sudo efibootmgr -v

    
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
change label
[http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr](http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr)

---

### Post by buzzingrobot on 2014-02-25
When a PC is restarted, the last task performed by the BIOS is to hand over control to a bootloader. Because a BIOS does not know what operating systems are installed, it expects this bootloader to be located at specific place on the drive. Whatever is there gets control.  That bootloader, then, is a small program whose job is to trigger the launch of the OS.

---

### Post by Blakeo on 2014-02-25
Thanks guys for the help, I understand now :)

---

### Post by mörgæs on 2014-02-26
Good, please read Oldfred's footnote.

---

