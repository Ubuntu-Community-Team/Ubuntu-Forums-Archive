---
title: "Interesting Desktop Effect problem"
date: 2008-04-26
forum: General Help
---

### Post by auruspex on 2008-04-26
Hello there. I recent reformatted and reinstalled Ubuntu Hardy on my machine and all worked great. I recently however decided to disable my desktop effects and found out I missed them so I went to re-enable and the screen flickers, then flashes a message saying "Desktop Effect could not be enabled." This confused me as they were enabled.

Output of command: "compiz"

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0193 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3200x1200) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

The odd thing to me here is that it seems to go without any errors but obviously I get no effects. I have a nVidia 8800 GTS video card and I recently reinstalled the drivers as a attempt to troubleshoot my issue. Also, as a reminder, the effects were working quite fine before I disabled them.

Thanks for any help you guys can provide. :)

---

### Post by Zorael on 2008-04-26
Have you tried adding the --replace argument? I'm not sure if it makes a difference.
```
$ compiz --replace &
```

---

### Post by auruspex on 2008-04-26
> **Zorael said:**
> Have you tried adding the --replace argument? I'm not sure if it makes a difference.
```
$ compiz --replace &
```

Yeah.. I tried that. Same output.

---

### Post by auruspex on 2008-04-26
Here's my xorg.conf

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option 		"Emulate3Buttons" "no"
#	Option          "Buttons"       "7"
#	Option 		"ButtonMapping" "1 2 3 4 5 6 7"
#	Option 		"ZAxisMapping" 	"4 5"
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
	Identifier	"nVidia Corporation G80 [GeForce 8800 GTS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Generic Monitor"
	Option		"RenderAccel"
	Option 		"TwinView"
	Option          "SecondMonitorHorizSync" "28-80"
        Option          "SecondMonitorVertRefresh" "43-60" 
	Option		"TwinViewOrientation"	"LeftOf"
	Option 		"MetaModes" "1600x1200 1600x1200"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

---

