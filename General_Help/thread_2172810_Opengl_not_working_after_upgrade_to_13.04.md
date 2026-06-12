---
title: "Opengl not working after upgrade to 13.04"
date: 2013-09-06
forum: General Help
---

### Post by Corey Goettsch on 2013-09-06
Hello,

I recently upgraded from Ubuntu 12.10 to 13.04.  When I tried to start Unity, I could get the wallpaper and some icons but no unity.  When I tried to start Gnome 3, I went straight to fallback mode.  I tried to reset Unity as some had suggested when Unity failed to work after upgrading.  However, this is terminal output I got: 

nicholas@nicholas-Inspiron-1545:~$ compiz --replace ccp
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
Segmentation fault (core dumped)
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
Segmentation fault (core dumped)
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
Compiz (opengl) - Fatal: No valid GL extensions string found.
compiz (core) - Error: Plugin initScreen failed: opengl
compiz (core) - Error: Failed to start plugin: opengl
compiz (core) - Info: Unloading plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
Segmentation fault (core dumped)
nicholas@nicholas-Inspiron-1545:~$ 

When I ran the Unity test, I got this error: 

nicholas@nicholas-Inspiron-1545:~$ /usr/lib/nux/unity_support_test -p
Error: invalid OpenGL extensions string
Segmentation fault (core dumped)
nicholas@nicholas-Inspiron-1545:~$

When I try to run graphics-intensive games, they don't open.  When I tried to open EDGE, it said OpenGL could not be initialized.  

I've been running MATE, but I'd like to use Unity, and I'd like to use graphics-intensive games again.  I would appreciate any help.  Thank you!

Sincerely,

Corey Goettsch

---

### Post by crazymonkey05 on 2013-09-06
well idk if you can tell but obviously 13.04 cant link the openGL string to your graphics card and there for anything graphically intensive will be rendered by software and that's probably why your games close? what graphics card are you using? also try downgrading your openGL version and maybe even your kernel.

---

### Post by Impavidus on 2013-09-06
It could be that 13.04 doesn't have a good driver for your graphics card, or that you use a proprietary driver not designed for 13.04. In either case, try activating a different driver. What graphics card do you have?

---

### Post by Corey Goettsch on 2013-09-06
My computer has Intel integrated graphics, and my chipset is an Intel G45.  I've been using the Intel drivers.  Which driver would you suggest?  Thanks for your help.

---

### Post by Impavidus on 2013-09-06
Interesting. Intel should work out of the box, so something else may be the problem.

---

### Post by Corey Goettsch on 2013-09-09
Any idea what that might be?  Is it a kernel issue?

---

### Post by Corey Goettsch on 2013-09-09
So, I figured I'd do a bit more digging around.  After I booted up into Unity (which was broken as always), I opened up kern.log through through a terminal, and I found these error codes:

Sep  9 11:18:37 nicholas-Inspiron-1545 kernel: [   69.683722] check_gl_textur[3182]: segfault at 8 ip 00007f7cc0d589c6 sp 00007fffff9b7640 error 4 in libdricore9.1.4.so.1.0.0[7f7cc0c86000+39e000]
Sep  9 11:18:39 nicholas-Inspiron-1545 kernel: [   71.962239] unity_support_t[3235]: segfault at 4e8 ip 00007fe36496f48e sp 00007fff54d4e800 error 4 in libdricore9.1.4.so.1.0.0[7fe36484a000+39e000]
Sep  9 11:18:40 nicholas-Inspiron-1545 kernel: [   72.741769] unity_support_t[3262]: segfault at 4e8 ip 00007f5300dd348e sp 00007fff51860f80 error 4 in libdricore9.1.4.so.1.0.0[7f5300cae000+39e000]
Sep  9 11:18:40 nicholas-Inspiron-1545 kernel: [   73.105481] compiz[3185]: segfault at 4e8 ip 00007f97ad56c48e sp 00007fff9f3eaf60 error 4 in libdricore9.1.4.so.1.0.0[7f97ad447000+39e000]

and I also found this one:

Sep  9 11:18:47 nicholas-Inspiron-1545 kernel: [   80.181104] unity_support_t[3309]: segfault at 4e8 ip 00007f031e93648e sp 00007fff01d9fb70 error 4 in libdricore9.1.4.so.1.0.0[7f031e811000+39e000]
Sep  9 11:18:48 nicholas-Inspiron-1545 kernel: [   80.447901] unity_support_t[3314]: segfault at 4e8 ip 00007ff7b6af348e sp 00007fff2e2d6350 error 4 in libdricore9.1.4.so.1.0.0[7ff7b69ce000+39e000]
Sep  9 11:18:48 nicholas-Inspiron-1545 kernel: [   80.704642] compiz[3297]: segfault at 4e8 ip 00007f9cc4ff348e sp 00007fff97c90040 error 4 in libdricore9.1.4.so.1.0.0[7f9cc4ece000+39e000]

