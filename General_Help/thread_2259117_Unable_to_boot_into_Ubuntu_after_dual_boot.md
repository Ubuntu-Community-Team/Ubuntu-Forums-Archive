---
title: "Unable to boot into Ubuntu after dual boot"
date: 2015-01-02
forum: General Help
---

### Post by kushal2 on 2015-01-02
[FONT=arial]Hi,[/FONT][FONT=arial]
[/FONT]
[FONT=arial]Here is the URL : [http://paste.ubuntu.com/9650810/](http://paste.ubuntu.com/9650810/)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I have HP Envy J110TX. It runs Windows 8.1 operating System. I recently tried to install Ubuntu 14.04 alongside Windows.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]# I have disabled secure boot.[/FONT]
[FONT=arial]# I have enabled legacy Support.[/FONT]
[FONT=arial]# Succesfully installed Ubuntu but when I restarted It boots straight into Windows 8.[/FONT]
[FONT=arial]# Tried to run bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi in command prompt. But that didnt help.[/FONT]
[FONT=arial]# Installed Boot-repair and tried to repair the boot. That ran succesfully but didnt work.[/FONT]
[FONT=arial]# Installed Gparted and enabled enable bios_grub flag..But that didnt work.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Now everytime system boots I press F9 and manually select Ubuntu from boot options.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]What is going wrong? Kindly help..

[/FONT]http://imgur.com/VKZ3RIF[FONT=arial]

[IMG]http://imgur.com/VKZ3RIF[/IMG][/FONT]

---

### Post by grahammechanical on 2015-01-02
> [COLOR=#000000][FONT=arial]# I have enabled legacy Support.[/FONT][/COLOR]

Why? As I understand things when Windows 8 is pre-installed then Windows 8 is installed in EFI mode. That means that Ubuntu must be installed in EFI mode. 

> 
[LIST]
[*=left][FONT=inherit]In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[/FONT]
[/LIST]


> 
[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Please confirm that you have taken that advice into account.

Regards.

---

### Post by liandhara on 2015-01-02
> **grahammechanical said:**
> Why? As I understand things when Windows 8 is pre-installed then Windows 8 is installed in EFI mode. That means that Ubuntu must be installed in EFI mode. 





[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Please confirm that you have taken that advice into account.

Regards.

Yes, Ubuntu to be installed in EFI mode. experience also.

a greeting [usahabagus15.blogspot.com]("http://usahabagus15.blogspot.com")

---

### Post by kushal2 on 2015-01-04
So now How Do I remove Ubuntu? I had shrinked my C drive in windows and created new volume and installed Ubuntu in this new volume.
Just remove this volume?

---

