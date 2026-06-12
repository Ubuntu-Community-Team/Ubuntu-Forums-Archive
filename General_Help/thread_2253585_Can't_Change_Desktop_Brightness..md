---
title: "Can't Change Desktop Brightness."
date: 2014-11-20
forum: General Help
---

### Post by nacor2 on 2014-11-20
Hi, I'm trying to change my desktop brightness using: ```
sudo setpci -s 01:00.0 F4.B= 72
``` but it does nothing, used lspci: ```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 530 Host (rev 03)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge) (rev b1)
00:01.1 Class ff00: Silicon Integrated Systems [SiS] ACPI
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 11)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:09.0 Network controller: RaLink RT2600 802.11 MIMO
00:0a.0 USB Controller: NEC Corporation USB (rev 41)
00:0a.1 USB Controller: NEC Corporation USB (rev 41)
00:0a.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:0c.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0c.1 Communication controller: C-Media Electronics Inc CM8738 (rev 20)
00:0d.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 02)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 530/620 PCI/AGP VGA Display Adapter (rev a3)
``` I've tried with ```
xgamma -gamma 1.5
``` it seems to work, but thats not real brightness, so if anyone knows a way i'll be Very Grateful.

My Desktop Specs:

CPU: AMD K6-II, 400 mhz.
RAM: 512 mb.
HDD: 20 Gb.
Video: [SiS] 530/620, 8 mb Shared Video Memory.
Monitor: LG Studioworks 775N.
Screen Resolution: 640 x 480.
MotherBoard: PCCHIPS M598LMR.
OS: Lubuntu 10.04 "Lucid Lynx".

---

