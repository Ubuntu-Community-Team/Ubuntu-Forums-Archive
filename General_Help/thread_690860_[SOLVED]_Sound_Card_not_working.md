---
title: "[SOLVED] Sound Card not working"
date: 2008-02-07
forum: General Help
---

### Post by lyceum on 2008-02-07
I have a HP Pavilion dv9740us laptop. The sound works fine on my Vista partition, but not on my Ubuntu 7.10 partition. I think the card is a Realtek High Definition Audio card, or at least that is what Vista tells me, but that is all it tells me. So a few questions:

1. How do I know the card name and model number?

I ran lapci in the terminal an got:

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

The only Realtek I see there looks like an Ethernet controller, not Audio. To me, it looks like Ubuntu can't see the audio card :confused:

2. If Realtek High Definition Audio, or something in the mess above, is all I need to know, how do I make it work? I tried searching the forums and Google. I found 

[http://ubuntuforums.org/showthread.php?t=516810](http://ubuntuforums.org/showthread.php?t=516810)

but, it is too old and has no solution. 

Thanks for any help.

---

### Post by machoo02 on 2008-02-07
> **lyceum said:**
> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
This line shows your audio card.  Try using the -v option with lspci to get a little more info.

---

### Post by lyceum on 2008-02-09
> **machoo02 said:**
> This line shows your audio card.  Try using the -v option with lspci to get a little more info.

sorry I took so long to respond, but here is what I got with lspci -v:

> 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


Is "unknown" the reason it is not working?

---

### Post by machoo02 on 2008-02-10
I don't think the "unknown" has anything to do with it.  Check out [this bug report]("https://bugs.launchpad.net/ubuntu/+bug/122560") for possible fixes, and [this wiki page]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") for some other possible fixes.

---

### Post by lyceum on 2008-02-10
> **machoo02 said:**
> I don't think the "unknown" has anything to do with it.  Check out [this bug report]("https://bugs.launchpad.net/ubuntu/+bug/122560") for possible fixes, and [this wiki page]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") for some other possible fixes.

Well, the wiki was the most help, but when I ran the script that looked like it would help it un-installed everything and my Vista partition gone (it is still there and fine, I just can't access it through the boot loader). So, I am off to re-install Ubuntu. I think I will just leave the sound alone for now. It looks like the developers are taking the bug seriously, so hopefully it will be fixed for 8.04. Thank you though.

---

### Post by lyceum on 2008-03-20
Well, I figured out what I did wrong. One of my external hard drives had previously been the main hard drive for my old desktop. I just put it into a box and plugged it into my new laptop. I finally realized that when I had it plugged it, grub changed. So I unplugged everything and started over, and now I am listening to Jimmy Hendrix :guitar:

Thank you!!!

:popcorn:

---

