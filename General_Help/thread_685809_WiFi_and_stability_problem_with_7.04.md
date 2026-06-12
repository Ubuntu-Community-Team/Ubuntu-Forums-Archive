---
title: "WiFi and stability problem with 7.04"
date: 2008-02-02
forum: General Help
---

### Post by NCLI on 2008-02-02
Ok, I just downgraded(complete format and clean install) from 7.10 to 7.04, after tiring of a lot of unstability and bugs.

A short while after booting Linux completely(all programs loaded, etc), the system starts slowing to a grinding halt whenever I try to enter text. The text appears after 10-20 seconds of unresponsiveness, and the problem doesn't go away untill I reboot the system.

When I reboot xserver, I get a message saying: "[random-number]HDC: Not ready for command"

This message repeats a few times, then the xserver reboots, but the problem doesn't go away.

I think Firefox is the culprit, as the problem doesn't occur unless I start it.

Also, I just found out my wireless network card doesn't work now, though it did last time I installed 7.04. It shows the nearby access points, but won't connect, and claims all of the connections are at 0%.


...for some reason it works fine right now(Firefox, not the wireless)

I wonder how long it'll last.

Here's the output of lspci -v:
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: bus master, 66MHz, fast devsel, latency 0
Capabilities: [44] HyperTransport: Slave or Primary Interface
Capabilities: [e0] HyperTransport: MSI Mapping

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: bus master, 66MHz, fast devsel, latency 0
Capabilities: [44] #00 [0000]

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
I/O behind bridge: 0000b000-0000bfff
Memory behind bridge: f8c00000-f8cfffff
Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
Capabilities: [48] Power Management version 2
Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
Capabilities: [60] HyperTransport: MSI Mapping
Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
I/O behind bridge: 0000c000-0000cfff
Memory behind bridge: f8d00000-f94fffff
Prefetchable memory behind bridge: 00000000bbf00000-00000000bdefffff
Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
Capabilities: [48] Power Management version 2
Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
Capabilities: [60] HyperTransport: MSI Mapping
Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
Memory behind bridge: f9500000-fd5fffff
Prefetchable memory behind bridge: 00000000bdf00000-00000000ddefffff
Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
Capabilities: [48] Power Management version 2
Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
Capabilities: [60] HyperTransport: MSI Mapping
Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: bus master, 66MHz, fast devsel, latency 0
Capabilities: [44] HyperTransport: Slave or Primary Interface
Capabilities: [e0] HyperTransport: MSI Mapping

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: 66MHz, fast devsel, IRQ 5
I/O ports at 5000 [size=64]
I/O ports at 6000 [size=64]
Capabilities: [44] Power Management version 2

00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
Memory at fdfc0000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
Memory at fdfbe000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [44] Power Management version 2

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
Memory at fdfbfc00 (32-bit, non-prefetchable) [size=256]
Capabilities: [44] Debug port
Capabilities: [80] Power Management version 2

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: bus master, 66MHz, fast devsel, latency 0
[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
I/O ports at ffa0 [size=16]
Capabilities: [44] Power Management version 2

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
I/O ports at e800 [size=8]
I/O ports at e480 [size=4]
I/O ports at e400 [size=8]
I/O ports at e080 [size=4]
I/O ports at e000 [size=16]
Memory at fdfbd000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [44] Power Management version 2
Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
Capabilities: [cc] HyperTransport: MSI Mapping

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
Flags: bus master, 66MHz, fast devsel, latency 0
Bus: primary=00, secondary=05, subordinate=09, sec-latency=64
I/O behind bridge: 0000d000-0000dfff
Memory behind bridge: fd600000-fdefffff
Prefetchable memory behind bridge: ddf00000-dfefffff
Capabilities: [b8] Subsystem: nVidia Corporation Unknown device cb84
Capabilities: [8c] HyperTransport: MSI Mapping

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
Memory at fdfb8000 (32-bit, non-prefetchable) [size=16K]
Capabilities: [44] Power Management version 2
Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
Capabilities: [6c] HyperTransport: MSI Mapping

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
Flags: fast devsel
Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
Flags: fast devsel
Capabilities: [f0] #0f [0010]

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fcc
Flags: bus master, fast devsel, latency 0, IRQ 18
I/O ports at b800 [size=256]
Memory at f8cff000 (64-bit, non-prefetchable) [size=4K]
Expansion ROM at f8ce0000 [disabled] [size=64K]
Capabilities: [40] Power Management version 2
Capabilities: [48] Vital Product Data
Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
Capabilities: [60] Express Endpoint IRQ 0
Capabilities: [84] Vendor Specific Information

04:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1) (prog-if 00 [VGA])
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: bus master, fast devsel, latency 0, IRQ 10
Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
Memory at c0000000 (64-bit, prefetchable) [size=256M]
Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
Expansion ROM at fd5e0000 [disabled] [size=128K]
Capabilities: [60] Power Management version 2
Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
Capabilities: [78] Express Endpoint IRQ 0