### Post by auruspex on 2008-04-26
Here's my Xorg log.. I don't see anything of interest:

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
Current Operating System: Linux god 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 26 11:57:29 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation G80 [GeForce 8800 GTS]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(==) Automatically adding devices
(==) Automatically enabling devices
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
(**) Extension "Composite" is enabled
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
(II) PCI: 00:00:0: chip 10de,03a3 card 0000,0000 rev a2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,03ac card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,03aa card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,03a9 card 0000,0000 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:00:4: chip 10de,03ab card 0000,0000 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,03a8 card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,03b5 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,03b4 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,03ad card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:1: chip 10de,03ae card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:2: chip 10de,03af card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:3: chip 10de,03b0 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:4: chip 10de,03b1 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:5: chip 10de,03b2 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:6: chip 10de,03b3 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,03b6 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:02:1: chip 10de,03bc card 0000,0000 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:02:2: chip 10de,03ba card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:03:0: chip 10de,03b7 card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 10de,03b8 card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 10de,03b9 card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 10de,03bb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0270 card 1043,81bc rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0260 card 1043,81bc rev a3 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 1043,81bc rev a3 class 0c,05,00 hdr 80
(II) PCI: 00:0a:2: chip 10de,0272 card 1043,81bc rev a3 class 05,00,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 1043,81bc rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 1043,81bc rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card f043,81bc rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 1043,81bc rev a1 class 01,01,85 hdr 00
(II) PCI: 00:0f:0: chip 10de,0267 card 1043,81bc rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:14:0: chip 10de,0269 card 1043,8221 rev a3 class 06,80,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0193 card 10de,0421 rev a2 class 03,00,00 hdr 00
(II) PCI: 04:00:0: chip 197b,2360 card 1043,8208 rev 02 class 01,06,01 hdr 00
(II) PCI: 05:06:0: chip 1317,0985 card 1317,0570 rev 11 class 02,00,00 hdr 00
(II) PCI: 05:07:0: chip 13f6,8788 card 1a58,0910 rev 00 class 04,01,00 hdr 00
(II) PCI: 05:08:0: chip 1106,3044 card 1043,81fe rev c0 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:3:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:5:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:6:0), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:7:0), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfd800000 - 0xfd8fffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xfdf00000 - 0xfdffffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:16:0), (0,5,5), BCTRL: 0x0200 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xfd900000 - 0xfd9fffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation G80 [GeForce 8800 GTS] rev 162, Mem @ 0xfa000000/24, 0xe0000000/28, 0xf8000000/25, I/O @ 0xcf00/7, BIOS @ 0xfbfe0000/17
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
	[0] -1	0	0xfdafe000 - 0xfdafe7ff (0x800) MX[B]
	[1] -1	0	0xfdaff000 - 0xfdaff3ff (0x400) MX[B]
	[2] -1	0	0xfd8fe000 - 0xfd8fffff (0x2000) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[4] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[8] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[9] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000bf00 - 0x0000bf7f (0x80) IX[B]
	[13] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[14] -1	0	0x0000ba00 - 0x0000baff (0x100) IX[B]
	[15] -1	0	0x0000db00 - 0x0000db0f (0x10) IX[B]
	[16] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[17] -1	0	0x0000dd00 - 0x0000dd07 (0x8) IX[B]
	[18] -1	0	0x0000de00 - 0x0000de03 (0x4) IX[B]
	[19] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[20] -1	0	0x0000f200 - 0x0000f207 (0x8) IX[B]
	[21] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[22] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[23] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[24] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[25] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[26] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000fd00 - 0x0000fd0f (0x10) IX[B]
	[32] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[33] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[34] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdafe000 - 0xfdafe7ff (0x800) MX[B]
	[1] -1	0	0xfdaff000 - 0xfdaff3ff (0x400) MX[B]
	[2] -1	0	0xfd8fe000 - 0xfd8fffff (0x2000) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[4] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[8] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[9] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000bf00 - 0x0000bf7f (0x80) IX[B]
	[13] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[14] -1	0	0x0000ba00 - 0x0000baff (0x100) IX[B]
	[15] -1	0	0x0000db00 - 0x0000db0f (0x10) IX[B]
	[16] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[17] -1	0	0x0000dd00 - 0x0000dd07 (0x8) IX[B]
	[18] -1	0	0x0000de00 - 0x0000de03 (0x4) IX[B]
	[19] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[20] -1	0	0x0000f200 - 0x0000f207 (0x8) IX[B]
	[21] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[22] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[23] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[24] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[25] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[26] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000fd00 - 0x0000fd0f (0x10) IX[B]
	[32] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[33] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[34] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B](B)
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
	[4] -1	0	0xfdafe000 - 0xfdafe7ff (0x800) MX[B]
	[5] -1	0	0xfdaff000 - 0xfdaff3ff (0x400) MX[B]
	[6] -1	0	0xfd8fe000 - 0xfd8fffff (0x2000) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000bf00 - 0x0000bf7f (0x80) IX[B]
	[19] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[20] -1	0	0x0000ba00 - 0x0000baff (0x100) IX[B]
	[21] -1	0	0x0000db00 - 0x0000db0f (0x10) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[23] -1	0	0x0000dd00 - 0x0000dd07 (0x8) IX[B]
	[24] -1	0	0x0000de00 - 0x0000de03 (0x4) IX[B]
	[25] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[26] -1	0	0x0000f200 - 0x0000f207 (0x8) IX[B]
	[27] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[28] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[29] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[30] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[31] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[32] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[33] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[34] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[35] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[36] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[37] -1	0	0x0000fd00 - 0x0000fd0f (0x10) IX[B]
	[38] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[39] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[40] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) NVIDIA dlloader X Driver  169.12  Thu Feb 14 17:55:38 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdafe000 - 0xfdafe7ff (0x800) MX[B]
	[5] -1	0	0xfdaff000 - 0xfdaff3ff (0x400) MX[B]
	[6] -1	0	0xfd8fe000 - 0xfd8fffff (0x2000) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000bf00 - 0x0000bf7f (0x80) IX[B]
	[19] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[20] -1	0	0x0000ba00 - 0x0000baff (0x100) IX[B]
	[21] -1	0	0x0000db00 - 0x0000db0f (0x10) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[23] -1	0	0x0000dd00 - 0x0000dd07 (0x8) IX[B]
	[24] -1	0	0x0000de00 - 0x0000de03 (0x4) IX[B]
	[25] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[26] -1	0	0x0000f200 - 0x0000f207 (0x8) IX[B]
	[27] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[28] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[29] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[30] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[31] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[32] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[33] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[34] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[35] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[36] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[37] -1	0	0x0000fd00 - 0x0000fd0f (0x10) IX[B]
	[38] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[39] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[40] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdafe000 - 0xfdafe7ff (0x800) MX[B]
	[5] -1	0	0xfdaff000 - 0xfdaff3ff (0x400) MX[B]
	[6] -1	0	0xfd8fe000 - 0xfd8fffff (0x2000) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000bf00 - 0x0000bf7f (0x80) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[23] -1	0	0x0000ba00 - 0x0000baff (0x100) IX[B]
	[24] -1	0	0x0000db00 - 0x0000db0f (0x10) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[26] -1	0	0x0000dd00 - 0x0000dd07 (0x8) IX[B]
	[27] -1	0	0x0000de00 - 0x0000de03 (0x4) IX[B]
	[28] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[29] -1	0	0x0000f200 - 0x0000f207 (0x8) IX[B]
	[30] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[31] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[32] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[33] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[34] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[35] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[36] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[37] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[38] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[39] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[40] -1	0	0x0000fd00 - 0x0000fd0f (0x10) IX[B]
	[41] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[42] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[43] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B](B)
	[44] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[45] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "RenderAccel"
