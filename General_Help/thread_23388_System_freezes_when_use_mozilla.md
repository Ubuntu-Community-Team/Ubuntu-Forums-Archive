---
title: "System freezes when use mozilla"
date: 2005-04-01
forum: General Help
---

### Post by xander on 2005-04-01
Hello. 

I`ve instaled Hoary and after latest update my system freezes.

ctrl+alt +f1 doesent work.
Keyboard and mouse buttons are inactive.
I have to reset my system by power button.
It starts, works about few minutes and freezes.

What to do with this problem?

X.

---

### Post by MaZiNgA on 2005-04-02
[QUOTE=xander]Hello. 

I`ve instaled Hoary and after latest update my system freezes.

ctrl+alt +f1 doesent work.
Keyboard and mouse buttons are inactive.
I have to reset my system by power button.
It starts, works about few minutes and freezes.

What to do with this problem?

X.[/QUOTE]
 Whoah! Same problem here! Can anyone help?
The PC works for 1 minute then freezes and i can only move the mouse over dead gnome's body...:(

PS: This only happens at linux not windows...:( So I'm posting from windows now

---

### Post by ubuntu_demon on 2005-04-02
1) report the bug if it isn't known already

2) use firefox instead of mozilla until the bug gets removed (just update regularly and have a little patience

PS why use mozilla instead of firefox ?

---

### Post by xander on 2005-04-02
This happens when I use both, firefox or mozilla. I think the problem is located in xorg server, but I dont  know what to do.

X.

---

### Post by ubuntu_demon on 2005-04-02
[QUOTE=xander]This happens when I use both, firefox or mozilla. I think the problem is located in xorg server, but I dont  know what to do.

X.[/QUOTE]
 with a bit of luck opgrading is the way to go

sudo apt-get update 
sudo apt-get dist-upgrade

if this doesn't work try :
sudo dpkg-reconfigure xserver-xorg

if this still doesn't work we have to analyze the problem more careful

---

### Post by xander on 2005-04-02
Those actions were first what I did. Without effect. I read other topics about system freezing and I think that isn`t only my problem.

X.

PS: Still need help.

---

### Post by dejitarob on 2005-04-02
I'm getting this as well. System is unresponsive after 15mins of usage in Firefox after the latest rounds of updates.

---

### Post by ubuntu_demon on 2005-04-02
what happens if you leave the system on for the same amount of time and still use it but don't use firefox ?

do this in the terminal :

firefox > firefoxlogfile

and after the system has frozen and you have rebooted do :

cat firefoxlogfile

I would like to see the contents of this file. Please attach it if it is too long.

---

### Post by xander on 2005-04-02
This file after reboot is empty.

My ubuntu freezes more and more frequent.


X.

---

### Post by ubuntu_demon on 2005-04-02
[QUOTE=xander]This file after reboot is empty.

My ubuntu freezes more and more frequent.


X.[/QUOTE]
 has it ever frozen when not in firefox ?

you should both attach the file /var/log/Xorg.0.log

and ~/xsession-errors or something like this ( I don't remember the exact file name)

---

### Post by computerguy867 on 2005-04-02
Same problem here!, has anyone filed a bug report or should I?

---

### Post by xander on 2005-04-02
This bug is noticed when I use webbrowsers and gedit.

My Xorg.0.log:


X Window System Version 6.8.2 (Ubuntu 6.8.2-9 20050402083823 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux Momik 2.6.10-5-k7 #1 Fri Apr 1 17:03:17 UTC 2005 i686
Build Date: 02 April 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-k7 (buildd@rothera) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri Apr 1 17:03:17 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr  2 22:14:59 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "F900P"
(**) |   |-->Device "NVIDIA Corporation NV18 [GeForce4 MX 440SE AGP 8x]"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc105"
(**) XKB: model: "pc105"
(**) Option "XkbLayout" "pl"
(**) XKB: layout: "pl"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
(II) PCI: 00:00:0: chip 1039,0735 card 0000,0000 rev 01 class 06,00,00 hdr 80
(II) PCI: 00:01:0: chip 1039,0001 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0018 card 0000,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 1039,0016 card 0000,0000 rev 00 class 0c,05,00 hdr 00
(II) PCI: 00:02:2: chip 1039,7001 card 1019,0a14 rev 07 class 0c,03,10 hdr 00
(II) PCI: 00:02:3: chip 1039,7001 card 1019,0a14 rev 07 class 0c,03,10 hdr 00
(II) PCI: 00:02:5: chip 1039,5513 card 1039,5513 rev d0 class 01,01,80 hdr 80
(II) PCI: 00:09:0: chip 1102,0002 card 1102,8066 rev 0a class 04,01,00 hdr 80
(II) PCI: 00:09:1: chip 1102,7002 card 1102,0020 rev 0a class 09,80,00 hdr 80
(II) PCI: 00:11:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0182 card 1554,1112 rev a2 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xcde00000 - 0xcfefffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc5c00000 - 0xcdcfffff (0x8100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV18 [GeForce4 MX 440SE AGP 8x] rev 162, Mem @ 0xce000000/24, 0xc8000000/26, BIOS @ 0xcfee0000/17
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd3ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xcfffdf00 - 0xcfffdfff (0x100) MX[B]
	[1] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[2] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[3] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[4] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[5] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[6] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[8] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[9] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[10] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[11] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xcfffdf00 - 0xcfffdfff (0x100) MX[B]
	[1] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[2] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[3] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[4] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[5] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[6] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[8] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[9] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[10] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[11] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
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
	[5] -1	0	0xcfffdf00 - 0xcfffdfff (0x100) MX[B]
	[6] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[7] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[10] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[11] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[17] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[18] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
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
(II) Loading extension FontCache
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
	compiled for 4.0.2, module version = 1.0.7167
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
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
	compiled for 4.0.2, module version = 1.0.7167
	Module class: XFree86 Video Driver
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) NVIDIA X Driver  1.0-7167  Fri Feb 25 09:10:21 PST 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xcfffdf00 - 0xcfffdfff (0x100) MX[B]
	[6] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[7] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[10] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[11] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[17] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[18] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xcfffdf00 - 0xcfffdfff (0x100) MX[B]
	[6] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[7] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[10] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[11] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[21] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NvAGP" "2"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Enabling experimental RENDER acceleration
(**) NVIDIA(0): Use of AGPGART requested
(--) NVIDIA(0): Linear framebuffer at 0xC8000000
(--) NVIDIA(0): MMIO registers at 0xCE000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce4 MX 440SE with AGP8X
(--) NVIDIA(0): VideoBIOS: 04.18.20.07.22
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): VideoRAM: 65536 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at  8 bpp: 350 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 16 bpp: 350 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 32 bpp: 350 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NVIDIA(0): F900P: Using default hsync range of 30.00-111.00 kHz
(II) NVIDIA(0): F900P: Using default vrefresh range of 50.00-160.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "1152x768":
(WW) NVIDIA(0):   horizontal sync start (1178) not a multiple of 8
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1600x1200": 229.5 MHz, 106.2 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 74.2 MHz, 85.9 kHz, 85.1 Hz (D)
(**) NVIDIA(0):      Default mode "1600x1200": 202.5 MHz, 93.8 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1600x1200": 189.0 MHz, 87.5 kHz, 70.0 Hz
(**) NVIDIA(0):      Default mode "1600x1200": 175.5 MHz, 81.2 kHz, 65.0 Hz
(**) NVIDIA(0):      Default mode "1600x1200": 162.0 MHz, 75.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1400x1050": 184.0 MHz, 93.9 kHz, 85.3 Hz
(**) NVIDIA(0):      Default mode "1400x1050": 155.8 MHz, 81.5 kHz, 74.8 Hz
(**) NVIDIA(0):      Default mode "1400x1050": 151.0 MHz, 77.0 kHz, 70.0 Hz
(**) NVIDIA(0):      Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1440x900": 108.8 MHz, 56.9 kHz, 60.2 Hz
(**) NVIDIA(0):      Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 133.5 MHz, 95.3 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.0 Hz (I)
(**) NVIDIA(0):      Default mode "960x720": 117.0 MHz, 90.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "928x696": 109.2 MHz, 86.4 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "896x672": 130.5 MHz, 106.3 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "960x600": 115.0 MHz, 91.0 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "960x600": 96.6 MHz, 74.5 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 114.8 MHz, 106.2 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 101.2 MHz, 93.8 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 94.5 MHz, 87.5 kHz, 70.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 92.0 MHz, 93.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 75.5 MHz, 77.0 kHz, 70.0 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 78.8 MHz, 91.1 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 60.8 MHz, 77.5 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.9 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): Display dimensions: (360, 270) mm
(--) NVIDIA(0): DPI set to (112, 112)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B]
	[1] 0	0	0xce000000 - 0xceffffff (0x1000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xcfffdf00 - 0xcfffdfff (0x100) MX[B]
	[8] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[9] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xcfee0000 - 0xcfefffff (0x20000) MX[B](B)
	[12] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[13] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[22] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[23] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[24] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[25] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1600x1200"
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
(II) Initializing built-in extension LBX
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
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "pl"
(**) Generic Keyboard: XkbLayout: "pl"
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
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!



Xander

---

### Post by xander on 2005-04-03
I think it could be this bug:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=5431](https://bugzilla.ubuntu.com/show_bug.cgi?id=5431)

I`ll try to add 'noinotify' to boot line.

Xander

---

### Post by ubuntu_demon on 2005-04-03
[QUOTE=xander]I think it could be this bug:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=5431](https://bugzilla.ubuntu.com/show_bug.cgi?id=5431)

I`ll try to add 'noinotify' to boot line.

Xander[/QUOTE]
 this bug is not related as far as I can see

---

### Post by ubuntu_demon on 2005-04-03
[QUOTE=demon666_nl]this bug is not related as far as I can see[/QUOTE]
 your Xorg.0.log seems fine

please post your ~/.xsession-errors

---

### Post by xander on 2005-04-03
I remove Render Accel from my xorg.conf and added 'noinotify'  to grub`s menu.lst.

Since these actions no freezing but I don`t know what was wrong.

my ~/.xsession-errors:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "xander"
/etc/gdm/Xsession: Beginning session setup...
Bonobo accessibility support initialized
GTK Accessibility Module initialized

(gnome-session:7692): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
SESSION_MANAGER=local/Momik:/tmp/.ICE-unix/7692
GTK Accessibility Module initialized
Ostrze&#380;enie mened&#380;era okien: Log level 16: Accessibility: failed to load module 'libatk-bridge': '/usr/lib/gtk-2.0/modules/libatk-bridge.so: cannot open shared object file: Nie ma takiego pliku ani katalogu'
Bonobo accessibility support initialized
GTK Accessibility Module initialized

(gnome-volume-manager:7796): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
manager.c/1250: mount_all: mounting /dev/hdd
Warning: device /dev/hdd is already handled by /etc/fstab, supplied label is ignored
Bonobo accessibility support initialized
mount: block device /dev/hdd is write-protected, mounting read-only
Bonobo accessibility support initialized
GTK Accessibility Module initialized

(update-notifier:7803): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
GTK Accessibility Module initialized

(gnome-panel:7798): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
Bonobo accessibility support initialized
GTK Accessibility Module initialized

(nautilus:7800): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
manager.c/1056: is_mounted property of /org/freedesktop/Hal/devices/block_Ubuntu 4.10 i386 Bin-1 changed to true
Bonobo accessibility support initialized
GTK Accessibility Module initialized

(gnome-terminal:7830): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
Bonobo accessibility support initialized
GTK Accessibility Module initialized

(gnome-terminal:7844): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
Bonobo accessibility support initialized
GTK Accessibility Module initialized



I`ll try to enable Render Accel in my xorg.conf and see what will happen.

X.

---

### Post by xander on 2005-04-03
Ok, I think i found a problem.

When I added to my xorg.conf in section device line: RenderAccel "true" , my system frozen. 

I don`t know why. I used Warty with this configuration and everything was ok.

Now I don`t have this line in my xorg.conf and have no freezes... Since now.

Xander

---

### Post by ubuntu_demon on 2005-04-03
[QUOTE=xander]Ok, I think i found a problem.

When I added to my xorg.conf in section device line: RenderAccel "true" , my system frozen. 

I don`t know why. I used Warty with this configuration and everything was ok.

Now I don`t have this line in my xorg.conf and have no freezes... Since now.

Xander[/QUOTE]
 great

---

### Post by Leif on 2005-04-04
This seems to work for me too, if you can call it that. Thanks for the hint. I will be checking every once in a while to see if things have changed, but if anybody notices that things are back to normal, please post here.

---

### Post by lee_connell on 2005-04-04
mine freezes up randomly also, i am using ati's driver but i dont use the config program to set it up therefore i dont even have render accel in there, i just simply replace ati with fglrx.

I havn't tried noinotify yet, what is inotify for anyways, what am i gonna lose by getting rid of it?

---

### Post by ubuntu_demon on 2005-04-04
[QUOTE=lee_connell]mine freezes up randomly also, i am using ati's driver but i dont use the config program to set it up therefore i dont even have render accel in there, i just simply replace ati with fglrx.

I havn't tried noinotify yet, what is inotify for anyways, what am i gonna lose by getting rid of it?[/QUOTE]
 it's a module that our compiled hoary kernel has already
It's not related to this problem.

---

### Post by limewolf on 2005-04-13
I've been having similar problems to the ones described here, with other linux distributions too (on a couple of machines, all with nvidia cards and nvidia's own drivers). 

