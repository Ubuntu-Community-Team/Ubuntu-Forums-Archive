---
title: "no direct rendering"
date: 2016-11-04
forum: General Help
---

### Post by fizikz on 2016-11-04
Today I got updated to NVIDIA 304.132 drivers (installed through "Additional Drivers"). But when I checked glxinfo, it indicated that direct rendering is not enabled. 

```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

Using "LIBGL_DEBUG=verbose glxinfo" either seems to give the same output as glxinfo, or it isn't working.

When I tried switching to the Nouveau driver (again with "Additional Drivers"), direct rendering was enabled. How can I enable it with the NVIDIA driver?

---

### Post by T.J. on 2016-11-04
The Nvidia driver should enable Direct Rendering automatically.  If it has not, then the installer did not function properly.  I'd suggest reinstalling the driver, run "sudo nvidia-xconfig" and then reset the machine.  See if that works.

---

### Post by fizikz on 2016-11-04
I ran "sudo nvidia-xconfig". It mentioned that no xorg.conf was found and so it created a new one. Rebooted, but no change; still no direct rendering.

"Additional Drivers" reports that the NVIDIA proprietary driver is in use, and glxinfo also mentions NVIDIA as the "vendor" for various parameters like glx server/client, OpenGL, etc. 

From running "inxi -Fxz":

```
Graphics:  
Card: NVIDIA G73M [GeForce Go 7700] 
bus-ID: 01:00.0 
X.Org: 1.15.1 
driver: nvidia 
Resolution: 1920x1080@60.0hz 
GLX Renderer: GeForce Go 7700/PCIe/SSE2 
GLX Version: 2.1.2 NVIDIA 304.132 
Direct Rendering: No
```

This situation is unusual, as updates including direct rendering typically worked without a hitch before, for many years. I occasionally spot check with glxinfo after updates to make sure everything is functioning correctly, and this time I was surprised.

---

### Post by T.J. on 2016-11-05
> **fizikz said:**
> 

This situation is unusual, as updates including direct rendering typically worked without a hitch before, for many years. I occasionally spot check with glxinfo after updates to make sure everything is functioning correctly, and this time I was surprised.

Quite.  It sounds to me as if you have a mangled OpenGL library somewhere.  I'd uninstall the Nvidia driver, then force a reinstall of the GLX and DRI libraries.

sudo apt-get install --reinstall libgl1-mesa-dri
sudo apt-get install --reinstall libgl1-mesa-glx

Then after a restart, if you want to try the prepackaged driver one more time, then go ahead.  If it still fails, then we can talk about repairing OpenGL and installing the driver manually.

---

### Post by fizikz on 2016-11-05
> **T.J. said:**
> I'd uninstall the Nvidia driver, then force a reinstall of the GLX and DRI libraries.

sudo apt-get install --reinstall libgl1-mesa-dri
sudo apt-get install --reinstall libgl1-mesa-glx

Then after a restart, if you want to try the prepackaged driver one more time, then go ahead. 

Thanks for the suggestions. Tried it and still no change. 

I also checked for direct rendering when using the nouveau drivers (direct rendering = yes, but with libgl=verbose it gave some errors/warnings about the display and library files). With nouveau, the resolution was limited to 1280x1024, but that's another story.

I thought I'd mention that I'm using an external display (DVI out) with the computer's internal display typically off. Would the specific monitor have any relevance to rendering? configuration? I've gotten used to things "just working" and haven't needed to dig into xorg.conf files as was typical years ago.

I hope the prepackaged nvidia drivers can be made to work. Until maybe a couple of years ago, I used to install/update the nvidia drivers manually, and it's a bit of a pain to have to recompile the kernel module every time there is a linux kernel update.

---

### Post by gordintoronto on 2016-11-05
I don't think this will solve your problem, but it's probably of interest:
[https://packages.debian.org/sid/nvidia-legacy-304xx-driver](https://packages.debian.org/sid/nvidia-legacy-304xx-driver)

---

### Post by fizikz on 2016-11-05
> **gordintoronto said:**
> I don't think this will solve your problem, but it's probably of interest:
[https://packages.debian.org/sid/nvidia-legacy-304xx-driver](https://packages.debian.org/sid/nvidia-legacy-304xx-driver)

Thanks. Is there a specific section/information that you thought might be relevant?

---

### Post by T.J. on 2016-11-05
> **fizikz said:**
> 

I thought I'd mention that I'm using an external display (DVI out) with the computer's internal display typically off. Would the specific monitor have any relevance to rendering? configuration? 

No.  This is entirely a software related problem.   If DRI is not functioning, either your Mesa installation is damaged, DRI is turned off in xorg.conf or the driver is not installed correctly.  If it were your hardware, you would not have a working display at all and nouveau would not work.  

Need to think.  BBL.

---

### Post by gordintoronto on 2016-11-05
Where it says, "This legacy version is the last release that supports the following GPUs: " and the list includes your GPU.

> **fizikz said:**
> Thanks. Is there a specific section/information that you thought might be relevant?

---

### Post by fizikz on 2016-11-06
My hardware has been on the legacy drivers for several years now. It still gets minor updates (304.xxx, currently 304.132) for security/bugfixes, but not major updates (now at 367.57) like for the latest hardware.

---

### Post by fizikz on 2016-11-06
Here's what I've found for possible diagnostics. Does anything stand out?

From [https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457](https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457) 
```
$ ldd /usr/bin/glxinfo
	linux-gate.so.1 =>  (0xb774d000)
	libGL.so.1 => /usr/lib/nvidia-304/libGL.so.1 (0xb7636000)
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xb7502000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb7352000)
	libnvidia-tls.so.304.132 => /usr/lib/nvidia-304/tls/libnvidia-tls.so.304.132 (0xb734e000)
	libnvidia-glcore.so.304.132 => /usr/lib/nvidia-304/libnvidia-glcore.so.304.132 (0xb5648000)
	libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xb5635000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb5630000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xb560d000)
	/lib/ld-linux.so.2 (0xb774e000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xb55c7000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xb55c3000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xb55bc000)

