---
title: "drm:drm_edid_block_valid] *ERROR* EDID has major version 0, instead of 1"
date: 2013-09-06
forum: General Help
---

### Post by jagat2 on 2013-09-06
Hi,

I installed Ubuntu 13.10 daily build on my machine. No custom drivers only base Ubuntu

I am getting this error in syslog

Can you please suggest.

Sorry posting full error stack , dont know which all things would be helpful for you to debug


Sep  7 10:51:52 nanak-P570WM kernel: [   42.403661] [drm:drm_edid_block_valid] *ERROR* EDID has major version 0, instead of 1
Sep  7 10:51:52 nanak-P570WM kernel: [   42.406156] [drm:drm_edid_block_valid] *ERROR* EDID has major version 0, instead of 1
Sep  7 10:51:52 nanak-P570WM kernel: [   42.408649] [drm:drm_edid_block_valid] *ERROR* EDID has major version 0, instead of 1
Sep  7 10:51:52 nanak-P570WM kernel: [   42.411150] [drm:drm_edid_block_valid] *ERROR* EDID has major version 0, instead of 1
Sep  7 10:51:55 nanak-P570WM NetworkManager[970]: <info> (wlan0): IP6 addrconf timed out or failed.
Sep  7 10:51:55 nanak-P570WM NetworkManager[970]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep  7 10:51:55 nanak-P570WM NetworkManager[970]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep  7 10:51:55 nanak-P570WM NetworkManager[970]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Sep  7 10:52:09 nanak-P570WM kernel: [   59.191657] [drm:drm_edid_block_valid] *ERROR* EDID has major version 0, instead of 1
Sep  7 10:52:09 nanak-P570WM kernel: [   59.194150] [drm:drm_edid_block_valid] *ERROR* EDID has major version 0, instead of 1

Sep  7 10:51:29 nanak-P570WM kernel: [   19.707173] [drm:drm_edid_block_valid] *ERROR* EDID has major version 0, instead of 1
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826693] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0x00000000 FAULT at 0x418880 [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826703] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0x00ffffff FAULT at 0x405844 [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826734] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0x00000000 FAULT at 0x40803c [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826749] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0x00000000 FAULT at 0x418c68 [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826760] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0x00000060 FAULT at 0x418e00 [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826781] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0x00000000 FAULT at 0x419ab0 [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826790] nouveau E[   PIBUS][0000:01:00.0] GPC0: 0x419cb8 0x00b08bea (0x3800820c)
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826796] nouveau E[   PIBUS][0000:01:00.0] GPC1: 0x419cb8 0x00b08bea (0x3800820c)
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826802] nouveau E[   PIBUS][0000:01:00.0] GPC2: 0x419cb8 0x00b08bea (0x3800820c)
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826808] nouveau E[   PIBUS][0000:01:00.0] GPC3: 0x419cb8 0x00b08bea (0x3800820c)
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826831] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0x00010384 FAULT at 0x419c84 [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826839] nouveau E[   PIBUS][0000:01:00.0] GPC0: 0x419f74 0x00000555 (0x3800820c)
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826845] nouveau E[   PIBUS][0000:01:00.0] GPC1: 0x419f74 0x00000555 (0x3800820c)
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826851] nouveau E[   PIBUS][0000:01:00.0] GPC2: 0x419f74 0x00000555 (0x3800820c)
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826857] nouveau E[   PIBUS][0000:01:00.0] GPC3: 0x419f74 0x00000555 (0x3800820c)
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826894] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0x00000000 FAULT at 0x41be04 [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826902] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0x11110000 FAULT at 0x418980 [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826918] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0x00000002 FAULT at 0x500914 [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826927] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0x00040008 FAULT at 0x518910 [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826940] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0x00000004 FAULT at 0x4188ac [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826948] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0xbadf1008 FAULT at 0x419cc0 [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826956] nouveau E[   PIBUS][0000:01:00.0] GPC0: 0x419cc0 0xbadf1008 (0x3800820c)
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826962] nouveau E[   PIBUS][0000:01:00.0] GPC1: 0x419cc0 0xbadf1008 (0x3800820c)
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826968] nouveau E[   PIBUS][0000:01:00.0] GPC2: 0x419cc0 0xbadf1008 (0x3800820c)
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826974] nouveau E[   PIBUS][0000:01:00.0] GPC3: 0x419cc0 0xbadf1008 (0x3800820c)
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826987] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0xbadf1000 FAULT at 0x419eb4 [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.826995] nouveau E[   PIBUS][0000:01:00.0] GPC0: 0x419eb4 0xbadf1000 (0x3800820c)
Sep  7 10:51:29 nanak-P570WM kernel: [   19.827001] nouveau E[   PIBUS][0000:01:00.0] GPC1: 0x419eb4 0xbadf1000 (0x3800820c)
Sep  7 10:51:29 nanak-P570WM kernel: [   19.827007] nouveau E[   PIBUS][0000:01:00.0] GPC2: 0x419eb4 0xbadf1000 (0x3800820c)
Sep  7 10:51:29 nanak-P570WM kernel: [   19.827013] nouveau E[   PIBUS][0000:01:00.0] GPC3: 0x419eb4 0xbadf1000 (0x3800820c)
Sep  7 10:51:29 nanak-P570WM kernel: [   19.827058] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0xc0000000 FAULT at 0x504224 [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.827081] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0xc0000000 FAULT at 0x510824 [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.827104] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0xc0000000 FAULT at 0x519028 [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.827122] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0xc0000000 FAULT at 0x410070 [ IBUS ]
Sep  7 10:51:29 nanak-P570WM kernel: [   19.827129] nouveau E[    PBUS][0000:01:00.0] MMIO write of 0xffffffff FAULT at 0x400130 [ IBUS ]




