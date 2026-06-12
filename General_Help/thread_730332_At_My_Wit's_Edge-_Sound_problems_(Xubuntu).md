---
title: "At My Wit's Edge- Sound problems (Xubuntu)"
date: 2008-03-20
forum: General Help
---

### Post by ThatGuyThere on 2008-03-20
I have been having sound issues ever since I have installed flashplayer for Firefox. Since then, My sound DOES NOT FUNCTION at all. No system sounds or anything. I get this error message from Amarok:

Audio output unavailable; the device is busy.
xine parameters: 

It's pretty vague. I've tried the guide on installing sound, but it didn't work. Whenever I go into Apps-Settings-Mixer Settings, The dropdown bar only says default, and doesn't drop down. I get no options to change any other sounds. I have tried uninstalling flash and rebooting, and the comprehensive sound guide. I'm teetering on the edge of uninstalling linux alltogether and going back to Windows (Something I dread), because this is the 3rd time this problem has happened in 3  different Ubuntu installs (Standard, kUbuntu, and xUbuntu). ANY Help would be appreciated. I love the OS so far, but with serious problems like these, it's really deterring me :(

EDIT- Some (imo) useful info:

LSPCI output: 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
0b:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
0c:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
0d:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 02)


aplay -l output : 

aplay: device_list:204: no soundcards found...

EDIT 2- Running linux on a Macbook pro 2.2ghz 2gb ram, if that makes a difference. Sounds are fine on OS X.

---

### Post by ThatGuyThere on 2008-03-20
Bump

---

### Post by superprash2003 on 2008-03-21
hope this works [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

