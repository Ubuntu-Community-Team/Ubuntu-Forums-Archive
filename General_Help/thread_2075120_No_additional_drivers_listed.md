---
title: "No additional drivers listed"
date: 2012-10-23
forum: General Help
---

### Post by hil4vitkutin on 2012-10-23
Hey!

I can't see any additional drivers on the Software Sources -> Additional Drivers tab. It is all empty. Does this just simply mean that there are no additional drivers available for my computer? 

And, what are the commands to find out if Ubuntu even detects my hardware? I have a wireless card and ATI Radeon HD 3200 graphics card.

---

### Post by drmrgd on 2012-10-23
I think if there are no drivers showing up, then none are available - although I'm not quite sure if the program will always pick up the proprietary drivers specifically.  You can see if your card is being detected by running:

```
sudo lspci | grep -i vga
```

Why are you interested in different video drivers?  Are you having a problem with the card?

---

### Post by Cheesemill on 2012-10-23
If there aren't any drivers listed it means there are none available. Chances are that your wireless will work out of the box as most drivers are included in the linux kernel.

As for your GPU there are no Additional Drivers for the 3xxx series of ATI graphics cards using 12.10.

ATI dropped support for all 2/3/4xxx cards over the summer and don't write drivers for them anymore.

---

### Post by Mark Phelps on 2012-10-23
I'm running an AMD HD 4290 video chipset, using the default Radeon drivers, and they're working fine.  

As to the AMD driver situation, if it's any consolation, they're not updating their HD 2x/3x/4x drivers for Win8, either.  Catalyst v12.6 is the last version they wrote for those chipsets.

---

### Post by hil4vitkutin on 2012-10-23
> **drmrgd said:**
> I think if there are no drivers showing up, then none are available - although I'm not quite sure if the program will always pick up the proprietary drivers specifically.  You can see if your card is being detected by running:

```
sudo lspci | grep -i vga
```Why are you interested in different video drivers?  Are you having a problem with the card?


Okay... I see my graphics card is detected. I don't really have a  problem, everything works fine, but I was wondering if I could get more  performance - just a little thing I would like to tweak. 

I want to get the best of my laptop  :D

>  As for your GPU there are no Additional Drivers for the 3xxx series of ATI graphics cards using 12.10.

ATI dropped support for all 2/3/4xxx cards over the summer and don't write drivers for them anymore.It's a shame that ATI has dropped support for my card. I hoped they would have been developing the drivers, because the drivers haven't ever worked well. 

>  As to the AMD driver situation, if it's any consolation, they're not  updating their HD 2x/3x/4x drivers for Win8, either.  Catalyst v2.6 is  the last version they wrote for those chipsets.  Well, it's too bad if they are not writing new drivers for my chipset anymore for Win8 either, I might be buying a new computer anyways.

And for the wireless card, I know a way how I'll get it working. I thought that there would have been a single-click solution, but if this is the case I'll live with it.

Thanks for your fast and informative answers!

---

### Post by hil4vitkutin on 2012-10-23
> **drmrgd said:**
> I think if there are no drivers showing up, then none are available - although I'm not quite sure if the program will always pick up the proprietary drivers specifically.  You can see if your card is being detected by running:

```
sudo lspci | grep -i vga
```Why are you interested in different video drivers?  Are you having a problem with the card?


Okay... I see my graphics card is detected. I don't really have a  problem, everything works fine, but I was wondering if I could get more  performance - just a little thing I would like to tweak. 

I want to get the best of my laptop  :D

> **Cheesemill said:**
>  As for your GPU there are no Additional Drivers for the 3xxx series of ATI graphics cards using 12.10.

ATI dropped support for all 2/3/4xxx cards over the summer and don't write drivers for them anymore.It's a shame that ATI has dropped support for my card. I hoped they would have been developing the drivers, because the drivers haven't ever worked well. 

> **Mark Phelps said:**
>  As to the AMD driver situation, if it's any consolation, they're not  updating their HD 2x/3x/4x drivers for Win8, either.  Catalyst v2.6 is  the last version they wrote for those chipsets. I really hope they would start their support for Windows 8 soon, because I might have it.

And for the wireless card, I think know a way how I'll get it working. I thought that there would have been a single-click solution, but if this is the case I'll live with it.


Thanks for your fast and informative answers!

---

### Post by GreatDanton on 2012-10-23
> **hil4vitkutin said:**
> 

It's a shame that ATI has dropped support for my card. I hoped they would have been developing the drivers, because the drivers haven't ever worked well. 


Exactly. That was the reason why I switched to 12.10, because I thought this problem will be solved. Drivers are actually working, but I noticed that during multitasking switching between workspaces is not smooth as it should be. I have Ati Radeon HD 4870.

---

### Post by hil4vitkutin on 2012-10-23
> **GreatDanton said:**
> Drivers are actually working, but I noticed that during multitasking switching between workspaces is not smooth as it should be. I have Ati Radeon HD 4870.

Well this is exactly the same experience I got, but I classified it as non-working, because I know how they should work like, the drivers worked perfectly with old ubuntu distros. 

But I like unity, and this isn't that bad without the drivers.

---

### Post by hil4vitkutin on 2012-10-23
Whoopsie... I think that I still have a problem, with my wireless card!

I tried *sudo lspci* but it doesn't show my wireless card, and I tried to find some information on the internet, but I didn't succeed in finding anything.

This is the output I get:

```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780M/RS780MN [Mobility Radeon HD 3200 Graphics]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8042 PCI-E Fast Ethernet Controller (rev 10)

```I can't see my wireless card there, so what's wrong?

---

### Post by Cheesemill on 2012-10-23
On laptops the wireless card is often attached to a USB port internally instead of the PCI bus. To list USB devices you need to do:
```
lsusb
```

---

### Post by hil4vitkutin on 2012-10-24
This is the output I got from *lsusb*:

```

Bus 002 Device 002: ID 04f2:b083 Chicony Electronics Co., Ltd 
Bus 006 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

However, I rebooted and tried *lspci* again, and I got the following:

```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780M/RS780MN [Mobility Radeon HD 3200 Graphics]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8042 PCI-E Fast Ethernet Controller (rev 10)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev ff)

```

Wonder how it got there now... I see rebooting is always the first thing to do!

---

