---
title: "I'm having trouble with duel booting Windows and Kubuntu"
date: 2021-07-16
forum: General Help
---

### Post by jacbo on 2021-07-16
Hi. I'm semi-new to using Linux. I was duel booting Windows and Kubuntu but I ran into a boot drive error along the way.

 I had it set up so one of my drives would have my Windows files and one of my drives would have my Kubuntu files, but now only Kubuntu loads up. All my Windows files are there, they just wont boot properly.

 When I go to select the Windows drive to boot manually from the f12 menu on startup, it says that no boot drive is selected. Is there any fix for this?

---

### Post by oldfred on 2021-07-16
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by jacbo on 2021-07-16
Alright, thanks. I'll send the summery shortly

---

### Post by jacbo on 2021-07-16
Should I post the pastebin here or is there a different place I should send it

---

### Post by tea for one on 2021-07-16
Post the link to your boot-repair report in this thread

---

### Post by jacbo on 2021-07-16
[https://paste.ubuntu.com/p/3tvGpZ7nSq/](https://paste.ubuntu.com/p/3tvGpZ7nSq/)

---

### Post by oldfred on 2021-07-16
You have newer UEFI hardware.
Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since 2012, so most hardware is now UEFI.

But you have Windows installed in the old BIOS/MBR configuration.
And then installed Ubuntu in UEFI boot mode on sda.
You cannot mix BIOS & UEFI unless both systems are totally isolated on separate drives. Generally you want both systems in UEFI boot mode or both in BIOS boot mode.

It also looks like you installed Windows to sdb drive, when BIOS had sda as default boot. So Windows in sdb1 has no boot partition, but sda has Windows boot partition, sda1. 
Windows has to have boot flag on its boot partition  to boot, so you must move boot flag using gparted from sda3 (ESP - efi system partition) to sda1, Windows boot partition.
That should get Windows boot working again.

But you still have mixed UEFI & BIOS installs & part of Windows on sda & most on sdb.
You can install BIOS version of grub2 boot loader to sdb, even though Ubuntu on sda. Strange to have Windows boot on Linux drive & Linux boot on Windows drive, but that would work. Use Boot-Repair booted in BIOS mode and its advanced mode to choose install on sda, but MBR of sdb. You want to keep Windows boot loader on sda.

Since UEFI hardware, best case is to have good backup of Windows & totally reinstall both systems in UEFI boot mode to gpt partitioned drives.
That takes advantage of newer UEFI hardware and configuration.

---

### Post by tea for one on 2021-07-17
[COLOR="#0000FF"]Line 107[/COLOR] - sda	: notGPT,	no-BIOSboot,	[COLOR="#0000FF"]has---ESP[/COLOR], 	not-usb,	not-mmc, has-os
[COLOR="#0000FF"]Line 108[/COLOR] - sdb	: notGPT,	no-BIOSboot,	[COLOR="#0000FF"]has-noESP[/COLOR], 	not-usb,	not-mmc, has-os

This indicates mixed mode installations, here is some more info:-
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> **oldfred said:**
> Since UEFI hardware, best case is to have good backup of Windows & totally reinstall both systems in UEFI boot mode to gpt partitioned drives.
That takes advantage of newer UEFI hardware and configuration.

Yes, the perfect solution from [COLOR="#0000FF"]oldfred[/COLOR]
Each OS on separate drives in UEFI mode with GPT is ideal.

I would also advise that you only have the target drive available when installing so that an ESP (EFI system partition) is automatically created on each drive.
In the event of drive failure/problems, each drive can then operate completely independently.

---

