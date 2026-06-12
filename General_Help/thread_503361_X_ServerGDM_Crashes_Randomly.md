---
title: "X Server/GDM Crashes Randomly"
date: 2007-07-17
forum: General Help
---

### Post by asutula on 2007-07-17
I've been trying to get Feisty running on my computer, but my X server/GDM will randomly crash on me returning me to the login screen. I can't find much of a pattern to this behaviour. Sometimes it will run fine for many hours or a couple days before crashing.

Here is my hardware:
    *MSI K9N Diamond Motherboard (AM2)
    * AMD Athalon 64 X2 4600+ CPU
    * 2 DDR2 800 MHz 1 GB memory modules
    * eVGA e-GeForce 7600GS graphics card (nvidia)
    * Pioneer SATA DVDRW optical drive
    * Seagate 320 GB SATA hard drive
    * Aspire 420 W power supply
    * Dell 2007WFP monitor

I am running i386 Feisty. I do have the Nvidia driver installed, but I have experienced the same crashes in the past without the driver installed.

Here are the contents of various log files leading up to a crash:

Xorg.0.log (notice the backtrace at the bottom):
```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux shambhala 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 16 07:08:37 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation G70 [GeForce 7600 GS]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
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
(II) PCI: 00:00:0: chip 10de,02f4 card 1462,7226 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 1462,7226 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 1462,7226 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 1462,7226 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 1462,7226 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 1462,7226 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 1462,7226 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 1462,7226 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:08:0: chip 10de,0369 card 1462,7226 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0360 card 1462,7226 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:09:1: chip 10de,0368 card 1462,7226 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:0a:0: chip 10de,036c card 1462,7226 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:0a:1: chip 10de,036d card 1462,7226 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:0c:0: chip 10de,036e card 1462,7226 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0d:0: chip 10de,037f card 1462,7226 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:0d:1: chip 10de,037f card 1462,7226 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:0d:2: chip 10de,037f card 1462,7226 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:0e:0: chip 10de,0370 card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:0: chip 10de,0373 card 1462,058c rev a2 class 06,80,00 hdr 00
(II) PCI: 00:12:0: chip 10de,0376 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:13:0: chip 10de,0374 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:14:0: chip 10de,0374 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:15:0: chip 10de,0378 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:16:0: chip 10de,0375 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:17:0: chip 10de,0377 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 03:00:0: chip 10de,0392 card 3842,c541 rev a1 class 03,00,00 hdr 00
(II) PCI: 04:05:0: chip 1102,0007 card 1462,1009 rev 00 class 04,01,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:4:0), (0,3,3), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfc000000 - 0xfebfffff (0x2c00000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:9:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:14:0), (0,4,4), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:18:0), (0,5,5), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:19:0), (0,6,6), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:20:0), (0,7,7), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 8: bridge is at (0:21:0), (0,8,8), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 9: bridge is at (0:22:0), (0,9,9), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 10: bridge is at (0:23:0), (0,10,10), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,10), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(3:0:0) nVidia Corporation G70 [GeForce 7600 GS] rev 161, Mem @ 0xfd000000/24, 0xd0000000/28, 0xfc000000/24, I/O @ 0xdc00/7, BIOS @ 0xfebe0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfbffa400 - 0xfbffa40f (0x10) MX[B]
	[1] -1	0	0xfbffa800 - 0xfbffa8ff (0x100) MX[B]
	[2] -1	0	0xfbff6000 - 0xfbff6fff (0x1000) MX[B]
	[3] -1	0	0xfbff7000 - 0xfbff7fff (0x1000) MX[B]
	[4] -1	0	0xfbff8000 - 0xfbff8fff (0x1000) MX[B]
	[5] -1	0	0xfbff9000 - 0xfbff9fff (0x1000) MX[B]
	[6] -1	0	0xfbffac00 - 0xfbffacff (0x100) MX[B]
	[7] -1	0	0xfbffb000 - 0xfbffbfff (0x1000) MX[B]
	[8] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[13] -1	0	0x0000a480 - 0x0000a487 (0x8) IX[B]
	[14] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[15] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[16] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[18] -1	0	0x0000b080 - 0x0000b087 (0x8) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[20] -1	0	0x0000b480 - 0x0000b483 (0x4) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[22] -1	0	0x0000b880 - 0x0000b883 (0x4) IX[B]
	[23] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[25] -1	0	0x0000c080 - 0x0000c083 (0x4) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[27] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[28] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[31] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[32] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfbffa400 - 0xfbffa40f (0x10) MX[B]
	[1] -1	0	0xfbffa800 - 0xfbffa8ff (0x100) MX[B]
	[2] -1	0	0xfbff6000 - 0xfbff6fff (0x1000) MX[B]
	[3] -1	0	0xfbff7000 - 0xfbff7fff (0x1000) MX[B]
	[4] -1	0	0xfbff8000 - 0xfbff8fff (0x1000) MX[B]
	[5] -1	0	0xfbff9000 - 0xfbff9fff (0x1000) MX[B]
	[6] -1	0	0xfbffac00 - 0xfbffacff (0x100) MX[B]
	[7] -1	0	0xfbffb000 - 0xfbffbfff (0x1000) MX[B]
	[8] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[13] -1	0	0x0000a480 - 0x0000a487 (0x8) IX[B]
	[14] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[15] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[16] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[18] -1	0	0x0000b080 - 0x0000b087 (0x8) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[20] -1	0	0x0000b480 - 0x0000b483 (0x4) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[22] -1	0	0x0000b880 - 0x0000b883 (0x4) IX[B]
	[23] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[25] -1	0	0x0000c080 - 0x0000c083 (0x4) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[27] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[28] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[31] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[32] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbffa400 - 0xfbffa40f (0x10) MX[B]
	[5] -1	0	0xfbffa800 - 0xfbffa8ff (0x100) MX[B]
	[6] -1	0	0xfbff6000 - 0xfbff6fff (0x1000) MX[B]
	[7] -1	0	0xfbff7000 - 0xfbff7fff (0x1000) MX[B]
	[8] -1	0	0xfbff8000 - 0xfbff8fff (0x1000) MX[B]
	[9] -1	0	0xfbff9000 - 0xfbff9fff (0x1000) MX[B]
	[10] -1	0	0xfbffac00 - 0xfbffacff (0x100) MX[B]
	[11] -1	0	0xfbffb000 - 0xfbffbfff (0x1000) MX[B]
	[12] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[19] -1	0	0x0000a480 - 0x0000a487 (0x8) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[21] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[22] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[24] -1	0	0x0000b080 - 0x0000b087 (0x8) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[26] -1	0	0x0000b480 - 0x0000b483 (0x4) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[28] -1	0	0x0000b880 - 0x0000b883 (0x4) IX[B]
	[29] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[30] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[31] -1	0	0x0000c080 - 0x0000c083 (0x4) IX[B]
	[32] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[33] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[34] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[35] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[36] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[37] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[38] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
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
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 18:58:58 PDT 2007
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
	compiled for 4.0.2, module version = 1.0.0
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
(II) NVIDIA dlloader X Driver  100.14.11  Wed Jun 13 18:23:34 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbffa400 - 0xfbffa40f (0x10) MX[B]
	[5] -1	0	0xfbffa800 - 0xfbffa8ff (0x100) MX[B]
	[6] -1	0	0xfbff6000 - 0xfbff6fff (0x1000) MX[B]
	[7] -1	0	0xfbff7000 - 0xfbff7fff (0x1000) MX[B]
	[8] -1	0	0xfbff8000 - 0xfbff8fff (0x1000) MX[B]
	[9] -1	0	0xfbff9000 - 0xfbff9fff (0x1000) MX[B]
	[10] -1	0	0xfbffac00 - 0xfbffacff (0x100) MX[B]
	[11] -1	0	0xfbffb000 - 0xfbffbfff (0x1000) MX[B]
	[12] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[19] -1	0	0x0000a480 - 0x0000a487 (0x8) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[21] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[22] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[24] -1	0	0x0000b080 - 0x0000b087 (0x8) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[26] -1	0	0x0000b480 - 0x0000b483 (0x4) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[28] -1	0	0x0000b880 - 0x0000b883 (0x4) IX[B]
	[29] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[30] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[31] -1	0	0x0000c080 - 0x0000c083 (0x4) IX[B]
	[32] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[33] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[34] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[35] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[36] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[37] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[38] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbffa400 - 0xfbffa40f (0x10) MX[B]
	[5] -1	0	0xfbffa800 - 0xfbffa8ff (0x100) MX[B]
	[6] -1	0	0xfbff6000 - 0xfbff6fff (0x1000) MX[B]
	[7] -1	0	0xfbff7000 - 0xfbff7fff (0x1000) MX[B]
	[8] -1	0	0xfbff8000 - 0xfbff8fff (0x1000) MX[B]
	[9] -1	0	0xfbff9000 - 0xfbff9fff (0x1000) MX[B]
	[10] -1	0	0xfbffac00 - 0xfbffacff (0x100) MX[B]
	[11] -1	0	0xfbffb000 - 0xfbffbfff (0x1000) MX[B]
	[12] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[22] -1	0	0x0000a480 - 0x0000a487 (0x8) IX[B]
	[23] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[24] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[25] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[27] -1	0	0x0000b080 - 0x0000b087 (0x8) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[29] -1	0	0x0000b480 - 0x0000b483 (0x4) IX[B]
	[30] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[31] -1	0	0x0000b880 - 0x0000b883 (0x4) IX[B]
	[32] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[33] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[34] -1	0	0x0000c080 - 0x0000c083 (0x4) IX[B]
	[35] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[36] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[37] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[38] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[39] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[40] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[41] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS (G73) at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.51.01
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:3:0:0:
(--) NVIDIA(0):     DELL 2007WFP (DFP-0)
(--) NVIDIA(0): DELL 2007WFP (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL 2007WFP (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1680x1050"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (99, 98); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfbffa400 - 0xfbffa40f (0x10) MX[B]
	[8] -1	0	0xfbffa800 - 0xfbffa8ff (0x100) MX[B]
	[9] -1	0	0xfbff6000 - 0xfbff6fff (0x1000) MX[B]
	[10] -1	0	0xfbff7000 - 0xfbff7fff (0x1000) MX[B]
	[11] -1	0	0xfbff8000 - 0xfbff8fff (0x1000) MX[B]
	[12] -1	0	0xfbff9000 - 0xfbff9fff (0x1000) MX[B]
	[13] -1	0	0xfbffac00 - 0xfbffacff (0x100) MX[B]
	[14] -1	0	0xfbffb000 - 0xfbffbfff (0x1000) MX[B]
	[15] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[16] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] 0	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[26] -1	0	0x0000a480 - 0x0000a487 (0x8) IX[B]
	[27] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[28] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[29] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[31] -1	0	0x0000b080 - 0x0000b087 (0x8) IX[B]
	[32] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[33] -1	0	0x0000b480 - 0x0000b483 (0x4) IX[B]
	[34] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[35] -1	0	0x0000b880 - 0x0000b883 (0x4) IX[B]
	[36] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[37] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[38] -1	0	0x0000c080 - 0x0000c083 (0x4) IX[B]
	[39] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[40] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[41] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[42] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[43] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[44] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[45] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
	[46] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[47] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1680x1050"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
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
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/X11R6/bin/X(Dispatch+0x15b) [0x808c5db]
3: /usr/X11R6/bin/X(main+0x495) [0x8074785]
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7cfaebc]
5: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11.  Server aborting
```
gdm/:0.log (notice the backtrace at the bottom):
```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux shambhala 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 16 07:08:37 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/X11R6/bin/X(Dispatch+0x15b) [0x808c5db]
3: /usr/X11R6/bin/X(main+0x495) [0x8074785]
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7cfaebc]
5: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11.  Server aborting
```
syslog:
```
Jul 16 23:17:01 shambhala /USR/SBIN/CRON[3165]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 16 23:21:21 shambhala gconfd (aaron-7085): Received signal 15, shutting down cleanly
Jul 16 23:21:21 shambhala gconfd (aaron-7085): Exiting
Jul 16 23:21:21 shambhala gdm[7005]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
```
messages:
```
Jul 16 23:21:21 shambhala gconfd (aaron-7085): Received signal 15, shutting down cleanly
Jul 16 23:21:21 shambhala gconfd (aaron-7085): Exiting
```
user.log
```
Jul 16 23:21:21 shambhala gconfd (aaron-7085): Received signal 15, shutting down cleanly
Jul 16 23:21:21 shambhala gconfd (aaron-7085): Exiting
```
daemon.log:
```
Jul 16 23:21:21 shambhala gdm[7005]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
```

Here is my xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 84.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GS]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

It seems like the backtrace in gdm/:0.log and Xorg.0.log could be useful information, but I don't know how to make any sense of it. Could this be a hardware issue (so far all my tests say no)? Any ideas why my X server keeps crashing?

Thank you for your help.

- Aaron

---

