---
title: "how to install a specific nvidia driver"
date: 2018-03-04
forum: General Help
---

### Post by cptcondor on 2018-03-04
I have used the recommended methods of retrieving the most current nvidia drivers 3 or 4 times now (with Internet connection) and each time it has soft locked my computer and resulted in full reinstalls of my Ubuntu 16.04. 
I have downloaded the most recent driver for my specific hard ware and the operating system as far as I am aware.
I have run into the same issue as this post that i cannot install it due to invalid characters.
[https://ubuntuforums.org/showthread.php?t=2268330]("https://ubuntuforums.org/showthread.php?t=2268330")
The goal of this post is to get THIS downloaded driver to work or use an apt-get command to get to the specific driver I need. The automated update or current command has locked me out of my computer.
the solutions in this post are different because they are going for an offline solution that i do not need and confused as to what action ***I*** should take.
here is my hardware that this post recommended I find to help find a solution that is right for my build.
```
 linux@linuxtop:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
	Subsystem: Micro-Star International Co., Ltd. [MSI] 4th Gen Core Processor DRAM Controller [1462:7850]
	Kernel driver in use: hsw_uncore
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:02.0 Display controller [0380]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0402] (rev 06)
	DeviceName:  Onboard IGD
	Subsystem: Micro-Star International Co., Ltd. [MSI] Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [1462:7850]
	Kernel driver in use: i915
	Kernel modules: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [1462:7850]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:14.0 USB controller [0c03]: Intel Corporation 9 Series Chipset Family USB xHCI Controller [8086:8cb1]
	Subsystem: Micro-Star International Co., Ltd. [MSI] 9 Series Chipset Family USB xHCI Controller [1462:7850]
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 9 Series Chipset Family ME Interface #1 [8086:8cba]
	Subsystem: Micro-Star International Co., Ltd. [MSI] 9 Series Chipset Family ME Interface [1462:7850]
	Kernel driver in use: mei_me
	Kernel modules: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2 [8086:8cad]
	Subsystem: Micro-Star International Co., Ltd. [MSI] 9 Series Chipset Family USB EHCI Controller [1462:7850]
	Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 9 Series Chipset Family HD Audio Controller [8086:8ca0]
	Subsystem: Micro-Star International Co., Ltd. [MSI] 9 Series Chipset Family HD Audio Controller [1462:d850]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 [8086:8c90] (rev d0)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.6 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d0)
00:1d.0 USB controller [0c03]: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1 [8086:8ca6]
	Subsystem: Micro-Star International Co., Ltd. [MSI] 9 Series Chipset Family USB EHCI Controller [1462:7850]
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation 9 Series Chipset Family Z97 LPC Controller [8086:8cc4]
	Subsystem: Micro-Star International Co., Ltd. [MSI] 9 Series Chipset Family Z97 LPC Controller [1462:7850]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode] [8086:8c82]
	Subsystem: Micro-Star International Co., Ltd. [MSI] 9 Series Chipset Family SATA Controller [AHCI Mode] [1462:7850]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 9 Series Chipset Family SMBus Controller [8086:8ca2]
	Subsystem: Micro-Star International Co., Ltd. [MSI] 9 Series Chipset Family SMBus Controller [1462:7850]
	Kernel modules: i2c_i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] [10de:1380] (rev a2)
	Subsystem: eVga.com. Corp. GM107 [GeForce GTX 750 Ti] [3842:3753]
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fbc] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:3753]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
03:00.0 PCI bridge [0604]: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge [1b21:1080] (rev 03)
	Kernel modules: shpchp
04:00.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
	Subsystem: Linksys RT2800 802.11n PCI [1737:0067]
	Kernel driver in use: rt2800pci
	Kernel modules: rt2800pci 
```

---

### Post by deadflowr on 2018-03-04
Post the results of
```
ubuntu-drivers devices
```

---