When I try to open EDGE (a 3D game), a similar error code comes up in kern.log: 

Sep  9 11:08:41 nicholas-Inspiron-1545 kernel: [  991.581543] EDGE.bin[3737]: segfault at 4e8 ip 00007ff4f1ef548e sp 00007ffffe82e630 error 4 in libdricore9.1.4.so.1.0.0[7ff4f1dd0000+39e000]

I honestly have no idea what lidricore is, nor do I have know what error 4 is.  Does this further clarify my issues?

---

### Post by Yellow Pasque on 2013-09-09
Post your /var/log/Xorg.0.log (use [ code ][ /code ] tags)

---

### Post by Corey Goettsch on 2013-09-09
Here it is: 

[    45.946] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    45.946] X Protocol Version 11, Revision 0
[    45.946] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    45.946] Current Operating System: Linux nicholas-Inspiron-1545 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:52:24 UTC 2013 x86_64
[    45.946] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-30-generic root=UUID=aeb9d028-0f92-4af8-9855-666c99a2932a ro crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7
[    45.946] Build Date: 17 April 2013  10:43:13PM
[    45.946] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    45.946] Current version of pixman: 0.28.2
[    45.946]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    45.946] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    45.946] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep  9 12:54:52 2013
[    45.993] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    45.993] (==) No Layout section.  Using the first Screen section.
[    45.993] (==) No screen section available. Using defaults.
[    45.993] (**) |-->Screen "Default Screen Section" (0)
[    45.993] (**) |   |-->Monitor "<default monitor>"
[    45.993] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    45.993] (==) Automatically adding devices
[    45.993] (==) Automatically enabling devices
[    45.993] (==) Automatically adding GPU devices
[    45.993] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    45.993]     Entry deleted from font path.
[    45.993] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    45.993]     Entry deleted from font path.
[    45.994] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    45.994]     Entry deleted from font path.
[    45.994] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    45.994] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    45.994] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    45.994] (II) Loader magic: 0x7f2ddd04bd20
[    45.994] (II) Module ABI versions:
[    45.994]     X.Org ANSI C Emulation: 0.4
[    45.994]     X.Org Video Driver: 13.1
[    45.994]     X.Org XInput driver : 18.0
[    45.994]     X.Org Server Extension : 7.0
[    45.994] (II) config/udev: Adding drm device (/dev/dri/card0)
[    45.996] (--) PCI:*(0:0:2:0) 8086:2a42:1028:02aa rev 7, Mem @ 0xf6c00000/4194304, 0xe0000000/268435456, I/O @ 0x0000efe8/8
[    45.996] (--) PCI: (0:0:2:1) 8086:2a43:1028:02aa rev 7, Mem @ 0xf6b00000/1048576
[    45.997] (II) Open ACPI successful (/var/run/acpid.socket)
[    45.997] Initializing built-in extension Generic Event Extension
[    45.997] Initializing built-in extension SHAPE
[    45.997] Initializing built-in extension MIT-SHM
[    45.997] Initializing built-in extension XInputExtension
[    45.997] Initializing built-in extension XTEST
[    45.997] Initializing built-in extension BIG-REQUESTS
[    45.997] Initializing built-in extension SYNC
[    45.997] Initializing built-in extension XKEYBOARD
[    45.997] Initializing built-in extension XC-MISC
[    45.997] Initializing built-in extension SECURITY
[    45.997] Initializing built-in extension XINERAMA
[    45.997] Initializing built-in extension XFIXES
[    45.997] Initializing built-in extension RENDER
[    45.997] Initializing built-in extension RANDR
[    45.997] Initializing built-in extension COMPOSITE
[    45.997] Initializing built-in extension DAMAGE
[    45.997] Initializing built-in extension MIT-SCREEN-SAVER
[    45.997] Initializing built-in extension DOUBLE-BUFFER
[    45.997] Initializing built-in extension RECORD
[    45.997] Initializing built-in extension DPMS
[    45.997] Initializing built-in extension X-Resource
[    45.997] Initializing built-in extension XVideo
[    45.997] Initializing built-in extension XVideo-MotionCompensation
[    45.997] Initializing built-in extension SELinux
[    45.997] Initializing built-in extension XFree86-VidModeExtension
[    45.997] Initializing built-in extension XFree86-DGA
[    45.997] Initializing built-in extension XFree86-DRI
[    45.997] Initializing built-in extension DRI2
[    45.997] (II) LoadModule: "glx"
[    46.149] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    46.149] (II) Module glx: vendor="X.Org Foundation"
[    46.149]     compiled for 1.13.3, module version = 1.0.0
[    46.149]     ABI class: X.Org Server Extension, version 7.0
[    46.149] (==) AIGLX enabled
[    46.150] Loading extension GLX
[    46.150] (==) Matched intel as autoconfigured driver 0
[    46.150] (==) Matched intel as autoconfigured driver 1
[    46.150] (==) Matched vesa as autoconfigured driver 2
[    46.150] (==) Matched modesetting as autoconfigured driver 3
[    46.150] (==) Matched fbdev as autoconfigured driver 4
[    46.150] (==) Assigned the driver to the xf86ConfigLayout
[    46.150] (II) LoadModule: "intel"
[    46.194] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    46.270] (II) Module intel: vendor="X.Org Foundation"
[    46.270]     compiled for 1.13.3, module version = 2.21.9
[    46.270]     Module class: X.Org Video Driver
[    46.270]     ABI class: X.Org Video Driver, version 13.1
[    46.270] (II) LoadModule: "vesa"
[    46.270] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    46.271] (II) Module vesa: vendor="X.Org Foundation"
[    46.271]     compiled for 1.12.99.902, module version = 2.3.2
[    46.271]     Module class: X.Org Video Driver
[    46.271]     ABI class: X.Org Video Driver, version 13.0
[    46.271] (II) LoadModule: "modesetting"
[    46.271] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    46.271] (II) Module modesetting: vendor="X.Org Foundation"
[    46.271]     compiled for 1.13.3, module version = 0.7.0
[    46.271]     Module class: X.Org Video Driver
[    46.271]     ABI class: X.Org Video Driver, version 13.1
[    46.271] (II) LoadModule: "fbdev"
[    46.271] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    46.271] (II) Module fbdev: vendor="X.Org Foundation"
[    46.271]     compiled for 1.12.99.902, module version = 0.4.3
[    46.271]     Module class: X.Org Video Driver
[    46.271]     ABI class: X.Org Video Driver, version 13.0
[    46.271] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), HD Graphics, HD Graphics 4600,
    Haswell Desktop (GT3), HD Graphics, HD Graphics 4600,
    Haswell Mobile (GT3), HD Graphics, HD Graphics P4600/P4700,
    Haswell Server (GT3), Haswell (GT1), Haswell (GT2), Haswell (GT3),
    HD Graphics, Haswell (GT2), Haswell (GT3), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT3),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT3), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT3),
    Haswell SDV (GT1), Haswell SDV (GT2), Haswell SDV (GT3),
    Haswell SDV (GT1), Haswell SDV (GT2), Haswell SDV (GT3),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Iris(TM) Graphics 5100, HD Graphics, HD Graphics 4400,
    HD Graphics 5000, Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Iris(TM) Graphics 5100, Haswell ULT (GT1), Haswell ULT (GT2),
    Iris(TM) Graphics 5100, HD Graphics, HD Graphics 4200,
    Iris(TM) Graphics 5100, Haswell CRW Desktop (GT1), HD Graphics 4600,
    Iris(TM) Pro Graphics 5200, Haswell CRW Mobile (GT1),
    HD Graphics 4600, Iris(TM) Pro Graphics 5200,
    Haswell CRW Server (GT1), Haswell CRW Server (GT2),
    Iris(TM) Pro Graphics 5200, Haswell CRW (GT1), Haswell CRW (GT2),
    Iris(TM) Pro Graphics 5200, Haswell CRW (GT1), Haswell CRW (GT2),
    Iris(TM) Pro Graphics 5200, ValleyView PO board
