---
title: "Black screen after ctrl+alt+f1 and back to ctrl+alt+f7"
date: 2007-11-24
forum: General Help
---

### Post by ekravche on 2007-11-24
Hello,

I get a black screen after ctrl+alt+f1 and then back to X windows using ctrl+alt+f7. I tried to ctrl+alt+backspace, but X just shows a black screen. I can still switch to ctrl+alt+f1 and work from the console, but I can't do anything in X. I posted a bug report here [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/68546](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/68546) but the problem hasn't been addressed. I'm wondering if anyone else has seen this, and what you have done to resolve it. I just end up doing sudo shutdown -r now, which restarts the machine. Kind of annoying to have to do that :(

------------------------------------------

Finally after years of having to deal with this issue I found how to resolve it without having to restart your machine.

Press ctrl+alt+f1 to go to the console. Login in as root or a user that has super user privilages. Type the following
```

/etc/init.d/gdm stop

Followed by 

[CODE]
/etc/init.d/gdm start

```

Your xorg should now be as good as new :) Happy ubuntuing :D

If that doesn't work try 

```

/etc/init.d/gdm force-reload

```

If that doesn't work try
```

/etc/init.d/gdm stop
startx

```

---

### Post by banewman on 2007-11-24
After ctrl-al-F...   to get back is just  alt-F7
Hope it helps :)

---

### Post by ekravche on 2007-11-24
> **banewman said:**
> After ctrl-al-F...   to get back is just  alt-F7
Hope it helps :)

That's great the only problem is that ctrl+alt+f7 or even alt+f7 would show a black screen... That is X hangs... And I need to restart the entire system. There is also a restartx command, but it only works when X is not active.

---

### Post by banewman on 2007-11-24
I think what you need is to type -
killx     -or something similar
then -
restartx
then alt-F7
:)

---

### Post by xeth_delta on 2007-11-24
What is the output of
```
cat /var/log/Xorg.0.log
```

or the equivalent log file?

---

### Post by posterboy on 2007-11-24
Yes, I experience this reliably. Very annoying. .So much so, I have tried to avoid the console. It simply won't recover the X session.This worked on 7.04, but not 7.10. I have no idea what to do about this. Anyone?

---

### Post by mali2297 on 2007-11-24
I have a somewhat similar problem in Feisty. Although the screen isn't black, rather psychedelic. My "solution" is to turn the screen off/on:
```

xset dpms force off

```
I have made this into a keyboard shortcut.

I don't know if it will help you guys, but it might be worth a shot.

---

### Post by ekravche on 2007-11-25
> **mali2297 said:**
> I have a somewhat similar problem in Feisty. Although the screen isn't black, rather psychedelic. My "solution" is to turn the screen off/on:
```

xset dpms force off

```
I have made this into a keyboard shortcut.

I don't know if it will help you guys, but it might be worth a shot.

Doesn't work for me...

---

### Post by FuturePilot on 2007-11-25
Do you have a Nvidia card? This is a known issue in their driver. The next release should fix it.

---

### Post by ekravche on 2007-11-25
> **FuturePilot said:**
> Do you have a Nvidia card? This is a known issue in their driver. The next release should fix it.

I have an intel 82915G/GV/910GL Express Chipset Family Graphics Controller which is using the i810 driver

---

### Post by ekravche on 2007-11-25
> **xeth_delta said:**
> What is the output of
```
cat /var/log/Xorg.0.log
```

or the equivalent log file?

Here is the output 

