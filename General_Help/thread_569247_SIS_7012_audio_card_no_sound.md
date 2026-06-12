---
title: "SIS 7012 audio card no sound"
date: 2007-10-06
forum: General Help
---

### Post by nigelms on 2007-10-06
Hi

No sound on the sis7012 using alsa mixer I have followed all other threads and no joy
using ubuntu dapper 6.06.1 

I have enjoyed using the operating system so far but would really like to listen to music
and watch movies as well.

I am running dual operating system winxp/ubuntu on a novatech brand laptop

No proplems with sound on winxp

Heres a log of;lspci

nigel@nigel-laptop:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 51)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 14)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:09.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 01)
0000:00:09.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
0000:00:0a.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
nigel@nigel-laptop:~$


Any help would be much appreciated

Thank you

Nigel M S

---

### Post by inoxllor on 2007-11-17
Hello 

I had the same problems with SIS 7012 onboard sound on ubuntu 7.04 and 7.10.

I believe the problem is related to the onboard modem, sometimes it overrides the soundcard (?). 
The thing should be bypassed if you know a way to turn off the modem permanently. 

The alternative is to try the steps mentioned here:
[http://ubuntuforums.org/showthread.php?t=484876](http://ubuntuforums.org/showthread.php?t=484876)

---