I disabled "RenderAccel" on my nvidia cards on my main machine (I have two, running 3 monitors) and the problem seems to have gone - i seem to vaugly remeber this first becoming a problem after upgrading to xorg from XFree86 in gentoo a while back now - but I could be completely wrong.

Anybody have any more information on this at all? I really don't like disabling RenderAccel :-).

---

### Post by foxy123 on 2005-04-13
Welcome to the club! It is well-known bug of random freezing, which may be observed on ATI and NVidia cards.

If you have ATI you may want to look into those threads on Rage3D:

[http://www.rage3d.com/board/showthread.php?t=33800697](http://www.rage3d.com/board/showthread.php?t=33800697)
[http://www.rage3d.com/board/showthread.php?t=33811518](http://www.rage3d.com/board/showthread.php?t=33811518)

In case of NVidia:

[http://www.nvnews.net/vbulletin/showthread.php?t=31858&page=1&pp=15](http://www.nvnews.net/vbulletin/showthread.php?t=31858&page=1&pp=15)

Basically as I understand no one actually knows what causes it and offer various solutions which may help or may not (like in my case).

---

### Post by foxy123 on 2005-04-14
Following my post, I managed to get rid of the freeze yesterday by forcing APG 8x to 4x.

---

### Post by misterlizard on 2005-04-14
There's been some discussion about this in the following thread about Firefox lock-ups:
[http://www.ubuntuforums.org/showthread.php?t=24672](http://www.ubuntuforums.org/showthread.php?t=24672)

From messing about with various settings, I reckon it's a combination of the following:

1. 'nvidia' driver in xorg.conf (instead of 'nv')
2. Option "RenderAccel" "true" in xorg.conf
3. Autohinting in fontconfig

---

### Post by lee_connell on 2005-04-16
I get lockups still.  I am using the fglrx driver, I don't even have RenderAccel in my xorg.conf file.  I will check on auto-hinting. 

Are you guys checking xorg log or something to figure out that it definately is the video driver being used?

Lee

---

### Post by foxy123 on 2005-04-17
[QUOTE=lee_connell]I get lockups still.  I am using the fglrx driver, I don't even have RenderAccel in my xorg.conf file.  I will check on auto-hinting. 

Are you guys checking xorg log or something to figure out that it definately is the video driver being used?

Lee[/QUOTE]

Try to set APG to 4x, following the posts on Rage3D I mentioned above.

---

### Post by lee_connell on 2005-04-19
foxy, i did a brand new install of ubuntu hoary and i'm using the ati xorg driver and my system locked up today on me while i was using evolution and adding some tasks.  before it happened when in firefox, another time it happened in a different program.

nothing is in my xsession-errors except gnome-cups-icon couldn't start.

though in my log it says the radeon driver is using render acceleration.

Where do i add RenderAccel False?  Also where do i tell it to use AGP4x?

---

### Post by foxy123 on 2005-04-20
[QUOTE=lee_connell]foxy, i did a brand new install of ubuntu hoary and i'm using the ati xorg driver and my system locked up today on me while i was using evolution and adding some tasks.  before it happened when in firefox, another time it happened in a different program.

nothing is in my xsession-errors except gnome-cups-icon couldn't start.

though in my log it says the radeon driver is using render acceleration.

Where do i add RenderAccel False?  Also where do i tell it to use AGP4x?[/QUOTE]

hi lee, you'd better try Rage3D, which has an unofficial radeon support forum. I posted a couple of links in my posts above. This topic is being heavily discussed there.

I am not sure about RenderAccel option. I thought that it is from nvidia. In my xorg.conf "Load dri" is used to enable 3D acceleration, so you can comment it to disable.

As for AGP 4x, please refer to a topic on Rage3D, where there is a good instruction. Also you need to make sure that FastWrite is disble as well.

---

### Post by maspro on 2005-05-17
[QUOTE=xander]
(gnome-session:7692): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
SESSION_MANAGER=local/Momik:/tmp/.ICE-unix/7692
GTK Accessibility Module initialized
Ostrze&#380;enie mened&#380;era okien: Log level 16: Accessibility: failed to load module 'libatk-bridge': '/usr/lib/gtk-2.0/modules/libatk-bridge.so: cannot open shared object file: Nie ma takiego pliku ani katalogu'
Bonobo accessibility support initialized
GTK Accessibility Module initialized

(gnome-volume-manager:7796): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
manager.c/1250: mount_all: mounting /dev/hdd
Warning: device /dev/hdd is already handled by /etc/fstab, supplied label is ignored
Bonobo accessibility support initialized
mount: block device /dev/hdd is write-protected, mounting read-only
Bonobo accessibility support initialized
GTK Accessibility Module initialized

(update-notifier:7803): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
GTK Accessibility Module initialized

(gnome-panel:7798): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
Bonobo accessibility support initialized
GTK Accessibility Module initialized

(nautilus:7800): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
manager.c/1056: is_mounted property of /org/freedesktop/Hal/devices/block_Ubuntu 4.10 i386 Bin-1 changed to true
Bonobo accessibility support initialized
GTK Accessibility Module initialized

(gnome-terminal:7830): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
Bonobo accessibility support initialized
GTK Accessibility Module initialized

(gnome-terminal:7844): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
Bonobo accessibility support initialized
GTK Accessibility Module initialized
X.[/QUOTE]
About this "libatk-bridge" error, install at-spi, which will probability solve the problem, you can get it through APT.

---

### Post by lee_connell on 2005-05-18
noinotify didn't work for me and i dont have renderaccel in xorg.conf at all.  Anyone have an answer for this?

---

