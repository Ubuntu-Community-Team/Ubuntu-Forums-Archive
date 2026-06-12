---
title: "Live session will not boot"
date: 2013-02-14
forum: General Help
---

### Post by Niccolo999 on 2013-02-14
I'm a newbie to Linux and Ubuntu. I ran a DVD live session on a work laptop to rescue some data and that went well. I also ran a USB live session on a netbook at home, then installed Ubuntu 12.10 as a dual boot with Windows 7. That works well.

My problem is when I try to run a DVD or USB live session from my desktop computer at home. It just won't boot, even after I pressed F6 and tried all the options. Is there some way to get an error log? As far as I can understand I have an ATA error. I have an SSD and a HDD.

Please help me run a live session on my desktop computer.

---

### Post by oldfred on 2013-02-14
Welcome to the forums.

Does it not start, it could be video but your boot option of nomodeset should work around that.

Is system using RAID or Intel SRT?
Does Windows need chkdsk?

Have you created more than 4 partitions with Windows and converted to dynamic partitions which do not work with Linux.

Is it older and 32 bit only and you are using 64 bit?

What system is it Brand & model. Or some specs if built.

---

### Post by C.S.Cameron on 2013-02-14
Does the USB stick work on a different computer?

---

### Post by Niccolo999 on 2013-02-15
I'm trying to boot into a live session of Ubuntu 12.10 64 bit.

@C.S.Cameron I booted Ubuntu successfully off the same USB drive on other computers.

@oldfred Answers below in blue:

> **oldfred said:**
> Welcome to the forums. [COLOR="Blue"]Thanks![/COLOR]

Does it not start, it could be video but your boot option of nomodeset should work around that. [COLOR="blue"]I don't think it's the video. When Ubuntu starts booting the screen goes off, then it comes back on and the font is smaller. As far as I know this is the video driver from the BIOS switching to the Linux video driver. I tried nomodeset and it still wouldn't boot.[/COLOR]

Is system using RAID or Intel SRT? [COLOR="blue"]I don't use RAID so assuming it's Intel SRT[/COLOR]
Does Windows need chkdsk? [COLOR="blue"]No when Windows 7 x64 boots it doesn't run chkdsk. No errors on my drives.[/COLOR]

Have you created more than 4 partitions with Windows and converted to dynamic partitions which do not work with Linux.[COLOR="blue"]No partitions besides the default Windows 7 ones. C:\ is a SSD with Windows 7 x64 installed on it. D:\ is 500Gb HDD for data.[/COLOR]

Is it older and 32 bit only and you are using 64 bit? [COLOR="blue"]All hardware is less than a year old and running 64 bit.[/COLOR]

What system is it Brand & model. Or some specs if built.
[COLOR="blue"]Custom system:
Processor Intel Core i5-3570k
Motherboard ASRock Z77 Extreme 6
8GB Kingston high performance RAM
Video Card Intel HD Graphics 4000 (integrated with CPU) and AMD Radeon HD 6870
Creative Labs X-Fi Xtreme Gamer sound card
TP-Link wifi card
C:\ SSD Samsung 830 series 64GB
D:\ HDD Seagate Barracuda ST500DM002-1BD142 500GB
Sony Optiarc DVD drive[/COLOR]

---

### Post by oldfred on 2013-02-15
You do not have Intel SRT as that is a built in SSD used with Windows in RAID on some high end laptops. 

Since a Z77, you have UEFI and BIOS. Which mode are you booting into?

       AsRock calls BIOS mode AHCI.> 
"Launch EFI Shell from Filesystem Device" in the Exit tab of Asrock motherboard
Asrock Extreme4 Z77 motherboard, which has 4 SATA3 ports: 2 Intel ports (0 & 1) and 2 Asmedia ports (A0 & A1).Had my DVD drive connected to one of the Asmedia ports (A1), and so I tried switching the connection to one of the Intel SATA2 ports and the errors went away.

    

       UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)

---

### Post by Niccolo999 on 2013-02-15
I'm booting into AHCI mode.

Thanks for that article, I'll go through it.

---

### Post by Niccolo999 on 2013-02-15
Confirmed my UEFI is set to use AHCI mode, NOT RAID or IDE. I also found this setting - **SATA boot ROM** (Run legacy options ROM) and it's _disabled_.

---

### Post by oldfred on 2013-02-15
That probably is the BIOS mode. Some UEFI also call it CSM or compatibly mode.

You should review manual for your motherboard on details.

---

### Post by Niccolo999 on 2013-04-25
Hey I finally got Ubuntu to boot through USB on my desktop computer. I'm using it right now.

Guess what the problem was?

I'm using an ASrock Z77 Extreme 6 motherboard which uses two Sata3 controllers, an Intel one, and an ASmedia 1061. I have a SSD and HDD both plugged into the Intel controller. Then I have a DVD drive plugged into the ASmedia contorller.

Linux doesn't support the ASmedia controller, so wouldn't let me boot. I disabled SATA3 mode from the bios and it all works well now. Next I'll try to plug the DVD drive into a SATA2 port and re-enable SATA3 mode on the ASmedia controller to see what happens.

Finally I'll install Ubuntu alongside Windows 7 so I can dualboot and use Windows only for Photoshop and some games.

---

