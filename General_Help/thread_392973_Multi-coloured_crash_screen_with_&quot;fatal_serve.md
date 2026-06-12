---
title: "Multi-coloured crash screen with &quot;fatal server error: lockup&quot; message in Xorg"
date: 2007-03-25
forum: General Help
---

### Post by Life On Mars on 2007-03-25
About two or three times a week my system crashes leaving me with the following display:

[IMG]http://farm1.static.flickr.com/146/432811067_da8afb095a.jpg?v=0[/IMG]

Keyboard and mouse are totally unresponsive and I have to manually reboot. Everything is then back to normal. The crash reports generated are so huge I can't even open them - 7 MB is the smallest.

In another thread someone suggested looking through the var/log directory. This is what I found for my Xorg.0.log.old file, which looks like it may give some useful information - can anyone tell me what it means?

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux holly 2.6.20-12-generic #2 SMP Wed Mar 21 20:55:46 UTC 2007 i686
Build Date: 20 March 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 23 18:26:12 2007
(==) Using config file: "/etc/X11/xorg.conf"
(WW) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Dell E771A"
(**) |   |-->Device "82810E DC-133"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(WW) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(WW) The core keyboard device wasn't specified explicitly in the layout.
	Using the first core keyboard device.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
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
(II) PCI: 00:00:0: chip 8086,7124 card 1028,0116 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7125 card 1028,0116 rev 03 class 03,00,00 hdr 00
(II) PCI: 00:1e:0: chip 8086,2418 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2410 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2411 card 8086,2411 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2412 card 8086,2412 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2413 card 8086,2413 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2415 card 1028,0116 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:07:0: chip 1033,0035 card 1799,0001 rev 43 class 0c,03,10 hdr 80
(II) PCI: 01:07:1: chip 1033,0035 card 1799,0001 rev 43 class 0c,03,10 hdr 00
(II) PCI: 01:07:2: chip 1033,00e0 card 1799,0002 rev 04 class 0c,03,20 hdr 00
(II) PCI: 01:08:0: chip 10ec,8139 card 13e0,0001 rev 10 class 02,00,00 hdr 00
(II) PCI: 01:0a:0: chip 14f1,2016 card 13e0,021a rev 01 class 07,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[1] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[2] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[3] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xff800000 - 0xff9fffff (0x200000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:1:0) Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] rev 3, Mem @ 0xf8000000/26, 0xffa00000/19
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
	[0] -1	0	0xff8e0000 - 0xff8effff (0x10000) MX[B]
	[1] -1	0	0xff8fd800 - 0xff8fd8ff (0x100) MX[B]
	[2] -1	0	0xff8fdc00 - 0xff8fdcff (0x100) MX[B]
	[3] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[4] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[5] -1	0	0xffa00000 - 0xffa7ffff (0x80000) MX[B](B)
	[6] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[7] -1	0	0x0000e8f8 - 0x0000e8ff (0x8) IX[B]
	[8] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[9] -1	0	0x0000dc80 - 0x0000dcbf (0x40) IX[B]
	[10] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[11] -1	0	0x0000dcd0 - 0x0000dcdf (0x10) IX[B]
	[12] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xff8e0000 - 0xff8effff (0x10000) MX[B]
	[1] -1	0	0xff8fd800 - 0xff8fd8ff (0x100) MX[B]
	[2] -1	0	0xff8fdc00 - 0xff8fdcff (0x100) MX[B]
	[3] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[4] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[5] -1	0	0xffa00000 - 0xffa7ffff (0x80000) MX[B](B)
	[6] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[7] -1	0	0x0000e8f8 - 0x0000e8ff (0x8) IX[B]
	[8] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[9] -1	0	0x0000dc80 - 0x0000dcbf (0x40) IX[B]
	[10] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[11] -1	0	0x0000dcd0 - 0x0000dcdf (0x10) IX[B]
	[12] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
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
	[4] -1	0	0xff8e0000 - 0xff8effff (0x10000) MX[B]
	[5] -1	0	0xff8fd800 - 0xff8fd8ff (0x100) MX[B]
	[6] -1	0	0xff8fdc00 - 0xff8fdcff (0x100) MX[B]
	[7] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[8] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[9] -1	0	0xffa00000 - 0xffa7ffff (0x80000) MX[B](B)
	[10] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e8f8 - 0x0000e8ff (0x8) IX[B]
	[14] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[15] -1	0	0x0000dc80 - 0x0000dcbf (0x40) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000dcd0 - 0x0000dcdf (0x10) IX[B]
	[18] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
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
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.7.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
(II) Primary Device is: PCI 00:01:0
(--) Chipset i810e found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff8e0000 - 0xff8effff (0x10000) MX[B]
	[5] -1	0	0xff8fd800 - 0xff8fd8ff (0x100) MX[B]
	[6] -1	0	0xff8fdc00 - 0xff8fdcff (0x100) MX[B]
	[7] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[8] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[9] -1	0	0xffa00000 - 0xffa7ffff (0x80000) MX[B](B)
	[10] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e8f8 - 0x0000e8ff (0x8) IX[B]
	[14] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[15] -1	0	0x0000dc80 - 0x0000dcbf (0x40) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000dcd0 - 0x0000dcdf (0x10) IX[B]
	[18] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff8e0000 - 0xff8effff (0x10000) MX[B]
	[5] -1	0	0xff8fd800 - 0xff8fd8ff (0x100) MX[B]
	[6] -1	0	0xff8fdc00 - 0xff8fdcff (0x100) MX[B]
	[7] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[8] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[9] -1	0	0xffa00000 - 0xffa7ffff (0x80000) MX[B](B)
	[10] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e8f8 - 0x0000e8ff (0x8) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[18] -1	0	0x0000dc80 - 0x0000dcbf (0x40) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[20] -1	0	0x0000dcd0 - 0x0000dcdf (0x10) IX[B]
	[21] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(**) I810(0): Depth 24, (--) framebuffer bpp 24
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(**) I810(0): DRI is disabled because it runs only at 16-bit depth.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) I810(0): initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 1024 kB
(II) I810(0): VESA VBE OEM: Intel(R) 8xx Chipset Video BIOS
(II) I810(0): VESA VBE OEM Software Rev: 34.40
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(R) 8xx Chipset
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: DEL  Model: a001  Serial#: 942754631
(II) I810(0): Year: 2002  Week: 11
(II) I810(0): EDID Version: 1.3
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) I810(0): Sync:  Separate
(II) I810(0): Max H-Image Size [cm]: horiz.: 31  vert.: 23
(II) I810(0): Gamma: 2.90
(II) I810(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) I810(0): First detailed timing is preferred mode
(II) I810(0): redX: 0.630 redY: 0.340   greenX: 0.279 greenY: 0.601
(II) I810(0): blueX: 0.145 blueY: 0.061   whiteX: 0.282 whiteY: 0.297
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) I810(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) I810(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) I810(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 78.8 MHz   Image Size:  310 x 230 mm
(II) I810(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) I810(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) I810(0): Serial No: 23DDC23C81KG
(II) I810(0): Monitor name: DELL E771a
(II) I810(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) I810(0): EDID (in hex):
(II) I810(0): 	00ffffffffffff0010ac01a0474b3138
(II) I810(0): 	0b0c0103081f17beea4b24a157479925
(II) I810(0): 	0f484ca4420031594559615981800101
(II) I810(0): 	010101010101c31e0020410020301060
(II) I810(0): 	130036e61000001e000000ff00323344
(II) I810(0): 	444332334338314b4720000000fc0044
(II) I810(0): 	454c4c2045373731610a2020000000fd
(II) I810(0): 	0032a01e460b000a20202020202000a8
(II) I810(0): Using hsync ranges from config file
(II) I810(0): Using vrefresh ranges from config file
(II) I810(0): Printing DDC gathered Modelines:
(II) I810(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) I810(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) I810(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) I810(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) I810(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) I810(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) I810(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) I810(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(II) I810(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) I810(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(--) I810(0): Chipset: "i810e"
(--) I810(0): Linear framebuffer at 0xF8000000
(--) I810(0): IO registers at addr 0xFFA00000
(II) I810(0): Kernel reported 112128 total, 1 used
(II) I810(0): I810CheckAvailableMemory: 448508k available
(==) I810(0): Will alloc AGP framebuffer: 8192 kByte
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): Dell E771A: Using hsync range of 51.00-80.00 kHz
(II) I810(0): Dell E771A: Using vrefresh range of 60.00-90.00 Hz
(II) I810(0): Clock range:   9.50 to 136.00 MHz
(II) I810(0): Not using default mode "640x350" (hsync out of range)
(II) I810(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x400" (hsync out of range)
(II) I810(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "720x400" (hsync out of range)
(II) I810(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x480" (hsync out of range)
(II) I810(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x480" (hsync out of range)
(II) I810(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x480" (hsync out of range)
(II) I810(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x480" (hsync out of range)
(II) I810(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (hsync out of range)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (hsync out of range)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (hsync out of range)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (hsync out of range)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1024x768" (unknown reason)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1024x768" (hsync out of range)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x1024" (mode clock too high)
(II) I810(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "832x624" (hsync out of range)
(II) I810(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x768" (hsync out of range)
(II) I810(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x800" (hsync out of range)
(II) I810(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1152x768" (hsync out of range)
(II) I810(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1152x864" (mode clock too high)
(II) I810(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1400x1050" (mode clock too high)
(II) I810(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) I810(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) I810(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) I810(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using driver mode "640x480" (hsync out of range)
(II) I810(0): Not using driver mode "640x480" (hsync out of range)
(II) I810(0): Not using driver mode "720x400" (hsync out of range)
(II) I810(0): Not using driver mode "800x600" (hsync out of range)
(II) I810(0): Not using driver mode "640x480" (hsync out of range)
(II) I810(0): Not using mode "640x480" (no mode of this name)
(II) I810(0): Not using driver mode "1280x1024" (width too large for virtual size)
(II) I810(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) I810(0): Not using default mode "1440x900" (width too large for virtual size)
(II) I810(0): Not using default mode "1280x960" (width too large for virtual size)
(II) I810(0): Not using default mode "1152x864" (width too large for virtual size)
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) I810(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) I810(0): *Driver mode "800x600": 56.8 MHz, 53.7 kHz, 84.9 Hz
(II) I810(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(**) I810(0):  Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 84.9 Hz
(II) I810(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(**) I810(0):  Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) I810(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) I810(0):  Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) I810(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) I810(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) I810(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) I810(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) I810(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) I810(0):  Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) I810(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) I810(0): Display dimensions: (310, 230) mm
(**) I810(0): DPI set to (83, 84)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) I810(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xffa00000 - 0xffa7ffff (0x80000) MS[B]
	[1] 0	0	0xf8000000 - 0xfbffffff (0x4000000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xff8e0000 - 0xff8effff (0x10000) MX[B]
	[7] -1	0	0xff8fd800 - 0xff8fd8ff (0x100) MX[B]
	[8] -1	0	0xff8fdc00 - 0xff8fdcff (0x100) MX[B]
	[9] -1	0	0xff8fe000 - 0xff8fefff (0x1000) MX[B]
	[10] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[11] -1	0	0xffa00000 - 0xffa7ffff (0x80000) MX[B](B)
	[12] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e8f8 - 0x0000e8ff (0x8) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[20] -1	0	0x0000dc80 - 0x0000dcbf (0x40) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000dcd0 - 0x0000dcdf (0x10) IX[B]
	[23] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) I810(0): Write-combining range (0xf8000000,0x4000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) I810(0): Setting dot clock to 78.7 MHz [ 0x50 0x17 0x20 ] [ 82 25 2 ]
(II) I810(0): chose watermark 0x22215000: (tab.freq 78.8)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x00000000 (pgoffset 0)
(WW) I810(0): xf86AllocateGARTMemory: allocation of 1024 pages failed
	(Cannot allocate memory)
(II) I810(0): No physical memory available for 4194304 bytes of DCACHE
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x00800000 (pgoffset 2048)
(II) I810(0): Allocated of 4096 bytes for HW cursor
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x00801000 (pgoffset 2049)
(II) I810(0): Allocated of 16384 bytes for ARGB HW cursor
(II) I810(0): Adding 512 scanlines for pixmap caching
(II) I810(0): Allocated Scratch Memory
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		16 128x128 slots
		4 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(**) Option "dpms"
(**) I810(0): DPMS enabled
(WW) I810(0): Direct rendering disabled
(WW) I810(0): Option "UseFBDev" is not used
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
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Buttons" "7"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "6 7"
(**) Configured Mouse: ZAxisMapping: buttons 6 and 7
(**) Option "ButtonMapping" "1 2 3 4 5"
(**) Configured Mouse: Buttons: 11
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
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
Error in I810WaitLpRing(), now is 86332149, start is 86330148
pgetbl_ctl: 0x13ed0001 pgetbl_err: 0x2e2e000
ipeir: 0 iphdr: 50c00004
LP ring tail: 4328 head: 4188 len: f001 start 3c0000
eir: 0 esr: 0 emr: 3d
instdone: ff3a instpm: 0
memmode: 4 instps: 810
hwstam: 9ac7 ier: 0 imr: 9ac7 iir: 0
space: 65112 wanted 65528

Fatal server error:
lockup

Error in I810WaitLpRing(), now is 86334894, start is 86332893
pgetbl_ctl: 0x13ed0001 pgetbl_err: 0x0
ipeir: 0 iphdr: 50c00004
LP ring tail: 4330 head: 4188 len: f001 start 3c0000
eir: 0 esr: 0 emr: 3d
instdone: ff3a instpm: 0
memmode: 4 instps: 810
hwstam: 9ac7 ier: 0 imr: 9ac7 iir: 0
space: 65104 wanted 65528

FatalError re-entered, aborting
lockup

```

---

### Post by scorcher on 2007-03-29
I have an Intel 82810 video card too and the exact same thing happens to me.

I cannot figure out exactly what is going wrong but it seems to only crash when I am using Firefox, and it first started happening when I upgraded to Firefox 1.5.

The crash seems to occur more on javascript heavy pages.

Any help or suggestions anyone can give would be awesome.



scorcher

---

### Post by Life On Mars on 2007-03-31
Nice to know that I'm not completely alone with this ):P 

Just to add that I had wondered if it was something to do with javascript, too. Thinking about it, I'm sure this crash happened a couple of times using BasKet and Kopete, two Kubuntu applications, too.

---

### Post by macjones on 2007-10-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/50576](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/50576) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Might be worth a look here...

I know the xorg log file here just says "FatalError", and mine says "Active Ring Not Flushed", but the pattern on my screen is exactly the same. Machine is a Dell Optiplex GX110.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/50576](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/50576)

---