[    46.273] (II) VESA: driver for VESA chipsets: vesa
[    46.273] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    46.273] (II) FBDEV: driver for framebuffer: fbdev
[    46.273] (++) using VT number 7

[    46.276] (WW) Falling back to old probe method for vesa
[    46.276] (WW) Falling back to old probe method for modesetting
[    46.276] (WW) Falling back to old probe method for fbdev
[    46.276] (II) Loading sub module "fbdevhw"
[    46.276] (II) LoadModule: "fbdevhw"
[    46.276] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    46.277] (II) Module fbdevhw: vendor="X.Org Foundation"
[    46.277]     compiled for 1.13.3, module version = 0.0.2
[    46.277]     ABI class: X.Org Video Driver, version 13.1
[    46.277] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    46.277] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    46.277] (==) intel(0): RGB weight 888
[    46.277] (==) intel(0): Default visual is TrueColor
[    46.277] (--) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[    46.312] (**) intel(0): Relaxed fencing enabled
[    46.312] (**) intel(0): Wait on SwapBuffers? enabled
[    46.312] (**) intel(0): Triple buffering? enabled
[    46.312] (**) intel(0): Framebuffer tiled
[    46.312] (**) intel(0): Pixmaps tiled
[    46.312] (**) intel(0): 3D buffers tiled
[    46.312] (**) intel(0): SwapBuffers wait enabled
[    46.312] (==) intel(0): video overlay key set to 0x101fe
[    46.312] (II) intel(0): Output LVDS1 has no monitor section
[    46.315] (--) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    46.344] (II) intel(0): Output VGA1 has no monitor section
[    46.392] (II) intel(0): Output DP1 has no monitor section
[    46.392] (II) intel(0): EDID for output LVDS1
[    46.392] (II) intel(0): Manufacturer: LGD  Model: 6e01  Serial#: 0
[    46.392] (II) intel(0): Year: 2008  Week: 0
[    46.392] (II) intel(0): EDID Version: 1.3
[    46.392] (II) intel(0): Digital Display Input
[    46.392] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    46.392] (II) intel(0): Gamma: 2.20
[    46.392] (II) intel(0): No DPMS capabilities specified
[    46.392] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    46.392] (II) intel(0): First detailed timing is preferred mode
[    46.392] (II) intel(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
[    46.392] (II) intel(0): blueX: 0.000 blueY: 0.000   whiteX: 0.312 whiteY: 0.328
[    46.392] (II) intel(0): Manufacturer's mask: 0
[    46.392] (II) intel(0): Supported detailed timing:
[    46.392] (II) intel(0): clock: 72.3 MHz   Image Size:  344 x 194 mm
[    46.392] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    46.392] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    46.392] (II) intel(0): Supported detailed timing:
[    46.392] (II) intel(0): clock: 72.3 MHz   Image Size:  344 x 194 mm
[    46.392] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    46.392] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    46.392] (II) intel(0):  J553H\80156WH1
[    46.392] (II) intel(0): Unknown vendor-specific block 0
[    46.392] (II) intel(0): EDID (in hex):
[    46.392] (II) intel(0):     00ffffffffffff0030e4016e00000000
[    46.392] (II) intel(0):     00120103802213780a00000000000000
[    46.392] (II) intel(0):     00505400000001010101010101010101
[    46.392] (II) intel(0):     0101010101013e1c56a0500016303020
[    46.392] (II) intel(0):     350058c2100000193e1c56a050001630
[    46.392] (II) intel(0):     3020350058c210000019000000fe004a
[    46.392] (II) intel(0):     35353348803135365748310a00000000
[    46.392] (II) intel(0):     00ffffffffffffffff01010a202000bf
[    46.392] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    46.392] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    46.393] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    46.393] (II) intel(0): Printing probed modes for output LVDS1
[    46.393] (II) intel(0): Modeline "1366x768"x60.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz eP)
[    46.393] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    46.393] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    46.393] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    46.393] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    46.393] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    46.393] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    46.416] (II) intel(0): EDID for output VGA1
[    46.464] (II) intel(0): EDID for output DP1
[    46.464] (II) intel(0): Output LVDS1 connected
[    46.464] (II) intel(0): Output VGA1 disconnected
[    46.464] (II) intel(0): Output DP1 disconnected
[    46.464] (II) intel(0): Using exact sizes for initial modes
[    46.464] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    46.464] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    46.464] (II) intel(0): Kernel page flipping support detected, enabling
[    46.464] (==) intel(0): DPI set to (96, 96)
[    46.464] (II) Loading sub module "fb"
[    46.464] (II) LoadModule: "fb"
[    46.464] (II) Loading /usr/lib/xorg/modules/libfb.so
[    46.540] (II) Module fb: vendor="X.Org Foundation"
[    46.540]     compiled for 1.13.3, module version = 1.0.0
[    46.540]     ABI class: X.Org ANSI C Emulation, version 0.4
[    46.540] (II) Loading sub module "dri2"
[    46.540] (II) LoadModule: "dri2"
[    46.540] (II) Module "dri2" already built-in
[    46.540] (II) UnloadModule: "vesa"
[    46.541] (II) Unloading vesa
[    46.541] (II) UnloadModule: "modesetting"
[    46.541] (II) Unloading modesetting
[    46.541] (II) UnloadModule: "fbdev"
[    46.541] (II) Unloading fbdev
[    46.541] (II) UnloadSubModule: "fbdevhw"
[    46.541] (II) Unloading fbdevhw
[    46.541] (==) Depth 24 pixmap format is 32 bpp
[    46.541] (II) intel(0): [DRI2] Setup complete
[    46.541] (II) intel(0): [DRI2]   DRI driver: i965
[    46.541] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    46.552] (II) UXA(0): Driver registered support for the following operations:
[    46.552] (II)         solid
[    46.552] (II)         copy
[    46.552] (II)         composite (RENDER acceleration)
[    46.552] (II)         put_image
[    46.552] (II)         get_image
[    46.552] (==) intel(0): Backing store disabled
[    46.552] (==) intel(0): Silken mouse enabled
[    46.552] (II) intel(0): Initializing HW Cursor
[    46.552] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    46.560] (==) intel(0): DPMS enabled
[    46.560] (==) intel(0): Intel XvMC decoder enabled
[    46.560] (II) intel(0): Set up textured video
[    46.560] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    46.560] (II) intel(0): direct rendering: DRI2 Enabled
[    46.560] (==) intel(0): hotplug detection: "enabled"
[    46.588] (--) RandR disabled
[    46.593] (II) SELinux: Disabled on system
[    47.064] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    47.064] (II) AIGLX: enabled GLX_INTEL_swap_event
[    47.064] (II) AIGLX: enabled GLX_ARB_create_context
[    47.064] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    47.064] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    47.064] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    47.064] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    47.064] (II) AIGLX: Loaded and initialized i965
[    47.064] (II) GLX: Initialized DRI2 GL provider for screen 0
[    47.065] (II) intel(0): Setting screen physical size to 361 x 203
[    47.077] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    47.080] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    47.080] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    47.080] (II) LoadModule: "evdev"
[    47.080] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    47.138] (II) Module evdev: vendor="X.Org Foundation"
[    47.138]     compiled for 1.13.3, module version = 2.7.3
[    47.138]     Module class: X.Org XInput Driver
[    47.138]     ABI class: X.Org XInput driver, version 18.0
[    47.138] (II) Using input driver 'evdev' for 'Video Bus'
[    47.138] (**) Video Bus: always reports core events
[    47.138] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    47.138] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    47.138] (--) evdev: Video Bus: Found keys
[    47.138] (II) evdev: Video Bus: Configuring as keyboard
[    47.138] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input6/event6"
[    47.138] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[    47.138] (**) Option "xkb_rules" "evdev"
[    47.138] (**) Option "xkb_model" "pc105"
[    47.138] (**) Option "xkb_layout" "us"
[    47.139] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    47.139] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    47.139] (II) Using input driver 'evdev' for 'Power Button'
[    47.139] (**) Power Button: always reports core events
[    47.139] (**) evdev: Power Button: Device: "/dev/input/event1"
[    47.139] (--) evdev: Power Button: Vendor 0 Product 0x1
[    47.139] (--) evdev: Power Button: Found keys
[    47.139] (II) evdev: Power Button: Configuring as keyboard
[    47.139] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    47.139] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    47.139] (**) Option "xkb_rules" "evdev"
[    47.139] (**) Option "xkb_model" "pc105"
[    47.139] (**) Option "xkb_layout" "us"
[    47.139] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    47.139] (II) No input driver specified, ignoring this device.
[    47.139] (II) This device may have been added with another device file.
[    47.140] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    47.140] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    47.140] (II) Using input driver 'evdev' for 'Sleep Button'
[    47.140] (**) Sleep Button: always reports core events
[    47.140] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    47.140] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    47.140] (--) evdev: Sleep Button: Found keys
[    47.140] (II) evdev: Sleep Button: Configuring as keyboard
[    47.140] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    47.140] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    47.140] (**) Option "xkb_rules" "evdev"
[    47.140] (**) Option "xkb_model" "pc105"
[    47.140] (**) Option "xkb_layout" "us"
[    47.140] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    47.140] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    47.141] (II) config/udev: Adding input device Integrated_Webcam_1.3M (/dev/input/event9)
[    47.141] (**) Integrated_Webcam_1.3M: Applying InputClass "evdev keyboard catchall"
[    47.141] (II) Using input driver 'evdev' for 'Integrated_Webcam_1.3M'
[    47.141] (**) Integrated_Webcam_1.3M: always reports core events
[    47.141] (**) evdev: Integrated_Webcam_1.3M: Device: "/dev/input/event9"
[    47.141] (--) evdev: Integrated_Webcam_1.3M: Vendor 0xc45 Product 0x63ee
[    47.141] (--) evdev: Integrated_Webcam_1.3M: Found keys
[    47.141] (II) evdev: Integrated_Webcam_1.3M: Configuring as keyboard
[    47.141] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input9/event9"
[    47.141] (II) XINPUT: Adding extended input device "Integrated_Webcam_1.3M" (type: KEYBOARD, id 9)
[    47.141] (**) Option "xkb_rules" "evdev"
[    47.141] (**) Option "xkb_model" "pc105"
[    47.141] (**) Option "xkb_layout" "us"
[    47.141] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event10)
[    47.141] (II) No input driver specified, ignoring this device.
[    47.141] (II) This device may have been added with another device file.
[    47.142] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event11)
[    47.142] (II) No input driver specified, ignoring this device.
[    47.142] (II) This device may have been added with another device file.
[    47.142] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[    47.142] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    47.142] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    47.142] (**) Logitech USB Receiver: always reports core events
[    47.142] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event4"
[    47.142] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc51b
[    47.142] (--) evdev: Logitech USB Receiver: Found 12 mouse buttons
[    47.142] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    47.142] (--) evdev: Logitech USB Receiver: Found relative axes
[    47.142] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[    47.142] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    47.142] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    47.142] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    47.142] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    47.142] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input4/event4"
[    47.142] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 10)
[    47.142] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    47.143] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    47.143] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    47.143] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    47.143] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    47.143] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    47.143] (II) No input driver specified, ignoring this device.
[    47.143] (II) This device may have been added with another device file.
[    47.143] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    47.143] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    47.143] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    47.143] (**) AT Translated Set 2 keyboard: always reports core events
[    47.143] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    47.143] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    47.143] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    47.143] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    47.143] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    47.143] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    47.143] (**) Option "xkb_rules" "evdev"
[    47.143] (**) Option "xkb_model" "pc105"
[    47.143] (**) Option "xkb_layout" "us"
[    47.144] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event7)
[    47.144] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    47.144] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    47.144] (**) PS/2 Mouse: always reports core events
[    47.144] (**) evdev: PS/2 Mouse: Device: "/dev/input/event7"
[    47.144] (--) evdev: PS/2 Mouse: Vendor 0x2 Product 0x8
[    47.144] (--) evdev: PS/2 Mouse: Found 3 mouse buttons
[    47.144] (--) evdev: PS/2 Mouse: Found relative axes
[    47.144] (--) evdev: PS/2 Mouse: Found x and y relative axes
[    47.144] (II) evdev: PS/2 Mouse: Configuring as mouse
[    47.144] (**) evdev: PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    47.144] (**) evdev: PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    47.144] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input7/event7"
[    47.144] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE, id 12)
[    47.144] (II) evdev: PS/2 Mouse: initialized for relative axes.
[    47.144] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    47.144] (**) PS/2 Mouse: (accel) acceleration profile 0
[    47.144] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    47.144] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    47.145] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
[    47.145] (II) No input driver specified, ignoring this device.
[    47.145] (II) This device may have been added with another device file.
[    47.145] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event8)
[    47.145] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    47.145] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    47.145] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "Default clickpad buttons"
[    47.145] (II) LoadModule: "synaptics"
[    47.145] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    47.145] (II) Module synaptics: vendor="X.Org Foundation"
[    47.145]     compiled for 1.13.1.901, module version = 1.6.2
[    47.145]     Module class: X.Org XInput Driver
[    47.146]     ABI class: X.Org XInput driver, version 18.0
[    47.146] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    47.146] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    47.146] (**) Option "Device" "/dev/input/event8"
[    47.146] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    47.146] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    47.146] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    47.146] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[    47.146] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    47.146] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[    47.146] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[    47.146] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    47.146] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    47.148] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input8/event8"
[    47.148] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 13)
[    47.148] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    47.148] (**) synaptics: AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    47.148] (**) synaptics: AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    47.148] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    47.148] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    47.148] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    47.148] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    47.148] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    47.148] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
[    47.148] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[    47.151] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event5)
[    47.151] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    47.151] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    47.151] (**) Dell WMI hotkeys: always reports core events
[    47.151] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event5"
[    47.151] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    47.151] (--) evdev: Dell WMI hotkeys: Found keys
[    47.151] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    47.151] (**) Option "config_info" "udev:/sys/devices/virtual/input/input5/event5"
[    47.151] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 14)
[    47.151] (**) Option "xkb_rules" "evdev"
[    47.151] (**) Option "xkb_model" "pc105"
[    47.151] (**) Option "xkb_layout" "us"
[    49.930] (II) intel(0): EDID vendor "LGD", prod id 28161
[    49.930] (II) intel(0): Printing DDC gathered Modelines:
[    49.930] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz eP)
[    52.329] (II) intel(0): EDID vendor "LGD", prod id 28161
[    52.329] (II) intel(0): Printing DDC gathered Modelines:
[    52.329] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz eP)
[    67.664] (II) intel(0): EDID vendor "LGD", prod id 28161
[    67.664] (II) intel(0): Printing DDC gathered Modelines:
[    67.664] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz eP)
[    69.390] (II) intel(0): EDID vendor "LGD", prod id 28161
[    69.390] (II) intel(0): Printing DDC gathered Modelines:
[    69.390] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz eP)
[    70.252] (II) intel(0): EDID vendor "LGD", prod id 28161
[    70.252] (II) intel(0): Printing DDC gathered Modelines:
[    70.252] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz eP)
[    79.716] (II) intel(0): EDID vendor "LGD", prod id 28161
[    79.716] (II) intel(0): Printing DDC gathered Modelines:
[    79.716] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz eP)

