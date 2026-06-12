---
title: "Webcam not working in Skype, 64 bit"
date: 2013-02-07
forum: General Help
---

### Post by Dberaud on 2013-02-07
Hi i'm currently using an Acer Aspire 7551 and i just got ubuntu after i had to reset my harddrive. I was using windows before that and i was just using the acer crystal eye webcam. 

I installed skype and now my webcam doesn't work or just isn't being detected. I'm not sure what i'm suppose to do exactly so i was wondering if someone can please help me out

---

### Post by kr651129 on 2013-02-07
Are you on 32 or 64 bit?  I've had a lot of problems in the past with webcams and skype on 64 bit Ubuntu.

---

### Post by Dberaud on 2013-02-07
64 bit but it worked fine before when i had windows. Completely new to Ubuntu

---

### Post by kr651129 on 2013-02-07
Can you run lsusb and lspci and post the results?

---

### Post by Dberaud on 2013-02-07
[PHP]Bus 002 Device 008: ID 04f2:b1d8 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/PHP]

[PHP]00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Acer Incorporated [ALI] AMD RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

[/PHP]

---

### Post by kr651129 on 2013-02-07
I dont see your cam listed...have you checked the HCL?

---

### Post by Dberaud on 2013-02-07
how would i do that?

---

### Post by kr651129 on 2013-02-07
[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

There are two threads hardware compatibility list and incompatibility list.  Is the webcam integrated?  I really think it might be a 64 bit issue.  I think you should download a 32 bit copy and install it on a USB Drive and try that out to see if it works.

---

### Post by mörgæs on 2013-02-08
The web cam is here:

```
Bus 002 Device 008: ID 04f2:b1d8 Chicony Electronics Co., Ltd 
```They are almost always on an internal USB connection.

Which version of Buntu are you using?
Does the camera work in Guvcview?

---

