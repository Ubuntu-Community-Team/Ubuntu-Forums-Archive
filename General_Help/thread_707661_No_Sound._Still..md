---
title: "No Sound. Still."
date: 2008-02-25
forum: General Help
---

### Post by AbsentHarvest on 2008-02-25
My laptop is the dell Inspiron 1721.
The sound card, as quoted on the acknowledgment e-mail i recieved stated that my sound card is...

Sound Card   	  Integrated Sound Blaster® Audigy™HD Software Edition

I have no sound on my laptop. I am running Ubuntu 7.10
I have tried hours, and hours worth of tutorials.
Including the Comprehensive Tutorial located on this site. Yet nothing.

It's simple, Ubuntu does not "SEE" the card. So I have to get the driver somehow, and somehow implement it into the system.

Can anyone help me do both??? Any information would be helpful.
A $300 surround sound system is rendered useless, and I want to enjoy it as soon as possible. +_+

---

### Post by Crafty Kisses on 2008-02-25
> **AbsentHarvest said:**
> My laptop is the dell Inspiron 1721.
The sound card, as quoted on the acknowledgment e-mail i recieved stated that my sound card is...

Sound Card   	  Integrated Sound Blaster® Audigy&#8482;HD Software Edition

I have no sound on my laptop. I am running Ubuntu 7.10
I have tried hours, and hours worth of tutorials.
Including the Comprehensive Tutorial located on this site. Yet nothing.

It's simple, Ubuntu does not "SEE" the card. So I have to get the driver somehow, and somehow implement it into the system.

Can anyone help me do both??? Any information would be helpful.
A $300 surround sound system is rendered useless, and I want to enjoy it as soon as possible. +_+
Post the following output:
```
lspci
```

---

### Post by AbsentHarvest on 2008-02-25
Uhm, ok.
Here's what I got from typing that.

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

What do I do now?

---

### Post by kaens on 2008-02-25
Have you tried typing alsamixer in a terminal?

---

### Post by AbsentHarvest on 2008-02-25
********************   WARNING   *******************************
Warning! alsamixer uses ALSA emulation instead of the native OSS API
****************************************************************

snd_mixer_set_callback()
No mixer elems found.




So yeah. Two different solutions to fixing my sound. However, they're are conflicting with one another and i'm left with no sound. I'm beginning to grow frustrated. I've lost count of how many hours i've spent just trying to fix this one problem.

---

### Post by AbsentHarvest on 2008-02-25
I don't even know how to remove either one of those things.
I have no idea what to do now. I'm stuck.

---

### Post by AbsentHarvest on 2008-02-25
Oddly enough, the sound works. However, i still get the same errors and what not, no bother, i can just adjust it on my speakers
weird.. i have no idea which one is causing it to work. does it matter?

---

