---
title: "Ubuntu loads black / blank screen"
date: 2014-03-02
forum: General Help
---

### Post by leo_mancini on 2014-03-02
Hi all,

Ubuntu loads a blank screen when loading the kernel 3.11.0-17-generic one, using Ubuntu 13.10.

The following is a xorg log and a lshw command.

Any help would be greatly appreciated.

Thank you.



>  [    24.202] X.Org X Server 1.14.5
Release Date: 2013-12-12
[    24.202] X Protocol Version 11, Revision 0
[    24.202] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    24.202] Current Operating System: Linux paulspc 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:52:43 UTC 2014 x86_64
[    24.202] Kernel command line: BOOT_IMAGE=/vmlinuz-3.11.0-17-generic root=/dev/mapper/ubuntu-root ro quiet splash
[    24.202] Build Date: 17 December 2013  10:06:15AM
[    24.202] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    24.202] Current version of pixman: 0.30.2
[    24.202]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    24.202] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.202] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar  1 21:56:54 2014
[    24.202] (==) Using config file: "/etc/X11/xorg.conf"
[    24.202] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.203] (==) ServerLayout "Layout0"
[    24.203] (**) |-->Screen "Screen0" (0)
[    24.203] (**) |   |-->Monitor "Monitor0"
[    24.203] (**) |   |-->Device "Device0"
[    24.203] (**) |-->Input Device "Keyboard0"
[    24.203] (**) |-->Input Device "Mouse0"
[    24.203] (==) Automatically adding devices
[    24.203] (==) Automatically enabling devices
[    24.203] (==) Automatically adding GPU devices
[    24.203] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.203]     Entry deleted from font path.
[    24.203] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.203]     Entry deleted from font path.
[    24.203] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.203]     Entry deleted from font path.
[    24.203] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.203]     Entry deleted from font path.
[    24.203] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.203]     Entry deleted from font path.
[    24.203] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    24.203] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.203] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    24.203] (WW) Disabling Keyboard0
[    24.203] (WW) Disabling Mouse0
[    24.203] (II) Loader magic: 0x7f659b023d20
[    24.203] (II) Module ABI versions:
[    24.203]     X.Org ANSI C Emulation: 0.4
[    24.203]     X.Org Video Driver: 14.1
[    24.203]     X.Org XInput driver : 19.1
[    24.203]     X.Org Server Extension : 7.0
[    24.205] (--) PCI:*(0:2:0:0) 10de:0fc6:1458:3555 rev 161, Mem @ 0xd0000000/16777216, 0xb0000000/268435456, 0xc0000000/33554432, I/O @ 0x0000a000/128, BIOS @ 0x????????/524288
[    24.205] (II) Open ACPI successful (/var/run/acpid.socket)
[    24.205] Initializing built-in extension Generic Event Extension
[    24.205] Initializing built-in extension SHAPE
[    24.205] Initializing built-in extension MIT-SHM
[    24.205] Initializing built-in extension XInputExtension
[    24.205] Initializing built-in extension XTEST
[    24.205] Initializing built-in extension BIG-REQUESTS
[    24.205] Initializing built-in extension SYNC
[    24.205] Initializing built-in extension XKEYBOARD
[    24.205] Initializing built-in extension XC-MISC
[    24.205] Initializing built-in extension SECURITY
[    24.205] Initializing built-in extension XINERAMA
[    24.205] Initializing built-in extension XFIXES
[    24.205] Initializing built-in extension RENDER
[    24.205] Initializing built-in extension RANDR
[    24.205] Initializing built-in extension COMPOSITE
[    24.205] Initializing built-in extension DAMAGE
[    24.205] Initializing built-in extension MIT-SCREEN-SAVER
[    24.205] Initializing built-in extension DOUBLE-BUFFER
[    24.205] Initializing built-in extension RECORD
[    24.205] Initializing built-in extension DPMS
[    24.205] Initializing built-in extension X-Resource
[    24.205] Initializing built-in extension XVideo
[    24.205] Initializing built-in extension XVideo-MotionCompensation
[    24.205] Initializing built-in extension SELinux
[    24.205] Initializing built-in extension XFree86-VidModeExtension
[    24.205] Initializing built-in extension XFree86-DGA
[    24.205] Initializing built-in extension XFree86-DRI
[    24.205] Initializing built-in extension DRI2
[    24.205] (II) "glx" will be loaded by default.
[    24.205] (WW) "xmir" is not to be loaded by default. Skipping.
[    24.205] (II) LoadModule: "dri2"
[    24.206] (II) Module "dri2" already built-in
[    24.206] (II) LoadModule: "glamoregl"
[    24.214] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    24.250] (II) Module glamoregl: vendor="X.Org Foundation"
[    24.250]     compiled for 1.14.3, module version = 0.5.1
[    24.250]     ABI class: X.Org ANSI C Emulation, version 0.4
[    24.250] (II) LoadModule: "glx"
[    24.250] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    24.344] (II) Module glx: vendor="NVIDIA Corporation"
[    24.344]     compiled for 4.0.2, module version = 1.0.0
[    24.344]     Module class: X.Org Server Extension
[    24.344] (II) NVIDIA GLX Module  319.32  Wed Jun 19 14:55:38 PDT 2013
[    24.344] Loading extension GLX
[    24.344] (II) LoadModule: "nvidia"
[    24.344] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    24.355] (II) Module nvidia: vendor="NVIDIA Corporation"
[    24.355]     compiled for 4.0.2, module version = 1.0.0
[    24.355]     Module class: X.Org Video Driver
[    24.361] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    24.361] (EE) NVIDIA:     system's kernel log for additional error messages.
[    24.361] (II) UnloadModule: "nvidia"
[    24.361] (II) Unloading nvidia
[    24.362] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    24.362] (==) Matched nvidia as autoconfigured driver 0
[    24.362] (==) Matched nouveau as autoconfigured driver 1
[    24.362] (==) Matched vesa as autoconfigured driver 2
[    24.362] (==) Matched modesetting as autoconfigured driver 3
[    24.362] (==) Matched fbdev as autoconfigured driver 4
[    24.362] (==) Assigned the driver to the xf86ConfigLayout
[    24.362] (II) LoadModule: "nvidia"
[    24.362] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    24.374] (II) Module nvidia: vendor="NVIDIA Corporation"
[    24.374]     compiled for 4.0.2, module version = 1.0.0
[    24.374]     Module class: X.Org Video Driver
[    24.381] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    24.382] (EE) NVIDIA:     system's kernel log for additional error messages.
[    24.382] (II) UnloadModule: "nvidia"
[    24.382] (II) Unloading nvidia
[    24.382] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    24.382] (II) LoadModule: "nouveau"
[    24.392] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    24.503] (II) Module nouveau: vendor="X.Org Foundation"
[    24.503]     compiled for 1.14.2.901, module version = 1.0.9
[    24.503]     Module class: X.Org Video Driver
[    24.503]     ABI class: X.Org Video Driver, version 14.1
[    24.503] (II) LoadModule: "vesa"
[    24.504] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.528] (II) Module vesa: vendor="X.Org Foundation"
[    24.529]     compiled for 1.14.1, module version = 2.3.2
[    24.529]     Module class: X.Org Video Driver
[    24.529]     ABI class: X.Org Video Driver, version 14.1
[    24.529] (II) LoadModule: "modesetting"
[    24.529] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    24.582] (II) Module modesetting: vendor="X.Org Foundation"
[    24.582]     compiled for 1.14.1, module version = 0.8.0
[    24.582]     Module class: X.Org Video Driver
[    24.582]     ABI class: X.Org Video Driver, version 14.1
[    24.582] (II) LoadModule: "fbdev"
[    24.582] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.604] (II) Module fbdev: vendor="X.Org Foundation"
[    24.604]     compiled for 1.14.1, module version = 0.4.3
[    24.604]     Module class: X.Org Video Driver
[    24.604]     ABI class: X.Org Video Driver, version 14.1
[    24.604] (II) NOUVEAU driver Date:   Wed Jul 31 10:51:03 2013 +1000
[    24.604] (II) NOUVEAU driver for NVIDIA chipset families :
[    24.604]     RIVA TNT        (NV04)
[    24.604]     RIVA TNT2       (NV05)
[    24.604]     GeForce 256     (NV10)
[    24.604]     GeForce 2       (NV11, NV15)
[    24.604]     GeForce 4MX     (NV17, NV18)
[    24.604]     GeForce 3       (NV20)
[    24.604]     GeForce 4Ti     (NV25, NV28)
[    24.604]     GeForce FX      (NV3x)
[    24.604]     GeForce 6       (NV4x)
[    24.604]     GeForce 7       (G7x)
[    24.605]     GeForce 8       (G8x)
[    24.605]     GeForce GTX 200 (NVA0)
[    24.605]     GeForce GTX 400 (NVC0)
[    24.605] (II) VESA: driver for VESA chipsets: vesa
[    24.605] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    24.605] (II) FBDEV: driver for framebuffer: fbdev
[    24.605] (++) using VT number 7


