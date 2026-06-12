---
title: "Monitor switching to standby (SiS video driver)"
date: 2007-06-19
forum: General Help
---

### Post by bogr@ on 2007-06-19
Hi. Been using Ubuntu 7.04 for 3 days now but my monitor keeps switching to standby at random intervals. I have to turn off the monitor for a few minutes and then switch it back on to see what's going on.  It appears to happen when switching from one webpage with a photo on it to another more than at other times; but also when switching workspaces or sometimes when using the Movie Player.

I've figured out some very basic things like lspci from the terminal window and here is the output;

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:09.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 43)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

I've searched these pages for this problem and although some folks have a similar issue, I can't find one like mine (don't want to be a time-waster...)

I've been to the SiS website to see if they have an updated driver, but they state that "The listed linux OS has default driver for SiS products."

Any ideas? Thanks.

Edit: Selecting the desktop icon in the lower left corner also randomly switches the monitor to standby.

---

### Post by bogr@ on 2007-06-20
OK no replies for 10 hours now - but I've been doing a lot of follow-up on these SiS drivers on these forums and over at [www.winischhofer.net](www.winischhofer.net).  Seems they're not worth the trouble, unless someone can give me a relatively simple fix.  Thomas Winischhofers' website was too advanced for me at this stage.

I don't want to go back to MS Windows, especially as I've overwritten my installation when installing Ubuntu - I was dual booting for the first few days and then decided that this was the direction I wanted to go in.

Does anyone have any suggestions as to which videocard would be best to replace the SiS with given that I:
1.  Rarely, if ever, play games
2.  Do mostly SOHO (small office, home office) usage
3.  Use a lot of video (downloaded guitar lessons)
4.  Need something that has a mature Linux driver

Thanks in advance.

---

