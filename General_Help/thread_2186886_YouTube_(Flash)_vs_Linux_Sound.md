---
title: "YouTube (Flash?) vs Linux Sound"
date: 2013-11-09
forum: General Help
---

### Post by mariusz2 on 2013-11-09
My friend is running Ubuntu 12.04, and whenever he goes on YouTube, no matter whether its Firefox or Chromium, the browser simply crashes, and sound stops owrking. If you go into sound settings after that, it lists no audio devices whatsoever. He sais it also happens on some other webistes (seems like it's related to FlashPlayer maybe?).

Does anyone know why this couldbe happening, and how to fix it?

Thank you.

---

### Post by tgalati4 on 2013-11-09
Wireless connection or wired connection?  Desktop or Laptop?  What is the hardware?

Open a terminal:

```
lspci
```

Some soundchips are part of the ethernet controller on the Southbridge chip, so watching a video causes the Southbridge to heat up and crash--temporarily killing sound.

What is the output of:

```
aplay -l
```

---

### Post by mariusz2 on 2013-11-10
The output of lspci was:

```

00:00.0 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: NVIDIA Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: NVIDIA Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: NVIDIA Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: NVIDIA Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 SATA controller: NVIDIA Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
02:00.0 VGA compatible controller: NVIDIA Corporation C77 [GeForce 8200] (rev a2)
05:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller

```

The output of aplay -l was:

```

**** Lista PLAYBACK urz&#261;dze&#324; ****
karta 0: NVidia [HDA NVidia], urz&#261;dzenie 0: ALC888 Analog [ALC888 Analog]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 0: NVidia [HDA NVidia], urz&#261;dzenie 1: ALC888 Digital [ALC888 Digital]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 0: NVidia [HDA NVidia], urz&#261;dzenie 3: HDMI 0 [HDMI 0]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 1: Audio [USB Audio], urz&#261;dzenie 0: USB Audio [USB Audio]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0

```

I'm sorry that the output is in Polish, but hopefully you can understand everything from format.

Thank you.

EDIT: forgot to mention: he uses external USB speakers.

---

### Post by tgalati4 on 2013-11-10
I noticed some USB ports are 1.1 and some are 2.0.  Make sure that the speakers are plugged into 2.0 ports.  The 1.1 ports don't have the throughput to support audio.  Maybe that is the problem.

Also, since this is an nVidia chipset PC, perhaps the nVidia proprietary drivers will work better.  Sometimes the open source nVidia drivers are buggy or slow and that might cause the browser to crash.

---

### Post by mariusz2 on 2013-11-11
> **tgalati4 said:**
> I noticed some USB ports are 1.1 and some are 2.0.  Make sure that the speakers are plugged into 2.0 ports.  The 1.1 ports don't have the throughput to support audio.  Maybe that is the problem.


The speakers work perfectly until the YouTube/Flash crash. Also, after the crash, even the built-in audio card disappears from the menu.

> **tgalati4 said:**
> 
Also, since this is an nVidia chipset PC, perhaps the nVidia proprietary drivers will work better.  Sometimes the open source nVidia drivers are buggy or slow and that might cause the browser to crash.

I have infact experienced a problem with some nVidia drivers (negative colors in YouTube), so I would agree with you here. Although shouldn't the proprietary drivers install themselves during Ubuntu installation if there was an Internet connection?

---

