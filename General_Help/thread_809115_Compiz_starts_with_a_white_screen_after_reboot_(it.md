---
title: "Compiz starts with a white screen after reboot (it worked yesterday)"
date: 2008-05-27
forum: General Help
---

### Post by mehovv on 2008-05-27
Hello,

I had Compiz configured and working nicely for the last couple of weeks (Ubuntu 8.04). However upon installation of the latest updates few hours ago (or at least that's what I think might caused it) and restarting the system, I get white screen after I log in. My xorg.conf hasn't changed. I have ATI Mobility Radeon 9700. Here's my /var/log/Xorg.0.log:

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
Current Operating System: Linux CALIFORNIA 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 27 10:50:23 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Synaptics Touchpad"
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
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
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
(II) PCI: 00:00:0: chip 8086,3340 card 1462,0031 rev 21 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,3341 card 0000,0000 rev 21 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 1462,0031 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1462,0031 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1462,0031 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1462,0031 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 83 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 1462,0031 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1462,0031 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 1462,0031 rev 03 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4e50 card 1462,0311 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:03:0: chip 10ec,8139 card 1462,0031 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 1180,0476 card c000,0000 rev ac class 06,07,00 hdr 82
(II) PCI: 02:04:1: chip 1180,0476 card cc00,0000 rev ac class 06,07,00 hdr 82
(II) PCI: 02:04:2: chip 1180,0552 card 1462,0031 rev 04 class 0c,00,10 hdr 80
(II) PCI: 02:09:0: chip 8086,4220 card 8086,2701 rev 05 class 02,80,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x0000bfff (0x3000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xffc00000 - 0xffcfffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xceb00000 - 0xdeafffff (0x10000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,10), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xffd00000 - 0xffdfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:4:0), (2,3,6), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 7: bridge is at (2:4:1), (2,7,10), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 7 I/O range:
	[0] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] rev 0, Mem @ 0xd0000000/27, 0xffcf0000/16, I/O @ 0xb000/8, BIOS @ 0xffcc0000/17
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xefffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xffdfe000 - 0xffdfefff (0x1000) MX[B]
	[1] -1	0	0xffdff000 - 0xffdff7ff (0x800) MX[B]
	[2] -1	0	0xffdffc00 - 0xffdffcff (0x100) MX[B]
	[3] -1	0	0xffeff400 - 0xffeff4ff (0x100) MX[B]
	[4] -1	0	0xffeff800 - 0xffeff9ff (0x200) MX[B]
	[5] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[6] -1	0	0xffeffc00 - 0xffefffff (0x400) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xffcc0000 - 0xffcdffff (0x20000) MX[B](B)
	[9] -1	0	0xffcf0000 - 0xffcfffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[12] -1	0	0x0000e080 - 0x0000e0ff (0x80) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e03f (0x40) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[16] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[22] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xffdfe000 - 0xffdfefff (0x1000) MX[B]
	[1] -1	0	0xffdff000 - 0xffdff7ff (0x800) MX[B]
	[2] -1	0	0xffdffc00 - 0xffdffcff (0x100) MX[B]
	[3] -1	0	0xffeff400 - 0xffeff4ff (0x100) MX[B]
	[4] -1	0	0xffeff800 - 0xffeff9ff (0x200) MX[B]
	[5] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[6] -1	0	0xffeffc00 - 0xffefffff (0x400) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xffcc0000 - 0xffcdffff (0x20000) MX[B](B)
	[9] -1	0	0xffcf0000 - 0xffcfffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[12] -1	0	0x0000e080 - 0x0000e0ff (0x80) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e03f (0x40) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[16] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[22] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
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
	[4] -1	0	0xffdfe000 - 0xffdfefff (0x1000) MX[B]
	[5] -1	0	0xffdff000 - 0xffdff7ff (0x800) MX[B]
	[6] -1	0	0xffdffc00 - 0xffdffcff (0x100) MX[B]
	[7] -1	0	0xffeff400 - 0xffeff4ff (0x100) MX[B]
	[8] -1	0	0xffeff800 - 0xffeff9ff (0x200) MX[B]
	[9] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[10] -1	0	0xffeffc00 - 0xffefffff (0x400) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xffcc0000 - 0xffcdffff (0x20000) MX[B](B)
	[13] -1	0	0xffcf0000 - 0xffcfffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[18] -1	0	0x0000e080 - 0x0000e0ff (0x80) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e03f (0x40) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[28] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.47.3
	Module class: X.Org Video Driver
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
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.47.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.476                    
(II) ATI Proprietary Linux Driver Build Date: Mar 29 2008 00:05:22
(--) Chipset Supported AMD Graphics Processor (0x4E50) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffdfe000 - 0xffdfefff (0x1000) MX[B]
	[5] -1	0	0xffdff000 - 0xffdff7ff (0x800) MX[B]
	[6] -1	0	0xffdffc00 - 0xffdffcff (0x100) MX[B]
	[7] -1	0	0xffeff400 - 0xffeff4ff (0x100) MX[B]
	[8] -1	0	0xffeff800 - 0xffeff9ff (0x200) MX[B]
	[9] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[10] -1	0	0xffeffc00 - 0xffefffff (0x400) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xffcc0000 - 0xffcdffff (0x20000) MX[B](B)
	[13] -1	0	0xffcf0000 - 0xffcfffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[18] -1	0	0x0000e080 - 0x0000e0ff (0x80) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e03f (0x40) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[28] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x820f238
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffdfe000 - 0xffdfefff (0x1000) MX[B]
	[5] -1	0	0xffdff000 - 0xffdff7ff (0x800) MX[B]
	[6] -1	0	0xffdffc00 - 0xffdffcff (0x100) MX[B]
	[7] -1	0	0xffeff400 - 0xffeff4ff (0x100) MX[B]
	[8] -1	0	0xffeff800 - 0xffeff9ff (0x200) MX[B]
	[9] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[10] -1	0	0xffeffc00 - 0xffefffff (0x400) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xffcc0000 - 0xffcdffff (0x20000) MX[B](B)
	[13] -1	0	0xffcf0000 - 0xffcfffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[21] -1	0	0x0000e080 - 0x0000e0ff (0x80) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e03f (0x40) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[25] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[31] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[33] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DesktopSetup" "clone"
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI MOBILITY RADEON 9600/9700 Series" (Chipset = 0x4e50)
(--) fglrx(0): (PciSubVendor = 0x1462, PciSubDevice = 0x0311)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xffcf0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 65536 kB
(II) fglrx(0): VESA VBE OEM: ATI MOBILITY RADEON 9600   
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: P11 
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 65536 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0):  Display1: Failed to get EDID information. 
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 446/230MHz @ 60Hz [enable load balancing]
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 16 modes found for primary display.
(--) fglrx(0): Virtual size is 1400x1050 (pitch 0)
(**) fglrx(0): *Mode "1400x1050": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  108.00  1400 1440 1552 1688  1050 1052 1055 1063 (64.0 kHz)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1376 1488 1688  1024 1038 1041 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "1280x768": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0  108.00  1280 1376 1496 1688  768 910 913 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0  108.00  1152 1312 1424 1688  864 961 964 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0  108.00  1024 1248 1360 1688  768 910 913 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "848x480": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0  108.00  848 1160 1272 1688  480 766 769 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "800x600": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0  108.00  800 1136 1248 1688  600 826 829 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "720x576": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"x60.0  108.00  720 1096 1208 1688  576 814 817 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "720x480": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0  108.00  720 1096 1208 1688  480 766 769 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "640x480": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0  108.00  640 1056 1168 1688  480 766 769 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "640x400": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0  108.00  640 1056 1168 1688  400 726 729 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "640x350": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"x60.0  108.00  640 1056 1168 1688  350 701 704 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "512x384": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0  108.00  512 992 1104 1688  384 718 721 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "400x300": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0  108.00  400 936 1048 1688  300 826 829 1066 doublescan (64.0 kHz)
(**) fglrx(0):  Default mode "320x240": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0  108.00  320 920 1032 1688  240 766 769 1066 doublescan (64.0 kHz)
(**) fglrx(0):  Default mode "320x200": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0  108.00  320 920 1032 1688  200 726 729 1066 doublescan (64.0 kHz)
(==) fglrx(0): DPI set to (96, 96)
(--) fglrx(0): Virtual size is 1400x1050 (pitch 1408)
(**) fglrx(0): *Mode "1400x1050": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  108.00  1400 1440 1552 1688  1050 1052 1055 1063 (64.0 kHz)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1376 1488 1688  1024 1038 1041 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "1280x768": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0  108.00  1280 1376 1496 1688  768 910 913 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0  108.00  1152 1312 1424 1688  864 961 964 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0  108.00  1024 1248 1360 1688  768 910 913 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "848x480": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0  108.00  848 1160 1272 1688  480 766 769 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "800x600": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0  108.00  800 1136 1248 1688  600 826 829 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "720x576": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"x60.0  108.00  720 1096 1208 1688  576 814 817 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "720x480": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0  108.00  720 1096 1208 1688  480 766 769 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "640x480": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0  108.00  640 1056 1168 1688  480 766 769 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "640x400": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0  108.00  640 1056 1168 1688  400 726 729 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "640x350": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"x60.0  108.00  640 1056 1168 1688  350 701 704 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "512x384": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0  108.00  512 992 1104 1688  384 718 721 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "400x300": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0  108.00  400 936 1048 1688  300 826 829 1066 doublescan (64.0 kHz)
(**) fglrx(0):  Default mode "320x240": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0  108.00  320 920 1032 1688  240 766 769 1066 doublescan (64.0 kHz)
(**) fglrx(0):  Default mode "320x200": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0  108.00  320 920 1032 1688  200 726 729 1066 doublescan (64.0 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.47.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xffcf0000 - 0xffcfffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xffdfe000 - 0xffdfefff (0x1000) MX[B]
	[7] -1	0	0xffdff000 - 0xffdff7ff (0x800) MX[B]
	[8] -1	0	0xffdffc00 - 0xffdffcff (0x100) MX[B]
	[9] -1	0	0xffeff400 - 0xffeff4ff (0x100) MX[B]
	[10] -1	0	0xffeff800 - 0xffeff9ff (0x200) MX[B]
	[11] -1	0	0x88000000 - 0x880003ff (0x400) MX[B]
	[12] -1	0	0xffeffc00 - 0xffefffff (0x400) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0xffcc0000 - 0xffcdffff (0x20000) MX[B](B)
	[15] -1	0	0xffcf0000 - 0xffcfffff (0x10000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[20] 0	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[24] -1	0	0x0000e080 - 0x0000e0ff (0x80) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e03f (0x40) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[28] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[34] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[35] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[36] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-3)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x04000000
(==) fglrx(0): Write-combining range (0xd0000000,0x4000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1408,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1408,1050) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1408 x 7141
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
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
Synaptics Touchpad no synaptics event device found (checked 19 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizEdgeScroll" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
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
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

Please help. I want my Compiz back ;(

---

### Post by vincentvee on 2008-05-27
hey i got that exact same problem, i thought it might be the new kernel, but then was just thinkin alond the lines of what you were saying, that it might be X, anyway trying to get a fix to it now, how are you going with yours?

---

### Post by mehovv on 2008-05-27
I didn't have more time to play with it now, so I rebooted and chose an older kernel with GRUB. That solved the problem for now. If you happen to find a better solution, please share it here. Thanks.

---

### Post by Neo4 on 2008-05-27
Same problem here after updating the kernel today!

---

### Post by RatSAT on 2008-05-27
And for me as well after updating from kernel-2.6.24-16 -> kernel-2.6.24-17. So back to the old kernel and waiting for a fix.

The reason for me seems to be that the ATI fglrx drivers are not loaded correctly. I have an ATI Radeon 9800 pro card, in case it matters.

---

### Post by Neo4 on 2008-05-27
mine is an ATI x700 mobile

---

### Post by tors on 2008-05-27
I resolved this by removing the dkms fglrx-modules and reinstalled my generated fglrx-debs from the ati-installer.

#dkms status

fglrx, 8.493, 2.6.24-17-generic, i686: installed

#sudo dkms remove -m fglrx -v 8.493 --all

#sudo dpkg -i fglrx-amdcccle_8.493-0ubuntu1_i386.deb fglrx-kernel-source_8.493-0ubuntu1_i386.deb xorg-driver-fglrx_8.493-0ubuntu1_i386.deb

---

### Post by mehovv on 2008-05-27
I have uninstalled and installed all three packages from the console, and it indeed solved the problem. Thanks for the tip tors.

---

### Post by BATLI on 2008-05-27
ive this problem just from 2 hours after i install update to xserver . but i restart computer and login as root and clear all data in xorg.conf file and computer login good but resolution and all desktop effects are changed and i returned all data to xorg.conf from my backup file

---

### Post by del_Brujo on 2008-05-29
I have the same problem here.
tors, sorry for being so noob, but I don't fully understand what you saying here. Do you mean install ati drivers again?
> **tors said:**
> I resolved this by removing the dkms fglrx-modules and reinstalled my generated fglrx-debs from the ati-installer.

#dkms status

fglrx, 8.493, 2.6.24-17-generic, i686: installed

#sudo dkms remove -m fglrx -v 8.493 --all

#sudo dpkg -i fglrx-amdcccle_8.493-0ubuntu1_i386.deb fglrx-kernel-source_8.493-0ubuntu1_i386.deb xorg-driver-fglrx_8.493-0ubuntu1_i386.deb

---

