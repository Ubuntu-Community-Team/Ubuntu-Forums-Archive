---
title: "Strange Nvidia GLX problem with beryl"
date: 2007-03-13
forum: General Help
---

### Post by nicjasno on 2007-03-13
I have another Nvidia glx related problem.

I noticed this, because i am running beryl. I installed fresh nvidia drivers, and glxinfo saig that direct rendering was enabled. Also nvidia-settings showed all the info.

But after the next boot, direct rendering didn't work. And beryl was unable to start.

I then disabled the glx module in xorg and rebooted x. It failed to load, of course. Then i enabled the glx module again, and direct rendering worked again.

What can i do, to fix this? I have run out of ideas.

---

### Post by freerick on 2007-03-13
First, open your /etc/X11/xorg.conf file and check under the "Device" section. Look for the "RenderAccel" option. If you don't see it, add this line:

Option "RenderAccel" "Enable"

Save the file (as root) and restart the X server. See if it works. If not, post the contents of your xorg.conf file here, as well as the contents of your /var/log/xorg.log file.

---

### Post by nicjasno on 2007-03-14
It didn't help. Here are the contents of the 2 files:

xorg.conf:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"
	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
                                                  # /dev/input/event
                                                  # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"          # Tablet PC ONLY
EndSection

Section "InputDevice"
                                                  # /dev/input/event
                                                  # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"          # Tablet PC ONLY
EndSection

Section "InputDevice"
                                                  # /dev/input/event
                                                  # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"          # Tablet PC ONLY
EndSection

Section "Monitor"
    # Option         "DPMS"
    Identifier     "LG 203wt"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce 7300 GT"
    Driver         "nvidia"
    Option         "RenderAccel" "Enable"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 7300 GT"
    Monitor        "LG 203wt"
    Option         "AddARGBGLXVisuals" "True"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

Xorg.0.log:
```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux black 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 14 08:08:05 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "LG 203wt"
(**) |   |-->Device "NVIDIA GeForce 7300 GT"
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
(WW) FontPath is completely invalid.  Using compiled-in default.
(==) FontPath set to:
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,0369 card 1043,8239 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0360 card 1043,8239 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0368 card 1043,8239 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:01:2: chip 10de,036a card 1043,8239 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,036c card 1043,8239 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,036d card 1043,8239 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,036e card 1043,8239 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:05:0: chip 10de,037f card 1043,8239 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:05:1: chip 10de,037f card 1043,8239 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:05:2: chip 10de,037f card 1043,8239 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:06:0: chip 10de,0370 card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:08:0: chip 10de,0373 card 1043,8239 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0376 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0b:0: chip 10de,0374 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,0374 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,0378 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,0375 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0f:0: chip 10de,0377 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:08:0: chip 1102,0002 card 1102,8061 rev 07 class 04,01,00 hdr 80
(II) PCI: 01:08:1: chip 1102,7002 card 1102,0020 rev 07 class 09,80,00 hdr 80
(II) PCI: 07:00:0: chip 10de,0393 card 1458,341b rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:6:0), (0,1,1), BCTRL: 0x0a04 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:10:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:11:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:12:0), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:13:0), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:14:0), (0,6,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:15:0), (0,7,7), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 7 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfcffffff (0x3000000) MX[B]
(II) Bus 7 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(7:0:0) nVidia Corporation unknown chipset (0x0393) rev 161, Mem @ 0xfa000000/24, 0xe0000000/28, 0xfb000000/24, I/O @ 0x9c00/7, BIOS @ 0xfcfe0000/17
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
	[0] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[1] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[2] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[4] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[8] -1	0	0xfcfe0000 - 0xfcffffff (0x20000) MX[B](B)
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[13] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[14] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[15] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[32] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[33] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[34] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[1] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[2] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[4] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[8] -1	0	0xfcfe0000 - 0xfcffffff (0x20000) MX[B](B)
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[13] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[14] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[15] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[32] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[33] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[34] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
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
	[4] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[5] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[6] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xfcfe0000 - 0xfcffffff (0x20000) MX[B](B)
	[13] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[19] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[23] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[25] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[27] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[28] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[29] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[30] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[31] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[32] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[33] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[34] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[35] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[36] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[37] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[38] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[39] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[40] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
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
(II) Primary Device is: PCI 07:00:0
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
	[4] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[5] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[6] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xfcfe0000 - 0xfcffffff (0x20000) MX[B](B)
	[13] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[19] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[23] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[25] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[27] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[28] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[29] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[30] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[31] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[32] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[33] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[34] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[35] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[36] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[37] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[38] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[39] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[40] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[5] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[6] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xfcfe0000 - 0xfcffffff (0x20000) MX[B](B)
	[13] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[22] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[24] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[25] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[26] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[28] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[29] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[30] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[31] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[32] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[33] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[34] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[35] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[36] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[37] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[38] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[39] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[40] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[41] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[42] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[43] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
	[44] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[45] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(WW) NVIDIA(0): Option "RenderAccel" requires a boolean value
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GT at PCI:7:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.16.02
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GT at PCI:7:0:0:
(--) NVIDIA(0):     LG L203WT (DFP-0)
(--) NVIDIA(0): LG L203WT (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): LG L203WT (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1680x1050"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] 0	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[8] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[9] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[10] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[11] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[12] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[13] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[14] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[15] -1	0	0xfcfe0000 - 0xfcffffff (0x20000) MX[B](B)
	[16] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[17] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] 0	0	0x00009c00 - 0x00009c7f (0x80) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[26] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[27] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[29] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[30] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[32] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[33] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[34] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[35] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[36] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[37] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[38] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[39] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[40] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[41] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[42] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[43] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[44] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[45] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[46] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[47] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
	[48] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[49] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1680x1050"
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
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
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
    xkb_symbols              { include "pc(pc104)+us" };
    xkb_geometry             { include "pc(pc104)" };
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

```

