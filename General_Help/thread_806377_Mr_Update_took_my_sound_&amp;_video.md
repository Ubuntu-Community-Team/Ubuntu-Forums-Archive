---
title: "Mr Update took my sound &amp; video"
date: 2008-05-24
forum: General Help
---

### Post by RefleXX on 2008-05-24
Yeah well, I'm on Ubuntu Hardy (AMD 64) which I just installed. I had experienced some troubles with it after updating it so I decided to reinstall and so I did.

After the re installation it asked me to update with the update-manager, which I did. System was fully updated and I rebooted - woho. When I came back in, I decided I wanted to install my nvidia drivers - but uh-oh! They weren't there. The hardware driver manager / restricted drivers manager was there in the administration menus, but it no longer found the drivers for me, it found nothing. Then I noticed that my sound was muted, and when I tried to go into sound options, it seemed that I no longer had a sound card, if I was to trust my computer.

Where did my sound go? And what happened to my not-installed nvidia drivers that I wanted?

Helps and ideas appreciated! :)

Regards,
RefleXX


EDIT: I found a post that fixed my sound problem, if anyone else is experiencing this, the post is here: [http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/](http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/)
the nvidia driver problem is still there though :/

---

### Post by ibuclaw on 2008-05-24
Which card do you have?

Have you tried just manually installing them?

Presuming that you have a PCI-Express card (Say, 8500GT for example)
Then you'll probably need the new drivers:
```
sudo apt-get install nvidia-glx-new
```

Regards
Iain

---

### Post by RefleXX on 2008-05-24
I have an nvidia 8800 GTX. 

I tried installing manually, but it didn't set them to default, so I ran nvidia-xconfig. After rebooting, it seemingly tried to start X several times but failed and eventually it started - in low graphic mode. I had that problem before I reinstalled Hardy, that was the reason I reinstalled it. If I run with those nvidia drivers, it goes completely black and I can't do anything, so I had to go into recovery kernel with root command and put back my old xorg.conf...

---

### Post by RefleXX on 2008-05-24
Sorry for the double post.

I tried running that command (I had done it in synaptic) and it installed it as if it wasn't installed, and removed nvidia-xconfig (no clue why), but after restarting X, still nothing. Starting nvidia-settings said I wasn't using the nvidia drivers and that I should do nvidia-xconfig, but that's where the problem started..

Also, when trying to use the nvidia drivers instead of i.e vesa, I either get a black screen nothing happening, or I get a "Low Graphic Mode" saying I need to configure my settings, and if I set them to use nvidia, well, black screen... These are my Xorg.0.log and Xorg.0.log.old:

