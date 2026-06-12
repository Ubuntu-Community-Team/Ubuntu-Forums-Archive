---
title: "X or GDM bad"
date: 2006-12-28
forum: General Help
---

### Post by davidsampson on 2006-12-28
When I boot up my computer, the initial boot goes fine, but then it start gdm, the login manager, and the screen flashes 3 times, trying to start X, and then fails, giving me a diagnostic screen, which informs me that X cannot start, GDM has an error, please fix and try again.  I am displayed a login prompt, so I log in.  If I type 'startx', things run smoothly, but I am loaded into gnome, without a login screen.  I would like to be able to load XFCE, and I would like to have a log in screen as well.  I have an AMD64 x2, running (X)ubuntu Edgy, with two monitors, one a 17" CRT running at 1600x1200 pixels, and a 19" LCD running at 1440x900.  After I started using the 2 monitors, these errors started occuring.  I will include xorg.conf an Xorg.0.log, as well as anything else if you need it.

/etc/X11/xorg.conf
```
Section "Files"
	FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
	FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
	FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
	FontPath   "/usr/X11R6/lib/X11/fonts/CID/"
	FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
	FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"
EndSection
Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card 1"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
	Screen		0
	Option "MonitorLayout" "CRT, TPMS"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card 2"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
	Screen		1
	Option "MonitorLayout" "CRT, TPMS"
EndSection


Section "Monitor"
	Identifier	"KOMODO K50X 1"
	Option		"DPMS"
	HorizSync 30-75
	VertRefresh 30-60
EndSection

Section "Monitor"
	Identifier	"KOMODO K50X 2"
	Option		"DPMS"
	HorizSync 30-75
	VertRefresh 30-60
EndSection

Section "Screen"
	Identifier	"0"
	Device		"NVIDIA Corporation NVIDIA Default Card 1"
	Monitor		"KOMODO K50X 1"
	DefaultDepth	24
		SubSection "Display"
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"1"
	Device		"NVIDIA Corporation NVIDIA Default Card 2"
	Monitor		"KOMODO K50X 2"
	DefaultDepth	24
		SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier 	"Multihead"
	Screen 		0 "0"
	Screen		1 "1" RightOf "0"
	InputDevice 	"Generic Keyboard"
	InputDevice 	"Configured Mouse"
EndSection


Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
Option "xinerama" "true"
EndSection
```