```


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux evgeny-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 24 23:05:23 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SyncMaster"
(**) |   |-->Device "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
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
(II) PCI: 00:00:0: chip 8086,2580 card 8086,2580 rev 0e class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2582 card 1462,7036 rev 0e class 03,00,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,2658 card 1462,7036 rev 04 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 1462,7036 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 1462,7036 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 1462,7036 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 1462,7036 rev 04 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev d4 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,266e card 1462,7036 rev 04 class 04,01,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,2640 card 8086,2640 rev 04 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 1462,7036 rev 04 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2651 card 1462,7036 rev 04 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 1462,7036 rev 04 class 0c,05,00 hdr 00
(II) PCI: 01:01:0: chip 1095,0680 card 1095,3680 rev 02 class 01,04,00 hdr 00
(II) PCI: 01:02:0: chip 1814,0201 card 1737,0032 rev 01 class 02,80,00 hdr 00
(II) PCI: 01:09:0: chip 104c,8024 card 1462,036d rev 00 class 0c,00,10 hdr 00
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
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd00fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x20000000 - 0x200fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82915G/GV/910GL Integrated Graphics Controller rev 14, Mem @ 0xd0100000/19, 0xc0000000/28, 0xd0180000/18, I/O @ 0xe400/3
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
	[0] -1	0	0xd0080000 - 0xd0083fff (0x4000) MX[B]
	[1] -1	0	0xd0088000 - 0xd00887ff (0x800) MX[B]
	[2] -1	0	0xd0084000 - 0xd0085fff (0x2000) MX[B]
	[3] -1	0	0xd0086000 - 0xd00860ff (0x100) MX[B]
	[4] -1	0	0xd01c2000 - 0xd01c20ff (0x100) MX[B]
	[5] -1	0	0xd01c1000 - 0xd01c11ff (0x200) MX[B]
	[6] -1	0	0xd01c0000 - 0xd01c03ff (0x400) MX[B]
	[7] -1	0	0xd0180000 - 0xd01bffff (0x40000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xd0100000 - 0xd017ffff (0x80000) MX[B](B)
	[10] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[11] -1	0	0x0000d300 - 0x0000d303 (0x4) IX[B]
	[12] -1	0	0x0000d200 - 0x0000d207 (0x8) IX[B]
	[13] -1	0	0x0000d100 - 0x0000d103 (0x4) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[15] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[16] -1	0	0x0000ed00 - 0x0000ed0f (0x10) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec03 (0x4) IX[B]
	[18] -1	0	0x0000eb00 - 0x0000eb07 (0x8) IX[B]
	[19] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[20] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000e600 - 0x0000e63f (0x40) IX[B]
	[27] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[28] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[29] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[30] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[32] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd0080000 - 0xd0083fff (0x4000) MX[B]
	[1] -1	0	0xd0088000 - 0xd00887ff (0x800) MX[B]
	[2] -1	0	0xd0084000 - 0xd0085fff (0x2000) MX[B]
	[3] -1	0	0xd0086000 - 0xd00860ff (0x100) MX[B]
	[4] -1	0	0xd01c2000 - 0xd01c20ff (0x100) MX[B]
	[5] -1	0	0xd01c1000 - 0xd01c11ff (0x200) MX[B]
	[6] -1	0	0xd01c0000 - 0xd01c03ff (0x400) MX[B]
	[7] -1	0	0xd0180000 - 0xd01bffff (0x40000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xd0100000 - 0xd017ffff (0x80000) MX[B](B)
	[10] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[11] -1	0	0x0000d300 - 0x0000d303 (0x4) IX[B]
	[12] -1	0	0x0000d200 - 0x0000d207 (0x8) IX[B]
	[13] -1	0	0x0000d100 - 0x0000d103 (0x4) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[15] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[16] -1	0	0x0000ed00 - 0x0000ed0f (0x10) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec03 (0x4) IX[B]
	[18] -1	0	0x0000eb00 - 0x0000eb07 (0x8) IX[B]
	[19] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[20] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000e600 - 0x0000e63f (0x40) IX[B]
	[27] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[28] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[29] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[30] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[32] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B](B)
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
	[4] -1	0	0xd0080000 - 0xd0083fff (0x4000) MX[B]
	[5] -1	0	0xd0088000 - 0xd00887ff (0x800) MX[B]
	[6] -1	0	0xd0084000 - 0xd0085fff (0x2000) MX[B]
	[7] -1	0	0xd0086000 - 0xd00860ff (0x100) MX[B]
	[8] -1	0	0xd01c2000 - 0xd01c20ff (0x100) MX[B]
	[9] -1	0	0xd01c1000 - 0xd01c11ff (0x200) MX[B]
	[10] -1	0	0xd01c0000 - 0xd01c03ff (0x400) MX[B]
	[11] -1	0	0xd0180000 - 0xd01bffff (0x40000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xd0100000 - 0xd017ffff (0x80000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[17] -1	0	0x0000d300 - 0x0000d303 (0x4) IX[B]
	[18] -1	0	0x0000d200 - 0x0000d207 (0x8) IX[B]
	[19] -1	0	0x0000d100 - 0x0000d103 (0x4) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[21] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[22] -1	0	0x0000ed00 - 0x0000ed0f (0x10) IX[B]
	[23] -1	0	0x0000ec00 - 0x0000ec03 (0x4) IX[B]
	[24] -1	0	0x0000eb00 - 0x0000eb07 (0x8) IX[B]
	[25] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[26] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[27] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x0000e600 - 0x0000e63f (0x40) IX[B]
	[33] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[34] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[35] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[36] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[38] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B](B)
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.7.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
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
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
(II) Primary Device is: PCI 00:02:0
(--) Chipset 915G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0080000 - 0xd0083fff (0x4000) MX[B]
	[5] -1	0	0xd0088000 - 0xd00887ff (0x800) MX[B]
	[6] -1	0	0xd0084000 - 0xd0085fff (0x2000) MX[B]
	[7] -1	0	0xd0086000 - 0xd00860ff (0x100) MX[B]
	[8] -1	0	0xd01c2000 - 0xd01c20ff (0x100) MX[B]
	[9] -1	0	0xd01c1000 - 0xd01c11ff (0x200) MX[B]
	[10] -1	0	0xd01c0000 - 0xd01c03ff (0x400) MX[B]
	[11] -1	0	0xd0180000 - 0xd01bffff (0x40000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xd0100000 - 0xd017ffff (0x80000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[17] -1	0	0x0000d300 - 0x0000d303 (0x4) IX[B]
	[18] -1	0	0x0000d200 - 0x0000d207 (0x8) IX[B]
	[19] -1	0	0x0000d100 - 0x0000d103 (0x4) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[21] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[22] -1	0	0x0000ed00 - 0x0000ed0f (0x10) IX[B]
	[23] -1	0	0x0000ec00 - 0x0000ec03 (0x4) IX[B]
	[24] -1	0	0x0000eb00 - 0x0000eb07 (0x8) IX[B]
	[25] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[26] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[27] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x0000e600 - 0x0000e63f (0x40) IX[B]
	[33] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[34] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[35] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[36] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[38] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0080000 - 0xd0083fff (0x4000) MX[B]
	[5] -1	0	0xd0088000 - 0xd00887ff (0x800) MX[B]
	[6] -1	0	0xd0084000 - 0xd0085fff (0x2000) MX[B]
	[7] -1	0	0xd0086000 - 0xd00860ff (0x100) MX[B]
	[8] -1	0	0xd01c2000 - 0xd01c20ff (0x100) MX[B]
	[9] -1	0	0xd01c1000 - 0xd01c11ff (0x200) MX[B]
	[10] -1	0	0xd01c0000 - 0xd01c03ff (0x400) MX[B]
	[11] -1	0	0xd0180000 - 0xd01bffff (0x40000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xd0100000 - 0xd017ffff (0x80000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[20] -1	0	0x0000d300 - 0x0000d303 (0x4) IX[B]
	[21] -1	0	0x0000d200 - 0x0000d207 (0x8) IX[B]
	[22] -1	0	0x0000d100 - 0x0000d103 (0x4) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[24] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[25] -1	0	0x0000ed00 - 0x0000ed0f (0x10) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ec03 (0x4) IX[B]
	[27] -1	0	0x0000eb00 - 0x0000eb07 (0x8) IX[B]
	[28] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[29] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x0000e600 - 0x0000e63f (0x40) IX[B]
	[36] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[37] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[38] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[39] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[40] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[41] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 32448 kB
(II) I810(0): VESA VBE OEM: Intel(r)915G/915GV/910GL Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915G/915GV/910GL Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 915G
(--) I810(0): Chipset: "915G"
(--) I810(0): Linear framebuffer at 0xC0000000
(--) I810(0): IO registers at addr 0xD0100000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 32508 kB stolen memory.
(II) I810(0): Kernel reported 104704 total, 1 used
(II) I810(0): I830CheckAvailableMemory: 418812 kB available
(II) I810(0): Will try to reserve 32768 kiB of AGP aperture space
	for the DRM memory manager.
(--) I810(0): Pre-allocated VideoRAM: 32508 kByte
(==) I810(0): VideoRAM: 65536 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 3414
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
	      If you encounter this problem please add 
		 Option "DisplayInfo" "FALSE"
	      to the Device section of your XF86Config file.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0): 	CRT
(II) I810(0): No active displays on Pipe B.
(==) I810(0): Display is using Pipe A
(--) I810(0): Maximum frambuffer space: 65368 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: SAM  Model: 125  Serial#: 1196634423
(II) I810(0): Year: 2005  Week: 4
(II) I810(0): EDID Version: 1.3
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) I810(0): Sync:  Separate  Composite
(II) I810(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) I810(0): Gamma: 2.20
(II) I810(0): DPMS capabilities: Off; RGB/Color Display
(II) I810(0): First detailed timing is preferred mode
(II) I810(0): redX: 0.633 redY: 0.351   greenX: 0.298 greenY: 0.592
(II) I810(0): blueX: 0.143 blueY: 0.092   whiteX: 0.316 whiteY: 0.337
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@67Hz
(II) I810(0): 640x480@72Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@56Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 800x600@72Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 832x624@75Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@70Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): 1280x1024@75Hz
(II) I810(0): 1152x870@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) I810(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) I810(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) I810(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) I810(0): Monitor name: SyncMaster
(II) I810(0): Serial No: H9NY150964
(II) I810(0): EDID (in hex):
(II) I810(0): 	00ffffffffffff004c2d250137315347
(II) I810(0): 	040f01036c221b782a36a1a2594c9724
(II) I810(0): 	175156bfef808180714f010101010101
(II) I810(0): 	010101010101302a009851002a403070
(II) I810(0): 	1300520e1100001e000000fd00384b1e
(II) I810(0): 	510e000a202020202020000000fc0053
(II) I810(0): 	796e634d61737465720a2020000000ff
(II) I810(0): 	0048394e593135303936340a202000c2
(II) I810(0): Using EDID range info for horizontal sync
(II) I810(0): Using EDID range info for vertical refresh
(II) I810(0): Printing DDC gathered Modelines:
(II) I810(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) I810(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) I810(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) I810(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) I810(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) I810(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) I810(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) I810(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) I810(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) I810(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) I810(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) I810(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) I810(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) I810(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) I810(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) I810(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) I810(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) I810(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) I810(0): Will use BIOS call 0x5f05 to set refresh rates for CRTs.
(--) I810(0): Maximum space available for video modes: 32448 kByte
(II) I810(0): Using detected DDC timings
(II) I810(0): 	HorizSync 30-81
(II) I810(0): 	VertRefresh 56-75
Mode: 30 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
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
	NumberOfImages: 100
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 100
	LinNumberOfImagePages: 100
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 32 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
	BytesPerScanline: 832
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 62
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 832
	BnkNumberOfImagePages: 62
	LinNumberOfImagePages: 62
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 34 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
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
	NumberOfImages: 41
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 41
	LinNumberOfImagePages: 41
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 38 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
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
	NumberOfImages: 24
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 24
	LinNumberOfImagePages: 24
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 3a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
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
	NumberOfImages: 16
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 3c (1920x1440)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
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
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1920
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
	MaxPixelClock: 230000000
Mode: 41 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
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
	NumberOfImages: 55
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 55
	LinNumberOfImagePages: 55
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 43 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 32
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 32
	LinNumberOfImagePages: 32
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 45 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
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
	NumberOfImages: 20
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 20
	LinNumberOfImagePages: 20
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 49 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
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
	NumberOfImages: 11
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 4b (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
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
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3200
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
	MaxPixelClock: 230000000
Mode: 4d (1920x1440)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
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
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3840
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
	MaxPixelClock: 230000000
*(II) I810(0): Not using mode "640x480" (vrefresh out of range)
Mode: 50 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
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
	NumberOfImages: 25
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 25
	LinNumberOfImagePages: 25
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(II) I810(0): Not using mode "800x600" (vrefresh out of range)
Mode: 52 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(II) I810(0): Not using mode "1024x768" (vrefresh out of range)
Mode: 54 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
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
	NumberOfImages: 9
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(II) I810(0): Not using mode "1280x1024" (hsync out of range)
Mode: 58 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
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
	NumberOfImages: 5
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(II) I810(0): Not using mode "1600x1200" (mode clock too high)
(II) I810(0): Not using mode "1600x1200" (mode clock too high)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (mode clock too high)
(II) I810(0): Not using mode "1600x1200" (mode clock too high)
(II) I810(0): Not using mode "1600x1200" (mode clock too high)
(II) I810(0): Not using mode "1600x1200" (mode clock too high)
(II) I810(0): Not using mode "1600x1200" (mode clock too high)
(II) I810(0): Not using mode "1600x1200" (mode clock too high)
(II) I810(0): Not using mode "1600x1200" (mode clock too high)
(II) I810(0): Not using mode "1600x1200" (mode clock too high)
(II) I810(0): Not using mode "1600x1200" (mode clock too high)
(II) I810(0): Not using mode "1600x1200" (mode clock too high)
(II) I810(0): Not using mode "1600x1200" (mode clock too high)
(II) I810(0): Not using mode "1600x1200" (mode clock too high)
Mode: 5a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
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
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
(II) I810(0): Not using mode "1920x1440" (hsync out of range)
Mode: 5c (1920x1440)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000575e
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
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 7680
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 60 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 61 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 62 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 63 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 64 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 65 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 66 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 67 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 68 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
(II) I810(0): SyncMaster: Using hsync range of 30.00-81.00 kHz
(II) I810(0): SyncMaster: Using vrefresh range of 56.00-75.00 Hz
(II) I810(0): Not using mode "1152x864" (no mode of this name)
(II) I810(0): Not using mode "832x624" (no mode of this name)
(II) I810(0): Not using mode "720x400" (no mode of this name)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(--) I810(0): Virtual size is 1280x1024 (pitch 2048)
(**) I810(0): *Built-in mode "1280x1024"
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(II) I810(0): Attempting to use 75.02Hz refresh for mode "1280x1024" (858)
(II) I810(0): Attempting to use 75.03Hz refresh for mode "1024x768" (854)
(II) I810(0): Attempting to use 75.00Hz refresh for mode "800x600" (852)
(II) I810(0): Attempting to use 75.00Hz refresh for mode "640x480" (850)
(**) I810(0): Display dimensions: (340, 270) mm
(**) I810(0): DPI set to (95, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) I810(0): VBE Restore workaround: enabled.
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0180000 - 0xd01bffff (0x40000) MS[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MS[B]
	[2] 0	0	0xd0100000 - 0xd017ffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xd0080000 - 0xd0083fff (0x4000) MX[B]
	[8] -1	0	0xd0088000 - 0xd00887ff (0x800) MX[B]
	[9] -1	0	0xd0084000 - 0xd0085fff (0x2000) MX[B]
	[10] -1	0	0xd0086000 - 0xd00860ff (0x100) MX[B]
	[11] -1	0	0xd01c2000 - 0xd01c20ff (0x100) MX[B]
	[12] -1	0	0xd01c1000 - 0xd01c11ff (0x200) MX[B]
	[13] -1	0	0xd01c0000 - 0xd01c03ff (0x400) MX[B]
	[14] -1	0	0xd0180000 - 0xd01bffff (0x40000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xd0100000 - 0xd017ffff (0x80000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] 0	0	0x0000e400 - 0x0000e407 (0x8) IS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[24] -1	0	0x0000d300 - 0x0000d303 (0x4) IX[B]
	[25] -1	0	0x0000d200 - 0x0000d207 (0x8) IX[B]
	[26] -1	0	0x0000d100 - 0x0000d103 (0x4) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[28] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[29] -1	0	0x0000ed00 - 0x0000ed0f (0x10) IX[B]
	[30] -1	0	0x0000ec00 - 0x0000ec03 (0x4) IX[B]
	[31] -1	0	0x0000eb00 - 0x0000eb07 (0x8) IX[B]
	[32] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[33] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[34] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[39] -1	0	0x0000e600 - 0x0000e63f (0x40) IX[B]
	[40] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[41] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[42] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[43] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[44] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[45] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B](B)
	[46] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[47] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 32448 kB
(II) I810(0): VESA VBE OEM: Intel(r)915G/915GV/910GL Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915G/915GV/910GL Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Allocated 128 kB for the ring buffer at 0x0
(II) I810(0): Allocating at least 256 scanlines for pixmap cache
(II) I810(0): Initial framebuffer allocation size: 12288 kByte
(II) I810(0): Allocated 4 kB for HW cursor at 0xdfff000 (0x15fab000)
(II) I810(0): Allocated 16 kB for HW (ARGB) cursor at 0xdffb000 (0x15db8000)
(II) I810(0): Allocated 4 kB for Overlay registers at 0xdffa000 (0x1cd40000).
(II) I810(0): Allocated 64 kB for the scratch buffer at 0xdfea000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) I810(0): [drm] loaded kernel module for "i915" driver
(II) I810(0): [drm] DRM interface version 1.3
(II) I810(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) I810(0): [drm] added 8192 byte SAREA at 0xdeccd000
(II) I810(0): [drm] mapped SAREA 0xdeccd000 to 0xb7f4f000
(II) I810(0): [drm] framebuffer handle = 0xc0020000
(II) I810(0): [drm] added 1 reserved context for kernel
(II) I810(0): Allocated 32 kB for the logical context at 0xdfe2000.
(II) I810(0): Allocated 8192 kB for the back buffer at 0xd000000.
(II) I810(0): Allocated 8192 kB for the depth buffer at 0xc800000.
(II) I810(0): Allocated 36608 kB for textures at 0xc20000
(II) I810(0): 0x8218100: Memory at offset 0x00020000, size 12288 kBytes
(II) I810(0): 0x8218a20: Memory at offset 0x0dfff000, size 4 kBytes
(II) I810(0): 0x8217730: Memory at offset 0x0dffb000, size 16 kBytes
(II) I810(0): 0x821775c: Memory at offset 0x00000000, size 128 kBytes
(II) I810(0): 0x8218140: Memory at offset 0x0dfea000, size 64 kBytes
(II) I810(0): 0x8218f18: Memory at offset 0x0dffa000, size 4 kBytes
(II) I810(0): 0x82182d8: Memory at offset 0x0dfe2000, size 32 kBytes
(II) I810(0): 0x82182f8: Memory at offset 0x0d000000, size 8192 kBytes
(II) I810(0): 0x8218318: Memory at offset 0x0c800000, size 8192 kBytes
(II) I810(0): 0x8218338: Memory at offset 0x00c20001, size 36608 kBytes
(II) I810(0): Activating tiled memory for the back buffer.
(II) I810(0): Activating tiled memory for the depth buffer.
(II) I810(0): [drm] Registers = 0xd0100000
(II) I810(0): [drm] ring buffer = 0xc0000000
(II) I810(0): [drm] init sarea width,height = 1280 x 1024 (pitch 2048)
(II) I810(0): [drm] Mapping front buffer
(II) I810(0): [drm] Front Buffer = 0x28004000
(II) I810(0): [drm] Back Buffer = 0xcd000000
(II) I810(0): [drm] Depth Buffer = 0xcc800000
(II) I810(0): [drm] textures = 0xc0c20000
(II) I810(0): [drm] Initialized kernel agp heap manager, 37486592
(II) I810(0): [dri] visual configs initialized
(==) I810(0): Write-combining range (0xc0000000,0x10000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(0): Extended BIOS function 0x5f05 not supported.
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x01fbf000 (pgoffset 8127)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0dfff000 (pgoffset 57343)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0dffb000 (pgoffset 57339)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0dfea000 (pgoffset 57322)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0dffa000 (pgoffset 57338)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x0dfe2000 (pgoffset 57314)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x0d000000 (pgoffset 53248)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x0c800000 (pgoffset 51200)
(WW) I810(0): Extended BIOS function 0x5f05 not supported.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.
(II) I810(0): Setting refresh with VBE 3 method.
(II) I810(0): Display plane A is enabled and connected to Pipe A.
(II) I810(0): Display plane B is disabled and connected to Pipe B.
(II) I810(0): Enabling plane A.
(II) I810(0): Display plane A is now enabled and connected to Pipe A.
(II) I810(0): Display plane B is now disabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x80000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 78 Mpixel/s
(WW) I810(0): Extended BIOS function 0x5f28 not supported.
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
(II) I810(0): Initializing HW Cursor
(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): Set up overlay video
(II) I810(0): Set up textured video
(II) I810(0): X context handle = 0x1
(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): [DRI] installation complete
(II) I810(0): [drm] dma control initialized, using IRQ 19
(II) I810(0): direct rendering: Enabled
(II) I810(0): RandR enabled, ignore the following RandR disabled message.
(II) I810(0): Rotating to 0 degrees
(--) RandR disabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
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
(**) Configured Mouse: Sensitivity: 1
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
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!


```

---

### Post by ekravche on 2007-11-25
Finally after years of having to deal with this issue I found how to resolve it without having to restart your machine.

Press ctrl+alt+f1 to go to the console. Login in as root or a user that has super user privilages. Type the following
```

/etc/init.d/gdm stop

```

Followed by 

```

/etc/init.d/gdm start

```

Your xorg should now be as good as new :) Happy ubuntuing :D

If that doesn't work try 

```

/etc/init.d/gdm force-reload

```

if that doesn't work try
```

/etc/init.d/gdm stop
startx

```

---

