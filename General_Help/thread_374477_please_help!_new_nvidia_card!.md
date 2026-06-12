---
title: "please help! new nvidia card!"
date: 2007-03-02
forum: General Help
---

### Post by Jphenow on 2007-03-02
So recently i had bout an ATI card and decided it was too much trouble and sold it to my cousin and bought a new Nvidia card, so after i put this new card in i was brought to a terminal instead of my desktop, now several times i've edited the xorg.conf file to fit the card and it is definitley a no go, I edit the file then do startx or restart and all i get is black, not even any output as to what went wrong!! what do i do fellahs??

thanks in advance!

---

### Post by taurus on 2007-03-02
At a prompt, run

```
sudo dpkg-reconfigure xserver-xorg
```
If you are not sure about a question, just use the default value/answer and use **vesa** as a driver for your graphic card.  Once you have X running again, then install nVidia driver for it.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by Jphenow on 2007-03-02
As said before, already did that, i set it to vesa several times and been using sudo dpkg-reconfigure xserver-xorg

---

### Post by taurus on 2007-03-02
And what happens when you run **startx** from a prompt?

---

### Post by Jphenow on 2007-03-02
whenever i run startx after hitting the terminal on boot, all i get is black, usually i'd think it was just takin a sec to load but i left for couple minutes once, it almost seems that the terminal thinks it's going when infact it isn't, because being that it's all black i see no output as to diagnose the problem

---

### Post by taurus on 2007-03-02
Look in /var/log/Xorg.0.log or ~/.xsession-errors.

```
more /var/log/Xorg.0.log
```
Hit the Space bar for the next 24 lines.

---

### Post by Jphenow on 2007-03-02
do you want me to post it? because honestly i'm only beginning to become mildly comfortable at a terminal myself, i don't trust my skills honestly as you can tell i only became a user about a month ago, probably less actually

---

### Post by taurus on 2007-03-02
Do you have a LiveCD handy somewhere and can you boot your machine with it, running KDE and everything?

---

### Post by Jphenow on 2007-03-02
that is what i'm using i've been booting into regular to hit the terminal then goin back into the live cd to get on the forums, also on that last command you said to use, it said file does not exist

---

### Post by taurus on 2007-03-02
Do you know what partition is your /?  For now, I will assume it's /dev/hda1.  While in LiveCD, open a terminal and copy the xorg.conf from the LiveCD to your harddrive.  Then, reboot (without the LiveCD in the drive) and see if X is running again with that new xorg.conf.

```
sudo  mkdir  /mnt/ubuntu
sudo  mount  -t  ext3  /dev/hda1  /mnt/ubuntu
sudo  /etc/X11/xorg.conf  /mnt/ubuntu/etc/X11/xorg.conf
sudo  umount  /mnt/ubuntu
```

---

### Post by Jphenow on 2007-03-02
also, i have tried running envy, it gives a little output then quickly goes to what looks like a blank terminal with just the cursor thing blinking and goes forever, usually have to manual reboot

---

### Post by Jphenow on 2007-03-02
still a no go

---

### Post by hikaricore on 2007-03-02
Just a thought since you're having so much trouble with your video card.  Does your motherboards have a builtin video chipset?  If so double check to make sure it's disabled in bios.  Sometimes this setting can reset on a hardware change to keep you from ending up with no video output (bios safety feature lol).

---

### Post by ehowell on 2007-03-02
For me I usually just type at a terminal

grep "(EE" /var/log/Xorg.0.log

which will try to find the errors in your log file, you can then post them up (if any)

---

### Post by Jphenow on 2007-03-02
the prob with that is when i get try to hit start x NORMALLY you see output and why it fails, the thing with my problem is when i hit startx all i see is black making it hard to get to that file of which you speak

---

### Post by Jphenow on 2007-03-02
okay, so went into live cd and mounted the drive so i could get hold of that log, my mouth dropped when i saw how long it was but idk what to do to fix it

