---
title: "fglrx 8.42 + Gutsy + 64 bits - Imposible Direct render"
date: 2007-11-12
forum: General Help
---

### Post by minijai on 2007-11-12
Hello,
(Excuse me, my english it's not very well)

My computer is an AMDx2 Dual core. I've an ATI Radeon X1300 in an Ubuntu 7.10 (64 bits), and after reading lots tutorials I haven't any Direct Render since Ubuntu 6.10.
My Ubuntu it's an upgrade from 6.06 to 7.10 (dapper 6.06 /edgy 6.10/..Gutsy 7.10)

I always get this message with the [COLOR="Red"]fglrxinfo[/COLOR] command:

```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```

I can see that the fglxrx Driver is loaded because if I write the next command I can see de module:

```
[COLOR="Red"]lsmod |grep fglrx[/COLOR]
```

Here you can view part of my xorg.conf file (I think it's the most important)
```

# xorg.conf (xorg X Window System server configuration file)

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
EndSection

Section "Device"
	Identifier	"RadeonX1300"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"RadeonX1300"
	Monitor		"Monitor genérico"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "Extensions"
	Option "Composite" "0"
EndSection
```


Can anyone Help me!!
the last tutorial that I follow was:[ this]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

thanks.-

---

### Post by kellemes on 2007-11-12
Can you post /var/log/Xorg.0.log please?

---

### Post by dannns on 2007-11-12
Did you uninstall XGL?

[FONT="Courier New"]sudo apt-get remove xserver-xgl[/FONT]

---

### Post by minijai on 2007-11-12
Hi,
First, I haven't installed then xserver-xgl packaged, and second here is a copy of my /var/log/Xorg.0.log

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux AMD64x2Linux 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 12 20:54:42 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Monitor genérico"
(**) |   |-->Device "RadeonX1300"
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
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
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
(II) Loader magic: 0x7cd8a0
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
(II) PCI: 00:00:0: chip 10de,005e card 1043,815a rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1043,815a rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1043,815a rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1043,815a rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1043,815a rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 1043,812a rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card 1043,815a rev f2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1043,8141 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,7146 card 18bc,2010 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,7166 card 18bc,2011 rev 00 class 03,80,00 hdr 00
(II) PCI: 05:0a:0: chip 1095,3114 card 1043,8167 rev 02 class 01,04,00 hdr 00
(II) PCI: 05:0b:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: 05:0c:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:9:0), (0,5,5), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00008000 - 0x00009fff (0x2000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x880fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:11:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:13:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:14:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc RV515 [Radeon X1300] rev 0, Mem @ 0xc0000000/28, 0xd1000000/16, I/O @ 0xa000/8, BIOS @ 0xd0000000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV515 [Radeon X1300] (Secondary) rev 0, Mem @ 0xd1010000/16
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
	[0] -1	0	0xd3004000 - 0xd3007fff (0x4000) MX[B]
	[1] -1	0	0xd3000000 - 0xd3003fff (0x4000) MX[B]
	[2] -1	0	0xd3009000 - 0xd30097ff (0x800) MX[B]
	[3] -1	0	0xd3008000 - 0xd30083ff (0x400) MX[B]
	[4] -1	0	0xd4000000 - 0xd4000fff (0x1000) MX[B]
	[5] -1	0	0xd4001000 - 0xd4001fff (0x1000) MX[B]
	[6] -1	0	0xd4002000 - 0xd4002fff (0x1000) MX[B]
	[7] -1	0	0xd4003000 - 0xd4003fff (0x1000) MX[B]
	[8] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[9] -1	0	0xd4004000 - 0xd4004fff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xd001ffff (0x20000) MX[B](B)
	[11] -1	0	0xd1000000 - 0xd100ffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[14] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[15] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[16] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[17] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[18] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[32] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[33] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[34] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[36] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xd1010000 - 0xd101ffff (0x10000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd3004000 - 0xd3007fff (0x4000) MX[B]
	[1] -1	0	0xd3000000 - 0xd3003fff (0x4000) MX[B]
	[2] -1	0	0xd3009000 - 0xd30097ff (0x800) MX[B]
	[3] -1	0	0xd3008000 - 0xd30083ff (0x400) MX[B]
	[4] -1	0	0xd4000000 - 0xd4000fff (0x1000) MX[B]
	[5] -1	0	0xd4001000 - 0xd4001fff (0x1000) MX[B]
	[6] -1	0	0xd4002000 - 0xd4002fff (0x1000) MX[B]
	[7] -1	0	0xd4003000 - 0xd4003fff (0x1000) MX[B]
	[8] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[9] -1	0	0xd4004000 - 0xd4004fff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xd001ffff (0x20000) MX[B](B)
	[11] -1	0	0xd1000000 - 0xd100ffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[14] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[15] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[16] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[17] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[18] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[32] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[33] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[34] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[36] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xd1010000 - 0xd101ffff (0x10000) MX[B](B)
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
	[4] -1	0	0xd3004000 - 0xd3007fff (0x4000) MX[B]
	[5] -1	0	0xd3000000 - 0xd3003fff (0x4000) MX[B]
	[6] -1	0	0xd3009000 - 0xd30097ff (0x800) MX[B]
	[7] -1	0	0xd3008000 - 0xd30083ff (0x400) MX[B]
	[8] -1	0	0xd4000000 - 0xd4000fff (0x1000) MX[B]
	[9] -1	0	0xd4001000 - 0xd4001fff (0x1000) MX[B]
	[10] -1	0	0xd4002000 - 0xd4002fff (0x1000) MX[B]
	[11] -1	0	0xd4003000 - 0xd4003fff (0x1000) MX[B]
	[12] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[13] -1	0	0xd4004000 - 0xd4004fff (0x1000) MX[B]
	[14] -1	0	0xd0000000 - 0xd001ffff (0x20000) MX[B](B)
	[15] -1	0	0xd1000000 - 0xd100ffff (0x10000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xd1010000 - 0xd101ffff (0x10000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[21] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[22] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[23] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[24] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[25] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[27] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[28] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[29] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[30] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[31] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[32] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[33] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[34] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[35] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[36] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[37] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[38] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[39] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[40] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[41] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[42] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[43] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
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
	compiled for 7.1.0, module version = 8.42.3
	Module class: X.Org Video Driver
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
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.42.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.423.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 19 2007 16:14:11
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x7146) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd3004000 - 0xd3007fff (0x4000) MX[B]
	[5] -1	0	0xd3000000 - 0xd3003fff (0x4000) MX[B]
	[6] -1	0	0xd3009000 - 0xd30097ff (0x800) MX[B]
	[7] -1	0	0xd3008000 - 0xd30083ff (0x400) MX[B]
	[8] -1	0	0xd4000000 - 0xd4000fff (0x1000) MX[B]
	[9] -1	0	0xd4001000 - 0xd4001fff (0x1000) MX[B]
	[10] -1	0	0xd4002000 - 0xd4002fff (0x1000) MX[B]
	[11] -1	0	0xd4003000 - 0xd4003fff (0x1000) MX[B]
	[12] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[13] -1	0	0xd4004000 - 0xd4004fff (0x1000) MX[B]
	[14] -1	0	0xd0000000 - 0xd001ffff (0x20000) MX[B](B)
	[15] -1	0	0xd1000000 - 0xd100ffff (0x10000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xd1010000 - 0xd101ffff (0x10000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[21] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[22] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[23] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[24] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[25] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[27] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[28] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[29] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[30] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[31] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[32] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[33] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[34] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[35] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[36] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[37] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[38] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[39] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[40] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[41] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[42] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[43] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x7f3b30
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd3004000 - 0xd3007fff (0x4000) MX[B]
	[5] -1	0	0xd3000000 - 0xd3003fff (0x4000) MX[B]
	[6] -1	0	0xd3009000 - 0xd30097ff (0x800) MX[B]
	[7] -1	0	0xd3008000 - 0xd30083ff (0x400) MX[B]
	[8] -1	0	0xd4000000 - 0xd4000fff (0x1000) MX[B]
	[9] -1	0	0xd4001000 - 0xd4001fff (0x1000) MX[B]
	[10] -1	0	0xd4002000 - 0xd4002fff (0x1000) MX[B]
	[11] -1	0	0xd4003000 - 0xd4003fff (0x1000) MX[B]
	[12] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[13] -1	0	0xd4004000 - 0xd4004fff (0x1000) MX[B]
	[14] -1	0	0xd0000000 - 0xd001ffff (0x20000) MX[B](B)
	[15] -1	0	0xd1000000 - 0xd100ffff (0x10000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xd1010000 - 0xd101ffff (0x10000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[24] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[25] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[26] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[27] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[28] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[29] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[30] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[31] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[32] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[33] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[34] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[35] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[36] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[37] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[38] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[39] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[40] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[41] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[42] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[43] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[44] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[45] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[46] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[47] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[48] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
(II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "Radeon X1300 / X1550 Series" (Chipset = 0x7146)
(--) fglrx(0): (PciSubVendor = 0x18bc, PciSubDevice = 0x2010)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xd1000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV515
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: CRT on secondary DAC [crt2]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: NEC  Model: 4272  Serial#: 16843009
(II) fglrx(0): Year: 2000  Week: 16
(II) fglrx(0): EDID Version: 1.2
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate  Composite
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 24
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.625 redY: 0.338   greenX: 0.281 greenY: 0.602
(II) fglrx(0): blueX: 0.149 blueY: 0.073   whiteX: 0.283 whiteY: 0.297
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 720x400@88Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@87Hz (interlaced)
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #5: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 94.5 MHz   Image Size:  315 x 236 mm
(II) fglrx(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) fglrx(0): Ranges: V min: 55  V max: 120 Hz, H min: 31  H max: 70 kHz, PixClock max 120 MHz
(II) fglrx(0): Monitor name: NEC FE700
(II) fglrx(0): Serial No: 0452211YA
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0038a3724201010101
(II) fglrx(0): 	100a01020c211878ea2078a056489a26
(II) fglrx(0): 	12484cfffe80315945596159714f8140
(II) fglrx(0): 	818001010101ea240060410028303060
(II) fglrx(0): 	13003bec1000001e000000fd0037781f
(II) fglrx(0): 	460c000a202020202020000000fc004e
(II) fglrx(0): 	45432046453730300a202020000000ff
(II) fglrx(0): 	003034353232313159410a20202000c8
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Connected Display2: Component Video [cv]
(II) fglrx(0):  Display2: No EDID information from DDC.
(II) fglrx(0):  Display2: Failed to get EDID information. 
(WW) fglrx(0): More than one displays are connected,so clone mode is enabled
(WW) fglrx(0): DALEnableDriverInstance on secondary failed: 9
(II) fglrx(0): For single mode, Component Video is disabled
(II) fglrx(0): Primary Controller - CRT on secondary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 42 modes found for primary display.
(--) fglrx(0): Virtual size is 1920x1080 (pitch 0)
(**) fglrx(0): *Mode "1920x1080": 172.8 MHz (scaled from 0.0 MHz), 67.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1080"  172.79  1920 2040 2248 2576  1080 1081 1084 1118 +hsync
(**) fglrx(0):  Default mode "1920x1080": 81.6 MHz (scaled from 0.0 MHz), 33.6 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"   81.64  1920 1984 2176 2432  1080 1081 1084 1119 interlace +hsync
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"   60.46  1280 1328 1456 1632  720 721 724 741 +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.17  800 848 936 1072  600 601 604 636 +hsync
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632 +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.40  640 680 744 848  480 481 484 515 +hsync
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509 +hsync
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
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
(--) fglrx(0): Display dimensions: (330, 240) mm
(--) fglrx(0): DPI set to (147, 114)
(--) fglrx(0): Virtual size is 1920x1080 (pitch 1920)
(**) fglrx(0): *Mode "1920x1080": 172.8 MHz (scaled from 0.0 MHz), 67.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1080"  172.79  1920 2040 2248 2576  1080 1081 1084 1118 +hsync
(**) fglrx(0):  Default mode "1920x1080": 81.6 MHz (scaled from 0.0 MHz), 33.6 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"   81.64  1920 1984 2176 2432  1080 1081 1084 1119 interlace +hsync
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"   60.46  1280 1328 1456 1632  720 721 724 741 +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.17  800 848 936 1072  600 601 604 636 +hsync
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632 +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.40  640 680 744 848  480 481 484 515 +hsync
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509 +hsync
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
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
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd1000000 - 0xd100ffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xd3004000 - 0xd3007fff (0x4000) MX[B]
	[7] -1	0	0xd3000000 - 0xd3003fff (0x4000) MX[B]
	[8] -1	0	0xd3009000 - 0xd30097ff (0x800) MX[B]
	[9] -1	0	0xd3008000 - 0xd30083ff (0x400) MX[B]
	[10] -1	0	0xd4000000 - 0xd4000fff (0x1000) MX[B]
	[11] -1	0	0xd4001000 - 0xd4001fff (0x1000) MX[B]
	[12] -1	0	0xd4002000 - 0xd4002fff (0x1000) MX[B]
	[13] -1	0	0xd4003000 - 0xd4003fff (0x1000) MX[B]
	[14] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[15] -1	0	0xd4004000 - 0xd4004fff (0x1000) MX[B]
	[16] -1	0	0xd0000000 - 0xd001ffff (0x20000) MX[B](B)
	[17] -1	0	0xd1000000 - 0xd100ffff (0x10000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xd1010000 - 0xd101ffff (0x10000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[23] 0	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[27] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[28] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[29] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[30] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[31] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[33] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[34] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[35] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[36] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[37] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[38] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[39] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[40] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[41] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[42] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[43] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[44] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[45] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[46] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[47] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[48] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[49] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[50] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[51] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
[COLOR="Red"](WW) fglrx(0): * DRI initialization failed!                  *[/COLOR]
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x10000000
(==) fglrx(0): Write-combining range (0xc0000000,0x10000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1920,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1080) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1920 x 7111
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support use Option "TexturedVideo".
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Silken mouse enabled
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
(EE) AIGLX: Screen 0 is not DRI capable
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
(**) Option "XkbLayout" "es"
(**) Generic Keyboard: XkbLayout: "es"
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
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
```

In that file,I can see the message:  DRI initialization failed! 
I think the problem is there....

On the other hand, sometimes when I swich on the computer I can view the login screen, and I have to enter by console!!

Can any one help me?

thanks.-

---

### Post by dannns on 2007-11-12
My xorg.conf is a mess, and I don know what's happening with some of the instructions, however I posting it for your reference since it is working with an ATI card, its the HD series though HD2600XT. I noticed that mine doesn load any dri module, and that yours doesn have Option "AIGLX" "True" in ServerLayout.

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"alt-intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	Busid		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"L91A"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"L91A"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"

		Option "AIGLX" "True"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```
My fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 XT
OpenGL version string: 1.4 (2.0.6958 Release)

```

---

### Post by kellemes on 2007-11-13
Ok.. well, lets try a few things.. first backup your xorg.conf so you can experiment with a copy..

I'm not sure if you're fglrx-driver supports AIGLX yet?
I assume for now... in this case you can ```
sudo apt-get remove xserver-xgl
```
Also you should add the following section..
```
Section "ServerFlags"
    Option        "AIGLX" "true"
EndSection
```

Do you have the following section?
```
Section "DRI"
    Mode         0666
EndSection
```

Add..
```
Option  "XAANoOffscreenPixmaps" "true"
```
to the device-section..

---

### Post by minijai on 2007-11-13
Here is a copy of my xorg.conf.
I put the news parameter without any result:

```
 fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: [COLOR="Red"]Mesa GLX Indirect[/COLOR]
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```

xorg.conf:

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	# path to defoma fonts
	Fontpath	"/usr/share/X11/fonts/misc"
	Fontpath	"/usr/share/X11/fonts/cyrillic"
	Fontpath	"/usr/share/X11/fonts/100dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/75dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/Type1"
	Fontpath	"/usr/share/X11/fonts/100dpi"
	Fontpath	"/usr/share/X11/fonts/75dpi"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"RadeonX1300"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
[COLOR="Red"]	Option		"XAANoOffscreenPixmaps" "true"[/COLOR]
EndSection

Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"RadeonX1300"
	Monitor		"Monitor genérico"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

[COLOR="Red"]Section "DRI"
	Mode 0666
EndSection[/COLOR]

[COLOR="Red"]Section "Extensions"
	Option "Composite" "true"
EndSection[/COLOR]

[COLOR="Red"]Section "ServerFlags"
	Option	"AIGLX"	"true"
EndSection[/COLOR]
```

Any idea?
thanks,

---

### Post by dannns on 2007-11-14
Actually Option "AIGLX" "true" should go under server layout
```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	[COLOR="Red"]Option        "AIGLX" "true"[/COLOR]

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

---

### Post by minijai on 2007-11-15
I've put the option  "AIGLX" "true"  under server layout, but I haven't any result.
I have this output for the [COLOR="Red"]fglrxinfo[/COLOR] command:

```
display: :0.0  screen: 0
OpenGL vendor string: [COLOR="Red"]Mesa project: www.mesa3d.org[/COLOR]
OpenGL renderer string: [COLOR="Red"]Mesa GLX Indirect[/COLOR]
OpenGL version string: [COLOR="Red"]1.4 (2.1 Mesa 7.0.1)
```[/COLOR]

Could you write the output for the command: [COLOR="Red"]lsmod[/COLOR]
so I can compare with mine, to see if there is some module that I haven't load.

```
Section "Module"
	Load		"i2c"  
	Load		[COLOR="Red"]"bitmap"[/COLOR]
	Load		[COLOR="Red"]"ddc"[/COLOR]
	Load		[COLOR="Red"]"dri"[/COLOR]
	Load		[COLOR="Red"]"extmod"[/COLOR]
	Load		[COLOR="Red"]"freetype"[/COLOR]
	Load		[COLOR="Red"]"glx"[/COLOR]
	Load		[COLOR="Red"]"int10"[/COLOR]
	Load		[COLOR="Red"]"type1"[/COLOR]
	Load		[COLOR="Red"]"vbe"[/COLOR]
EndSection
```
the above red lines are modules that I don't find with the command: lsmod |grep xxxx
where 'xxxx' is the name of the module!!

```
[COLOR="Blue"]Module                  Size  Used by[/COLOR]
ipv6                  317192  10 
af_packet              28172  2 
[COLOR="Red"]fglrx                1737948  0 [/COLOR]
binfmt_misc            14860  1 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
ppdev                  11272  0 
cpufreq_userspace       6048  0 
cpufreq_stats           8160  0 
cpufreq_powersave       3072  0 
cpufreq_ondemand       10896  0 
freq_table              6464  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     9608  0 
video                  21140  0 
sbs                    21520  0 
button                 10400  0 
dock                   12264  0 
container               6400  0 
ac                      7304  0 
battery                12424  0 
nls_iso8859_1           6528  2 
nls_cp437               8192  2 
vfat                   16128  2 
fat                    60208  1 vfat
sbp2                   27144  0 
lp                     15048  0 
snd_usb_audio          96640  0 
snd_usb_lib            20352  1 snd_usb_audio
snd_hwdep              12168  1 snd_usb_audio
snd_mpu401             11944  0 
snd_mpu401_uart        11008  1 snd_mpu401
snd_intel8x0           40104  1 
snd_ac97_codec        122200  1 snd_intel8x0
ac97_bus                4096  1 snd_ac97_codec
snd_pcm_oss            50048  0 
snd_pcm                94344  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          20096  1 snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
gspca                 617808  0 
snd_seq_midi           11008  0 
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
videodev               31360  1 gspca
v4l2_common            21888  1 videodev
v4l1_compat            15364  1 videodev
snd_rawmidi            29824  3 snd_usb_lib,snd_mpu401_uart,snd_seq_midi
parport_pc             41896  1 
parport                44172  3 ppdev,lp,parport_pc
analog                 13408  0 
k8temp                  7680  0 
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    69288  16 snd_usb_audio,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
pcspkr                  4608  0 
gameport               18704  1 analog
soundcore              10272  1 snd
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
snd_page_alloc         12560  2 snd_intel8x0,snd_pcm
psmouse                45596  0 
serio_raw               9092  0 
i2c_nforce2             7808  0 
i2c_core               30208  1 i2c_nforce2
evdev                  13056  3 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sg                     41384  0 
sd_mod                 32512  7 
ide_cd                 35488  0 
cdrom                  41768  1 ide_cd
sata_nv                24068  5 
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
sata_sil               14600  0 
skge                   47248  0 
floppy                 69608  0 
forcedeth              55048  0 
ata_generic             9988  0 
libata                138928  3 sata_nv,sata_sil,ata_generic
scsi_mod              172856  4 sbp2,sg,sd_mod,libata
amd74xx                17328  0 [permanent]
ide_core              141200  2 ide_cd,amd74xx
ehci_hcd               40076  0 
ohci_hcd               25092  0 
usbcore               161584  6 snd_usb_audio,snd_usb_lib,gspca,ehci_hcd,ohci_hcd
thermal                16528  0 
processor              36232  1 thermal
fan                     6920  0 
fuse                   52528  3 
apparmor               47008  0 
commoncap               9472  1 apparmor

```

By the way, when I introduce my user and password into the login screen I can view a high resolution in my monitor. However, when I confirm then password and enter to the system the resolution change and It's lower. 

Any idea??

Thanks.!!:confused:

---

### Post by dannns on 2007-11-15
lsmod:
```
Module                  Size  Used by
isofs                  39268  0 
udf                    90024  0 
af_packet              28172  2 
vmnet                  45344  15 
vmmon                 150124  7 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
vboxdrv              1649696  0 
ppdev                  11272  0 
ipv6                  317192  12 
powernow_k8            16608  1 
cpufreq_conservative     9608  0 
cpufreq_powersave       3072  0 
cpufreq_userspace       6048  0 
cpufreq_ondemand       10896  1 
cpufreq_stats           8160  0 
freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
dock                   12264  0 
sbs                    21520  0 
button                 10400  0 
ac                      7304  0 
container               6400  0 
video                  21140  0 
battery                12424  0 
sbp2                   27144  0 
lp                     15048  0 
snd_ca0106             41248  1 
snd_ac97_codec        122712  1 snd_ca0106
snd_pcm_oss            50816  0 
snd_mixer_oss          20352  1 snd_pcm_oss
snd_pcm                95112  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_oss            39040  0 
snd_seq_midi           11264  0 
snd_rawmidi            30336  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event     10240  2 snd_seq_oss,snd_seq_midi
snd_seq                63648  5 snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27656  2 snd_pcm,snd_seq
snd_seq_device         10772  4 snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71464  12 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                1737948  24 
soundcore              10272  1 snd
pcspkr                  4608  0 
ac97_bus                4352  1 snd_ac97_codec
serio_raw               9092  0 
shpchp                 38300  0 
parport_pc             41896  1 
parport                44172  3 ppdev,lp,parport_pc
snd_page_alloc         12944  2 snd_ca0106,snd_pcm
psmouse                45596  0 
k8temp                  7680  0 
pci_hotplug            36612  1 shpchp
i2c_nforce2             7808  0 
i2c_core               30208  1 i2c_nforce2
evdev                  13056  3 
ext3                  146576  2 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
dm_mirror              25472  0 
dm_mod                 67440  1 dm_mirror
sg                     41384  0 
ide_cd                 35488  0 
cdrom                  41768  1 ide_cd
ide_disk               20352  4 
sd_mod                 32512  0 
usbhid                 32576  0 
hid                    33408  1 usbhid
amd74xx                17328  0 [permanent]
ide_core              141200  3 ide_cd,ide_disk,amd74xx
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
sata_nv                24068  0 
floppy                 69608  0 
ohci_hcd               25092  0 
forcedeth              55048  0 
ata_generic             9988  0 
ehci_hcd               40076  0 
usbcore               161584  4 usbhid,ohci_hcd,ehci_hcd
libata                138928  2 sata_nv,ata_generic
scsi_mod              172856  4 sbp2,sg,sd_mod,libata
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor

```

How About changing the modules section to just this: (I don't load dri)
```
Section "Module"
	Load		"glx"
EndSection
```

---

