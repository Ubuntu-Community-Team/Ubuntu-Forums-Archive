---
title: "Flickering on every action in SciTE"
date: 2013-12-12
forum: General Help
---

### Post by Sworddragon on 2013-12-12
I'm noticing on Ubuntu 14.04 dev that SciTE (a text editor) now begins to flicker on pressing any key (for example keeping enter pressed will make this easily reproducible). I have already downgraded nvidia-331-updates/nvidia-settings, libglapi-mesa/libgl1-mesa-glx, xserver-common/xserver-xorg-core, openbox/libobt2, linux-image-generic/linux-headers-generic and scite to the saucy versions but after a reboot the issue still exists. As this problem appeared only recently I'm assuming that it was caused by a package that was upgraded in the last 3 days. Has somebody an idea that caused this problem or can somebody even reproduce it?

Edit: After downgrading libgtk-3-0 3.10.6-0ubuntu2 to version 3.8.6-0ubuntu3 the issue got fixed. I have now opened a bug on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1260236](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1260236)

---

### Post by kumoshk on 2014-04-18
Yep. SciTE flickers for me. Changing my Nvidia driver changes the way and speed with which it flickers, but it flickers all the same (even with the open source non-proprietary driver). However, the video driver doesn't seem to be working quite right either. Is yours?

Here's my lspci output:

```

00:00.0 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: NVIDIA Corporation Device 075e (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: NVIDIA Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: NVIDIA Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: NVIDIA Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: NVIDIA Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: NVIDIA Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)

```

---

### Post by cariboo on 2014-04-18
Moved to General Help, seeing as Trusty has been released, and the previous poster ignored the banner in the U+1 sub-forum.

---

### Post by Sworddragon on 2014-04-19
> **kumoshk said:**
> Yep. SciTE flickers for me. Changing my Nvidia driver changes the way and speed with which it flickers, but it flickers all the same (even with the open source non-proprietary driver).

Maybe you want to post this information in the linked bug report and also registering yourself to the affected users.


> **kumoshk said:**
> However, the video driver doesn't seem to be working quite right either. Is yours?

I'm preferring the NVIDIA driver.

Edit: I forgot that I'm having this issue also on a laptop with an AMD graphics card with fglrx as driver.

---

