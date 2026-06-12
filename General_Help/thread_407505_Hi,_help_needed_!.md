---
title: "Hi, help needed !"
date: 2007-04-12
forum: General Help
---

### Post by Kizilbas on 2007-04-12
[B][FONT="Courier New"]Hi I want to install my WebCam on my Xubuntu Edgy 6.10 Linux system but I just don't know how to do this using Wine.

My WebCam installation files are on the WebCam's CD.

How can I install my WebCam using Wine or are there any alternative method(s) of installation?

I want to use my WebCam on linux too :)  aswell as on Windows.

Thanks[/FONT][/B]

---

### Post by garrido on 2007-04-12
I don't think you can do this with wine, it doesn't deal with low-level stuff like hardware drivers...  You should try to find out which chipset your webcam uses by running lspci and checking if that is supported, it might be the case of just installing the proper native linux driver.

---

### Post by Kizilbas on 2007-04-12
Here's what I got then:
I bought my computer in 2002.

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

```

---

### Post by Kizilbas on 2007-04-12
I would even remove my Xubuntu Linux OS just to get my WebCam working maybe on another Linux OS, I really need it to work on Linux.

help PlS

---

### Post by Ambimom on 2007-04-12
Install camorama from synaptic.....that may work with your webcam...good luck.

---

### Post by Kizilbas on 2007-04-12
> **Ambimom said:**
> Install camorama from synaptic.....that may work with your webcam...good luck.

Thank you for that suggestion, I will test it :)

Good day 2 everyone

---

