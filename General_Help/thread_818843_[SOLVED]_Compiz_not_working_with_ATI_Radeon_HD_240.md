---
title: "[SOLVED] Compiz not working with ATI Radeon HD 2400 Pro"
date: 2008-06-04
forum: General Help
---

### Post by josh8 on 2008-06-04
I've been trying to get compiz to work on Hardy Heron for the past few days with little success. I've installed xserver-xgl and that didn't work. In Hardware drivers there are no proprietary drivers listed. I really don't know what to do (I'm completely new to linux), so any help would be much appreciated.
Hopefully this is all the information that you'll need.

compiz-check
```
 Distribution:          Ubuntu 8.04

 Desktop environment:   GNOME

 Graphics chip:         ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]

 Driver in use:         vesa

 Rendering method:      AIGLX



Checking if it's possible to run Compiz on your system...  [SKIP]



 Checking for hardware/setup problems...           [FAIL]



There has been (at least) one error detected with your setup:

 Error: Detected driver is not on Compiz' whitelist. 
```

compiz
```
Checking for Xgl: not present. 

No whitelisted driver found

aborting and using fallback: /usr/bin/metacity
```

/etc/X11/xorg.conf
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

	Identifier	"ATI Technologies Inc ATI Default Card" 

	Driver		"vesa"

	BusID		"PCI:1:0:0"

EndSection



Section "Monitor"

	Identifier	"Acer AL1916W"

	Option		"DPMS"

EndSection



Section "Screen"

	Identifier	"Default Screen"

	Device		"ATI Technologies Inc ATI Default Card"

	Monitor		"Acer AL1916W"

	DefaultDepth	24

	SubSection "Display"

		Modes		"1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"

	EndSubSection

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

```

/var/log/Xorg.0.log

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

Current Operating System: Linux shane-computer 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686

Build Date: 15 April 2008  05:26:17PM

 

	Before reporting problems, check http://wiki.x.org

	to make sure that you have the latest version.

Module Loader present

Markers: (--) probed, (**) from config file, (==) default setting,

	(++) from command line, (!!) notice, (II) informational,

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun  4 17:30:35 2008

(==) Using config file: "/etc/X11/xorg.conf"

(==) ServerLayout "Default Layout"

(**) |-->Screen "Default Screen" (0)

(**) |   |-->Monitor "Acer AL1916W"

(**) |   |-->Device "ATI Technologies Inc ATI Default Card"

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

(II) PCI: 00:00:0: chip 8086,29c0 card 1028,020d rev 02 class 06,00,00 hdr 00

(II) PCI: 00:01:0: chip 8086,29c1 card 0000,0000 rev 02 class 06,04,00 hdr 01

(II) PCI: 00:19:0: chip 8086,10c0 card 1028,020d rev 02 class 02,00,00 hdr 00

(II) PCI: 00:1a:0: chip 8086,2937 card 1028,020d rev 02 class 0c,03,00 hdr 80

(II) PCI: 00:1a:1: chip 8086,2938 card 1028,020d rev 02 class 0c,03,00 hdr 00

(II) PCI: 00:1a:2: chip 8086,2939 card 1028,020d rev 02 class 0c,03,00 hdr 00

(II) PCI: 00:1a:7: chip 8086,293c card 1028,020d rev 02 class 0c,03,20 hdr 00

(II) PCI: 00:1b:0: chip 8086,293e card 1028,020d rev 02 class 04,03,00 hdr 00

(II) PCI: 00:1d:0: chip 8086,2934 card 1028,020d rev 02 class 0c,03,00 hdr 80

(II) PCI: 00:1d:1: chip 8086,2935 card 1028,020d rev 02 class 0c,03,00 hdr 00

(II) PCI: 00:1d:2: chip 8086,2936 card 1028,020d rev 02 class 0c,03,00 hdr 00

(II) PCI: 00:1d:7: chip 8086,293a card 1028,020d rev 02 class 0c,03,20 hdr 00

(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 92 class 06,04,01 hdr 01

(II) PCI: 00:1f:0: chip 8086,2916 card 1028,020d rev 02 class 06,01,00 hdr 80

(II) PCI: 00:1f:2: chip 8086,2920 card 1028,020d rev 02 class 01,01,8f hdr 00

(II) PCI: 00:1f:3: chip 8086,2930 card 1028,020d rev 02 class 0c,05,00 hdr 00

(II) PCI: 00:1f:5: chip 8086,2926 card 1028,020d rev 02 class 01,01,85 hdr 00

(II) PCI: 01:00:0: chip 1002,94c3 card 1028,0402 rev 00 class 03,00,00 hdr 00

(II) PCI: 02:00:0: chip 14f1,2f20 card 14f1,200f rev 00 class 07,80,00 hdr 00

(II) PCI: End of PCI scan

(II) Intel Bridge workaround enabled

(II) Host-to-PCI bridge:

(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)

(II) Bus 0 I/O range:

	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]

(II) Bus 0 non-prefetchable memory range:

	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]

(II) Bus 0 prefetchable memory range:

	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]

(II) PCI-to-PCI bridge:

(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)

(II) Bus 1 I/O range:

	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]

(II) Bus 1 non-prefetchable memory range:

	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]

(II) Bus 1 prefetchable memory range:

	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]

(II) Subtractive PCI-to-PCI bridge:

(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)

(II) Bus 2 I/O range:

	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]

(II) Bus 2 non-prefetchable memory range:

	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]

(II) Bus 2 prefetchable memory range:

	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]

(II) PCI-to-ISA bridge:

(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)

(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x94c3) rev 0, Mem @ 0xd0000000/28, 0xfddf0000/16, I/O @ 0xce00/8

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

	[0] -1	0	0xfdcf0000 - 0xfdcfffff (0x10000) MX[B]

	[1] -1	0	0xfdffc000 - 0xfdffc0ff (0x100) MX[B]

	[2] -1	0	0xfdffd000 - 0xfdffd3ff (0x400) MX[B]

	[3] -1	0	0xfdff4000 - 0xfdff7fff (0x4000) MX[B]

	[4] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]

	[5] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]

	[6] -1	0	0xfdfc0000 - 0xfdfdffff (0x20000) MX[B]

	[7] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)

	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)

	[9] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]

	[10] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]

	[11] -1	0	0x0000ed00 - 0x0000ed0f (0x10) IX[B]

	[12] -1	0	0x0000ee00 - 0x0000ee03 (0x4) IX[B]

	[13] -1	0	0x0000ef00 - 0x0000ef07 (0x8) IX[B]

	[14] -1	0	0x0000f000 - 0x0000f003 (0x4) IX[B]

	[15] -1	0	0x0000f100 - 0x0000f107 (0x8) IX[B]

	[16] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]

	[17] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]

	[18] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]

	[19] -1	0	0x0000f500 - 0x0000f503 (0x4) IX[B]

	[20] -1	0	0x0000f600 - 0x0000f607 (0x8) IX[B]

	[21] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]

	[22] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]

	[23] -1	0	0x0000f900 - 0x0000f91f (0x20) IX[B]

	[24] -1	0	0x0000fa00 - 0x0000fa1f (0x20) IX[B]

	[25] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]

	[26] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]

	[27] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]

	[28] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]

	[29] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]

	[30] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B](B)

(II) Active PCI resource ranges after removing overlaps:

	[0] -1	0	0xfdcf0000 - 0xfdcfffff (0x10000) MX[B]

	[1] -1	0	0xfdffc000 - 0xfdffc0ff (0x100) MX[B]

	[2] -1	0	0xfdffd000 - 0xfdffd3ff (0x400) MX[B]

	[3] -1	0	0xfdff4000 - 0xfdff7fff (0x4000) MX[B]

	[4] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]

	[5] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]

	[6] -1	0	0xfdfc0000 - 0xfdfdffff (0x20000) MX[B]

	[7] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)

	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)

	[9] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]

	[10] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]

	[11] -1	0	0x0000ed00 - 0x0000ed0f (0x10) IX[B]

	[12] -1	0	0x0000ee00 - 0x0000ee03 (0x4) IX[B]

	[13] -1	0	0x0000ef00 - 0x0000ef07 (0x8) IX[B]

	[14] -1	0	0x0000f000 - 0x0000f003 (0x4) IX[B]

	[15] -1	0	0x0000f100 - 0x0000f107 (0x8) IX[B]

	[16] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]

	[17] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]

	[18] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]

	[19] -1	0	0x0000f500 - 0x0000f503 (0x4) IX[B]

	[20] -1	0	0x0000f600 - 0x0000f607 (0x8) IX[B]

	[21] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]

	[22] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]

	[23] -1	0	0x0000f900 - 0x0000f91f (0x20) IX[B]

	[24] -1	0	0x0000fa00 - 0x0000fa1f (0x20) IX[B]

	[25] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]

	[26] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]

	[27] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]

	[28] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]

	[29] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]

	[30] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B](B)

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

	[4] -1	0	0xfdcf0000 - 0xfdcfffff (0x10000) MX[B]

	[5] -1	0	0xfdffc000 - 0xfdffc0ff (0x100) MX[B]

	[6] -1	0	0xfdffd000 - 0xfdffd3ff (0x400) MX[B]

	[7] -1	0	0xfdff4000 - 0xfdff7fff (0x4000) MX[B]

	[8] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]

	[9] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]

	[10] -1	0	0xfdfc0000 - 0xfdfdffff (0x20000) MX[B]

	[11] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)

	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)

	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]

	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]

	[15] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]

	[16] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]

	[17] -1	0	0x0000ed00 - 0x0000ed0f (0x10) IX[B]

	[18] -1	0	0x0000ee00 - 0x0000ee03 (0x4) IX[B]

	[19] -1	0	0x0000ef00 - 0x0000ef07 (0x8) IX[B]

	[20] -1	0	0x0000f000 - 0x0000f003 (0x4) IX[B]

	[21] -1	0	0x0000f100 - 0x0000f107 (0x8) IX[B]

	[22] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]

	[23] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]

	[24] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]

	[25] -1	0	0x0000f500 - 0x0000f503 (0x4) IX[B]

	[26] -1	0	0x0000f600 - 0x0000f607 (0x8) IX[B]

	[27] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]

	[28] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]

	[29] -1	0	0x0000f900 - 0x0000f91f (0x20) IX[B]

	[30] -1	0	0x0000fa00 - 0x0000fa1f (0x20) IX[B]

	[31] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]

	[32] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]

	[33] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]

	[34] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]

	[35] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]

	[36] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B](B)

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

(II) LoadModule: "vesa"

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so

(II) Module vesa: vendor="X.Org Foundation"

	compiled for 1.4.0.90, module version = 1.3.0

	Module class: X.Org Video Driver

	ABI class: X.Org Video Driver, version 2.0

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

(II) VESA: driver for VESA chipsets: vesa

(II) Primary Device is: PCI 01:00:0

(--) Chipset vesa found

(II) resource ranges after xf86ClaimFixedResources() call:

	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)

	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]

	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]

	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]

	[4] -1	0	0xfdcf0000 - 0xfdcfffff (0x10000) MX[B]

	[5] -1	0	0xfdffc000 - 0xfdffc0ff (0x100) MX[B]

	[6] -1	0	0xfdffd000 - 0xfdffd3ff (0x400) MX[B]

	[7] -1	0	0xfdff4000 - 0xfdff7fff (0x4000) MX[B]

	[8] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]

	[9] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]

	[10] -1	0	0xfdfc0000 - 0xfdfdffff (0x20000) MX[B]

	[11] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)

	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)

	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]

	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]

	[15] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]

	[16] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]

	[17] -1	0	0x0000ed00 - 0x0000ed0f (0x10) IX[B]

	[18] -1	0	0x0000ee00 - 0x0000ee03 (0x4) IX[B]

	[19] -1	0	0x0000ef00 - 0x0000ef07 (0x8) IX[B]

	[20] -1	0	0x0000f000 - 0x0000f003 (0x4) IX[B]

	[21] -1	0	0x0000f100 - 0x0000f107 (0x8) IX[B]

	[22] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]

	[23] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]

	[24] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]

	[25] -1	0	0x0000f500 - 0x0000f503 (0x4) IX[B]

	[26] -1	0	0x0000f600 - 0x0000f607 (0x8) IX[B]

	[27] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]

	[28] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]

	[29] -1	0	0x0000f900 - 0x0000f91f (0x20) IX[B]

	[30] -1	0	0x0000fa00 - 0x0000fa1f (0x20) IX[B]

	[31] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]

	[32] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]

	[33] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]

	[34] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]

	[35] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]

	[36] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B](B)

(II) resource ranges after probing:

	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)

	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]

	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]

	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]

	[4] -1	0	0xfdcf0000 - 0xfdcfffff (0x10000) MX[B]

	[5] -1	0	0xfdffc000 - 0xfdffc0ff (0x100) MX[B]

	[6] -1	0	0xfdffd000 - 0xfdffd3ff (0x400) MX[B]

	[7] -1	0	0xfdff4000 - 0xfdff7fff (0x4000) MX[B]

	[8] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]

	[9] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]

	[10] -1	0	0xfdfc0000 - 0xfdfdffff (0x20000) MX[B]

	[11] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)

	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)

	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]

	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]

	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]

	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]

	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]

	[18] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]

	[19] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]

	[20] -1	0	0x0000ed00 - 0x0000ed0f (0x10) IX[B]

	[21] -1	0	0x0000ee00 - 0x0000ee03 (0x4) IX[B]

	[22] -1	0	0x0000ef00 - 0x0000ef07 (0x8) IX[B]

	[23] -1	0	0x0000f000 - 0x0000f003 (0x4) IX[B]

	[24] -1	0	0x0000f100 - 0x0000f107 (0x8) IX[B]

	[25] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]

	[26] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]

	[27] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]

	[28] -1	0	0x0000f500 - 0x0000f503 (0x4) IX[B]

	[29] -1	0	0x0000f600 - 0x0000f607 (0x8) IX[B]

	[30] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]

	[31] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]

	[32] -1	0	0x0000f900 - 0x0000f91f (0x20) IX[B]

	[33] -1	0	0x0000fa00 - 0x0000fa1f (0x20) IX[B]

	[34] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]

	[35] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]

	[36] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]

	[37] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]

	[38] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]

	[39] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B](B)

	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]

	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]

(II) Setting vga for screen 0.

(II) Loading sub module "vbe"

(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so

(II) Module vbe: vendor="X.Org Foundation"

	compiled for 1.4.0.90, module version = 1.1.0

	ABI class: X.Org Video Driver, version 2.0

(II) Loading sub module "int10"

(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so

(II) Module int10: vendor="X.Org Foundation"

	compiled for 1.4.0.90, module version = 1.0.0

	ABI class: X.Org Video Driver, version 2.0

(II) VESA(0): initializing int10

(II) VESA(0): Primary V_BIOS segment is: 0xc000

(II) VESA(0): VESA BIOS detected

(II) VESA(0): VESA VBE Version 3.0

(II) VESA(0): VESA VBE Total Mem: 16384 kB

(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS

(II) VESA(0): VESA VBE OEM Software Rev: 10.65

(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 

(II) VESA(0): VESA VBE OEM Product: RV610

(II) VESA(0): VESA VBE OEM Product Rev: 01.00

(**) VESA(0): Depth 24, (--) framebuffer bpp 32

(==) VESA(0): RGB weight 888

(==) VESA(0): Default visual is TrueColor

(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)

(II) Loading sub module "ddc"

(II) LoadModule: "ddc"(II) Module "ddc" already built-in

(II) VESA(0): VESA VBE DDC supported

(II) VESA(0): VESA VBE DDC Level 2

(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.

(II) VESA(0): VESA VBE DDC read successfully

(II) VESA(0): Manufacturer: ACR  Model: ad76  Serial#: 1935699249

(II) VESA(0): Year: 2007  Week: 36

(II) VESA(0): EDID Version: 1.3

(II) VESA(0): Digital Display Input

(II) VESA(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26

(II) VESA(0): Gamma: 2.20

(II) VESA(0): DPMS capabilities: Off; RGB/Color Display

(II) VESA(0): First detailed timing is preferred mode

(II) VESA(0): redX: 0.643 redY: 0.325   greenX: 0.295 greenY: 0.616

(II) VESA(0): blueX: 0.143 blueY: 0.081   whiteX: 0.310 whiteY: 0.330

(II) VESA(0): Supported VESA Video Modes:

(II) VESA(0): 720x400@70Hz

(II) VESA(0): 640x480@60Hz

(II) VESA(0): 640x480@67Hz

(II) VESA(0): 640x480@72Hz

(II) VESA(0): 640x480@75Hz

(II) VESA(0): 800x600@56Hz

(II) VESA(0): 800x600@60Hz

(II) VESA(0): 800x600@72Hz

(II) VESA(0): 800x600@75Hz

(II) VESA(0): 832x624@75Hz

(II) VESA(0): 1024x768@60Hz

(II) VESA(0): 1024x768@70Hz

(II) VESA(0): 1024x768@75Hz

(II) VESA(0): 1280x1024@75Hz

(II) VESA(0): Manufacturer's mask: 0

(II) VESA(0): Supported Future Video Modes:

(II) VESA(0): #0: hsize: 1024  vsize 768  refresh: 66  vid: 18017

(II) VESA(0): #1: hsize: 1152  vsize 864  refresh: 60  vid: 16497

(II) VESA(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337

(II) VESA(0): #3: hsize: 1280  vsize 960  refresh: 75  vid: 20353

(II) VESA(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897

(II) VESA(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989

(II) VESA(0): Supported additional Video Mode:

(II) VESA(0): clock: 106.5 MHz   Image Size:  408 x 255 mm

(II) VESA(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0

(II) VESA(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0

(II) VESA(0): Ranges: V min: 50  V max: 75 Hz, H min: 30  H max: 80 kHz, PixClock max 140 MHz

(II) VESA(0): Monitor name: Acer AL1916W

(II) VESA(0): Serial No: L76020444134

(II) VESA(0): EDID (in hex):

(II) VESA(0): 	00ffffffffffff00047276ad316d6073

(II) VESA(0): 	2411010380291a782a9bb6a4534b9d24

(II) VESA(0): 	144f54bfef0061467140714f814f8180

(II) VESA(0): 	950f010101019a29a0d0518422305098

(II) VESA(0): 	360098ff1000001c000000fd00324b1e

(II) VESA(0): 	500e000a202020202020000000fc0041

(II) VESA(0): 	63657220414c31393136570a000000ff

(II) VESA(0): 	004c37363032303434343133340a003b

(II) VESA(0): EDID vendor "ACR", prod id 44406

(II) VESA(0): Using EDID range info for horizontal sync

(II) VESA(0): Using EDID range info for vertical refresh

(II) VESA(0): Printing DDC gathered Modelines:

(II) VESA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)

(II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)

(II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)

(II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)

(II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)

(II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)

(II) VESA(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)

(II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)

(II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)

(II) VESA(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)

(II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)

(II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)

(II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)

(II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)

(II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)

(II) VESA(0): Modeline "1024x768"x65.7   70.75  1024 1080 1184 1344  768 771 775 801 -hsync +vsync (52.6 kHz)

(II) VESA(0): Modeline "1152x864"x60.0   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync (53.8 kHz)

(II) VESA(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)

(II) VESA(0): Modeline "1280x960"x74.9  130.00  1280 1368 1504 1728  960 963 967 1005 -hsync +vsync (75.2 kHz)

(II) VESA(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)

(II) VESA(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)

(II) VESA(0): Searching for matching VESA mode(s):

Mode: 100 (640x400)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 640

	XResolution: 640

	YResolution: 400

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 63

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 640

	BnkNumberOfImagePages: 63

	LinNumberOfImagePages: 63

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 101 (640x480)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 640

	XResolution: 640

	YResolution: 480

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 50

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 640

	BnkNumberOfImagePages: 50

	LinNumberOfImagePages: 50

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 103 (800x600)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 832

	XResolution: 800

	YResolution: 600

	XCharSize: 8

	YCharSize: 14

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 31

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 832

	BnkNumberOfImagePages: 31

	LinNumberOfImagePages: 31

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 105 (1024x768)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1024

	XResolution: 1024

	YResolution: 768

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 18

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1024

	BnkNumberOfImagePages: 18

	LinNumberOfImagePages: 18

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 107 (1280x1024)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1280

	XResolution: 1280

	YResolution: 1024

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 11

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1280

	BnkNumberOfImagePages: 11

	LinNumberOfImagePages: 11

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 111 (640x480)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1280

	XResolution: 640

	YResolution: 480

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 24

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1280

	BnkNumberOfImagePages: 24

	LinNumberOfImagePages: 24

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 114 (800x600)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1600

	XResolution: 800

	YResolution: 600

	XCharSize: 8

	YCharSize: 14

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 16

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1600

	BnkNumberOfImagePages: 16

	LinNumberOfImagePages: 16

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 117 (1024x768)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 2048

	XResolution: 1024

	YResolution: 768

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 9

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 2048

	BnkNumberOfImagePages: 9

	LinNumberOfImagePages: 9

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 11a (1280x1024)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 2560

	XResolution: 1280

	YResolution: 1024

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 5

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 2560

	BnkNumberOfImagePages: 5

	LinNumberOfImagePages: 5

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 10e (320x200)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 640

	XResolution: 320

	YResolution: 200

	XCharSize: 8

	YCharSize: 8

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 127

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 640

	BnkNumberOfImagePages: 127

	LinNumberOfImagePages: 127

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

*Mode: 120 (320x200)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1280

	XResolution: 320

	YResolution: 200

	XCharSize: 8

	YCharSize: 8

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 63

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1280

	BnkNumberOfImagePages: 63

	LinNumberOfImagePages: 63

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 193 (320x240)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 320

	XResolution: 320

	YResolution: 240

	XCharSize: 8

	YCharSize: 8

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 127

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 320

	BnkNumberOfImagePages: 127

	LinNumberOfImagePages: 127

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 195 (320x240)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 640

	XResolution: 320

	YResolution: 240

	XCharSize: 8

	YCharSize: 8

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 84

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 640

	BnkNumberOfImagePages: 84

	LinNumberOfImagePages: 84

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

*Mode: 196 (320x240)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1280

	XResolution: 320

	YResolution: 240

	XCharSize: 8

	YCharSize: 8

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 50

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1280

	BnkNumberOfImagePages: 50

	LinNumberOfImagePages: 50

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 1b3 (512x384)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 512

	XResolution: 512

	YResolution: 384

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 63

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 512

	BnkNumberOfImagePages: 63

	LinNumberOfImagePages: 63

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 1b5 (512x384)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1024

	XResolution: 512

	YResolution: 384

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 35

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1024

	BnkNumberOfImagePages: 35

	LinNumberOfImagePages: 35

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

*Mode: 1b6 (512x384)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 2048

	XResolution: 512

	YResolution: 384

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 18

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 2048

	BnkNumberOfImagePages: 18

	LinNumberOfImagePages: 18

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 1c3 (640x350)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 640

	XResolution: 640

	YResolution: 350

	XCharSize: 8

	YCharSize: 14

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 63

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 640

	BnkNumberOfImagePages: 63

	LinNumberOfImagePages: 63

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 1c5 (640x350)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1280

	XResolution: 640

	YResolution: 350

	XCharSize: 8

	YCharSize: 14

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 35

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1280

	BnkNumberOfImagePages: 35

	LinNumberOfImagePages: 35

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

*Mode: 1c6 (640x350)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 2560

	XResolution: 640

	YResolution: 350

	XCharSize: 8

	YCharSize: 14

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 17

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 2560

	BnkNumberOfImagePages: 17

	LinNumberOfImagePages: 17

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 183 (640x400)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 640

	XResolution: 640

	YResolution: 400

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 63

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 640

	BnkNumberOfImagePages: 63

	LinNumberOfImagePages: 63

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 185 (640x400)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1280

	XResolution: 640

	YResolution: 400

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 31

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1280

	BnkNumberOfImagePages: 31

	LinNumberOfImagePages: 31

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

*Mode: 186 (640x400)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 2560

	XResolution: 640

	YResolution: 400

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 15

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 2560

	BnkNumberOfImagePages: 15

	LinNumberOfImagePages: 15

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 133 (720x400)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 768

	XResolution: 720

	YResolution: 400

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 50

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 768

	BnkNumberOfImagePages: 50

	LinNumberOfImagePages: 50

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 135 (720x400)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1472

	XResolution: 720

	YResolution: 400

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 27

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1472

	BnkNumberOfImagePages: 27

	LinNumberOfImagePages: 27

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

*Mode: 136 (720x400)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 2944

	XResolution: 720

	YResolution: 400

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 13

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 2944

	BnkNumberOfImagePages: 13

	LinNumberOfImagePages: 13

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 153 (1152x864)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1152

	XResolution: 1152

	YResolution: 864

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 15

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1152

	BnkNumberOfImagePages: 15

	LinNumberOfImagePages: 15

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 155 (1152x864)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 2304

	XResolution: 1152

	YResolution: 864

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 7

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 2304

	BnkNumberOfImagePages: 7

	LinNumberOfImagePages: 7

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

*Mode: 156 (1152x864)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 4608

	XResolution: 1152

	YResolution: 864

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 3

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 4608

	BnkNumberOfImagePages: 3

	LinNumberOfImagePages: 3

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 163 (1280x1024)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1280

	XResolution: 1280

	YResolution: 1024

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 11

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1280

	BnkNumberOfImagePages: 11

	LinNumberOfImagePages: 11

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 165 (1280x1024)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 2560

	XResolution: 1280

	YResolution: 1024

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 5

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 2560

	BnkNumberOfImagePages: 5

	LinNumberOfImagePages: 5

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

*Mode: 166 (1280x1024)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 5120

	XResolution: 1280

	YResolution: 1024

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 2

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 5120

	BnkNumberOfImagePages: 2

	LinNumberOfImagePages: 2

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

*Mode: 121 (640x480)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 2560

	XResolution: 640

	YResolution: 480

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 12

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0


	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 2560

	BnkNumberOfImagePages: 12

	LinNumberOfImagePages: 12

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

*Mode: 122 (800x600)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 3200

	XResolution: 800

	YResolution: 600

	XCharSize: 8

	YCharSize: 14

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 7

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 3200

	BnkNumberOfImagePages: 7

	LinNumberOfImagePages: 7

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

*Mode: 123 (1024x768)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 4096

	XResolution: 1024

	YResolution: 768

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 4

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 4096

	BnkNumberOfImagePages: 4

	LinNumberOfImagePages: 4

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

*Mode: 124 (1280x1024)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 5120

	XResolution: 1280

	YResolution: 1024

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 2

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 5120

	BnkNumberOfImagePages: 2

	LinNumberOfImagePages: 2

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 143 (1400x1050)

	ModeAttributes: 0xba

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1408

	XResolution: 1400

	YResolution: 1050

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 10

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1408

	BnkNumberOfImagePages: 10

	LinNumberOfImagePages: 10

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 145 (1400x1050)

	ModeAttributes: 0xba

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 2816

	XResolution: 1400

	YResolution: 1050

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 4

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 2816

	BnkNumberOfImagePages: 4

	LinNumberOfImagePages: 4

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 146 (1400x1050)

	ModeAttributes: 0xba

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 5632

	XResolution: 1400

	YResolution: 1050

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 1

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 5632

	BnkNumberOfImagePages: 1

	LinNumberOfImagePages: 1

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 173 (1600x1200)

	ModeAttributes: 0xba

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1600

	XResolution: 1600

	YResolution: 1200

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 7

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1600

	BnkNumberOfImagePages: 7

	LinNumberOfImagePages: 7

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 175 (1600x1200)

	ModeAttributes: 0xba

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 3200

	XResolution: 1600

	YResolution: 1200

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 3

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 3200

	BnkNumberOfImagePages: 3

	LinNumberOfImagePages: 3

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 176 (1600x1200)

	ModeAttributes: 0xba

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 6400

	XResolution: 1600

	YResolution: 1200

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 1

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 6400

	BnkNumberOfImagePages: 1

	LinNumberOfImagePages: 1

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 183 (640x400)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 640

	XResolution: 640

	YResolution: 400

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 63

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 640

	BnkNumberOfImagePages: 63

	LinNumberOfImagePages: 63

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 185 (640x400)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1280

	XResolution: 640

	YResolution: 400

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 31

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1280

	BnkNumberOfImagePages: 31

	LinNumberOfImagePages: 31

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

*Mode: 186 (640x400)

	ModeAttributes: 0xbb

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 2560

	XResolution: 640

	YResolution: 400

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 15

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 2560

	BnkNumberOfImagePages: 15

	LinNumberOfImagePages: 15

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 1d3 (1856x1392)

	ModeAttributes: 0xba

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1856

	XResolution: 1856

	YResolution: 1392

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 5

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1856

	BnkNumberOfImagePages: 5

	LinNumberOfImagePages: 5

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 1d5 (1856x1392)

	ModeAttributes: 0xba

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000


	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 3712

	XResolution: 1856

	YResolution: 1392

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 2

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 3712

	BnkNumberOfImagePages: 2

	LinNumberOfImagePages: 2

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 1d6 (1856x1392)

	ModeAttributes: 0xba

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 7424

	XResolution: 1856

	YResolution: 1392

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 1

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 7424

	BnkNumberOfImagePages: 1

	LinNumberOfImagePages: 1

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 1e3 (1920x1440)

	ModeAttributes: 0xba

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 1920

	XResolution: 1920

	YResolution: 1440

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 8

	NumberOfBanks: 1

	MemoryModel: 4

	BankSize: 0

	NumberOfImages: 4

	RedMaskSize: 0

	RedFieldPosition: 0

	GreenMaskSize: 0

	GreenFieldPosition: 0

	BlueMaskSize: 0

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 1920

	BnkNumberOfImagePages: 4

	LinNumberOfImagePages: 4

	LinRedMaskSize: 0

	LinRedFieldPosition: 0

	LinGreenMaskSize: 0

	LinGreenFieldPosition: 0

	LinBlueMaskSize: 0

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 1e5 (1920x1440)

	ModeAttributes: 0xba

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 3840

	XResolution: 1920

	YResolution: 1440

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 16

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 2

	RedMaskSize: 5

	RedFieldPosition: 11

	GreenMaskSize: 6

	GreenFieldPosition: 5

	BlueMaskSize: 5

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 3840

	BnkNumberOfImagePages: 2

	LinNumberOfImagePages: 2

	LinRedMaskSize: 5

	LinRedFieldPosition: 11

	LinGreenMaskSize: 6

	LinGreenFieldPosition: 5

	LinBlueMaskSize: 5

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000

Mode: 1e6 (1920x1440)

	ModeAttributes: 0xba

	WinAAttributes: 0x7

	WinBAttributes: 0x0

	WinGranularity: 64

	WinSize: 64

	WinASegment: 0xa000

	WinBSegment: 0x0

	WinFuncPtr: 0xc00050cd

	BytesPerScanline: 7680

	XResolution: 1920

	YResolution: 1440

	XCharSize: 8

	YCharSize: 16

	NumberOfPlanes: 1

	BitsPerPixel: 32

	NumberOfBanks: 1

	MemoryModel: 6

	BankSize: 0

	NumberOfImages: 1

	RedMaskSize: 8

	RedFieldPosition: 16

	GreenMaskSize: 8

	GreenFieldPosition: 8

	BlueMaskSize: 8

	BlueFieldPosition: 0

	RsvdMaskSize: 0

	RsvdFieldPosition: 0

	DirectColorModeInfo: 0

	PhysBasePtr: 0xd0000000

	LinBytesPerScanLine: 7680

	BnkNumberOfImagePages: 1

	LinNumberOfImagePages: 1

	LinRedMaskSize: 8

	LinRedFieldPosition: 16

	LinGreenMaskSize: 8

	LinGreenFieldPosition: 8

	LinBlueMaskSize: 8

	LinBlueFieldPosition: 0

	LinRsvdMaskSize: 0

	LinRsvdFieldPosition: 0

	MaxPixelClock: 400000000



(II) VESA(0): Total Memory: 256 64KB banks (16384kB)

(II) VESA(0): Acer AL1916W: Using hsync range of 30.00-80.00 kHz

(II) VESA(0): Acer AL1916W: Using vrefresh range of 50.00-75.00 Hz

(II) VESA(0): Acer AL1916W: Using maximum pixel clock of 140.00 MHz

(II) VESA(0): Not using mode "1440x1440" (no mode of this name)

(II) VESA(0): Not using mode "1440x900" (no mode of this name)

(II) VESA(0): Not using mode "1280x960" (no mode of this name)

(II) VESA(0): Not using mode "832x624" (no mode of this name)

(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)

(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)

(II) VESA(0): Not using built-in mode "640x350" (no mode of this name)

(II) VESA(0): Not using built-in mode "512x384" (no mode of this name)

(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)

(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)

(--) VESA(0): Virtual size is 1280x1024 (pitch 1280)

(**) VESA(0): *Built-in mode "1280x1024"

(**) VESA(0): *Built-in mode "1152x864"

(**) VESA(0): *Built-in mode "1024x768"

(**) VESA(0): *Built-in mode "800x600"

(**) VESA(0): *Built-in mode "720x400"

(**) VESA(0): *Built-in mode "640x480"

(**) VESA(0):  Built-in mode "1280x1024"

(**) VESA(0): Display dimensions: (410, 260) mm

(**) VESA(0): DPI set to (79, 100)

(II) VESA(0): Attempting to use 75Hz refresh for mode "1280x1024" (166)

(II) VESA(0): Attempting to use 75Hz refresh for mode "1152x864" (156)

(II) VESA(0): Attempting to use 75Hz refresh for mode "1024x768" (123)

(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (122)

(II) VESA(0): Attempting to use 70Hz refresh for mode "720x400" (136)

(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (121)

(II) VESA(0): Attempting to use 75Hz refresh for mode "1280x1024" (124)

(**) VESA(0): Using "Shadow Framebuffer"

(II) Loading sub module "shadow"

(II) LoadModule: "shadow"

(II) Loading /usr/lib/xorg/modules//libshadow.so

(II) Module shadow: vendor="X.Org Foundation"

	compiled for 1.4.0.90, module version = 1.1.0

	ABI class: X.Org ANSI C Emulation, version 0.3

(II) Loading sub module "fb"

(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so

(II) Module fb: vendor="X.Org Foundation"

	compiled for 1.4.0.90, module version = 1.0.0

	ABI class: X.Org ANSI C Emulation, version 0.3

(--) Depth 24 pixmap format is 32 bpp

(II) do I need RAC?  No, I don't.

(II) resource ranges after preInit:

	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)

	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]

	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]

	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]

	[4] -1	0	0xfdcf0000 - 0xfdcfffff (0x10000) MX[B]

	[5] -1	0	0xfdffc000 - 0xfdffc0ff (0x100) MX[B]

	[6] -1	0	0xfdffd000 - 0xfdffd3ff (0x400) MX[B]

	[7] -1	0	0xfdff4000 - 0xfdff7fff (0x4000) MX[B]

	[8] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]

	[9] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]

	[10] -1	0	0xfdfc0000 - 0xfdfdffff (0x20000) MX[B]

	[11] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)

	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)

	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]

	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]

	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]

	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]

	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]

	[18] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]

	[19] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]

	[20] -1	0	0x0000ed00 - 0x0000ed0f (0x10) IX[B]

	[21] -1	0	0x0000ee00 - 0x0000ee03 (0x4) IX[B]

	[22] -1	0	0x0000ef00 - 0x0000ef07 (0x8) IX[B]

	[23] -1	0	0x0000f000 - 0x0000f003 (0x4) IX[B]

	[24] -1	0	0x0000f100 - 0x0000f107 (0x8) IX[B]

	[25] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]

	[26] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]

	[27] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]

	[28] -1	0	0x0000f500 - 0x0000f503 (0x4) IX[B]

	[29] -1	0	0x0000f600 - 0x0000f607 (0x8) IX[B]

	[30] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]

	[31] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]

	[32] -1	0	0x0000f900 - 0x0000f91f (0x20) IX[B]

	[33] -1	0	0x0000fa00 - 0x0000fa1f (0x20) IX[B]

	[34] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]

	[35] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]

	[36] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]

	[37] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]

	[38] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]

	[39] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B](B)

	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]

	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]

(II) Loading sub module "int10"

(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so

(II) VESA(0): initializing int10

(II) VESA(0): Primary V_BIOS segment is: 0xc000

(II) VESA(0): VESA BIOS detected

(II) VESA(0): VESA VBE Version 3.0

(II) VESA(0): VESA VBE Total Mem: 16384 kB

(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS

(II) VESA(0): VESA VBE OEM Software Rev: 10.65

(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 

(II) VESA(0): VESA VBE OEM Product: RV610

(II) VESA(0): VESA VBE OEM Product Rev: 01.00

(==) VESA(0): Write-combining range (0xd0000000,0x1000000)

(II) VESA(0): virtual address = 0xb6a00000,

	physical address = 0xd0000000, size = 16777216

(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.

(==) VESA(0): Default visual is TrueColor

(==) VESA(0): Backing store disabled

(**) Option "dpms"

(**) VESA(0): DPMS enabled

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

(II) AIGLX: Screen 0 is not DRI capable

(II) Loading sub module "GLcore"

(II) LoadModule: "GLcore"

(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so

(II) Module GLcore: vendor="X.Org Foundation"

	compiled for 1.4.0.90, module version = 1.0.0

	ABI class: X.Org Server Extension, version 0.3

(II) GLX: Initialized MESA-PROXY GL provider for screen 0

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

(**) Option "Protocol" "ImPS/2"

(**) Configured Mouse: Device: "/dev/input/mice"

(**) Configured Mouse: Protocol: "ImPS/2"

(**) Option "CorePointer"

(**) Configured Mouse: always reports core events

(**) Option "Device" "/dev/input/mice"

(**) Option "Emulate3Buttons" "true"

(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50

(**) Option "ZAxisMapping" "4 5"

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

SetGrabKeysState - disabled

SetGrabKeysState - enabled

SetClientVersion: 0 9

SetClientVersion: 0 9

SetClientVersion: 0 9
```

---

### Post by Forlong on 2008-06-05
Well, you are a victim of ATI's linux driver policy.

It seems like your card is too new to be supported by the driver included in Ubuntu.
Try the latest driver from ATI directly: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.5.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.5.29)

---

### Post by josh8 on 2008-06-05
That did it! Every thing is working perfectly. Thank you so much!

---