[    24.606] (EE) [drm] KMS not enabled
[    24.607] (WW) Falling back to old probe method for modesetting
[    24.607] (EE) open /dev/dri/card0: No such file or directory
[    24.607] (WW) Falling back to old probe method for fbdev
[    24.607] (II) Loading sub module "fbdevhw"
[    24.607] (II) LoadModule: "fbdevhw"
[    24.607] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.635] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.635]     compiled for 1.14.5, module version = 0.0.2
[    24.635]     ABI class: X.Org Video Driver, version 14.1
[    24.635] (EE) open /dev/fb0: No such file or directory
[    24.636] (II) Loading sub module "vbe"
[    24.636] (II) LoadModule: "vbe"
[    24.636] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    24.694] (II) Module vbe: vendor="X.Org Foundation"
[    24.694]     compiled for 1.14.5, module version = 1.1.0
[    24.694]     ABI class: X.Org Video Driver, version 14.1
[    24.694] (II) Loading sub module "int10"
[    24.694] (II) LoadModule: "int10"
[    24.695] (II) Loading /usr/lib/xorg/modules/libint10.so
[    24.723] (II) Module int10: vendor="X.Org Foundation"
[    24.724]     compiled for 1.14.5, module version = 1.0.0
[    24.724]     ABI class: X.Org Video Driver, version 14.1
[    24.724] (II) VESA(0): initializing int10
[    24.727] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    24.819] (II) VESA(0): VESA BIOS detected
[    24.819] (II) VESA(0): VESA VBE Version 3.0
[    24.819] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    24.819] (II) VESA(0): VESA VBE OEM: NVIDIA
[    24.819] (II) VESA(0): VESA VBE OEM Software Rev: 128.7
[    24.819] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    24.819] (II) VESA(0): VESA VBE OEM Product: GK107 Board - 20100004
[    24.819] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev
[    25.026] (**) VESA(0): Depth 24, (--) framebuffer bpp 32
[    25.026] (==) VESA(0): RGB weight 888
[    25.026] (==) VESA(0): Default visual is TrueColor
[    25.026] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    25.026] (II) Loading sub module "ddc"
[    25.026] (II) LoadModule: "ddc"
[    25.026] (II) Module "ddc" already built-in
[    25.027] (II) VESA(0): VESA VBE DDC supported
[    25.027] (II) VESA(0): VESA VBE DDC Level 2
[    25.027] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    25.070] (II) VESA(0): VESA VBE DDC read successfully
[    25.070] (II) VESA(0): Manufacturer: GSM  Model: 5663  Serial#: 316986
[    25.070] (II) VESA(0): Year: 2007  Week: 9
[    25.070] (II) VESA(0): EDID Version: 1.3
[    25.070] (II) VESA(0): Digital Display Input
[    25.070] (II) VESA(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    25.070] (II) VESA(0): Gamma: 2.20
[    25.070] (II) VESA(0): DPMS capabilities: StandBy Suspend Off
[    25.071] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    25.071] (II) VESA(0): First detailed timing is preferred mode
[    25.071] (II) VESA(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.605
[    25.071] (II) VESA(0): blueX: 0.152 blueY: 0.076   whiteX: 0.313 whiteY: 0.329
[    25.071] (II) VESA(0): Supported established timings:
[    25.071] (II) VESA(0): 720x400@70Hz
[    25.071] (II) VESA(0): 640x480@60Hz
[    25.071] (II) VESA(0): 640x480@75Hz
[    25.071] (II) VESA(0): 800x600@56Hz
[    25.071] (II) VESA(0): 800x600@60Hz
[    25.071] (II) VESA(0): 800x600@75Hz
[    25.071] (II) VESA(0): 832x624@75Hz
[    25.071] (II) VESA(0): 1024x768@60Hz
[    25.071] (II) VESA(0): 1024x768@75Hz
[    25.071] (II) VESA(0): 1280x1024@75Hz
[    25.071] (II) VESA(0): 1152x864@75Hz
[    25.071] (II) VESA(0): Manufacturer's mask: 0
[    25.071] (II) VESA(0): Supported standard timings:
[    25.071] (II) VESA(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    25.071] (II) VESA(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    25.071] (II) VESA(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    25.071] (II) VESA(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    25.071] (II) VESA(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    25.071] (II) VESA(0): Supported detailed timing:
[    25.071] (II) VESA(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
[    25.071] (II) VESA(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    25.071] (II) VESA(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    25.071] (II) VESA(0): Supported detailed timing:
[    25.071] (II) VESA(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    25.071] (II) VESA(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    25.071] (II) VESA(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    25.071] (II) VESA(0): Ranges: V min: 56 V max: 75 Hz, H min: 28 H max: 83 kHz, PixClock max 155 MHz
[    25.071] (II) VESA(0): Monitor name: L225W
[    25.071] (II) VESA(0): EDID (in hex):
[    25.071] (II) VESA(0):     00ffffffffffff001e6d63563ad60400
[    25.071] (II) VESA(0):     09110103ea2f1e78ead425a455499b27
[    25.071] (II) VESA(0):     135054a76b80950f950081808140714f
[    25.071] (II) VESA(0):     0101010101017c2e90a0601a1e403020
[    25.071] (II) VESA(0):     3600da281100001a21399030621a2740
[    25.071] (II) VESA(0):     68b03600da281100001c000000fd0038
[    25.071] (II) VESA(0):     4b1c530f000a202020202020000000fc
[    25.071] (II) VESA(0):     004c323235570a202020202020200027
[    25.071] (II) VESA(0): EDID vendor "GSM", prod id 22115
[    25.071] (II) VESA(0): Using hsync ranges from config file
[    25.071] (II) VESA(0): Using vrefresh ranges from config file
[    25.071] (II) VESA(0): Printing DDC gathered Modelines:
[    25.071] (II) VESA(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    25.071] (II) VESA(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    25.071] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    25.071] (II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    25.071] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    25.071] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    25.071] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    25.071] (II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    25.071] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    25.071] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    25.071] (II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    25.071] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    25.071] (II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    25.071] (II) VESA(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    25.071] (II) VESA(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    25.072] (II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    25.072] (II) VESA(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    25.072] (II) VESA(0): Searching for matching VESA mode(s):
[    25.074] Mode: 100 (640x400)
[    25.074]     ModeAttributes: 0x3bf
[    25.074]     WinAAttributes: 0x7
[    25.074]     WinBAttributes: 0x0
[    25.074]     WinGranularity: 64
[    25.074]     WinSize: 64
[    25.074]     WinASegment: 0xa000
[    25.074]     WinBSegment: 0x0
[    25.074]     WinFuncPtr: 0xc0007cbe
[    25.074]     BytesPerScanline: 640
[    25.074]     XResolution: 640
[    25.074]     YResolution: 400
[    25.074]     XCharSize: 8
[    25.074]     YCharSize: 16
[    25.074]     NumberOfPlanes: 1
[    25.074]     BitsPerPixel: 8
[    25.074]     NumberOfBanks: 1
[    25.074]     MemoryModel: 4
[    25.074]     BankSize: 0
[    25.074]     NumberOfImages: 14
[    25.074]     RedMaskSize: 0
[    25.074]     RedFieldPosition: 0
[    25.074]     GreenMaskSize: 0
[    25.074]     GreenFieldPosition: 0
[    25.074]     BlueMaskSize: 0
[    25.074]     BlueFieldPosition: 0
[    25.074]     RsvdMaskSize: 0
[    25.074]     RsvdFieldPosition: 0
[    25.074]     DirectColorModeInfo: 0
[    25.074]     PhysBasePtr: 0xc1000000
[    25.074]     LinBytesPerScanLine: 640
[    25.074]     BnkNumberOfImagePages: 14
[    25.074]     LinNumberOfImagePages: 14
[    25.074]     LinRedMaskSize: 0
[    25.074]     LinRedFieldPosition: 0
[    25.074]     LinGreenMaskSize: 0
[    25.074]     LinGreenFieldPosition: 0
[    25.074]     LinBlueMaskSize: 0
[    25.074]     LinBlueFieldPosition: 0
[    25.074]     LinRsvdMaskSize: 0
[    25.074]     LinRsvdFieldPosition: 0
[    25.074]     MaxPixelClock: 229500000
[    25.077] Mode: 101 (640x480)
[    25.077]     ModeAttributes: 0x3bf
[    25.077]     WinAAttributes: 0x7
[    25.077]     WinBAttributes: 0x0
[    25.077]     WinGranularity: 64
[    25.077]     WinSize: 64
[    25.077]     WinASegment: 0xa000
[    25.077]     WinBSegment: 0x0
[    25.077]     WinFuncPtr: 0xc0007cbe
[    25.077]     BytesPerScanline: 640
[    25.077]     XResolution: 640
[    25.077]     YResolution: 480
[    25.077]     XCharSize: 8
[    25.077]     YCharSize: 16
[    25.077]     NumberOfPlanes: 1
[    25.077]     BitsPerPixel: 8
[    25.077]     NumberOfBanks: 1
[    25.077]     MemoryModel: 4
[    25.077]     BankSize: 0
[    25.077]     NumberOfImages: 10
[    25.077]     RedMaskSize: 0
[    25.077]     RedFieldPosition: 0
[    25.077]     GreenMaskSize: 0
[    25.077]     GreenFieldPosition: 0
[    25.077]     BlueMaskSize: 0
[    25.077]     BlueFieldPosition: 0
[    25.077]     RsvdMaskSize: 0
[    25.077]     RsvdFieldPosition: 0
[    25.077]     DirectColorModeInfo: 0
[    25.077]     PhysBasePtr: 0xc1000000
[    25.077]     LinBytesPerScanLine: 640
[    25.077]     BnkNumberOfImagePages: 10
[    25.077]     LinNumberOfImagePages: 10
[    25.077]     LinRedMaskSize: 0
[    25.077]     LinRedFieldPosition: 0
[    25.077]     LinGreenMaskSize: 0
[    25.077]     LinGreenFieldPosition: 0
[    25.077]     LinBlueMaskSize: 0
[    25.077]     LinBlueFieldPosition: 0
[    25.077]     LinRsvdMaskSize: 0
[    25.077]     LinRsvdFieldPosition: 0
[    25.077]     MaxPixelClock: 229500000
[    25.080] Mode: 102 (800x600)
[    25.080]     ModeAttributes: 0x33f
[    25.080]     WinAAttributes: 0x7
[    25.080]     WinBAttributes: 0x0
[    25.080]     WinGranularity: 64
[    25.080]     WinSize: 64
[    25.080]     WinASegment: 0xa000
[    25.080]     WinBSegment: 0x0
[    25.080]     WinFuncPtr: 0xc0007cbe
[    25.080]     BytesPerScanline: 100
[    25.080]     XResolution: 800
[    25.080]     YResolution: 600
[    25.080]     XCharSize: 8
[    25.080]     YCharSize: 16
[    25.080]     NumberOfPlanes: 4
[    25.080]     BitsPerPixel: 4
[    25.080]     NumberOfBanks: 1
[    25.080]     MemoryModel: 3
[    25.080]     BankSize: 0
[    25.080]     NumberOfImages: 2
[    25.080]     RedMaskSize: 0
[    25.080]     RedFieldPosition: 0
[    25.080]     GreenMaskSize: 0
[    25.080]     GreenFieldPosition: 0
[    25.080]     BlueMaskSize: 0
[    25.080]     BlueFieldPosition: 0
[    25.080]     RsvdMaskSize: 0
[    25.080]     RsvdFieldPosition: 0
[    25.080]     DirectColorModeInfo: 0
[    25.080]     PhysBasePtr: 0x0
[    25.080]     LinBytesPerScanLine: 100
[    25.080]     BnkNumberOfImagePages: 2
[    25.080]     LinNumberOfImagePages: 2
[    25.080]     LinRedMaskSize: 0
[    25.080]     LinRedFieldPosition: 0
[    25.080]     LinGreenMaskSize: 0
[    25.080]     LinGreenFieldPosition: 0
[    25.080]     LinBlueMaskSize: 0
[    25.080]     LinBlueFieldPosition: 0
[    25.080]     LinRsvdMaskSize: 0
[    25.080]     LinRsvdFieldPosition: 0
[    25.080]     MaxPixelClock: 108500000
[    25.083] Mode: 103 (800x600)
[    25.083]     ModeAttributes: 0x3bf
[    25.083]     WinAAttributes: 0x7
[    25.083]     WinBAttributes: 0x0
[    25.083]     WinGranularity: 64
[    25.083]     WinSize: 64
[    25.083]     WinASegment: 0xa000
[    25.083]     WinBSegment: 0x0
[    25.083]     WinFuncPtr: 0xc0007cbe
[    25.083]     BytesPerScanline: 800
[    25.083]     XResolution: 800
[    25.083]     YResolution: 600
[    25.083]     XCharSize: 8
[    25.083]     YCharSize: 16
[    25.083]     NumberOfPlanes: 1
[    25.083]     BitsPerPixel: 8
[    25.083]     NumberOfBanks: 1
[    25.083]     MemoryModel: 4
[    25.083]     BankSize: 0
[    25.083]     NumberOfImages: 6
[    25.083]     RedMaskSize: 0
[    25.083]     RedFieldPosition: 0
[    25.083]     GreenMaskSize: 0
[    25.083]     GreenFieldPosition: 0
[    25.083]     BlueMaskSize: 0
[    25.083]     BlueFieldPosition: 0
[    25.083]     RsvdMaskSize: 0
[    25.083]     RsvdFieldPosition: 0
[    25.083]     DirectColorModeInfo: 0
[    25.083]     PhysBasePtr: 0xc1000000
[    25.083]     LinBytesPerScanLine: 800
[    25.083]     BnkNumberOfImagePages: 6
[    25.083]     LinNumberOfImagePages: 6
[    25.083]     LinRedMaskSize: 0
[    25.083]     LinRedFieldPosition: 0
[    25.083]     LinGreenMaskSize: 0
[    25.083]     LinGreenFieldPosition: 0
[    25.083]     LinBlueMaskSize: 0
[    25.083]     LinBlueFieldPosition: 0
[    25.083]     LinRsvdMaskSize: 0
[    25.083]     LinRsvdFieldPosition: 0
[    25.083]     MaxPixelClock: 229500000
[    25.086] Mode: 104 (1024x768)
[    25.086]     ModeAttributes: 0x33f
[    25.086]     WinAAttributes: 0x7
[    25.086]     WinBAttributes: 0x0
[    25.086]     WinGranularity: 64
[    25.086]     WinSize: 64
[    25.086]     WinASegment: 0xa000
[    25.086]     WinBSegment: 0x0
[    25.086]     WinFuncPtr: 0xc0007cbe
[    25.086]     BytesPerScanline: 128
[    25.086]     XResolution: 1024
[    25.086]     YResolution: 768
[    25.086]     XCharSize: 8
[    25.086]     YCharSize: 16
[    25.086]     NumberOfPlanes: 4
[    25.086]     BitsPerPixel: 4
[    25.086]     NumberOfBanks: 1
[    25.086]     MemoryModel: 3
[    25.086]     BankSize: 0
[    25.086]     NumberOfImages: 1
[    25.086]     RedMaskSize: 0
[    25.086]     RedFieldPosition: 0
[    25.086]     GreenMaskSize: 0
[    25.086]     GreenFieldPosition: 0
[    25.086]     BlueMaskSize: 0
[    25.086]     BlueFieldPosition: 0
[    25.086]     RsvdMaskSize: 0
[    25.086]     RsvdFieldPosition: 0
[    25.086]     DirectColorModeInfo: 0
[    25.086]     PhysBasePtr: 0x0
[    25.086]     LinBytesPerScanLine: 128
[    25.086]     BnkNumberOfImagePages: 1
[    25.086]     LinNumberOfImagePages: 1
[    25.086]     LinRedMaskSize: 0
[    25.086]     LinRedFieldPosition: 0
[    25.086]     LinGreenMaskSize: 0
[    25.086]     LinGreenFieldPosition: 0
[    25.086]     LinBlueMaskSize: 0
[    25.086]     LinBlueFieldPosition: 0
[    25.086]     LinRsvdMaskSize: 0
[    25.086]     LinRsvdFieldPosition: 0
[    25.086]     MaxPixelClock: 108500000
[    25.088] Mode: 105 (1024x768)
[    25.088]     ModeAttributes: 0x3bf
[    25.088]     WinAAttributes: 0x7
[    25.088]     WinBAttributes: 0x0
[    25.088]     WinGranularity: 64
[    25.088]     WinSize: 64
[    25.088]     WinASegment: 0xa000
[    25.088]     WinBSegment: 0x0
[    25.088]     WinFuncPtr: 0xc0007cbe
[    25.089]     BytesPerScanline: 1024
[    25.089]     XResolution: 1024
[    25.089]     YResolution: 768
[    25.089]     XCharSize: 8
[    25.089]     YCharSize: 16
[    25.089]     NumberOfPlanes: 1
[    25.089]     BitsPerPixel: 8
[    25.089]     NumberOfBanks: 1
[    25.089]     MemoryModel: 4
[    25.089]     BankSize: 0
[    25.089]     NumberOfImages: 3
[    25.089]     RedMaskSize: 0
[    25.089]     RedFieldPosition: 0
[    25.089]     GreenMaskSize: 0
[    25.089]     GreenFieldPosition: 0
[    25.089]     BlueMaskSize: 0
[    25.089]     BlueFieldPosition: 0
[    25.089]     RsvdMaskSize: 0
[    25.089]     RsvdFieldPosition: 0
[    25.089]     DirectColorModeInfo: 0
[    25.089]     PhysBasePtr: 0xc1000000
[    25.089]     LinBytesPerScanLine: 1024
[    25.089]     BnkNumberOfImagePages: 3
[    25.089]     LinNumberOfImagePages: 3
[    25.089]     LinRedMaskSize: 0
[    25.089]     LinRedFieldPosition: 0
[    25.089]     LinGreenMaskSize: 0
[    25.089]     LinGreenFieldPosition: 0
[    25.089]     LinBlueMaskSize: 0
[    25.089]     LinBlueFieldPosition: 0
[    25.089]     LinRsvdMaskSize: 0
[    25.089]     LinRsvdFieldPosition: 0
[    25.089]     MaxPixelClock: 229500000
[    25.091] Mode: 106 (1280x1024)
[    25.091]     ModeAttributes: 0x33f
[    25.091]     WinAAttributes: 0x7
[    25.091]     WinBAttributes: 0x0
[    25.091]     WinGranularity: 64
[    25.091]     WinSize: 64
[    25.091]     WinASegment: 0xa000
[    25.091]     WinBSegment: 0x0
[    25.091]     WinFuncPtr: 0xc0007cbe
[    25.091]     BytesPerScanline: 160
[    25.091]     XResolution: 1280
[    25.091]     YResolution: 1024
[    25.091]     XCharSize: 8
[    25.091]     YCharSize: 16
[    25.091]     NumberOfPlanes: 4
[    25.091]     BitsPerPixel: 4
[    25.091]     NumberOfBanks: 1
[    25.091]     MemoryModel: 3
[    25.091]     BankSize: 0
[    25.091]     NumberOfImages: 1
[    25.091]     RedMaskSize: 0
[    25.091]     RedFieldPosition: 0
[    25.091]     GreenMaskSize: 0
[    25.091]     GreenFieldPosition: 0
[    25.091]     BlueMaskSize: 0
[    25.092]     BlueFieldPosition: 0
[    25.092]     RsvdMaskSize: 0
[    25.092]     RsvdFieldPosition: 0
[    25.092]     DirectColorModeInfo: 0
[    25.092]     PhysBasePtr: 0x0
[    25.092]     LinBytesPerScanLine: 160
[    25.092]     BnkNumberOfImagePages: 1
[    25.092]     LinNumberOfImagePages: 1
[    25.092]     LinRedMaskSize: 0
[    25.092]     LinRedFieldPosition: 0
[    25.092]     LinGreenMaskSize: 0
[    25.092]     LinGreenFieldPosition: 0
[    25.092]     LinBlueMaskSize: 0
[    25.092]     LinBlueFieldPosition: 0
[    25.092]     LinRsvdMaskSize: 0
[    25.092]     LinRsvdFieldPosition: 0
[    25.092]     MaxPixelClock: 108500000
[    25.094] Mode: 107 (1280x1024)
[    25.094]     ModeAttributes: 0x3bf
[    25.094]     WinAAttributes: 0x7
[    25.094]     WinBAttributes: 0x0
[    25.094]     WinGranularity: 64
[    25.094]     WinSize: 64
[    25.094]     WinASegment: 0xa000
[    25.094]     WinBSegment: 0x0
[    25.094]     WinFuncPtr: 0xc0007cbe
[    25.094]     BytesPerScanline: 1280
[    25.094]     XResolution: 1280
[    25.094]     YResolution: 1024
[    25.094]     XCharSize: 8
[    25.094]     YCharSize: 16
[    25.094]     NumberOfPlanes: 1
[    25.094]     BitsPerPixel: 8
[    25.094]     NumberOfBanks: 1
[    25.094]     MemoryModel: 4
[    25.094]     BankSize: 0
[    25.094]     NumberOfImages: 1
[    25.094]     RedMaskSize: 0
[    25.094]     RedFieldPosition: 0
[    25.094]     GreenMaskSize: 0
[    25.094]     GreenFieldPosition: 0
[    25.094]     BlueMaskSize: 0
[    25.094]     BlueFieldPosition: 0
[    25.094]     RsvdMaskSize: 0
[    25.094]     RsvdFieldPosition: 0
[    25.094]     DirectColorModeInfo: 0
[    25.094]     PhysBasePtr: 0xc1000000
[    25.094]     LinBytesPerScanLine: 1280
[    25.094]     BnkNumberOfImagePages: 1
[    25.094]     LinNumberOfImagePages: 1
[    25.095]     LinRedMaskSize: 0
[    25.095]     LinRedFieldPosition: 0
[    25.095]     LinGreenMaskSize: 0
[    25.095]     LinGreenFieldPosition: 0
[    25.095]     LinBlueMaskSize: 0
[    25.095]     LinBlueFieldPosition: 0
[    25.095]     LinRsvdMaskSize: 0
[    25.095]     LinRsvdFieldPosition: 0
[    25.095]     MaxPixelClock: 229500000
[    25.097] Mode: 10e (320x200)
[    25.097]     ModeAttributes: 0x3bf
[    25.097]     WinAAttributes: 0x7
[    25.097]     WinBAttributes: 0x0
[    25.097]     WinGranularity: 64
[    25.097]     WinSize: 64
[    25.097]     WinASegment: 0xa000
[    25.097]     WinBSegment: 0x0
[    25.097]     WinFuncPtr: 0xc0007cbe
[    25.097]     BytesPerScanline: 640
[    25.097]     XResolution: 320
[    25.097]     YResolution: 200
[    25.097]     XCharSize: 8
[    25.097]     YCharSize: 8
[    25.097]     NumberOfPlanes: 1
[    25.097]     BitsPerPixel: 16
[    25.097]     NumberOfBanks: 1
[    25.097]     MemoryModel: 6
[    25.097]     BankSize: 0
[    25.097]     NumberOfImages: 30
[    25.097]     RedMaskSize: 5
[    25.097]     RedFieldPosition: 11
[    25.097]     GreenMaskSize: 6
[    25.097]     GreenFieldPosition: 5
[    25.097]     BlueMaskSize: 5
[    25.097]     BlueFieldPosition: 0
[    25.097]     RsvdMaskSize: 0
[    25.097]     RsvdFieldPosition: 0
[    25.097]     DirectColorModeInfo: 0
[    25.097]     PhysBasePtr: 0xc1000000
[    25.097]     LinBytesPerScanLine: 640
[    25.097]     BnkNumberOfImagePages: 30
[    25.097]     LinNumberOfImagePages: 30
[    25.097]     LinRedMaskSize: 5
[    25.098]     LinRedFieldPosition: 11
[    25.098]     LinGreenMaskSize: 6
[    25.098]     LinGreenFieldPosition: 5
[    25.098]     LinBlueMaskSize: 5
[    25.098]     LinBlueFieldPosition: 0
[    25.098]     LinRsvdMaskSize: 0
[    25.098]     LinRsvdFieldPosition: 0
[    25.098]     MaxPixelClock: 229500000
[    25.100] *Mode: 10f (320x200)
[    25.100]     ModeAttributes: 0x3bf
[    25.100]     WinAAttributes: 0x7
[    25.100]     WinBAttributes: 0x0
[    25.100]     WinGranularity: 64
[    25.100]     WinSize: 64
[    25.100]     WinASegment: 0xa000
[    25.100]     WinBSegment: 0x0
[    25.100]     WinFuncPtr: 0xc0007cbe
[    25.100]     BytesPerScanline: 1280
[    25.100]     XResolution: 320
[    25.100]     YResolution: 200
[    25.100]     XCharSize: 8
[    25.100]     YCharSize: 8
[    25.100]     NumberOfPlanes: 1
[    25.100]     BitsPerPixel: 32
[    25.100]     NumberOfBanks: 1
[    25.100]     MemoryModel: 6
[    25.100]     BankSize: 0
[    25.100]     NumberOfImages: 14
[    25.100]     RedMaskSize: 8
[    25.100]     RedFieldPosition: 16
[    25.100]     GreenMaskSize: 8
[    25.100]     GreenFieldPosition: 8
[    25.100]     BlueMaskSize: 8
[    25.100]     BlueFieldPosition: 0
[    25.100]     RsvdMaskSize: 8
[    25.100]     RsvdFieldPosition: 24
[    25.100]     DirectColorModeInfo: 0
[    25.100]     PhysBasePtr: 0xc1000000
[    25.100]     LinBytesPerScanLine: 1280
[    25.100]     BnkNumberOfImagePages: 14
[    25.100]     LinNumberOfImagePages: 14
[    25.100]     LinRedMaskSize: 8
[    25.100]     LinRedFieldPosition: 16
[    25.100]     LinGreenMaskSize: 8
[    25.100]     LinGreenFieldPosition: 8
[    25.100]     LinBlueMaskSize: 8
[    25.100]     LinBlueFieldPosition: 0
[    25.100]     LinRsvdMaskSize: 8
[    25.100]     LinRsvdFieldPosition: 24
[    25.100]     MaxPixelClock: 229500000
[    25.103] Mode: 111 (640x480)
[    25.103]     ModeAttributes: 0x3bf
[    25.103]     WinAAttributes: 0x7
[    25.103]     WinBAttributes: 0x0
[    25.103]     WinGranularity: 64
[    25.103]     WinSize: 64
[    25.103]     WinASegment: 0xa000
[    25.103]     WinBSegment: 0x0
[    25.103]     WinFuncPtr: 0xc0007cbe
[    25.103]     BytesPerScanline: 1280
[    25.103]     XResolution: 640
[    25.103]     YResolution: 480
[    25.103]     XCharSize: 8
[    25.103]     YCharSize: 16
[    25.103]     NumberOfPlanes: 1
[    25.103]     BitsPerPixel: 16
[    25.103]     NumberOfBanks: 1
[    25.103]     MemoryModel: 6
[    25.103]     BankSize: 0
[    25.103]     NumberOfImages: 4
[    25.103]     RedMaskSize: 5
[    25.103]     RedFieldPosition: 11
[    25.103]     GreenMaskSize: 6
[    25.103]     GreenFieldPosition: 5
[    25.103]     BlueMaskSize: 5
[    25.103]     BlueFieldPosition: 0
[    25.103]     RsvdMaskSize: 0
[    25.103]     RsvdFieldPosition: 0
[    25.103]     DirectColorModeInfo: 0
[    25.103]     PhysBasePtr: 0xc1000000
[    25.103]     LinBytesPerScanLine: 1280
[    25.103]     BnkNumberOfImagePages: 4
[    25.103]     LinNumberOfImagePages: 4
[    25.103]     LinRedMaskSize: 5
[    25.103]     LinRedFieldPosition: 11
[    25.103]     LinGreenMaskSize: 6
[    25.103]     LinGreenFieldPosition: 5
[    25.103]     LinBlueMaskSize: 5
[    25.103]     LinBlueFieldPosition: 0
[    25.103]     LinRsvdMaskSize: 0
[    25.103]     LinRsvdFieldPosition: 0
[    25.103]     MaxPixelClock: 229500000
[    25.106] *Mode: 112 (640x480)
[    25.106]     ModeAttributes: 0x3bf
[    25.106]     WinAAttributes: 0x7
[    25.106]     WinBAttributes: 0x0
[    25.106]     WinGranularity: 64
[    25.106]     WinSize: 64
[    25.106]     WinASegment: 0xa000
[    25.106]     WinBSegment: 0x0
[    25.106]     WinFuncPtr: 0xc0007cbe
[    25.106]     BytesPerScanline: 2560
[    25.106]     XResolution: 640
[    25.106]     YResolution: 480
[    25.106]     XCharSize: 8
[    25.106]     YCharSize: 16
[    25.106]     NumberOfPlanes: 1
[    25.106]     BitsPerPixel: 32
[    25.106]     NumberOfBanks: 1
[    25.106]     MemoryModel: 6
[    25.106]     BankSize: 0
[    25.106]     NumberOfImages: 1
[    25.106]     RedMaskSize: 8
[    25.106]     RedFieldPosition: 16
[    25.106]     GreenMaskSize: 8
[    25.106]     GreenFieldPosition: 8
[    25.106]     BlueMaskSize: 8
[    25.106]     BlueFieldPosition: 0
[    25.106]     RsvdMaskSize: 8
[    25.106]     RsvdFieldPosition: 24
[    25.106]     DirectColorModeInfo: 0
[    25.106]     PhysBasePtr: 0xc1000000
[    25.106]     LinBytesPerScanLine: 2560
[    25.106]     BnkNumberOfImagePages: 1
[    25.106]     LinNumberOfImagePages: 1
[    25.106]     LinRedMaskSize: 8
[    25.106]     LinRedFieldPosition: 16
[    25.106]     LinGreenMaskSize: 8
[    25.106]     LinGreenFieldPosition: 8
[    25.106]     LinBlueMaskSize: 8
[    25.106]     LinBlueFieldPosition: 0
[    25.106]     LinRsvdMaskSize: 8
[    25.106]     LinRsvdFieldPosition: 24
[    25.106]     MaxPixelClock: 229500000
[    25.109] Mode: 114 (800x600)
[    25.109]     ModeAttributes: 0x3bf
[    25.109]     WinAAttributes: 0x7
[    25.109]     WinBAttributes: 0x0
[    25.109]     WinGranularity: 64
[    25.109]     WinSize: 64
[    25.109]     WinASegment: 0xa000
[    25.109]     WinBSegment: 0x0
[    25.109]     WinFuncPtr: 0xc0007cbe
[    25.109]     BytesPerScanline: 1600
[    25.109]     XResolution: 800
[    25.109]     YResolution: 600
[    25.109]     XCharSize: 8
[    25.109]     YCharSize: 16
[    25.109]     NumberOfPlanes: 1
[    25.109]     BitsPerPixel: 16
[    25.109]     NumberOfBanks: 1
[    25.109]     MemoryModel: 6
[    25.109]     BankSize: 0
[    25.109]     NumberOfImages: 2
[    25.109]     RedMaskSize: 5
[    25.109]     RedFieldPosition: 11
[    25.109]     GreenMaskSize: 6
[    25.109]     GreenFieldPosition: 5
[    25.109]     BlueMaskSize: 5
[    25.109]     BlueFieldPosition: 0
[    25.109]     RsvdMaskSize: 0
[    25.109]     RsvdFieldPosition: 0
[    25.109]     DirectColorModeInfo: 0
[    25.109]     PhysBasePtr: 0xc1000000
[    25.109]     LinBytesPerScanLine: 1600
[    25.109]     BnkNumberOfImagePages: 2
[    25.109]     LinNumberOfImagePages: 2
[    25.109]     LinRedMaskSize: 5
[    25.109]     LinRedFieldPosition: 11
[    25.109]     LinGreenMaskSize: 6
[    25.109]     LinGreenFieldPosition: 5
[    25.109]     LinBlueMaskSize: 5
[    25.109]     LinBlueFieldPosition: 0
[    25.109]     LinRsvdMaskSize: 0
[    25.109]     LinRsvdFieldPosition: 0
[    25.109]     MaxPixelClock: 229500000
[    25.111] *Mode: 115 (800x600)
[    25.111]     ModeAttributes: 0x3bf
[    25.111]     WinAAttributes: 0x7
[    25.111]     WinBAttributes: 0x0
[    25.111]     WinGranularity: 64
[    25.111]     WinSize: 64
[    25.111]     WinASegment: 0xa000
[    25.111]     WinBSegment: 0x0
[    25.111]     WinFuncPtr: 0xc0007cbe
[    25.111]     BytesPerScanline: 3200
[    25.111]     XResolution: 800
[    25.111]     YResolution: 600
[    25.111]     XCharSize: 8
[    25.111]     YCharSize: 16
[    25.112]     NumberOfPlanes: 1
[    25.112]     BitsPerPixel: 32
[    25.112]     NumberOfBanks: 1
[    25.112]     MemoryModel: 6
[    25.112]     BankSize: 0
[    25.112]     NumberOfImages: 1
[    25.112]     RedMaskSize: 8
[    25.112]     RedFieldPosition: 16
[    25.112]     GreenMaskSize: 8
[    25.112]     GreenFieldPosition: 8
[    25.112]     BlueMaskSize: 8
[    25.112]     BlueFieldPosition: 0
[    25.112]     RsvdMaskSize: 8
[    25.112]     RsvdFieldPosition: 24
[    25.112]     DirectColorModeInfo: 0
[    25.112]     PhysBasePtr: 0xc1000000
[    25.112]     LinBytesPerScanLine: 3200
[    25.112]     BnkNumberOfImagePages: 1
[    25.112]     LinNumberOfImagePages: 1
[    25.112]     LinRedMaskSize: 8
[    25.112]     LinRedFieldPosition: 16
[    25.112]     LinGreenMaskSize: 8
[    25.112]     LinGreenFieldPosition: 8
[    25.112]     LinBlueMaskSize: 8
[    25.112]     LinBlueFieldPosition: 0
[    25.112]     LinRsvdMaskSize: 8
[    25.112]     LinRsvdFieldPosition: 24
[    25.112]     MaxPixelClock: 229500000
[    25.114] Mode: 117 (1024x768)
[    25.114]     ModeAttributes: 0x3bf
[    25.114]     WinAAttributes: 0x7
[    25.114]     WinBAttributes: 0x0
[    25.114]     WinGranularity: 64
[    25.114]     WinSize: 64
[    25.114]     WinASegment: 0xa000
[    25.114]     WinBSegment: 0x0
[    25.114]     WinFuncPtr: 0xc0007cbe
[    25.114]     BytesPerScanline: 2048
[    25.114]     XResolution: 1024
[    25.114]     YResolution: 768
[    25.114]     XCharSize: 8
[    25.114]     YCharSize: 16
[    25.114]     NumberOfPlanes: 1
[    25.114]     BitsPerPixel: 16
[    25.114]     NumberOfBanks: 1
[    25.114]     MemoryModel: 6
[    25.114]     BankSize: 0
[    25.114]     NumberOfImages: 1
[    25.114]     RedMaskSize: 5
[    25.115]     RedFieldPosition: 11
[    25.115]     GreenMaskSize: 6
[    25.115]     GreenFieldPosition: 5
[    25.115]     BlueMaskSize: 5
[    25.115]     BlueFieldPosition: 0
[    25.115]     RsvdMaskSize: 0
[    25.115]     RsvdFieldPosition: 0
[    25.115]     DirectColorModeInfo: 0
[    25.115]     PhysBasePtr: 0xc1000000
[    25.115]     LinBytesPerScanLine: 2048
[    25.115]     BnkNumberOfImagePages: 1
[    25.115]     LinNumberOfImagePages: 1
[    25.115]     LinRedMaskSize: 5
[    25.115]     LinRedFieldPosition: 11
[    25.115]     LinGreenMaskSize: 6
[    25.115]     LinGreenFieldPosition: 5
[    25.115]     LinBlueMaskSize: 5
[    25.115]     LinBlueFieldPosition: 0
[    25.115]     LinRsvdMaskSize: 0
[    25.115]     LinRsvdFieldPosition: 0
[    25.115]     MaxPixelClock: 229500000
[    25.117] *Mode: 118 (1024x768)
[    25.117]     ModeAttributes: 0x3bf
[    25.117]     WinAAttributes: 0x7
[    25.117]     WinBAttributes: 0x0
[    25.117]     WinGranularity: 64
[    25.117]     WinSize: 64
[    25.117]     WinASegment: 0xa000
[    25.117]     WinBSegment: 0x0
[    25.117]     WinFuncPtr: 0xc0007cbe
[    25.117]     BytesPerScanline: 4096
[    25.117]     XResolution: 1024
[    25.117]     YResolution: 768
[    25.117]     XCharSize: 8
[    25.117]     YCharSize: 16
[    25.117]     NumberOfPlanes: 1
[    25.117]     BitsPerPixel: 32
[    25.117]     NumberOfBanks: 1
[    25.117]     MemoryModel: 6
[    25.117]     BankSize: 0
[    25.117]     NumberOfImages: 1
[    25.117]     RedMaskSize: 8
[    25.117]     RedFieldPosition: 16
[    25.117]     GreenMaskSize: 8
[    25.117]     GreenFieldPosition: 8
[    25.117]     BlueMaskSize: 8
[    25.117]     BlueFieldPosition: 0
[    25.117]     RsvdMaskSize: 8
[    25.117]     RsvdFieldPosition: 24
[    25.117]     DirectColorModeInfo: 0
[    25.117]     PhysBasePtr: 0xc1000000
[    25.117]     LinBytesPerScanLine: 4096
[    25.117]     BnkNumberOfImagePages: 1
[    25.117]     LinNumberOfImagePages: 1
[    25.117]     LinRedMaskSize: 8
[    25.118]     LinRedFieldPosition: 16
[    25.118]     LinGreenMaskSize: 8
[    25.118]     LinGreenFieldPosition: 8
[    25.118]     LinBlueMaskSize: 8
[    25.118]     LinBlueFieldPosition: 0
[    25.118]     LinRsvdMaskSize: 8
[    25.118]     LinRsvdFieldPosition: 24
[    25.118]     MaxPixelClock: 229500000
[    25.120] Mode: 11a (1280x1024)
[    25.120]     ModeAttributes: 0x3bf
[    25.120]     WinAAttributes: 0x7
[    25.120]     WinBAttributes: 0x0
[    25.120]     WinGranularity: 64
[    25.120]     WinSize: 64
[    25.120]     WinASegment: 0xa000
[    25.120]     WinBSegment: 0x0
[    25.120]     WinFuncPtr: 0xc0007cbe
[    25.120]     BytesPerScanline: 2560
[    25.120]     XResolution: 1280
[    25.120]     YResolution: 1024
[    25.120]     XCharSize: 8
[    25.120]     YCharSize: 16
[    25.120]     NumberOfPlanes: 1
[    25.120]     BitsPerPixel: 16
[    25.120]     NumberOfBanks: 1
[    25.120]     MemoryModel: 6
[    25.120]     BankSize: 0
[    25.120]     NumberOfImages: 1
[    25.120]     RedMaskSize: 5
[    25.120]     RedFieldPosition: 11
[    25.120]     GreenMaskSize: 6
[    25.120]     GreenFieldPosition: 5
[    25.120]     BlueMaskSize: 5
[    25.120]     BlueFieldPosition: 0
[    25.120]     RsvdMaskSize: 0
[    25.120]     RsvdFieldPosition: 0
[    25.120]     DirectColorModeInfo: 0
[    25.120]     PhysBasePtr: 0xc1000000
[    25.120]     LinBytesPerScanLine: 2560
[    25.120]     BnkNumberOfImagePages: 1
[    25.120]     LinNumberOfImagePages: 1
[    25.120]     LinRedMaskSize: 5
[    25.120]     LinRedFieldPosition: 11
[    25.120]     LinGreenMaskSize: 6
[    25.120]     LinGreenFieldPosition: 5
[    25.120]     LinBlueMaskSize: 5
[    25.120]     LinBlueFieldPosition: 0
[    25.120]     LinRsvdMaskSize: 0
[    25.120]     LinRsvdFieldPosition: 0
[    25.120]     MaxPixelClock: 229500000
[    25.123] *Mode: 11b (1280x1024)
[    25.123]     ModeAttributes: 0x3bf
[    25.123]     WinAAttributes: 0x7
[    25.123]     WinBAttributes: 0x0
[    25.123]     WinGranularity: 64
[    25.123]     WinSize: 64
[    25.123]     WinASegment: 0xa000
[    25.123]     WinBSegment: 0x0
[    25.123]     WinFuncPtr: 0xc0007cbe
[    25.123]     BytesPerScanline: 5120
[    25.123]     XResolution: 1280
[    25.123]     YResolution: 1024
[    25.123]     XCharSize: 8
[    25.123]     YCharSize: 16
[    25.123]     NumberOfPlanes: 1
[    25.123]     BitsPerPixel: 32
[    25.123]     NumberOfBanks: 1
[    25.123]     MemoryModel: 6
[    25.123]     BankSize: 0
[    25.123]     NumberOfImages: 1
[    25.123]     RedMaskSize: 8
[    25.123]     RedFieldPosition: 16
[    25.123]     GreenMaskSize: 8
[    25.123]     GreenFieldPosition: 8
[    25.123]     BlueMaskSize: 8
[    25.123]     BlueFieldPosition: 0
[    25.123]     RsvdMaskSize: 8
[    25.123]     RsvdFieldPosition: 24
[    25.123]     DirectColorModeInfo: 0
[    25.123]     PhysBasePtr: 0xc1000000
[    25.123]     LinBytesPerScanLine: 5120
[    25.123]     BnkNumberOfImagePages: 1
[    25.123]     LinNumberOfImagePages: 1
[    25.123]     LinRedMaskSize: 8
[    25.123]     LinRedFieldPosition: 16
[    25.123]     LinGreenMaskSize: 8
[    25.123]     LinGreenFieldPosition: 8
[    25.123]     LinBlueMaskSize: 8
[    25.123]     LinBlueFieldPosition: 0
[    25.123]     LinRsvdMaskSize: 8
[    25.123]     LinRsvdFieldPosition: 24
[    25.123]     MaxPixelClock: 229500000
[    25.126] Mode: 130 (320x200)
[    25.126]     ModeAttributes: 0x3bf
[    25.126]     WinAAttributes: 0x7
[    25.126]     WinBAttributes: 0x0
[    25.126]     WinGranularity: 64
[    25.126]     WinSize: 64
[    25.126]     WinASegment: 0xa000
[    25.126]     WinBSegment: 0x0
[    25.126]     WinFuncPtr: 0xc0007cbe
[    25.126]     BytesPerScanline: 320
[    25.126]     XResolution: 320
[    25.126]     YResolution: 200
[    25.126]     XCharSize: 8
[    25.126]     YCharSize: 8
[    25.126]     NumberOfPlanes: 1
[    25.126]     BitsPerPixel: 8
[    25.126]     NumberOfBanks: 1
[    25.126]     MemoryModel: 4
[    25.126]     BankSize: 0
[    25.126]     NumberOfImages: 62
[    25.126]     RedMaskSize: 0
[    25.126]     RedFieldPosition: 0
[    25.126]     GreenMaskSize: 0
[    25.126]     GreenFieldPosition: 0
[    25.126]     BlueMaskSize: 0
[    25.126]     BlueFieldPosition: 0
[    25.126]     RsvdMaskSize: 0
[    25.126]     RsvdFieldPosition: 0
[    25.126]     DirectColorModeInfo: 0
[    25.126]     PhysBasePtr: 0xc1000000
[    25.126]     LinBytesPerScanLine: 320
[    25.126]     BnkNumberOfImagePages: 62
[    25.126]     LinNumberOfImagePages: 62
[    25.126]     LinRedMaskSize: 0
[    25.126]     LinRedFieldPosition: 0
[    25.126]     LinGreenMaskSize: 0
[    25.126]     LinGreenFieldPosition: 0
[    25.126]     LinBlueMaskSize: 0
[    25.126]     LinBlueFieldPosition: 0
[    25.126]     LinRsvdMaskSize: 0
[    25.126]     LinRsvdFieldPosition: 0
[    25.126]     MaxPixelClock: 229500000
[    25.129] Mode: 131 (320x400)
[    25.129]     ModeAttributes: 0x3bf
[    25.129]     WinAAttributes: 0x7
[    25.129]     WinBAttributes: 0x0
[    25.129]     WinGranularity: 64
[    25.129]     WinSize: 64
[    25.129]     WinASegment: 0xa000
[    25.129]     WinBSegment: 0x0
[    25.129]     WinFuncPtr: 0xc0007cbe
[    25.129]     BytesPerScanline: 320
[    25.129]     XResolution: 320
[    25.129]     YResolution: 400
[    25.129]     XCharSize: 8
[    25.129]     YCharSize: 16
[    25.129]     NumberOfPlanes: 1
[    25.129]     BitsPerPixel: 8
[    25.129]     NumberOfBanks: 1
[    25.129]     MemoryModel: 4
[    25.129]     BankSize: 0
[    25.129]     NumberOfImages: 30
[    25.129]     RedMaskSize: 0
[    25.129]     RedFieldPosition: 0
[    25.129]     GreenMaskSize: 0
[    25.129]     GreenFieldPosition: 0
[    25.129]     BlueMaskSize: 0
[    25.129]     BlueFieldPosition: 0
[    25.129]     RsvdMaskSize: 0
[    25.129]     RsvdFieldPosition: 0
[    25.129]     DirectColorModeInfo: 0
[    25.129]     PhysBasePtr: 0xc1000000
[    25.129]     LinBytesPerScanLine: 320
[    25.129]     BnkNumberOfImagePages: 30
[    25.129]     LinNumberOfImagePages: 30
[    25.129]     LinRedMaskSize: 0
[    25.129]     LinRedFieldPosition: 0
[    25.129]     LinGreenMaskSize: 0
[    25.129]     LinGreenFieldPosition: 0
[    25.129]     LinBlueMaskSize: 0
[    25.129]     LinBlueFieldPosition: 0
[    25.129]     LinRsvdMaskSize: 0
[    25.129]     LinRsvdFieldPosition: 0
[    25.129]     MaxPixelClock: 229500000
[    25.131] Mode: 132 (320x400)
[    25.131]     ModeAttributes: 0x3bf
[    25.131]     WinAAttributes: 0x7
[    25.131]     WinBAttributes: 0x0
[    25.131]     WinGranularity: 64
[    25.131]     WinSize: 64
[    25.131]     WinASegment: 0xa000
[    25.131]     WinBSegment: 0x0
[    25.131]     WinFuncPtr: 0xc0007cbe
[    25.131]     BytesPerScanline: 640
[    25.131]     XResolution: 320
[    25.131]     YResolution: 400
[    25.131]     XCharSize: 8
[    25.131]     YCharSize: 16
[    25.131]     NumberOfPlanes: 1
[    25.131]     BitsPerPixel: 16
[    25.131]     NumberOfBanks: 1
[    25.132]     MemoryModel: 6
[    25.132]     BankSize: 0
[    25.132]     NumberOfImages: 14
[    25.132]     RedMaskSize: 5
[    25.132]     RedFieldPosition: 11
[    25.132]     GreenMaskSize: 6
[    25.132]     GreenFieldPosition: 5
[    25.132]     BlueMaskSize: 5
[    25.132]     BlueFieldPosition: 0
[    25.132]     RsvdMaskSize: 0
[    25.132]     RsvdFieldPosition: 0
[    25.132]     DirectColorModeInfo: 0
[    25.132]     PhysBasePtr: 0xc1000000
[    25.132]     LinBytesPerScanLine: 640
[    25.132]     BnkNumberOfImagePages: 14
[    25.132]     LinNumberOfImagePages: 14
[    25.132]     LinRedMaskSize: 5
[    25.132]     LinRedFieldPosition: 11
[    25.132]     LinGreenMaskSize: 6
[    25.132]     LinGreenFieldPosition: 5
[    25.132]     LinBlueMaskSize: 5
[    25.132]     LinBlueFieldPosition: 0
[    25.132]     LinRsvdMaskSize: 0
[    25.132]     LinRsvdFieldPosition: 0
[    25.132]     MaxPixelClock: 229500000
[    25.134] *Mode: 133 (320x400)
[    25.134]     ModeAttributes: 0x3bf
[    25.134]     WinAAttributes: 0x7
[    25.134]     WinBAttributes: 0x0
[    25.134]     WinGranularity: 64
[    25.134]     WinSize: 64
[    25.134]     WinASegment: 0xa000
[    25.134]     WinBSegment: 0x0
[    25.134]     WinFuncPtr: 0xc0007cbe
[    25.134]     BytesPerScanline: 1280
[    25.134]     XResolution: 320
[    25.134]     YResolution: 400
[    25.134]     XCharSize: 8
[    25.134]     YCharSize: 16
[    25.134]     NumberOfPlanes: 1
[    25.134]     BitsPerPixel: 32
[    25.134]     NumberOfBanks: 1
[    25.134]     MemoryModel: 6
[    25.134]     BankSize: 0
[    25.134]     NumberOfImages: 6
[    25.134]     RedMaskSize: 8
[    25.134]     RedFieldPosition: 16
[    25.134]     GreenMaskSize: 8
[    25.134]     GreenFieldPosition: 8
[    25.134]     BlueMaskSize: 8
[    25.134]     BlueFieldPosition: 0
[    25.134]     RsvdMaskSize: 8
[    25.134]     RsvdFieldPosition: 24
[    25.134]     DirectColorModeInfo: 0
[    25.134]     PhysBasePtr: 0xc1000000
[    25.134]     LinBytesPerScanLine: 1280
[    25.134]     BnkNumberOfImagePages: 6
[    25.134]     LinNumberOfImagePages: 6
[    25.134]     LinRedMaskSize: 8
[    25.135]     LinRedFieldPosition: 16
[    25.135]     LinGreenMaskSize: 8
[    25.135]     LinGreenFieldPosition: 8
[    25.135]     LinBlueMaskSize: 8
[    25.135]     LinBlueFieldPosition: 0
[    25.135]     LinRsvdMaskSize: 8
[    25.135]     LinRsvdFieldPosition: 24
[    25.135]     MaxPixelClock: 229500000
[    25.137] Mode: 134 (320x240)
[    25.137]     ModeAttributes: 0x3bf
[    25.137]     WinAAttributes: 0x7
[    25.137]     WinBAttributes: 0x0
[    25.137]     WinGranularity: 64
[    25.137]     WinSize: 64
[    25.137]     WinASegment: 0xa000
[    25.137]     WinBSegment: 0x0
[    25.137]     WinFuncPtr: 0xc0007cbe
[    25.137]     BytesPerScanline: 320
[    25.137]     XResolution: 320
[    25.137]     YResolution: 240
[    25.137]     XCharSize: 8
[    25.137]     YCharSize: 8
[    25.137]     NumberOfPlanes: 1
[    25.137]     BitsPerPixel: 8
[    25.137]     NumberOfBanks: 1
[    25.137]     MemoryModel: 4
[    25.137]     BankSize: 0
[    25.137]     NumberOfImages: 30
[    25.137]     RedMaskSize: 0
[    25.137]     RedFieldPosition: 0
[    25.137]     GreenMaskSize: 0
[    25.137]     GreenFieldPosition: 0
[    25.137]     BlueMaskSize: 0
[    25.137]     BlueFieldPosition: 0
[    25.137]     RsvdMaskSize: 0
[    25.137]     RsvdFieldPosition: 0
[    25.137]     DirectColorModeInfo: 0
[    25.137]     PhysBasePtr: 0xc1000000
[    25.137]     LinBytesPerScanLine: 320
[    25.137]     BnkNumberOfImagePages: 30
[    25.137]     LinNumberOfImagePages: 30
[    25.137]     LinRedMaskSize: 0
[    25.137]     LinRedFieldPosition: 0
[    25.137]     LinGreenMaskSize: 0
[    25.137]     LinGreenFieldPosition: 0
[    25.137]     LinBlueMaskSize: 0
[    25.137]     LinBlueFieldPosition: 0
[    25.137]     LinRsvdMaskSize: 0
[    25.137]     LinRsvdFieldPosition: 0
[    25.137]     MaxPixelClock: 229500000
[    25.140] Mode: 135 (320x240)
[    25.140]     ModeAttributes: 0x3bf
[    25.140]     WinAAttributes: 0x7
[    25.140]     WinBAttributes: 0x0
[    25.140]     WinGranularity: 64
[    25.140]     WinSize: 64
[    25.140]     WinASegment: 0xa000
[    25.140]     WinBSegment: 0x0
[    25.140]     WinFuncPtr: 0xc0007cbe
[    25.140]     BytesPerScanline: 640
[    25.140]     XResolution: 320
[    25.140]     YResolution: 240
[    25.140]     XCharSize: 8
[    25.140]     YCharSize: 8
[    25.140]     NumberOfPlanes: 1
[    25.140]     BitsPerPixel: 16
[    25.140]     NumberOfBanks: 1
[    25.140]     MemoryModel: 6
[    25.140]     BankSize: 0
[    25.140]     NumberOfImages: 19
[    25.140]     RedMaskSize: 5
[    25.140]     RedFieldPosition: 11
[    25.140]     GreenMaskSize: 6
[    25.140]     GreenFieldPosition: 5
[    25.140]     BlueMaskSize: 5
[    25.140]     BlueFieldPosition: 0
[    25.140]     RsvdMaskSize: 0
[    25.140]     RsvdFieldPosition: 0
[    25.140]     DirectColorModeInfo: 0
[    25.140]     PhysBasePtr: 0xc1000000
[    25.140]     LinBytesPerScanLine: 640
[    25.140]     BnkNumberOfImagePages: 19
[    25.140]     LinNumberOfImagePages: 19
[    25.140]     LinRedMaskSize: 5
[    25.140]     LinRedFieldPosition: 11
[    25.140]     LinGreenMaskSize: 6
[    25.140]     LinGreenFieldPosition: 5
[    25.140]     LinBlueMaskSize: 5
[    25.140]     LinBlueFieldPosition: 0
[    25.140]     LinRsvdMaskSize: 0
[    25.140]     LinRsvdFieldPosition: 0
[    25.140]     MaxPixelClock: 229500000
[    25.143] *Mode: 136 (320x240)
[    25.143]     ModeAttributes: 0x3bf
[    25.143]     WinAAttributes: 0x7
[    25.143]     WinBAttributes: 0x0
[    25.143]     WinGranularity: 64
[    25.143]     WinSize: 64
[    25.143]     WinASegment: 0xa000
[    25.143]     WinBSegment: 0x0
[    25.143]     WinFuncPtr: 0xc0007cbe
[    25.143]     BytesPerScanline: 1280
[    25.143]     XResolution: 320
[    25.143]     YResolution: 240
[    25.143]     XCharSize: 8
[    25.143]     YCharSize: 8
[    25.143]     NumberOfPlanes: 1
[    25.143]     BitsPerPixel: 32
[    25.143]     NumberOfBanks: 1
[    25.143]     MemoryModel: 6
[    25.143]     BankSize: 0
[    25.143]     NumberOfImages: 10
[    25.143]     RedMaskSize: 8
[    25.143]     RedFieldPosition: 16
[    25.143]     GreenMaskSize: 8
[    25.143]     GreenFieldPosition: 8
[    25.143]     BlueMaskSize: 8
[    25.143]     BlueFieldPosition: 0
[    25.143]     RsvdMaskSize: 8
[    25.143]     RsvdFieldPosition: 24
[    25.143]     DirectColorModeInfo: 0
[    25.143]     PhysBasePtr: 0xc1000000
[    25.143]     LinBytesPerScanLine: 1280
[    25.143]     BnkNumberOfImagePages: 10
[    25.143]     LinNumberOfImagePages: 10
[    25.143]     LinRedMaskSize: 8
[    25.143]     LinRedFieldPosition: 16
[    25.143]     LinGreenMaskSize: 8
[    25.143]     LinGreenFieldPosition: 8
[    25.143]     LinBlueMaskSize: 8
[    25.143]     LinBlueFieldPosition: 0
[    25.143]     LinRsvdMaskSize: 8
[    25.143]     LinRsvdFieldPosition: 24
[    25.143]     MaxPixelClock: 229500000
[    25.145] Mode: 13d (640x400)
[    25.145]     ModeAttributes: 0x3bf
[    25.145]     WinAAttributes: 0x7
[    25.145]     WinBAttributes: 0x0
[    25.145]     WinGranularity: 64
[    25.145]     WinSize: 64
[    25.146]     WinASegment: 0xa000
[    25.146]     WinBSegment: 0x0
[    25.146]     WinFuncPtr: 0xc0007cbe
[    25.146]     BytesPerScanline: 1280
[    25.146]     XResolution: 640
[    25.146]     YResolution: 400
[    25.146]     XCharSize: 8
[    25.146]     YCharSize: 16
[    25.146]     NumberOfPlanes: 1
[    25.146]     BitsPerPixel: 16
[    25.146]     NumberOfBanks: 1
[    25.146]     MemoryModel: 6
[    25.146]     BankSize: 0
[    25.146]     NumberOfImages: 6
[    25.146]     RedMaskSize: 5
[    25.146]     RedFieldPosition: 11
[    25.146]     GreenMaskSize: 6
[    25.146]     GreenFieldPosition: 5
[    25.146]     BlueMaskSize: 5
[    25.146]     BlueFieldPosition: 0
[    25.146]     RsvdMaskSize: 0
[    25.146]     RsvdFieldPosition: 0
[    25.146]     DirectColorModeInfo: 0
[    25.146]     PhysBasePtr: 0xc1000000
[    25.146]     LinBytesPerScanLine: 1280
[    25.146]     BnkNumberOfImagePages: 6
[    25.146]     LinNumberOfImagePages: 6
[    25.146]     LinRedMaskSize: 5
[    25.146]     LinRedFieldPosition: 11
[    25.146]     LinGreenMaskSize: 6
[    25.146]     LinGreenFieldPosition: 5
[    25.146]     LinBlueMaskSize: 5
[    25.146]     LinBlueFieldPosition: 0
[    25.146]     LinRsvdMaskSize: 0
[    25.146]     LinRsvdFieldPosition: 0
[    25.146]     MaxPixelClock: 229500000
[    25.148] *Mode: 13e (640x400)
[    25.148]     ModeAttributes: 0x3bf
[    25.148]     WinAAttributes: 0x7
[    25.148]     WinBAttributes: 0x0
[    25.148]     WinGranularity: 64
[    25.148]     WinSize: 64
[    25.148]     WinASegment: 0xa000
[    25.148]     WinBSegment: 0x0
[    25.148]     WinFuncPtr: 0xc0007cbe
[    25.148]     BytesPerScanline: 2560
[    25.148]     XResolution: 640
[    25.148]     YResolution: 400
[    25.148]     XCharSize: 8
[    25.148]     YCharSize: 16
[    25.148]     NumberOfPlanes: 1
[    25.148]     BitsPerPixel: 32
[    25.148]     NumberOfBanks: 1
[    25.148]     MemoryModel: 6
[    25.148]     BankSize: 0
[    25.149]     NumberOfImages: 2
[    25.149]     RedMaskSize: 8
[    25.149]     RedFieldPosition: 16
[    25.149]     GreenMaskSize: 8
[    25.149]     GreenFieldPosition: 8
[    25.149]     BlueMaskSize: 8
[    25.149]     BlueFieldPosition: 0
[    25.149]     RsvdMaskSize: 8
[    25.149]     RsvdFieldPosition: 24
[    25.149]     DirectColorModeInfo: 0
[    25.149]     PhysBasePtr: 0xc1000000
[    25.149]     LinBytesPerScanLine: 2560
[    25.149]     BnkNumberOfImagePages: 2
[    25.149]     LinNumberOfImagePages: 2
[    25.149]     LinRedMaskSize: 8
[    25.149]     LinRedFieldPosition: 16
[    25.149]     LinGreenMaskSize: 8
[    25.149]     LinGreenFieldPosition: 8
[    25.149]     LinBlueMaskSize: 8
[    25.149]     LinBlueFieldPosition: 0
[    25.149]     LinRsvdMaskSize: 8
[    25.149]     LinRsvdFieldPosition: 24
[    25.149]     MaxPixelClock: 229500000
[    25.151] Mode: 14b (1680x1050)
[    25.151]     ModeAttributes: 0x3bf
[    25.151]     WinAAttributes: 0x7
[    25.151]     WinBAttributes: 0x0
[    25.151]     WinGranularity: 64
[    25.151]     WinSize: 64
[    25.151]     WinASegment: 0xa000
[    25.151]     WinBSegment: 0x0
[    25.151]     WinFuncPtr: 0xc0007cbe
[    25.151]     BytesPerScanline: 1680
[    25.151]     XResolution: 1680
[    25.151]     YResolution: 1050
[    25.151]     XCharSize: 8
[    25.151]     YCharSize: 16
[    25.151]     NumberOfPlanes: 1
[    25.151]     BitsPerPixel: 8
[    25.151]     NumberOfBanks: 1
[    25.151]     MemoryModel: 4
[    25.151]     BankSize: 0
[    25.151]     NumberOfImages: 1
[    25.151]     RedMaskSize: 0
[    25.151]     RedFieldPosition: 0
[    25.151]     GreenMaskSize: 0
[    25.151]     GreenFieldPosition: 0
[    25.151]     BlueMaskSize: 0
[    25.151]     BlueFieldPosition: 0
[    25.151]     RsvdMaskSize: 0
[    25.151]     RsvdFieldPosition: 0
[    25.151]     DirectColorModeInfo: 0
[    25.151]     PhysBasePtr: 0xc1000000
[    25.151]     LinBytesPerScanLine: 1680
[    25.151]     BnkNumberOfImagePages: 1
[    25.151]     LinNumberOfImagePages: 1
[    25.151]     LinRedMaskSize: 0
[    25.152]     LinRedFieldPosition: 0
[    25.152]     LinGreenMaskSize: 0
[    25.152]     LinGreenFieldPosition: 0
[    25.152]     LinBlueMaskSize: 0
[    25.152]     LinBlueFieldPosition: 0
[    25.152]     LinRsvdMaskSize: 0
[    25.152]     LinRsvdFieldPosition: 0
[    25.152]     MaxPixelClock: 229500000
[    25.154] Mode: 14c (1680x1050)
[    25.154]     ModeAttributes: 0x3bf
[    25.154]     WinAAttributes: 0x7
[    25.154]     WinBAttributes: 0x0
[    25.154]     WinGranularity: 64
[    25.154]     WinSize: 64
[    25.154]     WinASegment: 0xa000
[    25.154]     WinBSegment: 0x0
[    25.154]     WinFuncPtr: 0xc0007cbe
[    25.154]     BytesPerScanline: 3360
[    25.154]     XResolution: 1680
[    25.154]     YResolution: 1050
[    25.154]     XCharSize: 8
[    25.154]     YCharSize: 16
[    25.154]     NumberOfPlanes: 1
[    25.154]     BitsPerPixel: 16
[    25.154]     NumberOfBanks: 1
[    25.154]     MemoryModel: 6
[    25.154]     BankSize: 0
[    25.154]     NumberOfImages: 1
[    25.154]     RedMaskSize: 5
[    25.154]     RedFieldPosition: 11
[    25.154]     GreenMaskSize: 6
[    25.154]     GreenFieldPosition: 5
[    25.154]     BlueMaskSize: 5
[    25.154]     BlueFieldPosition: 0
[    25.154]     RsvdMaskSize: 0
[    25.154]     RsvdFieldPosition: 0
[    25.154]     DirectColorModeInfo: 0
[    25.154]     PhysBasePtr: 0xc1000000
[    25.154]     LinBytesPerScanLine: 3360
[    25.154]     BnkNumberOfImagePages: 1
[    25.154]     LinNumberOfImagePages: 1
[    25.154]     LinRedMaskSize: 5
[    25.154]     LinRedFieldPosition: 11
[    25.154]     LinGreenMaskSize: 6
[    25.154]     LinGreenFieldPosition: 5
[    25.154]     LinBlueMaskSize: 5
[    25.154]     LinBlueFieldPosition: 0
[    25.154]     LinRsvdMaskSize: 0
[    25.154]     LinRsvdFieldPosition: 0
[    25.154]     MaxPixelClock: 229500000
[    25.157] *Mode: 14d (1680x1050)
[    25.157]     ModeAttributes: 0x3bf
[    25.157]     WinAAttributes: 0x7
[    25.157]     WinBAttributes: 0x0
[    25.157]     WinGranularity: 64
[    25.157]     WinSize: 64
[    25.157]     WinASegment: 0xa000
[    25.157]     WinBSegment: 0x0
[    25.157]     WinFuncPtr: 0xc0007cbe
[    25.157]     BytesPerScanline: 6720
[    25.157]     XResolution: 1680
[    25.157]     YResolution: 1050
[    25.157]     XCharSize: 8
[    25.157]     YCharSize: 16
[    25.157]     NumberOfPlanes: 1
[    25.157]     BitsPerPixel: 32
[    25.157]     NumberOfBanks: 1
[    25.157]     MemoryModel: 6
[    25.157]     BankSize: 0
[    25.157]     NumberOfImages: 1
[    25.157]     RedMaskSize: 8
[    25.157]     RedFieldPosition: 16
[    25.157]     GreenMaskSize: 8
[    25.157]     GreenFieldPosition: 8
[    25.157]     BlueMaskSize: 8
[    25.157]     BlueFieldPosition: 0
[    25.157]     RsvdMaskSize: 8
[    25.157]     RsvdFieldPosition: 24
[    25.157]     DirectColorModeInfo: 0
[    25.157]     PhysBasePtr: 0xc1000000
[    25.157]     LinBytesPerScanLine: 6720
[    25.157]     BnkNumberOfImagePages: 1
[    25.157]     LinNumberOfImagePages: 1
[    25.157]     LinRedMaskSize: 8
[    25.157]     LinRedFieldPosition: 16
[    25.157]     LinGreenMaskSize: 8
[    25.157]     LinGreenFieldPosition: 8
[    25.157]     LinBlueMaskSize: 8
[    25.157]     LinBlueFieldPosition: 0
[    25.157]     LinRsvdMaskSize: 8
[    25.157]     LinRsvdFieldPosition: 24
[    25.157]     MaxPixelClock: 229500000
[    25.160] Mode: 160 (1280x800)
[    25.160]     ModeAttributes: 0x3bf
[    25.160]     WinAAttributes: 0x7
[    25.160]     WinBAttributes: 0x0
[    25.160]     WinGranularity: 64
[    25.160]     WinSize: 64
[    25.160]     WinASegment: 0xa000
[    25.160]     WinBSegment: 0x0
[    25.160]     WinFuncPtr: 0xc0007cbe
[    25.160]     BytesPerScanline: 1280
[    25.160]     XResolution: 1280
[    25.160]     YResolution: 800
[    25.160]     XCharSize: 8
[    25.160]     YCharSize: 16
[    25.160]     NumberOfPlanes: 1
[    25.160]     BitsPerPixel: 8
[    25.160]     NumberOfBanks: 1
[    25.160]     MemoryModel: 4
[    25.160]     BankSize: 0
[    25.160]     NumberOfImages: 2
[    25.160]     RedMaskSize: 0
[    25.160]     RedFieldPosition: 0
[    25.160]     GreenMaskSize: 0
[    25.160]     GreenFieldPosition: 0
[    25.160]     BlueMaskSize: 0
[    25.160]     BlueFieldPosition: 0
[    25.160]     RsvdMaskSize: 0
[    25.160]     RsvdFieldPosition: 0
[    25.160]     DirectColorModeInfo: 0
[    25.160]     PhysBasePtr: 0xc1000000
[    25.160]     LinBytesPerScanLine: 1280
[    25.160]     BnkNumberOfImagePages: 2
[    25.160]     LinNumberOfImagePages: 2
[    25.160]     LinRedMaskSize: 0
[    25.160]     LinRedFieldPosition: 0
[    25.160]     LinGreenMaskSize: 0
[    25.160]     LinGreenFieldPosition: 0
[    25.160]     LinBlueMaskSize: 0
[    25.160]     LinBlueFieldPosition: 0
[    25.160]     LinRsvdMaskSize: 0
[    25.160]     LinRsvdFieldPosition: 0
[    25.160]     MaxPixelClock: 229500000
[    25.163] *Mode: 161 (1280x800)
[    25.163]     ModeAttributes: 0x3bf
[    25.163]     WinAAttributes: 0x7
[    25.163]     WinBAttributes: 0x0
[    25.163]     WinGranularity: 64
[    25.163]     WinSize: 64
[    25.163]     WinASegment: 0xa000
[    25.163]     WinBSegment: 0x0
[    25.163]     WinFuncPtr: 0xc0007cbe
[    25.163]     BytesPerScanline: 5120
[    25.163]     XResolution: 1280
[    25.163]     YResolution: 800
[    25.163]     XCharSize: 8
[    25.163]     YCharSize: 16
[    25.163]     NumberOfPlanes: 1
[    25.163]     BitsPerPixel: 32
[    25.163]     NumberOfBanks: 1
[    25.163]     MemoryModel: 6
[    25.163]     BankSize: 0
[    25.163]     NumberOfImages: 1
[    25.163]     RedMaskSize: 8
[    25.163]     RedFieldPosition: 16
[    25.163]     GreenMaskSize: 8
[    25.163]     GreenFieldPosition: 8
[    25.163]     BlueMaskSize: 8
[    25.163]     BlueFieldPosition: 0
[    25.163]     RsvdMaskSize: 8
[    25.163]     RsvdFieldPosition: 24
[    25.163]     DirectColorModeInfo: 0
[    25.163]     PhysBasePtr: 0xc1000000
[    25.163]     LinBytesPerScanLine: 5120
[    25.163]     BnkNumberOfImagePages: 1
[    25.163]     LinNumberOfImagePages: 1
[    25.163]     LinRedMaskSize: 8
[    25.163]     LinRedFieldPosition: 16
[    25.163]     LinGreenMaskSize: 8
[    25.163]     LinGreenFieldPosition: 8
[    25.163]     LinBlueMaskSize: 8
[    25.163]     LinBlueFieldPosition: 0
[    25.163]     LinRsvdMaskSize: 8
[    25.163]     LinRsvdFieldPosition: 24
[    25.163]     MaxPixelClock: 229500000
[    25.163] 
[    25.163] (II) VESA(0): Total Memory: 224 64KB banks (14336kB)
[    25.163] (II) VESA(0): Monitor0: Using hsync range of 28.00-33.00 kHz
[    25.163] (II) VESA(0): Monitor0: Using vrefresh range of 43.00-72.00 Hz
[    25.163] (II) VESA(0): Monitor0: Using maximum pixel clock of 155.00 MHz
[    25.163] (WW) VESA(0): Unable to estimate virtual size
[    25.163] (II) VESA(0): Not using built-in mode "1680x1050" (no mode of this name)
[    25.163] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[    25.163] (II) VESA(0): Not using built-in mode "1280x800" (no mode of this name)
[    25.163] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    25.163] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    25.164] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    25.164] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    25.164] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    25.164] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    25.164] (--) VESA(0): Virtual size is 640x480 (pitch 640)
[    25.164] (**) VESA(0): *Built-in mode "640x480"
[    25.164] (**) VESA(0): Display dimensions: (470, 300) mm
[    25.164] (**) VESA(0): DPI set to (34, 40)
[    25.164] (**) VESA(0): Using "Shadow Framebuffer"
[    25.164] (II) Loading sub module "shadow"
[    25.164] (II) LoadModule: "shadow"
[    25.165] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    25.168] (II) Module shadow: vendor="X.Org Foundation"
[    25.168]     compiled for 1.14.5, module version = 1.1.0
[    25.168]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.168] (II) Loading sub module "fb"
[    25.168] (II) LoadModule: "fb"
[    25.168] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.171] (II) Module fb: vendor="X.Org Foundation"
[    25.171]     compiled for 1.14.5, module version = 1.0.0
[    25.171]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.171] (II) UnloadModule: "modesetting"
[    25.171] (II) Unloading modesetting
[    25.172] (II) UnloadModule: "fbdev"
[    25.172] (II) Unloading fbdev
[    25.172] (II) UnloadSubModule: "fbdevhw"
[    25.172] (II) Unloading fbdevhw
[    25.173] (==) Depth 24 pixmap format is 32 bpp
[    25.173] (II) Loading sub module "int10"
[    25.173] (II) LoadModule: "int10"
[    25.173] (II) Loading /usr/lib/xorg/modules/libint10.so
[    25.173] (II) Module int10: vendor="X.Org Foundation"
[    25.173]     compiled for 1.14.5, module version = 1.0.0
[    25.173]     ABI class: X.Org Video Driver, version 14.1
[    25.173] (II) VESA(0): initializing int10
[    25.176] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    25.269] (II) VESA(0): VESA BIOS detected
[    25.269] (II) VESA(0): VESA VBE Version 3.0
[    25.269] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    25.269] (II) VESA(0): VESA VBE OEM: NVIDIA
[    25.269] (II) VESA(0): VESA VBE OEM Software Rev: 128.7
[    25.269] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    25.269] (II) VESA(0): VESA VBE OEM Product: GK107 Board - 20100004
[    25.269] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev
[    25.269] (II) VESA(0): virtual address = 0x7f6590126000,
    physical address = 0xc1000000, size = 14680064