---

### Post by Corey Goettsch on 2013-09-12
Does /var/log/Xorg.0.log say anything useful here?

---

### Post by Corey Goettsch on 2013-09-12
This also happened when I ran the unity support test today.  

nicholas@nicholas-Inspiron-1545:~$ /usr/lib/nux/unity_support_test -p
Error: invalid OpenGL extensions string
Segmentation fault (core dumped)

---

### Post by Corey Goettsch on 2013-09-12
When I ran glxinfo, I got this: 

nicholas@nicholas-Inspiron-1545:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: i915
nicholas@nicholas-Inspiron-1545:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_multisample, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: (null)
OpenGL renderer string: (null)
OpenGL version string: (null)
Segmentation fault (core dumped)
nicholas@nicholas-Inspiron-1545:~$

---

### Post by Yellow Pasque on 2013-09-12
The xorg log looks good, so I'm stumped. Maybe libgl.so is borked. Try reinstalling:
```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
```
Then log out and in. If that doesn't work, maybe glxinfo will give more detailed info with:
```
export LIBGL_DEBUG=verbose; glxinfo
```

---

### Post by Corey Goettsch on 2013-09-13
Thanks for getting back to me, Temujin.  I appreciate it.  So, I tried reinstalling those packages as you suggested. It did not fix the problem.  I saved the terminal output, as there seemed to be some oddities in it: 

