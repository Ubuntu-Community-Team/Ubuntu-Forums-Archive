---
title: "help, my video drivers broke"
date: 2007-05-23
forum: General Help
---

### Post by The Squig on 2007-05-23
im using the nv 9755 drivers for my 6800le agp card. worked fine for a couple of days. An hour ago i decided to restart gdm and all hell broke lose. im stuck at 640*something resolution. cant change it and the drivers barly work.

I tried to replace xorg.conf with my backup (made before my nvidia drivers). it helped "somewhat". I have 800*600 resolution but nothing more. Ive tried everything I could think of. I removed the drivers and reinstalled them. same problem. I tried to install them automaticly in ubuntu which resulted in me not beiong able to load xorg. replaced the xorg.conf file again.

Dunno what the problem is ive tried rebooting etc. Installed the driver again thro the repos (nvida-glx-new). same result (boots but with only 680*x resolution). Im gonna post the log file after that boot. Helpis appreciated.
If im unable to fix this soon Ill have to reinstall :(

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux 2600 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May 24 01:58:02 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "PHILIPS 107X"
(**) |   |-->Device "nVidia Corporation NV40.2 [GeForce 6800 LE]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
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
(**) Extension "Composite" is disabled
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
(II) PCI: 00:00:0: chip 1106,3189 card 1043,807f rev 80 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 1102,0002 card 1102,8027 rev 07 class 04,01,00 hdr 80
(II) PCI: 00:0d:1: chip 1102,7002 card 1102,0020 rev 07 class 09,80,00 hdr 80
(II) PCI: 00:0f:0: chip 1106,3149 card 1043,80ed rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,80ed rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 0000,0000 rev 60 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 0000,0000 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1043,80ed rev 78 class 02,00,00 hdr 00
(II) PCI: 00:13:0: chip 10ec,8139 card 11f6,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0042 card 107d,299b rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xed000000 - 0xefefffff (0x2f00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xeff00000 - 0xf7ffffff (0x8100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV40.2 [GeForce 6800 LE] rev 161, Mem @ 0xee000000/24, 0xf0000000/27, 0xed000000/24, BIOS @ 0xeffe0000/17
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
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xeb800000 - 0xeb8000ff (0x100) MX[B]
	[1] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[2] -1	0	0xec800000 - 0xec8000ff (0x100) MX[B]
	[3] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[4] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[5] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[6] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[8] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[9] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[10] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[11] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[12] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[13] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[14] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[15] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[17] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xeb800000 - 0xeb8000ff (0x100) MX[B]
	[1] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[2] -1	0	0xec800000 - 0xec8000ff (0x100) MX[B]
	[3] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[4] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[5] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[6] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[8] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[9] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[10] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[11] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[12] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[13] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[14] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[15] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[17] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
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
	[4] -1	0	0xeb800000 - 0xeb8000ff (0x100) MX[B]
	[5] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[6] -1	0	0xec800000 - 0xec8000ff (0x100) MX[B]
	[7] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[8] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[9] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[10] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[15] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[16] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[19] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[20] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[21] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[23] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[24] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[29] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
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
	compiled for 4.0.2, module version = 1.0.9755
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
	compiled for 4.0.2, module version = 1.0.9755
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
(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:23:13 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
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
(WW) Warning, couldn't open module wfb
(II) UnloadModule: "wfb"
(EE) Failed to load module "wfb" (module does not exist, 0)
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
	[4] -1	0	0xeb800000 - 0xeb8000ff (0x100) MX[B]
	[5] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[6] -1	0	0xec800000 - 0xec8000ff (0x100) MX[B]
	[7] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[8] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[9] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[10] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[15] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[16] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[19] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[20] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[21] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[23] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[24] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[29] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xeb800000 - 0xeb8000ff (0x100) MX[B]
	[5] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[6] -1	0	0xec800000 - 0xec8000ff (0x100) MX[B]
	[7] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[8] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[9] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[10] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[18] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[19] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[21] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[22] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[23] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[24] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[26] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[27] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[28] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[29] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[30] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[31] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[32] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[33] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce 6800 LE at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.40.02.26.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6800 LE at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1152x864"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "832x624"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(WW) NVIDIA(0): No valid modes for "640x350"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xed000000 - 0xedffffff (0x1000000) MX[B]
	[1] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
	[2] 0	0	0xee000000 - 0xeeffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xeb800000 - 0xeb8000ff (0x100) MX[B]
	[8] -1	0	0xec000000 - 0xec0000ff (0x100) MX[B]
	[9] -1	0	0xec800000 - 0xec8000ff (0x100) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xeffe0000 - 0xefffffff (0x20000) MX[B](B)
	[12] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[21] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[22] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[24] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[25] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[26] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[27] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[28] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[29] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[30] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[31] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[32] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[33] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[34] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[35] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[36] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Built-in logo is bigger than the screen.
(II) NVIDIA(0): Setting mode "640x480"
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
(**) Option "XkbLayout" "se"
(**) Generic Keyboard: XkbLayout: "se"
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
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```

---

### Post by Sirhanz on 2007-05-23
```
sudo dpkg-reconfigure xserver-xorg

``` have you tried this already?

---

### Post by The Squig on 2007-05-23
i did. messed completly. I could only access the console after that. but im gonna try it again just to be sure

---

### Post by The Squig on 2007-05-23
Edit: DOH. found the problem. my monitor cable wasnt plugged in all the way. i feel stupid :p

---

