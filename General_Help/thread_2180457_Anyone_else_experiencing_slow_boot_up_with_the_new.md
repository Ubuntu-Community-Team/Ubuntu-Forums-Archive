---
title: "Anyone else experiencing slow boot up with the new NVidia 319 drivers?"
date: 2013-10-13
forum: General Help
---

### Post by vanessax on 2013-10-13
On Ubuntu Precise, when I rebooted with the new NVidia 319 drivers, I get that blinking cursor in the upper left corner for about 5 minutes, looks like everything is stuck or hanging, but if I wait longer then I get the graphical login screen.

I can switch to VT's (virtual terminals) with ALT+F1 during that time, so I'm not sure what is causing the delay. I used to have the NVidia 304 drivers and never came across slow boot ups before.

Info:

```

# lspci | grep -i nvidia
02:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9400 GT] (rev a1)

```

```

# cat /var/log/Xorg.0.log|grep -i nvidia
[   344.526] (II) Module glx: vendor="NVIDIA Corporation"
[   344.526] (II) NVIDIA GLX Module  319.32  Wed Jun 19 14:55:38 PDT 2013
[   344.531] (II) LoadModule: "nvidia"
[   344.531] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   344.651] (II) Module nvidia: vendor="NVIDIA Corporation"
[   344.666] (II) NVIDIA dlloader X Driver  319.32  Wed Jun 19 14:34:12 PDT 2013
[   344.666] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   344.740] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   344.740] (==) NVIDIA(0): RGB weight 888
[   344.740] (==) NVIDIA(0): Default visual is TrueColor
[   344.740] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   344.740] (**) NVIDIA(0): Option "Stereo" "0"
[   344.740] (**) NVIDIA(0): Option "nvidiaXineramaInfoOrder" "DFP-0"
[   344.740] (**) NVIDIA(0): Stereo disabled by request
[   344.740] (**) NVIDIA(0): Option "MetaModes" "800x600 +0+0"
[   344.740] (**) NVIDIA(0): Enabling 2D acceleration
[   346.104] (II) NVIDIA(GPU-0): Display (Acer G276HL (DFP-0)) does not support NVIDIA 3D
[   346.104] (II) NVIDIA(GPU-0):     Vision stereo.
[   346.106] (II) NVIDIA(0): NVIDIA GPU GeForce 9400 GT (G96) at PCI:2:0:0 (GPU-0)
[   346.106] (--) NVIDIA(0): Memory: 1048576 kBytes
[   346.106] (--) NVIDIA(0): VideoBIOS: 62.94.61.00.96
[   346.106] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   346.111] (--) NVIDIA(0): Valid display device(s) on GeForce 9400 GT at PCI:2:0:0
[   346.111] (--) NVIDIA(0):     CRT-0
[   346.111] (--) NVIDIA(0):     CRT-1
[   346.111] (--) NVIDIA(0):     Acer G276HL (DFP-0) (boot, connected)
[   346.111] (--) NVIDIA(0):     DFP-1
[   346.111] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[   346.111] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[   346.111] (--) NVIDIA(0): Acer G276HL (DFP-0): 330.0 MHz maximum pixel clock
[   346.111] (--) NVIDIA(0): Acer G276HL (DFP-0): Internal Dual Link TMDS
[   346.111] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[   346.111] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[   346.111] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   346.111] (**) NVIDIA(0):     device Acer G276HL (DFP-0) (Using EDID frequencies has
[   346.111] (**) NVIDIA(0):     been enabled on all display devices.)
[   346.114] (II) NVIDIA(0): Validated MetaModes:
[   346.114] (II) NVIDIA(0):     "800x600+0+0"
[   346.114] (II) NVIDIA(0): Virtual screen size determined to be 800 x 600
[   346.152] (--) NVIDIA(0): DPI set to (33, 44); computed from "UseEdidDpi" X config
[   346.152] (--) NVIDIA(0):     option
[   346.152] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[   346.161] (II) NVIDIA(0): Setting mode "800x600+0+0"
[   346.233] (==) NVIDIA(0): Disabling shared memory pixmaps
[   346.233] (==) NVIDIA(0): Backing store disabled
[   346.233] (==) NVIDIA(0): Silken mouse enabled
[   346.234] (**) NVIDIA(0): DPMS enabled
[   346.234] (II) NVIDIA(0): [DRI2] Setup complete
[   346.234] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[   349.217] (II) NVIDIA(GPU-0): Display (Acer G276HL (DFP-0)) does not support NVIDIA 3D
[   349.217] (II) NVIDIA(GPU-0):     Vision stereo.
[   349.217] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   349.217] (**) NVIDIA(0):     device Acer G276HL (DFP-0) (Using EDID frequencies has
[   349.217] (**) NVIDIA(0):     been enabled on all display devices.)
[   350.262] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[   350.621] (II) NVIDIA(GPU-0): Display (Acer G276HL (DFP-0)) does not support NVIDIA 3D
[   350.621] (II) NVIDIA(GPU-0):     Vision stereo.
[   350.621] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   350.621] (**) NVIDIA(0):     device Acer G276HL (DFP-0) (Using EDID frequencies has
[   350.621] (**) NVIDIA(0):     been enabled on all display devices.)
[   364.969] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[   365.109] (II) NVIDIA(GPU-0): Display (Acer G276HL (DFP-0)) does not support NVIDIA 3D
[   365.109] (II) NVIDIA(GPU-0):     Vision stereo.
[   365.109] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   365.109] (**) NVIDIA(0):     device Acer G276HL (DFP-0) (Using EDID frequencies has
[   365.109] (**) NVIDIA(0):     been enabled on all display devices.)
[   371.786] (II) NVIDIA(GPU-0): Display (Acer G276HL (DFP-0)) does not support NVIDIA 3D
[   371.786] (II) NVIDIA(GPU-0):     Vision stereo.
[   371.786] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   371.786] (**) NVIDIA(0):     device Acer G276HL (DFP-0) (Using EDID frequencies has
[   371.786] (**) NVIDIA(0):     been enabled on all display devices.)
[   372.166] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[   372.707] (II) NVIDIA(GPU-0): Display (Acer G276HL (DFP-0)) does not support NVIDIA 3D
[   372.707] (II) NVIDIA(GPU-0):     Vision stereo.
[   372.707] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   372.707] (**) NVIDIA(0):     device Acer G276HL (DFP-0) (Using EDID frequencies has
[   372.707] (**) NVIDIA(0):     been enabled on all display devices.)
[   375.772] (II) NVIDIA(GPU-0): Display (Acer G276HL (DFP-0)) does not support NVIDIA 3D
[   375.772] (II) NVIDIA(GPU-0):     Vision stereo.
[   375.772] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   375.772] (**) NVIDIA(0):     device Acer G276HL (DFP-0) (Using EDID frequencies has
[   375.772] (**) NVIDIA(0):     been enabled on all display devices.)
[   378.012] (II) NVIDIA(GPU-0): Display (Acer G276HL (DFP-0)) does not support NVIDIA 3D
[   378.012] (II) NVIDIA(GPU-0):     Vision stereo.
[   378.012] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   378.012] (**) NVIDIA(0):     device Acer G276HL (DFP-0) (Using EDID frequencies has
[   378.012] (**) NVIDIA(0):     been enabled on all display devices.)
[   378.091] (II) NVIDIA(GPU-0): Display (Acer G276HL (DFP-0)) does not support NVIDIA 3D
[   378.091] (II) NVIDIA(GPU-0):     Vision stereo.
[   378.091] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   378.091] (**) NVIDIA(0):     device Acer G276HL (DFP-0) (Using EDID frequencies has
[   378.091] (**) NVIDIA(0):     been enabled on all display devices.)

```

---

