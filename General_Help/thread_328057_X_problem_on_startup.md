---
title: "X problem on startup"
date: 2006-12-30
forum: General Help
---

### Post by donut_irl on 2006-12-30
Hi,

For some reason X won't start anymore.
It worked fine yesterday and now is dead.


I've run sudo dpkg-reconfigure xserver-xorg and rebooted several times and tried vesa and vga and still nothing.

The error I get when i try and run X is:
(EE) No devices detected

Fatal srever error
no screens found
(which google tells me is something to do with xorg-server-core 1:1.0.2-0ubuntu10.3  but my xorg-server-core version is 1:1.1.1-0ubuntu12  ... i think .. so the fixes for that don't work)

output from lspci (which tseliot wanted to see in a parellel [post]("http://www.ubuntuforums.org/showthread.php?t=327919") that i didn't want to interupt) is :
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
02:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
02:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

Thanks

---

### Post by wpshooter on 2006-12-30
Is this Edgy ?

If so, you might want to look at the ANNOUNCEMENT at the top of the General section forum.  Might be related to that.

---

### Post by donut_irl on 2006-12-30
it is edgy,

and i looked through the annocment post and tried the suggested soluton:

sudo apt-get install --reinstall linux-restricted-modules-`uname -r` nvidia-glx
sudo depmod -ae

and no difference, i'm looking through the rest of the psot but no changes yet

---