---

### Post by freerick on 2007-03-14
my bad, you have to put "RenderAccel" "true", sorry about that. Looking at your log file, I don't think that setting this would help either though. In addition to RenderAccel, add the following option to your Device section also:

    Option	   "EnablePageFlip" "on"
    Option	   "RenderAccel" "true"
    Option	   "NvAgp" "1"


I'm not quite sure why beryl isn't starting. You said direct redering doesn't work? I didn't see anything about enabling the direct rendering mode (DRI I think) in your config file, and it's not required to run beryl.

Try starting beryl from the command line and copy the output here. If you make changes to xorg.conf, also be sure to restart your X server and post the new files here as well. Also see if you get an error if you run "glxinfo" form the command line. You should get a bunch of numbers, but I've set up my system before in a way that prevented glx from loading correctly, so glxinfo returned an error. If glxinfo works fine, that means the problem is not with the GLX module. It might be with Beryl's configuration. 

On beryl's wiki, there is a script posted which sets up pertinent configuration parameters for you, as well as downloads and installs beryl automatically. You should try this option, when I did it, this brought me a lot closer to running beryl successfully.

---

### Post by nicjasno on 2007-03-14
The thing is, that if i first disable glx in xorg, and then restart x (which fails to load, of course), and then reenable glx, it all works fine. 

But once i start beryl, and restart x, direct rendering doesn't work. A phenomenoni can't explain.

---

### Post by freerick on 2007-03-14
> **nicjasno said:**
> The thing is, that if i first disable glx in xorg, and then restart x (which fails to load, of course), and then reenable glx, it all works fine. 

But once i start beryl, and restart x, direct rendering doesn't work. A phenomenoni can't explain.

Ok, try starting beryl from the command line (or another OpenGL application) and copy the output here, then we'll know more about what's going on.

---

### Post by nicjasno on 2007-03-14
I can't. Because beryl actually strats, but the screen goes white. So i don't see anything. But when i try to rotate the cube, i see the cube's top faces, but all the sides are white.

---