```


A chunk from Xorg.0.log:
```
[   142.709] (II) Module ABI versions:
[   142.709] 	X.Org ANSI C Emulation: 0.4
[   142.709] 	X.Org Video Driver: 15.0
[   142.709] 	X.Org XInput driver : 20.0
[   142.709] 	X.Org Server Extension : 8.0
[   142.709] (II) xfree86: Adding drm device (/dev/dri/card0)
[   142.710] (--) PCI:*(0:1:0:0) 10de:0397:1043:1442 rev 161, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xfc000000/16777216, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
[   142.711] Initializing built-in extension Generic Event Extension
[   142.711] Initializing built-in extension SHAPE
[   142.711] Initializing built-in extension MIT-SHM
[   142.711] Initializing built-in extension XInputExtension
[   142.711] Initializing built-in extension XTEST
[   142.711] Initializing built-in extension BIG-REQUESTS
[   142.711] Initializing built-in extension SYNC
[   142.711] Initializing built-in extension XKEYBOARD
[   142.711] Initializing built-in extension XC-MISC
[   142.711] Initializing built-in extension SECURITY
[   142.711] Initializing built-in extension XINERAMA
[   142.711] Initializing built-in extension XFIXES
[   142.711] Initializing built-in extension RENDER
[   142.711] Initializing built-in extension RANDR
[   142.711] Initializing built-in extension COMPOSITE
[   142.711] Initializing built-in extension DAMAGE
[   142.711] Initializing built-in extension MIT-SCREEN-SAVER
[   142.711] Initializing built-in extension DOUBLE-BUFFER
[   142.711] Initializing built-in extension RECORD
[   142.711] Initializing built-in extension DPMS
[   142.711] Initializing built-in extension Present
[   142.711] Initializing built-in extension DRI3
[   142.711] Initializing built-in extension X-Resource
[   142.711] Initializing built-in extension XVideo
[   142.711] Initializing built-in extension XVideo-MotionCompensation
[   142.711] Initializing built-in extension SELinux
[   142.711] Initializing built-in extension XFree86-VidModeExtension
[   142.711] Initializing built-in extension XFree86-DGA
[   142.711] Initializing built-in extension XFree86-DRI
[   142.711] Initializing built-in extension DRI2
[   142.711] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[   142.711] (II) "glx" will be loaded by default.
[   142.711] (WW) "xmir" is not to be loaded by default. Skipping.
[   142.711] (II) LoadModule: "glx"
[   142.711] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[   142.748] (II) Module glx: vendor="NVIDIA Corporation"
[   142.748] 	compiled for 4.0.2, module version = 1.0.0
[   142.748] 	Module class: X.Org Server Extension
[   142.748] (II) NVIDIA GLX Module  304.132  Fri Sep 16 11:43:26 PDT 2016
[   142.748] Loading extension GLX
[   142.748] (II) LoadModule: "nvidia"
[   142.748] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   142.749] (II) Module nvidia: vendor="NVIDIA Corporation"
[   142.749] 	compiled for 4.0.2, module version = 1.0.0
[   142.749] 	Module class: X.Org Video Driver
[   142.749] (II) NVIDIA dlloader X Driver  304.132  Fri Sep 16 11:24:03 PDT 2016
[   142.749] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   142.749] (++) using VT number 7

