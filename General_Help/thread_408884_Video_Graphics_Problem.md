---
title: "Video Graphics Problem?"
date: 2007-04-13
forum: General Help
---

### Post by antex on 2007-04-13
For the most part, Ubuntu is running fine, but one small (or big, depends how you see it) annoyance is that there appears to be a lot of lag with the GUI of most applications. For example, I can run Windows XP fine, and drag windows around, and scroll through large documents easily, but on Ubuntu, it's laggy even dragging gedit with nothing in it. I think the issue is that my computer has an inbuilt graphics card, SiS. I know nothing about graphics cards at all, really. I blame Packard Bell, though. :)

If anyone can help me out installing packages or whatever needs to be done to fix this and make it as smooth as XP, I'd be grateful.

---

### Post by maniacmusician on 2007-04-13
> **antex said:**
> For the most part, Ubuntu is running fine, but one small (or big, depends how you see it) annoyance is that there appears to be a lot of lag with the GUI of most applications. For example, I can run Windows XP fine, and drag windows around, and scroll through large documents easily, but on Ubuntu, it's laggy even dragging gedit with nothing in it. I think the issue is that my computer has an inbuilt graphics card, SiS. I know nothing about graphics cards at all, really. I blame Packard Bell, though. :)

If anyone can help me out installing packages or whatever needs to be done to fix this and make it as smooth as XP, I'd be grateful.
If I recally correctly, SiS is the company that provides no drivers for Linux whatsoever, and have horrible support for it. I think you may be out of luck. I'll look into it a little.

also, can you post the specific chipset that you have? it would show up if you use "lspci" at the terminal.

---

### Post by antex on 2007-04-14
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:09.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 0c)
00:0a.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
00:0b.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter
```

Wow, SiS pretty much owns my entire computer.

Basically all of my device information under Device Manager gives me unknown. All of it. Even the processor,  which I find pretty amusing, to be honest.

---

### Post by antex on 2007-04-14
*bump*

---

### Post by antex on 2007-04-16
*second bump* Surely someone must have a solution?

---

### Post by DougieFresh4U on 2007-04-16
Do not know if this helps but found this at Sis website just a sample of what you might find: for Linux:[B]Silicon Integrated Systems  	   	
PRODUCTSSUPPORTDOWNLOADPRESS ROOMSiS e-LIBRARYABOUT SiSWHERE TO BUYTraditional ChineseSimplified Chinese
	
Download Center
WELCOME TO SiS DOWNLOAD CENTER
Below you will find drivers for all SiS core logic chipsets , mature GPUs and network controllers. Just choose from the selections below and press Go when you are ready to download. For Linux users, please check out this page.


STEP BY STEP




  	  	  	  	 
  	  	  	  	

TOP DOWNLOADS
	SiS7012 Audio Driver
  	(v1.12d) 2005-06-09
	SiS AGP(GART) Driver
  	(v1.21) 2005-04-01
	SiS900 LAN Driver
  	(v1.19) 2006-06-29
	SiS IDE Driver
  	(v2.04a) 2003-11-18
	SiS UniVGA2 Graphic Driver for Win2000/XP
  	(v2.22) 2004-01-20
	
LATEST DRIVERS
	SiS UniVGA3 graphics driver
  	(v3.80) 2007-04-16
	SiS UniVGA5 graphics driver
  	(v5.03) 2007-03-23
	SiS191 Gigabit LAN & SiS190 LAN Driver
  	(v2.01a) 2007-02-13
	SiS RAID driver package
  	(v4.11a) 2007-02-08
	SiS UniVGA3 graphics driver
  	(v3.79) 2007-02-05
	
FAQ[/B]
	Why my SiS Integrated Graphic can not support 1440x900 resolution?
	Lately, Intel has just announced their new LGA775 CPU, and their new gerenation Chipset as well. ...
	It seems like PCI Express will be the most important new spec for the PC industry. But besides ne...
  	more FAQ

---

### Post by antex on 2007-04-16
Thanks. You didn't post a link though, so I went and found it on Google: [http://www.sis.com/support/support_faqs_16.htm]("http://www.sis.com/support/support_faqs_16.htm")

However, I know that Ubuntu installed an SiS package when I installed it. Can anyone tell me if Ubuntu is supporting my graphics card or how to tell if it is, and how I can get it working if it isn't?

---

