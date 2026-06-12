---
title: "glitchy graphics and lines on screen, intermittent"
date: 2015-12-31
forum: General Help
---

### Post by Thomas_Williams on 2015-12-31
I've recently updated from 15.04 to 15.10, and since then I will get these glitches and lines across the screen intermittently. Very occasionally (and I haven't worked out how to reliably replicate this) the screen will go black for a second then the entire screen will be garbled. Most of the time I'll open an application and it'll mess up like in the screenshots attached below. 

 [ATTACH=CONFIG]266472[/ATTACH][ATTACH=CONFIG]266473[/ATTACH][ATTACH=CONFIG]266474[/ATTACH]

Is it related to this bug:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507255](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507255)  or is it something else? Any advice you may have to help me fix this will be greatly  appreciated. Thanks!

---

### Post by QIII on 2015-12-31
Hello!

It would be quite helpful to know your machine's hardware specs.

---

### Post by Thomas_Williams on 2016-01-07
Hi there! Is this what you mean? From lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)

---

### Post by mörgæs on 2016-01-07
Edit: Yes, the idea of trying UXA graphics as mentioned in the bug report is worth trying.

---

