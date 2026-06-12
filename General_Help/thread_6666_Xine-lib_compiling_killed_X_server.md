---
title: "Xine-lib compiling killed X server"
date: 2004-11-30
forum: General Help
---

### Post by cws on 2004-11-30
I compiled xine-libs and the system got stucked. I rebooted, but Gnome wouldn't start. I tried startx and the output was:

[SIZE=1]Skipping "usr/X11R6/lib/modules/extensions/libGLcore.a:m:debug_norm.o": No symbols found
Skipping "usr/X11R6/lib/modules/extensions/libGLcore.a:m:debug_xform.o": No symbols found
Skipping "usr/X11R6/lib/modules/extensions/libGLcore.a:m:debug_vertex.o": No symbols found
Skipping "usr/X11R6/lib/modules/fonts/libspeedo.a:spencode.o" No symbols found

(EE) R128(0): No DFP detected 1

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

Could not init font path element unix/:7100, removing from list![/SIZE]

waiting for X server to shut down

I tried to reinstall fontconfig etc, but there was no effect. I believe my XF86Config-4 should be in order? [http://rmk.hamk.fi/~rikoivusa1/XF86Config-4](http://rmk.hamk.fi/~rikoivusa1/XF86Config-4)

Any ideas? I ran all out...  ](*,)

---

### Post by wallijonn on 2004-12-01
Are you saying that you installed[COLOR=DarkGreen] libxine1[/COLOR] through SPM and then there was a problem? You may have to re-install[COLOR=DarkGreen] x-window-system-core[/COLOR].

---

### Post by cws on 2004-12-01
Nope. I compiled xine-libs: 

xine-lib-1-rc7
xine-lib-1-rc6a
xine-lib-1-rc5
xine-lib-1-rc4a
xine-lib-0.9.13

After that the system got really stuck and I tried to reboot , but the x server wouldn't start.

---

### Post by cws on 2004-12-02
I reinstalled x-window-system-core, xfree86-common, xbase-clients, xserver-xfree86 etc, but when running startx the output is still the same...  :???:

---

### Post by daniels on 2004-12-02
Oooo, impressive.  Could you please paste your /var/log/XFree86.0.log also?  Try deleting the HorizSync and VertRefresh lines from /etc/X11/XF86Config-4 as a start.

---

### Post by cws on 2004-12-02
I deleted the HorizSync and VertRefresh lines in /etc/X11/XF86Config-4, no effect. Here is my /var/log/XFree86.0.log (I deleted some unnecessary lines from the beginning cos it is a bit too long to paste here) :
[SIZE=1]


