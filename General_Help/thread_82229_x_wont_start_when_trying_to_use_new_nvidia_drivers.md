---
title: "x wont start when trying to use new nvidia drivers"
date: 2005-10-26
forum: General Help
---

### Post by Jaristr on 2005-10-26
Hello, 
I am not sure if this should be in the hardware forum, so sorry if I got it wrong.

So the problem... First I just want to say that I have installed the newest drivers for my geforce 5200 fx in kubuntu 5.04. But now when trying to install at ubuntu 5.10 I ran into a problem.

These are the instructions I used:
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia)

I got it all done like in that thread but after booting the x server fails to start. The error screen that pops up in the console say something about "no screens"
So I'm out of ideas with this one... Any change that this is a common problem ubuntu?

Thanks.

---

### Post by Xian on 2005-10-26
[QUOTE=Jaristr]I got it all done like in that thread but after booting the x server fails to start. The error screen that pops up in the console say something about "no screens"[/QUOTE]
Please post the entire error message.

---

### Post by Jaristr on 2005-10-26
Ok, here you go, the whole log:

```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux HumbleComp 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 26 16:55:56 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "hp v72"
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3205 card 1043,8118 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0a:0: chip 11c1,048c card 11c1,044c rev 03 class 07,80,00 hdr 00
(II) PCI: 00:0b:0: chip 1106,3044 card 1043,808a rev 80 class 0c,00,10 hdr 00
(II) PCI: 00:0f:0: chip 1106,3149 card 1043,80ed rev 80 class 01,01,8f hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,80ed rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1043,810a rev 60 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1043,80ff rev 78 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0322 card 270f,1942 rev a1 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xe4000000/24, 0xd0000000/28
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe6003000 - 0xe60030ff (0x100) MX[B]
	[1] -1	0	0xe6002000 - 0xe60020ff (0x100) MX[B]
	[2] -1	0	0xe6001000 - 0xe60017ff (0x800) MX[B]
	[3] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[4] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[5] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[6] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[8] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[9] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[10] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[11] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[12] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[13] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[15] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[17] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[18] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[19] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[21] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe6003000 - 0xe60030ff (0x100) MX[B]
	[1] -1	0	0xe6002000 - 0xe60020ff (0x100) MX[B]
	[2] -1	0	0xe6001000 - 0xe60017ff (0x800) MX[B]
	[3] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[4] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[5] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[6] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[8] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[9] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[10] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[11] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[12] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[13] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[15] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[17] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[18] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[19] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[21] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe6003000 - 0xe60030ff (0x100) MX[B]
	[6] -1	0	0xe6002000 - 0xe60020ff (0x100) MX[B]
	[7] -1	0	0xe6001000 - 0xe60017ff (0x800) MX[B]
	[8] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[18] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[24] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[26] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[27] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[28] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[29] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
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
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7676
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "nvidia"
(II) Loading /usr/X11R6/lib/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7676
	Module class: XFree86 Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) NVIDIA X Driver  1.0-7676  Fri Jul 29 13:01:02 PDT 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe6003000 - 0xe60030ff (0x100) MX[B]
	[6] -1	0	0xe6002000 - 0xe60020ff (0x100) MX[B]
	[7] -1	0	0xe6001000 - 0xe60017ff (0x800) MX[B]
	[8] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[18] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[24] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[26] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[27] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[28] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[29] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe6003000 - 0xe60030ff (0x100) MX[B]
	[6] -1	0	0xe6002000 - 0xe60020ff (0x100) MX[B]
	[7] -1	0	0xe6001000 - 0xe60017ff (0x800) MX[B]
	[8] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[25] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[27] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[28] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[29] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[30] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[31] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[32] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):      that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):      that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):      Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.


```

thanks!

---

### Post by sanjose on 2005-10-26
how about your /etc/X11/**xorg.conf**

---

### Post by Xian on 2005-10-26
Okay, the NVIDIA kernel module has not been properly installed. I have not followed the How-To that you posted so I can not comment as to how well it works. However, I also use the nVidia driver and all I did on Breezy to install and run it was to:

1. Install the nvidia-glx package
2. Edit the xorg.conf file
3. Restart X

```
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
EndSection
```

Your entries may vary somewhat.
The above is just an example.

---

### Post by metoo on 2005-10-26
Do you have the 'linux-restricted-modules...' for your kernel (get the full name with 'uname -r') installed?

These provide the kernel module for the 3D accelerated driver.

If not, do so and re-configure xorg, if it is not done automatically.

---

### Post by Jaristr on 2005-10-27
Ok here is the xorg.conf file that I tried using but it caused X not to start.
There are three changes from the orginal and those are two commented lines modules and the device Driver is set to "nvidia" instead of "nv".
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	#Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"hp v72"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"hp v72"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I'm using the "nv" as device driver now because once its set to "nvidia" the x wont start.

---

### Post by Jaristr on 2005-10-27
[QUOTE=Xian]Okay, the NVIDIA kernel module has not been properly installed. I have not followed the How-To that you posted so I can not comment as to how well it works. However, I also use the nVidia driver and all I did on Breezy to install and run it was to:

1. Install the nvidia-glx package
2. Edit the xorg.conf file
3. Restart X

```
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
EndSection
```

Your entries may vary somewhat.
The above is just an example.[/QUOTE]

I installed nvidia-glx package and changed the Driver to "nvidia" but it just gives the error, probably because its too late for using the package since the drivers were installed by NVIDIA's own installation package. (as instructed in the guide)

---

### Post by Jaristr on 2005-10-27
[QUOTE=metoo]Do you have the 'linux-restricted-modules...' for your kernel (get the full name with 'uname -r') installed?

These provide the kernel module for the 3D accelerated driver.

If not, do so and re-configure xorg, if it is not done automatically.[/QUOTE]

Yes... they are installed by default, unless my card needs the legacy package.

---

### Post by N8MAN1068 on 2005-10-27
what kernel are you using? 386 or k7?

this thread might help...although i'm still having the problem myself

[http://ubuntuforums.org/showthread.php?p=447578#post447578](http://ubuntuforums.org/showthread.php?p=447578#post447578)

---

### Post by Jaristr on 2005-10-27
Kernel reported by "uname -r" is: 2.6.12-9-386

Thanks for the link, I havent found a solution yet though.

---

### Post by Jaristr on 2005-10-28
Well I didn't solve the problem but I installed kubuntu 5.10 and the card works fine in that one. (I installed the drivers using package manager)

So I'll be using kubuntu.

Thanks all.

---