[   142.749] (II) Loading sub module "fb"
[   142.749] (II) LoadModule: "fb"
[   142.749] (II) Loading /usr/lib/xorg/modules/libfb.so
[   142.749] (II) Module fb: vendor="X.Org Foundation"
[   142.749] 	compiled for 1.15.1, module version = 1.0.0
[   142.749] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   142.750] (II) Loading sub module "wfb"
[   142.750] (II) LoadModule: "wfb"
[   142.750] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   142.750] (II) Module wfb: vendor="X.Org Foundation"
[   142.750] 	compiled for 1.15.1, module version = 1.0.0
[   142.750] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   142.750] (II) Loading sub module "ramdac"
[   142.750] (II) LoadModule: "ramdac"
[   142.750] (II) Module "ramdac" already built-in
[   142.750] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   142.750] (==) NVIDIA(0): RGB weight 888
[   142.750] (==) NVIDIA(0): Default visual is TrueColor
[   142.750] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   142.750] (**) NVIDIA(0): Enabling 2D acceleration
[   143.356] (II) NVIDIA(GPU-0): Display (Chi Mei Optoelectronics corp. (DFP-0)) does not
[   143.356] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[   143.506] (II) NVIDIA(GPU-0): Display (SONY TV (DFP-1)) does not support NVIDIA 3D Vision
[   143.506] (II) NVIDIA(GPU-0):     stereo.
[   143.509] (II) NVIDIA(0): NVIDIA GPU GeForce Go 7700 (G73) at PCI:1:0:0 (GPU-0)
[   143.509] (--) NVIDIA(0): Memory: 524288 kBytes
[   143.509] (--) NVIDIA(0): VideoBIOS: 05.73.22.49.12
[   143.509] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   143.509] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   143.509] (--) NVIDIA(0): Valid display device(s) on GeForce Go 7700 at PCI:1:0:0
[   143.509] (--) NVIDIA(0):     CRT-0
[   143.509] (--) NVIDIA(0):     TV-0
[   143.509] (--) NVIDIA(0):     Chi Mei Optoelectronics corp. (DFP-0) (connected)
[   143.509] (--) NVIDIA(0):     SONY TV (DFP-1) (connected)
[   143.509] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[   143.509] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[   143.509] (--) NVIDIA(0): TV encoder: Unknown
[   143.509] (--) NVIDIA(0): Chi Mei Optoelectronics corp. (DFP-0): 330.0 MHz maximum pixel clock
[   143.509] (--) NVIDIA(0): Chi Mei Optoelectronics corp. (DFP-0): Internal Dual Link LVDS
[   143.509] (--) NVIDIA(0): SONY TV (DFP-1): 165.0 MHz maximum pixel clock
[   143.509] (--) NVIDIA(0): SONY TV (DFP-1): Internal Single Link TMDS
[   143.509] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   143.509] (**) NVIDIA(0):     device Chi Mei Optoelectronics corp. (DFP-0) (Using EDID
[   143.509] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[   143.509] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   143.509] (**) NVIDIA(0):     device SONY TV (DFP-1) (Using EDID frequencies has been
[   143.509] (**) NVIDIA(0):     enabled on all display devices.)
[   143.509] (WW) NVIDIA(GPU-0): The EDID for SONY TV (DFP-1) contradicts itself: mode
[   143.509] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[   143.509] (WW) NVIDIA(GPU-0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[   143.509] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[   143.509] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[   143.509] (WW) NVIDIA(GPU-0): The EDID for SONY TV (DFP-1) contradicts itself: mode
[   143.509] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[   143.509] (WW) NVIDIA(GPU-0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[   143.509] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[   143.509] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[   143.509] (WW) NVIDIA(GPU-0): The EDID for SONY TV (DFP-1) contradicts itself: mode
[   143.509] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[   143.509] (WW) NVIDIA(GPU-0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[   143.509] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (30.0 Hz); ignoring VertRefresh
[   143.509] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[   143.509] (WW) NVIDIA(GPU-0): The EDID for SONY TV (DFP-1) contradicts itself: mode
[   143.509] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[   143.509] (WW) NVIDIA(GPU-0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[   143.509] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (30.0 Hz); ignoring VertRefresh
[   143.509] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[   143.510] (==) NVIDIA(0): 
[   143.510] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[   143.510] (==) NVIDIA(0):     will be used as the requested mode.
[   143.510] (==) NVIDIA(0): 
[   143.510] (II) NVIDIA(0): Validated MetaModes:
[   143.510] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select,DFP-1:nvidia-auto-select"
[   143.510] (II) NVIDIA(0): Virtual screen size determined to be 3600 x 1080
[   143.510] (WW) NVIDIA(0): Unable to support custom viewPortOut 1312 x 1050 +184 +0
[   143.510] (WW) NVIDIA(0): Unable to support custom viewPortOut 1680 x 945 +0 +52
[   143.511] (WW) NVIDIA(0): Unable to support custom viewPortOut 1400 x 1050 +140 +0
[   143.511] (WW) NVIDIA(0): Unable to support custom viewPortOut 1400 x 1050 +140 +0
[   143.511] (WW) NVIDIA(0): Unable to support custom viewPortOut 1400 x 1050 +140 +0
[   143.512] (WW) NVIDIA(0): Unable to support custom viewPortOut 1680 x 945 +0 +52
[   143.512] (--) NVIDIA(0): DPI set to (129, 133); computed from "UseEdidDpi" X config
[   143.512] (--) NVIDIA(0):     option
[   143.512] (--) Depth 24 pixmap format is 32 bpp
[   143.525] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select,DFP-1:nvidia-auto-select"
[   143.654] Loading extension NV-GLX
[   143.692] (==) NVIDIA(0): Disabling shared memory pixmaps
[   143.692] (==) NVIDIA(0): Backing store enabled
[   143.692] (==) NVIDIA(0): Silken mouse enabled
[   143.693] (**) NVIDIA(0): DPMS enabled
[   143.693] Loading extension NV-CONTROL
[   143.693] Loading extension XINERAMA
[   143.693] (II) Loading sub module "dri2"
[   143.693] (II) LoadModule: "dri2"
[   143.693] (II) Module "dri2" already built-in
[   143.693] (II) NVIDIA(0): [DRI2] Setup complete
[   143.693] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[   143.693] (--) RandR disabled
[   143.704] (II) SELinux: Disabled on system
[   143.705] (II) Initializing extension GLX
```

Anything else to try?

---

### Post by fizikz on 2016-11-06
Ok, I think this might be some permissions issue. When I tried "sudo glxinfo" it said direct rendering was enabled. I tried adding my user to the "video" group and restarting X, but that didn't work.

---

### Post by kengordo on 2016-11-06
I am pretty sure you have a symlink issue.  Nvidia-304 did this to my installation when I had 14.04, and was fixed in later drivers.  It looks like you may be stuck with that version since your GeForce card seems to not be listed as supported hardware in later drivers. If you find you can run later than 304, I would check out installing the graphics-drivers ppa  [http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action) . 

Have you done a purge of your nvidia packages [http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely) and installed nvidia-current?  Make sure that you have not manually blacklisted the nouveau drivers before doing so.  I had a similar issue (no direct rendering) caused by symlinks and for some reason right now I cannot find the helpful page I used to manually create the links to your libraries that are needed. But in the support section of the Unix drivers on the Nvidia site it does discuss symlink issues.   

On later installations I was able to install the later driver package nvidia-352 which is a transitional package for nvidia-361 which fixed symlinks for me and the "no direct rendering" issue was fixed.

---

### Post by Yellow Pasque on 2016-11-06
Anything interesting in ~/.xsession-errors ?

---

### Post by fizikz on 2016-11-06
kengordo, if it's a symlink issue, how would "sudo glxinfo" show direct rendering enabled? I did read about symlink issues, but it was often for 32bit applications on 64bit systems, etc. I'm on a 32bit system. Nevertheless, I tried purging all nvidia-* packages, making sure there's no manual blacklist of nouveau, and reinstalling the nvidia 304.132 drivers (with "Additional Drivers"). No change.

Temüjin, here's the xsession errors. I don't see anything useful, and I suspect many of these errors are quite old.
```
$ cat ~/.xsession-errors
Warning: Only changing the first 12 of 24 buttons.
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth respawning too fast, stopped

```

---

### Post by alfernando on 2016-11-07
I have the same issue here, but with x86_64 libs.
Any hint?

---

### Post by fizikz on 2016-11-08
Looks like this issue is due to a bug in the latest updates to the nvidia driver. It has been reported on many forums and sites, and looks like nvidia is aware. The current workaround is to downgrade the driver until a fix is released. 

With tips from [http://unix.stackexchange.com/questions/321185/after-update-glx-works-only-for-root-nvidia](http://unix.stackexchange.com/questions/321185/after-update-glx-works-only-for-root-nvidia) I downgraded to driver version 304.117 (I'm on 14.04, other versions of ubuntu may prefer other driver versions) with: 

```
sudo apt-get install nvidia-304=304.117-0ubuntu1
```

and prevented it from being upgraded for now with:

```
sudo apt-mark hold nvidia-304
```

I have direct rendering again! :D

---

### Post by eddygeez on 2016-11-25
fizikz:

Just wanted to say thank you *very* much for posting this solution!

This has been causing issues for a week or so for me and I'm very happy to have fixed it for now!

---

### Post by fizikz on 2017-01-18
eddygeez, glad it helped.

Good news: the updated nvidia 304.134 solves the problem and is available in the repositories now.

```
sudo apt-mark unhold nvidia-304
sudo apt-get update
sudo apt-get upgrade
```

---