nicholas@nicholas-Inspiron-1545:~$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
[sudo] password for nicholas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  couchdb-bin e17-data erlang-asn1 erlang-base erlang-crypto erlang-eunit
  erlang-inets erlang-mnesia erlang-os-mon erlang-public-key
  erlang-runtime-tools erlang-snmp erlang-ssl erlang-syntax-tools erlang-tools
  erlang-webtool erlang-xmerl hal hal-info libedbus1 libefreet1
  libhal-storage1 libjs-jquery-form libsctp1 lksctp-tools python-avahi
  python-clamav python-couchdb python-nautilus python-pyclamav qemu
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 4 reinstalled, 0 to remove and 2 not upgraded.
Need to get 0 B/6,940 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 412815 files and directories currently installed.)
Preparing to replace libgl1-mesa-dri:amd64 9.1.4-0ubuntu0.1 (using .../libgl1-mesa-dri_9.1.4-0ubuntu0.1_amd64.deb) ...
Unpacking replacement libgl1-mesa-dri:amd64 ...
Preparing to replace libgl1-mesa-dri:i386 9.1.4-0ubuntu0.1 (using .../libgl1-mesa-dri_9.1.4-0ubuntu0.1_i386.deb) ...
Unpacking replacement libgl1-mesa-dri:i386 ...
Preparing to replace libgl1-mesa-glx:amd64 9.1.4-0ubuntu0.1 (using .../libgl1-mesa-glx_9.1.4-0ubuntu0.1_amd64.deb) ...
Unpacking replacement libgl1-mesa-glx:amd64 ...
Preparing to replace libgl1-mesa-glx:i386 9.1.4-0ubuntu0.1 (using .../libgl1-mesa-glx_9.1.4-0ubuntu0.1_i386.deb) ...
Unpacking replacement libgl1-mesa-glx:i386 ...
Setting up libgl1-mesa-dri:amd64 (9.1.4-0ubuntu0.1) ...
Setting up libgl1-mesa-dri:i386 (9.1.4-0ubuntu0.1) ...
Setting up libgl1-mesa-glx:amd64 (9.1.4-0ubuntu0.1) ...
/sbin/ldconfig.real: /usr/lib/i386-linux-gnu/libGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/i386-linux-gnu/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/i386-linux-gnu/libGLw.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/x86_64-linux-gnu/libGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/x86_64-linux-gnu/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/x86_64-linux-gnu/libGLw.so.1 is not a symbolic link