XFree86 Version 4.3.0.1 (Ubuntu 4.3.0.dfsg.1-6ubuntu25.1 20041117134039 root@)
Release Date: 15 August 2003
X Protocol Version 11, Revision 0, Release 6.6
Build Operating System: Linux 2.6.8.1 i686 [ELF] 
Build Date: 17 November 2004
	Before reporting problems, check [http://www.XFree86.Org/](http://www.XFree86.Org/)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.8.1-3-386 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Thu Nov 18 11:47:33 UTC 2004 
Markers: (--) probed, (**) from config file, (==) default setting,
         (++) from command line, (!!) notice, (II) informational,
         (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/XFree86.0.log", Time: Thu Dec  2 09:22:39 2004
(--) using VT number 7

(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	XFree86 ANSI C Emulation: 0.2
	XFree86 Video Driver: 0.6
	XFree86 XInput driver : 0.4
	XFree86 Server Extension : 0.2
	XFree86 Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Font Renderer
	ABI class: XFree86 Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Video Driver, version 0.6
(II) PCI: Probing config type using method 1
(II) PCI: Config type is 1
(II) PCI: stages = 0x03, oldVal1 = 0x00000000, mode1Res1 = 0x80000000
(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1043,80f2 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1043,80a6 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1043,80a6 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1043,80a6 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1043,80a6 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1043,812a rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,5446 card 1002,5446 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:05:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: 02:0b:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
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
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf3f00000 - 0xfbefffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Rage 128 Pro Ultra TF rev 0, Mem @ 0xf4000000/26, 0xfe9fc000/14, I/O @ 0xc000/8, BIOS @ 0xfe9c0000/17
List of video drivers:
	atimisc
	r128
	radeon
	mga
	glint
	nv
	tga
	s3
	s3virge
	sis
	rendition
	neomagic
	i740
	tdfx
	savage
	via
	cirrus
	vmware
	tseng
	trident
	chips
	apm
	glide
	fbdev
	i128
	nsc
	ati
	i810
	imstt
	newport
	ark
	cyrix
	siliconmotion
	vesa
	vga
	dummy
	v4l
(II) LoadModule: "atimisc"
(II) Loading /usr/X11R6/lib/modules/drivers/atimisc_drv.o
(II) Module atimisc: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 6.5.5
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "r128"
(II) Loading /usr/X11R6/lib/modules/drivers/r128_drv.o
(II) Module r128: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 4.0.1
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "radeon"
(II) Loading /usr/X11R6/lib/modules/drivers/radeon_drv.o
(II) Module radeon: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 4.0.1
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "mga"
(II) Loading /usr/X11R6/lib/modules/drivers/mga_drv.o
(II) Module mga: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.1.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "glint"
(II) Loading /usr/X11R6/lib/modules/drivers/glint_drv.o
(II) Module glint: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "nv"
(II) Loading /usr/X11R6/lib/modules/drivers/nv_drv.o
(II) Module nv: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.1
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "tga"
(II) Loading /usr/X11R6/lib/modules/drivers/tga_drv.o
(II) Module tga: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "s3"
(II) Loading /usr/X11R6/lib/modules/drivers/s3_drv.o
(II) Module s3: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 0.3.5
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "s3virge"
(II) Loading /usr/X11R6/lib/modules/drivers/s3virge_drv.o
(II) Module s3virge: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.8.6
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "sis"
(II) Loading /usr/X11R6/lib/modules/drivers/sis_drv.o
(II) Module sis: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 0.7.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "rendition"
(II) Loading /usr/X11R6/lib/modules/drivers/rendition_drv.o
(II) Module rendition: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 4.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "neomagic"
(II) Loading /usr/X11R6/lib/modules/drivers/neomagic_drv.o
(II) Module neomagic: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "i740"
(II) Loading /usr/X11R6/lib/modules/drivers/i740_drv.o
(II) Module i740: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "tdfx"
(II) Loading /usr/X11R6/lib/modules/drivers/tdfx_drv.o
(II) Module tdfx: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "savage"
(II) Loading /usr/X11R6/lib/modules/drivers/savage_drv.o
(II) Module savage: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.1.27
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "via"
(II) Loading /usr/X11R6/lib/modules/drivers/via_drv.o
(II) Module via: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 4.1.30
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "cirrus"
(II) Loading /usr/X11R6/lib/modules/drivers/cirrus_drv.o
(II) Module cirrus: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "vmware"
(II) Loading /usr/X11R6/lib/modules/drivers/vmware_drv.o
(II) Module vmware: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 10.10.2
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "tseng"
(II) Loading /usr/X11R6/lib/modules/drivers/tseng_drv.o
(II) Module tseng: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "trident"
(II) Loading /usr/X11R6/lib/modules/drivers/trident_drv.o
(II) Module trident: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "chips"
(II) Loading /usr/X11R6/lib/modules/drivers/chips_drv.o
(II) Module chips: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "apm"
(II) Loading /usr/X11R6/lib/modules/drivers/apm_drv.o
(II) Module apm: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "glide"
(II) Loading /usr/X11R6/lib/modules/drivers/glide_drv.o
(II) Module glide: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) Loading sub module "glide2x"
(II) LoadModule: "glide2x"
(WW) Warning, couldn't open module glide2x
(II) UnloadModule: "glide2x"
(EE) Glide driver:

Could not load the shared library file for Glide: "libglide2x.so"! 

You need to have Glide installed to run the glide driver for XFree86.
Also, you need to tell XFree86 where the libglide2x.so file is placed
by making a soft link in the /usr/X11R6/lib/modules directory that points
to the libglide2x.so file. For example (if your libglide2x.so file is in
/usr/lib):

  # ln -s /usr/lib/libglide2x.so /usr/X11R6/lib/modules


(II) UnloadModule: "glide"
(II) Unloading /usr/X11R6/lib/modules/drivers/glide_drv.o
(EE) Failed to load module "glide" (a required submodule could not be loaded, 2)
(II) LoadModule: "fbdev"
(II) Loading /usr/X11R6/lib/modules/drivers/fbdev_drv.o
(II) Module fbdev: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 0.1.0
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "i128"
(II) Loading /usr/X11R6/lib/modules/drivers/i128_drv.o
(II) Module i128: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "nsc"
(II) Loading /usr/X11R6/lib/modules/drivers/nsc_drv.o
(II) Module nsc: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 2.7.6
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "ati"
(II) Loading /usr/X11R6/lib/modules/drivers/ati_drv.o
(II) Module ati: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 6.5.5
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "i810"
(II) Loading /usr/X11R6/lib/modules/drivers/i810_drv.o
(II) Module i810: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.3.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "imstt"
(II) Loading /usr/X11R6/lib/modules/drivers/imstt_drv.o
(II) Module imstt: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "newport"
(II) Loading /usr/X11R6/lib/modules/drivers/newport_drv.o
(II) Module newport: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 0.1.3
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "ark"
(II) Loading /usr/X11R6/lib/modules/drivers/ark_drv.o
(II) Module ark: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 0.5.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "cyrix"
(II) Loading /usr/X11R6/lib/modules/drivers/cyrix_drv.o
(II) Module cyrix: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "siliconmotion"
(II) Loading /usr/X11R6/lib/modules/drivers/siliconmotion_drv.o
(II) Module siliconmotion: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.3.1
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "vesa"
(II) Loading /usr/X11R6/lib/modules/drivers/vesa_drv.o
(II) Module vesa: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "vga"
(II) Loading /usr/X11R6/lib/modules/drivers/vga_drv.o
(II) Module vga: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 4.0.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "dummy"
(II) Loading /usr/X11R6/lib/modules/drivers/dummy_drv.o
(II) Module dummy: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 0.1.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "v4l"
(II) Loading /usr/X11R6/lib/modules/drivers/linux/v4l_drv.o
(II) Module v4l: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 0.0.1
	ABI class: XFree86 Video Driver, version 0.6
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
(II) PCI Memory resource overlap reduced 0xfc000000 from 0xfdffffff to 0xfbffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[1] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[2] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[3] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[4] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[6] -1	0	0xfc000000 - 0xfbffffff (0x0) MX[B]O
	[7] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[8] -1	0	0xfe9fc000 - 0xfe9fffff (0x4000) MX[B](B)
	[9] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[12] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[16] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[17] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[18] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[19] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[1] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[2] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[3] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[4] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[6] -1	0	0xfc000000 - 0xfbffffff (0x0) MX[B]O
	[7] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[8] -1	0	0xfe9fc000 - 0xfe9fffff (0x4000) MX[B](B)
	[9] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[12] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[16] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[17] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[18] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[19] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[6] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[7] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[8] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[9] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[10] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[11] -1	0	0xfc000000 - 0xfbffffff (0x0) MX[B]O
	[12] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[13] -1	0	0xfe9fc000 - 0xfe9fffff (0x4000) MX[B](B)
	[14] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[21] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[24] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[25] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[26] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Primary Device is: PCI 01:00:0
(II) Loading sub module "cirrus_laguna"
(II) LoadModule: "cirrus_laguna"
(II) Loading /usr/X11R6/lib/modules/drivers/cirrus_laguna.o
(II) Module cirrus_laguna: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Video Driver, version 0.6
(II) Loading sub module "cirrus_alpine"
(II) LoadModule: "cirrus_alpine"
(II) Loading /usr/X11R6/lib/modules/drivers/cirrus_alpine.o
(II) Module cirrus_alpine: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Video Driver, version 0.6
(II) ATI: ATI driver (version 6.5.5) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (AGP?), ATI Rage 128 Pro GL PB (AGP?),
	ATI Rage 128 Pro GL PC (AGP?), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (AGP?), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (AGP?), ATI Rage 128 Pro VR PH (AGP?),
	ATI Rage 128 Pro VR PI (AGP?), ATI Rage 128 Pro VR PJ (AGP?),
	ATI Rage 128 Pro VR PK (AGP?), ATI Rage 128 Pro VR PL (AGP?),
	ATI Rage 128 Pro VR PM (AGP?), ATI Rage 128 Pro VR PN (AGP?),
	ATI Rage 128 Pro VR PO (AGP?), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (AGP?), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (AGP?), ATI Rage 128 Pro VR PT (AGP?),
	ATI Rage 128 Pro VR PU (AGP?), ATI Rage 128 Pro VR PV (AGP?),
	ATI Rage 128 Pro VR PW (AGP?), ATI Rage 128 Pro VR PX (AGP?),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (AGP?),
	ATI Rage 128 4X SF (AGP?), ATI Rage 128 4X SG (AGP?),
	ATI Rage 128 4X SH (AGP?), ATI Rage 128 4X SK (AGP?),
	ATI Rage 128 4X SL (AGP?), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (AGP?), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon 9200PRO 5960 (AGP), ATI Radeon 9200 5961 (AGP),
	ATI Radeon 9200 5962 (AGP), ATI Radeon 9200SE 5964 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9700 NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP), ATI Radeon Mobility 9600 (M10) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2 (M11) NV (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP)
(II) VESA: driver for VESA chipsets: vesa
(II) VGA: Generic VGA driver (version 4.0) for chipsets: generic
(II) v4l driver for Video4Linux
(++) Using config file: "/root/XF86Config.new"
(==) ServerLayout "XFree86 Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Keyboard: CustomKeycode disabled
(WW) The directory "/usr/X11R6/lib/X11/fonts/CID/" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/Speedo/,/usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/"
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(**) ModulePath set to "/usr/X11R6/lib/modules"
(II) ATI:  Candidate "Device" section "Card0".
(--) Chipset ATI Rage 128 Pro ULTRA TF (AGP) found
(II) Loading sub module "r128"
(II) LoadModule: "r128"
(II) Reloading /usr/X11R6/lib/modules/drivers/r128_drv.o
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[6] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[7] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[8] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[9] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[10] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[11] -1	0	0xfc000000 - 0xfbffffff (0x0) MX[B]O
	[12] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[13] -1	0	0xfe9fc000 - 0xfe9fffff (0x4000) MX[B](B)
	[14] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[21] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[24] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[25] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[26] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[6] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[7] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[8] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[9] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[10] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[11] -1	0	0xfc000000 - 0xfbffffff (0x0) MX[B]O
	[12] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[13] -1	0	0xfe9fc000 - 0xfe9fffff (0x4000) MX[B](B)
	[14] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[24] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[25] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[26] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[27] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[28] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[29] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
	[30] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.1.0
	ABI class: XFree86 Video Driver, version 0.6
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Video Driver, version 0.6
(II) R128(0): initializing int10
(II) R128(0): Primary V_BIOS segment is: 0xc000
(II) R128(0): VESA BIOS detected
(II) R128(0): VESA VBE Version 2.0
(II) R128(0): VESA VBE Total Mem: 32768 kB
(II) R128(0): VESA VBE OEM: ATI RAGE128
(II) R128(0): VESA VBE OEM Software Rev: 1.0
(II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) R128(0): VESA VBE OEM Product: R128
(II) R128(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Video Driver, version 0.6
(II) R128(0): VESA VBE DDC supported
(II) R128(0): VESA VBE DDC Level 2
(II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
(II) R128(0): VESA VBE DDC read successfully


XFree86 is not able to detect your mouse.
Edit the file and correct the Device.

Your XF86Config file is /root/XF86Config.new

To test the server, run 'XFree86 -xf86config /root/XF86Config.new'

[/SIZE]

---

### Post by daniels on 2004-12-02
Why are you running X -configure?

If you accidentally deleted your configuration file and want to start again, run 'dpkg-reconfigure xserver-xfree86'.

---

### Post by cws on 2004-12-02
> Why are you running X -configure? 

I don't know :)

I've ran 'dpkg-reconfigure xserver-xfree86' couple of times, but the same problems remain. I would rather not reinstall the whole system again, but I guess it would be the easiest way in this case..?

---

