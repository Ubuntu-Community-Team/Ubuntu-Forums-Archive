---
title: "Startx fails to start xserver, and Lightdm is stuck in login-loop"
date: 2017-05-16
forum: General Help
---

### Post by sean119 on 2017-05-16
I recently tried to switch from xfce to gnome, and had a problem with X ever since. I think it had to do something with gdm conflicting with lightdm, but I don't know. When I do 'sudo startx', I get a white graphical terminal where I can use the mouse, but it is not xfce. When I try 'startx', I get the following error:
```

xauth:  timeout in locking authority file /home/seanh/.Xauthority
xauth:  timeout in locking authority file /home/seanh/.Xauthority


X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-45-generic i686 Ubuntu
Current Operating System: Linux SeanDesktop 4.4.0-78-generic #99-Ubuntu SMP Thu Apr 27 15:28:22 UTC 2017 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-78-generic root=UUID=c19027c7-b8b6-47fb-8bc4-fb46c5723554 ro text text
Build Date: 02 November 2016  10:05:16PM
xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.33.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/home/seanh/.local/share/xorg/Xorg.1.log", Time: Tue May 16 16:56:28 2017
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
No protocol specified

waiting for X server to begin accepting connections .
No protocol specified
..
No protocol specified
..


```

When I try startxfce4, I get this message:
```

(EE) 
Fatal server error:
(EE) Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.
(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
(EE) 
No protocol specified
xinit: giving up
xinit: unable to connect to X server: Resource temporarily unavailable
xinit: server error

```
This is my ~/.local/share/xorg/Xorg.1.log file:
```

[   134.496] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[   134.497] X Protocol Version 11, Revision 0
[   134.497] Build Operating System: Linux 4.4.0-45-generic i686 Ubuntu
[   134.497] Current Operating System: Linux SeanDesktop 4.4.0-78-generic #99-Ubuntu SMP Thu Apr 27 15:28:22 UTC 2017 i686
[   134.497] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-78-generic root=UUID=c19027c7-b8b6-47fb-8bc4-fb46c5723554 ro text text
[   134.497] Build Date: 02 November 2016  10:05:16PM
[   134.498] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[   134.498] Current version of pixman: 0.33.6
[   134.498]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   134.498] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   134.499] (==) Log file: "/home/username/.local/share/xorg/Xorg.1.log", Time: Tue May 16 16:37:11 2017
[   134.499] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   134.500] (==) No Layout section.  Using the first Screen section.
[   134.500] (==) No screen section available. Using defaults.
[   134.500] (**) |-->Screen "Default Screen Section" (0)
[   134.500] (**) |   |-->Monitor "<default monitor>"
[   134.500] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   134.500] (==) Automatically adding devices
[   134.500] (==) Automatically enabling devices
[   134.500] (==) Automatically adding GPU devices
[   134.501] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   134.501] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   134.501]     Entry deleted from font path.
[   134.501] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   134.501]     Entry deleted from font path.
[   134.501] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   134.501]     Entry deleted from font path.
[   134.501] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    built-ins
[   134.501] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   134.501] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   134.501] (II) Loader magic: 0x8026b700
[   134.501] (II) Module ABI versions:
[   134.501]     X.Org ANSI C Emulation: 0.4
[   134.501]     X.Org Video Driver: 20.0
[   134.501]     X.Org XInput driver : 22.1
[   134.501]     X.Org Server Extension : 9.0
[   134.502] (++) using VT number 1

[   134.510] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_31
[   134.510] (II) xfree86: Adding drm device (/dev/dri/card0)
[   134.511] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 8 paused 0
[   134.512] (--) PCI:*(0:1:0:0) 10de:13c2:1462:3160 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[   134.512] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[   134.513] (II) "glx" will be loaded by default.
[   134.513] (II) LoadModule: "glx"
[   134.513] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[   134.536] (II) Module glx: vendor="NVIDIA Corporation"
[   134.536]     compiled for 4.0.2, module version = 1.0.0
[   134.536]     Module class: X.Org Server Extension
[   134.536] (II) NVIDIA GLX Module  375.39  Tue Jan 31 19:16:46 PST 2017
[   134.536] (==) Matched nvidia as autoconfigured driver 0
[   134.536] (==) Matched nouveau as autoconfigured driver 1
[   134.536] (==) Matched nvidia as autoconfigured driver 2
[   134.536] (==) Matched nouveau as autoconfigured driver 3
[   134.536] (==) Matched modesetting as autoconfigured driver 4
[   134.536] (==) Matched fbdev as autoconfigured driver 5
[   134.536] (==) Matched vesa as autoconfigured driver 6
[   134.536] (==) Assigned the driver to the xf86ConfigLayout
[   134.536] (II) LoadModule: "nvidia"
[   134.536] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   134.537] (II) Module nvidia: vendor="NVIDIA Corporation"
[   134.537]     compiled for 4.0.2, module version = 1.0.0
[   134.537]     Module class: X.Org Video Driver
[   134.537] (II) LoadModule: "nouveau"
[   134.537] (WW) Warning, couldn't open module nouveau
[   134.537] (II) UnloadModule: "nouveau"
[   134.537] (II) Unloading nouveau
[   134.537] (EE) Failed to load module "nouveau" (module does not exist, 0)
[   134.537] (II) LoadModule: "modesetting"
[   134.537] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   134.537] (II) Module modesetting: vendor="X.Org Foundation"
[   134.537]     compiled for 1.18.4, module version = 1.18.4
[   134.537]     Module class: X.Org Video Driver
[   134.537]     ABI class: X.Org Video Driver, version 20.0
[   134.537] (II) LoadModule: "fbdev"
[   134.537] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   134.538] (II) Module fbdev: vendor="X.Org Foundation"
[   134.538]     compiled for 1.18.1, module version = 0.4.4
[   134.538]     Module class: X.Org Video Driver
[   134.538]     ABI class: X.Org Video Driver, version 20.0
[   134.538] (II) LoadModule: "vesa"
[   134.538] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   134.538] (II) Module vesa: vendor="X.Org Foundation"
[   134.538]     compiled for 1.18.1, module version = 2.3.4
[   134.538]     Module class: X.Org Video Driver
[   134.538]     ABI class: X.Org Video Driver, version 20.0
[   134.538] (==) Matched nvidia as autoconfigured driver 0
[   134.538] (==) Matched nouveau as autoconfigured driver 1
[   134.538] (==) Matched nvidia as autoconfigured driver 2
[   134.538] (==) Matched nouveau as autoconfigured driver 3
[   134.538] (==) Matched modesetting as autoconfigured driver 4
[   134.538] (==) Matched fbdev as autoconfigured driver 5
[   134.538] (==) Matched vesa as autoconfigured driver 6
[   134.538] (==) Assigned the driver to the xf86ConfigLayout
[   134.538] (II) LoadModule: "nvidia"
[   134.538] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   134.538] (II) Module nvidia: vendor="NVIDIA Corporation"
[   134.538]     compiled for 4.0.2, module version = 1.0.0
[   134.538]     Module class: X.Org Video Driver
[   134.538] (II) UnloadModule: "nvidia"
[   134.538] (II) Unloading nvidia
[   134.538] (II) Failed to load module "nvidia" (already loaded, 4)
[   134.538] (II) LoadModule: "nouveau"
[   134.538] (WW) Warning, couldn't open module nouveau
[   134.538] (II) UnloadModule: "nouveau"
[   134.538] (II) Unloading nouveau
[   134.538] (EE) Failed to load module "nouveau" (module does not exist, 0)
[   134.538] (II) LoadModule: "modesetting"
[   134.538] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   134.538] (II) Module modesetting: vendor="X.Org Foundation"
[   134.538]     compiled for 1.18.4, module version = 1.18.4
[   134.538]     Module class: X.Org Video Driver
[   134.538]     ABI class: X.Org Video Driver, version 20.0
[   134.538] (II) UnloadModule: "modesetting"
[   134.538] (II) Unloading modesetting
[   134.538] (II) Failed to load module "modesetting" (already loaded, 0)
[   134.539] (II) LoadModule: "fbdev"
[   134.539] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   134.539] (II) Module fbdev: vendor="X.Org Foundation"
[   134.539]     compiled for 1.18.1, module version = 0.4.4
[   134.539]     Module class: X.Org Video Driver
[   134.539]     ABI class: X.Org Video Driver, version 20.0
[   134.539] (II) UnloadModule: "fbdev"
[   134.539] (II) Unloading fbdev
[   134.539] (II) Failed to load module "fbdev" (already loaded, 0)
[   134.539] (II) LoadModule: "vesa"
[   134.539] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   134.539] (II) Module vesa: vendor="X.Org Foundation"
[   134.539]     compiled for 1.18.1, module version = 2.3.4
[   134.539]     Module class: X.Org Video Driver
[   134.539]     ABI class: X.Org Video Driver, version 20.0
[   134.539] (II) UnloadModule: "vesa"
[   134.539] (II) Unloading vesa
[   134.539] (II) Failed to load module "vesa" (already loaded, 0)
[   134.539] (II) NVIDIA dlloader X Driver  375.39  Tue Jan 31 18:51:54 PST 2017
[   134.539] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   134.539] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   134.539] (II) FBDEV: driver for framebuffer: fbdev
[   134.539] (II) VESA: driver for VESA chipsets: vesa
[   134.539] xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
[   134.539] (II) systemd-logind: releasing fd for 226:0
[   134.540] (II) Loading sub module "fb"
[   134.540] (II) LoadModule: "fb"
[   134.540] (II) Loading /usr/lib/xorg/modules/libfb.so
[   134.540] (II) Module fb: vendor="X.Org Foundation"
[   134.540]     compiled for 1.18.4, module version = 1.0.0
[   134.540]     ABI class: X.Org ANSI C Emulation, version 0.4
[   134.540] (II) Loading sub module "wfb"
[   134.540] (II) LoadModule: "wfb"
[   134.540] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   134.540] (II) Module wfb: vendor="X.Org Foundation"
[   134.540]     compiled for 1.18.4, module version = 1.0.0
[   134.540]     ABI class: X.Org ANSI C Emulation, version 0.4
[   134.540] (II) Loading sub module "ramdac"
[   134.540] (II) LoadModule: "ramdac"
[   134.540] (II) Module "ramdac" already built-in
[   134.541] (WW) Falling back to old probe method for modesetting
[   134.541] (WW) Falling back to old probe method for fbdev
[   134.541] (II) Loading sub module "fbdevhw"
[   134.541] (II) LoadModule: "fbdevhw"
[   134.541] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   134.541] (II) Module fbdevhw: vendor="X.Org Foundation"
[   134.541]     compiled for 1.18.4, module version = 0.0.2
[   134.541]     ABI class: X.Org Video Driver, version 20.0
[   134.541] (EE) open /dev/fb0: No such file or directory
[   134.541] (EE) open /dev/fb0: No such file or directory
[   134.541] (WW) Falling back to old probe method for vesa
[   134.541] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[   134.541] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   134.541] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[   134.541] (==) NVIDIA(0): RGB weight 888
[   134.541] (==) NVIDIA(0): Default visual is TrueColor
[   134.541] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   134.541] (**) NVIDIA(0): Enabling 2D acceleration
[   134.543] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[   134.543] (--) NVIDIA(0):     CRT-0
[   134.543] (--) NVIDIA(0):     DFP-0
[   134.543] (--) NVIDIA(0):     DFP-1
[   134.543] (--) NVIDIA(0):     DFP-2
[   134.543] (--) NVIDIA(0):     DFP-3
[   134.543] (--) NVIDIA(0):     DFP-4 (boot)
[   134.546] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 970 (GM204-A) at PCI:1:0:0 (GPU-0)
[   134.546] (--) NVIDIA(0): Memory: 4194304 kBytes
[   134.546] (--) NVIDIA(0): VideoBIOS: 84.04.2f.00.50
[   134.546] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   134.549] (--) NVIDIA(GPU-0): CRT-0: disconnected
[   134.549] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[   134.549] (--) NVIDIA(GPU-0): 
[   134.551] (--) NVIDIA(GPU-0): DFP-0: disconnected
[   134.551] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[   134.551] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[   134.551] (--) NVIDIA(GPU-0): 
[   134.551] (--) NVIDIA(GPU-0): DFP-1: disconnected
[   134.552] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[   134.552] (--) NVIDIA(GPU-0): DFP-1: 330.0 MHz maximum pixel clock
[   134.552] (--) NVIDIA(GPU-0): 
[   134.552] (--) NVIDIA(GPU-0): DFP-2: disconnected
[   134.552] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[   134.552] (--) NVIDIA(GPU-0): DFP-2: 960.0 MHz maximum pixel clock
[   134.552] (--) NVIDIA(GPU-0): 
[   134.552] (--) NVIDIA(GPU-0): DFP-3: disconnected
[   134.552] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[   134.552] (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
[   134.552] (--) NVIDIA(GPU-0): 
[   134.568] (--) NVIDIA(GPU-0): DELL S2340M (DFP-4): connected
[   134.568] (--) NVIDIA(GPU-0): DELL S2340M (DFP-4): Internal TMDS
[   134.568] (--) NVIDIA(GPU-0): DELL S2340M (DFP-4): 330.0 MHz maximum pixel clock
[   134.568] (--) NVIDIA(GPU-0): 
[   134.570] (==) NVIDIA(0): 
[   134.570] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[   134.570] (==) NVIDIA(0):     will be used as the requested mode.
[   134.570] (==) NVIDIA(0): 
[   134.570] (II) NVIDIA(0): Validated MetaModes:
[   134.570] (II) NVIDIA(0):     "DFP-4:nvidia-auto-select"
[   134.570] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[   134.578] (--) NVIDIA(0): DPI set to (95, 94); computed from "UseEdidDpi" X config
[   134.578] (--) NVIDIA(0):     option
[   134.578] (II) UnloadModule: "modesetting"
[   134.578] (II) Unloading modesetting
[   134.578] (II) UnloadModule: "fbdev"
[   134.578] (II) Unloading fbdev
[   134.578] (II) UnloadSubModule: "fbdevhw"
[   134.578] (II) Unloading fbdevhw
[   134.578] (II) UnloadModule: "vesa"
[   134.578] (II) Unloading vesa
[   134.578] (--) Depth 24 pixmap format is 32 bpp
[   134.580] (II) NVIDIA: Using 1024.00 MB of virtual memory for indirect memory
[   134.580] (II) NVIDIA:     access.
[   134.633] (II) NVIDIA(0): Setting mode "DFP-4:nvidia-auto-select"
[   134.689] (==) NVIDIA(0): Disabling shared memory pixmaps
[   134.689] (==) NVIDIA(0): Backing store enabled
[   134.689] (==) NVIDIA(0): Silken mouse enabled
[   134.690] (==) NVIDIA(0): DPMS enabled
[   134.690] (II) Loading sub module "dri2"
[   134.690] (II) LoadModule: "dri2"
[   134.690] (II) Module "dri2" already built-in
[   134.690] (II) NVIDIA(0): [DRI2] Setup complete
[   134.690] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[   134.690] (--) RandR disabled
[   134.692] (II) SELinux: Disabled on system
[   134.693] (II) Initializing extension GLX
[   134.693] (II) Indirect GLX disabled.
[   134.715] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   134.715] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   134.715] (II) LoadModule: "evdev"
[   134.715] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   134.715] (II) Module evdev: vendor="X.Org Foundation"
[   134.715]     compiled for 1.18.1, module version = 2.10.1
[   134.715]     Module class: X.Org XInput Driver
[   134.715]     ABI class: X.Org XInput driver, version 22.1
[   134.715] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 26 paused 0
[   134.716] (II) Using input driver 'evdev' for 'Power Button'
[   134.716] (**) Power Button: always reports core events
[   134.716] (**) evdev: Power Button: Device: "/dev/input/event1"
[   134.716] (--) evdev: Power Button: Vendor 0 Product 0x1
[   134.716] (--) evdev: Power Button: Found keys
[   134.716] (II) evdev: Power Button: Configuring as keyboard
[   134.716] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   134.716] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   134.716] (**) Option "xkb_rules" "evdev"
[   134.716] (**) Option "xkb_model" "pc105"
[   134.716] (**) Option "xkb_layout" "us"
[   134.716] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   134.716] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   134.716] (II) systemd-logind: got fd for /dev/input/event0 13:64 fd 27 paused 0
[   134.716] (II) Using input driver 'evdev' for 'Power Button'
[   134.716] (**) Power Button: always reports core events
[   134.716] (**) evdev: Power Button: Device: "/dev/input/event0"
[   134.716] (--) evdev: Power Button: Vendor 0 Product 0x1
[   134.716] (--) evdev: Power Button: Found keys
[   134.716] (II) evdev: Power Button: Configuring as keyboard
[   134.716] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[   134.716] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   134.716] (**) Option "xkb_rules" "evdev"
[   134.716] (**) Option "xkb_model" "pc105"
[   134.716] (**) Option "xkb_layout" "us"
[   134.717] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event12)
[   134.717] (II) No input driver specified, ignoring this device.
[   134.717] (II) This device may have been added with another device file.
[   134.717] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event13)
[   134.717] (II) No input driver specified, ignoring this device.
[   134.717] (II) This device may have been added with another device file.
[   134.717] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event14)
[   134.717] (II) No input driver specified, ignoring this device.
[   134.717] (II) This device may have been added with another device file.
[   134.717] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event15)
[   134.717] (II) No input driver specified, ignoring this device.
[   134.717] (II) This device may have been added with another device file.
[   134.717] (II) config/udev: Adding input device USB Keyboard (/dev/input/event2)
[   134.717] (**) USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   134.718] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 28 paused 0
[   134.718] (II) Using input driver 'evdev' for 'USB Keyboard'
[   134.718] (**) USB Keyboard: always reports core events
[   134.718] (**) evdev: USB Keyboard: Device: "/dev/input/event2"
[   134.718] (--) evdev: USB Keyboard: Vendor 0x4d9 Product 0x169
[   134.718] (--) evdev: USB Keyboard: Found keys
[   134.718] (II) evdev: USB Keyboard: Configuring as keyboard
[   134.718] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/0003:04D9:0169.0001/input/input5/event2"
[   134.718] (II) XINPUT: Adding extended input device "USB Keyboard" (type: KEYBOARD, id 8)
[   134.718] (**) Option "xkb_rules" "evdev"
[   134.718] (**) Option "xkb_model" "pc105"
[   134.718] (**) Option "xkb_layout" "us"
[   134.718] (II) config/udev: Adding input device USB Keyboard (/dev/input/event3)
[   134.718] (**) USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   134.718] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 29 paused 0
[   134.718] (II) Using input driver 'evdev' for 'USB Keyboard'
[   134.718] (**) USB Keyboard: always reports core events
[   134.718] (**) evdev: USB Keyboard: Device: "/dev/input/event3"
[   134.718] (--) evdev: USB Keyboard: Vendor 0x4d9 Product 0x169
[   134.718] (--) evdev: USB Keyboard: Found keys
[   134.718] (II) evdev: USB Keyboard: Configuring as keyboard
[   134.718] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.1/0003:04D9:0169.0002/input/input6/event3"
[   134.718] (II) XINPUT: Adding extended input device "USB Keyboard" (type: KEYBOARD, id 9)
[   134.718] (**) Option "xkb_rules" "evdev"
[   134.718] (**) Option "xkb_model" "pc105"
[   134.718] (**) Option "xkb_layout" "us"
[   134.719] (II) config/udev: Adding input device Corsair Corsair M65 RGB Gaming Mouse (/dev/input/event4)
[   134.719] (**) Corsair Corsair M65 RGB Gaming Mouse: Applying InputClass "evdev pointer catchall"
[   134.772] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 30 paused 0
[   134.772] (II) Using input driver 'evdev' for 'Corsair Corsair M65 RGB Gaming Mouse'
[   134.772] (**) Corsair Corsair M65 RGB Gaming Mouse: always reports core events
[   134.772] (**) evdev: Corsair Corsair M65 RGB Gaming Mouse: Device: "/dev/input/event4"
[   134.772] (--) evdev: Corsair Corsair M65 RGB Gaming Mouse: Vendor 0x1b1c Product 0x1b12
[   134.772] (--) evdev: Corsair Corsair M65 RGB Gaming Mouse: Found 9 mouse buttons
[   134.772] (--) evdev: Corsair Corsair M65 RGB Gaming Mouse: Found scroll wheel(s)
[   134.772] (--) evdev: Corsair Corsair M65 RGB Gaming Mouse: Found relative axes
[   134.772] (--) evdev: Corsair Corsair M65 RGB Gaming Mouse: Found x and y relative axes
[   134.772] (II) evdev: Corsair Corsair M65 RGB Gaming Mouse: Configuring as mouse
[   134.772] (II) evdev: Corsair Corsair M65 RGB Gaming Mouse: Adding scrollwheel support
[   134.772] (**) evdev: Corsair Corsair M65 RGB Gaming Mouse: YAxisMapping: buttons 4 and 5
[   134.772] (**) evdev: Corsair Corsair M65 RGB Gaming Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   134.772] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/0003:1B1C:1B12.0003/input/input7/event4"
[   134.772] (II) XINPUT: Adding extended input device "Corsair Corsair M65 RGB Gaming Mouse" (type: MOUSE, id 10)
[   134.772] (II) evdev: Corsair Corsair M65 RGB Gaming Mouse: initialized for relative axes.
[   134.772] (**) Corsair Corsair M65 RGB Gaming Mouse: (accel) keeping acceleration scheme 1
[   134.772] (**) Corsair Corsair M65 RGB Gaming Mouse: (accel) acceleration profile 0
[   134.772] (**) Corsair Corsair M65 RGB Gaming Mouse: (accel) acceleration factor: 2.000
[   134.772] (**) Corsair Corsair M65 RGB Gaming Mouse: (accel) acceleration threshold: 4
[   134.772] (II) config/udev: Adding input device Corsair Corsair M65 RGB Gaming Mouse (/dev/input/mouse0)
[   134.772] (II) No input driver specified, ignoring this device.
[   134.772] (II) This device may have been added with another device file.
[   134.772] (II) config/udev: Adding input device Corsair Corsair M65 RGB Gaming Mouse (/dev/input/event5)
[   134.772] (**) Corsair Corsair M65 RGB Gaming Mouse: Applying InputClass "evdev pointer catchall"
[   134.772] (**) Corsair Corsair M65 RGB Gaming Mouse: Applying InputClass "evdev keyboard catchall"
[   134.773] (II) systemd-logind: got fd for /dev/input/event5 13:69 fd 31 paused 0
[   134.773] (II) Using input driver 'evdev' for 'Corsair Corsair M65 RGB Gaming Mouse'
[   134.773] (**) Corsair Corsair M65 RGB Gaming Mouse: always reports core events
[   134.773] (**) evdev: Corsair Corsair M65 RGB Gaming Mouse: Device: "/dev/input/event5"
[   134.773] (--) evdev: Corsair Corsair M65 RGB Gaming Mouse: Vendor 0x1b1c Product 0x1b12
[   134.773] (--) evdev: Corsair Corsair M65 RGB Gaming Mouse: Found 20 mouse buttons
[   134.773] (--) evdev: Corsair Corsair M65 RGB Gaming Mouse: Found scroll wheel(s)
[   134.773] (--) evdev: Corsair Corsair M65 RGB Gaming Mouse: Found relative axes
[   134.773] (--) evdev: Corsair Corsair M65 RGB Gaming Mouse: Found x and y relative axes
[   134.773] (--) evdev: Corsair Corsair M65 RGB Gaming Mouse: Found keys
[   134.773] (II) evdev: Corsair Corsair M65 RGB Gaming Mouse: Configuring as mouse
[   134.773] (II) evdev: Corsair Corsair M65 RGB Gaming Mouse: Configuring as keyboard
[   134.773] (II) evdev: Corsair Corsair M65 RGB Gaming Mouse: Adding scrollwheel support
[   134.773] (**) evdev: Corsair Corsair M65 RGB Gaming Mouse: YAxisMapping: buttons 4 and 5
[   134.773] (**) evdev: Corsair Corsair M65 RGB Gaming Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   134.773] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.1/0003:1B1C:1B12.0004/input/input8/event5"
[   134.773] (II) XINPUT: Adding extended input device "Corsair Corsair M65 RGB Gaming Mouse" (type: KEYBOARD, id 11)
[   134.773] (**) Option "xkb_rules" "evdev"
[   134.773] (**) Option "xkb_model" "pc105"
[   134.773] (**) Option "xkb_layout" "us"
[   134.773] (II) evdev: Corsair Corsair M65 RGB Gaming Mouse: initialized for relative axes.
[   134.773] (**) Corsair Corsair M65 RGB Gaming Mouse: (accel) keeping acceleration scheme 1
[   134.773] (**) Corsair Corsair M65 RGB Gaming Mouse: (accel) acceleration profile 0
[   134.773] (**) Corsair Corsair M65 RGB Gaming Mouse: (accel) acceleration factor: 2.000
[   134.773] (**) Corsair Corsair M65 RGB Gaming Mouse: (accel) acceleration threshold: 4
[   134.773] (II) config/udev: Adding input device Corsair Corsair M65 RGB Gaming Mouse (/dev/input/js0)
[   134.773] (II) No input driver specified, ignoring this device.
[   134.773] (II) This device may have been added with another device file.
[   134.774] (II) config/udev: Adding input device Corsair Corsair M65 RGB Gaming Mouse (/dev/input/mouse1)
[   134.774] (II) No input driver specified, ignoring this device.
[   134.774] (II) This device may have been added with another device file.
[   134.774] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event7)
[   134.774] (II) No input driver specified, ignoring this device.
[   134.774] (II) This device may have been added with another device file.
[   134.774] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event8)
[   134.774] (II) No input driver specified, ignoring this device.
[   134.774] (II) This device may have been added with another device file.
[   134.774] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event9)
[   134.774] (II) No input driver specified, ignoring this device.
[   134.774] (II) This device may have been added with another device file.
[   134.774] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event10)
[   134.774] (II) No input driver specified, ignoring this device.
[   134.774] (II) This device may have been added with another device file.
[   134.774] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event6)
[   134.774] (II) No input driver specified, ignoring this device.
[   134.774] (II) This device may have been added with another device file.
[   134.774] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event11)
[   134.774] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[   134.775] (II) systemd-logind: got fd for /dev/input/event11 13:75 fd 32 paused 0
[   134.775] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[   134.775] (**) Eee PC WMI hotkeys: always reports core events
[   134.775] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event11"
[   134.775] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[   134.775] (--) evdev: Eee PC WMI hotkeys: Found keys
[   134.775] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[   134.775] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input14/event11"
[   134.775] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 12)
[   134.775] (**) Option "xkb_rules" "evdev"
[   134.775] (**) Option "xkb_model" "pc105"
[   134.775] (**) Option "xkb_layout" "us"
[   155.427] (II) systemd-logind: got pause for 13:68
[   155.427] (II) systemd-logind: got pause for 13:75
[   155.427] (II) systemd-logind: got pause for 13:66
[   155.427] (II) systemd-logind: got pause for 13:67
[   155.427] (II) systemd-logind: got pause for 13:65
[   155.427] (II) systemd-logind: got pause for 13:69
[   155.427] (II) systemd-logind: got pause for 13:64
[   374.833] (II) evdev: Eee PC WMI hotkeys: Close
[   374.833] (II) UnloadModule: "evdev"
[   374.833] (II) systemd-logind: releasing fd for 13:75
[   374.844] (II) evdev: Corsair Corsair M65 RGB Gaming Mouse: Close
[   374.844] (II) UnloadModule: "evdev"
[   374.844] (II) systemd-logind: releasing fd for 13:69
[   374.856] (II) evdev: Corsair Corsair M65 RGB Gaming Mouse: Close
[   374.856] (II) UnloadModule: "evdev"
[   374.856] (II) systemd-logind: releasing fd for 13:68
[   374.872] (II) evdev: USB Keyboard: Close
[   374.872] (II) UnloadModule: "evdev"
[   374.872] (II) systemd-logind: releasing fd for 13:67
[   374.884] (II) evdev: USB Keyboard: Close
[   374.884] (II) UnloadModule: "evdev"
[   374.884] (II) systemd-logind: releasing fd for 13:66
[   374.896] (II) evdev: Power Button: Close
[   374.896] (II) UnloadModule: "evdev"
[   374.896] (II) systemd-logind: releasing fd for 13:64
[   374.908] (II) evdev: Power Button: Close
[   374.908] (II) UnloadModule: "evdev"
[   374.908] (II) systemd-logind: releasing fd for 13:65
[   374.927] (II) NVIDIA(GPU-0): Deleting GPU-0
[   374.933] (II) Server terminated successfully (0). Closing log file.

```
So far, I have tried changing the owner and permissions of my ~/.Xauthority file reinstalling my nvidia-375 driver, reconfiguring x and my nvidia-375 driver, deleting lightdm and using gdm, and deleting lightdm and booting from the console, all with no luck. I am on Ubuntu 16.04. Anyone else have this issue?

---

### Post by xblinky on 2017-05-16
Im having the same issue still nothing ;(

---

### Post by sean119 on 2017-05-16
I made a little progress. Now, I can boot into lightdm, then go into tty1 and do 'startx'(no sudo) to get the white gui terminal. From here, 'startxfce'(also no sudo) will start xfce. 'startxfce4' must be executed from the gui terminal after 'startx', or else it throws an error. This is okay, but is just a really big annoyance. The lightdm login loop still occurs. Also, booting directly to tty1, and skipping lightdm, will throw an error for both 'startx' and 'startxfce4'. If anyone has a suggestion, please chime in.

---