/var/log/Xorg.0.log
```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 x86_64 
Current Operating System: Linux admin-desktop 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 28 14:42:42 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Multihead"
(**) |-->Screen "0" (0)
(**) |   |-->Monitor "KOMODO K50X 1"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card 1"
(**) |-->Screen "1" (1)
(**) |   |-->Monitor "KOMODO K50X 2"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card 2"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) `fonts.dir' not found (or not valid) in "/usr/X11R6/lib/X11/fonts/misc/".
	Entry deleted from font path.
	(Run 'mkfontdir' onX Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 x86_64 
Current Operating System: Linux admin-desktop 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 28 14:42:42 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Multihead"
(**) |-->Screen "0" (0)
(**) |   |-->Monitor "KOMODO K50X 1"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card 1"
(**) |-->Screen "1" (1) "/usr/X11R6/lib/X11/fonts/misc/").
(WW) The directory "/usr/X11R6/lib/X11/fonts/Speedo/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Type1/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/CID/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) FontPath is completely invalid.  Using compiled-in default.
(==) FontPath set to:
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "true"
(**) Xinerama: enabled
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,02f4 card 1043,81d2 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 1043,81d2 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 1043,81d2 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 1043,81d2 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 1043,81d2 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 1043,81d2 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 1043,81d2 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 1043,81d2 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,005e card 1043,815a rev a4 class 05,80,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0050 card 1043,815a rev a4 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0052 card 1043,815a rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,005a card 1043,815a rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,005b card 1043,815a rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0059 card 1043,812a rev a2 class 04,01,00 hdr 00
(II) PCI: 00:0f:0: chip 10de,0053 card 1043,815a rev f3 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 10de,0054 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:11:0: chip 10de,0055 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:12:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:13:0: chip 10de,0057 card 1043,8141 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:16:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:17:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1095,3132 card 1043,8177 rev 01 class 01,04,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4362 card 1043,8142 rev 15 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 10de,0392 card 3842,c549 rev a1 class 03,00,00 hdr 00
(II) PCI: 04:07:0: chip 168c,001a card 1186,3a1d rev 01 class 02,00,00 hdr 00
(II) PCI: 04:0b:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdce00000 - 0xdcefffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdcf00000 - 0xdcffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:4:0), (0,3,3), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdd000000 - 0xdfefffff (0x2f00000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:18:0), (0,4,4), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xdff00000 - 0xdfffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:22:0), (0,5,5), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:23:0), (0,6,6), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(3:0:0) nVidia Corporation unknown chipset (0x0392) rev 161, Mem @ 0xde000000/24, 0xc0000000/28, 0xdd000000/24, I/O @ 0xec00/7, BIOS @ 0xdfee0000/17
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
	[0] -1	0	0xdffe8000 - 0xdffebfff (0x4000) MX[B]
	[1] -1	0	0xdffef800 - 0xdffeffff (0x800) MX[B]
	[2] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[3] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[4] -1	0	0xdcef8000 - 0xdcefbfff (0x4000) MX[B]
	[5] -1	0	0xdceffc00 - 0xdceffc7f (0x80) MX[B]
	[6] -1	0	0xdcdfa000 - 0xdcdfafff (0x1000) MX[B]
	[7] -1	0	0xdcdfb000 - 0xdcdfbfff (0x1000) MX[B]
	[8] -1	0	0xdcdfc000 - 0xdcdfcfff (0x1000) MX[B]
	[9] -1	0	0xdcdfd000 - 0xdcdfdfff (0x1000) MX[B]
	[10] -1	0	0xdcdffc00 - 0xdcdffcff (0x100) MX[B]
	[11] -1	0	0xdcdfe000 - 0xdcdfefff (0x1000) MX[B]
	[12] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[18] -1	0	0x00009480 - 0x00009487 (0x8) IX[B]
	[19] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[20] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[21] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[23] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[25] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[26] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[27] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[28] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[31] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[32] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[33] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[34] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdffe8000 - 0xdffebfff (0x4000) MX[B]
	[1] -1	0	0xdffef800 - 0xdffeffff (0x800) MX[B]
	[2] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[3] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[4] -1	0	0xdcef8000 - 0xdcefbfff (0x4000) MX[B]
	[5] -1	0	0xdceffc00 - 0xdceffc7f (0x80) MX[B]
	[6] -1	0	0xdcdfa000 - 0xdcdfafff (0x1000) MX[B]
	[7] -1	0	0xdcdfb000 - 0xdcdfbfff (0x1000) MX[B]
	[8] -1	0	0xdcdfc000 - 0xdcdfcfff (0x1000) MX[B]
	[9] -1	0	0xdcdfd000 - 0xdcdfdfff (0x1000) MX[B]
	[10] -1	0	0xdcdffc00 - 0xdcdffcff (0x100) MX[B]
	[11] -1	0	0xdcdfe000 - 0xdcdfefff (0x1000) MX[B]
	[12] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[18] -1	0	0x00009480 - 0x00009487 (0x8) IX[B]
	[19] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[20] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[21] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[23] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[25] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[26] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[27] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[28] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[31] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[32] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[33] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[34] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
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
	[4] -1	0	0xdffe8000 - 0xdffebfff (0x4000) MX[B]
	[5] -1	0	0xdffef800 - 0xdffeffff (0x800) MX[B]
	[6] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[7] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[8] -1	0	0xdcef8000 - 0xdcefbfff (0x4000) MX[B]
	[9] -1	0	0xdceffc00 - 0xdceffc7f (0x80) MX[B]
	[10] -1	0	0xdcdfa000 - 0xdcdfafff (0x1000) MX[B]
	[11] -1	0	0xdcdfb000 - 0xdcdfbfff (0x1000) MX[B]
	[12] -1	0	0xdcdfc000 - 0xdcdfcfff (0x1000) MX[B]
	[13] -1	0	0xdcdfd000 - 0xdcdfdfff (0x1000) MX[B]
	[14] -1	0	0xdcdffc00 - 0xdcdffcff (0x100) MX[B]
	[15] -1	0	0xdcdfe000 - 0xdcdfefff (0x1000) MX[B]
	[16] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[17] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[24] -1	0	0x00009480 - 0x00009487 (0x8) IX[B]
	[25] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[26] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[27] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[28] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[29] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[30] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[31] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[32] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[33] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[34] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[35] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[36] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[37] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[38] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[39] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[40] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[41] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
	compiled for 4.0.2, module version = 1.0.8776
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
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
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
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:56:44 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03:00:0
(--) Chipset NVIDIA GPU found
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
	[4] -1	0	0xdffe8000 - 0xdffebfff (0x4000) MX[B]
	[5] -1	0	0xdffef800 - 0xdffeffff (0x800) MX[B]
	[6] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[7] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[8] -1	0	0xdcef8000 - 0xdcefbfff (0x4000) MX[B]
	[9] -1	0	0xdceffc00 - 0xdceffc7f (0x80) MX[B]
	[10] -1	0	0xdcdfa000 - 0xdcdfafff (0x1000) MX[B]
	[11] -1	0	0xdcdfb000 - 0xdcdfbfff (0x1000) MX[B]
	[12] -1	0	0xdcdfc000 - 0xdcdfcfff (0x1000) MX[B]
	[13] -1	0	0xdcdfd000 - 0xdcdfdfff (0x1000) MX[B]
	[14] -1	0	0xdcdffc00 - 0xdcdffcff (0x100) MX[B]
	[15] -1	0	0xdcdfe000 - 0xdcdfefff (0x1000) MX[B]
	[16] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[17] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[24] -1	0	0x00009480 - 0x00009487 (0x8) IX[B]
	[25] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[26] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[27] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[28] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[29] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[30] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[31] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[32] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[33] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[34] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[35] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[36] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[37] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[38] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[39] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[40] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[41] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffe8000 - 0xdffebfff (0x4000) MX[B]
	[5] -1	0	0xdffef800 - 0xdffeffff (0x800) MX[B]
	[6] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[7] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[8] -1	0	0xdcef8000 - 0xdcefbfff (0x4000) MX[B]
	[9] -1	0	0xdceffc00 - 0xdceffc7f (0x80) MX[B]
	[10] -1	0	0xdcdfa000 - 0xdcdfafff (0x1000) MX[B]
	[11] -1	0	0xdcdfb000 - 0xdcdfbfff (0x1000) MX[B]
	[12] -1	0	0xdcdfc000 - 0xdcdfcfff (0x1000) MX[B]
	[13] -1	0	0xdcdfd000 - 0xdcdfdfff (0x1000) MX[B]
	[14] -1	0	0xdcdffc00 - 0xdcdffcff (0x100) MX[B]
	[15] -1	0	0xdcdfe000 - 0xdcdfefff (0x1000) MX[B]
	[16] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[17] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[26] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[27] -1	0	0x00009480 - 0x00009487 (0x8) IX[B]
	[28] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[29] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[30] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[31] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[32] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[33] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[34] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[35] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[36] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[37] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[38] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[39] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[40] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[41] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[42] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[43] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[44] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
	[45] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[46] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(0): Unable to read EDID for display device CRT-1
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS at PCI:3:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.16.03
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:3:0:0:
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0):     HSD HW191D (DFP-0)
(--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): HSD HW191D (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): HSD HW191D (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU GeForce 7600 GS at PCI:3:0:0
(--) NVIDIA(1): VideoRAM: 262144 kBytes
(--) NVIDIA(1): VideoBIOS: 05.73.22.16.03
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 7600 GS at PCI:3:0:0:
(--) NVIDIA(1):     CRT-1
(--) NVIDIA(1):     HSD HW191D (DFP-0)
(--) NVIDIA(1): CRT-1: 400.0 MHz maximum pixel clock
(--) NVIDIA(1): HSD HW191D (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(1): HSD HW191D (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(1): Assigned Display Device: DFP-0
(WW) NVIDIA(1): No valid modes for "2560x1600"; removing.
(WW) NVIDIA(1): 
(WW) NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(1):     "nvidia-auto-select".
(WW) NVIDIA(1): 
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "nvidia-auto-select"
(II) NVIDIA(1): Virtual screen size determined to be 1440 x 900
(++) NVIDIA(1): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after preInit:
	[0] 0	0	0xdd000000 - 0xddffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdffe8000 - 0xdffebfff (0x4000) MX[B]
	[8] -1	0	0xdffef800 - 0xdffeffff (0x800) MX[B]
	[9] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[10] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[11] -1	0	0xdcef8000 - 0xdcefbfff (0x4000) MX[B]
	[12] -1	0	0xdceffc00 - 0xdceffc7f (0x80) MX[B]
	[13] -1	0	0xdcdfa000 - 0xdcdfafff (0x1000) MX[B]
	[14] -1	0	0xdcdfb000 - 0xdcdfbfff (0x1000) MX[B]
	[15] -1	0	0xdcdfc000 - 0xdcdfcfff (0x1000) MX[B]
	[16] -1	0	0xdcdfd000 - 0xdcdfdfff (0x1000) MX[B]
	[17] -1	0	0xdcdffc00 - 0xdcdffcff (0x100) MX[B]
	[18] -1	0	0xdcdfe000 - 0xdcdfefff (0x1000) MX[B]
	[19] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[20] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[21] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[22] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[23] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[24] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[25] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[26] 0	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[30] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[31] -1	0	0x00009480 - 0x00009487 (0x8) IX[B]
	[32] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[33] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[34] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[35] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[36] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[37] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[38] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[39] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[40] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[41] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[42] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[43] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[44] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[45] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[46] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[47] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[48] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
	[49] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[50] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "MonitorLayout" is not used
(==) RandR enabled
(II) NVIDIA(1): Setting mode "nvidia-auto-select"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(1): DPMS enabled
(WW) NVIDIA(1): Option "MonitorLayout" is not used
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
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
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc104)+us" };
    xkb_geometry             { include "pc(pc104)" };
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources

```

Thanks in advance

---

### Post by kd7swh on 2006-12-29
Have you tried re-installing GDM? I didn't see anything too strange.

---

### Post by davidsampson on 2006-12-29
Tried it, same thing happened, but it printed an error about the font initialization:

Xorg.93.log
```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 x86_64 
Current Operating System: Linux admin-desktop 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.93.log", Time: Fri Dec 29 14:30:31 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Multihead"
(**) |-->Screen "0" (0)
(**) |   |-->Monitor "KOMODO K50X 1"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card 1"
(**) |-->Screen "1" (1)
(**) |   |-->Monitor "KOMODO K50X 2"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card 2"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) `fonts.dir' not found (or not valid) in "/usr/X11R6/lib/X11/fonts/misc/".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/X11R6/lib/X11/fonts/misc/").
(WW) The directory "/usr/X11R6/lib/X11/fonts/Speedo/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Type1/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/CID/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) FontPath is completely invalid.  Using compiled-in default.
(==) FontPath set to:
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "true"
(**) Xinerama: enabled
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
(II) PCI: 00:00:0: chip 10de,02f4 card 1043,81d2 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 1043,81d2 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 1043,81d2 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 1043,81d2 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 1043,81d2 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 1043,81d2 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 1043,81d2 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 1043,81d2 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,005e card 1043,815a rev a4 class 05,80,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0050 card 1043,815a rev a4 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0052 card 1043,815a rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,005a card 1043,815a rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,005b card 1043,815a rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0059 card 1043,812a rev a2 class 04,01,00 hdr 00
(II) PCI: 00:0f:0: chip 10de,0053 card 1043,815a rev f3 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 10de,0054 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:11:0: chip 10de,0055 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:12:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:13:0: chip 10de,0057 card 1043,8141 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:16:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:17:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1095,3132 card 1043,8177 rev 01 class 01,04,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4362 card 1043,8142 rev 15 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 10de,0392 card 3842,c549 rev a1 class 03,00,00 hdr 00
(II) PCI: 04:07:0: chip 168c,001a card 1186,3a1d rev 01 class 02,00,00 hdr 00
(II) PCI: 04:0b:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdce00000 - 0xdcefffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdcf00000 - 0xdcffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:4:0), (0,3,3), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdd000000 - 0xdfefffff (0x2f00000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:18:0), (0,4,4), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xdff00000 - 0xdfffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:22:0), (0,5,5), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:23:0), (0,6,6), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(3:0:0) nVidia Corporation unknown chipset (0x0392) rev 161, Mem @ 0xde000000/24, 0xc0000000/28, 0xdd000000/24, I/O @ 0xec00/7, BIOS @ 0xdfee0000/17
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
	[0] -1	0	0xdffe8000 - 0xdffebfff (0x4000) MX[B]
	[1] -1	0	0xdffef800 - 0xdffeffff (0x800) MX[B]
	[2] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[3] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[4] -1	0	0xdcef8000 - 0xdcefbfff (0x4000) MX[B]
	[5] -1	0	0xdceffc00 - 0xdceffc7f (0x80) MX[B]
	[6] -1	0	0xdcdfa000 - 0xdcdfafff (0x1000) MX[B]
	[7] -1	0	0xdcdfb000 - 0xdcdfbfff (0x1000) MX[B]
	[8] -1	0	0xdcdfc000 - 0xdcdfcfff (0x1000) MX[B]
	[9] -1	0	0xdcdfd000 - 0xdcdfdfff (0x1000) MX[B]
	[10] -1	0	0xdcdffc00 - 0xdcdffcff (0x100) MX[B]
	[11] -1	0	0xdcdfe000 - 0xdcdfefff (0x1000) MX[B]
	[12] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[18] -1	0	0x00009480 - 0x00009487 (0x8) IX[B]
	[19] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[20] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[21] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[23] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[25] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[26] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[27] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[28] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[31] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[32] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[33] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[34] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdffe8000 - 0xdffebfff (0x4000) MX[B]
	[1] -1	0	0xdffef800 - 0xdffeffff (0x800) MX[B]
	[2] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[3] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[4] -1	0	0xdcef8000 - 0xdcefbfff (0x4000) MX[B]
	[5] -1	0	0xdceffc00 - 0xdceffc7f (0x80) MX[B]
	[6] -1	0	0xdcdfa000 - 0xdcdfafff (0x1000) MX[B]
	[7] -1	0	0xdcdfb000 - 0xdcdfbfff (0x1000) MX[B]
	[8] -1	0	0xdcdfc000 - 0xdcdfcfff (0x1000) MX[B]
	[9] -1	0	0xdcdfd000 - 0xdcdfdfff (0x1000) MX[B]
	[10] -1	0	0xdcdffc00 - 0xdcdffcff (0x100) MX[B]
	[11] -1	0	0xdcdfe000 - 0xdcdfefff (0x1000) MX[B]
	[12] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[18] -1	0	0x00009480 - 0x00009487 (0x8) IX[B]
	[19] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[20] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[21] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[23] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[25] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[26] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[27] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[28] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[31] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[32] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[33] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[34] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
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
	[4] -1	0	0xdffe8000 - 0xdffebfff (0x4000) MX[B]
	[5] -1	0	0xdffef800 - 0xdffeffff (0x800) MX[B]
	[6] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[7] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[8] -1	0	0xdcef8000 - 0xdcefbfff (0x4000) MX[B]
	[9] -1	0	0xdceffc00 - 0xdceffc7f (0x80) MX[B]
	[10] -1	0	0xdcdfa000 - 0xdcdfafff (0x1000) MX[B]
	[11] -1	0	0xdcdfb000 - 0xdcdfbfff (0x1000) MX[B]
	[12] -1	0	0xdcdfc000 - 0xdcdfcfff (0x1000) MX[B]
	[13] -1	0	0xdcdfd000 - 0xdcdfdfff (0x1000) MX[B]
	[14] -1	0	0xdcdffc00 - 0xdcdffcff (0x100) MX[B]
	[15] -1	0	0xdcdfe000 - 0xdcdfefff (0x1000) MX[B]
	[16] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[17] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[24] -1	0	0x00009480 - 0x00009487 (0x8) IX[B]
	[25] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[26] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[27] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[28] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[29] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[30] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[31] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[32] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[33] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[34] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[35] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[36] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[37] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[38] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[39] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[40] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[41] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
	compiled for 4.0.2, module version = 1.0.8776
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
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
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
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:56:44 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03:00:0
(--) Chipset NVIDIA GPU found
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
	[4] -1	0	0xdffe8000 - 0xdffebfff (0x4000) MX[B]
	[5] -1	0	0xdffef800 - 0xdffeffff (0x800) MX[B]
	[6] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[7] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[8] -1	0	0xdcef8000 - 0xdcefbfff (0x4000) MX[B]
	[9] -1	0	0xdceffc00 - 0xdceffc7f (0x80) MX[B]
	[10] -1	0	0xdcdfa000 - 0xdcdfafff (0x1000) MX[B]
	[11] -1	0	0xdcdfb000 - 0xdcdfbfff (0x1000) MX[B]
	[12] -1	0	0xdcdfc000 - 0xdcdfcfff (0x1000) MX[B]
	[13] -1	0	0xdcdfd000 - 0xdcdfdfff (0x1000) MX[B]
	[14] -1	0	0xdcdffc00 - 0xdcdffcff (0x100) MX[B]
	[15] -1	0	0xdcdfe000 - 0xdcdfefff (0x1000) MX[B]
	[16] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[17] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[24] -1	0	0x00009480 - 0x00009487 (0x8) IX[B]
	[25] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[26] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[27] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[28] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[29] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[30] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[31] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[32] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[33] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[34] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[35] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[36] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[37] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[38] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[39] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[40] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[41] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffe8000 - 0xdffebfff (0x4000) MX[B]
	[5] -1	0	0xdffef800 - 0xdffeffff (0x800) MX[B]
	[6] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[7] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[8] -1	0	0xdcef8000 - 0xdcefbfff (0x4000) MX[B]
	[9] -1	0	0xdceffc00 - 0xdceffc7f (0x80) MX[B]
	[10] -1	0	0xdcdfa000 - 0xdcdfafff (0x1000) MX[B]
	[11] -1	0	0xdcdfb000 - 0xdcdfbfff (0x1000) MX[B]
	[12] -1	0	0xdcdfc000 - 0xdcdfcfff (0x1000) MX[B]
	[13] -1	0	0xdcdfd000 - 0xdcdfdfff (0x1000) MX[B]
	[14] -1	0	0xdcdffc00 - 0xdcdffcff (0x100) MX[B]
	[15] -1	0	0xdcdfe000 - 0xdcdfefff (0x1000) MX[B]
	[16] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[17] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[26] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[27] -1	0	0x00009480 - 0x00009487 (0x8) IX[B]
	[28] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[29] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[30] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[31] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[32] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[33] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[34] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[35] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[36] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[37] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[38] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[39] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[40] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[41] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[42] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[43] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[44] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
	[45] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[46] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(0): Unable to read EDID for display device CRT-1
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS at PCI:3:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.16.03
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:3:0:0:
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0):     HSD HW191D (DFP-0)
(--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): HSD HW191D (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): HSD HW191D (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
(WW) NVIDIA(0):     from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU GeForce 7600 GS at PCI:3:0:0
(--) NVIDIA(1): VideoRAM: 262144 kBytes
(--) NVIDIA(1): VideoBIOS: 05.73.22.16.03
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 7600 GS at PCI:3:0:0:
(--) NVIDIA(1):     CRT-1
(--) NVIDIA(1):     HSD HW191D (DFP-0)
(--) NVIDIA(1): CRT-1: 400.0 MHz maximum pixel clock
(--) NVIDIA(1): HSD HW191D (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(1): HSD HW191D (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(1): Assigned Display Device: DFP-0
(WW) NVIDIA(1): No valid modes for "2560x1600"; removing.
(WW) NVIDIA(1): 
(WW) NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(1):     "nvidia-auto-select".
(WW) NVIDIA(1): 
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "nvidia-auto-select"
(II) NVIDIA(1): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(1): DPI set to (89, 87); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after preInit:
	[0] 0	0	0xdd000000 - 0xddffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdffe8000 - 0xdffebfff (0x4000) MX[B]
	[8] -1	0	0xdffef800 - 0xdffeffff (0x800) MX[B]
	[9] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[10] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[11] -1	0	0xdcef8000 - 0xdcefbfff (0x4000) MX[B]
	[12] -1	0	0xdceffc00 - 0xdceffc7f (0x80) MX[B]
	[13] -1	0	0xdcdfa000 - 0xdcdfafff (0x1000) MX[B]
	[14] -1	0	0xdcdfb000 - 0xdcdfbfff (0x1000) MX[B]
	[15] -1	0	0xdcdfc000 - 0xdcdfcfff (0x1000) MX[B]
	[16] -1	0	0xdcdfd000 - 0xdcdfdfff (0x1000) MX[B]
	[17] -1	0	0xdcdffc00 - 0xdcdffcff (0x100) MX[B]
	[18] -1	0	0xdcdfe000 - 0xdcdfefff (0x1000) MX[B]
	[19] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[20] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[21] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[22] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[23] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[24] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[25] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[26] 0	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[30] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[31] -1	0	0x00009480 - 0x00009487 (0x8) IX[B]
	[32] -1	0	0x00009800 - 0x0000980f (0x10) IX[B]
	[33] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[34] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[35] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[36] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[37] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[38] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[39] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[40] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[41] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[42] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[43] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[44] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[45] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[46] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[47] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[48] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
	[49] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[50] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "MonitorLayout" is not used
(==) RandR enabled
(II) NVIDIA(1): Setting mode "nvidia-auto-select"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(1): DPMS enabled
(WW) NVIDIA(1): Option "MonitorLayout" is not used
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
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
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc104)+us" };
    xkb_geometry             { include "pc(pc104)" };
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources

```

---

### Post by Unterseeboot_234 on 2006-12-31
Hey, I'm a noob, but I thought Linux only supported TrueType fonts. Type1 is Postscript and Type3 is TrueType. I'd have to plug my old Win box back in to clarify that fact. But if anyone knows if Type1 is allowed on ubuntu and if this could trigger one of your symptoms.

---

