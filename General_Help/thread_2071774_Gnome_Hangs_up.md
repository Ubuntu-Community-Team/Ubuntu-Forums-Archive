---
title: "Gnome Hangs up?"
date: 2012-10-16
forum: General Help
---

### Post by riomus on 2012-10-16
Hardware:
Ubuntu 12.04 + Gnome-shell
i7 x64
ATI 5870m, ATI 12.06
8GB RAM
1TB Dysk

Problem
[https://dl.dropbox.com/u/27614504/Screenshots/2012101638.png]("https://dl.dropbox.com/u/27614504/Screenshots/2012101638.png")
Sometimes system randomly stop response, i can move my cursor and it changes over elements but i can't do anything , after switch to tty and back some thing like this showes up(Screen, shortcuts are working).Only way i found is to switch to tty and use killall5. Pleas help me, i'm quite new. Sorry for my english.

---

### Post by duanedesign on 2012-10-16
Hi,
What graphics card driver are you using?
If you run the following command and look for video controller/VGA:

```
lspci -v
```

This information might help find a bug or others with your problem and possibly a solution.
Does the system freeze when the screensaver is starting or when it is trying to go to sleep?
You might check the Power Management settings and switch off any screensaver or sleep settings.

Their is more info on gathering info and updating your kernel here:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

EDIT:
Looks like some people with ATI cards on UBuntu 12.04 solved their X freezing issue by using the driver from here:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Thanks,
Duane

---

### Post by riomus on 2012-10-16
I'm using driver from there.
Here is lscpi -v
```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
	Subsystem: ASUSTeK Computer Inc. Device 1c77
	Flags: fast devsel
	Capabilities: <access denied>

00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: c0000000-d00fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
	Subsystem: Device 0043:0077
	Flags: fast devsel
	Capabilities: <access denied>

00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
	Subsystem: Device 0043:0077
	Flags: fast devsel
	Capabilities: <access denied>

00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
	Subsystem: Device 0043:0077
	Flags: fast devsel
	Capabilities: <access denied>

00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
	Subsystem: Device 0043:0077
	Flags: fast devsel

00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
	Subsystem: Device 0043:0077
	Flags: fast devsel

00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
	Subsystem: Device 0043:0077
	Flags: fast devsel

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 1c77
	Flags: bus master, fast devsel, latency 0, IRQ 50
	Memory at d3e0a000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1c77
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at d3e08000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 1373
	Flags: bus master, fast devsel, latency 0, IRQ 51
	Memory at d3e00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: d2a00000-d3dfffff
	Prefetchable memory behind bridge: 00000000d4300000-00000000d44fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: d1600000-d29fffff
	Prefetchable memory behind bridge: 00000000d4100000-00000000d42fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: d0200000-d15fffff
	Prefetchable memory behind bridge: 00000000d3f00000-00000000d40fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1c77
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d3e07000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 1c77
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Device 1c77
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 49
	I/O ports at e070 [size=8]
	I/O ports at e060 [size=4]
	I/O ports at e050 [size=8]
	I/O ports at e040 [size=4]
	I/O ports at e020 [size=32]
	Memory at d3e06000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 1c77
	Flags: medium devsel, IRQ 10
	Memory at d3e05000 (64-bit, non-prefetchable) [size=256]
	I/O ports at e000 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Broadway XT [Mobility Radeon HD 5800 Series] (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 1c02
	Flags: bus master, fast devsel, latency 0, IRQ 54
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0020000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at d000 [size=256]
	Expansion ROM at d0000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Juniper HDMI Audio [Radeon HD 5700 Series]
	Subsystem: ASUSTeK Computer Inc. Device aa58
	Flags: bus master, fast devsel, latency 0, IRQ 52
	Memory at d0040000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card
	Physical Slot: 1
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d1600000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

04:00.0 Ethernet controller: Atheros Communications Inc. AR8131 Gigabit Ethernet (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device 1820
	Physical Slot: 5
	Flags: bus master, fast devsel, latency 0, IRQ 53
	Memory at d0200000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at a000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: atl1c
	Kernel modules: atl1c

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0
	Kernel modules: i7core_edac

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

```

Whene error will came up again i will collect dmesg and xorg log

DMESG and XOrg.log
 [https://dl.dropbox.com/u/27614504/Xorg.0.log](https://dl.dropbox.com/u/27614504/Xorg.0.log)
 [https://dl.dropbox.com/u/27614504/dmesg.txt](https://dl.dropbox.com/u/27614504/dmesg.txt)
When there is a freeze sound is working correct. Can any one help?

---

