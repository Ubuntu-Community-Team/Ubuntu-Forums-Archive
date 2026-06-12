---
title: "Video Driver reinstall required at each boot"
date: 2007-10-17
forum: General Help
---

### Post by rshawgo on 2007-10-17
I have been having an issue where, at each boot up, I must reinstall the nvidia video drivers and then everything is OK.  It happened a while ago, after I upgraded from Edgy to Feisty.  I have created a small script which runs and shuts down GDM, installed the driver, then restarts the GDM,  but I would really just like it to work.

System:  AMD 4200+ dual core with a GeForce 7300 GT display driver.  Currently running version tly running of the nVidia driver.  

If anyone has a suggestion as to a more permanent fix for this I would appreciate it.  I had hoped that either a new kernel module or updated video drivers would fix this issue, but I was wrong.  Xorg.log posted below

.```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ryans 3.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 17 05:35:14 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Nvidia GeForce 7300 GT"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
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
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
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
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7a16e0
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
(II) PCI: 00:00:0: chip 10de,0369 card 1297,3077 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0362 card 1297,3077 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0368 card 1297,3077 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:01:2: chip 10de,036a card 1297,3077 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,036c card 1297,3077 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,036d card 1297,3077 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,036e card 1297,3077 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:05:0: chip 10de,037f card 1297,3077 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:05:1: chip 10de,037f card 1297,3077 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:06:0: chip 10de,0370 card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:06:1: chip 10de,0371 card 1297,3077 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:08:0: chip 10de,0373 card 1297,3077 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:0f:0: chip 10de,0377 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:08:0: chip 1106,3044 card 1106,3044 rev 80 class 0c,00,10 hdr 00
(II) PCI: 02:00:0: chip 10de,0393 card 3842,c443 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:6:0), (0,1,1), BCTRL: 0x0a04 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:15:0), (0,2,2), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfcffffff (0x3000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(2:0:0) nVidia Corporation G70 [GeForce 7300 GT] rev 161, Mem @ 0xfa000000/24, 0xe0000000/28, 0xfb000000/24, I/O @ 0xac00/7
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[1] -1	0	0xfe029000 - 0xfe02900f (0x10) MX[B]
	[2] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[4] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[5] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[6] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[7] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[8] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[13] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[14] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[15] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[16] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[17] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[18] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[20] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[21] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[22] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[23] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[24] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[25] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[26] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[27] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[1] -1	0	0xfe029000 - 0xfe02900f (0x10) MX[B]
	[2] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[4] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[5] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[6] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[7] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[8] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[13] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[14] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[15] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[16] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[17] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[18] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[20] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[21] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[22] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[23] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[24] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[25] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[26] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[27] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
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
	[4] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[5] -1	0	0xfe029000 - 0xfe02900f (0x10) MX[B]
	[6] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[9] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[13] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[20] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[31] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[32] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[33] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
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
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:51:24 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
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
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:10:47 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02:00:0
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
	[4] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[5] -1	0	0xfe029000 - 0xfe02900f (0x10) MX[B]
	[6] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[9] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[13] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[20] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[31] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[32] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[33] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[5] -1	0	0xfe029000 - 0xfe02900f (0x10) MX[B]
	[6] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[9] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[13] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[24] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[25] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[26] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[27] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[29] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[30] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[31] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[32] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[33] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[34] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[35] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[36] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


```

---

### Post by DagMan on 2007-10-17
I had this issue.
It's the restricted driver manager selecting the Ubuntu restricted modules restricted driver instead of the one you built.  My only other module the restricted manager spoke of was my ipw3945 wireless card.  The chances are likely that it's the same for you.  If all that's listed there is this and NVIDIA, then it's easily fixed.  
You can't just uninstall package because it removes the ipw3945 module in the process... for me, you're case might be differant.
Anyhow, just do this
```
sudo chmod -x /etc/init.d/linux-restricted-modules-common
```
then reboot and check to see if the other restricted modules your machine might be running still work.  Some may not, my wireless did.  If that breaks something then undo it like this and reboot again
```
sudo chmod +x /etc/init.d/linux-restricted-modules-common
```
and then you'lle have to look at that script /etc/init.d/ linux-restricted-modules-common and see what it does and what other scripts it calls and simply stop it from doing anything with nvidia... which as I recall wasn't as simple as I thought it would be since it handles quite a few modules and forks out into quite a few scripts that in turn call on other things and so on.  If you need help with this please also post what restricted modules the restricted manager thing is listing.

---

### Post by dabl on 2007-10-17
Boot Ubuntu, install your Nvidia driver, then open a console window and do the following:

```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

This will write a new /etc/X11/xorg.conf file that supports glx.  Re-start the X server with Ctrl-Alt-Backspace.

Open the console again, and enter ```
sudo nvidia-settings
```

Now you can click on the X Server Configuration tab, click "detect displays", and then set the resolution to what you would like as a default.  I leave the "refresh" setting at "Auto", but you can set it if you wish.  When you have it the way you want it, click the "Save to X Configuration File" button in the lower right, put an "x" in "Merge", click "Save", and it will overwrite these settings to the /etc/X11/xorg.conf file.

Now you can restart the X server again, and it should come up with your default settings, and always boot up that way.

:guitar:

---

### Post by DagMan on 2007-10-18
I tried that and it fixed some things that I was previously using a workaround for in compiz.  I re-enabled my restricted-driver thing in init.d but it's a custom kernel so I cant tell if it's made a differance there without having a harder look, but thanks for that.

---

### Post by rshawgo on 2007-10-19
Thanks, made the restricted module change and all is well.  Back to happy computing without driver installs every boot.
Thanks again.

---

### Post by runemaste644 on 2007-12-18
What packages did you reinstall? I have the same error as you, but i dont know what package i need to reinstall. I dont care about installing drivers on every bootup, i just want to boot up X-Windows!!!!!!!

---

