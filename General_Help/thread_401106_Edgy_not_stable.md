---
title: "Edgy not stable"
date: 2007-04-04
forum: General Help
---

### Post by mrmonday on 2007-04-04
Hi Everyone,

Recently, for no apparent reason, when I am in Ubuntu, my PC just restarts randomly, or it freezes and doesn't respond to anything (except occasionally mouse movements). Is there any way I can monitor what's going on, so I can try and diagnose the problem? Also (and more importantly) how can I solve this problem.

I am very close to doing something I really don't want to do (go back to windows)....

Thanks for any help.

---

### Post by 1/0 on 2007-04-04
In Linux, in comparison to Windows, you have log files. One of the best things I know. Check log files in /var/log/. Interesting files are messages, dmesg and Xorg.0.log. 

Post the last bit of the first two and the whole of Xorg.0.log. It could be many things that causes this and it'll be easier if there something to start with.

---

### Post by mrmonday on 2007-04-04
I wasn't sure what you meant by 'the last bit' so I will attach them all, and post a chunk from the ends.

Won't let me attach them...

xorg.0.log:
> 
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux Roberts-PC 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr  4 12:47:39 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "CMC 22 W"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card"
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
(II) PCI: 00:00:0: chip 8086,2770 card 1019,1b74 rev 81 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2771 card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,27c8 card 1019,1b74 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1019,1b74 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1019,1b74 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1019,1b74 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1019,1b74 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,27de card 1019,aa52 rev 01 class 04,01,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,27b8 card 1019,1b74 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1019,1b74 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 1019,1b74 rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1019,1b74 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,01df card 1682,2200 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 1814,0301 card 1458,e934 rev 00 class 02,80,00 hdr 00
(II) PCI: 02:05:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfa900000 - 0xfe9fffff (0x4100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xcff00000 - 0xefefffff (0x20000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x01df) rev 161, Mem @ 0xfd000000/24, 0xd0000000/28, 0xfc000000/24, BIOS @ 0xfe9e0000/17
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
	[0] -1	0	0xfeaf7c00 - 0xfeaf7cff (0x100) MX[B]
	[1] -1	0	0xfeaf8000 - 0xfeafffff (0x8000) MX[B]
	[2] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[3] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[4] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[5] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[6] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[10] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[11] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[12] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[14] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[16] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[19] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[22] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeaf7c00 - 0xfeaf7cff (0x100) MX[B]
	[1] -1	0	0xfeaf8000 - 0xfeafffff (0x8000) MX[B]
	[2] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[3] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[4] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[5] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[6] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[10] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[11] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[12] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[14] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[16] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[19] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[22] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
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
	[4] -1	0	0xfeaf7c00 - 0xfeaf7cff (0x100) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafffff (0x8000) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[16] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[18] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[20] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[25] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[28] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
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
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9746
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
	compiled for 4.0.2, module version = 1.0.9746
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
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-9746  Fri Dec 15 09:56:41 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 7.1.99.2, module version = 1.0.0
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
	[4] -1	0	0xfeaf7c00 - 0xfeaf7cff (0x100) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafffff (0x8000) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[16] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[18] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[20] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[25] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[28] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeaf7c00 - 0xfeaf7cff (0x100) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafffff (0x8000) MX[B]
	[6] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[7] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[19] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[21] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[23] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[25] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[27] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[28] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[29] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[31] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GS at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.34.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GS at PCI:1:0:0:
(--) NVIDIA(0):     CMO CMC 22 W (DFP-0)
(--) NVIDIA(0): CMO CMC 22 W (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): CMO CMC 22 W (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1440x1440"; removing.
(WW) NVIDIA(0): No valid modes for "1360x850"; removing.
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1680x1050"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1280x960"
(II) NVIDIA(0):     "1280x800"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfeaf7c00 - 0xfeaf7cff (0x100) MX[B]
	[8] -1	0	0xfeaf8000 - 0xfeafffff (0x8000) MX[B]
	[9] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[10] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[11] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[12] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[22] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[24] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[26] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[27] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[28] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[30] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[31] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[32] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[33] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[34] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1680x1050"
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
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
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
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+gb+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!


hope this helps... (I will post again with the others, it says it is too long otherwise)

---

### Post by mrmonday on 2007-04-04
dmesg:

> [17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000007ffc0000 (usable)
[17179569.184000]  BIOS-e820: 000000007ffc0000 - 000000007ffce000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000007ffce000 - 000000007fff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[17179569.184000] 1151MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 524224
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 294848 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f9020
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x10000518 MSFT 0x00000097) @ 0x7ffc0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x10000518 MSFT 0x00000097) @ 0x7ffc0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x10000518 MSFT 0x00000097) @ 0x7ffc0390
[17179569.184000] ACPI: MCFG (v001 A M I  OEMMCFG  0x10000518 MSFT 0x00000097) @ 0x7ffc03f0
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x10000518 MSFT 0x00000097) @ 0x7ffce040
[17179569.184000] ACPI: DSDT (v001   945P    945PA 0x00000000 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:4 APIC version 20
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 2993.114 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.556000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.556000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.628000] Memory: 2069208k/2096896k available (1911k kernel code, 26352k reserved, 1073k data, 308k init, 1179392k highmem)
[17179572.628000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.708000] Calibrating delay using timer specific routine.. 5992.91 BogoMIPS (lpj=11985836)
[17179572.708000] Security Framework v1.0.0 initialized
[17179572.708000] SELinux:  Disabled at boot.
[17179572.708000] Mount-cache hash table entries: 512
[17179572.708000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[17179572.708000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[17179572.708000] monitor/mwait feature present.
[17179572.708000] using mwait in idle threads.
[17179572.708000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179572.708000] CPU: L2 cache: 2048K
[17179572.708000] CPU: Hyper-Threading is disabled
[17179572.708000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000649d 00000000 00000000
[17179572.708000] Checking 'hlt' instruction... OK.
[17179572.724000] SMP alternatives: switching to UP code
[17179572.724000] checking if image is initramfs... it is
[17179573.148000] Freeing initrd memory: 5326k freed
[17179573.148000] ACPI: Core revision 20060707
[17179573.148000] ACPI: Looking for DSDT ... not found!
[17179573.164000] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[17179573.164000] SMP alternatives: switching to SMP code
[17179573.164000] Booting processor 1/1 eip 3000
[17179573.172000] Initializing CPU#1
[17179573.256000] Calibrating delay using timer specific routine.. 5985.52 BogoMIPS (lpj=11971054)
[17179573.256000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[17179573.256000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[17179573.256000] monitor/mwait feature present.
[17179573.256000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179573.256000] CPU: L2 cache: 2048K
[17179573.256000] CPU: Hyper-Threading is disabled
[17179573.256000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000649d 00000000 00000000
[17179573.256000] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[17179573.256000] Total of 2 processors activated (11978.44 BogoMIPS).
[17179573.256000] ENABLING IO-APIC IRQs
[17179573.256000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.400000] checking TSC synchronization across 2 CPUs: 
[17179573.404000] Brought up 2 CPUs
[17179573.476000] migration_cost=4000
[17179573.476000] NET: Registered protocol family 16
[17179573.476000] EISA bus registered
[17179573.476000] ACPI: bus type pci registered
[17179573.476000] PCI: BIOS Bug: MCFG area at f0000000 is not E820-reserved
[17179573.476000] PCI: Not using MMCONFIG.
[17179573.476000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
[17179573.476000] PCI: Using configuration type 1
[17179573.476000] Setting up standard PCI resources
[17179573.516000] ACPI: Interpreter enabled
[17179573.516000] ACPI: Using IOAPIC for interrupt routing
[17179573.516000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.516000] PCI: Probing PCI hardware (bus 00)
[17179573.520000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179573.520000] Boot video device is 0000:01:00.0
[17179573.520000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.520000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.532000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179573.544000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179573.544000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.544000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.544000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.544000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.544000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.544000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.544000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.544000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.544000] pnp: PnP ACPI init
[17179573.548000] pnp: PnP ACPI: found 16 devices
[17179573.548000] PnPBIOS: Disabled by ACPI PNP
[17179573.548000] PCI: Using ACPI for IRQ routing
[17179573.548000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.556000] pnp: 00:0c: ioport range 0x290-0x29f has been reserved
[17179573.556000] PCI: Bridge: 0000:00:01.0
[17179573.556000]   IO window: disabled.
[17179573.556000]   MEM window: fa900000-fe9fffff
[17179573.556000]   PREFETCH window: cff00000-efefffff
[17179573.556000] PCI: Bridge: 0000:00:1e.0
[17179573.556000]   IO window: c000-cfff
[17179573.556000]   MEM window: fea00000-feafffff
[17179573.556000]   PREFETCH window: disabled.
[17179573.556000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.556000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.556000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179573.556000] NET: Registered protocol family 2
[17179573.596000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.596000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[17179573.596000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179573.596000] TCP: Hash tables configured (established 262144 bind 65536)
[17179573.596000] TCP reno registered
[17179573.596000] audit: initializing netlink socket (disabled)
[17179573.596000] audit(1175690838.596:1): initialized
[17179573.596000] highmem bounce pool size: 64 pages
[17179573.596000] VFS: Disk quotas dquot_6.5.1
[17179573.596000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.596000] Initializing Cryptographic API
[17179573.596000] io scheduler noop registered
[17179573.596000] io scheduler anticipatory registered
[17179573.596000] io scheduler deadline registered
[17179573.596000] io scheduler cfq registered (default)
[17179573.596000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.596000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.596000] assign_interrupt_mode Found MSI capability
[17179573.596000] Allocate Port Service[0000:00:01.0:pcie00]
[17179573.596000] isapnp: Scanning for PnP cards...
[17179573.952000] isapnp: No Plug & Play device found
[17179573.976000] Real Time Clock Driver v1.12ac
[17179573.976000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.976000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.976000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.976000] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.976000] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.976000] mice: PS/2 mouse device common for all mice
[17179573.976000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.976000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.976000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.980000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179573.980000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179573.980000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.980000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.980000] EISA: Probing bus 0 at eisa.0
[17179573.980000] EISA: Detected 0 cards.
[17179573.980000] TCP bic registered
[17179573.980000] NET: Registered protocol family 1
[17179573.980000] NET: Registered protocol family 8
[17179573.980000] NET: Registered protocol family 20
[17179573.980000] Starting balanced_irq
[17179573.980000] Using IPI No-Shortcut mode
[17179573.980000] ACPI: (supports S0 S1 S3 S4 S5)
[17179573.980000] Freeing unused kernel memory: 308k freed
[17179574.260000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.048000] Capability LSM initialized
[17179575.084000] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node dffed2d4), AE_BAD_HEADER
[17179575.084000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179575.084000] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PDC] (Node dffed84c), AE_BAD_HEADER
[17179575.084000] ACPI: Processor [CPU2] (supports 8 throttling states)
[17179575.084000] ACPI: Thermal Zone [THRM] (-269 C)
[17179575.748000] ICH7: IDE controller at PCI slot 0000:00:1f.1
[17179575.748000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 193
[17179575.748000] ICH7: chipset revision 1
[17179575.748000] ICH7: not 100% native mode: will probe irqs later
[17179575.748000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[17179575.748000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
[17179575.748000] Probing IDE interface ide0...
[17179576.684000] hda: ASUS DRW-1608P2S, ATAPI CD/DVD-ROM drive
[17179577.504000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.504000] Probing IDE interface ide1...
[17179578.088000] hda: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2000kB Cache, UDMA(66)
[17179578.088000] Uniform CD-ROM driver Revision: 3.20
[17179578.192000] SCSI subsystem initialized
[17179578.192000] libata version 1.20 loaded.
[17179578.196000] ata_piix 0000:00:1f.2: version 1.05
[17179578.196000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 201
[17179578.196000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179578.196000] ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE882 bmdma 0xE400 irq 201
[17179578.196000] ata2: SATA max UDMA/133 cmd 0xE800 ctl 0xE482 bmdma 0xE408 irq 201
[17179578.360000] ata1: dev 0 cfg 49:2f00 82:7c6b 83:7f09 84:4773 85:7c69 86:3e01 87:4763 88:207f
[17179578.360000] ata1: dev 0 ATA-7, max UDMA/133, 160086528 sectors: LBA48
[17179578.368000] ata1: dev 0 configured for UDMA/133
[17179578.368000] scsi0 : ata_piix
[17179578.532000] ata2: disabling port
[17179578.532000] scsi1 : ata_piix
[17179578.532000]   Vendor: ATA       Model: Maxtor 6V080E0    Rev: VA11
[17179578.532000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179578.540000] SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
[17179578.540000] sda: Write Protect is off
[17179578.540000] sda: Mode Sense: 00 3a 00 00
[17179578.540000] SCSI device sda: drive cache: write back
[17179578.540000] SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
[17179578.540000] sda: Write Protect is off
[17179578.540000] sda: Mode Sense: 00 3a 00 00
[17179578.540000] SCSI device sda: drive cache: write back
[17179578.540000]  sda: sda1 sda2 sda3 < sda5 >
[17179578.572000] sd 0:0:0:0: Attached scsi disk sda
[17179578.760000] Probing IDE interface ide1...
[17179578.820000] usbcore: registered new driver usbfs
[17179578.820000] usbcore: registered new driver hub
[17179578.824000] USB Universal Host Controller Interface driver v3.0
[17179578.824000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 209
[17179578.824000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179578.824000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179578.824000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179578.824000] uhci_hcd 0000:00:1d.0: irq 209, io base 0x0000e080
[17179578.824000] usb usb1: configuration #1 chosen from 1 choice
[17179578.824000] hub 1-0:1.0: USB hub found
[17179578.824000] hub 1-0:1.0: 2 ports detected
[17179578.928000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 201
[17179578.928000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179578.928000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179578.928000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179578.928000] uhci_hcd 0000:00:1d.1: irq 201, io base 0x0000e000
[17179578.928000] usb usb2: configuration #1 chosen from 1 choice
[17179578.928000] hub 2-0:1.0: USB hub found
[17179578.928000] hub 2-0:1.0: 2 ports detected
[17179579.032000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 193
[17179579.032000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179579.032000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179579.032000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179579.032000] uhci_hcd 0000:00:1d.2: irq 193, io base 0x0000dc00
[17179579.032000] usb usb3: configuration #1 chosen from 1 choice
[17179579.032000] hub 3-0:1.0: USB hub found
[17179579.032000] hub 3-0:1.0: 2 ports detected
[17179579.136000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179579.136000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179579.136000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179579.136000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179579.136000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000d880
[17179579.136000] usb usb4: configuration #1 chosen from 1 choice
[17179579.136000] hub 4-0:1.0: USB hub found
[17179579.136000] hub 4-0:1.0: 2 ports detected
[17179579.168000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179579.252000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 209
[17179579.252000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179579.252000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179579.252000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179579.252000] ehci_hcd 0000:00:1d.7: debug port 1
[17179579.252000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179579.252000] ehci_hcd 0000:00:1d.7: irq 209, io mem 0xfebffc00
[17179579.256000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.256000] usb usb5: configuration #1 chosen from 1 choice
[17179579.256000] hub 5-0:1.0: USB hub found
[17179579.256000] hub 5-0:1.0: 8 ports detected
[17179579.408000] Attempting manual resume
[17179579.420000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179579.420000] EXT3-fs: write access will be enabled during recovery.
[17179579.700000] usb 1-1: device not accepting address 2, error -71
[17179580.140000] kjournald starting.  Commit interval 5 seconds
[17179580.140000] EXT3-fs: recovery complete.
[17179580.140000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.180000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[17179580.360000] usb 1-1: configuration #1 chosen from 1 choice
[17179588.976000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 217
[17179588.976000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[17179589.072000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179589.164000] Floppy drive(s): fd0 is 1.44M
[17179589.176000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.184000] FDC 0 is a post-1991 82077
[17179589.208000] hw_random: RNG not detected
[17179589.212000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.256000] input: PC Speaker as /class/input/input1
[17179589.260000] usbcore: registered new driver hiddev
[17179589.292000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[17179589.292000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
[17179589.292000] usbcore: registered new driver usbhid
[17179589.292000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179589.292000] intel8x0_measure_ac97_clock: measured 54664 usecs
[17179589.292000] intel8x0: clocking to 48000
[17179589.292000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.292000] agpgart: Detected an Intel 945G Chipset.
[17179589.312000] agpgart: AGP aperture is 256M @ 0x0
[17179589.396000] parport: PnPBIOS parport detected.
[17179589.396000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179589.424000] parport0: Printer, HEWLETT-PACKARD DESKJET 895C
[17179589.456000] ts: Compaq touchscreen protocol output
[17179589.536000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 18 (level, low) -> IRQ 193
[17179589.536000] RT61: Vendor = 0x1814, Product = 0x0301 
[17179589.628000] 8139too Fast Ethernet driver 0.9.27
[17179589.628000] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 21 (level, low) -> IRQ 225
[17179589.628000] eth0: RealTek RTL8139 at 0xf88f8c00, 00:14:2a:b1:e0:61, IRQ 225
[17179589.628000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179589.644000] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[17179589.676000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179589.876000] eth0: link down
[17179589.924000] nvidia: module license 'NVIDIA' taints kernel.
[17179590.064000] RT61: RfIcType= 3
[17179590.196000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179590.196000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[17179590.196000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9746  Fri Dec 15 09:54:45 PST 2006
[17179590.296000] lp0: using parport0 (interrupt-driven).
[17179590.332000] Adding 1389580k swap on /dev/disk/by-uuid/dacf6311-3b03-4c76-88ac-4a25f02ce1b0.  Priority:-1 extents:1 across:1389580k
[17179590.400000] EXT3 FS on sda2, internal journal
[17179590.520000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179590.584000] NTFS volume version 3.1.
[17179590.912000] NET: Registered protocol family 17


---

### Post by mrmonday on 2007-04-04
messages (as much as I could get, starting recently):

> 
Apr  4 12:45:55 Roberts-PC kernel: [17179586.932000] agpgart: Detected an Intel 945G Chipset.
Apr  4 12:45:55 Roberts-PC kernel: [17179586.948000] agpgart: AGP aperture is 256M @ 0x0
Apr  4 12:45:55 Roberts-PC kernel: [17179587.088000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  4 12:45:55 Roberts-PC kernel: [17179587.092000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  4 12:45:55 Roberts-PC kernel: [17179587.136000] hw_random: RNG not detected
Apr  4 12:45:55 Roberts-PC kernel: [17179587.180000] parport: PnPBIOS parport detected.
Apr  4 12:45:55 Roberts-PC kernel: [17179587.180000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Apr  4 12:45:55 Roberts-PC kernel: [17179587.208000] parport0: Printer, HEWLETT-PACKARD DESKJET 895C
Apr  4 12:45:55 Roberts-PC kernel: [17179587.212000] Floppy drive(s): fd0 is 1.44M
Apr  4 12:45:55 Roberts-PC kernel: [17179587.232000] FDC 0 is a post-1991 82077
Apr  4 12:45:55 Roberts-PC kernel: [17179587.328000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  4 12:45:55 Roberts-PC kernel: [17179587.480000] usbcore: registered new driver hiddev
Apr  4 12:45:55 Roberts-PC kernel: [17179587.512000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
Apr  4 12:45:55 Roberts-PC kernel: [17179587.512000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
Apr  4 12:45:55 Roberts-PC kernel: [17179587.512000] usbcore: registered new driver usbhid
Apr  4 12:45:55 Roberts-PC kernel: [17179587.512000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Apr  4 12:45:55 Roberts-PC kernel: [17179587.572000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 18 (level, low) -> IRQ 193
Apr  4 12:45:55 Roberts-PC kernel: [17179587.572000] RT61: Vendor = 0x1814, Product = 0x0301 
Apr  4 12:45:55 Roberts-PC kernel: [17179587.588000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 217
Apr  4 12:45:55 Roberts-PC kernel: [17179587.644000] 8139too Fast Ethernet driver 0.9.27
Apr  4 12:45:55 Roberts-PC kernel: [17179587.824000] nvidia: module license 'NVIDIA' taints kernel.
Apr  4 12:45:55 Roberts-PC kernel: [17179588.076000] intel8x0_measure_ac97_clock: measured 228813 usecs
Apr  4 12:45:55 Roberts-PC kernel: [17179588.076000] intel8x0: clocking to 48000
Apr  4 12:45:55 Roberts-PC kernel: [17179588.080000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
Apr  4 12:45:55 Roberts-PC kernel: [17179588.080000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9746  Fri Dec 15 09:54:45 PST 2006
Apr  4 12:45:55 Roberts-PC kernel: [17179588.080000] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 21 (level, low) -> IRQ 225
Apr  4 12:45:55 Roberts-PC kernel: [17179588.080000] eth0: RealTek RTL8139 at 0xf8a6ac00, 00:14:2a:b1:e0:61, IRQ 225
Apr  4 12:45:55 Roberts-PC kernel: [17179588.080000] ts: Compaq touchscreen protocol output
Apr  4 12:45:55 Roberts-PC kernel: [17179588.120000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
Apr  4 12:45:55 Roberts-PC kernel: [17179588.180000] eth0: link down
Apr  4 12:45:55 Roberts-PC kernel: [17179588.360000] RT61: RfIcType= 3
Apr  4 12:45:55 Roberts-PC kernel: [17179588.368000] lp0: using parport0 (interrupt-driven).
Apr  4 12:45:55 Roberts-PC kernel: [17179588.408000] Adding 1389580k swap on /dev/disk/by-uuid/dacf6311-3b03-4c76-88ac-4a25f02ce1b0.  Priority:-1 extents:1 across:1389580k
Apr  4 12:45:55 Roberts-PC kernel: [17179588.464000] EXT3 FS on sda2, internal journal
Apr  4 12:45:55 Roberts-PC kernel: [17179588.656000] NTFS driver 2.1.27 [Flags: R/O MODULE].
Apr  4 12:45:55 Roberts-PC kernel: [17179588.712000] NTFS volume version 3.1.
Apr  4 12:45:55 Roberts-PC kernel: [17179589.224000] NET: Registered protocol family 17
Apr  4 12:45:55 Roberts-PC kernel: [17179592.372000] 7b:07:8d:0d:60:7c:95:41:17:2f:53:67:34:d5:a2:ef:
Apr  4 12:45:55 Roberts-PC kernel: [17179592.372000] e4:72:08:c7:83:24:58:49:
Apr  4 12:45:55 Roberts-PC kernel: [17179592.372000] 01:4b:4c:9b:00:fb:e6:d5:
Apr  4 12:45:55 Roberts-PC kernel: [17179592.392000] 6b:40:fb:66:e0:93:da:e9:3d:e1:96:35:db:9f:d9:71:
Apr  4 12:45:55 Roberts-PC kernel: [17179592.392000] 29:25:92:e4:1b:0e:b9:a2:
Apr  4 12:45:55 Roberts-PC kernel: [17179592.392000] f8:47:84:85:fd:cd:12:45:
Apr  4 12:45:55 Roberts-PC kernel: [17179593.064000] ACPI: Power Button (FF) [PWRF]
Apr  4 12:45:55 Roberts-PC kernel: [17179593.064000] ACPI: Power Button (CM) [PWRB]
Apr  4 12:45:55 Roberts-PC kernel: [17179593.188000] pcc_acpi: loading...
Apr  4 12:45:54 Roberts-PC hpiod: 1.6.9 accepting connections at 2208... 
Apr  4 12:45:55 Roberts-PC kernel: [17179597.656000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Apr  4 12:45:55 Roberts-PC kernel: [17179597.656000] apm: disabled - APM is not SMP safe.
Apr  4 12:46:02 Roberts-PC kernel: [17179604.308000] Bluetooth: Core ver 2.8
Apr  4 12:46:02 Roberts-PC kernel: [17179604.308000] NET: Registered protocol family 31
Apr  4 12:46:02 Roberts-PC kernel: [17179604.308000] Bluetooth: HCI device and connection manager initialized
Apr  4 12:46:02 Roberts-PC kernel: [17179604.308000] Bluetooth: HCI socket layer initialized
Apr  4 12:46:02 Roberts-PC kernel: [17179604.340000] Bluetooth: L2CAP ver 2.8
Apr  4 12:46:02 Roberts-PC kernel: [17179604.340000] Bluetooth: L2CAP socket layer initialized
Apr  4 12:46:02 Roberts-PC kernel: [17179604.344000] Bluetooth: RFCOMM socket layer initialized
Apr  4 12:46:02 Roberts-PC kernel: [17179604.344000] Bluetooth: RFCOMM TTY layer initialized
Apr  4 12:46:02 Roberts-PC kernel: [17179604.344000] Bluetooth: RFCOMM ver 1.7
Apr  4 12:46:07 Roberts-PC gconfd (manager-4716): starting (version 2.16.0), pid 4716 user 'manager'
Apr  4 12:46:07 Roberts-PC gconfd (manager-4716): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  4 12:46:07 Roberts-PC gconfd (manager-4716): Resolved address "xml:readwrite:/home/manager/.gconf" to a writable configuration source at position 1
Apr  4 12:46:07 Roberts-PC gconfd (manager-4716): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  4 12:46:07 Roberts-PC gconfd (manager-4716): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  4 12:46:07 Roberts-PC gconfd (manager-4716): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  4 12:46:12 Roberts-PC gconfd (manager-4716): Resolved address "xml:readwrite:/home/manager/.gconf" to a writable configuration source at position 0
Apr  4 12:47:37 Roberts-PC syslogd 1.4.1#18ubuntu6: restart.
Apr  4 12:47:37 Roberts-PC kernel: Inspecting /boot/System.map-2.6.17-11-generic
Apr  4 12:47:37 Roberts-PC kernel: Loaded 22866 symbols from /boot/System.map-2.6.17-11-generic.
Apr  4 12:47:37 Roberts-PC kernel: Symbols match kernel version 2.6.17.
Apr  4 12:47:37 Roberts-PC kernel: No module symbols loaded - kernel modules not enabled. 
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] BIOS-provided physical RAM map:
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000007ffc0000 (usable)
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000]  BIOS-e820: 000000007ffc0000 - 000000007ffce000 (ACPI data)
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000]  BIOS-e820: 000000007ffce000 - 000000007fff0000 (ACPI NVS)
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] 1151MB HIGHMEM available.
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] 896MB LOWMEM available.
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] found SMP MP-table at 000ff780
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] DMI 2.3 present.
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x808
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] Processor #0 15:4 APIC version 20
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] Processor #1 15:4 APIC version 20
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] Using ACPI (MADT) for SMP configuration information
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] Built 1 zonelists
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] Enabling fast FPU save and restore... done.
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] Enabling unmasked SIMD FPU exception support... done.
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] Initializing CPU#0
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] Detected 2993.114 MHz processor.
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] Using pmtmr for high-res timesource
Apr  4 12:47:37 Roberts-PC kernel: [17179569.184000] Console: colour VGA+ 80x25
Apr  4 12:47:37 Roberts-PC kernel: [17179572.556000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr  4 12:47:37 Roberts-PC kernel: [17179572.556000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  4 12:47:37 Roberts-PC kernel: [17179572.628000] Memory: 2069208k/2096896k available (1911k kernel code, 26352k reserved, 1073k data, 308k init, 1179392k highmem)
Apr  4 12:47:37 Roberts-PC kernel: [17179572.628000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr  4 12:47:37 Roberts-PC kernel: [17179572.708000] Calibrating delay using timer specific routine.. 5992.91 BogoMIPS (lpj=11985836)
Apr  4 12:47:37 Roberts-PC kernel: [17179572.708000] Security Framework v1.0.0 initialized
Apr  4 12:47:37 Roberts-PC kernel: [17179572.708000] SELinux:  Disabled at boot.
Apr  4 12:47:37 Roberts-PC kernel: [17179572.708000] Mount-cache hash table entries: 512
Apr  4 12:47:37 Roberts-PC kernel: [17179572.708000] monitor/mwait feature present.
Apr  4 12:47:37 Roberts-PC kernel: [17179572.708000] using mwait in idle threads.
Apr  4 12:47:37 Roberts-PC kernel: [17179572.708000] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr  4 12:47:37 Roberts-PC kernel: [17179572.708000] CPU: L2 cache: 2048K
Apr  4 12:47:37 Roberts-PC kernel: [17179572.708000] CPU: Hyper-Threading is disabled
Apr  4 12:47:37 Roberts-PC kernel: [17179572.708000] Checking 'hlt' instruction... OK.
Apr  4 12:47:37 Roberts-PC kernel: [17179572.724000] SMP alternatives: switching to UP code
Apr  4 12:47:37 Roberts-PC kernel: [17179572.724000] checking if image is initramfs... it is
Apr  4 12:47:37 Roberts-PC kernel: [17179573.148000] Freeing initrd memory: 5326k freed
Apr  4 12:47:37 Roberts-PC kernel: [17179573.148000] ACPI: Core revision 20060707
Apr  4 12:47:37 Roberts-PC kernel: [17179573.148000] ACPI: Looking for DSDT ... not found!
Apr  4 12:47:37 Roberts-PC kernel: [17179573.164000] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
Apr  4 12:47:37 Roberts-PC kernel: [17179573.164000] SMP alternatives: switching to SMP code
Apr  4 12:47:37 Roberts-PC kernel: [17179573.164000] Booting processor 1/1 eip 3000
Apr  4 12:47:37 Roberts-PC kernel: [17179573.172000] Initializing CPU#1
Apr  4 12:47:37 Roberts-PC kernel: [17179573.256000] Calibrating delay using timer specific routine.. 5985.52 BogoMIPS (lpj=11971054)
Apr  4 12:47:37 Roberts-PC kernel: [17179573.256000] monitor/mwait feature present.
Apr  4 12:47:37 Roberts-PC kernel: [17179573.256000] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr  4 12:47:37 Roberts-PC kernel: [17179573.256000] CPU: L2 cache: 2048K
Apr  4 12:47:37 Roberts-PC kernel: [17179573.256000] CPU: Hyper-Threading is disabled
Apr  4 12:47:37 Roberts-PC kernel: [17179573.256000] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
Apr  4 12:47:37 Roberts-PC kernel: [17179573.256000] Total of 2 processors activated (11978.44 BogoMIPS).
Apr  4 12:47:37 Roberts-PC kernel: [17179573.256000] ENABLING IO-APIC IRQs
Apr  4 12:47:37 Roberts-PC kernel: [17179573.256000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  4 12:47:37 Roberts-PC kernel: [17179573.400000] checking TSC synchronization across 2 CPUs: 
Apr  4 12:47:37 Roberts-PC kernel: [17179573.404000] Brought up 2 CPUs
Apr  4 12:47:37 Roberts-PC kernel: [17179573.476000] migration_cost=4000
Apr  4 12:47:37 Roberts-PC kernel: [17179573.476000] NET: Registered protocol family 16
Apr  4 12:47:37 Roberts-PC kernel: [17179573.476000] EISA bus registered
Apr  4 12:47:37 Roberts-PC kernel: [17179573.476000] ACPI: bus type pci registered
Apr  4 12:47:37 Roberts-PC kernel: [17179573.476000] PCI: BIOS Bug: MCFG area at f0000000 is not E820-reserved
Apr  4 12:47:37 Roberts-PC kernel: [17179573.476000] PCI: Not using MMCONFIG.
Apr  4 12:47:37 Roberts-PC kernel: [17179573.476000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
Apr  4 12:47:37 Roberts-PC kernel: [17179573.476000] PCI: Using configuration type 1
Apr  4 12:47:37 Roberts-PC kernel: [17179573.476000] Setting up standard PCI resources
Apr  4 12:47:37 Roberts-PC kernel: [17179573.516000] ACPI: Interpreter enabled
Apr  4 12:47:37 Roberts-PC kernel: [17179573.516000] ACPI: Using IOAPIC for interrupt routing
Apr  4 12:47:37 Roberts-PC kernel: [17179573.516000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  4 12:47:37 Roberts-PC kernel: [17179573.520000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
Apr  4 12:47:37 Roberts-PC kernel: [17179573.520000] PCI: Transparent bridge - 0000:00:1e.0
Apr  4 12:47:37 Roberts-PC kernel: [17179573.544000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Apr  4 12:47:37 Roberts-PC kernel: [17179573.544000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Apr  4 12:47:37 Roberts-PC kernel: [17179573.544000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Apr  4 12:47:37 Roberts-PC kernel: [17179573.544000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Apr  4 12:47:37 Roberts-PC kernel: [17179573.544000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Apr  4 12:47:37 Roberts-PC kernel: [17179573.544000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Apr  4 12:47:37 Roberts-PC kernel: [17179573.544000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Apr  4 12:47:37 Roberts-PC kernel: [17179573.544000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Apr  4 12:47:37 Roberts-PC kernel: [17179573.544000] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr  4 12:47:37 Roberts-PC kernel: [17179573.544000] pnp: PnP ACPI init
Apr  4 12:47:37 Roberts-PC kernel: [17179573.548000] pnp: PnP ACPI: found 16 devices
Apr  4 12:47:37 Roberts-PC kernel: [17179573.548000] PnPBIOS: Disabled by ACPI PNP
Apr  4 12:47:37 Roberts-PC kernel: [17179573.548000] PCI: Using ACPI for IRQ routing
Apr  4 12:47:37 Roberts-PC kernel: [17179573.548000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr  4 12:47:37 Roberts-PC kernel: [17179573.556000] pnp: 00:0c: ioport range 0x290-0x29f has been reserved
Apr  4 12:47:37 Roberts-PC kernel: [17179573.556000] PCI: Bridge: 0000:00:01.0
Apr  4 12:47:37 Roberts-PC kernel: [17179573.556000]   IO window: disabled.
Apr  4 12:47:37 Roberts-PC kernel: [17179573.556000]   MEM window: fa900000-fe9fffff
Apr  4 12:47:37 Roberts-PC kernel: [17179573.556000]   PREFETCH window: cff00000-efefffff
Apr  4 12:47:37 Roberts-PC kernel: [17179573.556000] PCI: Bridge: 0000:00:1e.0
Apr  4 12:47:37 Roberts-PC kernel: [17179573.556000]   IO window: c000-cfff
Apr  4 12:47:37 Roberts-PC kernel: [17179573.556000]   MEM window: fea00000-feafffff
Apr  4 12:47:37 Roberts-PC kernel: [17179573.556000]   PREFETCH window: disabled.
Apr  4 12:47:37 Roberts-PC kernel: [17179573.556000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
Apr  4 12:47:37 Roberts-PC kernel: [17179573.556000] NET: Registered protocol family 2
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] TCP: Hash tables configured (established 262144 bind 65536)
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] TCP reno registered
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] audit: initializing netlink socket (disabled)
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] audit(1175690838.596:1): initialized
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] highmem bounce pool size: 64 pages
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] VFS: Disk quotas dquot_6.5.1
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] Initializing Cryptographic API
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] io scheduler noop registered
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] io scheduler anticipatory registered
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] io scheduler deadline registered
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] io scheduler cfq registered (default)
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] assign_interrupt_mode Found MSI capability
Apr  4 12:47:37 Roberts-PC kernel: [17179573.596000] isapnp: Scanning for PnP cards...
Apr  4 12:47:37 Roberts-PC kernel: [17179573.952000] isapnp: No Plug & Play device found
Apr  4 12:47:37 Roberts-PC kernel: [17179573.976000] Real Time Clock Driver v1.12ac
Apr  4 12:47:37 Roberts-PC kernel: [17179573.976000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr  4 12:47:37 Roberts-PC kernel: [17179573.976000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  4 12:47:37 Roberts-PC kernel: [17179573.976000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr  4 12:47:37 Roberts-PC kernel: [17179573.976000] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr  4 12:47:37 Roberts-PC kernel: [17179573.976000] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  4 12:47:37 Roberts-PC kernel: [17179573.976000] mice: PS/2 mouse device common for all mice
Apr  4 12:47:37 Roberts-PC kernel: [17179573.976000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr  4 12:47:37 Roberts-PC kernel: [17179573.976000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr  4 12:47:37 Roberts-PC kernel: [17179573.976000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr  4 12:47:37 Roberts-PC kernel: [17179573.980000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Apr  4 12:47:37 Roberts-PC kernel: [17179573.980000] PNP: PS/2 controller doesn't have AUX irq; using default 12
Apr  4 12:47:37 Roberts-PC kernel: [17179573.980000] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr  4 12:47:37 Roberts-PC kernel: [17179573.980000] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  4 12:47:37 Roberts-PC kernel: [17179573.980000] EISA: Probing bus 0 at eisa.0
Apr  4 12:47:37 Roberts-PC kernel: [17179573.980000] EISA: Detected 0 cards.
Apr  4 12:47:37 Roberts-PC kernel: [17179573.980000] TCP bic registered
Apr  4 12:47:37 Roberts-PC kernel: [17179573.980000] NET: Registered protocol family 1
Apr  4 12:47:37 Roberts-PC kernel: [17179573.980000] NET: Registered protocol family 8
Apr  4 12:47:37 Roberts-PC kernel: [17179573.980000] NET: Registered protocol family 20
Apr  4 12:47:37 Roberts-PC kernel: [17179573.980000] Starting balanced_irq
Apr  4 12:47:37 Roberts-PC kernel: [17179573.980000] Using IPI No-Shortcut mode
Apr  4 12:47:37 Roberts-PC kernel: [17179573.980000] ACPI: (supports S0 S1 S3 S4 S5)
Apr  4 12:47:37 Roberts-PC kernel: [17179573.980000] Freeing unused kernel memory: 308k freed
Apr  4 12:47:37 Roberts-PC kernel: [17179574.260000] input: AT Translated Set 2 keyboard as /class/input/input0
Apr  4 12:47:37 Roberts-PC kernel: [17179575.048000] Capability LSM initialized
Apr  4 12:47:37 Roberts-PC kernel: [17179575.084000] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node dffed2d4), AE_BAD_HEADER
Apr  4 12:47:37 Roberts-PC kernel: [17179575.084000] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr  4 12:47:37 Roberts-PC kernel: [17179575.084000] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PDC] (Node dffed84c), AE_BAD_HEADER
Apr  4 12:47:37 Roberts-PC kernel: [17179575.084000] ACPI: Processor [CPU2] (supports 8 throttling states)
Apr  4 12:47:37 Roberts-PC kernel: [17179575.084000] ACPI: Thermal Zone [THRM] (-269 C)
Apr  4 12:47:37 Roberts-PC kernel: [17179575.748000] ICH7: IDE controller at PCI slot 0000:00:1f.1
Apr  4 12:47:37 Roberts-PC kernel: [17179575.748000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 193
Apr  4 12:47:37 Roberts-PC kernel: [17179575.748000] ICH7: chipset revision 1
Apr  4 12:47:37 Roberts-PC kernel: [17179575.748000] ICH7: not 100%% native mode: will probe irqs later
Apr  4 12:47:37 Roberts-PC kernel: [17179575.748000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
Apr  4 12:47:37 Roberts-PC kernel: [17179575.748000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
Apr  4 12:47:37 Roberts-PC kernel: [17179576.684000] hda: ASUS DRW-1608P2S, ATAPI CD/DVD-ROM drive
Apr  4 12:47:37 Roberts-PC kernel: [17179577.504000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr  4 12:47:37 Roberts-PC kernel: [17179578.088000] hda: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2000kB Cache, UDMA(66)
Apr  4 12:47:37 Roberts-PC kernel: [17179578.088000] Uniform CD-ROM driver Revision: 3.20
Apr  4 12:47:37 Roberts-PC kernel: [17179578.192000] SCSI subsystem initialized
Apr  4 12:47:37 Roberts-PC kernel: [17179578.196000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 201
Apr  4 12:47:37 Roberts-PC kernel: [17179578.196000] ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE882 bmdma 0xE400 irq 201
Apr  4 12:47:37 Roberts-PC kernel: [17179578.196000] ata2: SATA max UDMA/133 cmd 0xE800 ctl 0xE482 bmdma 0xE408 irq 201
Apr  4 12:47:37 Roberts-PC kernel: [17179578.360000] ata1: dev 0 ATA-7, max UDMA/133, 160086528 sectors: LBA48
Apr  4 12:47:37 Roberts-PC kernel: [17179578.368000] ata1: dev 0 configured for UDMA/133
Apr  4 12:47:37 Roberts-PC kernel: [17179578.368000] scsi0 : ata_piix
Apr  4 12:47:37 Roberts-PC kernel: [17179578.532000] scsi1 : ata_piix
Apr  4 12:47:37 Roberts-PC kernel: [17179578.532000]   Vendor: ATA       Model: Maxtor 6V080E0    Rev: VA11
Apr  4 12:47:37 Roberts-PC kernel: [17179578.532000]   Type:   Direct-Access                      ANSI SCSI revision: 05
Apr  4 12:47:37 Roberts-PC kernel: [17179578.540000] SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
Apr  4 12:47:37 Roberts-PC kernel: [17179578.540000] sda: Write Protect is off
Apr  4 12:47:37 Roberts-PC kernel: [17179578.540000] SCSI device sda: drive cache: write back
Apr  4 12:47:37 Roberts-PC kernel: [17179578.540000] SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
Apr  4 12:47:37 Roberts-PC kernel: [17179578.540000] sda: Write Protect is off
Apr  4 12:47:37 Roberts-PC kernel: [17179578.540000] SCSI device sda: drive cache: write back
Apr  4 12:47:37 Roberts-PC kernel: [17179578.540000]  sda: sda1 sda2 sda3 < sda5 >
Apr  4 12:47:37 Roberts-PC kernel: [17179578.572000] sd 0:0:0:0: Attached scsi disk sda
Apr  4 12:47:37 Roberts-PC kernel: [17179578.820000] usbcore: registered new driver usbfs
Apr  4 12:47:37 Roberts-PC kernel: [17179578.820000] usbcore: registered new driver hub
Apr  4 12:47:37 Roberts-PC kernel: [17179578.824000] USB Universal Host Controller Interface driver v3.0
Apr  4 12:47:37 Roberts-PC kernel: [17179578.824000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 209
Apr  4 12:47:37 Roberts-PC kernel: [17179578.824000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr  4 12:47:37 Roberts-PC kernel: [17179578.824000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr  4 12:47:37 Roberts-PC kernel: [17179578.824000] uhci_hcd 0000:00:1d.0: irq 209, io base 0x0000e080
Apr  4 12:47:37 Roberts-PC kernel: [17179578.824000] usb usb1: configuration #1 chosen from 1 choice
Apr  4 12:47:37 Roberts-PC kernel: [17179578.824000] hub 1-0:1.0: USB hub found
Apr  4 12:47:37 Roberts-PC kernel: [17179578.824000] hub 1-0:1.0: 2 ports detected
Apr  4 12:47:37 Roberts-PC kernel: [17179578.928000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 201
Apr  4 12:47:37 Roberts-PC kernel: [17179578.928000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr  4 12:47:37 Roberts-PC kernel: [17179578.928000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr  4 12:47:37 Roberts-PC kernel: [17179578.928000] uhci_hcd 0000:00:1d.1: irq 201, io base 0x0000e000
Apr  4 12:47:37 Roberts-PC kernel: [17179578.928000] usb usb2: configuration #1 chosen from 1 choice
Apr  4 12:47:37 Roberts-PC kernel: [17179578.928000] hub 2-0:1.0: USB hub found
Apr  4 12:47:37 Roberts-PC kernel: [17179578.928000] hub 2-0:1.0: 2 ports detected
Apr  4 12:47:37 Roberts-PC kernel: [17179579.032000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 193
Apr  4 12:47:37 Roberts-PC kernel: [17179579.032000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr  4 12:47:37 Roberts-PC kernel: [17179579.032000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr  4 12:47:37 Roberts-PC kernel: [17179579.032000] uhci_hcd 0000:00:1d.2: irq 193, io base 0x0000dc00
Apr  4 12:47:37 Roberts-PC kernel: [17179579.032000] usb usb3: configuration #1 chosen from 1 choice
Apr  4 12:47:37 Roberts-PC kernel: [17179579.032000] hub 3-0:1.0: USB hub found
Apr  4 12:47:37 Roberts-PC kernel: [17179579.032000] hub 3-0:1.0: 2 ports detected
Apr  4 12:47:37 Roberts-PC kernel: [17179579.136000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
Apr  4 12:47:37 Roberts-PC kernel: [17179579.136000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Apr  4 12:47:37 Roberts-PC kernel: [17179579.136000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Apr  4 12:47:37 Roberts-PC kernel: [17179579.136000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000d880
Apr  4 12:47:37 Roberts-PC kernel: [17179579.136000] usb usb4: configuration #1 chosen from 1 choice
Apr  4 12:47:37 Roberts-PC kernel: [17179579.136000] hub 4-0:1.0: USB hub found
Apr  4 12:47:37 Roberts-PC kernel: [17179579.136000] hub 4-0:1.0: 2 ports detected
Apr  4 12:47:37 Roberts-PC kernel: [17179579.168000] usb 1-1: new low speed USB device using uhci_hcd and address 2
Apr  4 12:47:37 Roberts-PC kernel: [17179579.252000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 209
Apr  4 12:47:37 Roberts-PC kernel: [17179579.252000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr  4 12:47:37 Roberts-PC kernel: [17179579.252000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Apr  4 12:47:37 Roberts-PC kernel: [17179579.252000] ehci_hcd 0000:00:1d.7: debug port 1
Apr  4 12:47:37 Roberts-PC kernel: [17179579.252000] ehci_hcd 0000:00:1d.7: irq 209, io mem 0xfebffc00
Apr  4 12:47:37 Roberts-PC kernel: [17179579.256000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr  4 12:47:37 Roberts-PC kernel: [17179579.256000] usb usb5: configuration #1 chosen from 1 choice
Apr  4 12:47:37 Roberts-PC kernel: [17179579.256000] hub 5-0:1.0: USB hub found
Apr  4 12:47:37 Roberts-PC kernel: [17179579.256000] hub 5-0:1.0: 8 ports detected
Apr  4 12:47:37 Roberts-PC kernel: [17179579.408000] Attempting manual resume
Apr  4 12:47:37 Roberts-PC kernel: [17179579.420000] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr  4 12:47:37 Roberts-PC kernel: [17179579.420000] EXT3-fs: write access will be enabled during recovery.
Apr  4 12:47:37 Roberts-PC kernel: [17179580.140000] kjournald starting.  Commit interval 5 seconds
Apr  4 12:47:37 Roberts-PC kernel: [17179580.140000] EXT3-fs: recovery complete.
Apr  4 12:47:37 Roberts-PC kernel: [17179580.140000] EXT3-fs: mounted filesystem with ordered data mode.
Apr  4 12:47:37 Roberts-PC kernel: [17179580.180000] usb 1-1: new low speed USB device using uhci_hcd and address 4
Apr  4 12:47:37 Roberts-PC kernel: [17179580.360000] usb 1-1: configuration #1 chosen from 1 choice
Apr  4 12:47:37 Roberts-PC kernel: [17179588.976000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 217
Apr  4 12:47:37 Roberts-PC kernel: [17179589.072000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  4 12:47:37 Roberts-PC kernel: [17179589.164000] Floppy drive(s): fd0 is 1.44M
Apr  4 12:47:37 Roberts-PC kernel: [17179589.176000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  4 12:47:37 Roberts-PC kernel: [17179589.184000] FDC 0 is a post-1991 82077
Apr  4 12:47:37 Roberts-PC kernel: [17179589.208000] hw_random: RNG not detected
Apr  4 12:47:37 Roberts-PC kernel: [17179589.212000] Linux agpgart interface v0.101 (c) Dave Jones
Apr  4 12:47:37 Roberts-PC kernel: [17179589.256000] input: PC Speaker as /class/input/input1
Apr  4 12:47:37 Roberts-PC kernel: [17179589.260000] usbcore: registered new driver hiddev
Apr  4 12:47:37 Roberts-PC kernel: [17179589.292000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
Apr  4 12:47:37 Roberts-PC kernel: [17179589.292000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
Apr  4 12:47:37 Roberts-PC kernel: [17179589.292000] usbcore: registered new driver usbhid
Apr  4 12:47:37 Roberts-PC kernel: [17179589.292000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Apr  4 12:47:37 Roberts-PC kernel: [17179589.292000] intel8x0_measure_ac97_clock: measured 54664 usecs
Apr  4 12:47:37 Roberts-PC kernel: [17179589.292000] intel8x0: clocking to 48000
Apr  4 12:47:37 Roberts-PC kernel: [17179589.292000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  4 12:47:37 Roberts-PC kernel: [17179589.292000] agpgart: Detected an Intel 945G Chipset.
Apr  4 12:47:37 Roberts-PC kernel: [17179589.312000] agpgart: AGP aperture is 256M @ 0x0
Apr  4 12:47:37 Roberts-PC kernel: [17179589.396000] parport: PnPBIOS parport detected.
Apr  4 12:47:37 Roberts-PC kernel: [17179589.396000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Apr  4 12:47:37 Roberts-PC kernel: [17179589.424000] parport0: Printer, HEWLETT-PACKARD DESKJET 895C
Apr  4 12:47:37 Roberts-PC kernel: [17179589.456000] ts: Compaq touchscreen protocol output
Apr  4 12:47:37 Roberts-PC kernel: [17179589.536000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 18 (level, low) -> IRQ 193
Apr  4 12:47:37 Roberts-PC kernel: [17179589.536000] RT61: Vendor = 0x1814, Product = 0x0301 
Apr  4 12:47:37 Roberts-PC kernel: [17179589.628000] 8139too Fast Ethernet driver 0.9.27
Apr  4 12:47:37 Roberts-PC kernel: [17179589.628000] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 21 (level, low) -> IRQ 225
Apr  4 12:47:37 Roberts-PC kernel: [17179589.628000] eth0: RealTek RTL8139 at 0xf88f8c00, 00:14:2a:b1:e0:61, IRQ 225
Apr  4 12:47:37 Roberts-PC kernel: [17179589.676000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
Apr  4 12:47:37 Roberts-PC kernel: [17179589.876000] eth0: link down
Apr  4 12:47:37 Roberts-PC kernel: [17179589.924000] nvidia: module license 'NVIDIA' taints kernel.
Apr  4 12:47:37 Roberts-PC kernel: [17179590.064000] RT61: RfIcType= 3
Apr  4 12:47:37 Roberts-PC kernel: [17179590.196000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
Apr  4 12:47:37 Roberts-PC kernel: [17179590.196000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9746  Fri Dec 15 09:54:45 PST 2006
Apr  4 12:47:37 Roberts-PC kernel: [17179590.296000] lp0: using parport0 (interrupt-driven).
Apr  4 12:47:37 Roberts-PC kernel: [17179590.332000] Adding 1389580k swap on /dev/disk/by-uuid/dacf6311-3b03-4c76-88ac-4a25f02ce1b0.  Priority:-1 extents:1 across:1389580k
Apr  4 12:47:37 Roberts-PC kernel: [17179590.400000] EXT3 FS on sda2, internal journal
Apr  4 12:47:37 Roberts-PC kernel: [17179590.520000] NTFS driver 2.1.27 [Flags: R/O MODULE].
Apr  4 12:47:37 Roberts-PC kernel: [17179590.584000] NTFS volume version 3.1.
Apr  4 12:47:37 Roberts-PC kernel: [17179590.912000] NET: Registered protocol family 17
Apr  4 12:47:37 Roberts-PC kernel: [17179594.688000] ACPI: Power Button (FF) [PWRF]
Apr  4 12:47:37 Roberts-PC kernel: [17179594.688000] ACPI: Power Button (CM) [PWRB]
Apr  4 12:47:37 Roberts-PC kernel: [17179594.832000] pcc_acpi: loading...
Apr  4 12:47:37 Roberts-PC kernel: [17179596.088000] e7:6d:7a:b0:50:3f:30:d5:c7:9f:b6:2e:1a:d2:05:03:
Apr  4 12:47:37 Roberts-PC kernel: [17179596.088000] 49:70:58:67:d7:2a:33:93:
Apr  4 12:47:37 Roberts-PC kernel: [17179596.088000] 51:8e:21:b4:74:6f:b4:51:
Apr  4 12:47:37 Roberts-PC kernel: [17179596.104000] c8:c7:4f:6b:88:4c:9e:39:8e:68:17:47:a1:4b:01:bb:
Apr  4 12:47:37 Roberts-PC kernel: [17179596.104000] 8b:98:4d:df:a5:f4:ac:4c:
Apr  4 12:47:37 Roberts-PC kernel: [17179596.104000] 59:d5:53:07:c1:12:fd:a9:
Apr  4 12:47:40 Roberts-PC hpiod: 1.6.9 accepting connections at 2208... 
Apr  4 12:47:41 Roberts-PC kernel: [17179599.212000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Apr  4 12:47:41 Roberts-PC kernel: [17179599.212000] apm: disabled - APM is not SMP safe.
Apr  4 12:47:46 Roberts-PC kernel: [17179605.060000] Bluetooth: Core ver 2.8
Apr  4 12:47:46 Roberts-PC kernel: [17179605.060000] NET: Registered protocol family 31
Apr  4 12:47:46 Roberts-PC kernel: [17179605.060000] Bluetooth: HCI device and connection manager initialized
Apr  4 12:47:46 Roberts-PC kernel: [17179605.060000] Bluetooth: HCI socket layer initialized
Apr  4 12:47:46 Roberts-PC kernel: [17179605.092000] Bluetooth: L2CAP ver 2.8
Apr  4 12:47:46 Roberts-PC kernel: [17179605.092000] Bluetooth: L2CAP socket layer initialized
Apr  4 12:47:46 Roberts-PC kernel: [17179605.096000] Bluetooth: RFCOMM socket layer initialized
Apr  4 12:47:46 Roberts-PC kernel: [17179605.096000] Bluetooth: RFCOMM TTY layer initialized
Apr  4 12:47:46 Roberts-PC kernel: [17179605.096000] Bluetooth: RFCOMM ver 1.7
Apr  4 12:47:52 Roberts-PC gconfd (manager-4696): starting (version 2.16.0), pid 4696 user 'manager'
Apr  4 12:47:52 Roberts-PC gconfd (manager-4696): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  4 12:47:52 Roberts-PC gconfd (manager-4696): Resolved address "xml:readwrite:/home/manager/.gconf" to a writable configuration source at position 1
Apr  4 12:47:52 Roberts-PC gconfd (manager-4696): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  4 12:47:52 Roberts-PC gconfd (manager-4696): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  4 12:47:52 Roberts-PC gconfd (manager-4696): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  4 12:47:55 Roberts-PC kernel: [17179614.092000] 97:ab:e8:21:24:dc:86:3d:74:52:5e:bd:2b:3b:9f:69:
Apr  4 12:47:55 Roberts-PC kernel: [17179614.092000] cf:95:11:f6:75:d1:f8:b8:
Apr  4 12:47:55 Roberts-PC kernel: [17179614.092000] 68:c4:6e:dd:18:d8:9f:d0:
Apr  4 12:47:55 Roberts-PC kernel: [17179614.112000] 84:8f:07:57:80:cf:92:b4:fa:19:e6:78:96:fb:71:0e:
Apr  4 12:47:55 Roberts-PC kernel: [17179614.112000] c7:da:3f:3a:cf:4d:34:a0:
Apr  4 12:47:55 Roberts-PC kernel: [17179614.112000] c1:93:fd:b4:6a:6e:52:c9:
Apr  4 12:47:57 Roberts-PC gconfd (manager-4696): Resolved address "xml:readwrite:/home/manager/.gconf" to a writable configuration source at position 0
Apr  4 12:48:03 Roberts-PC kernel: [17179621.464000] 97:e8:de:51:81:fe:79:c2:69:30:ca:83:db:d3:7c:d4:
Apr  4 12:48:03 Roberts-PC kernel: [17179621.464000] 71:f6:d8:f6:d6:a9:4a:7d:
Apr  4 12:48:03 Roberts-PC kernel: [17179621.464000] 93:23:5a:9f:be:d9:dd:9e:
Apr  4 12:48:03 Roberts-PC kernel: [17179621.484000] e1:2e:05:48:57:60:f7:a1:9b:f9:28:a3:4d:40:09:fc:
Apr  4 12:48:03 Roberts-PC kernel: [17179621.484000] de:af:05:75:67:f9:ea:77:
Apr  4 12:48:03 Roberts-PC kernel: [17179621.484000] 8b:2c:cf:38:39:64:a2:33:
Apr  4 12:52:07 Roberts-PC kernel: [17179868.256000] 2b:ed:bb:26:53:4d:5c:f4:d6:0c:b1:bc:70:2d:e1:2a:
Apr  4 12:52:07 Roberts-PC kernel: [17179868.256000] 93:55:53:33:16:9e:b0:83:
Apr  4 12:52:07 Roberts-PC kernel: [17179868.256000] de:3e:6e:cb:87:e4:ab:e9:
Apr  4 12:52:07 Roberts-PC kernel: [17179868.276000] 43:32:e2:e7:49:5c:4e:b3:c0:9e:cb:af:5f:81:6f:df:
Apr  4 12:52:07 Roberts-PC kernel: [17179868.276000] a6:cb:15:f1:ba:c2:85:ce:
Apr  4 12:52:07 Roberts-PC kernel: [17179868.276000] fd:cf:e7:55:d6:2c:32:31:
Apr  4 12:52:09 Roberts-PC kernel: [17179871.120000] 2d:be:68:fb:64:ac:5b:c8:a6:a5:66:05:af:b5:cc:70:
Apr  4 12:52:09 Roberts-PC kernel: [17179871.120000] ee:9f:43:94:6d:1b:08:68:
Apr  4 12:52:09 Roberts-PC kernel: [17179871.120000] ea:04:61:a2:09:e0:0b:8e:
Apr  4 12:52:09 Roberts-PC kernel: [17179871.136000] 2d:ce:48:50:09:3a:04:ab:b0:d0:dd:97:11:46:87:9a:
Apr  4 12:52:09 Roberts-PC kernel: [17179871.136000] 97:af:86:c4:2a:3d:5a:4a:
Apr  4 12:52:09 Roberts-PC kernel: [17179871.136000] 6b:22:47:be:35:0d:5a:cd:
Apr  4 13:07:34 Roberts-PC -- MARK --


---

### Post by 1/0 on 2007-04-04
Well, I don't know about these errors:

[17179575.084000] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node dffed2d4), AE_BAD_HEADER

[17179579.700000] usb 1-1: device not accepting address 2, error -71

It could be many things that are bad. What kind of computer do you have (laptop, graphics card, cpu, NIC)? 

I know that bling bling on the desktop can cause this, just as the screenserver or the graphics driver. I'm not seing that many errors though... Any log from the time when it crashed?

---

### Post by rjfioravanti on 2007-04-04
I have a question about this /var/log directory

I am going to be installing ubuntu on three computer this weekend, and I've already started on the first one and it is already having issues (completely freezing)

So I was interested when I saw your message about diagnosing things from here... however there is lots of stuff in /var/log

Can someone give me some information about how I should approach all these files and messages in this directory when I am trying to diagnose a problem, or point me to some good reading / tutorial on it?

I guess I just want to know which files / logs i should be looking at for what kind of problem, and what kind of errors / messages I should be looking for in these files. 

Thanks

---

### Post by Punker on 2007-04-04
> **mrmonday said:**
> Hi Everyone,

Recently, for no apparent reason, when I am in Ubuntu, my PC just restarts randomly, or it freezes and doesn't respond to anything (except occasionally mouse movements). Is there any way I can monitor what's going on, so I can try and diagnose the problem? Also (and more importantly) how can I solve this problem.

I am very close to doing something I really don't want to do (go back to windows)....

Thanks for any help.

sound's to me your hanging out with the wrong people! I have done this in real life many times I'm still a bit of newbie with this I try not to do too much I see what I get 
I spend most of my time reading in the Ubuntu forum's  check your logs I also feel "windwos" is a waste of my time. dont worry be happy its only a computer

---

### Post by mrmonday on 2007-04-04
> **1/0 said:**
> Well, I don't know about these errors:

[17179575.084000] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node dffed2d4), AE_BAD_HEADER

[17179579.700000] usb 1-1: device not accepting address 2, error -71

It could be many things that are bad. What kind of computer do you have (laptop, graphics card, cpu, NIC)? 

I know that bling bling on the desktop can cause this, just as the screenserver or the graphics driver. I'm not seing that many errors though... Any log from the time when it crashed?

I am using a desktop PC:

Intel Pentium 4 630 (3.0ghz, HT)
2GB Ram
nVidia Geforce 7300GS (256mb onboard, 512 with system
Gigabyte AirCruiserG GN-WP01GS Wireless card

I am using beryl (0.2) and my graphics card driver is version 1.0-9746.

It has crashed several times during today, so there should be some sort of log in there.

EDIT: I will post the rest of messages, from today, as  couldn't fit all of todays on.

---

### Post by mrmonday on 2007-04-04
Here is the rest (before the last) of messages.  - Too long again. I will save it in openoffice, and attach it - yet again won't do it... I have archived all of the files, and attached them.

---

### Post by 67GTA on 2007-04-04
I actually downgraded from Egdy to Dapper because Edgy was too buggy for me. Edgy is still considered to be an unstable/testing version. Beryl is also still in an unstable/testing state. You really can't expect everything to run perfectly all the time. If you like Ubuntu, then I would suggest trying Dapper before giving up.

---

### Post by 1/0 on 2007-04-04
> **rjfioravanti said:**
> I have a question about this /var/log directory

I am going to be installing ubuntu on three computer this weekend, and I've already started on the first one and it is already having issues (completely freezing)

So I was interested when I saw your message about diagnosing things from here... however there is lots of stuff in /var/log

Can someone give me some information about how I should approach all these files and messages in this directory when I am trying to diagnose a problem, or point me to some good reading / tutorial on it?

I guess I just want to know which files / logs i should be looking at for what kind of problem, and what kind of errors / messages I should be looking for in these files. 

Thanks

Well, I don't know any tutorial but it should be explained in many general Linux books. What you want to control is configured and done by syslog and placed in /var/log/. 

dmesg contains most info from the kernel

messages contains information about most stuff from the OS

Xorg.0.log contains the log from xorg

syslog contains system related information

the cups directory contains various logs about the printing system CUPS

Many of them have the same info and the logs are compressed after a while by logrotate to save disk space. When you have an error note the exact time! That way you can check what happened then in the logs, or what was intiated just before. 

Xorg.0.log can be handy when xorg behaves weired. You can see if the graphics driver is causing problems aso. Lines with EE are often a bad thing; WW and !! can be interesting as well.

Its a bit of a detective work to find the causes of the problem. I find most of mine by searching for keywords in Google or various forums. If you search for xorg freezes you will find irrelevant stuff but if you, for instance, search for "ACPI Error Method parse/execution failed AE_BAD_HEADER" you'll find more relevant information. Those keywords can be important. 

I've found that ACPI can cause problems when installing some computers. Using the noacpi or acpi=off when installing can solve that. (I'm not sure if you need the alternative install CD for that.)

Hope that helps

---

### Post by 1/0 on 2007-04-04
Ohh... Beryl... I'm not keen on the bling bling stuff. I like console. Mmmmm... console

So stumblin' in the dark. What guide did you follow to install Beryl? [http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy) ?

It could be the beryl install or maybe the Nvidia drivers. 

Try turning off features and see if that helps. Someone said that *Disable "Sync to Vblank"* could help. 

Someone else wrote that this worked: "Force AIGLX" in section "rendering" and Texture "Fast" 

I don't know what else to suggest or if there are any logs for Beryl.

---

### Post by mrmonday on 2007-04-04
I think I used this guide.... But I might not of... It might have been an older version....

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia)

I have changed the Texture to fast, but I can't find the other options. I doubt there will be a 'Force AIGLX' option though, becuase nvidia cards use AIGLX anyway.

---

