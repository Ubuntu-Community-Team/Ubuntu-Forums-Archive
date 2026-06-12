---
title: "UEFI and Legacy bootloaders in one system"
date: 2013-09-25
forum: General Help
---

### Post by zany_001 on 2013-09-25
I've had Windows 7 installed for some time, and recently reinstalled Ubuntu 13.04. After managing to get Ubuntu to boot ([http://ubuntuforums.org/showthread.php?t=2175937](http://ubuntuforums.org/showthread.php?t=2175937)) I now have the problem that Windows 7 no longer boots, with an error "Invalid EFI file path". If I understand correctly, Windows 7 doesn't need to have the disk in UEFI mode for it to boot, but my Ubuntu install does. So I want to place a separate GRUB bootloader on one of the other disks, and select that when I want to boot into Windows. Ideally I'd do it from one bootloader install but I'm not sure if that's possible.

Anyway, I don't know how I can have two separate bootloaders, one UEFI for Ubuntu, and one Legacy/BIOS for Win7. I don't even know if it's possible :P 

The other disks I have give the error "File /boot/grub/i386-pc/normal.mod not found".

---

### Post by ajgreeny on 2013-09-25
Follow the directions in the Boot-repair link in my signature and it will help us to see what the current situation is, and give clues about how to solve it; it may even solve your problem for you, but if not it will produce a report in a link which you can post back here for viewing.

There is also a lot of info on UEFI at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) which you may find useful.

---

