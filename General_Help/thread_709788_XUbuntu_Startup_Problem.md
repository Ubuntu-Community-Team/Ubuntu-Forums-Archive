---
title: "XUbuntu Startup Problem"
date: 2008-02-27
forum: General Help
---

### Post by Gannon8 on 2008-02-27
I have the latest version of xubuntu on a live cd. When I boot it up normally, selecting the "Start or Install Xubuntu," it runs fine until after all the lines of code come up and at the end of it it says [OK], then I get some weird 1 pixl thick horizontal lines that appear to go down the further you go right. I can start it in safe graphics mode, and I checked the checksum and everything was ok. Any tips?

---

### Post by doublehelixer on 2008-02-27
It's probably not picking the right driver config for your video.  what kind of video card and monitor do you have?

If you need info about the card boot in safe video mode and at a terminal prompt type 'lspci'.  This will spit out a bunch of hardware info and you should be able to spot your card The 8th line in my results below shows mine as an ATI Radeon, so I need to use the 'ati' driver

me@mycomputer:~$ lspci

00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)

00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 04)

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

02:01.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)

02:01.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)

02:01.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)

02:02.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)

02:02.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)

02:02.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)

02:07.0 Mass storage controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)

02:09.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

02:0a.0 Modem: PCTel Inc HSP56 MicroModem (rev 03)

02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

]0;me@mycomputerme@mycomputer: ~me@mycomputer:~$ exit

exit


Script done on Wed 27 Feb 2008 08:41:58 PM EST

---

### Post by Gannon8 on 2008-02-28
The windows device manager says I have a NVIDIA GeForce 440 Go (Dell Mobile)
This is a pretty old computer, an Inspiron 8200.
Is there anyway to fix it?

---

### Post by Gannon8 on 2008-02-29
bump:|

---

