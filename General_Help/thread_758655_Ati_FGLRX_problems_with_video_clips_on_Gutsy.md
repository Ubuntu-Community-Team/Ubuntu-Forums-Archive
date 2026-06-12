---
title: "Ati FGLRX problems with video clips on Gutsy"
date: 2008-04-18
forum: General Help
---

### Post by kisalli on 2008-04-18
Before I got my new Radeon X1600 card, I had Radeon 8500 and installed all the necessary packages to watch .wmv and .mpg video clips and they worked just fine. Then I got the new X1600 and installed the newest fglrx driver on Finnish repositories (8.37.6) with synaptic and problems appeared:

When trying to watch video clip files (.wmv and .mpg), the picture appears blueish *outside* the player, at the bottom of the screen, and cannot be moved or resized. Audio works fine. This happens with Totem, MPlayer and VLC.
3D games do not work at all. The screen turns dark and monitor gives some sync error messages, after which the system must be rebooted.

I'm aware that there are newer fglrx driver packages on ATI website, but I'm too newbie to install them myself. Last time I tried with googled step-by-step instructions, the system wouldn't boot at all, even from the CD. DIsplay server just crashed immediately. My Kernel version is 2.6.22-14-generic.

Xorg.0.log:
> 
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux kisalli-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 18 14:03:07 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "NOKIA 920C"
(**) |   |-->Device "ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 1043,80ac rev c1 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 1043,80ad rev a4 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 1043,0c11 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 1043,0c11 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 1043,0c11 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 1043,0c11 rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 1043,80a7 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 10de,006b card 1043,0c11 rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,006a card 1043,8095 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 1043,0c11 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0d:0: chip 10de,006e card 1043,809a rev a3 class 0c,00,10 hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev c1 class 06,04,00 hdr 01
(II) PCI: 01:04:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: 01:09:0: chip 1106,3038 card 0925,1234 rev 50 class 0c,03,00 hdr 80
(II) PCI: 01:09:1: chip 1106,3038 card 0925,1234 rev 50 class 0c,03,00 hdr 80
(II) PCI: 01:09:2: chip 1106,3104 card 0925,1234 rev 51 class 0c,03,20 hdr 80
(II) PCI: 03:00:0: chip 1002,71c2 card 174b,e100 rev 00 class 03,00,00 hdr 80
(II) PCI: 03:00:1: chip 1002,71e2 card 174b,e101 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe7000000 - 0xe8ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x300fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xe5000000 - 0xe6ffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(--) PCI:*(3:0:0) ATI Technologies Inc RV530 [Radeon X1600] rev 0, Mem @ 0xd0000000/28, 0xe6000000/16, I/O @ 0xc000/8
(--) PCI: (3:0:1) ATI Technologies Inc RV530 [Radeon X1600] (Secondary) rev 0, Mem @ 0xe6010000/16
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[1] -1	0	0xe8000000 - 0xe8003fff (0x4000) MX[B]
	[2] -1	0	0xe9085000 - 0xe908503f (0x40) MX[B]
	[3] -1	0	0xe9084000 - 0xe90847ff (0x800) MX[B]
	[4] -1	0	0xe9080000 - 0xe9080fff (0x1000) MX[B]
	[5] -1	0	0xe9000000 - 0xe907ffff (0x80000) MX[B]
	[6] -1	0	0xe9086000 - 0xe9086fff (0x1000) MX[B]
	[7] -1	0	0xe9083000 - 0xe90830ff (0x100) MX[B]
	[8] -1	0	0xe9082000 - 0xe9082fff (0x1000) MX[B]
	[9] -1	0	0xe9087000 - 0xe9087fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xe6000000 - 0xe600ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[14] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[15] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[16] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xe6010000 - 0xe601ffff (0x10000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[1] -1	0	0xe8000000 - 0xe8003fff (0x4000) MX[B]
	[2] -1	0	0xe9085000 - 0xe908503f (0x40) MX[B]
	[3] -1	0	0xe9084000 - 0xe90847ff (0x800) MX[B]
	[4] -1	0	0xe9080000 - 0xe9080fff (0x1000) MX[B]
	[5] -1	0	0xe9000000 - 0xe907ffff (0x80000) MX[B]
	[6] -1	0	0xe9086000 - 0xe9086fff (0x1000) MX[B]
	[7] -1	0	0xe9083000 - 0xe90830ff (0x100) MX[B]
	[8] -1	0	0xe9082000 - 0xe9082fff (0x1000) MX[B]
	[9] -1	0	0xe9087000 - 0xe9087fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xe6000000 - 0xe600ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[14] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[15] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[16] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xe6010000 - 0xe601ffff (0x10000) MX[B](B)
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
	[4] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[5] -1	0	0xe8000000 - 0xe8003fff (0x4000) MX[B]
	[6] -1	0	0xe9085000 - 0xe908503f (0x40) MX[B]
	[7] -1	0	0xe9084000 - 0xe90847ff (0x800) MX[B]
	[8] -1	0	0xe9080000 - 0xe9080fff (0x1000) MX[B]
	[9] -1	0	0xe9000000 - 0xe907ffff (0x80000) MX[B]
	[10] -1	0	0xe9086000 - 0xe9086fff (0x1000) MX[B]
	[11] -1	0	0xe9083000 - 0xe90830ff (0x100) MX[B]
	[12] -1	0	0xe9082000 - 0xe9082fff (0x1000) MX[B]
	[13] -1	0	0xe9087000 - 0xe9087fff (0x1000) MX[B]
	[14] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[15] -1	0	0xe6000000 - 0xe600ffff (0x10000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xe6010000 - 0xe601ffff (0x10000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[21] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[28] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.37.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) v4l driver for Video4Linux
(II) Primary Device is: PCI 03:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.37.6
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.37g1                           
(II) ATI Proprietary Linux Driver Build Date: May 25 2007 14:25:03
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.37.1.1.2.3-driver-lnx-x86-x86_64-346145
(WW) fglrx: No matching Device section for instance (BusID PCI:3:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x71C2) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[5] -1	0	0xe8000000 - 0xe8003fff (0x4000) MX[B]
	[6] -1	0	0xe9085000 - 0xe908503f (0x40) MX[B]
	[7] -1	0	0xe9084000 - 0xe90847ff (0x800) MX[B]
	[8] -1	0	0xe9080000 - 0xe9080fff (0x1000) MX[B]
	[9] -1	0	0xe9000000 - 0xe907ffff (0x80000) MX[B]
	[10] -1	0	0xe9086000 - 0xe9086fff (0x1000) MX[B]
	[11] -1	0	0xe9083000 - 0xe90830ff (0x100) MX[B]
	[12] -1	0	0xe9082000 - 0xe9082fff (0x1000) MX[B]
	[13] -1	0	0xe9087000 - 0xe9087fff (0x1000) MX[B]
	[14] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[15] -1	0	0xe6000000 - 0xe600ffff (0x10000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xe6010000 - 0xe601ffff (0x10000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[21] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[28] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8208d58
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[5] -1	0	0xe8000000 - 0xe8003fff (0x4000) MX[B]
	[6] -1	0	0xe9085000 - 0xe908503f (0x40) MX[B]
	[7] -1	0	0xe9084000 - 0xe90847ff (0x800) MX[B]
	[8] -1	0	0xe9080000 - 0xe9080fff (0x1000) MX[B]
	[9] -1	0	0xe9000000 - 0xe907ffff (0x80000) MX[B]
	[10] -1	0	0xe9086000 - 0xe9086fff (0x1000) MX[B]
	[11] -1	0	0xe9083000 - 0xe90830ff (0x100) MX[B]
	[12] -1	0	0xe9082000 - 0xe9082fff (0x1000) MX[B]
	[13] -1	0	0xe9087000 - 0xe9087fff (0x1000) MX[B]
	[14] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[15] -1	0	0xe6000000 - 0xe600ffff (0x10000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xe6010000 - 0xe601ffff (0x10000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[26] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[30] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 3 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "Radeon X1600 Series" (Chipset = 0x71c2)
(--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0xe100)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xe6000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV530
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.37.6
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: NOK  Model: 142  Serial#: 4449
(II) fglrx(0): Year: 2000  Week: 6
(II) fglrx(0): EDID Version: 1.2
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 36  vert.: 27
(II) fglrx(0): Gamma: 2.28
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): GTF timings supported
(II) fglrx(0): redX: 0.638 redY: 0.325   greenX: 0.276 greenY: 0.596
(II) fglrx(0): blueX: 0.143 blueY: 0.066   whiteX: 0.283 whiteY: 0.297
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) fglrx(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 157.5 MHz   Image Size:  355 x 266 mm
(II) fglrx(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) fglrx(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 96 kHz, PixClock max 210 MHz
(II) fglrx(0): Serial No: K006004449
(II) fglrx(0): Monitor name: NOKIA 920C
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0039eb420161110000
(II) fglrx(0): 	060a01026e241b80eb5e88a353469824
(II) fglrx(0): 	11484ca10980a94f6159455901010101
(II) fglrx(0): 	010101010101863d00c05100304040a0
(II) fglrx(0): 	1300630a1100001e000000fd0032a01e
(II) fglrx(0): 	6015000a202020202020000000ff004b
(II) fglrx(0): 	3030363030343434390a2020000000fc
(II) fglrx(0): 	004e4f4b494120393230430a202000e7
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(**) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 92 modes found for primary display.
(--) fglrx(0): Virtual size is 2048x1536 (pitch 0)
(**) fglrx(0): *Mode "1280x1024@85": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024@85"  157.50  1280 1344 1504 1728  1024 1025 1028 1072
(**) fglrx(0): *Mode "1280x1024@85": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024@85"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024@85": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024@85"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x1024@60": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024@60"  157.50  1280 1344 1504 1728  1024 1025 1028 1072
(**) fglrx(0): *Mode "1280x1024@60": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024@60"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024@60": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024@60"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x1024@75": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024@75"  157.50  1280 1344 1504 1728  1024 1025 1028 1072
(**) fglrx(0): *Mode "1280x1024@75": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024@75"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x1024@75": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024@75"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864@75": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864@75"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0): *Mode "1600x1200@65": 202.5 MHz (scaled from 0.0 MHz), 93.8 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1600x1200@65"  202.50  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1600x1200@65": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200@65"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1024x768@43": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768@43"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0): *Mode "1024x768@43": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768@43"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@43": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768@43"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@43": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768@43"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "1600x1200@60": 202.5 MHz (scaled from 0.0 MHz), 93.8 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1600x1200@60"  202.50  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1600x1200@60": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200@60"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1024x768@60": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768@60"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0): *Mode "1024x768@60": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768@60"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@60": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768@60"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@60": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768@60"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "1600x1200@75": 202.5 MHz (scaled from 0.0 MHz), 93.8 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1600x1200@75"  202.50  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1600x1200@75": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200@75"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1024x768@70": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768@70"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0): *Mode "1024x768@70": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768@70"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@70": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768@70"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@70": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768@70"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "1600x1200@70": 202.5 MHz (scaled from 0.0 MHz), 93.8 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1600x1200@70"  202.50  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1600x1200@70": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200@70"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1024x768@75": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768@75"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0): *Mode "1024x768@75": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768@75"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@75": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768@75"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768@75": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768@75"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "1024x768@85": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768@85"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0): *Mode "1024x768@85": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768@85"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@85": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768@85"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@85": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768@85"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "832x624@75": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.0 Hz (I)
(II) fglrx(0): Modeline "832x624@75"   57.28  832 864 928 1152  624 625 628 667 interlace +vsync
(**) fglrx(0): *Mode "800x600@60": 56.3 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   56.30  800 832 896 1048  600 601 604 631 doublescan +hsync
(**) fglrx(0): *Mode "800x600@60": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@60": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@60": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0):  Default mode "800x600@60": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@85": 56.3 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz (D)
(II) fglrx(0): Modeline "800x600@85"   56.30  800 832 896 1048  600 601 604 631 doublescan +hsync
(**) fglrx(0): *Mode "800x600@85": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@85"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@85": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@85"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@85": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@85"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0):  Default mode "800x600@85": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@85"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@75": 56.3 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   56.30  800 832 896 1048  600 601 604 631 doublescan +hsync
(**) fglrx(0): *Mode "800x600@75": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@75": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@75": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0):  Default mode "800x600@75": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@72": 56.3 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   56.30  800 832 896 1048  600 601 604 631 doublescan +hsync
(**) fglrx(0): *Mode "800x600@72": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@72": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@72": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0):  Default mode "800x600@72": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 56.3 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   56.30  800 832 896 1048  600 601 604 631 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "640x480@85": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz (I)
(II) fglrx(0): Modeline "640x480@85"   36.00  640 696 752 832  480 481 484 509 interlace +vsync
(**) fglrx(0): *Mode "640x480@85": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "640x480@85"   31.50  640 656 720 840  480 481 484 500 interlace +vsync
(**) fglrx(0): *Mode "640x480@85": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz (I)
(II) fglrx(0): Modeline "640x480@85"   31.50  640 664 704 832  480 489 491 520 interlace +vsync
(**) fglrx(0):  Default mode "640x480@85": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (I)
(II) fglrx(0): Modeline "640x480@85"   25.20  640 656 752 800  480 490 492 525 interlace +vsync
(**) fglrx(0): *Mode "640x480@75": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz (I)
(II) fglrx(0): Modeline "640x480@75"   36.00  640 696 752 832  480 481 484 509 interlace +vsync
(**) fglrx(0): *Mode "640x480@75": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "640x480@75"   31.50  640 656 720 840  480 481 484 500 interlace +vsync
(**) fglrx(0): *Mode "640x480@75": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz (I)
(II) fglrx(0): Modeline "640x480@75"   31.50  640 664 704 832  480 489 491 520 interlace +vsync
(**) fglrx(0):  Default mode "640x480@75": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (I)
(II) fglrx(0): Modeline "640x480@75"   25.20  640 656 752 800  480 490 492 525 interlace +vsync
(**) fglrx(0): *Mode "640x480@72": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz (I)
(II) fglrx(0): Modeline "640x480@72"   36.00  640 696 752 832  480 481 484 509 interlace +vsync
(**) fglrx(0): *Mode "640x480@72": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "640x480@72"   31.50  640 656 720 840  480 481 484 500 interlace +vsync
(**) fglrx(0): *Mode "640x480@72": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz (I)
(II) fglrx(0): Modeline "640x480@72"   31.50  640 664 704 832  480 489 491 520 interlace +vsync
(**) fglrx(0):  Default mode "640x480@72": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (I)
(II) fglrx(0): Modeline "640x480@72"   25.20  640 656 752 800  480 490 492 525 interlace +vsync
(**) fglrx(0): *Mode "640x480@60": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz (I)
(II) fglrx(0): Modeline "640x480@60"   36.00  640 696 752 832  480 481 484 509 interlace +vsync
(**) fglrx(0): *Mode "640x480@60": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "640x480@60"   31.50  640 656 720 840  480 481 484 500 interlace +vsync
(**) fglrx(0): *Mode "640x480@60": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz (I)
(II) fglrx(0): Modeline "640x480@60"   31.50  640 664 704 832  480 489 491 520 interlace +vsync
(**) fglrx(0): *Mode "640x480@60": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (I)
(II) fglrx(0): Modeline "640x480@60"   25.20  640 656 752 800  480 490 492 525 interlace +vsync
(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (360, 270) mm
(--) fglrx(0): DPI set to (144, 144)
(--) fglrx(0): Virtual size is 2048x1536 (pitch 2048)
(**) fglrx(0): *Mode "1280x1024@85": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024@85"  157.50  1280 1344 1504 1728  1024 1025 1028 1072
(**) fglrx(0): *Mode "1280x1024@85": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024@85"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024@85": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024@85"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x1024@60": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024@60"  157.50  1280 1344 1504 1728  1024 1025 1028 1072
(**) fglrx(0): *Mode "1280x1024@60": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024@60"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024@60": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024@60"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x1024@75": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024@75"  157.50  1280 1344 1504 1728  1024 1025 1028 1072
(**) fglrx(0): *Mode "1280x1024@75": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024@75"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x1024@75": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024@75"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864@75": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864@75"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0): *Mode "1600x1200@65": 202.5 MHz (scaled from 0.0 MHz), 93.8 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1600x1200@65"  202.50  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1600x1200@65": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200@65"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1024x768@43": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768@43"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0): *Mode "1024x768@43": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768@43"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@43": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768@43"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@43": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768@43"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "1600x1200@60": 202.5 MHz (scaled from 0.0 MHz), 93.8 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1600x1200@60"  202.50  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1600x1200@60": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200@60"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1024x768@60": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768@60"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0): *Mode "1024x768@60": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768@60"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@60": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768@60"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@60": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768@60"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "1600x1200@75": 202.5 MHz (scaled from 0.0 MHz), 93.8 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1600x1200@75"  202.50  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1600x1200@75": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200@75"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1024x768@70": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768@70"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0): *Mode "1024x768@70": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768@70"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@70": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768@70"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@70": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768@70"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "1600x1200@70": 202.5 MHz (scaled from 0.0 MHz), 93.8 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1600x1200@70"  202.50  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1600x1200@70": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200@70"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1024x768@75": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768@75"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0): *Mode "1024x768@75": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768@75"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@75": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768@75"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768@75": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768@75"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "1024x768@85": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768@85"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0): *Mode "1024x768@85": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768@85"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@85": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768@85"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@85": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768@85"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "832x624@75": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.0 Hz (I)
(II) fglrx(0): Modeline "832x624@75"   57.28  832 864 928 1152  624 625 628 667 interlace +vsync
(**) fglrx(0): *Mode "800x600@60": 56.3 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   56.30  800 832 896 1048  600 601 604 631 doublescan +hsync
(**) fglrx(0): *Mode "800x600@60": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@60": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@60": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0):  Default mode "800x600@60": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@85": 56.3 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz (D)
(II) fglrx(0): Modeline "800x600@85"   56.30  800 832 896 1048  600 601 604 631 doublescan +hsync
(**) fglrx(0): *Mode "800x600@85": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@85"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@85": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@85"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@85": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@85"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0):  Default mode "800x600@85": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@85"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@75": 56.3 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   56.30  800 832 896 1048  600 601 604 631 doublescan +hsync
(**) fglrx(0): *Mode "800x600@75": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@75": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@75": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0):  Default mode "800x600@75": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@72": 56.3 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   56.30  800 832 896 1048  600 601 604 631 doublescan +hsync
(**) fglrx(0): *Mode "800x600@72": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@72": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@72": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0):  Default mode "800x600@72": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 56.3 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   56.30  800 832 896 1048  600 601 604 631 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "640x480@85": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz (I)
(II) fglrx(0): Modeline "640x480@85"   36.00  640 696 752 832  480 481 484 509 interlace +vsync
(**) fglrx(0): *Mode "640x480@85": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "640x480@85"   31.50  640 656 720 840  480 481 484 500 interlace +vsync
(**) fglrx(0): *Mode "640x480@85": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz (I)
(II) fglrx(0): Modeline "640x480@85"   31.50  640 664 704 832  480 489 491 520 interlace +vsync
(**) fglrx(0):  Default mode "640x480@85": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (I)
(II) fglrx(0): Modeline "640x480@85"   25.20  640 656 752 800  480 490 492 525 interlace +vsync
(**) fglrx(0): *Mode "640x480@75": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz (I)
(II) fglrx(0): Modeline "640x480@75"   36.00  640 696 752 832  480 481 484 509 interlace +vsync
(**) fglrx(0): *Mode "640x480@75": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "640x480@75"   31.50  640 656 720 840  480 481 484 500 interlace +vsync
(**) fglrx(0): *Mode "640x480@75": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz (I)
(II) fglrx(0): Modeline "640x480@75"   31.50  640 664 704 832  480 489 491 520 interlace +vsync
(**) fglrx(0):  Default mode "640x480@75": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (I)
(II) fglrx(0): Modeline "640x480@75"   25.20  640 656 752 800  480 490 492 525 interlace +vsync
(**) fglrx(0): *Mode "640x480@72": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz (I)
(II) fglrx(0): Modeline "640x480@72"   36.00  640 696 752 832  480 481 484 509 interlace +vsync
(**) fglrx(0): *Mode "640x480@72": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "640x480@72"   31.50  640 656 720 840  480 481 484 500 interlace +vsync
(**) fglrx(0): *Mode "640x480@72": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz (I)
(II) fglrx(0): Modeline "640x480@72"   31.50  640 664 704 832  480 489 491 520 interlace +vsync
(**) fglrx(0):  Default mode "640x480@72": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (I)
(II) fglrx(0): Modeline "640x480@72"   25.20  640 656 752 800  480 490 492 525 interlace +vsync
(**) fglrx(0): *Mode "640x480@60": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz (I)
(II) fglrx(0): Modeline "640x480@60"   36.00  640 696 752 832  480 481 484 509 interlace +vsync
(**) fglrx(0): *Mode "640x480@60": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "640x480@60"   31.50  640 656 720 840  480 481 484 500 interlace +vsync
(**) fglrx(0): *Mode "640x480@60": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz (I)
(II) fglrx(0): Modeline "640x480@60"   31.50  640 664 704 832  480 489 491 520 interlace +vsync
(**) fglrx(0): *Mode "640x480@60": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (I)
(II) fglrx(0): Modeline "640x480@60"   25.20  640 656 752 800  480 490 492 525 interlace +vsync
(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000000f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(II) fglrx(0): [pcie] 131072 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) LoadModule: "glesx.so" (glesx)
(WW) LoadModule: given non-canonical module name "glesx.so"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe6000000 - 0xe600ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[7] -1	0	0xe8000000 - 0xe8003fff (0x4000) MX[B]
	[8] -1	0	0xe9085000 - 0xe908503f (0x40) MX[B]
	[9] -1	0	0xe9084000 - 0xe90847ff (0x800) MX[B]
	[10] -1	0	0xe9080000 - 0xe9080fff (0x1000) MX[B]
	[11] -1	0	0xe9000000 - 0xe907ffff (0x80000) MX[B]
	[12] -1	0	0xe9086000 - 0xe9086fff (0x1000) MX[B]
	[13] -1	0	0xe9083000 - 0xe90830ff (0x100) MX[B]
	[14] -1	0	0xe9082000 - 0xe9082fff (0x1000) MX[B]
	[15] -1	0	0xe9087000 - 0xe9087fff (0x1000) MX[B]
	[16] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[17] -1	0	0xe6000000 - 0xe600ffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xe6010000 - 0xe601ffff (0x10000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[23] 0	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[27] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[28] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[33] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[34] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:3:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:3:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb795b000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.37.6
(II) fglrx(0):     Date: May 25 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.22-14-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): Interrupt handler installed at IRQ 19.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x00e01000
(II) fglrx(0): FBMM initialized for area (0,0)-(2048,1792)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(2048,1536) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 2048 x 256
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(II) fglrx(0): GLESX enableFlags = 16
(II) fglrx(0): GLESX is enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		16 128x128 slots
		4 256x256 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "MergedFB" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:3:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:3:0:0
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "fi"
(**) Generic Keyboard: XkbLayout: "fi"
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
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
BOGUS LENGTH in write keyboard desc, expected 5628, got 5632

---

