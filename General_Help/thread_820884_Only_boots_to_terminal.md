---
title: "Only boots to terminal"
date: 2008-06-06
forum: General Help
---

### Post by ludicrous on 2008-06-06
My computer was acting a little sluggish. I tried to open up a terminal and it wouldn't open- 'Opening terminal' would show up in the bar at the bottom of the screen briefly, then close. I rebooted, and it now only boots to a terminal.  

The only thing I can think of that may have caused this is the normal updates I installed yesterday.

Any ideas? Thanks.

---

### Post by VMC on 2008-06-06
> **ludicrous said:**
> My computer was acting a little sluggish. I tried to open up a terminal and it wouldn't open- 'Opening terminal' would show up in the bar at the bottom of the screen briefly, then close. I rebooted, and it now only boots to a terminal.  

The only thing I can think of that may have caused this is the normal updates I installed yesterday.

Any ideas? Thanks.

Have you tried 'startx' in the terminal to see if xorg will start? What options , if any, does Grub give.

---

### Post by ludicrous on 2008-06-06
startx didn't work. Here is the log from the attempt-
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux ubuntu 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun  6 20:37:08 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 103c,30bb rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 103c,30bb rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 103c,30bb rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 103c,30bb rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 103c,30bb rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 103c,30bb rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 103c,30bb rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 103c,30bb rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 103c,30bb rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c5 card 103c,30bb rev 02 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 103c,30bb rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,01d8 card 103c,30bb rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 8086,4222 card 103c,135b rev 02 class 02,80,00 hdr 00
(II) PCI: 05:00:0: chip 8086,109a card 103c,30bb rev 00 class 02,00,00 hdr 00
(II) PCI: 07:05:0: chip 1180,0832 card 103c,30bb rev 00 class 0c,00,10 hdr 80
(II) PCI: 07:05:1: chip 1180,0822 card 103c,30bb rev 19 class 08,05,00 hdr 80
(II) PCI: 07:05:2: chip 1180,0592 card 103c,30bb rev 0a class 08,80,00 hdr 80
(II) PCI: 07:05:3: chip 1180,0852 card 103c,30bb rev 05 class 08,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xd9ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xd6000000 - 0xd7ffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:2), (0,5,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xda000000 - 0xdbffffff (0x2000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xd4000000 - 0xd5ffffff (0x2000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:30:0), (0,7,7), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xde000000 - 0xde0fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation G72M [GeForce Go 7400] rev 161, Mem @ 0xdd000000/24, 0xc0000000/28, 0xdc000000/24
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
	[0] -1	0	0xde000800 - 0xde0008ff (0x100) MX[B]
	[1] -1	0	0xde000000 - 0xde0007ff (0x800) MX[B]
	[2] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B]
	[3] -1	0	0xd8000000 - 0xd8000fff (0x1000) MX[B]
	[4] -1	0	0xde304400 - 0xde3047ff (0x400) MX[B]
	[5] -1	0	0xde304000 - 0xde3043ff (0x400) MX[B]
	[6] -1	0	0xde300000 - 0xde303fff (0x4000) MX[B]
	[7] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[10] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[11] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[12] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[13] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[14] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[15] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[16] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[17] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[23] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[24] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[25] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xde001000 - 0xde0010ff (0x100) MX[B]
	[1] -1	0	0xde000c00 - 0xde000cff (0x100) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xde000800 - 0xde0008ff (0x100) MX[B]
	[1] -1	0	0xde000000 - 0xde0007ff (0x800) MX[B]
	[2] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B]
	[3] -1	0	0xd8000000 - 0xd8000fff (0x1000) MX[B]
	[4] -1	0	0xde304400 - 0xde3047ff (0x400) MX[B]
	[5] -1	0	0xde304000 - 0xde3043ff (0x400) MX[B]
	[6] -1	0	0xde300000 - 0xde303fff (0x4000) MX[B]
	[7] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[10] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[11] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[12] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[13] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[14] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[15] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[16] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[17] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[23] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[24] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[25] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xde001000 - 0xde0010ff (0x100) MX[B]
	[1] -1	0	0xde000c00 - 0xde000cff (0x100) MX[B]
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
	[4] -1	0	0xde000800 - 0xde0008ff (0x100) MX[B]
	[5] -1	0	0xde000000 - 0xde0007ff (0x800) MX[B]
	[6] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B]
	[7] -1	0	0xd8000000 - 0xd8000fff (0x1000) MX[B]
	[8] -1	0	0xde304400 - 0xde3047ff (0x400) MX[B]
	[9] -1	0	0xde304000 - 0xde3043ff (0x400) MX[B]
	[10] -1	0	0xde300000 - 0xde303fff (0x4000) MX[B]
	[11] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xde001000 - 0xde0010ff (0x100) MX[B]
	[15] -1	0	0xde000c00 - 0xde000cff (0x100) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[19] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[22] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[23] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[24] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[25] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[31] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[32] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[33] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched nv from file name nv.ids in autoconfig
