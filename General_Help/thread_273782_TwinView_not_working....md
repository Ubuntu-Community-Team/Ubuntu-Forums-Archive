---
title: "TwinView not working..."
date: 2006-10-08
forum: General Help
---

### Post by themoebius on 2006-10-08
I'm using the beta drivers 1.0.9625 for nVidia and I just cannot get Twinview to work. It will only use my secondary monitor. I've tried all kinds of configurations. Below are my xorg.conf and my Xorg.0.log Note I have two video cards installed but I won't be using the Geforce 6200 with the Dell attached, so just ignore it.

Xorg.0.log
```


X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux zac-desktop 2.6.17-10-generic #2 SMP Fri Oct 6 00:36:14 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct  8 18:50:32 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "Off"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3188 card 1043,80a3 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1106,3044 card 1043,808a rev 80 class 0c,00,10 hdr 00
(II) PCI: 00:08:0: chip 105a,3373 card 1043,80f5 rev 02 class 01,04,00 hdr 00
(II) PCI: 00:09:0: chip 1317,0985 card 1317,0570 rev 11 class 02,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10b7,1700 card 1043,80eb rev 12 class 02,00,00 hdr 00
(II) PCI: 00:0e:0: chip 10de,0221 card 270f,1974 rev a1 class 03,00,00 hdr 00
(II) PCI: 00:0f:0: chip 1106,3149 card 1043,80ed rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1043,80b0 rev 60 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 0000,0000 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0332 card 3842,a323 rev a1 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe8d00000 - 0xeaefffff (0x2200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc8c00000 - 0xd8bfffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:14:0) nVidia Corporation GeForce 6200 rev 161, Mem @ 0xee000000/24, 0xe0000000/27, 0xed000000/24, BIOS @ 0xefe00000/17
(--) PCI:*(1:0:0) nVidia Corporation NV35 [GeForce FX 5900XT] rev 161, Mem @ 0xe9000000/24, 0xd0000000/27, BIOS @ 0xeae00000/17
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
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xeff00000 - 0xeff000ff (0x100) MX[B]
	[1] -1	0	0xefd00000 - 0xefd03fff (0x4000) MX[B]
	[2] -1	0	0xefc00000 - 0xefc003ff (0x400) MX[B]
	[3] -1	0	0xef900000 - 0xef91ffff (0x20000) MX[B]
	[4] -1	0	0xefa00000 - 0xefa00fff (0x1000) MX[B]
	[5] -1	0	0xef800000 - 0xef8007ff (0x800) MX[B]
	[6] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[7] -1	0	0xeae00000 - 0xeae1ffff (0x20000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[11] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[14] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[27] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[28] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[29] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[31] -1	0	0x0000a400 - 0x0000a43f (0x40) IX[B]
	[32] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xeff00000 - 0xeff000ff (0x100) MX[B]
	[1] -1	0	0xefd00000 - 0xefd03fff (0x4000) MX[B]
	[2] -1	0	0xefc00000 - 0xefc003ff (0x400) MX[B]
	[3] -1	0	0xef900000 - 0xef91ffff (0x20000) MX[B]
	[4] -1	0	0xefa00000 - 0xefa00fff (0x1000) MX[B]
	[5] -1	0	0xef800000 - 0xef8007ff (0x800) MX[B]
	[6] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[7] -1	0	0xeae00000 - 0xeae1ffff (0x20000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[11] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[14] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[27] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[28] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[29] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[31] -1	0	0x0000a400 - 0x0000a43f (0x40) IX[B]
	[32] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
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
	[4] -1	0	0xeff00000 - 0xeff000ff (0x100) MX[B]
	[5] -1	0	0xefd00000 - 0xefd03fff (0x4000) MX[B]
	[6] -1	0	0xefc00000 - 0xefc003ff (0x400) MX[B]
	[7] -1	0	0xef900000 - 0xef91ffff (0x20000) MX[B]
	[8] -1	0	0xefa00000 - 0xefa00fff (0x1000) MX[B]
	[9] -1	0	0xef800000 - 0xef8007ff (0x800) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xeae00000 - 0xeae1ffff (0x20000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[15] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[17] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[22] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[24] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[26] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[33] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[34] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[36] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[37] -1	0	0x0000a400 - 0x0000a43f (0x40) IX[B]
	[38] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9625
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9625
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) NVIDIA dlloader X Driver  1.0-9625  Thu Sep 14 15:35:06 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:14:0) found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xeff00000 - 0xeff000ff (0x100) MX[B]
	[5] -1	0	0xefd00000 - 0xefd03fff (0x4000) MX[B]
	[6] -1	0	0xefc00000 - 0xefc003ff (0x400) MX[B]
	[7] -1	0	0xef900000 - 0xef91ffff (0x20000) MX[B]
	[8] -1	0	0xefa00000 - 0xefa00fff (0x1000) MX[B]
	[9] -1	0	0xef800000 - 0xef8007ff (0x800) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xeae00000 - 0xeae1ffff (0x20000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[15] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[17] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[22] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[24] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[26] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[33] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[34] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[36] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[37] -1	0	0x0000a400 - 0x0000a43f (0x40) IX[B]
	[38] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xeff00000 - 0xeff000ff (0x100) MX[B]
	[5] -1	0	0xefd00000 - 0xefd03fff (0x4000) MX[B]
	[6] -1	0	0xefc00000 - 0xefc003ff (0x400) MX[B]
	[7] -1	0	0xef900000 - 0xef91ffff (0x20000) MX[B]
	[8] -1	0	0xefa00000 - 0xefa00fff (0x1000) MX[B]
	[9] -1	0	0xef800000 - 0xef8007ff (0x800) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xeae00000 - 0xeae1ffff (0x20000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[15] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[17] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[25] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[26] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[29] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[31] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[32] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[33] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[34] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[35] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[36] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[37] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[38] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[39] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[40] -1	0	0x0000a400 - 0x0000a43f (0x40) IX[B]
	[41] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NvAGP" "0"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "TwinViewOrientation" "LeftOf"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "31-87"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "55-85"
(**) NVIDIA(0): Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "TripleBuffer" "true"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): Use of AGP disabled per request
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5900XT at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.35.20.45.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5900XT at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     @@@ (CRT-0)
(--) NVIDIA(0):     Envision EN9110 (DFP-0)
(--) NVIDIA(0): @@@ (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): Envision EN9110 (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): Envision EN9110 (DFP-0): External Single Link TMDS
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024,1280x1024"
(II) NVIDIA(0):     "1024x768,1024x768"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): Cannot find size of first mode for @@@ (CRT-0); cannot compute
(WW) NVIDIA(0):     DPI from @@@ (CRT-0)'s EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[1] 0	0	0xe9000000 - 0xe9ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xeff00000 - 0xeff000ff (0x100) MX[B]
	[7] -1	0	0xefd00000 - 0xefd03fff (0x4000) MX[B]
	[8] -1	0	0xefc00000 - 0xefc003ff (0x400) MX[B]
	[9] -1	0	0xef900000 - 0xef91ffff (0x20000) MX[B]
	[10] -1	0	0xefa00000 - 0xefa00fff (0x1000) MX[B]
	[11] -1	0	0xef800000 - 0xef8007ff (0x800) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xeae00000 - 0xeae1ffff (0x20000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[17] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[18] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[19] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[27] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[28] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[29] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[30] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[32] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[33] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[34] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[35] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[36] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[37] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[38] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[39] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[40] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[41] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[42] -1	0	0x0000a400 - 0x0000a43f (0x40) IX[B]
	[43] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[44] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[45] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(GPU-1): NVIDIA GPU GeForce 6200 at PCI:0:14:0 (GPU-1)
(--) NVIDIA(GPU-1): Memory: 131072 kBytes
(--) NVIDIA(GPU-1): VideoBIOS: 05.44.a2.07.61
(--) NVIDIA(GPU-1): Interlaced video modes are supported on this GPU
(--) NVIDIA(GPU-1): Connected display device(s) on GeForce 6200 at PCI:0:14:0:
(--) NVIDIA(GPU-1):     DELL P780 (CRT-0)
(--) NVIDIA(GPU-1): DELL P780 (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Setting mode "1280x1024,1280x1024"
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
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+gb+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

```


xorg.conf
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen        0 "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
Option "Xinerama" "Off"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
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
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Extensions"
     Option "Composite" "Enable"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Envision EN9110"
    HorizSync       31.0 - 87.0
    VertRefresh     55.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
Identifier	"Videocard0"
Driver		"nvidia"
VendorName	"NVIDIA Corporation"
BoardName	"GeForce FX 5900XT"
BusID		"PCI:1:0:0"
Option	   	"NvAGP" "0"
Option 		"TripleBuffer" "true"
Option 	   	"TwinView" "1"
Option		"TwinViewOrientation" "LeftOf"
#Option		"HorizSync"   "DFP: 31-87; CRT: 31-87"
#Option 	"VertRefresh" "DFP: 55-85; CRT: 55-85"
Option 		"SecondMonitorHorizSync" "31-87"
Option 		"SecondMonitorVertRefresh" "55-85"
#Option 	"ConnectedMonitor" "CRT, DFP"
Option 		"RenderAccel" "true"
Option 		"AllowGLXWithComposite" "true"
Option		"MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
Option 		"AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    

    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

---

