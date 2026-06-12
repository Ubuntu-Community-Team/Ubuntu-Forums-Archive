---
title: "Xorg stopped working after yesterdays update"
date: 2014-01-04
forum: General Help
---

### Post by RaZoR1394 on 2014-01-04
Hi.

The Xorg server on my 13.10 i386 computer is not working properly. Yesterday I updated the system and there were nvidia updates and what I believe was kernel updates. When I boot up the nvidia driver fails and I end up at low resolution dialogue. I tried fixing the xserver from the menu, the rescue mode and also from the terminal by issuing

sudo dpkg-reconfigure xserver-xorg .

I've also purged the nvidia driver and xorg and reinstalled them.

I've tried booting an older kernel from the grub menu without any luck.

It's the same problem both with the nvidia driver and without.

My graphics card is a Nvidia 560.

I don't feel like reinstalling.

---

### Post by claracc on 2014-01-04
I think, this thread [http://ubuntuforums.org/showthread.php?t=1678203](http://ubuntuforums.org/showthread.php?t=1678203) can help you to solve your problem with new kernel and nvidia drivers.

See particularly, post number 7 where is addressed a possible solution.

---

### Post by RaZoR1394 on 2014-01-04
Hi.

I have no old stuff in the dkms directory.

Here is the latest Xorg log from my system.

```
[    20.135] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[    20.135] X Protocol Version 11, Revision 0
[    20.135] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    20.135] Current Operating System: Linux zeus 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 17:26:33 UTC 2013 i686
[    20.135] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-13-generic root=UUID=9600889d-aa95-464d-b696-6f04576f7098 ro quiet splash
[    20.135] Build Date: 15 October 2013  09:23:29AM
[    20.135] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    20.135] Current version of pixman: 0.30.2
[    20.135] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    20.135] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.135] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  4 10:36:25 2014
[    20.152] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.184] (==) No Layout section.  Using the first Screen section.
[    20.184] (==) No screen section available. Using defaults.
[    20.184] (**) |-->Screen "Default Screen Section" (0)
[    20.184] (**) |   |-->Monitor "<default monitor>"
[    20.205] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    20.205] (==) Automatically adding devices
[    20.205] (==) Automatically enabling devices
[    20.205] (==) Automatically adding GPU devices
[    20.233] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.233] 	Entry deleted from font path.
[    20.233] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.233] 	Entry deleted from font path.
[    20.233] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.233] 	Entry deleted from font path.
[    20.234] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.234] 	Entry deleted from font path.
[    20.234] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.234] 	Entry deleted from font path.
[    20.234] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    20.234] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.234] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.234] (II) Loader magic: 0xb77a86a0
[    20.234] (II) Module ABI versions:
[    20.234] 	X.Org ANSI C Emulation: 0.4
[    20.234] 	X.Org Video Driver: 14.1
[    20.234] 	X.Org XInput driver : 19.1
[    20.234] 	X.Org Server Extension : 7.0
[    20.234] (II) xfree86: Adding drm device (/dev/dri/card0)
[    20.235] (--) PCI:*(0:1:0:0) 10de:1087:19da:2207 rev 161, Mem @ 0xf6000000/16777216, 0xe8000000/134217728, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    20.235] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.236] Initializing built-in extension Generic Event Extension
[    20.236] Initializing built-in extension SHAPE
[    20.236] Initializing built-in extension MIT-SHM
[    20.236] Initializing built-in extension XInputExtension
[    20.236] Initializing built-in extension XTEST
[    20.236] Initializing built-in extension BIG-REQUESTS
[    20.236] Initializing built-in extension SYNC
[    20.236] Initializing built-in extension XKEYBOARD
[    20.236] Initializing built-in extension XC-MISC
[    20.236] Initializing built-in extension SECURITY
[    20.236] Initializing built-in extension XINERAMA
[    20.236] Initializing built-in extension XFIXES
[    20.236] Initializing built-in extension RENDER
[    20.236] Initializing built-in extension RANDR
[    20.236] Initializing built-in extension COMPOSITE
[    20.236] Initializing built-in extension DAMAGE
[    20.236] Initializing built-in extension MIT-SCREEN-SAVER
[    20.236] Initializing built-in extension DOUBLE-BUFFER
[    20.236] Initializing built-in extension RECORD
[    20.236] Initializing built-in extension DPMS
[    20.236] Initializing built-in extension X-Resource
[    20.236] Initializing built-in extension XVideo
[    20.236] Initializing built-in extension XVideo-MotionCompensation
[    20.236] Initializing built-in extension SELinux
[    20.236] Initializing built-in extension XFree86-VidModeExtension
[    20.236] Initializing built-in extension XFree86-DGA
[    20.236] Initializing built-in extension XFree86-DRI
[    20.236] Initializing built-in extension DRI2
[    20.236] (II) "glx" will be loaded by default.
[    20.236] (WW) "xmir" is not to be loaded by default. Skipping.
[    20.236] (II) LoadModule: "dri2"
[    20.236] (II) Module "dri2" already built-in
[    20.236] (II) LoadModule: "glamoregl"
[    20.266] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    20.453] (II) Module glamoregl: vendor="X.Org Foundation"
[    20.453] 	compiled for 1.14.3, module version = 0.5.1
[    20.453] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    20.453] (II) LoadModule: "glx"
[    20.453] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.523] (II) Module glx: vendor="X.Org Foundation"
[    20.523] 	compiled for 1.14.3, module version = 1.0.0
[    20.523] 	ABI class: X.Org Server Extension, version 7.0
[    20.523] (==) AIGLX enabled
[    20.523] Loading extension GLX
[    20.523] (==) Matched nvidia as autoconfigured driver 0
[    20.523] (==) Matched nouveau as autoconfigured driver 1
[    20.523] (==) Matched nvidia as autoconfigured driver 2
[    20.523] (==) Matched nouveau as autoconfigured driver 3
[    20.523] (==) Matched vesa as autoconfigured driver 4
[    20.523] (==) Matched modesetting as autoconfigured driver 5
[    20.523] (==) Matched fbdev as autoconfigured driver 6
[    20.523] (==) Assigned the driver to the xf86ConfigLayout
[    20.523] (II) LoadModule: "nvidia"
[    20.523] (WW) Warning, couldn't open module nvidia
[    20.523] (II) UnloadModule: "nvidia"
[    20.523] (II) Unloading nvidia
[    20.523] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    20.523] (II) LoadModule: "nouveau"
[    20.524] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    20.543] (II) Module nouveau: vendor="X.Org Foundation"
[    20.543] 	compiled for 1.14.2.901, module version = 1.0.9
[    20.543] 	Module class: X.Org Video Driver
[    20.543] 	ABI class: X.Org Video Driver, version 14.1
[    20.543] (II) LoadModule: "vesa"
[    20.543] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.549] (II) Module vesa: vendor="X.Org Foundation"
[    20.549] 	compiled for 1.14.1, module version = 2.3.2
[    20.549] 	Module class: X.Org Video Driver
[    20.549] 	ABI class: X.Org Video Driver, version 14.1
[    20.549] (II) LoadModule: "modesetting"
[    20.549] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    20.559] (II) Module modesetting: vendor="X.Org Foundation"
[    20.559] 	compiled for 1.14.1, module version = 0.8.0
[    20.559] 	Module class: X.Org Video Driver
[    20.559] 	ABI class: X.Org Video Driver, version 14.1
[    20.559] (II) LoadModule: "fbdev"
[    20.559] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.566] (II) Module fbdev: vendor="X.Org Foundation"
[    20.566] 	compiled for 1.14.1, module version = 0.4.3
[    20.566] 	Module class: X.Org Video Driver
[    20.566] 	ABI class: X.Org Video Driver, version 14.1
[    20.566] (==) Matched nvidia as autoconfigured driver 0
[    20.566] (==) Matched nouveau as autoconfigured driver 1
[    20.566] (==) Matched nvidia as autoconfigured driver 2
[    20.566] (==) Matched nouveau as autoconfigured driver 3
[    20.566] (==) Matched vesa as autoconfigured driver 4
[    20.566] (==) Matched modesetting as autoconfigured driver 5
[    20.566] (==) Matched fbdev as autoconfigured driver 6
[    20.566] (==) Assigned the driver to the xf86ConfigLayout
[    20.566] (II) LoadModule: "nvidia"
[    20.566] (WW) Warning, couldn't open module nvidia
[    20.566] (II) UnloadModule: "nvidia"
[    20.566] (II) Unloading nvidia
[    20.566] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    20.566] (II) LoadModule: "nouveau"
[    20.566] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    20.567] (II) Module nouveau: vendor="X.Org Foundation"
[    20.567] 	compiled for 1.14.2.901, module version = 1.0.9
[    20.567] 	Module class: X.Org Video Driver
[    20.567] 	ABI class: X.Org Video Driver, version 14.1
[    20.567] (II) UnloadModule: "nouveau"
[    20.567] (II) Unloading nouveau
[    20.567] (II) Failed to load module "nouveau" (already loaded, 0)
[    20.567] (II) LoadModule: "vesa"
[    20.567] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.567] (II) Module vesa: vendor="X.Org Foundation"
[    20.567] 	compiled for 1.14.1, module version = 2.3.2
[    20.567] 	Module class: X.Org Video Driver
[    20.567] 	ABI class: X.Org Video Driver, version 14.1
[    20.567] (II) UnloadModule: "vesa"
[    20.567] (II) Unloading vesa
[    20.567] (II) Failed to load module "vesa" (already loaded, 0)
[    20.567] (II) LoadModule: "modesetting"
[    20.567] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    20.567] (II) Module modesetting: vendor="X.Org Foundation"
[    20.567] 	compiled for 1.14.1, module version = 0.8.0
[    20.567] 	Module class: X.Org Video Driver
[    20.567] 	ABI class: X.Org Video Driver, version 14.1
[    20.567] (II) UnloadModule: "modesetting"
[    20.567] (II) Unloading modesetting
[    20.567] (II) Failed to load module "modesetting" (already loaded, 0)
[    20.567] (II) LoadModule: "fbdev"
[    20.567] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.567] (II) Module fbdev: vendor="X.Org Foundation"
[    20.567] 	compiled for 1.14.1, module version = 0.4.3
[    20.567] 	Module class: X.Org Video Driver
[    20.567] 	ABI class: X.Org Video Driver, version 14.1
[    20.567] (II) UnloadModule: "fbdev"
[    20.567] (II) Unloading fbdev
[    20.567] (II) Failed to load module "fbdev" (already loaded, 0)
[    20.567] (II) NOUVEAU driver Date:   Wed Jul 31 10:51:03 2013 +1000
[    20.567] (II) NOUVEAU driver for NVIDIA chipset families :
[    20.567] 	RIVA TNT        (NV04)
[    20.567] 	RIVA TNT2       (NV05)
[    20.567] 	GeForce 256     (NV10)
[    20.567] 	GeForce 2       (NV11, NV15)
[    20.567] 	GeForce 4MX     (NV17, NV18)
[    20.567] 	GeForce 3       (NV20)
[    20.567] 	GeForce 4Ti     (NV25, NV28)
[    20.567] 	GeForce FX      (NV3x)
[    20.567] 	GeForce 6       (NV4x)
[    20.567] 	GeForce 7       (G7x)
[    20.567] 	GeForce 8       (G8x)
[    20.567] 	GeForce GTX 200 (NVA0)
[    20.567] 	GeForce GTX 400 (NVC0)
[    20.567] (II) VESA: driver for VESA chipsets: vesa
[    20.567] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    20.567] (II) FBDEV: driver for framebuffer: fbdev
[    20.567] (++) using VT number 7

[    20.567] (II) [drm] nouveau interface version: 1.1.1
[    20.567] (WW) Falling back to old probe method for vesa
[    20.567] (WW) Falling back to old probe method for modesetting
[    20.567] (WW) Falling back to old probe method for fbdev
[    20.567] (II) Loading sub module "fbdevhw"
[    20.567] (II) LoadModule: "fbdevhw"
[    20.568] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.572] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.572] 	compiled for 1.14.3, module version = 0.0.2
[    20.572] 	ABI class: X.Org Video Driver, version 14.1
[    20.572] (II) Loading sub module "dri2"
[    20.572] (II) LoadModule: "dri2"
[    20.572] (II) Module "dri2" already built-in
[    20.573] (--) NOUVEAU(0): Chipset: "NVIDIA NVC8"
[    20.573] (II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    20.573] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    20.573] (==) NOUVEAU(0): RGB weight 888
[    20.573] (==) NOUVEAU(0): Default visual is TrueColor
[    20.573] (==) NOUVEAU(0): Using HW cursor
[    20.573] (==) NOUVEAU(0): GLX sync to VBlank enabled.
[    20.573] (==) NOUVEAU(0): Page flipping enabled
[    20.573] (==) NOUVEAU(0): Swap limit set to 2 [Max allowed 2]
[    20.598] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[    20.621] (II) NOUVEAU(0): Output DVI-I-2 has no monitor section
[    20.677] (II) NOUVEAU(0): Output HDMI-1 has no monitor section
[    20.804] (II) NOUVEAU(0): Output DP-1 has no monitor section
[    20.826] (II) NOUVEAU(0): EDID for output DVI-I-1
[    20.849] (II) NOUVEAU(0): EDID for output DVI-I-2
[    20.905] (II) NOUVEAU(0): EDID for output HDMI-1
[    20.905] (II) NOUVEAU(0): Manufacturer: ONK  Model: a62  Serial#: 0
[    20.905] (II) NOUVEAU(0): Year: 2010  Week: 0
[    20.905] (II) NOUVEAU(0): EDID Version: 1.3
[    20.905] (II) NOUVEAU(0): Digital Display Input
[    20.905] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 51  vert.: 29
[    20.905] (II) NOUVEAU(0): Gamma: 2.20
[    20.905] (II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off
[    20.905] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    20.905] (II) NOUVEAU(0): Default color space is primary color space
[    20.905] (II) NOUVEAU(0): First detailed timing is preferred mode
[    20.905] (II) NOUVEAU(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    20.905] (II) NOUVEAU(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    20.905] (II) NOUVEAU(0): Supported established timings:
[    20.905] (II) NOUVEAU(0): 720x400@70Hz
[    20.905] (II) NOUVEAU(0): 640x480@60Hz
[    20.905] (II) NOUVEAU(0): 640x480@75Hz
[    20.905] (II) NOUVEAU(0): 800x600@60Hz
[    20.905] (II) NOUVEAU(0): 800x600@75Hz
[    20.905] (II) NOUVEAU(0): 1024x768@60Hz
[    20.905] (II) NOUVEAU(0): 1024x768@75Hz
[    20.905] (II) NOUVEAU(0): 1280x1024@75Hz
[    20.905] (II) NOUVEAU(0): Manufacturer's mask: 0
[    20.905] (II) NOUVEAU(0): Supported standard timings:
[    20.905] (II) NOUVEAU(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    20.905] (II) NOUVEAU(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    20.905] (II) NOUVEAU(0): #2: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    20.905] (II) NOUVEAU(0): Supported detailed timing:
[    20.905] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  509 x 286 mm
[    20.905] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    20.905] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    20.905] (II) NOUVEAU(0): Monitor name: TX-SR608
[    20.905] (II) NOUVEAU(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[    20.905] (II) NOUVEAU(0): Number of EDID sections to follow: 1
[    20.905] (II) NOUVEAU(0): EDID (in hex):
[    20.905] (II) NOUVEAU(0): 	00ffffffffffff003dcb620a00000000
[    20.905] (II) NOUVEAU(0): 	0014010380331d78eeee95a3544c9926
[    20.905] (II) NOUVEAU(0): 	0f5054a54b00714f8180d1c001010101
[    20.905] (II) NOUVEAU(0): 	010101010101023a801871382d40582c
[    20.905] (II) NOUVEAU(0): 	4500fd1e1100001e0000001000000000
[    20.905] (II) NOUVEAU(0): 	00000000000000000000000000fc0054
[    20.905] (II) NOUVEAU(0): 	582d53523630380a20202020000000fd
[    20.905] (II) NOUVEAU(0): 	00384c1e5311000a2020202020200143
[    20.905] (II) NOUVEAU(0): 	02033c41538403020e0f232410059312
[    20.905] (II) NOUVEAU(0): 	111d1e2526011f1438097f070f7f0717
[    20.905] (II) NOUVEAU(0): 	07503f06c04d02005706005f7e016754
[    20.905] (II) NOUVEAU(0): 	00834f000066030c00ffff8000000010
[    20.905] (II) NOUVEAU(0): 	00000000000000000000000000000000
[    20.905] (II) NOUVEAU(0): 	00100000000000000000000000000000
[    20.905] (II) NOUVEAU(0): 	00000010000000000000000000000000
[    20.905] (II) NOUVEAU(0): 	000000000000000000000000000000b0
[    20.905] (II) NOUVEAU(0): Printing probed modes for output HDMI-1
[    20.905] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    20.905] (II) NOUVEAU(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "1920x1080i"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "1920x1080i"x50.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "1920x1080i"x59.9   74.18  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.7 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "2880x576"x50.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "2880x480"x60.0  108.11  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "2880x480"x59.9  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "1440x576"x50.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "1440x480"x60.0   54.05  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "1440x480"x59.9   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    20.905] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    21.032] (II) NOUVEAU(0): EDID for output DP-1
[    21.032] (II) NOUVEAU(0): Output DVI-I-1 disconnected
[    21.032] (II) NOUVEAU(0): Output DVI-I-2 disconnected
[    21.032] (II) NOUVEAU(0): Output HDMI-1 connected
[    21.032] (II) NOUVEAU(0): Output DP-1 disconnected
[    21.032] (II) NOUVEAU(0): Using exact sizes for initial modes
[    21.032] (II) NOUVEAU(0): Output HDMI-1 using initial mode 1920x1080
[    21.032] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    21.032] (--) NOUVEAU(0): Virtual size is 1920x1080 (pitch 0)
[    21.032] (**) NOUVEAU(0):  Driver mode "1920x1080": 148.5 MHz (scaled from 0.0 MHz), 67.5 kHz, 60.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    21.032] (**) NOUVEAU(0):  Driver mode "1920x1080": 148.5 MHz (scaled from 0.0 MHz), 56.2 kHz, 50.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "1920x1080": 148.4 MHz (scaled from 0.0 MHz), 67.4 kHz, 59.9 Hz
[    21.032] (II) NOUVEAU(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "1920x1080i": 74.2 MHz (scaled from 0.0 MHz), 33.8 kHz, 60.0 Hz (I)
[    21.032] (II) NOUVEAU(0): Modeline "1920x1080i"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "1920x1080i": 74.2 MHz (scaled from 0.0 MHz), 28.1 kHz, 50.0 Hz (I)
[    21.032] (II) NOUVEAU(0): Modeline "1920x1080i"x50.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "1920x1080i": 74.2 MHz (scaled from 0.0 MHz), 33.7 kHz, 59.9 Hz (I)
[    21.032] (II) NOUVEAU(0): Modeline "1920x1080i"x59.9   74.18  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.7 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "2880x576": 108.0 MHz (scaled from 0.0 MHz), 31.2 kHz, 50.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "2880x576"x50.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "2880x480": 108.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "2880x480"x60.0  108.11  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "2880x480": 108.0 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
[    21.032] (II) NOUVEAU(0): Modeline "2880x480"x59.9  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "1280x720": 74.2 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "1280x720": 74.2 MHz (scaled from 0.0 MHz), 37.5 kHz, 50.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "1280x720": 74.2 MHz (scaled from 0.0 MHz), 45.0 kHz, 59.9 Hz
[    21.032] (II) NOUVEAU(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "1440x576": 54.0 MHz (scaled from 0.0 MHz), 31.2 kHz, 50.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "1440x576"x50.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
[    21.032] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "1440x480": 54.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "1440x480"x60.0   54.05  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "1440x480": 54.0 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
[    21.032] (II) NOUVEAU(0): Modeline "1440x480"x59.9   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[    21.032] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "720x576": 27.0 MHz (scaled from 0.0 MHz), 31.2 kHz, 50.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "720x480": 27.0 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "720x480": 27.0 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
[    21.032] (II) NOUVEAU(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[    21.032] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
[    21.032] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    21.032] (**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[    21.032] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    21.032] (==) NOUVEAU(0): DPI set to (96, 96)
[    21.032] (II) Loading sub module "fb"
[    21.032] (II) LoadModule: "fb"
[    21.032] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.046] (II) Module fb: vendor="X.Org Foundation"
[    21.046] 	compiled for 1.14.3, module version = 1.0.0
[    21.046] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.046] (II) Loading sub module "exa"
[    21.046] (II) LoadModule: "exa"
[    21.046] (II) Loading /usr/lib/xorg/modules/libexa.so
[    21.055] (II) Module exa: vendor="X.Org Foundation"
[    21.055] 	compiled for 1.14.3, module version = 2.6.0
[    21.055] 	ABI class: X.Org Video Driver, version 14.1
[    21.055] (II) Loading sub module "shadowfb"
[    21.055] (II) LoadModule: "shadowfb"
[    21.055] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    21.055] (II) Module shadowfb: vendor="X.Org Foundation"
[    21.055] 	compiled for 1.14.3, module version = 1.0.0
[    21.055] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.055] (II) UnloadModule: "vesa"
[    21.055] (II) Unloading vesa
[    21.055] (II) UnloadModule: "modesetting"
[    21.055] (II) Unloading modesetting
[    21.055] (II) UnloadModule: "fbdev"
[    21.055] (II) Unloading fbdev
[    21.055] (II) UnloadSubModule: "fbdevhw"
[    21.055] (II) Unloading fbdevhw
[    21.055] (--) Depth 24 pixmap format is 32 bpp
[    21.057] (II) NOUVEAU(0): Opened GPU channel 0
[    21.073] (II) NOUVEAU(0): [DRI2] Setup complete
[    21.073] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[    21.073] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[    21.081] (II) EXA(0): Driver allocated offscreen pixmaps
[    21.081] (II) EXA(0): Driver registered support for the following operations:
[    21.081] (II)         Solid
[    21.081] (II)         Copy
[    21.081] (II)         Composite (RENDER acceleration)
[    21.081] (II)         UploadToScreen
[    21.081] (II)         DownloadFromScreen
[    21.081] (==) NOUVEAU(0): Backing store disabled
[    21.081] (==) NOUVEAU(0): Silken mouse enabled
[    21.081] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[    21.081] (II) NOUVEAU(0): [XvMC] Extension initialized.
[    21.081] (==) NOUVEAU(0): DPMS enabled
[    21.081] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.082] (--) RandR disabled
[    21.087] (II) SELinux: Disabled on system
[    22.662] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    22.662] (II) AIGLX: enabled GLX_INTEL_swap_event
[    22.662] (II) AIGLX: enabled GLX_ARB_create_context
[    22.662] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    22.662] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    22.662] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    22.662] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    22.663] (II) AIGLX: Loaded and initialized nouveau
[    22.663] (II) GLX: Initialized DRI2 GL provider for screen 0
[    22.666] (II) NOUVEAU(0): NVEnterVT is called.
[    22.694] (II) NOUVEAU(0): Setting screen physical size to 507 x 285
[    22.694] resize called 1920 1080
[    22.792] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.798] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    22.798] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.798] (II) LoadModule: "evdev"
[    22.798] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.829] (II) Module evdev: vendor="X.Org Foundation"
[    22.829] 	compiled for 1.14.1, module version = 2.7.3
[    22.829] 	Module class: X.Org XInput Driver
[    22.829] 	ABI class: X.Org XInput driver, version 19.1
[    22.829] (II) Using input driver 'evdev' for 'Power Button'
[    22.829] (**) Power Button: always reports core events
[    22.829] (**) evdev: Power Button: Device: "/dev/input/event1"
[    22.829] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.829] (--) evdev: Power Button: Found keys
[    22.829] (II) evdev: Power Button: Configuring as keyboard
[    22.829] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    22.829] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    22.829] (**) Option "xkb_rules" "evdev"
[    22.829] (**) Option "xkb_model" "pc105"
[    22.829] (**) Option "xkb_layout" "se"
[    22.830] (II) XKB: reuse xkmfile /var/lib/xkb/server-523B07B557B20588EB459118C97940B7C9FF61EB.xkm
[    22.831] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    22.831] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.831] (II) Using input driver 'evdev' for 'Power Button'
[    22.831] (**) Power Button: always reports core events
[    22.831] (**) evdev: Power Button: Device: "/dev/input/event0"
[    22.831] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.831] (--) evdev: Power Button: Found keys
[    22.831] (II) evdev: Power Button: Configuring as keyboard
[    22.831] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    22.831] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    22.831] (**) Option "xkb_rules" "evdev"
[    22.831] (**) Option "xkb_model" "pc105"
[    22.831] (**) Option "xkb_layout" "se"
[    22.831] (II) config/udev: Adding drm device (/dev/dri/card0)
[    22.831] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    22.831] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event15)
[    22.831] (II) No input driver specified, ignoring this device.
[    22.831] (II) This device may have been added with another device file.
[    22.831] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event16)
[    22.831] (II) No input driver specified, ignoring this device.
[    22.831] (II) This device may have been added with another device file.
[    22.832] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event17)
[    22.832] (II) No input driver specified, ignoring this device.
[    22.832] (II) This device may have been added with another device file.
[    22.832] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event18)
[    22.832] (II) No input driver specified, ignoring this device.
[    22.832] (II) This device may have been added with another device file.
[    22.832] (II) config/udev: Adding input device SteelSeries SteelSeries Apex Gaming Keyboard (/dev/input/event2)
[    22.832] (**) SteelSeries SteelSeries Apex Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[    22.832] (II) Using input driver 'evdev' for 'SteelSeries SteelSeries Apex Gaming Keyboard'
[    22.832] (**) SteelSeries SteelSeries Apex Gaming Keyboard: always reports core events
[    22.832] (**) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Device: "/dev/input/event2"
[    22.832] (--) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Vendor 0x1038 Product 0x1202
[    22.832] (--) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Found keys
[    22.832] (II) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Configuring as keyboard
[    22.832] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.1/input/input2/event2"
[    22.832] (II) XINPUT: Adding extended input device "SteelSeries SteelSeries Apex Gaming Keyboard" (type: KEYBOARD, id 8)
[    22.832] (**) Option "xkb_rules" "evdev"
[    22.832] (**) Option "xkb_model" "pc105"
[    22.832] (**) Option "xkb_layout" "se"
[    22.832] (II) config/udev: Adding input device SteelSeries SteelSeries Apex Gaming Keyboard (/dev/input/event3)
[    22.832] (**) SteelSeries SteelSeries Apex Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[    22.832] (II) Using input driver 'evdev' for 'SteelSeries SteelSeries Apex Gaming Keyboard'
[    22.832] (**) SteelSeries SteelSeries Apex Gaming Keyboard: always reports core events
[    22.832] (**) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Device: "/dev/input/event3"
[    22.832] (--) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Vendor 0x1038 Product 0x1202
[    22.832] (--) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Found 1 mouse buttons
[    22.832] (--) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Found scroll wheel(s)
[    22.832] (--) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Found relative axes
[    22.832] (II) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Forcing relative x/y axes to exist.
[    22.832] (--) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Found absolute axes
[    22.832] (II) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Forcing absolute x/y axes to exist.
[    22.832] (--) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Found keys
[    22.832] (II) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Configuring as mouse
[    22.832] (II) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Configuring as keyboard
[    22.832] (II) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Adding scrollwheel support
[    22.832] (**) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: YAxisMapping: buttons 4 and 5
[    22.832] (**) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.832] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.2/input/input3/event3"
[    22.832] (II) XINPUT: Adding extended input device "SteelSeries SteelSeries Apex Gaming Keyboard" (type: KEYBOARD, id 9)
[    22.832] (**) Option "xkb_rules" "evdev"
[    22.832] (**) Option "xkb_model" "pc105"
[    22.832] (**) Option "xkb_layout" "se"
[    22.833] (II) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: initialized for relative axes.
[    22.833] (WW) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: ignoring absolute axes.
[    22.833] (**) SteelSeries SteelSeries Apex Gaming Keyboard: (accel) keeping acceleration scheme 1
[    22.833] (**) SteelSeries SteelSeries Apex Gaming Keyboard: (accel) acceleration profile 0
[    22.833] (**) SteelSeries SteelSeries Apex Gaming Keyboard: (accel) acceleration factor: 2.000
[    22.833] (**) SteelSeries SteelSeries Apex Gaming Keyboard: (accel) acceleration threshold: 4
[    22.833] (II) config/udev: Adding input device Razer Razer DeathAdder 2013 (/dev/input/event4)
[    22.833] (**) Razer Razer DeathAdder 2013: Applying InputClass "evdev pointer catchall"
[    22.833] (II) Using input driver 'evdev' for 'Razer Razer DeathAdder 2013'
[    22.833] (**) Razer Razer DeathAdder 2013: always reports core events
[    22.833] (**) evdev: Razer Razer DeathAdder 2013: Device: "/dev/input/event4"
[    22.833] (--) evdev: Razer Razer DeathAdder 2013: Vendor 0x1532 Product 0x37
[    22.833] (--) evdev: Razer Razer DeathAdder 2013: Found 9 mouse buttons
[    22.833] (--) evdev: Razer Razer DeathAdder 2013: Found scroll wheel(s)
[    22.833] (--) evdev: Razer Razer DeathAdder 2013: Found relative axes
[    22.833] (--) evdev: Razer Razer DeathAdder 2013: Found x and y relative axes
[    22.833] (II) evdev: Razer Razer DeathAdder 2013: Configuring as mouse
[    22.833] (II) evdev: Razer Razer DeathAdder 2013: Adding scrollwheel support
[    22.833] (**) evdev: Razer Razer DeathAdder 2013: YAxisMapping: buttons 4 and 5
[    22.833] (**) evdev: Razer Razer DeathAdder 2013: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.833] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.2/1-1.3.2:1.0/input/input4/event4"
[    22.833] (II) XINPUT: Adding extended input device "Razer Razer DeathAdder 2013" (type: MOUSE, id 10)
[    22.833] (II) evdev: Razer Razer DeathAdder 2013: initialized for relative axes.
[    22.833] (**) Razer Razer DeathAdder 2013: (accel) keeping acceleration scheme 1
[    22.833] (**) Razer Razer DeathAdder 2013: (accel) acceleration profile 0
[    22.833] (**) Razer Razer DeathAdder 2013: (accel) acceleration factor: 2.000
[    22.833] (**) Razer Razer DeathAdder 2013: (accel) acceleration threshold: 4
[    22.833] (II) config/udev: Adding input device Razer Razer DeathAdder 2013 (/dev/input/mouse0)
[    22.833] (II) No input driver specified, ignoring this device.
[    22.833] (II) This device may have been added with another device file.
[    22.834] (II) config/udev: Adding input device Razer Razer DeathAdder 2013 (/dev/input/event5)
[    22.834] (**) Razer Razer DeathAdder 2013: Applying InputClass "evdev keyboard catchall"
[    22.834] (II) Using input driver 'evdev' for 'Razer Razer DeathAdder 2013'
[    22.834] (**) Razer Razer DeathAdder 2013: always reports core events
[    22.834] (**) evdev: Razer Razer DeathAdder 2013: Device: "/dev/input/event5"
[    22.834] (--) evdev: Razer Razer DeathAdder 2013: Vendor 0x1532 Product 0x37
[    22.834] (--) evdev: Razer Razer DeathAdder 2013: Found 1 mouse buttons
[    22.834] (--) evdev: Razer Razer DeathAdder 2013: Found scroll wheel(s)
[    22.834] (--) evdev: Razer Razer DeathAdder 2013: Found relative axes
[    22.834] (II) evdev: Razer Razer DeathAdder 2013: Forcing relative x/y axes to exist.
[    22.834] (--) evdev: Razer Razer DeathAdder 2013: Found absolute axes
[    22.834] (--) evdev: Razer Razer DeathAdder 2013: Found absolute multitouch axes
[    22.834] (--) evdev: Razer Razer DeathAdder 2013: Found keys
[    22.834] (II) evdev: Razer Razer DeathAdder 2013: Configuring as mouse
[    22.834] (II) evdev: Razer Razer DeathAdder 2013: Configuring as keyboard
[    22.834] (II) evdev: Razer Razer DeathAdder 2013: Adding scrollwheel support
[    22.834] (**) evdev: Razer Razer DeathAdder 2013: YAxisMapping: buttons 4 and 5
[    22.834] (**) evdev: Razer Razer DeathAdder 2013: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.834] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.2/1-1.3.2:1.1/input/input5/event5"
[    22.834] (II) XINPUT: Adding extended input device "Razer Razer DeathAdder 2013" (type: KEYBOARD, id 11)
[    22.834] (**) Option "xkb_rules" "evdev"
[    22.834] (**) Option "xkb_model" "pc105"
[    22.834] (**) Option "xkb_layout" "se"
[    22.834] (II) evdev: Razer Razer DeathAdder 2013: initialized for relative axes.
[    22.834] (WW) evdev: Razer Razer DeathAdder 2013: ignoring absolute axes.
[    22.834] (**) Razer Razer DeathAdder 2013: (accel) keeping acceleration scheme 1
[    22.834] (**) Razer Razer DeathAdder 2013: (accel) acceleration profile 0
[    22.834] (**) Razer Razer DeathAdder 2013: (accel) acceleration factor: 2.000
[    22.834] (**) Razer Razer DeathAdder 2013: (accel) acceleration threshold: 4
[    22.834] (II) config/udev: Adding input device Razer Razer DeathAdder 2013 (/dev/input/event6)
[    22.834] (**) Razer Razer DeathAdder 2013: Applying InputClass "evdev keyboard catchall"
[    22.834] (II) Using input driver 'evdev' for 'Razer Razer DeathAdder 2013'
[    22.834] (**) Razer Razer DeathAdder 2013: always reports core events
[    22.834] (**) evdev: Razer Razer DeathAdder 2013: Device: "/dev/input/event6"
[    22.834] (--) evdev: Razer Razer DeathAdder 2013: Vendor 0x1532 Product 0x37
[    22.834] (--) evdev: Razer Razer DeathAdder 2013: Found keys
[    22.834] (II) evdev: Razer Razer DeathAdder 2013: Configuring as keyboard
[    22.834] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.2/1-1.3.2:1.2/input/input6/event6"
[    22.834] (II) XINPUT: Adding extended input device "Razer Razer DeathAdder 2013" (type: KEYBOARD, id 12)
[    22.834] (**) Option "xkb_rules" "evdev"
[    22.834] (**) Option "xkb_model" "pc105"
[    22.834] (**) Option "xkb_layout" "se"
[    22.835] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event10)
[    22.835] (II) No input driver specified, ignoring this device.
[    22.835] (II) This device may have been added with another device file.
[    22.835] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event11)
[    22.835] (II) No input driver specified, ignoring this device.
[    22.835] (II) This device may have been added with another device file.
[    22.835] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event12)
[    22.835] (II) No input driver specified, ignoring this device.
[    22.835] (II) This device may have been added with another device file.
[    22.835] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event13)
[    22.835] (II) No input driver specified, ignoring this device.
[    22.835] (II) This device may have been added with another device file.
[    22.835] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event14)
[    22.835] (II) No input driver specified, ignoring this device.
[    22.835] (II) This device may have been added with another device file.
[    22.835] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event7)
[    22.835] (II) No input driver specified, ignoring this device.
[    22.835] (II) This device may have been added with another device file.
[    22.835] (II) config/udev: Adding input device HDA Intel PCH Line Out Side (/dev/input/event8)
[    22.835] (II) No input driver specified, ignoring this device.
[    22.835] (II) This device may have been added with another device file.
[    22.835] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event9)
[    22.835] (II) No input driver specified, ignoring this device.
[    22.835] (II) This device may have been added with another device file.
[    37.228] (II) evdev: Razer Razer DeathAdder 2013: Close
[    37.228] (II) UnloadModule: "evdev"
[    37.228] (II) evdev: Razer Razer DeathAdder 2013: Close
[    37.228] (II) UnloadModule: "evdev"
[    37.228] (II) evdev: Razer Razer DeathAdder 2013: Close
[    37.228] (II) UnloadModule: "evdev"
[    37.228] (II) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Close
[    37.228] (II) UnloadModule: "evdev"
[    37.228] (II) evdev: SteelSeries SteelSeries Apex Gaming Keyboard: Close
[    37.228] (II) UnloadModule: "evdev"
[    37.228] (II) evdev: Power Button: Close
[    37.228] (II) UnloadModule: "evdev"
[    37.228] (II) evdev: Power Button: Close
[    37.228] (II) UnloadModule: "evdev"
[    37.230] (II) NOUVEAU(0): NVLeaveVT is called.
[    37.231] (II) NOUVEAU(0): Closed GPU channel 0
[    37.272] (EE) Server terminated successfully (0). Closing log file.
```

---

### Post by claracc on 2014-01-04
Perhaps, this most updated thread [http://ubuntuforums.org/showthread.php?t=2161403](http://ubuntuforums.org/showthread.php?t=2161403) can help you.

---

### Post by RaZoR1394 on 2014-01-04
Thanks for helping. I tried all tips in those links without any luck. I'm starting to believe my system is totally broken.

I did purge all nvidia* packages and I could enter into lightdm but after logging in the desktop is totally black and in very low resolution.

---

### Post by mc4man on 2014-01-04
What does this show - 
```
sudo update-alternatives --config i386-linux-gnu_gl_conf
```
(- also, do you have a /etc/X11/xorg.conf file?

---

### Post by RaZoR1394 on 2014-01-04
Sorry, It's in swedish...

Without Nvidia drivers installed it show:

```
Det finns bara ett alternativ i länkgruppen i386-linux-gnu_gl_conf (tillhandahåller /etc/ld.so.conf.d/i386-linux-gnu_GL.conf): /usr/lib/i386-linux-gnu/mesa/ld.so.conf
Inget att konfigurera.
```

With the Nvidia drivers it shows```
Det finns 3 val för alternativet i386-linux-gnu_gl_conf (som tillhandahåller /etc/ld.so.conf.d/i386-linux-gnu_GL.conf).

  Val          Sökväg                                 Prioritet  Status
------------------------------------------------------------
* 0            /usr/lib/nvidia-331/ld.so.conf            8604      automatiskt läge
  1            /usr/lib/i386-linux-gnu/mesa/ld.so.conf   500       manuellt läge
  2            /usr/lib/nvidia-331-prime/ld.so.conf      8603      manuellt läge
  3            /usr/lib/nvidia-331/ld.so.conf            8604      manuellt läge

Tryck Enter för att behålla standardvärdet[*], eller ange nummer på önskat val: 
```

I've tried with and without a Xorg.conf. Currently I'm using one generated by nvidia-xconfig.

---

### Post by mc4man on 2014-01-04
That looks ok, just wanted to see if removing nvidia left a dangling link.
I guess I'd try one more time to get back to nouveau - 

purge nvidia packages
run - 
sudo ldconfig
sudo update-initramfs -u

Remove any/all  xorg.conf files in /etc/X11/
reboot to current or any other avail. kernel

---

### Post by steeldriver on 2014-01-04
I don't read Swedish but I believe I had a similar issue when trying to install the CUDA SDK (which installs nvidia 319 proprietary) on my 12.04 system (it is saying that it can't configure because another package owns the symlink?) If so I believe I solved it by running

```
sudo update-alternatives --remove-all i386-linux-gnu_gl_conf
```

followed by

```
sudo apt-get -f install
```

however you may want to try removing only the /usr/lib/i386-linux-gnu/mesa/ld.so.conf alternative first

---

### Post by RaZoR1394 on 2014-01-04
Thanks.

I tried both your tips but I'm still stuck.

---

### Post by caymus on 2014-01-04
if you have xorg/edgers depots like me, bumblebee into nvidia-331 is the culprit
I dont know if it is the same on officials depots now.

Same problem for me after the last update, on my 770gtx

after messing 30 min (i m becoming crazy or dumb?)....

I have take a closer look at nvidia-331 & bumblebee is packaged with this driver.

Here how i have solved this mess:

delete all xorg.conf*

```

sudo apt-get purge nvidia-*
sudo apt-get purge bumblebee*
sudo apt-get autoremove
sudo apt-get autoclean

```

them
```

sudo apt-get install nvidia-331
sudo apt-get remove --purge bumblebee
sudo nvidia-xconfig

```

then reboot

I dont know why but optirun or bumblebee is packaged with nvidia-331 (maybe for laptop users)

Since i use a desktop, with nvidia 770, with 4 screens & i disable intel i7 gpu into bios, bumblebee or optirun is the last thing i wan to be enable.

Now it work fine for my desktop with optirun & bumblebee removed.

It is maybe your problem also?

---

### Post by mörgæs on 2014-01-05
Razor, please use CODE tags in stead of QUOTE.

---