Setting up libgl1-mesa-glx:i386 (9.1.4-0ubuntu0.1) ...
/sbin/ldconfig.real: /usr/lib/i386-linux-gnu/libGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/i386-linux-gnu/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/i386-linux-gnu/libGLw.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/x86_64-linux-gnu/libGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/x86_64-linux-gnu/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/x86_64-linux-gnu/libGLw.so.1 is not a symbolic link

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/lib/i386-linux-gnu/libGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/i386-linux-gnu/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/i386-linux-gnu/libGLw.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/x86_64-linux-gnu/libGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/x86_64-linux-gnu/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/x86_64-linux-gnu/libGLw.so.1 is not a symbolic link

nicholas@nicholas-Inspiron-1545:~$ 


What's all this "is not a symbolic link" business?  

Also, here's the output you asked for: 

nicholas@nicholas-Inspiron-1545:~$ export LIBGL_DEBUG=verbose; glxinfo
name of display: :0.0
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_multisample, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: (null)
OpenGL renderer string: (null)
OpenGL version string: (null)
Segmentation fault (core dumped)
nicholas@nicholas-Inspiron-1545:~$ 

Thanks so much for your help.

---

### Post by Yellow Pasque on 2013-09-13
I'm personally stumped. If it was me, I would try xorg-edgers ppa ( [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) ) in the chance that this is a bug that has already been fixed upstream.
Note: If the PPA, doesn't help, reverse the changes using ppa-purge command, install xdiagnose package and file a bug with it.

