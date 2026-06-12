---
title: "clueless..."
date: 2007-04-29
forum: General Help
---

### Post by lionstilidie on 2007-04-29
Hi,

   I have searched and search and am prolly just missing something, but I just got v7.04 up and running on my Gateway m505 and I can not figure out how to enable my wireless connection. There are two things that i think could fix this, but I don't know how to do/where to find them. either, how do you enable your wireless radio from the terminal? or does anyone know of a linux driver for the launch manager for the gateway m505 (i believe it is the same as the m500 also) this has my radio toggle button on it, but needs a driver...
the last driver I had working on windows (my first attempt away from windows) was...Gateway M505 Launch Manager Software driver, version 1.1.7... I have read a number of forums with people having issues with this notebook and the ati graphics card in the past but never anything else so it must be something i am overlooking....

-thanks

---

### Post by hardyn on 2007-04-29
please post the contents of the "sudo lspci"

you likely have a broadcom wifi chipset, and it will take some massaging to make it work.

---

### Post by lionstilidie on 2007-04-29
```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:01.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:06.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:06.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

It's and intel 2100 3b pro/wireless. It's detected  but the rf_kill can not enable it, just the hardware...which doesnt work. Rf_kill reports a power status of 2, so hardware and sofware both are disabling the radio...thats about all i have been able to google and find out so far...
-thanks

---

### Post by fAlCoNNiAn on 2007-05-01
i looked online and all i found were people with a simular build, the gigabyte n601? which is pretty much a clone of your gateway m505. Unfortunitly, there isnt a large linux support community for that model.

I looked online as well and came up with the acer functional panels. That might be able to help, but i also knew a guy that had a m500, which also has the panel, and couldnt get it to work. :(

Anyone here know anything more?

---

### Post by Turellius on 2007-05-01
If there is not support for your wireless chipset, then you can use [NDISwrapper]("http://ndiswrapper.sourceforge.net/joomla/") 
I haven't ever used it myself, so this is more of a simple point in the right direction than a solution to your problem.

---

### Post by fAlCoNNiAn on 2007-05-01
> **Turellius said:**
> If there is not support for your wireless chipset, then you can use [NDISwrapper]("http://ndiswrapper.sourceforge.net/joomla/") 
I haven't ever used it myself, so this is more of a simple point in the right direction than a solution to your problem.

His problem is that it IS supported, just the panel on the right side of his laptop is not recognized. And on that panel is the radio on/off switch for the wireless.

---

### Post by fAlCoNNiAn on 2007-05-01
is there anything that you can enable in the bios?

---

### Post by lionstilidie on 2007-05-03
Well, I figured it out...kind of. I just set up a dual boot with Windows  and turned on my wireless radio. Now my wireless is on 24/7, but at least now I can learn linux during boring lectures!

---

