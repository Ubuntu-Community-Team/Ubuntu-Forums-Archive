---
title: "Unity login doesn't work after rebooting"
date: 2015-08-13
forum: General Help
---

### Post by Serhan_Gl on 2015-08-13
Hi, I shut down my machine with Ubuntu 14.04 and came back following day and started it. However, I couldn't log into Unity with my password. I can log into Gnome though. I suspect that this is caused by some automatic updates that I'm not aware of because when I log into Gnome, I get the following error message with the title:

```
Xorg crashed with SIGABRT in OsAbort()
```

Here is the error message I get:

[ATTACH=CONFIG]263816[/ATTACH]


Output of ```
less /var/log/Xorg.0.log
``` looks like:

```
[   682.533] (II) LoadModule: "glx"
[   682.533] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[   682.533] (EE) Failed to load /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so: libnvidia-tls.so.349.16: cannot open shared object file: No such file or directory
[   682.533] (II) UnloadModule: "glx"
[   682.533] (II) Unloading glx
[   682.533] (EE) Failed to load module "glx" (loader failed, 7)
[   682.533] (==) Matched nvidia as autoconfigured driver 0
[   682.533] (==) Matched nouveau as autoconfigured driver 1
[   682.533] (==) Matched nvidia as autoconfigured driver 2
[   682.533] (==) Matched nouveau as autoconfigured driver 3
[   682.533] (==) Matched modesetting as autoconfigured driver 4
[   682.533] (==) Matched fbdev as autoconfigured driver 5
[   682.533] (==) Matched vesa as autoconfigured driver 6
[   682.533] (==) Assigned the driver to the xf86ConfigLayout
[   682.533] (II) LoadModule: "nvidia"
[   682.533] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   682.534] (II) Module nvidia: vendor="NVIDIA Corporation"
[   682.534]     compiled for 4.0.2, module version = 1.0.0
[   682.534]     Module class: X.Org Video Driver
[   682.534] (II) LoadModule: "nouveau"
[   682.534] (WW) Warning, couldn't open module nouveau
[   682.534] (II) UnloadModule: "nouveau"
[   682.534] (II) Unloading nouveau
[   682.534] (EE) Failed to load module "nouveau" (module does not exist, 0)
[   682.534] (II) LoadModule: "modesetting"
[   682.534] (WW) Warning, couldn't open module modesetting
[   682.534] (II) UnloadModule: "modesetting"
[   682.534] (II) Unloading modesetting
[   682.534] (EE) Failed to load module "modesetting" (module does not exist, 0)
[   682.534] (II) LoadModule: "fbdev"
[   682.534] (WW) Warning, couldn't open module fbdev
[   682.534] (II) UnloadModule: "fbdev"
[   682.534] (II) Unloading fbdev
[   682.534] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   682.534] (II) LoadModule: "vesa"
[   682.534] (WW) Warning, couldn't open module vesa
[   682.534] (II) UnloadModule: "vesa"
[   682.534] (II) Unloading vesa
[   682.534] (EE) Failed to load module "vesa" (module does not exist, 0)
[   682.534] (==) Matched nvidia as autoconfigured driver 0
[   682.534] (==) Matched nouveau as autoconfigured driver 1
[   682.534] (==) Matched nvidia as autoconfigured driver 2
[   682.534] (==) Matched nouveau as autoconfigured driver 3
[   682.534] (==) Matched modesetting as autoconfigured driver 4
[   682.534] (==) Matched fbdev as autoconfigured driver 5
[   682.534] (==) Matched vesa as autoconfigured driver 6
[   682.534] (==) Assigned the driver to the xf86ConfigLayout
[   682.534] (II) LoadModule: "nvidia"
[   682.534] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   682.534] (II) Module nvidia: vendor="NVIDIA Corporation"
[   682.534]     compiled for 4.0.2, module version = 1.0.0
[   682.534]     Module class: X.Org Video Driver
[   682.534] (II) UnloadModule: "nvidia"
[   682.534] (II) Unloading nvidia
[   682.534] (II) Failed to load module "nvidia" (already loaded, 32523)
[   682.534] (II) LoadModule: "nouveau"
[   682.534] (WW) Warning, couldn't open module nouveau
[   682.534] (II) UnloadModule: "nouveau"
[   682.534] (II) Unloading nouveau
[   682.534] (EE) Failed to load module "nouveau" (module does not exist, 0)
[   682.534] (II) LoadModule: "modesetting"
[   682.535] (WW) Warning, couldn't open module modesetting
[   682.535] (II) UnloadModule: "modesetting"
[   682.535] (II) Unloading modesetting
[   682.535] (EE) Failed to load module "modesetting" (module does not exist, 0)
[   682.535] (II) LoadModule: "fbdev"
[   682.535] (WW) Warning, couldn't open module fbdev
[   682.535] (II) UnloadModule: "fbdev"
[   682.535] (II) Unloading fbdev
[   682.535] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   682.535] (II) LoadModule: "vesa"
[   682.535] (WW) Warning, couldn't open module vesa
[   682.535] (II) UnloadModule: "vesa"
[   682.535] (II) Unloading vesa
[   682.535] (EE) Failed to load module "vesa" (module does not exist, 0)
[   682.535] (II) NVIDIA dlloader X Driver  349.16  Tue Apr  7 23:19:49 PDT 2015
[   682.535] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   682.535] (++) using VT number 7

[   682.539] (II) Loading sub module "fb"
[   682.539] (II) LoadModule: "fb"
[   682.539] (II) Loading /usr/lib/xorg/modules/libfb.so
[   682.540] (II) Module fb: vendor="X.Org Foundation"
[   682.540]     compiled for 1.15.1, module version = 1.0.0
[   682.540]     ABI class: X.Org ANSI C Emulation, version 0.4
[   682.540] (II) Loading sub module "wfb"
[   682.540] (II) LoadModule: "wfb"
[   682.540] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   682.540] (II) Module wfb: vendor="X.Org Foundation"
[   682.540]     compiled for 1.15.1, module version = 1.0.0
[   682.540]     ABI class: X.Org ANSI C Emulation, version 0.4
[   682.540] (II) Loading sub module "ramdac"
[   682.540] (II) LoadModule: "ramdac"
[   682.540] (II) Module "ramdac" already built-in
[   682.540] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   682.540] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[   682.540] (==) NVIDIA(0): RGB weight 888
[   682.540] (==) NVIDIA(0): Default visual is TrueColor
[   682.540] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   682.540] (**) NVIDIA(0): Enabling 2D acceleration
[   682.540] (EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
[   682.540] (EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
[   682.540] (EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
[   682.540] (EE) NVIDIA(0):     you continue to encounter problems, Please try
[   682.540] (EE) NVIDIA(0):     reinstalling the NVIDIA driver.
[   682.549] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[   682.550] (II) NVIDIA(0): NVIDIA GPU Quadro K2200 (GM107GL-A) at PCI:3:0:0 (GPU-0)
[   682.550] (--) NVIDIA(0): Memory: 4194304 kBytes
[   682.550] (--) NVIDIA(0): VideoBIOS: 82.07.5a.00.01
[   682.550] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   682.622] (--) NVIDIA(0): Valid display device(s) on Quadro K2200 at PCI:3:0:0
[   682.622] (--) NVIDIA(0):     CRT-0
[   682.622] (--) NVIDIA(0):     DFP-0
[   682.622] (--) NVIDIA(0):     DFP-1
[   682.622] (--) NVIDIA(0):     DFP-2
[   682.622] (--) NVIDIA(0):     DELL U2711 (DFP-3) (connected)
[   682.622] (--) NVIDIA(0):     DELL 2709W (DFP-4) (boot, connected)
[   682.622] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[   682.622] (--) NVIDIA(0): DFP-0: Internal TMDS
[   682.622] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[   682.622] (--) NVIDIA(0): DFP-1: Internal TMDS
[   682.622] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[   682.622] (--) NVIDIA(0): DFP-2: Internal TMDS
[   682.622] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
[   682.622] (--) NVIDIA(0): DELL U2711 (DFP-3): Internal DisplayPort
[   682.622] (--) NVIDIA(GPU-0): DELL U2711 (DFP-3): 960.0 MHz maximum pixel clock
[   682.623] (--) NVIDIA(0): DELL 2709W (DFP-4): Internal DisplayPort
[   682.623] (--) NVIDIA(GPU-0): DELL 2709W (DFP-4): 960.0 MHz maximum pixel clock
[   682.623] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   682.623] (**) NVIDIA(0):     device DELL U2711 (DFP-3) (Using EDID frequencies has been
[   682.623] (**) NVIDIA(0):     enabled on all display devices.)
[   682.625] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   682.625] (**) NVIDIA(0):     device DELL 2709W (DFP-4) (Using EDID frequencies has been
[   682.625] (**) NVIDIA(0):     enabled on all display devices.)
[   682.642] (==) NVIDIA(0): 
[   682.642] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[   682.642] (==) NVIDIA(0):     will be used as the requested mode.
[   682.642] (==) NVIDIA(0): 
[   682.642] (II) NVIDIA(0): Validated MetaModes:
[   682.642] (II) NVIDIA(0):     "DFP-4:nvidia-auto-select,DFP-3:nvidia-auto-select"
[   682.642] (II) NVIDIA(0): Virtual screen size determined to be 4480 x 1440
[   682.643] (--) NVIDIA(0): DPI set to (84, 84); computed from "UseEdidDpi" X config
[   682.643] (--) NVIDIA(0):     option
[   682.643] (--) Depth 24 pixmap format is 32 bpp
[   682.644] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[   682.644] (II) NVIDIA:     access.
[   682.649] (II) NVIDIA(0): Setting mode "DFP-4:nvidia-auto-select,DFP-3:nvidia-auto-select"
[   682.723] Loading extension NV-GLX
[   682.769] (==) NVIDIA(0): Disabling shared memory pixmaps
[   682.769] (==) NVIDIA(0): Backing store enabled
[   682.769] (==) NVIDIA(0): Silken mouse enabled
[   682.769] (==) NVIDIA(0): DPMS enabled
[   682.769] Loading extension NV-CONTROL
[   682.769] Loading extension XINERAMA
[   682.769] (II) Loading sub module "dri2"
[   682.769] (II) LoadModule: "dri2"
[   682.769] (II) Module "dri2" already built-in
[   682.769] (II) NVIDIA(0): [DRI2] Setup complete
[   682.769] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
```

Might it be a graphics card problem, like a conflict between NVidia drivers and XServer? Thank you.

EDIT:
I looked into ~/.xsession-errors.old and there I see the error:

```
/usr/lib/nux/unity_support_test: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

---

