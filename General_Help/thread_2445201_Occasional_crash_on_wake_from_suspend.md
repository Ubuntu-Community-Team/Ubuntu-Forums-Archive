---
title: "Occasional crash on wake from suspend"
date: 2020-06-10
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2020-06-10
Has anyone elase see this happen? not 100% sure if it is my FCLK PICe stability or a driver bug, i think this has only happened twice since i upgrade to xubuntu 20.04

[LIST]
[*]there is no crash report 
[*]keyboard is unresponsive (no [reisub]("https://en.wikipedia.org/wiki/Magic_SysRq_key"))
[LIST]
[*]tried hookingup my PS/2 keyboard still nothing 
[/LIST]
  
[*]ssh is down 
[*]reset button works 
[/LIST]
to me it looks like a GPU crash, one monitor is black and the other has artifacts
CPU: R5 3600 w/ FCLK at 1866
GPU: [RX 580]("https://imgur.com/a/AOHDtRb") (2 display port monitors)
Board: X470 Gaming Plus
RAM: BLS2K8G4D32AESEK (Overclocked to 3733)
```
~$ lspci
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
01:00.0 Non-Volatile memory controller: Phison Electronics Corporation E7 NVMe Controller (rev 01)
03:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 43d0 (rev 01)
03:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset SATA Controller (rev 01)
03:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Bridge (rev 01)
20:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
20:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
20:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
20:03.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
20:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
20:08.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
24:00.0 Ethernet controller: Intel Corporation 82572EI Gigabit Ethernet Controller (Copper) (rev 06)
26:00.0 USB controller: ASMedia Technology Inc. ASM1143 USB 3.1 Host Controller
27:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] (rev e7)
27:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590]
28:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Function
29:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Reserved SPP
29:00.1 Encryption controller: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Cryptographic Coprocessor PSPCPP
29:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Matisse USB 3.0 Host Controller
29:00.4 Audio device: Advanced Micro Devices, Inc. [AMD] Starship/Matisse HD Audio Controller
30:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)
31:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)
```

---

### Post by dino99 on 2020-06-10
Maybe start with a ram memtest first

---

### Post by pqwoerituytrueiwoq on 2020-06-10
i know the ram is stable, 800% even at 3800 Mhz with these timings, the fclk just pukes when the gpu is under load at that speed

---

