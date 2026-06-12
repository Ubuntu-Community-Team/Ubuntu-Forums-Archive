---
title: "linux-restricted-modules?"
date: 2007-05-05
forum: General Help
---

### Post by atari05 on 2007-05-05
Ok, I have a question that spawns from the BATTLE I have going with my 8800GTS and getting the Nvidia driver to work.


Why is linux-restricted-modules-<kernel> installed by default? From the description it sounds like it will give me the "non-free" ATI,Nvidia and madwifi kernel modules.

Now, I do have a 8800GTS but I don't get why I need this package ON TOP of the nvidia-glx-new. So is there some underlying difference here I'm not getting due to lack of details in the description?

I would assume that you having these and the nvida-glx-new installed would cause issues? Also, I find it weird that on the nvnews site they want me to remove these restricted modules but ....it seem there is dep for linux-generic...which seems to be my kernel???
 

and btw, this emoticon is here just because I think its funny

:lolflag: 


heheh yaGoku

---

### Post by Theimon on 2007-05-06
You don't need to remove them for the binary nVidia drivers to work. You just have to disable the nv driver because it can conflict with the nVidia driver.
But when you use the nvidia-glx package that's not necessary, only with the binary.
The restricted modules package is there to supply the nv, ati madwifi etc. drivers, you could uninstall it, but it doesn't get in the way so why bother?

---

### Post by atari05 on 2007-05-06
Ahh see I thought NV was a free and open driver. So when I read that the license are restricted I got thrown. My bad for not doing a bit of dig'in


In the end this 8800 is giving me a huge headache...something tells me I will have to wait a bit for a solid and well rounded solution. 

I mean, I install the glx-new, I ensure my x-org reflects nvidia...and then I get black screen after restart....I even blacklisted the nv module...so...I got no bones, no bones at all

---

### Post by Theimon on 2007-05-06
Do you see any errors in dmesg and/or the xorg.0.log? At what point does the screen go black?

---

### Post by atari05 on 2007-05-07
Well, at least in Ubuntu (does not happen in Kubuntu) I get a ncurse based message telling me it can't bring up X. When It asked if I wanted to look at the logs I said yes and saw very cryptic messages, nothing from what I could form a good idea on what the issue might be. I don't have time right now but let me go through the process again (had to reinstall due to my tinkering) and post some relevant information from the logs, I will have to check dmesg as I didn't do that yet.

---

### Post by atari05 on 2007-05-12
Well my logs and dmesg didnt give me much insite as to why it wasn´t working. 

Below is my Xorg log.

```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux tron 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May 12 00:37:09 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
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
(II) PCI: 00:06:1: chip 10de,0371 card 1043,81f6 rev a2 class 04,03,00 hdr 80
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
(II) PCI: 01:08:0: chip 1102,0008 card 1102,1001 rev 00 class 04,01,00 hdr 00
(II) PCI: 07:00:0: chip 10de,0193 card 19f1,2289 rev a2 class 03,00,00 hdr 00
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
	[0] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B]
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
(--) PCI:*(7:0:0) nVidia Corporation unknown chipset (0x0193) rev 162, Mem @ 0xfa000000/24, 0xe0000000/28, 0xf8000000/25, I/O @ 0x9c00/7, BIOS @ 0xfbfe0000/17
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
	[3] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[4] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[5] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[6] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[7] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[8] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[9] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[10] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ac00 - 0x0000ac3f (0x40) IX[B]
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
	[3] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[4] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[5] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[6] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[7] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[8] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[9] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[10] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ac00 - 0x0000ac3f (0x40) IX[B]
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
	[7] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[8] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[9] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[13] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[14] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000ac00 - 0x0000ac3f (0x40) IX[B]
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
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:23:13 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 07:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:7:0:0) found
(EE) No devices detected.

Fatal server error:
no screens found

```

Dmesg will be in another post

---

### Post by atari05 on 2007-05-12
Here is my dmesg