(**) NVIDIA(0): Option "TwinView"
(**) NVIDIA(0): Option "TwinViewOrientation" "LeftOf"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "28-80"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "43-60"
(**) NVIDIA(0): Option "MetaModes" "1600x1200 1600x1200"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8800 GTS (G80) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 655360 kBytes
(--) NVIDIA(0): VideoBIOS: 60.80.13.00.02
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8800 GTS at PCI:1:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(0):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
(WW) NVIDIA(0): No valid modes for "1600x12001600x1200"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 3200 x 1200
(--) NVIDIA(0): DPI set to (99, 98); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdafe000 - 0xfdafe7ff (0x800) MX[B]
	[5] -1	0	0xfdaff000 - 0xfdaff3ff (0x400) MX[B]
	[6] -1	0	0xfd8fe000 - 0xfd8fffff (0x2000) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000bf00 - 0x0000bf7f (0x80) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[23] -1	0	0x0000ba00 - 0x0000baff (0x100) IX[B]
	[24] -1	0	0x0000db00 - 0x0000db0f (0x10) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[26] -1	0	0x0000dd00 - 0x0000dd07 (0x8) IX[B]
	[27] -1	0	0x0000de00 - 0x0000de03 (0x4) IX[B]
	[28] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[29] -1	0	0x0000f200 - 0x0000f207 (0x8) IX[B]
	[30] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[31] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[32] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[33] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[34] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[35] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[36] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[37] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[38] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[39] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[40] -1	0	0x0000fd00 - 0x0000fd0f (0x10) IX[B]
	[41] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[42] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[43] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B](B)
	[44] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[45] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Setting vga for screen 0.
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
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "no"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetClientVersion: 0 9

```

Also, glxinfo | grep direct prints:

```

direct rendering: Yes

```

---

### Post by auruspex on 2008-04-26
Tried the following:

Removed nvidia drivers, reinstalled.
Removed compiz, reinstalled.

---

### Post by auruspex on 2008-04-26
Problem Solved!

Ran the following command to disable metacity composite effects:

gconftool-2 -s  --type bool  /apps/metacity/general/compositing_manager  false

And it worked. :)

---

