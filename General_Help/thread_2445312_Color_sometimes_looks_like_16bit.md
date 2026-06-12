---
title: "Color sometimes looks like 16bit"
date: 2020-06-12
forum: General Help
---

### Post by stephenmichaelphotography on 2020-06-12
Hey, first post back on UbuntuForums in a while. Not sure if I ever posted under this name or not, but I used to be pretty active under VeeDubb65.

Anyway, I'm running 20.04 and having a really strange and intermittent visual artifact. 

Sometimes (no correlation identified yet) when I sit down at my desktop, the color will be off. It looks almost like the old windows 2000 days when somebody would set their desktop color settings to 16 or 24 bit instead of 32 bit. Smooth/natural gradient transitions like skin tone look slightly color banded.

This is a really huge problem for me, since photo editing is one of the main things I use my desktop for. I've done just a handful of tests, but it's such an odd-ball problem I don't have any idea what to try next. Any suggestions welcome.

Ubuntu 20.04
AMD Ryzen 9, 3900x
GeForce RTX 2060
1080p monitor connected via HDMI

I don't have any kind of color device permanently attached to my computer, but I did use one to generate a monitor profile and apply it to my display using the built in Color app in the settings menu.

Power cycling my monitor won't fix it or reproduce it.
Waiting for my monitor to sleep based on my power settings won't fix it or reproduce it
Disabling and re-enabling my monitor color profile won't fix it or reproduce it.
Logging out and back or rebooting both fix it temporarily
I've never seen the change happen. 
If I take a screenshot while it is happening, and then look at that screenshot after a logout or reboot, the screenshot is fine and does not show banding.

The fact that the screenshot doesn't capture the problem makes it look like a display hardware issue, but the fact that I can't reproduce it or fix it byh sleeping or power cycling the monitor, can fix it by logging out, and first noticed it within a couple days of upgrading to 20.04 all make me think it's a software problem.

Again, any suggestions welcome.

Thank you,

Stephen

```
:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Starship/Matisse IOMMU
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge
00:01.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge
00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:05.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:07.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:07.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
00:08.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 5
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 6
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 7
01:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983
02:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset USB 3.1 XHCI Controller (rev 01)
02:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset SATA Controller (rev 01)
02:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Bridge (rev 01)
03:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
03:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
03:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
07:00.0 VGA compatible controller: NVIDIA Corporation TU106 [GeForce RTX 2060 Rev. A] (rev a1)
07:00.1 Audio device: NVIDIA Corporation TU106 High Definition Audio Controller (rev a1)
07:00.2 USB controller: NVIDIA Corporation TU106 USB 3.1 Host Controller (rev a1)
07:00.3 Serial bus controller [0c80]: NVIDIA Corporation TU106 USB Type-C UCSI Controller (rev a1)
08:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Function
09:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Reserved SPP
09:00.1 Encryption controller: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Cryptographic Coprocessor PSPCPP
09:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Matisse USB 3.0 Host Controller
09:00.4 Audio device: Advanced Micro Devices, Inc. [AMD] Starship/Matisse HD Audio Controller
0a:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)
0b:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)

```

```
uname -a
Linux BearBox 5.4.0-37-generic #41-Ubuntu SMP Wed Jun 3 18:57:02 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by CelticWarrior on 2020-06-12
What drivers are you using for the Nvidia?

---

### Post by stephenmichaelphotography on 2020-06-14
I'm using the proprietary, tested 440 drivers.

That said, it seems to be resolved. 

I was apparently doing the turn it off and turn it back on a little too quick, including disabling and re-enabling the color profile. 

When I re-did some tests, taking a little more time, I realized that the problem DID go away when I disabled the color profile, then came back when I re-enabled it. (odd that the profile was applying correctly at boot/login without issue.

I deleted the profile I had been using and created a new one. No apparent issues since then.

---