05:04.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: bus master, stepping, slow devsel, latency 168, IRQ 16
Memory at fd600000 (32-bit, non-prefetchable) [size=4K]
Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
Memory window 0: 50000000-53fff000 (prefetchable)
Memory window 1: 54000000-57fff000
I/O window 0: 0000d000-0000d0ff
I/O window 1: 0000d400-0000d4ff
16-bit legacy interface ports at 0001

05:04.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: slow devsel, IRQ 16
Memory at fdefe400 (32-bit, non-prefetchable) [size=256]
Capabilities: [a0] Power Management version 2

05:04.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
Subsystem: Micro-Star International Co., Ltd. Unknown device 3fdf
Flags: slow devsel, IRQ 10
Memory at fdefd000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [a0] Power Management version 2

05:04.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10 [OHCI])
Subsystem: O2 Micro, Inc. Firewire (IEEE 1394)
Flags: bus master, medium devsel, latency 64, IRQ 16
Memory at fdeff000 (32-bit, non-prefetchable) [size=4K]
Memory at fdefe800 (32-bit, non-prefetchable) [size=2K]
Capabilities: [60] Power Management version 2

05:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
Subsystem: Micro-Star International Co., Ltd. Unknown 802.11g mini-PCI Adapter
Flags: bus master, slow devsel, latency 64, IRQ 20
Memory at fdefa000 (32-bit, non-prefetchable) [size=8K]
Capabilities: [40] Power Management version 2
```

And /var/log/Xorg.0.log while the problem is present:
```
]X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux seph-laptop 2.6.20-16-generic #2 SMP Tue Dec 18 05:45:12 UTC 2007 i686
Build Date: 18 January 2008
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb 2 18:24:57 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) | |-->Monitor "Generic Monitor"
(**) | |-->Device "nVidia Corporation G72M [GeForce Go 7400]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
Entry deleted from font path.
(**) FontPath set to:
/usr/share/fonts/X11/misc,
/usr/share/fonts/X11/100dpi/:unscaled,
/usr/share/fonts/X11/75dpi/:unscaled,
/usr/share/fonts/X11/Type1,
/usr/share/fonts/X11/100dpi,
/usr/share/fonts/X11/75dpi,
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
/usr/share/fonts/X11/misc,
/usr/X11R6/lib/X11/fonts/misc,
/usr/share/fonts/X11/cyrillic,
/usr/share/fonts/X11/100dpi/:unscaled,
/usr/share/fonts/X11/75dpi/:unscaled,
/usr/share/fonts/X11/Type1,
/usr/X11R6/lib/X11/fonts/Type1,
/usr/share/fonts/X11/100dpi,
/usr/share/fonts/X11/75dpi,
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
X.Org ANSI C Emulation: 0.3
X.Org Video Driver: 1.1
X.Org XInput driver : 0.7
X.Org Server Extension : 0.3
X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.0.0
ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,02f7 card 1462,3fdf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 1462,3fdf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 1462,3fdf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 1462,3fdf rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 1462,3fdf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 1462,3fdf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 1462,3fdf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0270 card 1462,3fdf rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0260 card 1462,3fdf rev a3 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 1462,3fdf rev a3 class 0c,05,00 hdr 80
(II) PCI: 00:0a:3: chip 10de,0271 card 1462,3fdf rev a3 class 0b,40,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 1462,3fdf rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 1462,3fdf rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 1462,3fdf rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 1462,3fdf rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 1462,3fdf rev a2 class 04,03,00 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10ec,8168 card 1462,3fcc rev 01 class 02,00,00 hdr 00
(II) PCI: 04:00:0: chip 10de,01d8 card 1462,3fdf rev a1 class 03,00,00 hdr 00
(II) PCI: 05:04:0: chip 1217,7134 card d001,0000 rev 21 class 06,07,00 hdr 82
(II) PCI: 05:04:2: chip 1217,7120 card 1462,3fdf rev 01 class 08,05,00 hdr 00
(II) PCI: 05:04:3: chip 1217,7130 card 1462,3fdf rev 01 class 06,80,00 hdr 00
(II) PCI: 05:04:4: chip 1217,00f7 card 1217,00f7 rev 02 class 0c,00,10 hdr 00
(II) PCI: 05:09:0: chip 1814,0201 card 1462,6833 rev 01 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
[0] -1 0 0x0000b000 - 0x0000bfff (0x1000) IX[b]
(II) Bus 1 non-prefetchable memory range:
[0] -1 0 0xf8c00000 - 0xf8cfffff (0x100000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
[0] -1 0 0x0000c000 - 0x0000cfff (0x1000) IX[b]
(II) Bus 2 non-prefetchable memory range:
[0] -1 0 0xf8d00000 - 0xf94fffff (0x800000) MX[b]
(II) Bus 2 prefetchable memory range:
[0] -1 0 0xbbf00000 - 0xbdefffff (0x2000000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:4:0), (0,4,4), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 4 non-prefetchable memory range:
[0] -1 0 0xf9500000 - 0xfd5fffff (0x4100000) MX[b]
(II) Bus 4 prefetchable memory range:
[0] -1 0 0xbdf00000 - 0xddefffff (0x20000000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:16:0), (0,5,9), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 5 I/O range:
[0] -1 0 0x0000d000 - 0x0000dfff (0x1000) IX[b]
(II) Bus 5 non-prefetchable memory range:
[0] -1 0 0xfd600000 - 0xfdefffff (0x900000) MX[b]
(II) Bus 5 prefetchable memory range:
[0] -1 0 0xddf00000 - 0xdfefffff (0x2000000) MX[b]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
[0] -1 0 0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
[0] -1 0 0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
[0] -1 0 0x00000000 - 0xffffffff (0x0) MX[b]
(II) PCI-to-CardBus bridge:
(II) Bus 6: bridge is at (5:4:0), (5,6,9), BCTRL: 0x05c3 (VGA_EN is cleared)
(II) Bus 6 I/O range:
[0] -1 0 0x0000d000 - 0x0000d0ff (0x100) IX[b]
[1] -1 0 0x0000d400 - 0x0000d4ff (0x100) IX[b]
(--) PCI: (0:10:3) nVidia Corporation MCP51 PMU rev 163, Mem @ 0xfdfc0000/18
(--) PCI:*(4:0:0) nVidia Corporation GeForce Go 7400 rev 161, Mem @ 0xfc000000/24, 0xc0000000/28, 0xfb000000/24, BIOS @ 0xfd5e0000/17
(II) Addressable bus resource ranges are
[0] -1 0 0x00000000 - 0xffffffff (0x0) MX[b]
[1] -1 0 0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[5] -1 0 0x00000000 - 0x000000ff (0x100) IX[b]
(II) Active PCI resource ranges:
[0] -1 0 0xfdefa000 - 0xfdefbfff (0x2000) MX[b]
[1] -1 0 0xfdefe800 - 0xfdefefff (0x800) MX[b]
[2] -1 0 0xfdeff000 - 0xfdefffff (0x1000) MX[b]
[3] -1 0 0xfdefd000 - 0xfdefdfff (0x1000) MX[b]
[4] -1 0 0xfdefe400 - 0xfdefe4ff (0x100) MX[b]
[5] -1 0 0xf8cff000 - 0xf8cfffff (0x1000) MX[b]
[6] -1 0 0xfdfb8000 - 0xfdfbbfff (0x4000) MX[b]
[7] -1 0 0xfdfbd000 - 0xfdfbdfff (0x1000) MX[b]
[8] -1 0 0xfdfbfc00 - 0xfdfbfcff (0x100) MX[b]
[9] -1 0 0xfdfbe000 - 0xfdfbefff (0x1000) MX[b]
[10] -1 0 0xfd5e0000 - 0xfd5fffff (0x20000) MX[b](B)
[11] -1 0 0xfb000000 - 0xfbffffff (0x1000000) MX[b](B)
[12] -1 0 0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
[13] -1 0 0xfc000000 - 0xfcffffff (0x1000000) MX[b](B)
[14] -1 0 0xfdfc0000 - 0xfdffffff (0x40000) MX[b]
[15] -1 0 0x0000b800 - 0x0000b8ff (0x100) IX[b]
[16] -1 0 0x0000e000 - 0x0000e00f (0x10) IX[b]
[17] -1 0 0x0000e080 - 0x0000e083 (0x4) IX[b]
[18] -1 0 0x0000e400 - 0x0000e407 (0x8) IX[b]
[19] -1 0 0x0000e480 - 0x0000e483 (0x4) IX[b]
[20] -1 0 0x0000e800 - 0x0000e807 (0x8) IX[b]
[21] -1 0 0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
[22] -1 0 0x00006000 - 0x0000603f (0x40) IX[b]
[23] -1 0 0x00005000 - 0x0000503f (0x40) IX[b]
(II) Active PCI resource ranges after removing overlaps:
[0] -1 0 0xfdefa000 - 0xfdefbfff (0x2000) MX[b]
[1] -1 0 0xfdefe800 - 0xfdefefff (0x800) MX[b]
[2] -1 0 0xfdeff000 - 0xfdefffff (0x1000) MX[b]
[3] -1 0 0xfdefd000 - 0xfdefdfff (0x1000) MX[b]
[4] -1 0 0xfdefe400 - 0xfdefe4ff (0x100) MX[b]
[5] -1 0 0xf8cff000 - 0xf8cfffff (0x1000) MX[b]
[6] -1 0 0xfdfb8000 - 0xfdfbbfff (0x4000) MX[b]
[7] -1 0 0xfdfbd000 - 0xfdfbdfff (0x1000) MX[b]
[8] -1 0 0xfdfbfc00 - 0xfdfbfcff (0x100) MX[b]
[9] -1 0 0xfdfbe000 - 0xfdfbefff (0x1000) MX[b]
[10] -1 0 0xfd5e0000 - 0xfd5fffff (0x20000) MX[b](B)
[11] -1 0 0xfb000000 - 0xfbffffff (0x1000000) MX[b](B)
[12] -1 0 0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
[13] -1 0 0xfc000000 - 0xfcffffff (0x1000000) MX[b](B)
[14] -1 0 0xfdfc0000 - 0xfdffffff (0x40000) MX[b]
[15] -1 0 0x0000b800 - 0x0000b8ff (0x100) IX[b]
[16] -1 0 0x0000e000 - 0x0000e00f (0x10) IX[b]
[17] -1 0 0x0000e080 - 0x0000e083 (0x4) IX[b]
[18] -1 0 0x0000e400 - 0x0000e407 (0x8) IX[b]
[19] -1 0 0x0000e480 - 0x0000e483 (0x4) IX[b]
[20] -1 0 0x0000e800 - 0x0000e807 (0x8) IX[b]
[21] -1 0 0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
[22] -1 0 0x00006000 - 0x0000603f (0x40) IX[b]
[23] -1 0 0x00005000 - 0x0000503f (0x40) IX[b]
(II) OS-reported resource ranges after removing overlaps with PCI:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[5] -1 0 0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0xfdefa000 - 0xfdefbfff (0x2000) MX[b]
[5] -1 0 0xfdefe800 - 0xfdefefff (0x800) MX[b]
[6] -1 0 0xfdeff000 - 0xfdefffff (0x1000) MX[b]
[7] -1 0 0xfdefd000 - 0xfdefdfff (0x1000) MX[b]
[8] -1 0 0xfdefe400 - 0xfdefe4ff (0x100) MX[b]
[9] -1 0 0xf8cff000 - 0xf8cfffff (0x1000) MX[b]
[10] -1 0 0xfdfb8000 - 0xfdfbbfff (0x4000) MX[b]
[11] -1 0 0xfdfbd000 - 0xfdfbdfff (0x1000) MX[b]
[12] -1 0 0xfdfbfc00 - 0xfdfbfcff (0x100) MX[b]
[13] -1 0 0xfdfbe000 - 0xfdfbefff (0x1000) MX[b]
[14] -1 0 0xfd5e0000 - 0xfd5fffff (0x20000) MX[b](B)
[15] -1 0 0xfb000000 - 0xfbffffff (0x1000000) MX[b](B)
[16] -1 0 0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
[17] -1 0 0xfc000000 - 0xfcffffff (0x1000000) MX[b](B)
[18] -1 0 0xfdfc0000 - 0xfdffffff (0x40000) MX[b]
[19] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[20] -1 0 0x00000000 - 0x000000ff (0x100) IX[b]
[21] -1 0 0x0000b800 - 0x0000b8ff (0x100) IX[b]
[22] -1 0 0x0000e000 - 0x0000e00f (0x10) IX[b]
[23] -1 0 0x0000e080 - 0x0000e083 (0x4) IX[b]
[24] -1 0 0x0000e400 - 0x0000e407 (0x8) IX[b]
[25] -1 0 0x0000e480 - 0x0000e483 (0x4) IX[b]
[26] -1 0 0x0000e800 - 0x0000e807 (0x8) IX[b]
[27] -1 0 0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
[28] -1 0 0x00006000 - 0x0000603f (0x40) IX[b]
[29] -1 0 0x00005000 - 0x0000503f (0x40) IX[b]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.2.0
ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.0.0
ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.0.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
compiled for 7.2.0, module version = 2.1.0
Module class: X.Org Font Renderer
ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
compiled for 4.0.2, module version = 1.0.9631
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.0.0
ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.1.0
ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
compiled for 4.0.2, module version = 1.0.9631
Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.1.0
Module class: X.Org XInput Driver
ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.1.1
Module class: X.Org XInput Driver
ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
compiled for 4.3.99.902, module version = 1.0.0
Module class: X.Org XInput Driver
ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
compiled for 4.2.0, module version = 1.0.0
Module class: XFree86 XInput Driver
ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA dlloader X Driver 1.0-9631 Thu Nov 9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 04:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:10:3) found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.0.0
ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 0.1.0
ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0xfdefa000 - 0xfdefbfff (0x2000) MX[b]
[5] -1 0 0xfdefe800 - 0xfdefefff (0x800) MX[b]
[6] -1 0 0xfdeff000 - 0xfdefffff (0x1000) MX[b]
[7] -1 0 0xfdefd000 - 0xfdefdfff (0x1000) MX[b]
[8] -1 0 0xfdefe400 - 0xfdefe4ff (0x100) MX[b]
[9] -1 0 0xf8cff000 - 0xf8cfffff (0x1000) MX[b]
[10] -1 0 0xfdfb8000 - 0xfdfbbfff (0x4000) MX[b]
[11] -1 0 0xfdfbd000 - 0xfdfbdfff (0x1000) MX[b]
[12] -1 0 0xfdfbfc00 - 0xfdfbfcff (0x100) MX[b]
[13] -1 0 0xfdfbe000 - 0xfdfbefff (0x1000) MX[b]
[14] -1 0 0xfd5e0000 - 0xfd5fffff (0x20000) MX[b](B)
[15] -1 0 0xfb000000 - 0xfbffffff (0x1000000) MX[b](B)
[16] -1 0 0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
[17] -1 0 0xfc000000 - 0xfcffffff (0x1000000) MX[b](B)
[18] -1 0 0xfdfc0000 - 0xfdffffff (0x40000) MX[b]
[19] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[20] -1 0 0x00000000 - 0x000000ff (0x100) IX[b]
[21] -1 0 0x0000b800 - 0x0000b8ff (0x100) IX[b]
[22] -1 0 0x0000e000 - 0x0000e00f (0x10) IX[b]
[23] -1 0 0x0000e080 - 0x0000e083 (0x4) IX[b]
[24] -1 0 0x0000e400 - 0x0000e407 (0x8) IX[b]
[25] -1 0 0x0000e480 - 0x0000e483 (0x4) IX[b]
[26] -1 0 0x0000e800 - 0x0000e807 (0x8) IX[b]
[27] -1 0 0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
[28] -1 0 0x00006000 - 0x0000603f (0x40) IX[b]
[29] -1 0 0x00005000 - 0x0000503f (0x40) IX[b]
(II) resource ranges after probing:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0xfdefa000 - 0xfdefbfff (0x2000) MX[b]
[5] -1 0 0xfdefe800 - 0xfdefefff (0x800) MX[b]
[6] -1 0 0xfdeff000 - 0xfdefffff (0x1000) MX[b]
[7] -1 0 0xfdefd000 - 0xfdefdfff (0x1000) MX[b]
[8] -1 0 0xfdefe400 - 0xfdefe4ff (0x100) MX[b]
[9] -1 0 0xf8cff000 - 0xf8cfffff (0x1000) MX[b]
[10] -1 0 0xfdfb8000 - 0xfdfbbfff (0x4000) MX[b]
[11] -1 0 0xfdfbd000 - 0xfdfbdfff (0x1000) MX[b]
[12] -1 0 0xfdfbfc00 - 0xfdfbfcff (0x100) MX[b]
[13] -1 0 0xfdfbe000 - 0xfdfbefff (0x1000) MX[b]
[14] -1 0 0xfd5e0000 - 0xfd5fffff (0x20000) MX[b](B)
[15] -1 0 0xfb000000 - 0xfbffffff (0x1000000) MX[b](B)
[16] -1 0 0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
[17] -1 0 0xfc000000 - 0xfcffffff (0x1000000) MX[b](B)
[18] -1 0 0xfdfc0000 - 0xfdffffff (0x40000) MX[b]
[19] 0 0 0x000a0000 - 0x000affff (0x10000) MS[b]
[20] 0 0 0x000b0000 - 0x000b7fff (0x8000) MS[b]
[21] 0 0 0x000b8000 - 0x000bffff (0x8000) MS[b]
[22] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[23] -1 0 0x00000000 - 0x000000ff (0x100) IX[b]
[24] -1 0 0x0000b800 - 0x0000b8ff (0x100) IX[b]
[25] -1 0 0x0000e000 - 0x0000e00f (0x10) IX[b]
[26] -1 0 0x0000e080 - 0x0000e083 (0x4) IX[b]
[27] -1 0 0x0000e400 - 0x0000e407 (0x8) IX[b]
[28] -1 0 0x0000e480 - 0x0000e483 (0x4) IX[b]
[29] -1 0 0x0000e800 - 0x0000e807 (0x8) IX[b]
[30] -1 0 0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
[31] -1 0 0x00006000 - 0x0000603f (0x40) IX[b]
[32] -1 0 0x00005000 - 0x0000503f (0x40) IX[b]
[33] 0 0 0x000003b0 - 0x000003bb (0xc) IS[b]
[34] 0 0 0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0): enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce Go 7400 at PCI:4:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.56.07
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 7400 at PCI:4:0:0:
(--) NVIDIA(0): Seiko (DFP-0)
(--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): "1280x800"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0): option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC? No, I don't.
(II) resource ranges after preInit:
[0] 0 0 0xfb000000 - 0xfbffffff (0x1000000) MX[b]
[1] 0 0 0xc0000000 - 0xcfffffff (0x10000000) MX[b]
[2] 0 0 0xfc000000 - 0xfcffffff (0x1000000) MX[b]
[3] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
[4] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[5] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[6] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[7] -1 0 0xfdefa000 - 0xfdefbfff (0x2000) MX[b]
[8] -1 0 0xfdefe800 - 0xfdefefff (0x800) MX[b]
[9] -1 0 0xfdeff000 - 0xfdefffff (0x1000) MX[b]
[10] -1 0 0xfdefd000 - 0xfdefdfff (0x1000) MX[b]
[11] -1 0 0xfdefe400 - 0xfdefe4ff (0x100) MX[b]
[12] -1 0 0xf8cff000 - 0xf8cfffff (0x1000) MX[b]
[13] -1 0 0xfdfb8000 - 0xfdfbbfff (0x4000) MX[b]
[14] -1 0 0xfdfbd000 - 0xfdfbdfff (0x1000) MX[b]
[15] -1 0 0xfdfbfc00 - 0xfdfbfcff (0x100) MX[b]
[16] -1 0 0xfdfbe000 - 0xfdfbefff (0x1000) MX[b]
[17] -1 0 0xfd5e0000 - 0xfd5fffff (0x20000) MX[b](B)
[18] -1 0 0xfb000000 - 0xfbffffff (0x1000000) MX[b](B)
[19] -1 0 0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
[20] -1 0 0xfc000000 - 0xfcffffff (0x1000000) MX[b](B)
[21] -1 0 0xfdfc0000 - 0xfdffffff (0x40000) MX[b]
[22] 0 0 0x000a0000 - 0x000affff (0x10000) MS[b](OprD)
[23] 0 0 0x000b0000 - 0x000b7fff (0x8000) MS[b](OprD)
[24] 0 0 0x000b8000 - 0x000bffff (0x8000) MS[b](OprD)
[25] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[26] -1 0 0x00000000 - 0x000000ff (0x100) IX[b]
[27] -1 0 0x0000b800 - 0x0000b8ff (0x100) IX[b]
[28] -1 0 0x0000e000 - 0x0000e00f (0x10) IX[b]
[29] -1 0 0x0000e080 - 0x0000e083 (0x4) IX[b]
[30] -1 0 0x0000e400 - 0x0000e407 (0x8) IX[b]
[31] -1 0 0x0000e480 - 0x0000e483 (0x4) IX[b]
[32] -1 0 0x0000e800 - 0x0000e807 (0x8) IX[b]
[33] -1 0 0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
[34] -1 0 0x00006000 - 0x0000603f (0x40) IX[b]
[35] -1 0 0x00005000 - 0x0000503f (0x40) IX[b]
[36] 0 0 0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
[37] 0 0 0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) NVIDIA(0): Setting mode "1280x800"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "dk"
(**) Generic Keyboard: XkbLayout: "dk"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 18 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
SetGrabKeysState - disabled
SetGrabKeysState - enabled
```

---

### Post by NCLI on 2008-02-02
"bump"

---

### Post by NCLI on 2008-02-03
"bump"

---

