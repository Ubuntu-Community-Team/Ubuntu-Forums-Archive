---
title: "Firefox and Evolution causing PC to freeze"
date: 2016-01-23
forum: General Help
---

### Post by Jonners59 on 2016-01-23
My PC has been running like a pig.  I started another thread ([http://ubuntuforums.org/showthread.php?t=2308934](http://ubuntuforums.org/showthread.php?t=2308934)), but from that I have diognosed that the route cause is Firefox and Evolution.

Any suggestions.

Latest 15:10 SW release of Ubuntu.

```
[COLOR=#111111][FONT=Consolas]uname-a
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]Linuxbaronipc 4.2.0-18-generic #22-Ubuntu SMP Fri Nov 6 18:25:50 UTC 2015x86_64 x86_64 x86_64 GNU/Linux[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=Ubuntu Mono]lspci
 -v00:00.0 Host bridge:Intel Corporation 2nd Generation Core Processor Family DRAMController (rev 09)[/FONT][/COLOR][COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Subsystem: ASUSTeKComputer Inc. P8P67/P8H67 Series Motherboard[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: snb_uncore[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]00:01.0 PCI bridge:Intel Corporation Xeon E3-1200/2nd Generation Core Processor FamilyPCI Express Root Port (rev 09) (prog-if 00 [Normal decode])[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0, IRQ 24[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Bus: primary=00,secondary=01, subordinate=01, sec-latency=0[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O behind bridge:0000e000-0000efff[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory behindbridge: fa000000-fb0fffff[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Prefetchable memorybehind bridge: 00000000c0000000-00000000d1ffffff[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: pcieport[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]00:16.0Communication controller: Intel Corporation 6 Series/C200 SeriesChipset Family MEI Controller #1 (rev 04)[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Subsystem: ASUSTeKComputer Inc. P8 series motherboard[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0, IRQ 40[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory at fb408000(64-bit, non-prefetchable) [size=16][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: mei_me[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]00:1a.0 USBcontroller: Intel Corporation 6 Series/C200 Series Chipset Family USBEnhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Subsystem: ASUSTeKComputer Inc. P8 series motherboard[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,medium devsel, latency 0, IRQ 23[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory at fb407000(32-bit, non-prefetchable) [size=1K][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: ehci-pci[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]00:1b.0 Audiodevice: Intel Corporation 6 Series/C200 Series Chipset Family HighDefinition Audio Controller (rev 05)[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Subsystem: ASUSTeKComputer Inc. Device 8469[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0, IRQ 41[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory at fb400000(64-bit, non-prefetchable) [size=16K][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: snd_hda_intel[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]00:1c.0 PCI bridge:Intel Corporation 6 Series/C200 Series Chipset Family PCI ExpressRoot Port 1 (rev b5) (prog-if 00 [Normal decode])[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0, IRQ 25[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Bus: primary=00,secondary=02, subordinate=02, sec-latency=0[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: pcieport[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]00:1c.2 PCI bridge:Intel Corporation 6 Series/C200 Series Chipset Family PCI ExpressRoot Port 3 (rev b5) (prog-if 00 [Normal decode])[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0, IRQ 26[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Bus: primary=00,secondary=03, subordinate=03, sec-latency=0[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: pcieport[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]00:1c.3 PCI bridge:Intel Corporation 6 Series/C200 Series Chipset Family PCI ExpressRoot Port 4 (rev b5) (prog-if 00 [Normal decode])[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0, IRQ 27[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Bus: primary=00,secondary=04, subordinate=04, sec-latency=0[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: pcieport[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]00:1c.4 PCI bridge:Intel Corporation 6 Series/C200 Series Chipset Family PCI ExpressRoot Port 5 (rev b5) (prog-if 00 [Normal decode])[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0, IRQ 28[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Bus: primary=00,secondary=05, subordinate=05, sec-latency=0[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O behind bridge:0000d000-0000dfff[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory behindbridge: fb300000-fb3fffff[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: pcieport[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]00:1c.5 PCI bridge:Intel Corporation 6 Series/C200 Series Chipset Family PCI ExpressRoot Port 6 (rev b5) (prog-if 00 [Normal decode])[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0, IRQ 29[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Bus: primary=00,secondary=06, subordinate=06, sec-latency=0[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O behind bridge:0000c000-0000cfff[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Prefetchable memorybehind bridge: 00000000d2100000-00000000d21fffff[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: pcieport[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]00:1c.6 PCI bridge:Intel Corporation 6 Series/C200 Series Chipset Family PCI ExpressRoot Port 7 (rev b5) (prog-if 00 [Normal decode])[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0, IRQ 30[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Bus: primary=00,secondary=07, subordinate=07, sec-latency=0[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O behind bridge:0000b000-0000bfff[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory behindbridge: fb200000-fb2fffff[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: pcieport[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]00:1c.7 PCI bridge:Intel Corporation 6 Series/C200 Series Chipset Family PCI ExpressRoot Port 8 (rev b5) (prog-if 00 [Normal decode])[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0, IRQ 31[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Bus: primary=00,secondary=08, subordinate=08, sec-latency=0[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory behindbridge: fb100000-fb1fffff[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: pcieport[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]00:1d.0 USBcontroller: Intel Corporation 6 Series/C200 Series Chipset Family USBEnhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Subsystem: ASUSTeKComputer Inc. P8 series motherboard[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,medium devsel, latency 0, IRQ 23[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory at fb406000(32-bit, non-prefetchable) [size=1K][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: ehci-pci[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]00:1f.0 ISA bridge:Intel Corporation P67 Express Chipset Family LPC Controller (rev 05)[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Subsystem: ASUSTeKComputer Inc. P8P67 Deluxe Motherboard[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,medium devsel, latency 0[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: lpc_ich[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]00:1f.2 SATAcontroller: Intel Corporation 6 Series/C200 Series Chipset FamilySATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Subsystem: ASUSTeKComputer Inc. P8 series motherboard[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,66MHz, medium devsel, latency 0, IRQ 38[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O ports at f070[size=8][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O ports at f060[size=4][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O ports at f050[size=8][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O ports at f040[size=4][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O ports at f020[size=32][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory at fb405000(32-bit, non-prefetchable) [size=2K][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: ahci[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]00:1f.3 SMBus: IntelCorporation 6 Series/C200 Series Chipset Family SMBus Controller (rev05)[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Subsystem: ASUSTeKComputer Inc. P8 series motherboard[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: mediumdevsel, IRQ 10[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory at fb404000(64-bit, non-prefetchable) [size=256][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O ports at f000[size=32][/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]01:00.0 VGAcompatible controller: NVIDIA Corporation GK107 [GeForce GTX 650](rev a1) (prog-if 00 [VGA controller])[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Subsystem: GigabyteTechnology Co., Ltd Device 362b[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0, IRQ 42[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory at fa000000(32-bit, non-prefetchable) [size=16M][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory at c0000000(64-bit, prefetchable) [size=256M][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory at d0000000(64-bit, prefetchable) [size=32M][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O ports at e000[size=128][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace][virtual] ExpansionROM at fb000000 [disabled] [size=512K][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: nvidia[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]01:00.1 Audiodevice: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Subsystem: GigabyteTechnology Co., Ltd Device 362b[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0, IRQ 17[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory at fb080000(32-bit, non-prefetchable) [size=16K][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: snd_hda_intel[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]05:00.0 FireWire(IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller(rev 01) (prog-if 10 [OHCI])[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Subsystem: ASUSTeKComputer Inc. P8P67 Deluxe Motherboard[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0, IRQ 16[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory at fb300000(64-bit, non-prefetchable) [size=2K][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O ports at d000[size=256][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: firewire_ohci[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]06:00.0 Ethernetcontroller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCIExpress Gigabit Ethernet Controller (rev 06)[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Subsystem: ASUSTeKComputer Inc. P8P67 and other motherboards[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0, IRQ 37[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O ports at c000[size=256][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory at d2104000(64-bit, prefetchable) [size=4K][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory at d2100000(64-bit, prefetchable) [size=16K][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: r8169[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]07:00.0 IDEinterface: Marvell Technology Group Ltd. 88SE912x SATA 6Gb/sController [IDE mode] (rev 12) (prog-if 8f [Master SecP SecO PriPPriO])[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Subsystem: ASUSTeKComputer Inc. Device 83ba[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0, IRQ 39[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O ports at b090[size=8][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O ports at b080[size=4][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O ports at b070[size=8][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O ports at b060[size=4][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]I/O ports at b050[size=16][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory at fb215000(32-bit, non-prefetchable) [size=2K][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Expansion ROM atfb200000 [disabled] [size=64K][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Kernel driver inuse: ahci[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]08:00.0 USBcontroller: ASMedia Technology Inc. ASM1042 SuperSpeed USB HostController (prog-if 30 [XHCI])[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Subsystem: ASUSTeKComputer Inc. P8B WS Motherboard[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Flags: bus master,fast devsel, latency 0, IRQ 19[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Memory at fb100000(64-bit, non-prefetchable) [size=32K][/FONT][/COLOR]
[COLOR=#000000]        [FONT=Ubuntu Mono, monospace]Capabilities:<access denied>[/FONT][/COLOR] [COLOR=#000000]        [/COLOR][FONT=Ubuntu Mono, monospace][COLOR=#000000]Kernel driver inuse: xhci_hcd
[/COLOR][/FONT]
```

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo fdisk -l[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono, monospace][sudo] password forbaronipc: [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/ram0: 64MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/ram1: 64MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/ram2: 64MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/ram3: 64MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/ram4: 64MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/ram5: 64MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/ram6: 64MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/ram7: 64MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/ram8: 64MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/ram9: 64MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/ram10: 64MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/ram11: 64MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/ram12: 64MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/ram13: 64MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/ram14: 64MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/ram15: 64MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/sda: 465.8GiB, 500106780160 bytes, 976771055 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disklabel type: dos[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk identifier:0x0009f620[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Device     Boot    Start       End   Sectors   Size Id Type[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]/dev/sda1             63  78116863  78116801  37.3G 83 Linux[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]/dev/sda3       78116864 771809279 693692416 330.8G  7 HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]/dev/sda4      771813374 976766500 204953127  97.7G  5 Extended[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]/dev/sda5  *   771813376 976766500 204953125  97.7G 83 Linux[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk /dev/sdb: 232.9GiB, 250059350016 bytes, 488397168 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Units: sectors of 1* 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Sector size(logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]I/O size(minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disklabel type: dos[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]Disk identifier:0x000a9a63[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Mono, monospace]Device     Boot    Start       End   Sectors   Size Id Type[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]/dev/sdb1           2048 307734527 307732480 146.8G  7 HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]/dev/sdb2      402946048 467871743  64925696    31G 83 Linux[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono, monospace]/dev/sdb3  *   307734528 402946047  95211520  45.4G 83 Linux[/FONT][/COLOR] [COLOR=#000000][FONT=Ubuntu Mono]/dev/sdb4      467871744 488390655  20518912   9.8G 82 Linux swap / Solaris[/FONT][/COLOR]
```

---

