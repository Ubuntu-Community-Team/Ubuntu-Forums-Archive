---
title: "Computer doesn't boot anymore after boot repair (unable to mount root, kernel panic)"
date: 2017-07-13
forum: General Help
---

### Post by elolitta on 2017-07-13
[COLOR=#111111][FONT=Ubuntu]I previously installed Ubuntu Mate on my Lenovo X201 using a USB-stick that I got from a friend. Ubuntu was running well but after the installation I couldn't boot anymore into Windows 10 (basically it went into an infinite loop when I entered my password). I tried to fix this error following the instructions provided here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) (2nd option). 
However, now I can't boot my computer at all - not into windows nor ubuntu - and I get this:
[/FONT][/COLOR]> [INDENT][FONT=inherit]GNU GRUB version2.02~beta2-36ubuntu3.9[/FONT]
[FONT=inherit]Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions[/FONT]
[/INDENT]

[COLOR=#111111][FONT=Ubuntu]I tried changing the boot mode from diagnostics to quick and I clicked "load setup defaults" in the BIOS setup utility - didn't help.


If I select the USB-stick in the boot menu and try to boot from there I get automatically:[/FONT][/COLOR]> [INDENT][FONT=inherit]Missing parameter in configuration file. Keyword: path[/FONT]
[FONT=inherit]gfxboot.c32 not a COM32R image[/FONT]
[/INDENT]

[COLOR=#111111][FONT=Ubuntu]I typed "live" as suggested in another thread but then I get this and the computer doesn't react anymore afterwards.
Picture: [https://drive.google.com/open?id=0B8Brt06Ux5w-SVF3QlFxdFdGMkk](https://drive.google.com/open?id=0B8Brt06Ux5w-SVF3QlFxdFdGMkk)
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Still very new to ubuntu and slowly getting to know all the terminology, please bear with me.

[/FONT][/COLOR]

---

### Post by oldfred on 2017-07-13
UEFI or BIOS install?
If Windows 10 pre-installed then Windows would be UEFI and then best to boot Ubuntu in UEFI boot mode.
But your error is an old error from syslinux which is the BIOS boot mode bootloader on the flash drive.
Your flash drive has two ways to boot from UEFI boot mode, one UEFI and one BIOS and you need to boot in UEFI boot mode. How you boot Ubuntu live installer, is then how it installs UEFI or BIOS.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

For more info on UEFI installs see also link below in my signature.

---

### Post by elolitta on 2017-07-20
I'm not sure.. as described above I can't really get any further than the BIOS setup utility.. when I want to boot the USB I eventually get the error [FONT=Ubuntu]"...Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(2,0)"[/FONT] [https://drive.google.com/open?id=0B8Brt06Ux5w-SVF3QlFxdFdGMkk](https://drive.google.com/open?id=0B8Brt06Ux5w-SVF3QlFxdFdGMkk)

I actually think that this article describes the issue: [https://wiki.gentoo.org/wiki/Knowledge_Base:Unable_to_mount_root_fs](https://wiki.gentoo.org/wiki/Knowledge_Base:Unable_to_mount_root_fs)
But I don't really understand the resolution: 
> open the kernel configuration: 
root #make menuconfig


---

### Post by oldfred on 2017-07-20
Did you verify down load of ISO was correct?
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 

And some have issues with one installer and another works, or with one flash drive and another works. Or even with different ports on system.


 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 

      
 pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
USB flash drives Pendrive lifetime sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

### Post by jsmolka on 2017-07-22
> **elolitta said:**
> ...boot the USB I eventually get the error [FONT=Ubuntu]"...Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(2,0)"[/FONT]

There might be a solution for your USB stick ... 
Have a look at: [Kernel panic on flash drive]("https://ubuntuforums.org/showthread.php?t=2366670&p=13668646#post13668646")

Then you can go from there.

---

### Post by oldfred on 2017-07-22
If syslinux error, you should be able to press tab.

[https://askubuntu.com/questions/486602/ubuntu-14-04-lts-live-usb-boot-error-gfxboot-c32not-a-valid-com32r-image](https://askubuntu.com/questions/486602/ubuntu-14-04-lts-live-usb-boot-error-gfxboot-c32not-a-valid-com32r-image)

But error related to creating flash drive from older version of Ubuntu with older syslinux and newer install version expecting newer syslinux. Details in link above.

---

