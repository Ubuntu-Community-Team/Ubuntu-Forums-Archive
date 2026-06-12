---
title: "Mouse and Keyboard take 30 seconds to be detected at startup"
date: 2015-08-31
forum: General Help
---

### Post by JazzPotato on 2015-08-31
Hi There,
My mouse and keyboard only work around 30 seconds after startup.

Here's my Xorg.0.log, check around 43 seconds in to see my mouse and keyboard being registered.

```

[     2.903] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[     2.903] X Protocol Version 11, Revision 0
[     2.903] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[     2.903] Current Operating System: Linux glcheetham-pc 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64
[     2.903] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-38-generic root=UUID=473ad0e8-d936-4a2b-ad6c-69d8b5aa54d9 ro quiet splash vt.handoff=7
[     2.903] Build Date: 12 February 2015  02:49:29PM
[     2.903] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[     2.903] Current version of pixman: 0.30.2
[     2.903]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     2.903] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     2.903] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 31 08:56:38 2015
[     2.904] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     2.906] (==) No Layout section.  Using the first Screen section.
[     2.906] (==) No screen section available. Using defaults.
[     2.906] (**) |-->Screen "Default Screen Section" (0)
[     2.906] (**) |   |-->Monitor "<default monitor>"
[     2.906] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     2.906] (==) Automatically adding devices
[     2.906] (==) Automatically enabling devices
[     2.906] (==) Automatically adding GPU devices
[     2.912] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     2.912]     Entry deleted from font path.
[     2.912] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     2.912]     Entry deleted from font path.
[     2.912] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     2.912]     Entry deleted from font path.
[     2.912] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     2.912]     Entry deleted from font path.
[     2.912] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     2.912]     Entry deleted from font path.
[     2.912] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     2.912] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     2.912] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     2.912] (II) Loader magic: 0x7f636183dd40
[     2.912] (II) Module ABI versions:
[     2.912]     X.Org ANSI C Emulation: 0.4
[     2.912]     X.Org Video Driver: 15.0
[     2.912]     X.Org XInput driver : 20.0
[     2.912]     X.Org Server Extension : 8.0
[     2.912] (II) xfree86: Adding drm device (/dev/dri/card0)
[     2.913] (--) PCI:*(0:1:0:0) 10de:1184:1043:8465 rev 161, Mem @ 0xf6000000/16777216, 0xe8000000/134217728, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     2.913] Initializing built-in extension Generic Event Extension
[     2.913] Initializing built-in extension SHAPE
[     2.913] Initializing built-in extension MIT-SHM
[     2.913] Initializing built-in extension XInputExtension
[     2.913] Initializing built-in extension XTEST
[     2.913] Initializing built-in extension BIG-REQUESTS
[     2.913] Initializing built-in extension SYNC
[     2.913] Initializing built-in extension XKEYBOARD
[     2.913] Initializing built-in extension XC-MISC
[     2.913] Initializing built-in extension SECURITY
[     2.913] Initializing built-in extension XINERAMA
[     2.913] Initializing built-in extension XFIXES
[     2.913] Initializing built-in extension RENDER
[     2.913] Initializing built-in extension RANDR
[     2.913] Initializing built-in extension COMPOSITE
[     2.913] Initializing built-in extension DAMAGE
[     2.913] Initializing built-in extension MIT-SCREEN-SAVER
[     2.913] Initializing built-in extension DOUBLE-BUFFER
[     2.913] Initializing built-in extension RECORD
[     2.913] Initializing built-in extension DPMS
[     2.913] Initializing built-in extension Present
[     2.913] Initializing built-in extension DRI3
[     2.913] Initializing built-in extension X-Resource
[     2.913] Initializing built-in extension XVideo
[     2.913] Initializing built-in extension XVideo-MotionCompensation
[     2.913] Initializing built-in extension SELinux
[     2.913] Initializing built-in extension XFree86-VidModeExtension
[     2.913] Initializing built-in extension XFree86-DGA
[     2.913] Initializing built-in extension XFree86-DRI
[     2.913] Initializing built-in extension DRI2
[     2.913] (II) LoadModule: "glx"
[     2.916] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     2.925] (II) Module glx: vendor="X.Org Foundation"
[     2.925]     compiled for 1.15.1, module version = 1.0.0
[     2.925]     ABI class: X.Org Server Extension, version 8.0
[     2.925] (==) AIGLX enabled
[     2.925] Loading extension GLX
[     2.925] (==) Matched nvidia as autoconfigured driver 0
[     2.925] (==) Matched nouveau as autoconfigured driver 1
[     2.925] (==) Matched nvidia as autoconfigured driver 2
[     2.925] (==) Matched nouveau as autoconfigured driver 3
[     2.925] (==) Matched modesetting as autoconfigured driver 4
[     2.925] (==) Matched fbdev as autoconfigured driver 5
[     2.925] (==) Matched vesa as autoconfigured driver 6
[     2.925] (==) Assigned the driver to the xf86ConfigLayout
[     2.925] (II) LoadModule: "nvidia"
[     2.925] (WW) Warning, couldn't open module nvidia
[     2.925] (II) UnloadModule: "nvidia"
[     2.925] (II) Unloading nvidia
[     2.925] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     2.925] (II) LoadModule: "nouveau"
[     2.925] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     2.928] (II) Module nouveau: vendor="X.Org Foundation"
[     2.928]     compiled for 1.15.0, module version = 1.0.10
[     2.928]     Module class: X.Org Video Driver
[     2.928]     ABI class: X.Org Video Driver, version 15.0
[     2.928] (II) LoadModule: "modesetting"
[     2.928] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     2.929] (II) Module modesetting: vendor="X.Org Foundation"
[     2.929]     compiled for 1.15.0, module version = 0.8.1
[     2.929]     Module class: X.Org Video Driver
[     2.929]     ABI class: X.Org Video Driver, version 15.0
[     2.929] (II) LoadModule: "fbdev"
[     2.929] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     2.929] (II) Module fbdev: vendor="X.Org Foundation"
[     2.929]     compiled for 1.15.0, module version = 0.4.4
[     2.929]     Module class: X.Org Video Driver
[     2.929]     ABI class: X.Org Video Driver, version 15.0
[     2.929] (II) LoadModule: "vesa"
[     2.929] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     2.930] (II) Module vesa: vendor="X.Org Foundation"
[     2.930]     compiled for 1.15.0, module version = 2.3.3
[     2.930]     Module class: X.Org Video Driver
[     2.930]     ABI class: X.Org Video Driver, version 15.0
[     2.930] (==) Matched nvidia as autoconfigured driver 0
[     2.930] (==) Matched nouveau as autoconfigured driver 1
[     2.930] (==) Matched nvidia as autoconfigured driver 2
[     2.930] (==) Matched nouveau as autoconfigured driver 3
[     2.930] (==) Matched modesetting as autoconfigured driver 4
[     2.930] (==) Matched fbdev as autoconfigured driver 5
[     2.930] (==) Matched vesa as autoconfigured driver 6
[     2.930] (==) Assigned the driver to the xf86ConfigLayout
[     2.930] (II) LoadModule: "nvidia"
[     2.931] (WW) Warning, couldn't open module nvidia
[     2.931] (II) UnloadModule: "nvidia"
[     2.931] (II) Unloading nvidia
[     2.931] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     2.931] (II) LoadModule: "nouveau"
[     2.931] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     2.931] (II) Module nouveau: vendor="X.Org Foundation"
[     2.931]     compiled for 1.15.0, module version = 1.0.10
[     2.931]     Module class: X.Org Video Driver
[     2.931]     ABI class: X.Org Video Driver, version 15.0
[     2.931] (II) UnloadModule: "nouveau"
[     2.931] (II) Unloading nouveau
[     2.931] (II) Failed to load module "nouveau" (already loaded, 0)
[     2.931] (II) LoadModule: "modesetting"
[     2.931] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     2.931] (II) Module modesetting: vendor="X.Org Foundation"
[     2.931]     compiled for 1.15.0, module version = 0.8.1
[     2.931]     Module class: X.Org Video Driver
[     2.931]     ABI class: X.Org Video Driver, version 15.0
[     2.931] (II) UnloadModule: "modesetting"
[     2.931] (II) Unloading modesetting
[     2.931] (II) Failed to load module "modesetting" (already loaded, 0)
[     2.931] (II) LoadModule: "fbdev"
[     2.931] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     2.931] (II) Module fbdev: vendor="X.Org Foundation"
[     2.931]     compiled for 1.15.0, module version = 0.4.4
[     2.931]     Module class: X.Org Video Driver
[     2.931]     ABI class: X.Org Video Driver, version 15.0
[     2.931] (II) UnloadModule: "fbdev"
[     2.931] (II) Unloading fbdev
[     2.931] (II) Failed to load module "fbdev" (already loaded, 0)
[     2.931] (II) LoadModule: "vesa"
[     2.931] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     2.931] (II) Module vesa: vendor="X.Org Foundation"
[     2.931]     compiled for 1.15.0, module version = 2.3.3
[     2.931]     Module class: X.Org Video Driver
[     2.931]     ABI class: X.Org Video Driver, version 15.0
[     2.931] (II) UnloadModule: "vesa"
[     2.931] (II) Unloading vesa
[     2.931] (II) Failed to load module "vesa" (already loaded, 0)
[     2.931] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[     2.931] (II) NOUVEAU driver for NVIDIA chipset families :
[     2.931]     RIVA TNT        (NV04)
[     2.931]     RIVA TNT2       (NV05)
[     2.931]     GeForce 256     (NV10)
[     2.931]     GeForce 2       (NV11, NV15)
[     2.931]     GeForce 4MX     (NV17, NV18)
[     2.931]     GeForce 3       (NV20)
[     2.931]     GeForce 4Ti     (NV25, NV28)
[     2.931]     GeForce FX      (NV3x)
[     2.931]     GeForce 6       (NV4x)
[     2.931]     GeForce 7       (G7x)
[     2.931]     GeForce 8       (G8x)
[     2.931]     GeForce GTX 200 (NVA0)
[     2.931]     GeForce GTX 400 (NVC0)
[     2.931] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     2.931] (II) FBDEV: driver for framebuffer: fbdev
[     2.931] (II) VESA: driver for VESA chipsets: vesa
[     2.931] (++) using VT number 8


[     2.934] (II) [drm] nouveau interface version: 1.1.2
[     2.934] (WW) Falling back to old probe method for modesetting
[     2.934] (WW) Falling back to old probe method for fbdev
[     2.934] (II) Loading sub module "fbdevhw"
[     2.934] (II) LoadModule: "fbdevhw"
[     2.934] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     2.935] (II) Module fbdevhw: vendor="X.Org Foundation"
[     2.935]     compiled for 1.15.1, module version = 0.0.2
[     2.935]     ABI class: X.Org Video Driver, version 15.0
[     2.935] (WW) Falling back to old probe method for vesa
[     2.935] (II) Loading sub module "dri2"
[     2.935] (II) LoadModule: "dri2"
[     2.935] (II) Module "dri2" already built-in
[     2.935] (--) NOUVEAU(0): Chipset: "NVIDIA NVE4"
[     2.935] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     2.935] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[     2.935] (==) NOUVEAU(0): RGB weight 888
[     2.935] (==) NOUVEAU(0): Default visual is TrueColor
[     2.935] (==) NOUVEAU(0): Using HW cursor
[     2.935] (==) NOUVEAU(0): GLX sync to VBlank enabled.
[     2.935] (==) NOUVEAU(0): Page flipping enabled
[     2.935] (==) NOUVEAU(0): Swap limit set to 2 [Max allowed 2]
[     2.962] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[     2.965] (II) NOUVEAU(0): Output DVI-D-1 has no monitor section
[     2.967] (II) NOUVEAU(0): Output HDMI-1 has no monitor section
[     2.988] (II) NOUVEAU(0): Output DP-1 has no monitor section
[     3.012] (II) NOUVEAU(0): EDID for output DVI-I-1
[     3.014] (II) NOUVEAU(0): EDID for output DVI-D-1
[     3.016] (II) NOUVEAU(0): EDID for output HDMI-1
[     3.038] (II) NOUVEAU(0): EDID for output DP-1
[     3.038] (II) NOUVEAU(0): Manufacturer: GSM  Model: 5ae2  Serial#: 16843009
[     3.038] (II) NOUVEAU(0): Year: 2013  Week: 50
[     3.038] (II) NOUVEAU(0): EDID Version: 1.4
[     3.038] (II) NOUVEAU(0): Digital Display Input
[     3.038] (II) NOUVEAU(0): 8 bits per channel
[     3.038] (II) NOUVEAU(0): Digital interface is DisplayPort
[     3.038] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 80  vert.: 34
[     3.038] (II) NOUVEAU(0): Gamma: 2.20
[     3.038] (II) NOUVEAU(0): DPMS capabilities: StandBy
[     3.038] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 YCrCb 4:2:2
[     3.038] (II) NOUVEAU(0): Default color space is primary color space
[     3.038] (II) NOUVEAU(0): First detailed timing is preferred mode
[     3.038] (II) NOUVEAU(0): Preferred mode is native pixel format and refresh rate
[     3.038] (II) NOUVEAU(0): redX: 0.651 redY: 0.332   greenX: 0.307 greenY: 0.631
[     3.038] (II) NOUVEAU(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[     3.038] (II) NOUVEAU(0): Supported established timings:
[     3.038] (II) NOUVEAU(0): 640x480@60Hz
[     3.038] (II) NOUVEAU(0): 800x600@60Hz
[     3.038] (II) NOUVEAU(0): 1024x768@60Hz
[     3.038] (II) NOUVEAU(0): Manufacturer's mask: 0
[     3.038] (II) NOUVEAU(0): Supported standard timings:
[     3.038] (II) NOUVEAU(0): #0: hsize: 1152  vsize 864  refresh: 60  vid: 16497
[     3.038] (II) NOUVEAU(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     3.038] (II) NOUVEAU(0): #2: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[     3.038] (II) NOUVEAU(0): #3: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[     3.038] (II) NOUVEAU(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     3.038] (II) NOUVEAU(0): #5: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     3.038] (II) NOUVEAU(0): #6: hsize: 1280  vsize 800  refresh: 60  vid: 129
[     3.038] (II) NOUVEAU(0): Supported detailed timing:
[     3.038] (II) NOUVEAU(0): clock: 319.8 MHz   Image Size:  800 x 335 mm
[     3.038] (II) NOUVEAU(0): h_active: 3440  h_sync: 3488  h_sync_end 3520 h_blank_end 3600 h_border: 0
[     3.038] (II) NOUVEAU(0): v_active: 1440  v_sync: 1443  v_sync_end 1453 v_blanking: 1481 v_border: 0
[     3.038] (II) NOUVEAU(0): Supported detailed timing:
[     3.038] (II) NOUVEAU(0): clock: 265.2 MHz   Image Size:  800 x 335 mm
[     3.038] (II) NOUVEAU(0): h_active: 3440  h_sync: 3488  h_sync_end 3520 h_blank_end 3600 h_border: 0
[     3.038] (II) NOUVEAU(0): v_active: 1440  v_sync: 1443  v_sync_end 1453 v_blanking: 1474 v_border: 0
[     3.038] (II) NOUVEAU(0): Ranges: V min: 56 V max: 61 Hz, H min: 30 H max: 90 kHz, PixClock max 325 MHz
[     3.038] (II) NOUVEAU(0): Monitor name: LG ULTRAWIDE
[     3.038] (II) NOUVEAU(0): Supported detailed timing:
[     3.038] (II) NOUVEAU(0): clock: 157.8 MHz   Image Size:  800 x 335 mm
[     3.038] (II) NOUVEAU(0): h_active: 3440  h_sync: 3488  h_sync_end 3520 h_blank_end 3600 h_border: 0
[     3.038] (II) NOUVEAU(0): v_active: 1440  v_sync: 1443  v_sync_end 1453 v_blanking: 1461 v_border: 0
[     3.038] (II) NOUVEAU(0): Supported detailed timing:
[     3.038] (II) NOUVEAU(0): clock: 185.6 MHz   Image Size:  800 x 335 mm
[     3.038] (II) NOUVEAU(0): h_active: 2560  h_sync: 2624  h_sync_end 2688 h_blank_end 2784 h_border: 0
[     3.038] (II) NOUVEAU(0): v_active: 1080  v_sync: 1083  v_sync_end 1093 v_blanking: 1111 v_border: 0
[     3.038] (II) NOUVEAU(0): Supported detailed timing:
[     3.038] (II) NOUVEAU(0): clock: 74.2 MHz   Image Size:  800 x 335 mm
[     3.038] (II) NOUVEAU(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[     3.038] (II) NOUVEAU(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[     3.038] (II) NOUVEAU(0): Supported detailed timing:
[     3.038] (II) NOUVEAU(0): clock: 27.0 MHz   Image Size:  800 x 335 mm
[     3.038] (II) NOUVEAU(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[     3.038] (II) NOUVEAU(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[     3.038] (II) NOUVEAU(0): Supported detailed timing:
[     3.038] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  800 x 335 mm
[     3.038] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     3.038] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     3.038] (II) NOUVEAU(0): Number of EDID sections to follow: 1
[     3.038] (II) NOUVEAU(0): EDID (in hex):
[     3.038] (II) NOUVEAU(0):     00ffffffffffff001e6de25a01010101
[     3.038] (II) NOUVEAU(0):     32170104a55022789eca95a6554ea126
[     3.038] (II) NOUVEAU(0):     0f50542108007140818081c0a9c0b300
[     3.038] (II) NOUVEAU(0):     d1c081000101e77c70a0d0a029503020
[     3.038] (II) NOUVEAU(0):     3a00204f3100001a9d6770a0d0a02250
[     3.038] (II) NOUVEAU(0):     30203a00204f3100001a000000fd0038
[     3.038] (II) NOUVEAU(0):     3d1e5a20000a202020202020000000fc
[     3.038] (II) NOUVEAU(0):     004c4720554c545241574944450a0139
[     3.038] (II) NOUVEAU(0):     02031171230906074410040301830100
[     3.038] (II) NOUVEAU(0):     009f3d70a0d0a0155030203a00204f31
[     3.038] (II) NOUVEAU(0):     00001a7e4800e0a0381f4040403a0020
[     3.038] (II) NOUVEAU(0):     4f31000018011d007251d01e206e2855
[     3.038] (II) NOUVEAU(0):     00204f3100001e8c0ad08a20e02d1010
[     3.038] (II) NOUVEAU(0):     3e9600204f31000018023a801871382d
[     3.038] (II) NOUVEAU(0):     40582c4500204f3100001e0000000000
[     3.038] (II) NOUVEAU(0):     0000000000000000000000000000003a
[     3.038] (II) NOUVEAU(0): Printing probed modes for output DP-1
[     3.038] (II) NOUVEAU(0): Modeline "3440x1440"x60.0  319.75  3440 3488 3520 3600  1440 1443 1453 1481 +hsync -vsync (88.8 kHz eP)
[     3.038] (II) NOUVEAU(0): Modeline "3440x1440"x50.0  265.25  3440 3488 3520 3600  1440 1443 1453 1474 +hsync -vsync (73.7 kHz e)
[     3.038] (II) NOUVEAU(0): Modeline "3440x1440"x30.0  157.75  3440 3488 3520 3600  1440 1443 1453 1461 +hsync -vsync (43.8 kHz e)
[     3.038] (II) NOUVEAU(0): Modeline "2560x1080"x60.0  185.58  2560 2624 2688 2784  1080 1083 1093 1111 -hsync -vsync (66.7 kHz e)
[     3.038] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     3.038] (II) NOUVEAU(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[     3.038] (II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[     3.038] (II) NOUVEAU(0): Modeline "1600x900"x60.0  118.96  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[     3.038] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     3.038] (II) NOUVEAU(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz e)
[     3.038] (II) NOUVEAU(0): Modeline "1152x864"x60.0   81.58  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[     3.038] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     3.038] (II) NOUVEAU(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     3.038] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     3.038] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     3.038] (II) NOUVEAU(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     3.038] (II) NOUVEAU(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     3.038] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     3.038] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     3.038] (II) NOUVEAU(0): Output DVI-I-1 disconnected
[     3.038] (II) NOUVEAU(0): Output DVI-D-1 disconnected
[     3.038] (II) NOUVEAU(0): Output HDMI-1 disconnected
[     3.038] (II) NOUVEAU(0): Output DP-1 connected
[     3.038] (II) NOUVEAU(0): Using exact sizes for initial modes
[     3.038] (II) NOUVEAU(0): Output DP-1 using initial mode 3440x1440
[     3.038] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     3.038] (--) NOUVEAU(0): Virtual size is 3440x1440 (pitch 0)
[     3.038] (**) NOUVEAU(0):  Driver mode "3440x1440": 319.8 MHz (scaled from 0.0 MHz), 88.8 kHz, 60.0 Hz
[     3.038] (II) NOUVEAU(0): Modeline "3440x1440"x60.0  319.75  3440 3488 3520 3600  1440 1443 1453 1481 +hsync -vsync (88.8 kHz eP)
[     3.038] (**) NOUVEAU(0):  Driver mode "3440x1440": 265.2 MHz (scaled from 0.0 MHz), 73.7 kHz, 50.0 Hz
[     3.038] (II) NOUVEAU(0): Modeline "3440x1440"x50.0  265.25  3440 3488 3520 3600  1440 1443 1453 1474 +hsync -vsync (73.7 kHz e)
[     3.038] (**) NOUVEAU(0):  Driver mode "3440x1440": 157.8 MHz (scaled from 0.0 MHz), 43.8 kHz, 30.0 Hz
[     3.038] (II) NOUVEAU(0): Modeline "3440x1440"x30.0  157.75  3440 3488 3520 3600  1440 1443 1453 1461 +hsync -vsync (43.8 kHz e)
[     3.038] (**) NOUVEAU(0):  Driver mode "2560x1080": 185.6 MHz (scaled from 0.0 MHz), 66.7 kHz, 60.0 Hz
[     3.038] (II) NOUVEAU(0): Modeline "2560x1080"x60.0  185.58  2560 2624 2688 2784  1080 1083 1093 1111 -hsync -vsync (66.7 kHz e)
[     3.038] (**) NOUVEAU(0):  Driver mode "1920x1080": 148.5 MHz (scaled from 0.0 MHz), 67.5 kHz, 60.0 Hz
[     3.038] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     3.038] (**) NOUVEAU(0):  Driver mode "1920x1080": 148.4 MHz (scaled from 0.0 MHz), 67.4 kHz, 59.9 Hz
[     3.038] (II) NOUVEAU(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[     3.038] (**) NOUVEAU(0):  Driver mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
[     3.038] (II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[     3.038] (**) NOUVEAU(0):  Mode "1600x900": 119.0 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
[     3.038] (II) NOUVEAU(0): Modeline "1600x900"x60.0  118.96  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[     3.038] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[     3.038] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     3.038] (**) NOUVEAU(0):  Driver mode "1280x800": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 59.8 Hz
[     3.038] (II) NOUVEAU(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz e)
[     3.038] (**) NOUVEAU(0):  Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
[     3.038] (II) NOUVEAU(0): Modeline "1152x864"x60.0   81.58  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[     3.038] (**) NOUVEAU(0):  Driver mode "1280x720": 74.2 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz
[     3.038] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     3.038] (**) NOUVEAU(0):  Driver mode "1280x720": 74.2 MHz (scaled from 0.0 MHz), 45.0 kHz, 59.9 Hz
[     3.038] (II) NOUVEAU(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     3.038] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[     3.038] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     3.038] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[     3.038] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     3.038] (**) NOUVEAU(0):  Driver mode "720x480": 27.0 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[     3.038] (II) NOUVEAU(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     3.038] (**) NOUVEAU(0):  Driver mode "720x480": 27.0 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
[     3.038] (II) NOUVEAU(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     3.038] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[     3.038] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     3.038] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
[     3.038] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     3.038] (==) NOUVEAU(0): DPI set to (96, 96)
[     3.038] (II) Loading sub module "fb"
[     3.038] (II) LoadModule: "fb"
[     3.038] (II) Loading /usr/lib/xorg/modules/libfb.so
[     3.093] (II) Module fb: vendor="X.Org Foundation"
[     3.093]     compiled for 1.15.1, module version = 1.0.0
[     3.093]     ABI class: X.Org ANSI C Emulation, version 0.4
[     3.093] (II) Loading sub module "exa"
[     3.093] (II) LoadModule: "exa"
[     3.094] (II) Loading /usr/lib/xorg/modules/libexa.so
[     3.094] (II) Module exa: vendor="X.Org Foundation"
[     3.094]     compiled for 1.15.1, module version = 2.6.0
[     3.094]     ABI class: X.Org Video Driver, version 15.0
[     3.094] (II) Loading sub module "shadowfb"
[     3.094] (II) LoadModule: "shadowfb"
[     3.094] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[     3.094] (II) Module shadowfb: vendor="X.Org Foundation"
[     3.094]     compiled for 1.15.1, module version = 1.0.0
[     3.094]     ABI class: X.Org ANSI C Emulation, version 0.4
[     3.094] (II) UnloadModule: "modesetting"
[     3.094] (II) Unloading modesetting
[     3.094] (II) UnloadModule: "fbdev"
[     3.095] (II) Unloading fbdev
[     3.095] (II) UnloadSubModule: "fbdevhw"
[     3.095] (II) Unloading fbdevhw
[     3.095] (II) UnloadModule: "vesa"
[     3.095] (II) Unloading vesa
[     3.095] (--) Depth 24 pixmap format is 32 bpp
[     3.096] (II) NOUVEAU(0): Opened GPU channel 0
[     3.102] (II) NOUVEAU(0): [DRI2] Setup complete
[     3.102] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[     3.102] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[     3.103] (II) EXA(0): Driver allocated offscreen pixmaps
[     3.103] (II) EXA(0): Driver registered support for the following operations:
[     3.103] (II)         Solid
[     3.103] (II)         Copy
[     3.103] (II)         Composite (RENDER acceleration)
[     3.103] (II)         UploadToScreen
[     3.103] (II)         DownloadFromScreen
[     3.103] (==) NOUVEAU(0): Backing store enabled
[     3.103] (==) NOUVEAU(0): Silken mouse enabled
[     3.103] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[     3.104] (II) NOUVEAU(0): [XvMC] Extension initialized.
[     3.104] (==) NOUVEAU(0): DPMS enabled
[     3.104] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     3.104] (--) RandR disabled
[     3.108] (II) SELinux: Disabled on system
[     3.169] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     3.169] (II) AIGLX: enabled GLX_ARB_create_context
[     3.169] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     3.169] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[     3.169] (II) AIGLX: enabled GLX_INTEL_swap_event
[     3.169] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     3.169] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[     3.169] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[     3.169] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     3.169] (II) AIGLX: Loaded and initialized nouveau
[     3.169] (II) GLX: Initialized DRI2 GL provider for screen 0
[     3.172] (II) NOUVEAU(0): NVEnterVT is called.
[     3.193] (II) NOUVEAU(0): Setting screen physical size to 910 x 381
[     3.193] resize called 3440 1440
[     3.200] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     3.202] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     3.202] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.202] (II) LoadModule: "evdev"
[     3.202] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     3.203] (II) Module evdev: vendor="X.Org Foundation"
[     3.203]     compiled for 1.15.0, module version = 2.8.2
[     3.203]     Module class: X.Org XInput Driver
[     3.203]     ABI class: X.Org XInput driver, version 20.0
[     3.203] (II) Using input driver 'evdev' for 'Power Button'
[     3.203] (**) Power Button: always reports core events
[     3.203] (**) evdev: Power Button: Device: "/dev/input/event1"
[     3.203] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.203] (--) evdev: Power Button: Found keys
[     3.203] (II) evdev: Power Button: Configuring as keyboard
[     3.203] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     3.203] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     3.203] (**) Option "xkb_rules" "evdev"
[     3.203] (**) Option "xkb_model" "pc105"
[     3.203] (**) Option "xkb_layout" "us"
[     3.203] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     3.203] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.203] (II) Using input driver 'evdev' for 'Power Button'
[     3.203] (**) Power Button: always reports core events
[     3.203] (**) evdev: Power Button: Device: "/dev/input/event0"
[     3.203] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.203] (--) evdev: Power Button: Found keys
[     3.203] (II) evdev: Power Button: Configuring as keyboard
[     3.203] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     3.203] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     3.203] (**) Option "xkb_rules" "evdev"
[     3.203] (**) Option "xkb_model" "pc105"
[     3.203] (**) Option "xkb_layout" "us"
[     3.203] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
[     3.203] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     3.203] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event11)
[     3.203] (II) No input driver specified, ignoring this device.
[     3.203] (II) This device may have been added with another device file.
[     3.204] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event12)
[     3.204] (II) No input driver specified, ignoring this device.
[     3.204] (II) This device may have been added with another device file.
[     3.204] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event13)
[     3.204] (II) No input driver specified, ignoring this device.
[     3.204] (II) This device may have been added with another device file.
[     3.204] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event14)
[     3.204] (II) No input driver specified, ignoring this device.
[     3.204] (II) This device may have been added with another device file.
[     3.204] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event7)
[     3.204] (II) No input driver specified, ignoring this device.
[     3.204] (II) This device may have been added with another device file.
[     3.204] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event8)
[     3.204] (II) No input driver specified, ignoring this device.
[     3.204] (II) This device may have been added with another device file.
[     3.204] (II) config/udev: Adding input device HDA Intel PCH Line Out Side (/dev/input/event9)
[     3.204] (II) No input driver specified, ignoring this device.
[     3.204] (II) This device may have been added with another device file.
[     3.204] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event10)
[     3.204] (II) No input driver specified, ignoring this device.
[     3.204] (II) This device may have been added with another device file.
[     3.204] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event3)
[     3.204] (II) No input driver specified, ignoring this device.
[     3.204] (II) This device may have been added with another device file.
[     3.204] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event4)
[     3.204] (II) No input driver specified, ignoring this device.
[     3.204] (II) This device may have been added with another device file.
[     3.204] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event5)
[     3.204] (II) No input driver specified, ignoring this device.
[     3.204] (II) This device may have been added with another device file.
[     3.205] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event6)
[     3.205] (II) No input driver specified, ignoring this device.
[     3.205] (II) This device may have been added with another device file.
[     3.205] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event2)
[     3.205] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     3.205] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     3.205] (**) Eee PC WMI hotkeys: always reports core events
[     3.205] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event2"
[     3.205] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     3.205] (--) evdev: Eee PC WMI hotkeys: Found keys
[     3.205] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     3.205] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input5/event2"
[     3.205] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 8)
[     3.205] (**) Option "xkb_rules" "evdev"
[     3.205] (**) Option "xkb_model" "pc105"
[     3.205] (**) Option "xkb_layout" "us"
[    43.555] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/mouse0)
[    43.555] (II) No input driver specified, ignoring this device.
[    43.555] (II) This device may have been added with another device file.
[    43.555] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/event15)
[    43.555] (**) Logitech Unifying Device. Wireless PID:101a: Applying InputClass "evdev pointer catchall"
[    43.555] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:101a'
[    43.555] (**) Logitech Unifying Device. Wireless PID:101a: always reports core events
[    43.555] (**) evdev: Logitech Unifying Device. Wireless PID:101a: Device: "/dev/input/event15"
[    43.555] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Vendor 0x46d Product 0xc52b
[    43.555] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found 20 mouse buttons
[    43.555] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found scroll wheel(s)
[    43.555] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found relative axes
[    43.555] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found x and y relative axes
[    43.555] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Configuring as mouse
[    43.555] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Adding scrollwheel support
[    43.555] (**) evdev: Logitech Unifying Device. Wireless PID:101a: YAxisMapping: buttons 4 and 5
[    43.555] (**) evdev: Logitech Unifying Device. Wireless PID:101a: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    43.555] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.2/0003:046D:C52B.0003/0003:046D:C52B.0004/input/input18/event15"
[    43.555] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:101a" (type: MOUSE, id 9)
[    43.555] (II) evdev: Logitech Unifying Device. Wireless PID:101a: initialized for relative axes.
[    43.555] (**) Logitech Unifying Device. Wireless PID:101a: (accel) keeping acceleration scheme 1
[    43.555] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration profile 0
[    43.555] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration factor: 2.000
[    43.555] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration threshold: 4
[    43.689] (II) config/udev: Adding input device Topre Corporation HHKB Professional (/dev/input/event16)
[    43.689] (**) Topre Corporation HHKB Professional: Applying InputClass "evdev keyboard catchall"
[    43.689] (II) Using input driver 'evdev' for 'Topre Corporation HHKB Professional'
[    43.689] (**) Topre Corporation HHKB Professional: always reports core events
[    43.689] (**) evdev: Topre Corporation HHKB Professional: Device: "/dev/input/event16"
[    43.689] (--) evdev: Topre Corporation HHKB Professional: Vendor 0x853 Product 0x100
[    43.689] (--) evdev: Topre Corporation HHKB Professional: Found keys
[    43.689] (II) evdev: Topre Corporation HHKB Professional: Configuring as keyboard
[    43.689] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-9/3-9.1/3-9.1:1.0/0003:0853:0100.0005/input/input19/event16"
[    43.689] (II) XINPUT: Adding extended input device "Topre Corporation HHKB Professional" (type: KEYBOARD, id 10)
[    43.689] (**) Option "xkb_rules" "evdev"
[    43.689] (**) Option "xkb_model" "pc105"
[    43.689] (**) Option "xkb_layout" "us"
[    56.018] (II) NOUVEAU(0): EDID vendor "GSM", prod id 23266
[    56.018] (II) NOUVEAU(0): Using EDID range info for horizontal sync
[    56.018] (II) NOUVEAU(0): Using EDID range info for vertical refresh
[    56.018] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    56.018] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  319.75  3440 3488 3520 3600  1440 1443 1453 1481 +hsync -vsync (88.8 kHz eP)
[    56.018] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  265.25  3440 3488 3520 3600  1440 1443 1453 1474 +hsync -vsync (73.7 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  157.75  3440 3488 3520 3600  1440 1443 1453 1461 +hsync -vsync (43.8 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "2560x1080"x0.0  185.58  2560 2624 2688 2784  1080 1083 1093 1111 -hsync -vsync (66.7 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    56.018] (II) NOUVEAU(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    56.257] resize called 3440 1440
[    59.898] (II) NOUVEAU(0): EDID vendor "GSM", prod id 23266
[    59.898] (II) NOUVEAU(0): Using hsync ranges from config file
[    59.898] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    59.898] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    59.898] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  319.75  3440 3488 3520 3600  1440 1443 1453 1481 +hsync -vsync (88.8 kHz eP)
[    59.898] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  265.25  3440 3488 3520 3600  1440 1443 1453 1474 +hsync -vsync (73.7 kHz e)
[    59.898] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  157.75  3440 3488 3520 3600  1440 1443 1453 1461 +hsync -vsync (43.8 kHz e)
[    59.898] (II) NOUVEAU(0): Modeline "2560x1080"x0.0  185.58  2560 2624 2688 2784  1080 1083 1093 1111 -hsync -vsync (66.7 kHz e)
[    59.898] (II) NOUVEAU(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    59.898] (II) NOUVEAU(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    59.898] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    59.899] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    59.899] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    59.899] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    59.899] (II) NOUVEAU(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    59.899] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    59.899] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    59.899] (II) NOUVEAU(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    59.899] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    59.899] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    59.899] (II) NOUVEAU(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    59.899] (II) NOUVEAU(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    59.899] (II) NOUVEAU(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    60.070] (II) NOUVEAU(0): EDID vendor "GSM", prod id 23266
[    60.070] (II) NOUVEAU(0): Using hsync ranges from config file
[    60.070] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    60.070] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    60.070] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  319.75  3440 3488 3520 3600  1440 1443 1453 1481 +hsync -vsync (88.8 kHz eP)
[    60.070] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  265.25  3440 3488 3520 3600  1440 1443 1453 1474 +hsync -vsync (73.7 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  157.75  3440 3488 3520 3600  1440 1443 1453 1461 +hsync -vsync (43.8 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "2560x1080"x0.0  185.58  2560 2624 2688 2784  1080 1083 1093 1111 -hsync -vsync (66.7 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    60.070] (II) NOUVEAU(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    60.140] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    60.184] (II) XKB: reuse xkmfile /var/lib/xkb/server-1908D3BB0224FA577B58A32F49D8B4107F7BAFFD.xkm
[    61.241] (II) NOUVEAU(0): EDID vendor "GSM", prod id 23266
[    61.241] (II) NOUVEAU(0): Using hsync ranges from config file
[    61.241] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    61.241] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    61.241] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  319.75  3440 3488 3520 3600  1440 1443 1453 1481 +hsync -vsync (88.8 kHz eP)
[    61.241] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  265.25  3440 3488 3520 3600  1440 1443 1453 1474 +hsync -vsync (73.7 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  157.75  3440 3488 3520 3600  1440 1443 1453 1461 +hsync -vsync (43.8 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "2560x1080"x0.0  185.58  2560 2624 2688 2784  1080 1083 1093 1111 -hsync -vsync (66.7 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    61.241] (II) NOUVEAU(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    61.290] (II) NOUVEAU(0): EDID vendor "GSM", prod id 23266
[    61.290] (II) NOUVEAU(0): Using hsync ranges from config file
[    61.290] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    61.290] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    61.290] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  319.75  3440 3488 3520 3600  1440 1443 1453 1481 +hsync -vsync (88.8 kHz eP)
[    61.290] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  265.25  3440 3488 3520 3600  1440 1443 1453 1474 +hsync -vsync (73.7 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  157.75  3440 3488 3520 3600  1440 1443 1453 1461 +hsync -vsync (43.8 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "2560x1080"x0.0  185.58  2560 2624 2688 2784  1080 1083 1093 1111 -hsync -vsync (66.7 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    61.290] (II) NOUVEAU(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    61.404] (II) XKB: reuse xkmfile /var/lib/xkb/server-1908D3BB0224FA577B58A32F49D8B4107F7BAFFD.xkm
[    61.405] (II) XKB: reuse xkmfile /var/lib/xkb/server-1908D3BB0224FA577B58A32F49D8B4107F7BAFFD.xkm
[    61.406] (II) XKB: reuse xkmfile /var/lib/xkb/server-1908D3BB0224FA577B58A32F49D8B4107F7BAFFD.xkm
[    61.407] (II) XKB: reuse xkmfile /var/lib/xkb/server-1908D3BB0224FA577B58A32F49D8B4107F7BAFFD.xkm
[    61.409] (II) XKB: reuse xkmfile /var/lib/xkb/server-1908D3BB0224FA577B58A32F49D8B4107F7BAFFD.xkm
[    61.410] (II) XKB: reuse xkmfile /var/lib/xkb/server-1908D3BB0224FA577B58A32F49D8B4107F7BAFFD.xkm
[    80.679] (II) NOUVEAU(0): EDID vendor "GSM", prod id 23266
[    80.679] (II) NOUVEAU(0): Using hsync ranges from config file
[    80.679] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    80.679] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    80.679] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  319.75  3440 3488 3520 3600  1440 1443 1453 1481 +hsync -vsync (88.8 kHz eP)
[    80.679] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  265.25  3440 3488 3520 3600  1440 1443 1453 1474 +hsync -vsync (73.7 kHz e)
[    80.679] (II) NOUVEAU(0): Modeline "3440x1440"x0.0  157.75  3440 3488 3520 3600  1440 1443 1453 1461 +hsync -vsync (43.8 kHz e)
[    80.679] (II) NOUVEAU(0): Modeline "2560x1080"x0.0  185.58  2560 2624 2688 2784  1080 1083 1093 1111 -hsync -vsync (66.7 kHz e)
[    80.679] (II) NOUVEAU(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    80.679] (II) NOUVEAU(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    80.679] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    80.679] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    80.680] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    80.680] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    80.680] (II) NOUVEAU(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    80.680] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    80.680] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    80.680] (II) NOUVEAU(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    80.680] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    80.680] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    80.680] (II) NOUVEAU(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    80.680] (II) NOUVEAU(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    80.680] (II) NOUVEAU(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)

```

---

### Post by ajgreeny on 2015-08-31
Both wireless by the look of it.  Do you have any USB cable connected keyboard and mouse you can try just to see of the delay disappears when using them, because it looks as if the problem is a delay at this point, ie, adding the Logitech Unifying Device, but only for the mouse, but which may be the USB receiver for both items.
```
[     3.205] (**) Option "xkb_model" "pc105"
[     3.205] (**) Option "xkb_layout" "us"
[    43.555] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/mouse0)
```

Perhaps the receiver used by the mouse and keyboard is badly connected in its USB socket, if that is the way they connect.  Try it in a different USB socket.

---