[    25.296] (II) VESA(0): Setting up VESA Mode 0x112 (640x480)
[    25.403] (==) VESA(0): Default visual is TrueColor
[    25.403] (==) VESA(0): Backing store disabled
[    25.403] (**) VESA(0): DPMS enabled
[    25.403] (==) RandR enabled
[    25.410] (II) SELinux: Disabled on system
[    25.411] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    25.423] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.427] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    25.427] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.427] (II) LoadModule: "evdev"
[    25.427] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.430] (II) Module evdev: vendor="X.Org Foundation"
[    25.430]     compiled for 1.14.1, module version = 2.7.3
[    25.430]     Module class: X.Org XInput Driver
[    25.430]     ABI class: X.Org XInput driver, version 19.1
[    25.430] (II) Using input driver 'evdev' for 'Power Button'
[    25.430] (**) Power Button: always reports core events
[    25.430] (**) evdev: Power Button: Device: "/dev/input/event1"
[    25.430] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.430] (--) evdev: Power Button: Found keys
[    25.430] (II) evdev: Power Button: Configuring as keyboard
[    25.430] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    25.430] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    25.430] (**) Option "xkb_rules" "evdev"
[    25.430] (**) Option "xkb_model" "pc105"
[    25.430] (**) Option "xkb_layout" "us"
[    25.431] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    25.431] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.431] (II) Using input driver 'evdev' for 'Power Button'
[    25.431] (**) Power Button: always reports core events
[    25.431] (**) evdev: Power Button: Device: "/dev/input/event0"
[    25.431] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.431] (--) evdev: Power Button: Found keys
[    25.431] (II) evdev: Power Button: Configuring as keyboard
[    25.431] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    25.431] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    25.431] (**) Option "xkb_rules" "evdev"
[    25.431] (**) Option "xkb_model" "pc105"
[    25.431] (**) Option "xkb_layout" "us"
[    25.432] (II) config/udev: Adding input device Microsoft Natural® Ergonomic Keyboard 4000 (/dev/input/event2)
[    25.432] (**) Microsoft Natural® Ergonomic Keyboard 4000: Applying InputClass "evdev keyboard catchall"
[    25.432] (II) Using input driver 'evdev' for 'Microsoft Natural® Ergonomic Keyboard 4000'
[    25.432] (**) Microsoft Natural® Ergonomic Keyboard 4000: always reports core events
[    25.432] (**) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Device: "/dev/input/event2"
[    25.432] (--) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Vendor 0x45e Product 0xdb
[    25.432] (--) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Found keys
[    25.432] (II) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Configuring as keyboard
[    25.432] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input2/event2"
[    25.432] (II) XINPUT: Adding extended input device "Microsoft Natural® Ergonomic Keyboard 4000" (type: KEYBOARD, id 8)
[    25.432] (**) Option "xkb_rules" "evdev"
[    25.432] (**) Option "xkb_model" "pc105"
[    25.432] (**) Option "xkb_layout" "us"
[    25.433] (II) config/udev: Adding input device Microsoft Natural® Ergonomic Keyboard 4000 (/dev/input/event3)
[    25.433] (**) Microsoft Natural® Ergonomic Keyboard 4000: Applying InputClass "evdev keyboard catchall"
[    25.433] (II) Using input driver 'evdev' for 'Microsoft Natural® Ergonomic Keyboard 4000'
[    25.433] (**) Microsoft Natural® Ergonomic Keyboard 4000: always reports core events
[    25.433] (**) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Device: "/dev/input/event3"
[    25.433] (--) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Vendor 0x45e Product 0xdb
[    25.433] (--) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Found 1 mouse buttons
[    25.433] (--) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Found scroll wheel(s)
[    25.433] (--) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Found relative axes
[    25.433] (II) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Forcing relative x/y axes to exist.
[    25.433] (--) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Found absolute axes
[    25.433] (II) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Forcing absolute x/y axes to exist.
[    25.433] (--) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Found keys
[    25.433] (II) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Configuring as mouse
[    25.433] (II) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Configuring as keyboard
[    25.433] (II) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Adding scrollwheel support
[    25.433] (**) evdev: Microsoft Natural® Ergonomic Keyboard 4000: YAxisMapping: buttons 4 and 5
[    25.433] (**) evdev: Microsoft Natural® Ergonomic Keyboard 4000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    25.433] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.1/input/input3/event3"
[    25.433] (II) XINPUT: Adding extended input device "Microsoft Natural® Ergonomic Keyboard 4000" (type: KEYBOARD, id 9)
[    25.433] (**) Option "xkb_rules" "evdev"
[    25.433] (**) Option "xkb_model" "pc105"
[    25.433] (**) Option "xkb_layout" "us"
[    25.433] (II) evdev: Microsoft Natural® Ergonomic Keyboard 4000: initialized for relative axes.
[    25.433] (WW) evdev: Microsoft Natural® Ergonomic Keyboard 4000: ignoring absolute axes.
[    25.434] (**) Microsoft Natural® Ergonomic Keyboard 4000: (accel) keeping acceleration scheme 1
[    25.434] (**) Microsoft Natural® Ergonomic Keyboard 4000: (accel) acceleration profile 0
[    25.434] (**) Microsoft Natural® Ergonomic Keyboard 4000: (accel) acceleration factor: 2.000
[    25.434] (**) Microsoft Natural® Ergonomic Keyboard 4000: (accel) acceleration threshold: 4
[    25.434] (II) config/udev: Adding input device Logitech Logitech RumblePad 2 USB (/dev/input/event4)
[    25.434] (II) No input driver specified, ignoring this device.
[    25.434] (II) This device may have been added with another device file.
[    25.434] (II) config/udev: Adding input device Logitech Logitech RumblePad 2 USB (/dev/input/js0)
[    25.434] (II) No input driver specified, ignoring this device.
[    25.435] (II) This device may have been added with another device file.
[    25.435] (II) config/udev: Adding input device HID 04d9:1135 (/dev/input/event5)
[    25.435] (**) HID 04d9:1135: Applying InputClass "evdev pointer catchall"
[    25.435] (II) Using input driver 'evdev' for 'HID 04d9:1135'
[    25.435] (**) HID 04d9:1135: always reports core events
[    25.435] (**) evdev: HID 04d9:1135: Device: "/dev/input/event5"
[    25.435] (--) evdev: HID 04d9:1135: Vendor 0x4d9 Product 0x1135
[    25.435] (--) evdev: HID 04d9:1135: Found 9 mouse buttons
[    25.435] (--) evdev: HID 04d9:1135: Found scroll wheel(s)
[    25.435] (--) evdev: HID 04d9:1135: Found relative axes
[    25.435] (--) evdev: HID 04d9:1135: Found x and y relative axes
[    25.435] (II) evdev: HID 04d9:1135: Configuring as mouse
[    25.435] (II) evdev: HID 04d9:1135: Adding scrollwheel support
[    25.435] (**) evdev: HID 04d9:1135: YAxisMapping: buttons 4 and 5
[    25.435] (**) evdev: HID 04d9:1135: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    25.435] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.3/1-3.3:1.0/input/input5/event5"
[    25.435] (II) XINPUT: Adding extended input device "HID 04d9:1135" (type: MOUSE, id 10)
[    25.435] (II) evdev: HID 04d9:1135: initialized for relative axes.
[    25.435] (**) HID 04d9:1135: (accel) keeping acceleration scheme 1
[    25.435] (**) HID 04d9:1135: (accel) acceleration profile 0
[    25.436] (**) HID 04d9:1135: (accel) acceleration factor: 2.000
[    25.436] (**) HID 04d9:1135: (accel) acceleration threshold: 4
[    25.436] (II) config/udev: Adding input device HID 04d9:1135 (/dev/input/mouse0)
[    25.436] (II) No input driver specified, ignoring this device.
[    25.436] (II) This device may have been added with another device file.
[    25.436] (II) config/udev: Adding input device UVC Camera (046d:0990) (/dev/input/event6)
[    25.436] (**) UVC Camera (046d:0990): Applying InputClass "evdev keyboard catchall"
[    25.436] (II) Using input driver 'evdev' for 'UVC Camera (046d:0990)'
[    25.436] (**) UVC Camera (046d:0990): always reports core events
[    25.436] (**) evdev: UVC Camera (046d:0990): Device: "/dev/input/event6"
[    25.436] (--) evdev: UVC Camera (046d:0990): Vendor 0x46d Product 0x990
[    25.436] (--) evdev: UVC Camera (046d:0990): Found keys
[    25.436] (II) evdev: UVC Camera (046d:0990): Configuring as keyboard
[    25.436] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4:1.0/input/input6/event6"
[    25.436] (II) XINPUT: Adding extended input device "UVC Camera (046d:0990)" (type: KEYBOARD, id 11)
[    25.436] (**) Option "xkb_rules" "evdev"
[    25.436] (**) Option "xkb_model" "pc105"
[    25.436] (**) Option "xkb_layout" "us"
[    25.437] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event7)
[    25.437] (II) No input driver specified, ignoring this device.
[    25.437] (II) This device may have been added with another device file.
[    25.437] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event8)
[    25.437] (II) No input driver specified, ignoring this device.
[    25.437] (II) This device may have been added with another device file.
[    25.438] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event9)
[    25.438] (II) No input driver specified, ignoring this device.
[    25.438] (II) This device may have been added with another device file.
[    28.280] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.385] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.416] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  3921.830] (II) evdev: UVC Camera (046d:0990): Close
[  3921.831] (II) UnloadModule: "evdev"
[  3921.831] (II) evdev: HID 04d9:1135: Close
[  3921.831] (II) UnloadModule: "evdev"
[  3921.831] (II) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Close
[  3921.831] (II) UnloadModule: "evdev"
[  3921.831] (II) evdev: Microsoft Natural® Ergonomic Keyboard 4000: Close
[  3921.831] (II) UnloadModule: "evdev"
[  3921.831] (II) evdev: Power Button: Close
[  3921.831] (II) UnloadModule: "evdev"
[  3921.831] (II) evdev: Power Button: Close
[  3921.831] (II) UnloadModule: "evdev"
[  3921.840] (EE) Server terminated successfully (0). Closing log file. 

