---
title: "trouble with usb devices"
date: 2006-08-29
forum: General Help
---

### Post by lucho64 on 2006-08-29
I've had problems with my USB devices that are not completely reproducible. I'm running a Athlon 1700+ with 1.5G of RAM and ATA hard drives (I attached lspci listing at the end). In the USB bus I have a printer, a scanner, a webcam, a gamepad and some cameras and mp3 players that I plug and unplug as needed. After a fresh reboot everything works normally: I can print, scan, capture video, upload pictures and download songs, but after a while (a day, two days) XSane will hang looking for devices, the pluggable devices wont ever appear in the desktop. The processes are unkillable at that point, so no matter how many times I issue a "killall -9 xsane" it just won't die. So I'm thinking it's a problem with the kernel USB subsystem getting locked. When I'm having those problems the shutdown procedure appears to hang in the bluetooth part. I'm disabling bluetooth, to see if that helps, but I was wondering if anyone has a similar problem, I haven't been able to google any solution yet...](*,) 


0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
0000:00:09.0 Network controller: PLX Technology, Inc. PCI <-> IOBus Bridge (rev 01)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]

Bus 004 Device 005: ID 046e:300d Behavior Tech. Computer Corp.
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 003: ID 04b8:010b Seiko Epson Corp. Perfection 1240
Bus 001 Device 004: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 002 Device 004: ID 047d:4005 Kensington Gravis Eliminator GamePad Pro
Bus 002 Device 003: ID 041e:4034 Creative Technology, Ltd
Bus 002 Device 001: ID 0000:0000

---

