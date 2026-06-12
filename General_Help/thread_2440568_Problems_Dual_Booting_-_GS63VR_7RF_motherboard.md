---
title: "Problems Dual Booting - GS63VR 7RF motherboard"
date: 2020-04-12
forum: General Help
---

### Post by jolewis211 on 2020-04-12
Hey Everyone, 

[COLOR=#1A1A1B][FONT=&amp]I'm trying to dual boot Ubuntu-18.04.4 with Windows 10 but am having a hard time with it and think it's because of my setup.[/FONT][/COLOR]

[LIST]
[*]MSI laptop
[*]GS63VR 7RF motherboard
[/LIST]
[COLOR=#1A1A1B][FONT=&amp]I've been scouring for info but am having a hard time weeding through non-effective and outdated solutions. Basically what I've tried is:[/FONT][/COLOR]

[LIST]
[*]Disabling fast boot
[*]Disabling secure in BIOS
[*]Changing priority to the USB stick in BIOS
[/LIST]
[COLOR=#1A1A1B][FONT=&amp]At this point, when I reboot I am prompted to install tor try Ubuntu. If I don't select an option Ubuntu launches, I find myself at a home screen and withing about a minute the system errors (see screenshot) and my laptop powers down. Notice, the failed "unmounting cdrom.mount" line.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]If I select the option to Install Ubuntu, the install wizard crashes too, I think the error is the same. Anyone know how I can handle this?[/FONT][/COLOR]

---

### Post by oldfred on 2020-04-12
Looks like it is starting to boot.

Typically you need UEFI update & if SSD, SSD firmware update.
Windows fast start up also needs to be off.

Issues often common across similar models by brand.
MSI GS65  Boot parameter: modprobe.blacklist=nouveau 
[https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions](https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions)
MSI GE63 Update UEFI then acpi=off not required
[https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues](https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues) & 
[https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off](https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off)
MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)

See also link below in my signature.

---

