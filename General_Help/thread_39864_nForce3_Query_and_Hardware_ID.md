---
title: "nForce3 Query and Hardware ID"
date: 2005-06-06
forum: General Help
---

### Post by hammett111 on 2005-06-06
Hi, does anyone out there know if installing the nForce3 drivers from Nvidia will allow identification of all the "unknown device" listings when I run lspci? (As per below)

I have installed the new nforce3 installation from nvidia (a sh *.run). Am I supposed to put the compiled modules into my modules listing to allow id of the hardware components below, or is there something in Kubuntu (Hoary) that I'm missing.

quentin@ubuntu:~$ lspci
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)
0000:02:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:02:07.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
0000:02:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
0000:02:0b.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)

Cheers to those who can help me, I wanna get all the devices on my system identified.

**Free beer to anyone who solves this for me** :smile:

---