Xorg.0.log:
```



This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.1)
Current Operating System: Linux poni 2.6.24-17-server #1 SMP Thu May 1 14:28:06 UTC 2008 x86_64
Build Date: 21 May 2008  12:21:14PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 25 04:20:58 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,0369 card 1462,7250 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0360 card 1462,7250 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0368 card 1462,7250 rev a3 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,036c card 1462,7250 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,036d card 1462,7250 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,036e card f462,7250 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:05:0: chip 10de,037f card 1462,7250 rev a3 class 01,01,85 hdr 80
(II) PCI: 00:05:1: chip 10de,037f card 1462,7250 rev a3 class 01,01,85 hdr 80
(II) PCI: 00:05:2: chip 10de,037f card 1462,7250 rev a3 class 01,01,85 hdr 80
(II) PCI: 00:06:0: chip 10de,0370 card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:06:1: chip 10de,0371 card 1462,7250 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:08:0: chip 10de,0373 card 1462,7250 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0373 card 1462,7250 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0376 card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0b:0: chip 10de,0374 card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,0374 card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,0378 card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,0375 card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0f:0: chip 10de,0377 card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:04:0: chip 1106,3044 card 1462,250d rev 80 class 0c,00,10 hdr 00
(II) PCI: 07:00:0: chip 10de,0191 card 1682,2250 rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:6:0), (0,1,1), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf9f00000 - 0xf9ffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:10:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:11:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:12:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:13:0), (0,5,5), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:14:0), (0,6,6), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:15:0), (0,7,7), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 7 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfebfffff (0x4c00000) MX[B]
(II) Bus 7 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(7:0:0) nVidia Corporation G80 [GeForce 8800 GTX] rev 162, Mem @ 0xfd000000/24, 0xc0000000/28, 0xfa000000/25, I/O @ 0xec00/7, BIOS @ 0xfebe0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xf9fff800 - 0xf9ffffff (0x800) MX[B]
	[1] -1	0	0xf9ef4c00 - 0xf9ef4c0f (0x10) MX[B]
	[2] -1	0	0xf9efa000 - 0xf9efa0ff (0x100) MX[B]
	[3] -1	0	0xf9ef5000 - 0xf9ef5fff (0x1000) MX[B]
	[4] -1	0	0xf9efa400 - 0xf9efa40f (0x10) MX[B]
	[5] -1	0	0xf9efa800 - 0xf9efa8ff (0x100) MX[B]
	[6] -1	0	0xf9ef6000 - 0xf9ef6fff (0x1000) MX[B]
	[7] -1	0	0xf9ef0000 - 0xf9ef3fff (0x4000) MX[B]
	[8] -1	0	0xf9ef7000 - 0xf9ef7fff (0x1000) MX[B]
	[9] -1	0	0xf9ef8000 - 0xf9ef8fff (0x1000) MX[B]
	[10] -1	0	0xf9ef9000 - 0xf9ef9fff (0x1000) MX[B]
	[11] -1	0	0xf9efac00 - 0xf9efacff (0x100) MX[B]
	[12] -1	0	0xf9efb000 - 0xf9efbfff (0x1000) MX[B]
	[13] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[14] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[18] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[20] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[21] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[22] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[23] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[25] -1	0	0x0000b080 - 0x0000b08f (0x10) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[27] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[29] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[30] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[32] -1	0	0x0000c080 - 0x0000c087 (0x8) IX[B]
	[33] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[34] -1	0	0x0000c480 - 0x0000c487 (0x8) IX[B]
	[35] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[36] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[37] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[38] -1	0	0x00002900 - 0x0000293f (0x40) IX[B]
	[39] -1	0	0x00002f00 - 0x00002f7f (0x80) IX[B]
	[40] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf9fff800 - 0xf9ffffff (0x800) MX[B]
	[1] -1	0	0xf9ef4c00 - 0xf9ef4c0f (0x10) MX[B]
	[2] -1	0	0xf9efa000 - 0xf9efa0ff (0x100) MX[B]
	[3] -1	0	0xf9ef5000 - 0xf9ef5fff (0x1000) MX[B]
	[4] -1	0	0xf9efa400 - 0xf9efa40f (0x10) MX[B]
	[5] -1	0	0xf9efa800 - 0xf9efa8ff (0x100) MX[B]
	[6] -1	0	0xf9ef6000 - 0xf9ef6fff (0x1000) MX[B]
	[7] -1	0	0xf9ef0000 - 0xf9ef3fff (0x4000) MX[B]
	[8] -1	0	0xf9ef7000 - 0xf9ef7fff (0x1000) MX[B]
	[9] -1	0	0xf9ef8000 - 0xf9ef8fff (0x1000) MX[B]
	[10] -1	0	0xf9ef9000 - 0xf9ef9fff (0x1000) MX[B]
	[11] -1	0	0xf9efac00 - 0xf9efacff (0x100) MX[B]
	[12] -1	0	0xf9efb000 - 0xf9efbfff (0x1000) MX[B]
	[13] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[14] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[18] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[20] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[21] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[22] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[23] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[25] -1	0	0x0000b080 - 0x0000b08f (0x10) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[27] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[29] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[30] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[32] -1	0	0x0000c080 - 0x0000c087 (0x8) IX[B]
	[33] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[34] -1	0	0x0000c480 - 0x0000c487 (0x8) IX[B]
	[35] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[36] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[37] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[38] -1	0	0x00002900 - 0x0000293f (0x40) IX[B]
	[39] -1	0	0x00002f00 - 0x00002f7f (0x80) IX[B]
	[40] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
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
	[4] -1	0	0xf9fff800 - 0xf9ffffff (0x800) MX[B]
	[5] -1	0	0xf9ef4c00 - 0xf9ef4c0f (0x10) MX[B]
	[6] -1	0	0xf9efa000 - 0xf9efa0ff (0x100) MX[B]
	[7] -1	0	0xf9ef5000 - 0xf9ef5fff (0x1000) MX[B]
	[8] -1	0	0xf9efa400 - 0xf9efa40f (0x10) MX[B]
	[9] -1	0	0xf9efa800 - 0xf9efa8ff (0x100) MX[B]
	[10] -1	0	0xf9ef6000 - 0xf9ef6fff (0x1000) MX[B]
	[11] -1	0	0xf9ef0000 - 0xf9ef3fff (0x4000) MX[B]
	[12] -1	0	0xf9ef7000 - 0xf9ef7fff (0x1000) MX[B]
	[13] -1	0	0xf9ef8000 - 0xf9ef8fff (0x1000) MX[B]
	[14] -1	0	0xf9ef9000 - 0xf9ef9fff (0x1000) MX[B]
	[15] -1	0	0xf9efac00 - 0xf9efacff (0x100) MX[B]
	[16] -1	0	0xf9efb000 - 0xf9efbfff (0x1000) MX[B]
	[17] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[18] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[24] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[25] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[26] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[27] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[28] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[29] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[31] -1	0	0x0000b080 - 0x0000b08f (0x10) IX[B]
	[32] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[33] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[34] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[35] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[36] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[37] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[38] -1	0	0x0000c080 - 0x0000c087 (0x8) IX[B]
	[39] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[40] -1	0	0x0000c480 - 0x0000c487 (0x8) IX[B]
	[41] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[42] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[43] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[44] -1	0	0x00002900 - 0x0000293f (0x40) IX[B]
	[45] -1	0	0x00002f00 - 0x00002f7f (0x80) IX[B]
	[46] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:34:02 PST 2008
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) v4l driver for Video4Linux
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 07:00:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf9fff800 - 0xf9ffffff (0x800) MX[B]
	[5] -1	0	0xf9ef4c00 - 0xf9ef4c0f (0x10) MX[B]
	[6] -1	0	0xf9efa000 - 0xf9efa0ff (0x100) MX[B]
	[7] -1	0	0xf9ef5000 - 0xf9ef5fff (0x1000) MX[B]
	[8] -1	0	0xf9efa400 - 0xf9efa40f (0x10) MX[B]
	[9] -1	0	0xf9efa800 - 0xf9efa8ff (0x100) MX[B]
	[10] -1	0	0xf9ef6000 - 0xf9ef6fff (0x1000) MX[B]
	[11] -1	0	0xf9ef0000 - 0xf9ef3fff (0x4000) MX[B]
	[12] -1	0	0xf9ef7000 - 0xf9ef7fff (0x1000) MX[B]
	[13] -1	0	0xf9ef8000 - 0xf9ef8fff (0x1000) MX[B]
	[14] -1	0	0xf9ef9000 - 0xf9ef9fff (0x1000) MX[B]
	[15] -1	0	0xf9efac00 - 0xf9efacff (0x100) MX[B]
	[16] -1	0	0xf9efb000 - 0xf9efbfff (0x1000) MX[B]
	[17] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[18] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[24] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[25] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[26] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[27] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[28] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[29] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[31] -1	0	0x0000b080 - 0x0000b08f (0x10) IX[B]
	[32] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[33] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[34] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[35] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[36] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[37] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[38] -1	0	0x0000c080 - 0x0000c087 (0x8) IX[B]
	[39] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[40] -1	0	0x0000c480 - 0x0000c487 (0x8) IX[B]
	[41] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[42] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[43] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[44] -1	0	0x00002900 - 0x0000293f (0x40) IX[B]
	[45] -1	0	0x00002f00 - 0x00002f7f (0x80) IX[B]
	[46] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf9fff800 - 0xf9ffffff (0x800) MX[B]
	[5] -1	0	0xf9ef4c00 - 0xf9ef4c0f (0x10) MX[B]
	[6] -1	0	0xf9efa000 - 0xf9efa0ff (0x100) MX[B]
	[7] -1	0	0xf9ef5000 - 0xf9ef5fff (0x1000) MX[B]
	[8] -1	0	0xf9efa400 - 0xf9efa40f (0x10) MX[B]
	[9] -1	0	0xf9efa800 - 0xf9efa8ff (0x100) MX[B]
	[10] -1	0	0xf9ef6000 - 0xf9ef6fff (0x1000) MX[B]
	[11] -1	0	0xf9ef0000 - 0xf9ef3fff (0x4000) MX[B]
	[12] -1	0	0xf9ef7000 - 0xf9ef7fff (0x1000) MX[B]
	[13] -1	0	0xf9ef8000 - 0xf9ef8fff (0x1000) MX[B]
	[14] -1	0	0xf9ef9000 - 0xf9ef9fff (0x1000) MX[B]
	[15] -1	0	0xf9efac00 - 0xf9efacff (0x100) MX[B]
	[16] -1	0	0xf9efb000 - 0xf9efbfff (0x1000) MX[B]
	[17] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[18] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[27] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[28] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[29] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[30] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[31] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[32] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[33] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[34] -1	0	0x0000b080 - 0x0000b08f (0x10) IX[B]
	[35] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[36] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[37] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[38] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[39] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[40] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[41] -1	0	0x0000c080 - 0x0000c087 (0x8) IX[B]
	[42] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[43] -1	0	0x0000c480 - 0x0000c487 (0x8) IX[B]
	[44] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[45] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[46] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[47] -1	0	0x00002900 - 0x0000293f (0x40) IX[B]
	[48] -1	0	0x00002f00 - 0x00002f7f (0x80) IX[B]
	[49] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
	[50] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[51] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 14336 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 96.128
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G80 Board - p355h00 
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(**) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(**) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 10
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x33f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 2
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
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x33f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 1
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
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 106 (1280x1024)
	ModeAttributes: 0x33f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 160
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 1
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
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 107 (1280x1024)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 10e (320x200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10f (320x200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 111 (640x480)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 112 (640x480)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 114 (800x600)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 115 (800x600)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 117 (1024x768)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 118 (1024x768)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 11a (1280x1024)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 11b (1280x1024)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
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
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 320
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
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 132 (320x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 133 (320x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 135 (320x240)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 19
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 19
	LinNumberOfImagePages: 19
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 136 (320x240)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 13d (640x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 13e (640x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
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
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 2560
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
	MaxPixelClock: 229500000
Mode: 145 (1600x1200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 146 (1600x1200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 224 64KB banks (14336kB)
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-65.50 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-65.00 Hz
(II) VESA(0): Not using mode "1680x1050@60" (no mode of this name)
(II) VESA(0): Not using mode "1600x1024@60" (no mode of this name)
(II) VESA(0): Not using mode "1440x900@60" (no mode of this name)
(II) VESA(0): Not using mode "1280x800@60" (no mode of this name)
(II) VESA(0): Not using mode "1280x720@60" (no mode of this name)
(II) VESA(0): Not using mode "1280x768@60" (no mode of this name)
(II) VESA(0): Not using mode "800x600@60" (no mode of this name)
(II) VESA(0): Not using mode "800x600@56" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x200" (hsync out of range)
(**) VESA(0): Virtual size is 1680x1050 (pitch 1680)
(**) VESA(0):  Built-in mode "1280x1024"
(**) VESA(0):  Built-in mode "1024x768"
(**) VESA(0):  Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1280x1024" (11b)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf9fff800 - 0xf9ffffff (0x800) MX[B]
	[5] -1	0	0xf9ef4c00 - 0xf9ef4c0f (0x10) MX[B]
	[6] -1	0	0xf9efa000 - 0xf9efa0ff (0x100) MX[B]
	[7] -1	0	0xf9ef5000 - 0xf9ef5fff (0x1000) MX[B]
	[8] -1	0	0xf9efa400 - 0xf9efa40f (0x10) MX[B]
	[9] -1	0	0xf9efa800 - 0xf9efa8ff (0x100) MX[B]
	[10] -1	0	0xf9ef6000 - 0xf9ef6fff (0x1000) MX[B]
	[11] -1	0	0xf9ef0000 - 0xf9ef3fff (0x4000) MX[B]
	[12] -1	0	0xf9ef7000 - 0xf9ef7fff (0x1000) MX[B]
	[13] -1	0	0xf9ef8000 - 0xf9ef8fff (0x1000) MX[B]
	[14] -1	0	0xf9ef9000 - 0xf9ef9fff (0x1000) MX[B]
	[15] -1	0	0xf9efac00 - 0xf9efacff (0x100) MX[B]
	[16] -1	0	0xf9efb000 - 0xf9efbfff (0x1000) MX[B]
	[17] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[18] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[27] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[28] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[29] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[30] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[31] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[32] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[33] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[34] -1	0	0x0000b080 - 0x0000b08f (0x10) IX[B]
	[35] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[36] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[37] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[38] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[39] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[40] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[41] -1	0	0x0000c080 - 0x0000c087 (0x8) IX[B]
	[42] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[43] -1	0	0x0000c480 - 0x0000c487 (0x8) IX[B]
	[44] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[45] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[46] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[47] -1	0	0x00002900 - 0x0000293f (0x40) IX[B]
	[48] -1	0	0x00002f00 - 0x00002f7f (0x80) IX[B]
	[49] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
	[50] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[51] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 14336 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 96.128
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G80 Board - p355h00 
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(II) VESA(0): Splitting WC range: base: 0xfb000000, size: 0xe00000
(II) VESA(0): Splitting WC range: base: 0xfb800000, size: 0x600000
(==) VESA(0): Write-combining range (0xfbc00000,0x200000)
(==) VESA(0): Write-combining range (0xfb800000,0x600000)
(==) VESA(0): Write-combining range (0xfb000000,0xe00000)
(II) VESA(0): virtual address = 0x7fd8fddb1000,
	physical address = 0xfb000000, size = 14680064
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
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
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
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
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded


```