Also at times my machine hangs in between and then i have to force it to power off using hard power restart.

System configuration



jagat@nanak-P570WM:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Xeon E5/Core i7 DMI2 [8086:3c00] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
00:02.0 PCI bridge [0604]: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 2a [8086:3c04] (rev 07)
    Kernel driver in use: pcieport
00:03.0 PCI bridge [0604]: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 3a in PCI Express Mode [8086:3c08] (rev 07)
    Kernel driver in use: pcieport
00:05.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Address Map, VTd_Misc, System Management [8086:3c28] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
00:05.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Control Status and Global Errors [8086:3c2a] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
00:05.4 PIC [0800]: Intel Corporation Xeon E5/Core i7 I/O APIC [8086:3c2c] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
00:11.0 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Virtual Root Port [8086:1d3e] (rev 06)
    Kernel driver in use: pcieport
00:16.0 Communication controller [0780]: Intel Corporation C600/X79 series chipset MEI Controller #1 [8086:1d3a] (rev 05)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: mei_me
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 06)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #2 [8086:1d2d] (rev 06)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation C600/X79 series chipset High Definition Audio Controller [8086:1d20] (rev 06)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 1 [8086:1d10] (rev b6)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 2 [8086:1d12] (rev b6)
    Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 3 [8086:1d14] (rev b6)
    Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 4 [8086:1d16] (rev b6)
    Kernel driver in use: pcieport
00:1c.7 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 8 [8086:1d1e] (rev b6)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #1 [8086:1d26] (rev 06)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation C600/X79 series chipset LPC Controller [8086:1d41] (rev 06)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation C600/X79 series chipset 6-Port SATA AHCI Controller [8086:1d02] (rev 06)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation C600/X79 series chipset SMBus Host Controller [8086:1d22] (rev 06)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK104M [GeForce GTX 780M] [10de:119f] (rev a1)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation GK104 HDMI Audio Controller [10de:0e0a] (rev a1)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: snd_hda_intel
04:00.0 USB controller [0c03]: Texas Instruments TUSB73x0 SuperSpeed USB 3.0 xHCI Host Controller [104c:8241] (rev 02)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: xhci_hcd
05:00.0 PCI bridge [0604]: Texas Instruments XIO2213A/B/XIO2221 PCI Express to PCI Bridge [Cheetah Express] [104c:823e] (rev 01)
06:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments XIO2213A/B/XIO2221 IEEE-1394b OHCI Controller [Cheetah Express] [104c:823f] (rev 01)
    Kernel driver in use: firewire_ohci
07:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
    Kernel driver in use: iwlwifi
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229]
    Kernel driver in use: rtsx_pci
ff:08.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link 0 [8086:3c80] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:08.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link Reut 0 [8086:3c83] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:08.4 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link Reut 0 [8086:3c84] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:09.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link 1 [8086:3c90] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:09.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link Reut 1 [8086:3c93] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:09.4 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link Reut 1 [8086:3c94] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0a.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Power Control Unit 0 [8086:3cc0] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0a.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Power Control Unit 1 [8086:3cc1] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0a.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Power Control Unit 2 [8086:3cc2] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0a.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Power Control Unit 3 [8086:3cd0] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0b.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Interrupt Control Registers [8086:3ce0] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0b.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Semaphore and Scratchpad Configuration Registers [8086:3ce3] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0c.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0c.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0c.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0c.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 0 [8086:3cf4] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0c.7 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 System Address Decoder [8086:3cf6] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0d.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0d.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0d.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0d.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 1 [8086:3cf5] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0e.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Processor Home Agent [8086:3ca0] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0e.1 Performance counters [1101]: Intel Corporation Xeon E5/Core i7 Processor Home Agent Performance Monitoring [8086:3c46] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: snbep_uncore
ff:0f.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Registers [8086:3ca8] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0f.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller RAS Registers [8086:3c71] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0f.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 0 [8086:3caa] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0f.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 1 [8086:3cab] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0f.4 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 2 [8086:3cac] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0f.5 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 3 [8086:3cad] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:0f.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 4 [8086:3cae] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:10.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 0 [8086:3cb0] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: snbep_uncore
ff:10.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 1 [8086:3cb1] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: snbep_uncore
ff:10.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 0 [8086:3cb2] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:10.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 1 [8086:3cb3] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:10.4 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 2 [8086:3cb4] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: snbep_uncore
ff:10.5 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 3 [8086:3cb5] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: snbep_uncore
ff:10.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 2 [8086:3cb6] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:10.7 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 3 [8086:3cb7] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:11.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DDRIO [8086:3cb8] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:13.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 R2PCIe [8086:3ce4] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:13.1 Performance counters [1101]: Intel Corporation Xeon E5/Core i7 Ring to PCI Express Performance Monitor [8086:3c43] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: snbep_uncore
ff:13.4 Performance counters [1101]: Intel Corporation Xeon E5/Core i7 QuickPath Interconnect Agent Ring Registers [8086:3ce6] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
ff:13.5 Performance counters [1101]: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 0 Performance Monitor [8086:3c44] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: snbep_uncore
ff:13.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 1 Performance Monitor [8086:3c45] (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0270]
    Kernel driver in use: snbep_uncore
jagat@nanak-P570WM:~$

---

### Post by jagat2 on 2013-10-28
Sorry for bumping the thread.

Can i request attention of yours to guide me on this error.

My machine is freezing frequently and which i have to hard boot from power button. I can see my var log spammed with error messages like above.

Please let me know if you need additional logs.

Thank you

---

### Post by be.nicolas.michel on 2014-01-05
Hello,

I also have a NVIDIA GK104 and I can't make it working correctly with the nouveau driver (the default open-source one). So you should install the propriatary driver from nvidia. You can do it going to the "control pannel"/software source and then click on the tab : "additional drivers" and select the appropriate nvidia driver.

---

