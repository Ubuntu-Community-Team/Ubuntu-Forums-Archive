---
title: "PCIe Bus Error: severity=Corrected"
date: 2019-03-06
forum: General Help
---

### Post by VMC on 2019-03-06
This is a know issue for a couple of years now. I see erroneous comments on what's causing the error. See the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173") on what's causing the issue and how to prevent the errors hogging dmesg.
[pcie wireless mainly]

If you have wireless check dmesg: ```
dmesg | grep pcie
```
> [ 3056.549121] pcieport 0000:00:1c.0: AER: Corrected error received: 0000:00:1c.0[ 3056.549136] pcieport 0000:00:1c.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Transmitter ID)
[ 3056.549147] pcieport 0000:00:1c.0:   device [8086:a33d] error status/mask=00001000/00002000
[ 3056.549154] pcieport 0000:00:1c.0:    [12] Timeout               
================


00:1c.0 0604: 8086:a33d (rev f0) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 122
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: a2100000-a21fffff
        Prefetchable memory behind bridge: 00000000a0000000-00000000a00fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
=================
lspci -s 000:00:1c.0
00:1c.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port (rev f0)
=================
$ lspci -vt
-[0000:00]-+-00.0  Intel Corporation 8th Gen Core Processor Host Bridge/DRAM Registers
           +-02.0  Intel Corporation UHD Graphics 630 (Desktop)
           +-08.0  Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
           +-12.0  Intel Corporation Cannon Lake PCH Thermal Controller
           +-14.0  Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller
           +-14.2  Intel Corporation Cannon Lake PCH Shared SRAM
           +-14.3  Intel Corporation Wireless-AC 9560 [Jefferson Peak]
           +-16.0  Intel Corporation Cannon Lake PCH HECI Controller
           +-17.0  Intel Corporation SATA Controller [RAID mode]
           +-1c.0-[01]----00.0  Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           +-1f.0  Intel Corporation Device a308
           +-1f.3  Intel Corporation Cannon Lake PCH cAVS
           +-1f.4  Intel Corporation Cannon Lake PCH SMBus Controller
           \-1f.5  Intel Corporation Cannon Lake PCH SPI Controller

---

