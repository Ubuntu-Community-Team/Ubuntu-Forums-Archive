---
title: "Multi-boot 3 OS Grub recovery/configuration"
date: 2017-02-28
forum: General Help
---

### Post by nervousdev on 2017-02-28
Hi there,

first time here. Let me know if I'm doing something wrong.

[COLOR=#242729][FONT=Arial]So right now I have 3 OS installations on my laptop: 2 Windows 10 and 1 Ubuntu.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I first installed my 1º Windows, then Ubuntu and now I installed my 2º Windows 10.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The thing is before I installed the last one, GRUB was fine (the entry menu was working perfect). After the 2º Windows installation there was no change so I ran "boot-repair" on Ubuntu and now the laptop automatically launchs the "Windows boot window" (don't know the exact name).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My question is: how can I recover GRUB and then make the 2 Windows entries work (on GRUB, not on the "windows boot manager")?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thank you.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial](By the way, if you are wondering why I want 2 Windows 10 installations is because I want to separate my private and working installation).[/FONT][/COLOR]

---

### Post by oldfred on 2017-02-28
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If BIOS a Windows install overwrites the MBR, you have to reinstall grub to MBR.
If UEFI, Windows will change UEFI boot order to make Windows first. You have to use efibootmgr or go into UEFI and change boot order.

You cannot easily have grub show both Windows.
Windows in BIOS only puts boot files into primary NTFS partition with boot flag.
If UEFI Windows only boots from /EFI/Microsoft folder in ESP - efi system partition. 
Some have done a work around with a second ESP (you can only have one working one), but grub does not care and may work.

---

### Post by nervousdev on 2017-02-28
Hi, thank you for the input...

So, all the installations are in "UEFI" mode. I'm gonna try get that report and I'm gonna share it here. 

Can you share some link of the work done by who managed to get it to work?

Thank you again.

---

### Post by oldfred on 2017-02-28
This does not have Windows.
 Oldfred's 16.04 Asus-AR
[http://paste2.org/JCDWpOJM](http://paste2.org/JCDWpOJM) 

I do have one Windows 10 on a SFF Dell Haswell, but just have it booting Windows normally. If necessary, I could reboot into 16.04 and run the Boot-Repair on it.
It is just used to watch Comcast DVR from Ill in Fla.

---