Xorg.0.log.old:

```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.1)
Current Operating System: Linux poni 2.6.24-17-server #1 SMP Thu May 1 14:28:06 UTC 2008 x86_64
Build Date: 21 May 2008  12:21:14PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 25 04:19:17 2008
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,0369 card 1462,7250 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0360 card 1462,7250 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0368 card 1462,7250 rev a3 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,036c card 1462,7250 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,036d card 1462,7250 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,036e card f462,7250 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:05:0: chip 10de,037f card 1462,7250 rev a3 class 01,01,85 hdr 80
(II) PCI: 00:05:1: chip 10de,037f card 1462,7250 rev a3 class 01,01,85 hdr 80
(II) PCI: 00:05:2: chip 10de,037f card 1462,7250 rev a3 class 01,01,85 hdr 80
(II) PCI: 00:06:0: chip 10de,0370 card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:06:1: chip 10de,0371 card 1462,7250 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:08:0: chip 10de,0373 card 1462,7250 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0373 card 1462,7250 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0376 card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0b:0: chip 10de,0374 card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,0374 card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,0378 card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,0375 card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0f:0: chip 10de,0377 card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:04:0: chip 1106,3044 card 1462,250d rev 80 class 0c,00,10 hdr 00
(II) PCI: 07:00:0: chip 10de,0191 card 1682,2250 rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:6:0), (0,1,1), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf9f00000 - 0xf9ffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:10:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:11:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:12:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:13:0), (0,5,5), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:14:0), (0,6,6), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:15:0), (0,7,7), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 7 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfebfffff (0x4c00000) MX[B]
(II) Bus 7 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(7:0:0) nVidia Corporation G80 [GeForce 8800 GTX] rev 162, Mem @ 0xfd000000/24, 0xc0000000/28, 0xfa000000/25, I/O @ 0xec00/7, BIOS @ 0xfebe0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xf9fff800 - 0xf9ffffff (0x800) MX[B]
	[1] -1	0	0xf9ef4c00 - 0xf9ef4c0f (0x10) MX[B]
	[2] -1	0	0xf9efa000 - 0xf9efa0ff (0x100) MX[B]
	[3] -1	0	0xf9ef5000 - 0xf9ef5fff (0x1000) MX[B]
	[4] -1	0	0xf9efa400 - 0xf9efa40f (0x10) MX[B]
	[5] -1	0	0xf9efa800 - 0xf9efa8ff (0x100) MX[B]
	[6] -1	0	0xf9ef6000 - 0xf9ef6fff (0x1000) MX[B]
	[7] -1	0	0xf9ef0000 - 0xf9ef3fff (0x4000) MX[B]
	[8] -1	0	0xf9ef7000 - 0xf9ef7fff (0x1000) MX[B]
	[9] -1	0	0xf9ef8000 - 0xf9ef8fff (0x1000) MX[B]
	[10] -1	0	0xf9ef9000 - 0xf9ef9fff (0x1000) MX[B]
	[11] -1	0	0xf9efac00 - 0xf9efacff (0x100) MX[B]
	[12] -1	0	0xf9efb000 - 0xf9efbfff (0x1000) MX[B]
	[13] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[14] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[18] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[20] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[21] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[22] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[23] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[25] -1	0	0x0000b080 - 0x0000b08f (0x10) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[27] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[29] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[30] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[32] -1	0	0x0000c080 - 0x0000c087 (0x8) IX[B]
	[33] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[34] -1	0	0x0000c480 - 0x0000c487 (0x8) IX[B]
	[35] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[36] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[37] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[38] -1	0	0x00002900 - 0x0000293f (0x40) IX[B]
	[39] -1	0	0x00002f00 - 0x00002f7f (0x80) IX[B]
	[40] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf9fff800 - 0xf9ffffff (0x800) MX[B]
	[1] -1	0	0xf9ef4c00 - 0xf9ef4c0f (0x10) MX[B]
	[2] -1	0	0xf9efa000 - 0xf9efa0ff (0x100) MX[B]
	[3] -1	0	0xf9ef5000 - 0xf9ef5fff (0x1000) MX[B]
	[4] -1	0	0xf9efa400 - 0xf9efa40f (0x10) MX[B]
	[5] -1	0	0xf9efa800 - 0xf9efa8ff (0x100) MX[B]
	[6] -1	0	0xf9ef6000 - 0xf9ef6fff (0x1000) MX[B]
	[7] -1	0	0xf9ef0000 - 0xf9ef3fff (0x4000) MX[B]
	[8] -1	0	0xf9ef7000 - 0xf9ef7fff (0x1000) MX[B]
	[9] -1	0	0xf9ef8000 - 0xf9ef8fff (0x1000) MX[B]
	[10] -1	0	0xf9ef9000 - 0xf9ef9fff (0x1000) MX[B]
	[11] -1	0	0xf9efac00 - 0xf9efacff (0x100) MX[B]
	[12] -1	0	0xf9efb000 - 0xf9efbfff (0x1000) MX[B]
	[13] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[14] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[18] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[20] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[21] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[22] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[23] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[25] -1	0	0x0000b080 - 0x0000b08f (0x10) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[27] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[29] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[30] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[32] -1	0	0x0000c080 - 0x0000c087 (0x8) IX[B]
	[33] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[34] -1	0	0x0000c480 - 0x0000c487 (0x8) IX[B]
	[35] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[36] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[37] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[38] -1	0	0x00002900 - 0x0000293f (0x40) IX[B]
	[39] -1	0	0x00002f00 - 0x00002f7f (0x80) IX[B]
	[40] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
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
	[4] -1	0	0xf9fff800 - 0xf9ffffff (0x800) MX[B]
	[5] -1	0	0xf9ef4c00 - 0xf9ef4c0f (0x10) MX[B]
	[6] -1	0	0xf9efa000 - 0xf9efa0ff (0x100) MX[B]
	[7] -1	0	0xf9ef5000 - 0xf9ef5fff (0x1000) MX[B]
	[8] -1	0	0xf9efa400 - 0xf9efa40f (0x10) MX[B]
	[9] -1	0	0xf9efa800 - 0xf9efa8ff (0x100) MX[B]
	[10] -1	0	0xf9ef6000 - 0xf9ef6fff (0x1000) MX[B]
	[11] -1	0	0xf9ef0000 - 0xf9ef3fff (0x4000) MX[B]
	[12] -1	0	0xf9ef7000 - 0xf9ef7fff (0x1000) MX[B]
	[13] -1	0	0xf9ef8000 - 0xf9ef8fff (0x1000) MX[B]
	[14] -1	0	0xf9ef9000 - 0xf9ef9fff (0x1000) MX[B]
	[15] -1	0	0xf9efac00 - 0xf9efacff (0x100) MX[B]
	[16] -1	0	0xf9efb000 - 0xf9efbfff (0x1000) MX[B]
	[17] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[18] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[24] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[25] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[26] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[27] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[28] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[29] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[31] -1	0	0x0000b080 - 0x0000b08f (0x10) IX[B]
	[32] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[33] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[34] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[35] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[36] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[37] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[38] -1	0	0x0000c080 - 0x0000c087 (0x8) IX[B]
	[39] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[40] -1	0	0x0000c480 - 0x0000c487 (0x8) IX[B]
	[41] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[42] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[43] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[44] -1	0	0x00002900 - 0x0000293f (0x40) IX[B]
	[45] -1	0	0x00002f00 - 0x00002f7f (0x80) IX[B]
	[46] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:34:02 PST 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 07:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf9fff800 - 0xf9ffffff (0x800) MX[B]
	[5] -1	0	0xf9ef4c00 - 0xf9ef4c0f (0x10) MX[B]
	[6] -1	0	0xf9efa000 - 0xf9efa0ff (0x100) MX[B]
	[7] -1	0	0xf9ef5000 - 0xf9ef5fff (0x1000) MX[B]
	[8] -1	0	0xf9efa400 - 0xf9efa40f (0x10) MX[B]
	[9] -1	0	0xf9efa800 - 0xf9efa8ff (0x100) MX[B]
	[10] -1	0	0xf9ef6000 - 0xf9ef6fff (0x1000) MX[B]
	[11] -1	0	0xf9ef0000 - 0xf9ef3fff (0x4000) MX[B]
	[12] -1	0	0xf9ef7000 - 0xf9ef7fff (0x1000) MX[B]
	[13] -1	0	0xf9ef8000 - 0xf9ef8fff (0x1000) MX[B]
	[14] -1	0	0xf9ef9000 - 0xf9ef9fff (0x1000) MX[B]
	[15] -1	0	0xf9efac00 - 0xf9efacff (0x100) MX[B]
	[16] -1	0	0xf9efb000 - 0xf9efbfff (0x1000) MX[B]
	[17] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[18] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[24] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[25] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[26] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[27] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[28] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[29] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[31] -1	0	0x0000b080 - 0x0000b08f (0x10) IX[B]
	[32] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[33] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[34] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[35] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[36] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[37] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[38] -1	0	0x0000c080 - 0x0000c087 (0x8) IX[B]
	[39] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[40] -1	0	0x0000c480 - 0x0000c487 (0x8) IX[B]
	[41] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[42] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[43] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[44] -1	0	0x00002900 - 0x0000293f (0x40) IX[B]
	[45] -1	0	0x00002f00 - 0x00002f7f (0x80) IX[B]
	[46] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf9fff800 - 0xf9ffffff (0x800) MX[B]
	[5] -1	0	0xf9ef4c00 - 0xf9ef4c0f (0x10) MX[B]
	[6] -1	0	0xf9efa000 - 0xf9efa0ff (0x100) MX[B]
	[7] -1	0	0xf9ef5000 - 0xf9ef5fff (0x1000) MX[B]
	[8] -1	0	0xf9efa400 - 0xf9efa40f (0x10) MX[B]
	[9] -1	0	0xf9efa800 - 0xf9efa8ff (0x100) MX[B]
	[10] -1	0	0xf9ef6000 - 0xf9ef6fff (0x1000) MX[B]
	[11] -1	0	0xf9ef0000 - 0xf9ef3fff (0x4000) MX[B]
	[12] -1	0	0xf9ef7000 - 0xf9ef7fff (0x1000) MX[B]
	[13] -1	0	0xf9ef8000 - 0xf9ef8fff (0x1000) MX[B]
	[14] -1	0	0xf9ef9000 - 0xf9ef9fff (0x1000) MX[B]
	[15] -1	0	0xf9efac00 - 0xf9efacff (0x100) MX[B]
	[16] -1	0	0xf9efb000 - 0xf9efbfff (0x1000) MX[B]
	[17] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[18] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[27] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[28] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[29] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[30] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[31] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[32] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[33] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[34] -1	0	0x0000b080 - 0x0000b08f (0x10) IX[B]
	[35] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[36] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[37] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[38] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[39] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[40] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[41] -1	0	0x0000c080 - 0x0000c087 (0x8) IX[B]
	[42] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[43] -1	0	0x0000c480 - 0x0000c487 (0x8) IX[B]
	[44] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[45] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[46] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[47] -1	0	0x00002900 - 0x0000293f (0x40) IX[B]
	[48] -1	0	0x00002f00 - 0x00002f7f (0x80) IX[B]
	[49] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
	[50] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[51] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 14336 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 96.128
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G80 Board - p355h00 
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(==) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 10
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x33f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 2
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
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x33f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 1
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
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 106 (1280x1024)
	ModeAttributes: 0x33f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 160
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 1
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
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 107 (1280x1024)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10e (320x200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 10f (320x200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 111 (640x480)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 112 (640x480)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 114 (800x600)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 115 (800x600)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 117 (1024x768)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 118 (1024x768)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 11a (1280x1024)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 11b (1280x1024)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
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
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 320
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
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 132 (320x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 133 (320x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 135 (320x240)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 19
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 19
	LinNumberOfImagePages: 19
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 136 (320x240)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 13d (640x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 13e (640x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
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
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 2560
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
	MaxPixelClock: 229500000
Mode: 145 (1600x1200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 146 (1600x1200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000838a
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
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xfb000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 224 64KB banks (14336kB)
(II) VESA(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(II) VESA(0): Not using built-in mode "1600x1200" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1024x768" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x200" (hsync out of range)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (114)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (111)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf9fff800 - 0xf9ffffff (0x800) MX[B]
	[5] -1	0	0xf9ef4c00 - 0xf9ef4c0f (0x10) MX[B]
	[6] -1	0	0xf9efa000 - 0xf9efa0ff (0x100) MX[B]
	[7] -1	0	0xf9ef5000 - 0xf9ef5fff (0x1000) MX[B]
	[8] -1	0	0xf9efa400 - 0xf9efa40f (0x10) MX[B]
	[9] -1	0	0xf9efa800 - 0xf9efa8ff (0x100) MX[B]
	[10] -1	0	0xf9ef6000 - 0xf9ef6fff (0x1000) MX[B]
	[11] -1	0	0xf9ef0000 - 0xf9ef3fff (0x4000) MX[B]
	[12] -1	0	0xf9ef7000 - 0xf9ef7fff (0x1000) MX[B]
	[13] -1	0	0xf9ef8000 - 0xf9ef8fff (0x1000) MX[B]
	[14] -1	0	0xf9ef9000 - 0xf9ef9fff (0x1000) MX[B]
	[15] -1	0	0xf9efac00 - 0xf9efacff (0x100) MX[B]
	[16] -1	0	0xf9efb000 - 0xf9efbfff (0x1000) MX[B]
	[17] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[18] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[27] -1	0	0x0000a080 - 0x0000a087 (0x8) IX[B]
	[28] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[29] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[30] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[31] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[32] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[33] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[34] -1	0	0x0000b080 - 0x0000b08f (0x10) IX[B]
	[35] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[36] -1	0	0x0000b480 - 0x0000b487 (0x8) IX[B]
	[37] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[38] -1	0	0x0000b880 - 0x0000b887 (0x8) IX[B]
	[39] -1	0	0x0000bc00 - 0x0000bc0f (0x10) IX[B]
	[40] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[41] -1	0	0x0000c080 - 0x0000c087 (0x8) IX[B]
	[42] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[43] -1	0	0x0000c480 - 0x0000c487 (0x8) IX[B]
	[44] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[45] -1	0	0x00002e00 - 0x00002e3f (0x40) IX[B]
	[46] -1	0	0x00002d00 - 0x00002d3f (0x40) IX[B]
	[47] -1	0	0x00002900 - 0x0000293f (0x40) IX[B]
	[48] -1	0	0x00002f00 - 0x00002f7f (0x80) IX[B]
	[49] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
	[50] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[51] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 14336 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 96.128
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G80 Board - p355h00 
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(II) VESA(0): Splitting WC range: base: 0xfb000000, size: 0xe00000
(II) VESA(0): Splitting WC range: base: 0xfb800000, size: 0x600000
(==) VESA(0): Write-combining range (0xfbc00000,0x200000)
(==) VESA(0): Write-combining range (0xfb800000,0x600000)
(==) VESA(0): Write-combining range (0xfb000000,0xe00000)
(II) VESA(0): virtual address = 0x7f4576bfd000,
	physical address = 0xfb000000, size = 14680064
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
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
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
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
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9


```

---

