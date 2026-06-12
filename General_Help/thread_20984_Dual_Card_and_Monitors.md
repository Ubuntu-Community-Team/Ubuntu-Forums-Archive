---
title: "Dual Card and Monitors"
date: 2005-03-19
forum: General Help
---

### Post by datacaliber on 2005-03-19
I have a GeForce 3 card (AGP) and a GeForce FX5200 (PCI). I am trying to get both to work on Hoary. The GeForce 3 works fine by itself but X -configure gives me the error below. X -configure properly sets up my cards in Warty and in FreeBSD5.3 which uses Xorg. Any idea why Xorg would work in freebsd and not Hoary?

Sorry for the repost.

> X Window System Version 6.8.2 (Ubuntu 6.8.2-5.1 20050317074038 root@)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.8.1 i686 [ELF] 
Current Operating System: Linux Magnum 2.6.10-5-386 #1 Tue Mar 15 14:43:37 UTC 2005 i686
Build Date: 17 March 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@rothera) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Mar 15 14:43:37 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 19 17:45:02 2005
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
(--) using VT number 2

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2578 card 1043,80f6 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2579 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 8086,257b card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1043,80a6 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1043,80a6 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1043,80a6 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 1043,80a6 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1043,80a6 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1043,80f3 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0200 card 1681,0040 rev a3 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 8086,1019 card 1043,80f7 rev 00 class 02,00,00 hdr 00
(II) PCI: 03:03:0: chip 1106,3044 card 1043,808a rev 46 class 0c,00,10 hdr 00
(II) PCI: 03:04:0: chip 105a,3373 card 1043,80f5 rev 02 class 01,04,00 hdr 00
(II) PCI: 03:0b:0: chip 10de,0322 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf3c00000 - 0xf5cfffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd3a00000 - 0xdbafffff (0x8100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf5d00000 - 0xf5dfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xf5e00000 - 0xf7efffff (0x2100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xdbb00000 - 0xebafffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV20 [GeForce3] rev 163, Mem @ 0xf4000000/24, 0xd4000000/26, 0xdba80000/19, BIOS @ 0xf5cf0000/16
(--) PCI: (3:11:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xf6000000/24, 0xe0000000/27, BIOS @ 0xf7ea0000/17
Missing output drivers.  Configuration failed.

---

### Post by emuman on 2005-03-21
Do you use the nvidia closed source driver or the built in nv driver?

---

### Post by datacaliber on 2005-03-23
[QUOTE=emuman]Do you use the nvidia closed source driver or the built in nv driver?[/QUOTE]
 Problem persists with both drivers. I even tried with the new ones.

---