>  lspci00:00.0 Memory controller: NVIDIA Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: NVIDIA Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: NVIDIA Corporation CK804 SMBus (rev a2)
00:02.0 USB controller: NVIDIA Corporation CK804 USB Controller (rev a2)
00:02.1 USB controller: NVIDIA Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: NVIDIA Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: NVIDIA Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: NVIDIA Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: NVIDIA Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: NVIDIA Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: NVIDIA Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GTX 650] (rev a1)
02:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)
05:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
05:08.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
05:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
05:0a.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)




my lshw command
>  paulspc    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall32
    configuration: boot=normal chassis=desktop uuid=0019FB04-5F1D-D711-8C57-0013D46A06B2
  *-core
       description: Motherboard
       product: A8N-SLI Premium
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.02
       serial: 123456789000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS A8N-SLI Premium ACPI BIOS Revision 1303
          date: 08/10/2006
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          slot: Socket 939
          size: 2200MHz
          capacity: 3700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good nopl pni lahf_lm cmp_legacy
        *-cache:0
             description: L1 cache
             physical id: a
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: b
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 43
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-10-12 13:19+0000X-Generator: Launchpad (build 16799) 333 MHz (3.0 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-10-12 13:19+0000X-Generator: Launchpad (build 16799) 333 MHz (3.0 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-10-12 13:19+0000X-Generator: Launchpad (build 16799) 333 MHz (3.0 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-10-12 13:19+0000X-Generator: Launchpad (build 16799) 333 MHz (3.0 ns)
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
          resources: irq:5 ioport:e400(size=32) ioport:4c00(size=64) ioport:4c40(size=64)
     *-usb:0
          description: USB controller
          product: CK804 USB Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:d5004000-d5004fff
     *-usb:1
          description: USB controller
          product: CK804 USB Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:d5005000-d50050ff
     *-multimedia
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=snd_intel8x0 latency=0 maxlatency=5 mingnt=2
          resources: irq:22 ioport:dc00(size=256) ioport:e000(size=256) memory:d5003000-d5003fff
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d800(size=16) memory:d5002000-d5002fff
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:c400(size=16) memory:d5001000-d5001fff
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
          resources: ioport:8000(size=8192) memory:d3000000-d4ffffff memory:d5100000-d51fffff
        *-multimedia
             description: Multimedia audio controller
             product: SB Audigy
             vendor: Creative Labs
             physical id: 8
             bus info: pci@0000:05:08.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_emu10k1 latency=32 maxlatency=20 mingnt=2
             resources: irq:18 ioport:8000(size=64)
        *-input
             description: Input device controller
             product: SB Audigy Game Port
             vendor: Creative Labs
             physical id: 8.1
             bus info: pci@0000:05:08.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Emu10k1_gameport latency=32
             resources: irq:0 ioport:8400(size=8)
        *-firewire:0
             description: FireWire (IEEE 1394)
             product: SB Audigy FireWire Port
             vendor: Creative Labs
             physical id: 8.2
             bus info: pci@0000:05:08.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
             resources: irq:19 memory:d400e000-d400e7ff memory:d4000000-d4003fff
        *-storage
             description: RAID bus controller
             product: SiI 3114 [SATALink/SATARaid] Serial ATA Controller
             vendor: Silicon Image, Inc.
             physical id: a
             bus info: pci@0000:05:0a.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list rom
             configuration: driver=sata_sil latency=32
             resources: irq:19 ioport:8800(size=8) ioport:8c00(size=4) ioport:9000(size=8) ioport:9400(size=4) ioport:9800(size=16) memory:d400d000-d400d3ff memory:d3000000-d307ffff
        *-firewire:1
             description: FireWire (IEEE 1394)
             product: TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
             vendor: Texas Instruments
             physical id: b
             bus info: pci@0000:05:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
             resources: irq:16 memory:d400c000-d400c7ff memory:d4004000-d4007fff
        *-network
             description: Ethernet interface
             product: 88E8001 Gigabit Ethernet Controller
             vendor: Marvell Technology Group Ltd.
             physical id: c
             bus info: pci@0000:05:0c.0
             logical name: eth0
             version: 13
             serial: 00:13:d4:6a:11:a2
             capacity: 1Gbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.14 latency=32 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
             resources: irq:17 memory:d4008000-d400bfff ioport:9c00(size=256) memory:d5100000-d511ffff
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: NVIDIA Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth1
          version: f3
          serial: 00:13:d4:6a:06:b2
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.4 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:23 memory:d5000000-d5000fff ioport:b000(size=8)
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: f3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: f3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: f3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42 ioport:a000(size=4096) memory:d0000000-d2ffffff ioport:b0000000(size=536870912)
        *-display
             description: VGA compatible controller
             product: GK107 [GeForce GTX 650]
             vendor: NVIDIA Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:19 memory:d0000000-d0ffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:a000(size=128) memory:d1000000-d107ffff
        *-multimedia
             description: Audio device
             product: GK107 HDMI Audio Controller
             vendor: NVIDIA Corporation
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:16 memory:d2000000-d2003fff
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: NVIDIA Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:43
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: f
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST31000528AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: CC38
             serial: 9VP4YDMB
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0006eabf
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: 28ed2aad-c80f-4207-ba1c-96daf6fed618
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable ext2 initialized
                configuration: filesystem=ext2 modified=2014-03-02 22:02:07 mount.fstype=ext2 mount.options=rw,relatime,errors=continue state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 931GiB
                capacity: 931GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux LVM Physical Volume partition
                   physical id: 5
                   logical name: /dev/sda5
                   serial: GzOlyK-782K-j030-MNvR-sTxC-ZW3k-rtR38A
                   size: 931GiB
                   capacity: 931GiB
                   capabilities: multi lvm2
     *-scsi:1
          physical id: 10
          bus info: usb@1:3.1
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@8:0.0.1
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@8:0.0.2
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@8:0.0.3
             logical name: /dev/sde
             configuration: sectorsize=512
     *-scsi:2
          physical id: 11
          logical name: scsi9
          capabilities: emulated
        *-cdrom:0
             description: DVD writer
             product: DVD-RW  DVR-109
             vendor: PIONEER
             physical id: 0.0.0
             bus info: scsi@9:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.58
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
        *-cdrom:1
             description: CD-R/CD-RW writer
             product: LTR-52246S
             vendor: LITE-ON
             physical id: 0.1.0
             bus info: scsi@9:0.1.0
             logical name: /dev/sr1
             version: 6S0F
             capabilities: removable audio cd-r cd-rw
             configuration: ansiversion=5 status=nodisc 

---

### Post by mörgæs on 2014-03-02
Please change your QUOTE tags to CODE. The output is hard to read.

---

### Post by jeanjd63 on 2014-03-03
Hello
You can try to open a console (CTRL+ALT+F1), connect with your user/password and do :
[B]sudo  apt-get  purge  "nvidia *"
sudo  apt-get  install  nvidia-current
sudo  reboot[/B]

---

