---
title: "Ubuntu Studio Kernel 14-rt kills NVIDIA in GUTSY"
date: 2007-10-22
forum: General Help
---

### Post by Shlomir on 2007-10-22
Hi there,

I've upgraded my GUTSY to Ubuntu-Studio via a LiveCd, it's upgraded OK HOWEVER, when I use the Kernel 'Ubuntu 7.10 2.6.22-14-rt', it kills Xorg and the Nvidia driver I get the following :

```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux U-Booty 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 22 19:42:47 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation NV36.2 [GeForce FX 5700]"
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
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
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
(II) PCI: 00:00:0: chip 8086,2570 card 1849,2570 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1849,24d0 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1849,24d0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1849,24d0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1849,24d0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1849,24d0 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1849,24d0 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 1849,24d1 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1849,24d0 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1849,9761 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0342 card 107d,298b rev a1 class 03,00,00 hdr 00
(II) PCI: 02:02:0: chip 1106,3044 card 1106,3044 rev 80 class 0c,00,10 hdr 00
(II) PCI: 02:05:0: chip 10ec,8139 card 1849,8139 rev 10 class 02,00,00 hdr 00
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
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc900000 - 0xfe9fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd7f00000 - 0xf7efffff (0x20000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV36.2 [GeForce FX 5700] rev 161, Mem @ 0xfd000000/24, 0xe0000000/28, BIOS @ 0xfe9e0000/17
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
	[0] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[1] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[2] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[3] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[4] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[11] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[18] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[1] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[2] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[3] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[4] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[11] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[18] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
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
	[4] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[5] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[20] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[26] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[33] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:48:02 PDT 2007
(II) Loading extension GLX
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
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:14:20 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[5] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[20] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[26] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[33] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[5] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[20] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[23] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[26] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[29] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[35] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[36] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5700 (NV36) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 04.36.20.23.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5700 at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024@75"
(II) NVIDIA(0):     "1280x960@60"
(II) NVIDIA(0):     "1152x864@75"
(II) NVIDIA(0):     "1280x1024@60"
(II) NVIDIA(0):     "1024x768@43"
(II) NVIDIA(0):     "1280x960@75"
(II) NVIDIA(0):     "1024x768@60"
(II) NVIDIA(0):     "1400x1050@60"
(II) NVIDIA(0):     "1024x768@70"
(II) NVIDIA(0):     "1400x1050@75"
(II) NVIDIA(0):     "1024x768@75"
(II) NVIDIA(0):     "1600x1200@65"
(II) NVIDIA(0):     "1024x768@85"
(II) NVIDIA(0):     "1600x1200@60"
(II) NVIDIA(0):     "832x624@75"
(II) NVIDIA(0):     "1792x1344@60"
(II) NVIDIA(0):     "800x600@60"
(II) NVIDIA(0):     "800x600@85"
(II) NVIDIA(0):     "800x600@75"
(II) NVIDIA(0):     "800x600@72"
(II) NVIDIA(0):     "800x600@56"
(II) NVIDIA(0):     "640x480@85"
(II) NVIDIA(0):     "640x480@75"
(II) NVIDIA(0):     "640x480@72"
(II) NVIDIA(0):     "640x480@60"
(**) NVIDIA(0): Virtual screen size configured to be 1792 x 1344
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[7] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[8] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[9] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[10] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[11] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[12] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[13] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[25] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[28] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[30] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[37] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[38] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[39] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "1280x1024@75"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
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
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
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
(II) NVIDIA(0): Setting mode "1280x1024@60"
SetClientVersion: 0 9
```

HOWEVER it works fine when I select the generic 2.6.22-14 kernel...

Is this due to the Nivdia-glx-new not being updated yet, and is there a fix?

Cheers:guitar::guitar:

---

### Post by Prefader on 2007-10-22
Either I'm missing something, or that's the wrong logfile.  There don't appear to be any errors there.  Also, the kernel version at the top of the log claims to be "2.6.22-14-generic".

---

### Post by Jussi01 on 2007-10-22
Did you install the restricted drivers for rt?? If not, then do:

```
sudo apt-get install linux-rt 
```

---

### Post by Shlomir on 2007-10-23
> **Jussi01 said:**
> Did you install the restricted drivers for rt?? If not, then do:

```
sudo apt-get install linux-rt 
```

Thanks Jussi01, that fixed it fine!

---

