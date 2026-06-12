---
title: "Dual Booting 14.04 LTS Goes Straight to Windows 8"
date: 2014-05-01
forum: General Help
---

### Post by nholloway2007 on 2014-05-01
I'm currently dual booting Windows 8 and Ubuntu 14.04. I would like to boot directly to GRUB and then to Windows, but instead, it boots straight to Windows. In order to get into Ubuntu, I have to tap F9, access my boot options, and boot into Ubuntu that way. It's  annoying because I intend to use Ubuntu far more than Windows.

In order to remedy this, I installed boot-repair to a LiveUSB and ran it. It failed with the following error: [http://imgur.com/P8bvk8J](http://imgur.com/P8bvk8J)

The boot-info summary is posted here: [http://paste2.org/UBxEd2xk](http://paste2.org/UBxEd2xk)

This is the output for "sudo fdisk -l": [http://paste.ubuntu.com/7375197/](http://paste.ubuntu.com/7375197/)

And my fstab is as follows: [http://paste.ubuntu.com/7375302/](http://paste.ubuntu.com/7375302/)

---

### Post by oldfred on 2014-05-01
Some systems only boot Windows and have to have work arounds.
Some like yours seem to just make it difficult as they really only want you booting Windows.

I now see Boot-Repair/grub showing some errors but it still works, not not sure errors apply.

You have ubuntu, can you in UEFI menu make it the first choice?
```
BootOrder: 0001,2001,3005,3001,3002,2002,2003

Boot0000* Notebook Hard Drive
Boot0003* USB Hard Drive - SanDisk
Boot0004* USB Hard Drive (UEFI) - SanDisk
Boot0005* Windows Boot Manager
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3005* Internal Hard Disk or Solid State Disk
Boot0001* [COLOR=#ff0000]ubuntu[/COLOR].


```

A few systems will let you modify directly even though menu in UEFI does not.
Above is form this in your bootinfo report.
 sudo efibootmgr -v

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

      
 **Systems that only boot Windows from UEFI. Often Sony & HP, maybe others**
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.

   Boot_Repair - Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   Some install rEFInd which seems to be another workaround.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