---

### Post by Corey Goettsch on 2013-09-15
Well, Temujin, I did as you suggested.  Unfortunately, the problem still exists.  Thanks for your help, though.

---

### Post by Corey Goettsch on 2013-09-16
I figured a reinstall would do the trick.  Boy was I wrong....

I tried to reinstall 13.04 through a usb device.  Everything was fine until it started restoring my software.  Some package was broken (I guess I should've purged my PPAs), and it bulldozed through this, leaving me with a broken desktop.  I then tried to do a fresh install.  My mouse and touchpad didn't work.  I also couldn't get my broadcom driver to work for my wireless.  I reinstalled it AGAIN.  Still no mouse or touchpad.  

I think it's time to take a break from Ubuntu.  I've never had so many problems with a Linux distro as I have 13.04.  I'm about to install Linux Mint.

---

### Post by Yellow Pasque on 2013-09-17
Mint 15 is based off Ubuntu 13.04, so don't be surprised if the same issues resurface there...

---

### Post by wsv on 2013-10-02
Same up here.
After upgrading to 13.4 glsl started hampering.
Few months ago happened on my old HP notebook (12.10->13.4).
Now, on my brand new Dell XPS 13 notebook (12.10->13.4).

First I thought the old notebook died (a bit), but now it is clearly ubuntu 13.4.
I have tested HTML5/opengl ES as well native Qt C++/opengl GLSL.
In both cases it works fine on my (old) server (12.04 LTS) and WebGL on a Windows box.
It fails on both 13.4 notebooks.
To be specific:
GLSL: uniform variables lose their values in the shaders. The values become totally unpredictable!
See [http://qt-project.org/forums/viewthread/33151/](http://qt-project.org/forums/viewthread/33151/)
I have been looking end testing for days now.

wim@elsams-u:~$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_multisample, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_framebuffer_sRGB, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL version string: 3.0 Mesa 9.1.4
OpenGL shading language version string: 1.30
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_polygon_offset, GL_EXT_subtexture, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, GL_EXT_texture, 
    GL_EXT_texture3D, GL_IBM_rasterpos_clip, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_ARB_framebuffer_sRGB, GL_ARB_multitexture, 
    GL_EXT_framebuffer_sRGB, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_3DFX_texture_compression_FXT1, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, GL_S3_s3tc, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_MESA_window_pos, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_ARB_depth_texture, GL_ARB_occlusion_query, 
    GL_ARB_shadow, GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ATI_envmap_bumpmap, GL_EXT_stencil_two_side, 
    GL_EXT_texture_cube_map, GL_NV_depth_clamp, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_wrap, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_primitive_restart, GL_ARB_depth_clamp, 
    GL_ARB_fragment_program_shadow, GL_ARB_half_float_pixel, 
    GL_ARB_occlusion_query2, GL_ARB_point_sprite, GL_ARB_shading_language_100, 
    GL_ARB_sync, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_color_buffer_float, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_float, 
    GL_ARB_texture_rectangle, GL_EXT_packed_float, GL_EXT_pixel_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_ARB_framebuffer_object, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_packed_depth_stencil, GL_APPLE_object_purgeable, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, GL_EXT_draw_buffers2, 
    GL_EXT_draw_instanced, GL_EXT_gpu_program_parameters, 
    GL_EXT_texture_array, GL_EXT_texture_integer, GL_EXT_texture_sRGB_decode, 
    GL_EXT_timer_query, GL_OES_EGL_image, GL_MESA_texture_array, 
    GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, GL_ARB_draw_instanced, 
    GL_ARB_half_float_vertex, GL_ARB_instanced_arrays, 
    GL_ARB_map_buffer_range, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_vertex_array_bgra, GL_EXT_separate_shader_objects, 
    GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra, 
    GL_NV_conditional_render, GL_AMD_draw_buffers_blend, 
    GL_ARB_ES2_compatibility, GL_ARB_blend_func_extended, GL_ARB_debug_output, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_provoking_vertex, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_shader_texture_lod, GL_ARB_texture_cube_map_array, 
    GL_ARB_texture_rgb10_a2ui, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_EXT_provoking_vertex, 
    GL_EXT_texture_snorm, GL_MESA_texture_signed_rgba, 
    GL_ARB_get_program_binary, GL_ARB_robustness, GL_ARB_shader_bit_encoding, 
    GL_ARB_timer_query, GL_ANGLE_texture_compression_dxt3, 
    GL_ANGLE_texture_compression_dxt5, GL_ARB_internalformat_query, 
    GL_ARB_shading_language_packing, GL_ARB_texture_storage, 
    GL_EXT_transform_feedback, GL_ARB_ES3_compatibility, 
    GL_ARB_invalidate_subdata

20 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x020 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x021 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a0 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0a2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0a3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x0a4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0a5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0aa 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0ab 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0ac 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x0ad 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0ae 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x071 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

44 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x072  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x073  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x074  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x075  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x076  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x077  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x078 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x079 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x07a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x07e 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x080  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x081  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x082  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x083  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x084 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x085 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x086 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x087 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x088  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x089  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08b  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08c  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08d  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x090 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x091 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x092  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x093  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x094 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x095 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x096  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x097  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x098  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x099  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x09a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x09b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x09c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x09d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None

wim@elsams-u:~$

---

