---
title: "Computer Locks up in Edgy"
date: 2007-01-29
forum: General Help
---

### Post by rfdeshon on 2007-01-29
I just put a fresh installation of Edgy on my laptop. I'm having a problem where it will often freeze up when idle. When it does this, the touchpad still works just fine but it will not recognize any keyboard presses (with the exception of Alt+SysRq keystrokes I use to reboot it). Also, if I did not lock my screen before it locked up, it will not let me launch any new programs. I don't even know where to begin to look for the answer to this. Can anyone help?

---

### Post by Chiro on 2007-01-29
Can you describe your computer and the installation media you used.

---

### Post by rfdeshon on 2007-01-30
I'm on a Lenovo 3000 C100 (Celeron-M 1.5 GHz, 512 MB DDR, Intel 915GM). I installed off the standard Edgy installation media. Although this also happened when I had upgraded from Dapper to Edgy via apt.

just in case you need more info about my system. lspci gives this

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:02.0 Network controller: Broadcom Corporation Dell Wireless 1470 DualBand WLAN (rev 02)
01:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
01:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
01:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
01:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

```

Sorry about the lack of info in my last post, I usually remember to be more detailed, I was just in a hurry to get to work earlier.

---

### Post by rfdeshon on 2007-01-31
UPDATE: Since installing Edgy fresh, this now happens EVERY time I leave my laptop on overnight. I have tried closing programs before I go to bed, leaving my laptop open and unlocked, closing the lid and locking it, and a handful of other things, none of it seems to work. I have Splunked through my logs, I can't seem to find any obvious culprit. Could this be a driver problem? I do use the bcm43xx driver for my wireless card which is far less than perfect. I would just go back to Dapper but the support for my wireless card even with the bcm43xx driver in Dapper is pretty crappy. I often have to reload the module to get it to connect to a new network. Not exactly efficient. 

This problems officially makes Ubuntu LESS STABLE than my Windows box. Do I just have some fluky problem that is a result of my less-than-common laptop or are other people having this issue? If so, has anything been done to rectify it?

---

### Post by rfdeshon on 2007-04-12
This problem has been solved. It was the wireless card that shipped in my laptop. Apparently the bcm43xx drivers don't like it much. Threw an IPW2200 card in there and it's all kosher now. Ubuntu, it's linux: Horray Linux!

---