(==) Matched nv for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.1.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
	GeForce 8600 GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 8600M GT,
	GeForce 8700M GT, Quadro FX 370, Quadro NVS 320M, Quadro FX 570M,
	Quadro FX 1600M, Quadro FX 570, Quadro FX 1700, GeForce 8500 GT,
	GeForce 8400 GS, GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS,
	GeForce 8400M GT, GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M,
	Quadro NVS 130M, Quadro NVS 135M, Quadro FX 360M, Quadro NVS 290,
	GeForce 8800 GT, GeForce 8800 GS, GeForce 8800 GS, GeForce 8800 GT,
	Quadro FX 3700, GeForce 9600 GT, GeForce 8400 GS
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset GeForce Go 7400 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xde000800 - 0xde0008ff (0x100) MX[B]
	[5] -1	0	0xde000000 - 0xde0007ff (0x800) MX[B]
	[6] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B]
	[7] -1	0	0xd8000000 - 0xd8000fff (0x1000) MX[B]
	[8] -1	0	0xde304400 - 0xde3047ff (0x400) MX[B]
	[9] -1	0	0xde304000 - 0xde3043ff (0x400) MX[B]
	[10] -1	0	0xde300000 - 0xde303fff (0x4000) MX[B]
	[11] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xde001000 - 0xde0010ff (0x100) MX[B]
	[15] -1	0	0xde000c00 - 0xde000cff (0x100) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[19] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[22] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[23] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[24] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[25] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[31] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[32] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[33] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xde000800 - 0xde0008ff (0x100) MX[B]
	[5] -1	0	0xde000000 - 0xde0007ff (0x800) MX[B]
	[6] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B]
	[7] -1	0	0xd8000000 - 0xd8000fff (0x1000) MX[B]
	[8] -1	0	0xde304400 - 0xde3047ff (0x400) MX[B]
	[9] -1	0	0xde304000 - 0xde3043ff (0x400) MX[B]
	[10] -1	0	0xde300000 - 0xde303fff (0x4000) MX[B]
	[11] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xde001000 - 0xde0010ff (0x100) MX[B]
	[15] -1	0	0xde000c00 - 0xde000cff (0x100) MX[B]
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[22] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[23] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[24] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[25] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[26] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[27] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[28] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[34] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[35] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[36] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce Go 7400"
(II) NV(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (==) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xC0000000
(--) NV(0): MMIO registers at 0xDD000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 0
(--) NV(0): Panel size is 1280 x 800
(II) NV(0): Panel is LVDS
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Configured Monitor: Using hsync range of 0.00-49.31 kHz
(II) NV(0): Configured Monitor: Using vrefresh range of 0.00-59.91 Hz
(WW) NV(0): Unable to estimate virtual size
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "832x624" (vrefresh out of range)
(II) NV(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) NV(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) NV(0): Virtual size is 1280x800 (pitch 1280)
(**) NV(0): *Driver mode "1280x800": 71.0 MHz, 49.3 kHz, 59.9 Hz
(II) NV(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(**) NV(0): *Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(**) NV(0): *Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(**) NV(0): *Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) NV(0): Modeline "1152x768"x54.8   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync (44.2 kHz)
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(==) NV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xdd000000 - 0xddffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xde000800 - 0xde0008ff (0x100) MX[B]
	[8] -1	0	0xde000000 - 0xde0007ff (0x800) MX[B]
	[9] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B]
	[10] -1	0	0xd8000000 - 0xd8000fff (0x1000) MX[B]
	[11] -1	0	0xde304400 - 0xde3047ff (0x400) MX[B]
	[12] -1	0	0xde304000 - 0xde3043ff (0x400) MX[B]
	[13] -1	0	0xde300000 - 0xde303fff (0x4000) MX[B]
	[14] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[17] -1	0	0xde001000 - 0xde0010ff (0x100) MX[B]
	[18] -1	0	0xde000c00 - 0xde000cff (0x100) MX[B]
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00004000 - 0x0000401f (0x20) IX[B]
	[25] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[26] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[27] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[28] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[29] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[30] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[31] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[37] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[38] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[39] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xc0000000,0x8000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(II) NV(0): DPMS enabled
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
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
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
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
SetClientVersion: 0 9
```

GRUB gives me 3 kernal versions for ubuntu and associated recovery modes, and Vista.

---

### Post by ludicrous on 2008-06-06
Also, when I booted with recovery mode and picked the option to continue a normal boot, I could see 
```
GNOME Desktop Manager             [fail]
```
as it was attempting to boot.
And, um, something about GLX and my Nvidia card... I can get that verbatim next time I try it.

---

### Post by ludicrous on 2008-06-07
Here are the contents of my ~/.xsession-errors:
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/rob-laptop:/tmp/.ICE-unix/5727
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:01d8 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
11


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
starting HAL detection for ac adaptors...found /org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_ACAD
Throttle level is 0
Initializing nautilus-share extension
seahorse nautilus module initialized
evolution-alarm-notify-Message: Setting timeout for 80760 1212796800 1212716040
evolution-alarm-notify-Message:  Fri Jun  6 19:00:00 2008

evolution-alarm-notify-Message:  Thu Jun  5 20:34:00 2008


** (nautilus:5826): WARNING **: Unable to add monitor: Not supported
I/O warning : failed to load external entity "/home/rob/.compiz/session/default0"
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x805e108: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805e108: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805e108: NP_GetValue
GCJ PLUGIN: thread 0x805e108: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805e108: NP_GetValue return
GCJ PLUGIN: thread 0x805e108: NP_GetValue
GCJ PLUGIN: thread 0x805e108: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805e108: NP_GetValue return
  PID TTY          TIME CMD
 5798 ?        00:00:00 pulseaudio

(firefox:6111): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6111): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6111): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6111): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6111): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6111): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x805e108: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805e108: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805e108: NP_GetValue
GCJ PLUGIN: thread 0x805e108: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805e108: NP_GetValue return
GCJ PLUGIN: thread 0x805e108: NP_GetValue
GCJ PLUGIN: thread 0x805e108: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805e108: NP_GetValue return
** Message: NP_Initialize
** Message: NP_Initialize succeeded
** Message: totemPlugin ctor [0xbb9ae88]
** Message: Init mimetype 'video/mp4' mode 1
** Message: Base URI is 'http://www.spaceflightnowplus.com/content.php?i=3363'
** Message: Real mimetype for 'video/mp4' is 'video/mp4'
argv[0] src /plus/p0806/080601externaltank.mp4
argv[1] autoplay true
argv[2] controller true
argv[3] loop false
argv[4] pluginspage http://quicktime.apple.com/
argv[5] height 376
argv[6] width 480
** Message: mSrc: /plus/p0806/080601externaltank.mp4
** Message: mCache: 1
** Message: mControllerHidden: 0
** Message: mShowStatusbar: 0
** Message: mHidden: 0
** Message: mAudioOnly: 0
** Message: mAutostart: 1, mRepeat: 0
** Message: mHref: 
** Message: mTarget: 
** Message: Launching: /usr/lib/totem/gstreamer/totem-plugin-viewer --plugin-type narrowspace --user-agent Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5 --mimetype video/mp4 
** Message: Viewer spawned, PID 8524
** Message: GetValue variable 14 (e)
** Message: Initial window set, XID 28550cb size 480x376
** Message: No viewer proxy yet, deferring SetWindow
** Message: GetValue variable 15 (f)
** Message: Unhandled variable NPPVpluginScriptableNPObject
** Message: GetValue variable 11 (b)
** Message: GetValue variable 268435466 (1000000a)
** Message: GetScriptable [0xbb9ae88]
** Message: totemNarrowSpacePlugin ctor [0xbf69d98]
** Message: Viewer DBus interface name is 'org.gnome.totem.PluginViewer_8524'
** Message: NameOwnerChanged old-owner '' new-owner ':1.31'
** Message: Viewer now connected to the bus
** Message: ViewerSetup
** Message: Calling SetWindow
** Message: NameOwnerChanged old-owner '' new-owner ':1.31'
** Message: Already have owner, why are we notified again?
Viewer: SetWindow XID 42291403 size 480:376
TotemEmbedded-Message: Viewer state: STOPPED
** Message: SetWindow reply
** Message: ViewerReady
** Message: IsSchemeSupported scheme 'http': yes
TotemEmbedded-Message: totem_embedded_open_stream called: uri http://www.spaceflightnowplus.com/plus/p0806/080601externaltank.mp4, base_uri: http://www.spaceflightnowplus.com/content.php?i=3363
TotemEmbedded-Message: totem_embedded_open_internal 'fd://0' is-browser-stream 1 start-play 1
TotemEmbedded-Message: BEFORE _open
TotemEmbedded-Message: AFTER _open (ret: 1)
TotemEmbedded-Message: Viewer state: PLAYING
** Message: OpenStream reply
** Message: URLNotify URL 'http://www.spaceflightnowplus.com/plus/p0806/080601externaltank.mp4' reason 1
TotemEmbedded-Message: totem_embedded_set_error_logo called by browser plugin
TotemEmbedded-Message: Viewer state: STOPPED
TotemEmbedded-Message: Viewer state: PLAYING
TotemEmbedded-Message: Viewer state: PAUSED
TotemEmbedded-Message: Viewer state: PLAYING

(totem-plugin-viewer:8524): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed
** Message: totemPlugin ctor [0xb9b3270]
** Message: Init mimetype 'video/mp4' mode 1
** Message: Base URI is 'http://www.spaceflightnowplus.com/content.php?i=3363'
** Message: Real mimetype for 'video/mp4' is 'video/mp4'
argv[0] src /plus/p0806/080601externaltank.mp4
argv[1] autoplay true
argv[2] controller true
argv[3] loop false
argv[4] pluginspage http://quicktime.apple.com/
argv[5] height 376
argv[6] width 480
** Message: mSrc: /plus/p0806/080601externaltank.mp4
** Message: mCache: 1
** Message: mControllerHidden: 0
** Message: mShowStatusbar: 0
** Message: mHidden: 0
** Message: mAudioOnly: 0
** Message: mAutostart: 1, mRepeat: 0
** Message: mHref: 
** Message: mTarget: 
** Message: Launching: /usr/lib/totem/gstreamer/totem-plugin-viewer --plugin-type narrowspace --user-agent Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5 --mimetype video/mp4 
** Message: Viewer spawned, PID 8542
** Message: GetValue variable 14 (e)
** Message: Initial window set, XID 2856eef size 480x376
** Message: No viewer proxy yet, deferring SetWindow
** Message: GetValue variable 15 (f)
** Message: Unhandled variable NPPVpluginScriptableNPObject
** Message: GetValue variable 11 (b)
** Message: GetValue variable 268435466 (1000000a)
** Message: GetScriptable [0xb9b3270]
** Message: totemNarrowSpacePlugin ctor [0xb949f28]
** Message: totemPlugin dtor [0xbb9ae88]
** Message: Viewer DBus interface name is 'org.gnome.totem.PluginViewer_8542'
** Message: NameOwnerChanged old-owner '' new-owner ':1.32'
** Message: Viewer now connected to the bus
** Message: ViewerSetup
** Message: Calling SetWindow
Viewer: SetWindow XID 42299119 size 480:376
** Message: NameOwnerChanged old-owner '' new-owner ':1.32'
** Message: Already have owner, why are we notified again?
TotemEmbedded-Message: Viewer state: STOPPED
** Message: SetWindow reply
** Message: ViewerReady
** Message: IsSchemeSupported scheme 'http': yes
TotemEmbedded-Message: totem_embedded_open_stream called: uri http://www.spaceflightnowplus.com/plus/p0806/080601externaltank.mp4, base_uri: http://www.spaceflightnowplus.com/content.php?i=3363
TotemEmbedded-Message: totem_embedded_open_internal 'fd://0' is-browser-stream 1 start-play 1
TotemEmbedded-Message: BEFORE _open
TotemEmbedded-Message: AFTER _open (ret: 1)
TotemEmbedded-Message: Viewer state: PLAYING
** Message: OpenStream reply
** Message: URLNotify URL 'http://www.spaceflightnowplus.com/plus/p0806/080601externaltank.mp4' reason 1
TotemEmbedded-Message: totem_embedded_set_error_logo called by browser plugin
TotemEmbedded-Message: Viewer state: STOPPED
** Message: totemPlugin dtor [0xb9b3270]
** Message: NP_Shutdown
** Message: totemNarrowSpacePlugin dtor [0xbf69d98]
** Message: totemNarrowSpacePlugin dtor [0xb949f28]
Error - cannot end transaction. Rolling back...
Error - cannot end transaction. Rolling back...
Error - cannot end transaction. Rolling back...
Error - cannot end transaction. Rolling back...
Error - cannot end transaction. Rolling back...
Error - cannot end transaction. Rolling back...
Error - cannot end transaction. Rolling back...
current dist not found in meta-release file

(firefox:7000): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:7000): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:7000): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:7000): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
gnome-terminal: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_signal_accumulator_true_handled
gnome-terminal: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_signal_accumulator_true_handled
gnome-terminal: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_signal_accumulator_true_handled
gnome-terminal: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_signal_accumulator_true_handled
gnome-terminal: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_signal_accumulator_true_handled
gnome-terminal: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_signal_accumulator_true_handled
gnome-terminal: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_signal_accumulator_true_handled
/usr/lib/gnome-screensaver/gnome-screensaver-gl-helper: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
gconftool-2: symbol lookup error: gconftool-2: undefined symbol: g_option_context_new
Couldn't load XPCOM.
seahorse nautilus module shutdown
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
DBus connection has been lost, trackerd will now shutdown
/usr/bin/gconftool-2: symbol lookup error: /usr/bin/gconftool-2: undefined symbol: g_option_context_new
** Message: Got disconnected from the session message bus; retrying to reconnect every 10 seconds

** (x-session-manager:5727): WARNING **: Running '/usr/bin/gconftool-2 --shutdown' at logout returned an exit status of '32512'
Xsession: X session started for rob at Fri Jun  6 20:29:44 CDT 2008
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/seahorse-agent: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
Xsession: X session started for rob at Fri Jun  6 20:30:36 CDT 2008
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/seahorse-agent: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
Xsession: X session started for rob at Fri Jun  6 20:48:19 CDT 2008
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/seahorse-agent: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
```

