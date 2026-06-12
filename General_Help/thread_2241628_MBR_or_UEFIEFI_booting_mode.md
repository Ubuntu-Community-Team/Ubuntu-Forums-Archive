---
title: "MBR or UEFI/EFI booting mode?"
date: 2014-08-27
forum: General Help
---

### Post by tegelstom on 2014-08-27
Here is my partitioning scheme, do I boot in MBR or UEFI/EFI mode, and what's the difference between them?
[https://plus.google.com/u/0/photos/112478144887851328209/albums/5736976833890696177/6052266521589486434?pid=6052266521589486434&oid=112478144887851328209](https://plus.google.com/u/0/photos/112478144887851328209/albums/5736976833890696177/6052266521589486434?pid=6052266521589486434&oid=112478144887851328209)

---

### Post by rbmorse on 2014-08-27
You boot in BIOS mode.  For more information on UEFI on PCs, I'd start at:

[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by grahammechanical on 2014-08-27
What version of Windows do you have? And is it installed in UEFI mode? Ubuntu must be installed in the same mode as Windows was installed.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> 
[LIST]
[*=left][FONT=inherit]In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6")(SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[/FONT]
[/LIST]


> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in EFI mode or not.
[/LIST]


> [COLOR=#333333][FONT=Ubuntu]To install Ubuntu in EFI mode:[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit]Use a 64bit disk of Ubuntu ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"))[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]You might want to use an [EFI-only image]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image") to avoid troubles with mistakenly booting the image and installing Ubuntu in BIOS mode. [FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Use a supported version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI[SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2.[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in EFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below)[FONT=inherit][/FONT][/FONT]

[*=left]Then:
[/LIST]


Regards.

---

### Post by tegelstom on 2014-08-27
I use Windows 7 preinstalled on my Toshiba laptop.
Thanks for your replies :)

---

### Post by tegelstom on 2014-08-27
thomas@myUbuntuPC:~$ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 
Legacy boot on HDD
[COLOR=#333333][FONT=Ubuntu]Remark: if the result is "Legacy boot on HDD", then either the BIOS is not UEFI type, or the BIOS is not set up to boot the HDD in UEFI mode.
I guess my Toshiba laptop BIOS is not UEFI type, I did a quick lookup in it and has no such option.
But what is the reason of /dev/sda1(SYSTEM) partition? This was there with the preinstalled Windows7.[/FONT][/COLOR]

---

### Post by rbmorse on 2014-08-27
System Reserved is created by the Windows Installer during both BIOS and UEFI mode installs.  It holds Windows code needed by BCD, the WIndows boot loader and is also used by Bitlocker, the Windows file encryption service. 

If Windows had been installed in UEFI mode there would be an additional small partition named \boot, formatted as FAT32, that holds the EFI/UEFI boot loaders and EFI related utilities.

---

### Post by tegelstom on 2014-08-28
Clear enough! Thank You All! :)
ps: need to read more about BIOS and UEFI/EFI mode, your links are very useful!

---

