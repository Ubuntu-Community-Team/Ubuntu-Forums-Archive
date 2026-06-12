---
title: "Need to Uninstall 16.04 LTS from Desktop Leaving only Win10"
date: 2018-01-14
forum: General Help
---

### Post by vector3 on 2018-01-14
[FONT=century gothic]My department head chose to have me use a laptop and he placed the order for it last week.  My desktop was just returned to me by IT configured with a Win10 Ubuntu 16.04 LTS.  My department head wants to re-purpose my desktop because it is still under warranty.  I would like to do him a favor in a timely manner and remove all traces of the Ubuntu and leave only Win10 as this is what he prefers to use for the instructor PC's.  To that end, I prepared a bootable USB with the i386 16.04.3 LTS desktop  earlier today.  I suspect uninstall is a simple menu selection I can make after running the LiveUSB.

If you need additional information regarding the desktop I can get that and add it to this thread in the morning.
[/FONT]

---

### Post by oldfred on 2018-01-14
If Windows 10 was pre-installed, it will be UEFI. And your i386 32 bit version will not work or may cause issues.
Only use 64 bit versions with UEFI systems.

Make sure Windows 10 fast start up is off.
Use Linux tools for Linux and Windows tools for Linux.

First change UEFI boot order to make Windows default.
Manually boot 64 bit Ubuntu in UEFI mode and use gparted to remove Ubuntu partition(s).
Use efibootmgr on Ubuntu live installer's terminal to remove UEFI boot entry for Ubuntu.
And remove /EFI/ubuntu folder from ESP - efi system partition.
Then use Windows tools to expand NTFS partition.

 Uninstall Ubuntu from menu, Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi) 


        # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[URL="http://software.intel.com/en-us/articles/efi-shells-and-scripting/"]http://software.intel.com/en-us/articles/efi-shells-and-scripting/

[/URL]
 How To Remove Ubuntu From A Computer Dual Booting With Windows 10
[http://www.everydaylinuxuser.com/2016/04/how-to-remove-ubuntu-from-computer-dual.html](http://www.everydaylinuxuser.com/2016/04/how-to-remove-ubuntu-from-computer-dual.html)
Delete /EFI/ubuntu folder from Windows
[http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/](http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/)
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)
[http://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader/497720?noredirect=1#comment1369050_497720](http://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader/497720?noredirect=1#comment1369050_497720) 

[URL="http://software.intel.com/en-us/articles/efi-shells-and-scripting/"]
[/URL]

---

### Post by vector3 on 2018-01-15
[FONT=comic sans ms]I was unable to boot this desktop initially.  Motherboard was replaced yet, when desktop was returned to me I still observed a message indicating no video signal was detected.  The video adapter between the VGA connector and Dell's proprietary version of HMDI was also found to be bad.  I was told Win7 was on the drive previously yet, cannot confirm this.  Regardless, I created a bootable USB drive with the 64-bit iso image and Rufus after seeing your response.  I made the bootable USB for legacy and UEFI.  This means I will have to create a second bootable USB for my Core i5-760M (?) 2.67 MHz runnning Win7 Pro.

I will examine settings in UEFI and note them prior to beginning.  I took a preliminary look at the ask ubuntu reference you provided and it looks useful.  I will post additional questions if needed before beginning this exercise.

Thank you for your help.
[/FONT]

---

### Post by oldfred on 2018-01-15
If you create a standard flash drive image of Ubuntu it will boot in either UEFI or BIOS boot mode. It just is some tools do not create a correct configuration.
And then whether you install in UEFI or BIOS boot mode depends on how you boot from UEFI/BIOS boot menu. New UEFI systems will offer two boot options for Ubuntu, one UEFI:flash and the other flash (BIOS) where flash is name or label of flash drive.

All Intel i5 versions used UEFI based motherboards, but older ones may not have best UEFI. Make sure you have latest UEFI/BIOS from vendor.
And most Windows 7 installs were BIOS even on newer UEFI hardware.  A few were UEFI (64 bit only), but had to have UEFI secure boot off.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