---

### Post by spiderbatdad on 2008-06-07
can you get the dmesg log from a boot?

---

### Post by ludicrous on 2008-06-08
dmesg:
```
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe70000 (usable)
[    0.000000]  BIOS-e820: 000000007fe70000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7d10
[    0.000000] Entering add_active_range(0, 0, 523888) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   523888
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   523888
[    0.000000] On node 0 totalpages: 523888
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2300 pages used for memmap
[    0.000000]   HighMem zone: 292212 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7C60 checksum 0
[    0.000000] ACPI: RSDP 000F7C60, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT 7FE7B3D3, 0084 (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP 7FE83BF8, 00F4 (r3 INTEL  CALISTGA  6040000 ALAN        1)
[    0.000000] ACPI: DSDT 7FE7C693, 74F1 (r1 HP     30BC      6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FE84FC0, 0040
[    0.000000] ACPI: APIC 7FE83CEC, 0068 (r1 HP     30BC      6040000 LOHR       5A)
[    0.000000] ACPI: HPET 7FE83D54, 0038 (r1 HP     30BC      6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 7FE83D8C, 003C (r1 HP     30BC      6040000 LOHR       5A)
[    0.000000] ACPI: TCPA 7FE83DC8, 0032 (r1 HP     30BB      6040000  PTL        1)
[    0.000000] ACPI: APIC 7FE83DFA, 0068 (r1 HP     30BC      6040000  LTP        0)
[    0.000000] ACPI: BOOT 7FE83E62, 0028 (r1 HP     30BC      6040000  LTP        1)
[    0.000000] ACPI: SLIC 7FE83E8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: SSDT 7FE7C489, 020A (r1  HP    30BC         1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FE7B9E3, 025F (r1 HP     30BC         3000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FE7B93D, 00A6 (r1 HP     30BC         3000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FE7B457, 04E6 (r1 HP     30BC         3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519796
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1729.593 MHz processor.
[   30.666775] Console: colour VGA+ 80x25
[   30.666778] console [tty0] enabled
[   30.667075] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   30.667453] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   30.790120] Memory: 2065352k/2095552k available (2157k kernel code, 29016k reserved, 998k data, 364k init, 1178048k highmem)
[   30.790129] virtual kernel memory layout:
[   30.790130]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   30.790132]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   30.790133]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   30.790134]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   30.790135]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   30.790137]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   30.790138]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   30.790142] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   30.790182] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   30.790331] hpet clockevent registered
[   30.870327] Calibrating delay using timer specific routine.. 3463.08 BogoMIPS (lpj=6926160)
[   30.870351] Security Framework initialized
[   30.870359] SELinux:  Disabled at boot.
[   30.870374] AppArmor: AppArmor initialized
[   30.870379] Failure registering capabilities with primary security module.
[   30.870387] Mount-cache hash table entries: 512
[   30.870520] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
[   30.870530] monitor/mwait feature present.
[   30.870532] using mwait in idle threads.
[   30.870536] CPU: L1 I cache: 32K, L1 D cache: 32K
[   30.870539] CPU: L2 cache: 2048K
[   30.870541] CPU: Physical Processor ID: 0
[   30.870543] CPU: Processor Core ID: 0
[   30.870545] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
[   30.870555] Compat vDSO mapped to ffffe000.
[   30.870568] Checking 'hlt' instruction... OK.
[   30.886717] SMP alternatives: switching to UP code
[   30.888502] Early unpacking initramfs... done
[   31.256805] ACPI: Core revision 20070126
[   31.256874] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   31.263136] CPU0: Intel(R) Core(TM) Duo CPU      T2250  @ 1.73GHz stepping 0c
[   31.263153] SMP alternatives: switching to SMP code
[   31.263832] Booting processor 1/1 eip 3000
[   31.274098] Initializing CPU#1
[   31.354259] Calibrating delay using timer specific routine.. 3459.11 BogoMIPS (lpj=6918226)
[   31.354266] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
[   31.354272] monitor/mwait feature present.
[   31.354275] CPU: L1 I cache: 32K, L1 D cache: 32K
[   31.354277] CPU: L2 cache: 2048K
[   31.354280] CPU: Physical Processor ID: 0
[   31.354281] CPU: Processor Core ID: 1
[   31.354283] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
[   31.354860] CPU1: Intel(R) Core(TM) Duo CPU      T2250  @ 1.73GHz stepping 0c
[   31.354883] Total of 2 processors activated (6922.19 BogoMIPS).
[   31.355083] ENABLING IO-APIC IRQs
[   31.355279] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   31.502360] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   31.522376] Brought up 2 CPUs
[   31.522402] CPU0 attaching sched-domain:
[   31.522405]  domain 0: span 03
[   31.522407]   groups: 01 02
[   31.522410] CPU1 attaching sched-domain:
[   31.522412]  domain 0: span 03
[   31.522413]   groups: 02 01
[   31.522665] net_namespace: 64 bytes
[   31.522675] Booting paravirtualized kernel on bare hardware
[   31.523169] Time: 11:18:53  Date: 06/08/08
[   31.523198] NET: Registered protocol family 16
[   31.523410] EISA bus registered
[   31.523414] ACPI: bus type pci registered
[   31.523634] PCI: PCI BIOS revision 2.10 entry at 0xfd883, last bus=7
[   31.523637] PCI: Using configuration type 1
[   31.523639] Setting up standard PCI resources
[   31.526193] ACPI: EC: Look up EC in DSDT
[   31.528591] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   31.529038] ACPI: Interpreter enabled
[   31.529042] ACPI: (supports S0 S3 S4 S5)
[   31.529056] ACPI: Using IOAPIC for interrupt routing
[   31.530523] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   31.535098] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[   31.535101] ACPI: EC: driver started in interrupt mode
[   31.535148] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   31.535931] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   31.535936] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   31.537442] PCI: Transparent bridge - 0000:00:1e.0
[   31.537489] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   31.537799] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[   31.537935] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   31.538062] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   31.538185] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   31.538322] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   31.545051] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[   31.545174] ACPI: PCI Interrupt Link [LNKB] (IRQs *3)
[   31.545295] ACPI: PCI Interrupt Link [LNKC] (IRQs *3)
[   31.545415] ACPI: PCI Interrupt Link [LNKD] (IRQs *4)
[   31.545535] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[   31.545656] ACPI: PCI Interrupt Link [LNKF] (IRQs 11) *0, disabled.
[   31.545777] ACPI: PCI Interrupt Link [LNKG] (IRQs *5)
[   31.545897] ACPI: PCI Interrupt Link [LNKH] (IRQs *7)
[   31.546041] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.546073] pnp: PnP ACPI init
[   31.546080] ACPI: bus type pnp registered
[   31.548510] pnp: PnP ACPI: found 11 devices
[   31.548513] ACPI: ACPI bus type pnp unregistered
[   31.548516] PnPBIOS: Disabled by ACPI PNP
[   31.548765] PCI: Using ACPI for IRQ routing
[   31.548767] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   31.594382] NET: Registered protocol family 8
[   31.594384] NET: Registered protocol family 20
[   31.594420] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   31.594425] hpet0: 3 64-bit timers, 14318180 Hz
[   31.595462] AppArmor: AppArmor Filesystem Enabled
[   31.598235] Time: tsc clocksource has been installed.
[   31.598250] Switched to high resolution mode on CPU 0
[   31.598360] Switched to high resolution mode on CPU 1
[   31.607230] system 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
[   31.607237] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[   31.607241] system 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
[   31.607244] system 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[   31.607247] system 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
[   31.607250] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   31.607254] system 00:02: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   31.607257] system 00:02: iomem range 0xfed40000-0xfed44fff could not be reserved
[   31.607260] system 00:02: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   31.607267] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   31.607274] system 00:06: ioport range 0x380-0x383 has been reserved
[   31.607277] system 00:06: ioport range 0x680-0x69f has been reserved
[   31.607280] system 00:06: ioport range 0x800-0x80f has been reserved
[   31.607283] system 00:06: ioport range 0x1000-0x107f has been reserved
[   31.607286] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   31.607288] system 00:06: ioport range 0x1640-0x164f has been reserved
[   31.607296] system 00:07: ioport range 0x6a0-0x6af has been reserved
[   31.607298] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[   31.637741] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0
[   31.637743] PCI: Bridge: 0000:00:01.0
[   31.637745]   IO window: disabled.
[   31.637749]   MEM window: dc000000-ddffffff
[   31.637752]   PREFETCH window: c0000000-cfffffff
[   31.637756] PCI: Bridge: 0000:00:1c.0
[   31.637759]   IO window: 2000-2fff
[   31.637765]   MEM window: d8000000-d9ffffff
[   31.637770]   PREFETCH window: d2000000-d3ffffff
[   31.637776] PCI: Bridge: 0000:00:1c.1
[   31.637779]   IO window: 3000-3fff
[   31.637785]   MEM window: d6000000-d7ffffff
[   31.637790]   PREFETCH window: d0000000-d1ffffff
[   31.637796] PCI: Bridge: 0000:00:1c.2
[   31.637799]   IO window: 4000-4fff
[   31.637805]   MEM window: da000000-dbffffff
[   31.637810]   PREFETCH window: d4000000-d5ffffff
[   31.637816] PCI: Bridge: 0000:00:1e.0
[   31.637818]   IO window: disabled.
[   31.637824]   MEM window: de000000-de0fffff
[   31.637828]   PREFETCH window: disabled.
[   31.637846] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.637851] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   31.637875] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   31.637881] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   31.637905] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[   31.637911] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   31.637935] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   31.637941] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   31.637953] PCI: Enabling device 0000:00:1e.0 (0004 -> 0006)
[   31.637960] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   31.637971] NET: Registered protocol family 2
[   31.675248] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.675470] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   31.676176] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   31.676529] TCP: Hash tables configured (established 131072 bind 65536)
[   31.676532] TCP reno registered
[   31.687334] checking if image is initramfs... it is
[   32.416024] Freeing initrd memory: 7665k freed
[   32.416195] Simple Boot Flag at 0x35 set to 0x1
[   32.416896] audit: initializing netlink socket (disabled)
[   32.416911] audit(1212923933.500:1): initialized
[   32.417149] highmem bounce pool size: 64 pages
[   32.419217] VFS: Disk quotas dquot_6.5.1
[   32.419296] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   32.419437] io scheduler noop registered
[   32.419439] io scheduler anticipatory registered
[   32.419442] io scheduler deadline registered
[   32.419453] io scheduler cfq registered (default)
[   32.419555] Boot video device is 0000:01:00.0
[   32.419674] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   32.419711] assign_interrupt_mode Found MSI capability
[   32.419743] Allocate Port Service[0000:00:01.0:pcie00]
[   32.419827] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   32.419886] assign_interrupt_mode Found MSI capability
[   32.419933] Allocate Port Service[0000:00:1c.0:pcie00]
[   32.419967] Allocate Port Service[0000:00:1c.0:pcie02]
[   32.420071] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   32.420129] assign_interrupt_mode Found MSI capability
[   32.420176] Allocate Port Service[0000:00:1c.1:pcie00]
[   32.420210] Allocate Port Service[0000:00:1c.1:pcie02]
[   32.420315] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   32.420373] assign_interrupt_mode Found MSI capability
[   32.420420] Allocate Port Service[0000:00:1c.2:pcie00]
[   32.420454] Allocate Port Service[0000:00:1c.2:pcie02]
[   32.420726] isapnp: Scanning for PnP cards...
[   32.775157] isapnp: No Plug & Play device found
[   32.803219] Real Time Clock Driver v1.12ac
[   32.803471] hpet_resources: 0xfed00000 is busy
[   32.803501] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   32.804747] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   32.804820] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   32.804920] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   32.821412] serio: i8042 KBD port at 0x60,0x64 irq 1
[   32.821418] serio: i8042 AUX port at 0x60,0x64 irq 12
[   32.842126] mice: PS/2 mouse device common for all mice
[   32.842244] EISA: Probing bus 0 at eisa.0
[   32.842252] Cannot allocate resource for EISA slot 1
[   32.842254] Cannot allocate resource for EISA slot 2
[   32.842257] Cannot allocate resource for EISA slot 3
[   32.842259] Cannot allocate resource for EISA slot 4
[   32.842278] EISA: Detected 0 cards.
[   32.842281] cpuidle: using governor ladder
[   32.842283] cpuidle: using governor menu
[   32.842373] NET: Registered protocol family 1
[   32.842401] Using IPI No-Shortcut mode
[   32.842432] registered taskstats version 1
[   32.842547]   Magic number: 12:37:327
[   32.842636] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   32.842639] EDD information not available.
[   32.842841] Freeing unused kernel memory: 364k freed
[   32.853713] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   34.066049] fuse init (API version 7.9)
[   34.090555] ACPI: SSDT 7FE7C189, 0238 (r1 HP     30BC         3000 INTL 20050624)
[   34.090776] ACPI: SSDT 7FE7BC42, 04C2 (r1 HP     30BC         3001 INTL 20050624)
[   34.092937] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   34.092942] ACPI: Processor [CPU0] (supports 8 throttling states)
[   34.093184] ACPI: SSDT 7FE7C3C1, 00C8 (r1 HP     30BC         3000 INTL 20050624)
[   34.093384] ACPI: SSDT 7FE7C104, 0085 (r1 HP     30BC         3000 INTL 20050624)
[   34.094342] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   34.094348] ACPI: Processor [CPU1] (supports 8 throttling states)
[   34.098610] ACPI: Thermal Zone [THR1] (46 C)
[   34.517390] usbcore: registered new interface driver usbfs
[   34.517417] usbcore: registered new interface driver hub
[   34.517953] usbcore: registered new device driver usb
[   34.529866] USB Universal Host Controller Interface driver v3.0
[   34.529932] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   34.529944] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   34.529948] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   34.530230] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   34.530267] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001800
[   34.530421] usb usb1: configuration #1 chosen from 1 choice
[   34.530455] hub 1-0:1.0: USB hub found
[   34.530460] hub 1-0:1.0: 2 ports detected
[   34.588283] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   34.588288] Copyright (c) 1999-2006 Intel Corporation.
[   34.640851] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   34.640865] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   34.640870] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   34.640896] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   34.640932] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001820
[   34.641057] usb usb2: configuration #1 chosen from 1 choice
[   34.641084] hub 2-0:1.0: USB hub found
[   34.641090] hub 2-0:1.0: 2 ports detected
[   34.727571] SCSI subsystem initialized
[   34.738011] libata version 3.00 loaded.
[   34.742173] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   34.742185] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   34.742190] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   34.742215] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   34.742251] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[   34.742368] usb usb3: configuration #1 chosen from 1 choice
[   34.742395] hub 3-0:1.0: USB hub found
[   34.742402] hub 3-0:1.0: 2 ports detected
[   34.845900] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   34.845912] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   34.845916] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   34.845940] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   34.845974] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[   34.846093] usb usb4: configuration #1 chosen from 1 choice
[   34.846117] hub 4-0:1.0: USB hub found
[   34.846123] hub 4-0:1.0: 2 ports detected
[   34.949940] ACPI: PCI Interrupt 0000:07:05.0[A] -> <6>ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   34.949948] GSI 16 (level, low) -> IRQ 16
[   34.949954] PCI: Setting latency timer of device 0000:07:05.0 to 64
[   34.949959] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   34.949965] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   34.949991] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   34.953916] ehci_hcd 0000:00:1d.7: debug port 1
[   34.953923] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   34.953930] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xde304000
[   35.010524] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[de000000-de0007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   35.015213] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   35.025778] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   35.025899] usb usb5: configuration #1 chosen from 1 choice
[   35.025926] hub 5-0:1.0: USB hub found
[   35.025932] hub 5-0:1.0: 8 ports detected
[   35.130913] ahci 0000:00:1f.2: version 3.0
[   35.130943] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   35.130995] ahci 0000:00:1f.2: nr_ports (4) and implemented port map (0x5) don't match, using nr_ports
[   35.130998] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0xf
[   35.413732] Clocksource tsc unstable (delta = -907745394 ns)
[   35.419750] Time: hpet clocksource has been installed.
[   35.449666] usb 2-1: new low speed USB device using uhci_hcd and address 3
[   35.504294] usb 2-1: configuration #1 chosen from 1 choice
[   35.521405] usbcore: registered new interface driver hiddev
[   35.540105] input: Microsoft Microsoft Wireless Optical Mouse® 1.00 as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input2
[   35.544055] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.00] on usb-0000:00:1d.1-1
[   35.544081] usbcore: registered new interface driver usbhid
[   35.544088] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   35.619830] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[   35.619840] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[   35.619850] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   35.620240] scsi0 : ahci
[   35.620450] scsi1 : ahci
[   35.620598] scsi2 : ahci
[   35.620755] scsi3 : ahci
[   35.620836] ata1: SATA max UDMA/133 abar m1024@0xde304400 port 0xde304500 irq 219
[   35.620840] ata2: SATA max UDMA/133 abar m1024@0xde304400 port 0xde304580 irq 219
[   35.620843] ata3: SATA max UDMA/133 abar m1024@0xde304400 port 0xde304600 irq 219
[   35.620847] ata4: SATA max UDMA/133 abar m1024@0xde304400 port 0xde304680 irq 219
[   35.639228] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00f6bb1100]
[   35.695771] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   35.696239] ata1.00: ATA-7: WDC WD800BEVS-60RST0, 04.01G04, max UDMA/100
[   35.696246] ata1.00: 156301488 sectors, multi 16: LBA48 
[   35.696847] ata1.00: configured for UDMA/100
[   35.730284] ata2: SATA link down (SStatus 0 SControl 0)
[   35.764654] ata3: SATA link down (SStatus 0 SControl 300)
[   35.799713] ata4: SATA link down (SStatus 0 SControl 0)
[   35.800012] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BEVS-60 04.0 PQ: 0 ANSI: 5
[   35.801558] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   35.801574] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   35.809556] Driver 'sd' needs updating - please use bus_type methods
[   35.814886] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   35.814901] sd 0:0:0:0: [sda] Write Protect is off
[   35.814903] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.814922] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.814974] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   35.814985] sd 0:0:0:0: [sda] Write Protect is off
[   35.814988] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.815005] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.815008]  sda:<6>e1000: 0000:05:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1b:24:1f:8d:85
[   35.918917] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   35.919192] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   35.919228] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   35.919241] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   35.922822] ata_piix 0000:00:1f.1: version 2.12
[   35.922837] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   35.922864] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   35.923655] scsi4 : ata_piix
[   35.924131] scsi5 : ata_piix
[   35.924615] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[   35.924618] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[   36.149482]  sda1 sda2 sda3 < sda5 >
[   36.182343] sd 0:0:0:0: [sda] Attached SCSI disk
[   36.186830] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   36.258287] ata5.00: ATAPI: TSSTcorpCD/DVDW TS-L632M, 0817, max MWDMA2
[   36.444147] ata5.00: configured for MWDMA2
[   36.444232] ata6: port disabled. ignoring.
[   36.444928] scsi 4:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632M 0817 PQ: 0 ANSI: 5
[   36.445077] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   36.452004] Driver 'sr' needs updating - please use bus_type methods
[   36.456114] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   36.456121] Uniform CD-ROM driver Revision: 3.20
[   36.456206] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   36.877994] kjournald starting.  Commit interval 5 seconds
[   36.878026] EXT3-fs: mounted filesystem with ordered data mode.
[   37.401992] ISO 9660 Extensions: Microsoft Joliet Level 3
[   37.438815] ISO 9660 Extensions: RRIP_1991A
[   37.759736] Registering unionfs 1.4
[   37.759739] unionfs: debugging is not enabled
[   37.768034] loop: module loaded
[   38.066216] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[  112.444593] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  112.528215] iTCO_vendor_support: vendor-support=0
[  113.001470] Linux agpgart interface v0.102
[  113.132158] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  114.714331] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[  114.714431] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[  114.714468] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  114.980136] input: Power Button (FF) as /devices/virtual/input/input3
[  115.027918] ACPI: Power Button (FF) [PWRF]
[  115.027991] input: Power Button (CM) as /devices/virtual/input/input4
[  115.083911] ACPI: Power Button (CM) [PWRB]
[  115.083975] input: Sleep Button (CM) as /devices/virtual/input/input5
[  115.143898] ACPI: Sleep Button (CM) [SLPB]
[  115.143963] input: Lid Switch as /devices/virtual/input/input6
[  115.176200] ACPI: Lid Switch [LID]
[  115.176288] ACPI: WMI-Acer: Mapper loaded
[  115.401212] input: PC Speaker as /devices/platform/pcspkr/input/input7
[  115.733581] ACPI: Battery Slot [BAT0] (battery present)
[  115.734101] ACPI: AC Adapter [ACAD] (on-line)
[  115.875747] intel_rng: FWH not detected
[  116.137053] sdhci: Secure Digital Host Controller Interface driver
[  116.137058] sdhci: Copyright(c) Pierre Ossman
[  116.137098] sdhci: SDHCI controller found at 0000:07:05.1 [1180:0822] (rev 19)
[  116.137121] PCI: Enabling device 0000:07:05.1 (0000 -> 0002)
[  116.137128] ACPI: PCI Interrupt 0000:07:05.1[B] -> GSI 17 (level, low) -> IRQ 17
[  116.137146] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[  116.137154] PCI: Setting latency timer of device 0000:07:05.1 to 64
[  116.137205] mmc0: SDHCI at 0xde000800 irq 17 DMA
[  116.176243] ricoh-mmc: Ricoh MMC Controller disabling driver
[  116.176247] ricoh-mmc: Copyright(c) Philip Langdale
[  116.176288] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 1)
[  116.176302] ricoh-mmc: Controller is now disabled.
[  116.177068] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input8
[  116.215759] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  116.217583] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9
[  116.251749] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[  116.509380] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[  116.509385] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[  116.509492] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  116.509507] PCI: Setting latency timer of device 0000:02:00.0 to 64
[  116.509528] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[  116.922452] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[  116.922850] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[  117.261058] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[  117.321653] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[  117.446210] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[  117.446244] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[  118.495254] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x011f000c
[  119.648964] Adding 353388k swap on /dev/sda5.  Priority:-1 extents:1 across:353388k
[  120.439331] ip_tables: (C) 2000-2006 Netfilter Core Team
```

---

### Post by ludicrous on 2008-06-09
(Bump)

---

### Post by VMC on 2008-06-09
Go here [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
and read up on the xorg config. It tells what to look for regarding monitor, resulotion.

---

### Post by ludicrous on 2008-06-10
Thanks, but I couldn't find anything there that helped.  I haven't changed anything recently with the resolution or xorg, and using the fresh default xorg.conf didn't change anything, even though I used that for a while with no problems.

When I run startx, one thing it prints to the screen is
```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```
Seems like it should be able to find a driver, I was using a restricted Nvidia driver before.

---