```

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007fde0000 end: 000000007fee0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007fee0000 size: 0000000000003000 end: 000000007fee3000 type: 4
[    0.000000] copy_e820_map() start: 000000007fee3000 size: 000000000000d000 end: 000000007fef0000 type: 3
[    0.000000] copy_e820_map() start: 000000007fef0000 size: 0000000000010000 end: 000000007ff00000 type: 2
[    0.000000] copy_e820_map() start: 00000000f0000000 size: 0000000004000000 end: 00000000f4000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5940
[    0.000000] Entering add_active_range(0, 0, 524000) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524000
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524000
[    0.000000] On node 0 totalpages: 524000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292323 pages, LIFO batch:31
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v002 Nvidia                                ) @ 0x000f7620
[    0.000000] ACPI: XSDT (v001 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000000) @ 0x7fee30c0
[    0.000000] ACPI: FADT (v003 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000000) @ 0x7feec400
[    0.000000] ACPI: HPET (v001 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000098) @ 0x7feec600
[    0.000000] ACPI: MCFG (v001 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000000) @ 0x7feec680
[    0.000000] ACPI: MADT (v001 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000000) @ 0x7feec540
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x03000000) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
[    0.000000] Detected 2009.282 MHz processor.
[   21.029972] Built 1 zonelists.  Total pages: 519907
[   21.029975] Kernel command line: root=UUID=9a947484-17cd-4a1a-a3f3-aa38268acafa ro quiet splash
[   21.030096] mapped APIC to ffffd000 (fee00000)
[   21.030099] mapped IOAPIC to ffffc000 (fec00000)
[   21.030102] Enabling fast FPU save and restore... done.
[   21.030104] Enabling unmasked SIMD FPU exception support... done.
[   21.030109] Initializing CPU#0
[   21.030143] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   21.030168] spurious 8259A interrupt: IRQ7.
[   21.032841] Console: colour VGA+ 80x25
[   21.033079] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   21.033387] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.089266] Memory: 2066772k/2096000k available (1992k kernel code, 27928k reserved, 893k data, 328k init, 1178496k highmem)
[   21.089276] virtual kernel memory layout:
[   21.089277]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   21.089278]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.089279]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   21.089280]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   21.089281]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   21.089283]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   21.089284]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   21.089286] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   21.089395] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
[   21.089399] hpet0: 3 32-bit timers, 25000000 Hz
[   21.090405] Using HPET for base-timer
[   21.169297] Calibrating delay using timer specific routine.. 4021.64 BogoMIPS (lpj=8043299)
[   21.169330] Security Framework v1.0.0 initialized
[   21.169335] SELinux:  Disabled at boot.
[   21.169346] Mount-cache hash table entries: 512
[   21.169444] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[   21.169452] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.169454] CPU: L2 Cache: 512K (64 bytes/line)
[   21.169457] CPU 0(2) -> Core 0
[   21.169458] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[   21.169466] Compat vDSO mapped to ffffe000.
[   21.169469] Remapping vsyscall page to ffffe000
[   21.169477] Checking 'hlt' instruction... OK.
[   21.185367] SMP alternatives: switching to UP code
[   21.185637] Early unpacking initramfs... done
[   21.470317] ACPI: Core revision 20060707
[   21.476624] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   21.482455] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[   21.482472] SMP alternatives: switching to SMP code
[   21.482533] Booting processor 1/1 eip 3000
[   21.492054] Initializing CPU#1
[   21.572142] Calibrating delay using timer specific routine.. 4018.58 BogoMIPS (lpj=8037162)
[   21.572148] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[   21.572154] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.572156] CPU: L2 Cache: 512K (64 bytes/line)
[   21.572158] CPU 1(2) -> Core 1
[   21.572159] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[   21.572994] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[   21.573004] Total of 2 processors activated (8040.23 BogoMIPS).
[   21.573236] ENABLING IO-APIC IRQs
[   21.573438] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   21.720600] checking TSC synchronization across 2 CPUs: 
[    0.000001] CPU#0 had 323 usecs TSC skew, fixed it up.
[    0.000003] CPU#1 had -323 usecs TSC skew, fixed it up.
[    0.003996] Brought up 2 CPUs
[    0.058189] migration_cost=170
[    0.058389] Booting paravirtualized kernel on bare hardware
[    0.058443] Time:  0:36:31  Date: 04/12/107
[    0.058467] NET: Registered protocol family 16
[    0.058530] EISA bus registered
[    0.058533] ACPI: bus type pci registered
[    0.089225] PCI: PCI BIOS revision 3.00 entry at 0xf1e40, last bus=7
[    0.089227] PCI: Using configuration type 1
[    0.089229] Setting up standard PCI resources
[    0.102926] ACPI: Interpreter enabled
[    0.102929] ACPI: Using IOAPIC for interrupt routing
[    0.103496] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.103501] PCI: Probing PCI hardware (bus 00)
[    0.106098] PCI: Transparent bridge - 0000:00:06.0
[    0.106375] Boot video device is 0000:07:00.0
[    0.106441] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.177395] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.182688] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.183072] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.183454] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
[    0.183837] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.184219] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.184601] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 *11 14 15)
[    0.184980] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.185362] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.185746] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.186129] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[    0.186511] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[    0.186895] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
[    0.187280] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.187663] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[    0.188047] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.188429] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.188812] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.189197] ACPI: PCI Interrupt Link [LFID] (IRQs *5 7 9 10 11 14 15)
[    0.189580] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)
[    0.190047] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.190506] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.190965] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.191423] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.191882] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.192343] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.192799] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.193254] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.193711] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[    0.194171] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[    0.194628] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.195085] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[    0.195543] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[    0.196003] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[    0.196461] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.196919] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.197377] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[    0.197838] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.198299] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0, disabled.
[    0.198605] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.198612] pnp: PnP ACPI init
[    0.206947] pnp: PnP ACPI: found 13 devices
[    0.206950] PnPBIOS: Disabled by ACPI PNP
[    0.206989] PCI: Using ACPI for IRQ routing
[    0.206993] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.289169] NET: Registered protocol family 8
[    0.289171] NET: Registered protocol family 20
[    0.289632] pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
[    0.289634] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.289637] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[    0.289640] pnp: 00:01: ioport range 0x1480-0x14ff could not be reserved
[    0.289642] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[    0.289645] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.289875] PCI: Bridge: 0000:00:06.0
[    0.289878]   IO window: a000-afff
[    0.289880]   MEM window: disabled.
[    0.289882]   PREFETCH window: disabled.
[    0.289885] PCI: Bridge: 0000:00:0a.0
[    0.289886]   IO window: disabled.
[    0.289888]   MEM window: disabled.
[    0.289890]   PREFETCH window: disabled.
[    0.289892] PCI: Bridge: 0000:00:0b.0
[    0.289894]   IO window: disabled.
[    0.289896]   MEM window: disabled.
[    0.289898]   PREFETCH window: disabled.
[    0.289900] PCI: Bridge: 0000:00:0c.0
[    0.289901]   IO window: disabled.
[    0.289903]   MEM window: disabled.
[    0.289905]   PREFETCH window: disabled.
[    0.289907] PCI: Bridge: 0000:00:0d.0
[    0.289909]   IO window: disabled.
[    0.289911]   MEM window: disabled.
[    0.289913]   PREFETCH window: disabled.
[    0.289915] PCI: Bridge: 0000:00:0e.0
[    0.289916]   IO window: disabled.
[    0.289918]   MEM window: disabled.
[    0.289920]   PREFETCH window: disabled.
[    0.289922] PCI: Bridge: 0000:00:0f.0
[    0.289924]   IO window: 9000-9fff
[    0.289927]   MEM window: f8000000-fbffffff
[    0.289929]   PREFETCH window: e0000000-efffffff
[    0.289938] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    0.289945] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[    0.289951] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    0.289957] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    0.289963] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    0.289969] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    0.289974] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[    0.290000] NET: Registered protocol family 2
[    0.331622] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.331735] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.332298] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.332561] TCP: Hash tables configured (established 131072 bind 65536)
[    0.332564] TCP reno registered
[    0.347662] checking if image is initramfs... it is
[    0.909840] Freeing initrd memory: 6998k freed
[    1.436000] audit: initializing netlink socket (disabled)
[    1.436000] audit(1178930192.620:1): initialized
[    1.436000] highmem bounce pool size: 64 pages
[    1.436000] VFS: Disk quotas dquot_6.5.1
[    1.436000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.436000] io scheduler noop registered
[    1.436000] io scheduler anticipatory registered
[    1.436000] io scheduler deadline registered
[    1.436000] io scheduler cfq registered (default)
[    1.456000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[    1.456000] assign_interrupt_mode Found MSI capability
[    1.456000] Allocate Port Service[0000:00:0a.0:pcie00]
[    1.456000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    1.456000] assign_interrupt_mode Found MSI capability
[    1.456000] Allocate Port Service[0000:00:0b.0:pcie00]
[    1.456000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    1.456000] assign_interrupt_mode Found MSI capability
[    1.456000] Allocate Port Service[0000:00:0c.0:pcie00]
[    1.456000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    1.456000] assign_interrupt_mode Found MSI capability
[    1.456000] Allocate Port Service[0000:00:0d.0:pcie00]
[    1.456000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    1.456000] assign_interrupt_mode Found MSI capability
[    1.456000] Allocate Port Service[0000:00:0e.0:pcie00]
[    1.456000] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[    1.456000] assign_interrupt_mode Found MSI capability
[    1.456000] Allocate Port Service[0000:00:0f.0:pcie00]
[    1.456000] isapnp: Scanning for PnP cards...
[    1.808000] isapnp: No Plug & Play device found
[    1.828000] Real Time Clock Driver v1.12ac
[    1.828000] hpet_resources: 0xfefff000 is busy
[    1.828000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.828000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.828000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.828000] mice: PS/2 mouse device common for all mice
[    1.832000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.832000] input: Macintosh mouse button emulation as /class/input/input0
[    1.832000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.832000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.832000] PNP: No PS/2 controller found. Probing ports directly.
[    1.832000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.832000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.832000] EISA: Probing bus 0 at eisa.0
[    1.832000] Cannot allocate resource for EISA slot 1
[    1.832000] EISA: Detected 0 cards.
[    1.860000] TCP cubic registered
[    1.860000] NET: Registered protocol family 1
[    1.860000] Starting balanced_irq
[    1.860000] Using IPI No-Shortcut mode
[    1.860000] ACPI: (supports S0 S1 S3 S4 S5)
[    1.860000]   Magic number: 7:471:607
[    1.860000]   hash matches device ptyae
[    1.860000] Freeing unused kernel memory: 328k freed
[    1.864000] Time: hpet clocksource has been installed.
[    3.104000] Capability LSM initialized
[    3.136000] ACPI: Fan [FAN] (on)
[    3.140000] ACPI: Thermal Zone [THRM] (40 C)
[    3.596000] SCSI subsystem initialized
[    3.620000] libata version 2.20 loaded.
[    3.628000] usbcore: registered new interface driver usbfs
[    3.628000] usbcore: registered new interface driver hub
[    3.628000] usbcore: registered new device driver usb
[    3.628000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.628000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    3.628000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[    3.628000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    3.628000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.628000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    3.628000] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfe02f000
[    3.628000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[    3.688000] usb usb1: configuration #1 chosen from 1 choice
[    3.688000] hub 1-0:1.0: USB hub found
[    3.688000] hub 1-0:1.0: 10 ports detected
[    3.696000] Floppy drive(s): fd0 is 1.44M
[    3.716000] FDC 0 is a post-1991 82077
[    3.796000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    3.796000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 17
[    3.796000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[    3.796000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    3.796000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    3.796000] ehci_hcd 0000:00:02.1: debug port 1
[    3.796000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[    3.796000] ehci_hcd 0000:00:02.1: irq 17, io mem 0xfe02e000
[    3.796000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.796000] usb usb2: configuration #1 chosen from 1 choice
[    3.796000] hub 2-0:1.0: USB hub found
[    3.796000] hub 2-0:1.0: 10 ports detected
[    3.904000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[    3.904000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 18
[    3.904000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    3.904000] forcedeth: using HIGHDMA
[    4.428000] eth0: forcedeth.c: subsystem: 01043:8239 bound to 0000:00:08.0
[    4.428000] sata_nv 0000:00:05.0: version 3.3
[    4.428000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    4.428000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 19
[    4.428000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[    4.428000] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001dc00 irq 19
[    4.428000] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001dc08 irq 19
[    4.428000] scsi0 : sata_nv
[    4.516000] usb 2-2: new high speed USB device using ehci_hcd and address 3
[    4.660000] usb 2-2: configuration #1 chosen from 1 choice
[    4.660000] hub 2-2:1.0: USB hub found
[    4.660000] hub 2-2:1.0: 4 ports detected
[    4.900000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.916000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[    4.916000] ata1.00: ATA-7: WDC WD2000JS-00MHB0, 02.01C03, max UDMA/133
[    4.916000] ata1.00: 390721968 sectors, multi 1: LBA48 
[    4.928000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[    4.928000] ata1.00: configured for UDMA/133
[    4.928000] scsi1 : sata_nv
[    5.228000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[    5.440000] usb 1-1: configuration #1 chosen from 1 choice
[    5.440000] hub 1-1:1.0: USB hub found
[    5.444000] hub 1-1:1.0: 4 ports detected
[    5.516000] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.532000] ata2.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    5.532000] ata2.00: ATA-6: ST380013AS, 3.18, max UDMA/133
[    5.532000] ata2.00: 156301488 sectors, multi 1: LBA48 
[    5.544000] ata2.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    5.544000] ata2.00: configured for UDMA/133
[    5.544000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2000JS-00M 02.0 PQ: 0 ANSI: 5
[    5.544000] scsi 1:0:0:0: Direct-Access     ATA      ST380013AS       3.18 PQ: 0 ANSI: 5
[    5.544000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[    5.544000] ACPI: PCI Interrupt 0000:00:05.1[B] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
[    5.544000] PCI: Setting latency timer of device 0000:00:05.1 to 64
[    5.544000] ata3: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001c800 irq 16
[    5.544000] ata4: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001c808 irq 16
[    5.544000] scsi2 : sata_nv
[    5.780000] usb 2-2.3: new full speed USB device using ehci_hcd and address 4
[    5.976000] usb 2-2.3: configuration #1 chosen from 1 choice
[    6.016000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.192000] ata3.00: ATAPI, max UDMA/100
[    6.212000] usb 1-1.1: new low speed USB device using ohci_hcd and address 3
[    6.336000] usb 1-1.1: configuration #1 chosen from 1 choice
[    6.364000] ata3.00: configured for UDMA/100
[    6.364000] scsi3 : sata_nv
[    6.576000] usb 1-1.3: new full speed USB device using ohci_hcd and address 4
[    6.676000] ata4: SATA link down (SStatus 0 SControl 300)
[    6.676000] ATA: abnormal status 0x7F on port 0x00010967
[    6.680000] scsi 2:0:0:0: CD-ROM            LITE-ON  COMBO SHC-52S7K  VK03 PQ: 0 ANSI: 5
[    6.684000] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 22
[    6.684000] ACPI: PCI Interrupt 0000:00:05.2[C] -> Link [ASA2] -> GSI 22 (level, low) -> IRQ 17
[    6.684000] PCI: Setting latency timer of device 0000:00:05.2 to 64
[    6.684000] ata5: SATA max UDMA/133 cmd 0x0001c400 ctl 0x0001c002 bmdma 0x0001b400 irq 17
[    6.684000] ata6: SATA max UDMA/133 cmd 0x0001bc00 ctl 0x0001b802 bmdma 0x0001b408 irq 17
[    6.684000] scsi4 : sata_nv
[    6.708000] usb 1-1.3: configuration #1 chosen from 1 choice
[    6.948000] usb 1-1.4: new full speed USB device using ohci_hcd and address 5
[    6.996000] ata5: SATA link down (SStatus 0 SControl 300)
[    6.996000] ATA: abnormal status 0x7F on port 0x0001c407
[    7.000000] scsi5 : sata_nv
[    7.080000] usb 1-1.4: configuration #1 chosen from 1 choice
[    7.084000] usbcore: registered new interface driver hiddev
[    7.092000] input: Logitech Logitech Gaming Keyboard as /class/input/input1
[    7.092000] input: USB HID v1.10 Keyboard [Logitech Logitech Gaming Keyboard] on usb-0000:00:02.0-1.1
[    7.104000] input: Logitech Logitech Gaming Keyboard as /class/input/input2
[    7.104000] input,hiddev96: USB HID v1.10 Device [Logitech Logitech Gaming Keyboard] on usb-0000:00:02.0-1.1
[    7.108000] input: Logitech USB Receiver as /class/input/input3
[    7.108000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-1.3
[    7.120000] input: Logitech USB Receiver as /class/input/input4
[    7.120000] input,hiddev97: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:02.0-1.3
[    7.128000] input: G15 Keyboard G15 Keyboard as /class/input/input5
[    7.128000] input,hiddev98: USB HID v1.11 Keypad [G15 Keyboard G15 Keyboard] on usb-0000:00:02.0-1.4
[    7.128000] usbcore: registered new interface driver usbhid
[    7.128000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    7.312000] ata6: SATA link down (SStatus 0 SControl 300)
[    7.312000] ATA: abnormal status 0x7F on port 0x0001bc07
[    7.320000] NFORCE-MCP55: IDE controller at PCI slot 0000:00:04.0
[    7.320000] NFORCE-MCP55: chipset revision 161
[    7.320000] NFORCE-MCP55: not 100% native mode: will probe irqs later
[    7.320000] NFORCE-MCP55: 0000:00:04.0 (rev a1) UDMA133 controller
[    7.320000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[    7.320000] Probing IDE interface ide0...
[    7.336000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[    7.336000] sda: Write Protect is off
[    7.336000] sda: Mode Sense: 00 3a 00 00
[    7.336000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.336000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[    7.336000] sda: Write Protect is off
[    7.336000] sda: Mode Sense: 00 3a 00 00
[    7.336000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.336000]  sda: sda1
[    7.352000] sd 0:0:0:0: Attached scsi disk sda
[    7.352000] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[    7.352000] sdb: Write Protect is off
[    7.352000] sdb: Mode Sense: 00 3a 00 00
[    7.352000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.352000] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[    7.352000] sdb: Write Protect is off
[    7.352000] sdb: Mode Sense: 00 3a 00 00
[    7.352000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.352000]  sdb: sdb1 sdb2
[    7.388000] sd 1:0:0:0: Attached scsi disk sdb
[    7.392000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.392000] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    7.392000] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    7.400000] sr0: scsi3-mmc drive: 0x/52x writer cd/rw xa/form2 cdda tray
[    7.400000] Uniform CD-ROM driver Revision: 3.20
[    7.400000] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    7.608000] Attempting manual resume
[    7.608000] swsusp: Resume From Partition 8:17
[    7.608000] PM: Checking swsusp image.
[    7.628000] PM: Resume from disk failed.
[    7.664000] kjournald starting.  Commit interval 5 seconds
[    7.664000] EXT3-fs: mounted filesystem with ordered data mode.
[   15.476000] NET: Registered protocol family 10
[   15.476000] lo: Disabled Privacy Extensions
[   16.552000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   16.552000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   16.568000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.568000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.792000] parport: PnPBIOS parport detected.
[   16.792000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   16.908000] input: PC Speaker as /class/input/input6
[   17.060000] usbcore: registered new interface driver xpad
[   17.060000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   17.096000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.124000] Linux video capture interface: v2.00
[   17.264000] pwc: Philips webcam module version 10.0.12 loaded.
[   17.264000] pwc: Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[   17.264000] pwc: Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[   17.264000] pwc: the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[   17.312000] nvidia: module license 'NVIDIA' taints kernel.
[   17.564000] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[   17.564000] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [APC6] -> GSI 16 (level, low) -> IRQ 20
[   17.564000] PCI: Setting latency timer of device 0000:07:00.0 to 64
[   17.564000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
[   17.604000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   17.604000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 21
[   17.604000] Audigy2 value: Special config.
[   17.676000] usbcore: registered new interface driver snd-usb-audio
[   17.676000] pwc: Logitech QuickCam Pro 3000 USB webcam detected.
[   17.708000] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   17.708000] ACPI: PCI Interrupt 0000:00:06.1[B] -> Link [AAZA] -> GSI 21 (level, low) -> IRQ 18
[   17.708000] PCI: Setting latency timer of device 0000:00:06.1 to 64
[   17.712000] pwc: Registered as /dev/video0.
[   17.716000] usbcore: registered new interface driver Philips webcam
[   18.240000] fuse init (API version 7.8)
[   18.268000] lp0: using parport0 (interrupt-driven).
[   18.300000] Adding 971924k swap on /dev/disk/by-uuid/0da1ce20-bee7-44d9-a17b-49ddbbe416b8.  Priority:-1 extents:1 across:971924k
[   18.472000] EXT3 FS on sdb2, internal journal
[   18.684000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   18.716000] NTFS volume version 3.1.
[   20.044000] NET: Registered protocol family 17
[   23.976000] Using specific hotkey driver
[   24.120000] ibm_acpi: ec object not found
[   24.216000] No dock devices found.
[   24.232000] input: Power Button (FF) as /class/input/input7
[   24.232000] ACPI: Power Button (FF) [PWRF]
[   24.232000] input: Power Button (CM) as /class/input/input8
[   24.232000] ACPI: Power Button (CM) [PWRB]
[   24.276000] pcc_acpi: loading...
[   24.464000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (version 2.00.00)
[   24.464000] powernow-k8: MP systems not supported by PSB BIOS structure
[   24.464000] powernow-k8: MP systems not supported by PSB BIOS structure
[   25.768000] eth0: no IPv6 routers present
[   31.628000] ppdev: user-space parallel port driver
[   32.136000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   32.136000] apm: disabled - APM is not SMP safe.
[   32.296000] Bluetooth: Core ver 2.11
[   32.296000] NET: Registered protocol family 31
[   32.296000] Bluetooth: HCI device and connection manager initialized
[   32.296000] Bluetooth: HCI socket layer initialized
[   32.324000] Bluetooth: L2CAP ver 2.8
[   32.324000] Bluetooth: L2CAP socket layer initialized
[   32.332000] Bluetooth: RFCOMM socket layer initialized
[   32.332000] Bluetooth: RFCOMM TTY layer initialized
[   32.332000] Bluetooth: RFCOMM ver 1.8

```

---

### Post by atari05 on 2007-05-12
For good measure, my Xorg.conf also

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        BusID           "PCI:0:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666

```

---

### Post by MartinN on 2007-05-16
Your problem is one line above the line starting with "(EE)"

> **atari05 said:**
> 
```


(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:23:13 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 07:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:7:0:0) found
(EE) No devices detected.

Fatal server error:
no screens found

```


> 
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        BusID           "PCI:0:5:0"
EndSection

The failure is in your configuration, the above section says, use the nvidia driver for the graphic card with the pci-id 0:5:0 but referring to the output of your log file it should be 7:00:0.
You can remove the BusID line if you've got just one graphic card in your computer, an other way is to check for the correct ID with the help of
```

lspci|grep -i nvidia 

```
on a console application.
This should fix your problem.

---

