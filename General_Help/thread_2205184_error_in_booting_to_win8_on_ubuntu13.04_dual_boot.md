---
title: "error in booting to win8 on ubuntu13.04 dual boot"
date: 2014-02-12
forum: General Help
---

### Post by AbhimanyuAryan on 2014-02-12
[COLOR=#000000][FONT=arial] i read from here and found that the only way to boot into windows8 pre-installed is via refind boot manager...i have downloaded this but how to make a flash drive for it? can i straight away copy the img file to a pen drive and when boot options appear on starting screen.....choose boot from usb?
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial] [/FONT][/COLOR]
[COLOR=#000000][FONT=arial]also could please tell me a link to video which i can follow?[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[http://askubuntu.com/questions/335019/unable-to-boot-windows-8-after-ubuntu-installation](http://askubuntu.com/questions/335019/unable-to-boot-windows-8-after-ubuntu-installation)

---

### Post by oldfred on 2014-02-12
What vendor & model? And what video card/chip?

rEFInd is one way to boot, I have not used it but others have posted it works. For some systems with issues it may work a bit better but there are also other work arounds for those systems.
Rod Smith is the author of rEFInd and you show his post & links to his site on rEFInd. He has not liked grub2, but grub2 has been improved a lot.
 Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards](https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards)
Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

Most follow these instructions and get UEFI to dual boot.
      
 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by crazymonkey05 on 2014-02-12
have you tried running without UEFI enabled?

---

### Post by AbhimanyuAryan on 2014-02-12
no how to disable UEFI? i can't boot into windows

---

### Post by oldfred on 2014-02-12
You need UEFI to boot Windows and then should install Ubuntu in UEFI mode. Only a few systems have to have Ubuntu in BIOS boot mode and then you can only dual boot from UEFI/BIOS menu. And you may have to turn on/off UEFI or BIOS/Legacy/CSM boot mode.

---

### Post by crazymonkey05 on 2014-02-19
you should also try and update grub as changing a partiotion in windows can screw up the boot order and cause grub to not see the os i belive the command is > sudo update-grub or sudo apt-get update grub IDK its been awhile since i ran the command.

---