[I]
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux tsphenow-desktop 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  2 16:20:55 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV34[GeForce FX 5200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) `fonts.dir' not found (or not valid) in "/usr/share/X11/fonts/misc".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/X11/fonts/misc").
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
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
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
(--) using VT number 2

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2530 card 0000,0000 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2532 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 04 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 107b,0173 rev 04 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 107b,0173 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 107b,0173 rev 04 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0322 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 1033,0035 card 107b,0173 rev 41 class 0c,03,10 hdr 80
(II) PCI: 02:01:1: chip 1033,0035 card 107b,0173 rev 41 class 0c,03,10 hdr 00
(II) PCI: 02:01:2: chip 1033,00e0 card 107b,0173 rev 02 class 0c,03,20 hdr 00
(II) PCI: 02:08:0: chip 8086,2449 card 107b,0173 rev 03 class 02,00,00 hdr 00
(II) PCI: 02:0c:0: chip 1102,0004 card 1102,0058 rev 03 class 04,01,00 hdr 80
(II) PCI: 02:0c:2: chip 1102,4001 card 1102,0010 rev 00 class 0c,00,10 hdr 80
(II) PCI: 02:0d:0: chip 14e4,4212 card 14e4,0002 rev 00 class 07,03,00 hdr 00
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
	[0] -1	0	0xfc900000 - 0xfe9fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe4600000 - 0xf46fffff (0x10100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf4700000 - 0xf47fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfd000000/24, 0xe8000000/27, BIOS @ 0xfe9e0000/17
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
	[0] -1	0	0xfeaf7000 - 0xfeaf7fff (0x1000) MX[B]
	[1] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[2] -1	0	0xfeaff000 - 0xfeaff7ff (0x800) MX[B]
	[3] -1	0	0xfeafc000 - 0xfeafcfff (0x1000) MX[B]
	[4] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[5] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[6] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[7] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[8] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[9] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[12] -1	0	0x0000df80 - 0x0000df9f (0x20) IX[B]
	[13] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[14] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[15] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[16] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeaf7000 - 0xfeaf7fff (0x1000) MX[B]
	[1] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[2] -1	0	0xfeaff000 - 0xfeaff7ff (0x800) MX[B]
	[3] -1	0	0xfeafc000 - 0xfeafcfff (0x1000) MX[B]
	[4] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[5] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[6] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[7] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[8] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[9] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[12] -1	0	0x0000df80 - 0x0000df9f (0x20) IX[B]
	[13] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[14] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[15] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[16] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
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
	[4] -1	0	0xfeaf7000 - 0xfeaf7fff (0x1000) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[6] -1	0	0xfeaff000 - 0xfeaff7ff (0x800) MX[B]
	[7] -1	0	0xfeafc000 - 0xfeafcfff (0x1000) MX[B]
	[8] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[9] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[10] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[11] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[12] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[18] -1	0	0x0000df80 - 0x0000df9f (0x20) IX[B]
	[19] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[20] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[21] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
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
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so

Backtrace:
[/I]

---

### Post by taurus on 2007-03-02
Can you post your /etc/X11/xorg.conf from the harddrive, not from the LiveCD?

---

### Post by Jphenow on 2007-03-02
yes sir...

[I]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"1"
	Option		"XkbOptions"	"lv3:ralt_switch"
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

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34[GeForce FX 5200]"
	Driver		"vesa"
	BusID		"PCI:01:00:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34[GeForce FX 5200]"
	Monitor		"Generic Monitor"
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
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
[/I]

---

### Post by taurus on 2007-03-02
Edit /etc/X11/xorg.conf and place a # in front of this line (in the Device section).

```
Option "UseFBDev" "true"
```
Save it and reboot to see if you can see anything in Gnome now.

---

### Post by Jphenow on 2007-03-02
it's KDE but okay, ill be back in a few

---

### Post by Jphenow on 2007-03-02
yea so that's a no go, any new ideas?

---

### Post by Jphenow on 2007-03-02
is there ANY solution??? i need my desktop back

---

### Post by Maestro23 on 2007-03-02
> **Jphenow said:**
> is there ANY solution??? i need my desktop back

Does you machine have on-board video?  Have you tried this Nvidia card in another machine?

---

### Post by Jphenow on 2007-03-02
i took out it's stock vid card, if you look at the log it has almost nothing to do with the card as it seems, i just need to know how to copy some things to a mount from live cd, it won't give me the ability to paste things there

---

### Post by Jphenow on 2007-03-02
so what im just screwed? can someone at least tell me how i'd uninstall and reinstall the main things i'd need, like uninstall everyrthing having to do with video and reinstall the basics, because the prob is probably that i just f-ed with things a lot when i had an ATI card in... please, im a sittin duck at the moment

---

