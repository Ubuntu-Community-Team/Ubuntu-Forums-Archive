---
title: "Mouse pointer dissapearing 12.10"
date: 2012-12-13
forum: General Help
---

### Post by GodspeedyouBlackEmperor on 2012-12-13
Hello.
I am new to Ubuntu, I just installed Ubuntu 12.10 because I was tired of windows.
I did a few updates, followed a few guides to make Ubuntu faster because it was running too slow. And I got some big changes, way faster now.

The problem is that my mouse pointer dissapears whenever I am not moving it, now.

Any ideas?

Keep in mind that I know next to nothing about this OS and how it works, so try to keep it simple.

Regards.

---

### Post by scbingham on 2012-12-14
I have the same problem with ubuntu 12.04 using unity.

I've been searching for a solution for weeks but to no avail

---

### Post by GodspeedyouBlackEmperor on 2012-12-14
> **scbingham said:**
> I have the same problem with ubuntu 12.04 using unity.

I've been searching for a solution for weeks but to no avail

This happened after I updated some related to the video drivers, I think.
I was stuck at 800x600 resolution, after fixing it, this pointer problem came up.

---

### Post by scbingham on 2012-12-14
My resolution is 1024 x 768 (4:3)
So I don't think that's my problem.

I'm also not using any proprietary drivers. 

Thanks for the pointer, I'll play with other resolutions.

---

### Post by GodspeedyouBlackEmperor on 2012-12-15
Anyone?

---

### Post by Rexilion on 2012-12-15
What video driver are you guys using?

Consult the file /var/log/Xorg.0.log for this.

What did you do before this problem showed up? I.e. be more specific like what packages did you update, what guides did you follow.

And most of all, what kind of video hardware do you have? And do you all use Unity??

---

### Post by GodspeedyouBlackEmperor on 2012-12-15
I will have to paste the full file info because I don't know how to find them.

```
[    15.041] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    15.041] X Protocol Version 11, Revision 0
[    15.041] Build Operating System: Linux 3.2.0-26-generic i686 Ubuntu
[    15.041] Current Operating System: Linux pedrofradique 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:49:53 UTC 2012 i686
[    15.041] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-19-generic root=UUID=7ecbcf22-cf95-4804-9e41-46d0cad3348e ro quiet splash
[    15.041] Build Date: 27 November 2012  07:44:37AM
[    15.041] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    15.041] Current version of pixman: 0.26.0
[    15.041]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    15.041] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.041] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 15 20:38:42 2012
[    15.041] (==) Using config file: "/etc/X11/xorg.conf"
[    15.041] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.042] (==) ServerLayout "Layout0"
[    15.042] (**) |-->Screen "Screen0" (0)
[    15.042] (**) |   |-->Monitor "Monitor0"
[    15.042] (**) |   |-->Device "Device0"
[    15.042] (==) Automatically adding devices
[    15.042] (==) Automatically enabling devices
[    15.042] (==) Automatically adding GPU devices
[    15.042] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.042]     Entry deleted from font path.
[    15.042] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.042]     Entry deleted from font path.
[    15.042] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.042]     Entry deleted from font path.
[    15.042] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.042]     Entry deleted from font path.
[    15.042] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.042]     Entry deleted from font path.
[    15.042] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    15.042]     Entry deleted from font path.
[    15.042] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    15.042] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.042] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.042] (II) Loader magic: 0xb770d640
[    15.042] (II) Module ABI versions:
[    15.042]     X.Org ANSI C Emulation: 0.4
[    15.042]     X.Org Video Driver: 13.0
[    15.042]     X.Org XInput driver : 18.0
[    15.042]     X.Org Server Extension : 7.0
[    15.045] (--) PCI:*(0:1:0:0) 10de:06ec:1025:0205 rev 161, Mem @ 0xf2000000/16777216, 0xd0000000/268435456, 0xf0000000/33554432, I/O @ 0x00002000/128
[    15.045] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.045] Initializing built-in extension Generic Event Extension
[    15.045] Initializing built-in extension SHAPE
[    15.045] Initializing built-in extension MIT-SHM
[    15.045] Initializing built-in extension XInputExtension
[    15.045] Initializing built-in extension XTEST
[    15.045] Initializing built-in extension BIG-REQUESTS
[    15.045] Initializing built-in extension SYNC
[    15.045] Initializing built-in extension XKEYBOARD
[    15.045] Initializing built-in extension XC-MISC
[    15.045] Initializing built-in extension SECURITY
[    15.045] Initializing built-in extension XINERAMA
[    15.045] Initializing built-in extension XFIXES
[    15.045] Initializing built-in extension RENDER
[    15.045] Initializing built-in extension RANDR
[    15.045] Initializing built-in extension COMPOSITE
[    15.045] Initializing built-in extension DAMAGE
[    15.045] Initializing built-in extension MIT-SCREEN-SAVER
[    15.045] Initializing built-in extension DOUBLE-BUFFER
[    15.045] Initializing built-in extension RECORD
[    15.045] Initializing built-in extension DPMS
[    15.045] Initializing built-in extension X-Resource
[    15.045] Initializing built-in extension XVideo
[    15.045] Initializing built-in extension XVideo-MotionCompensation
[    15.045] Initializing built-in extension XFree86-VidModeExtension
[    15.045] Initializing built-in extension XFree86-DGA
[    15.045] Initializing built-in extension XFree86-DRI
[    15.045] Initializing built-in extension DRI2
[    15.045] (II) LoadModule: "glx"
[    15.047] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    15.079] (II) Module glx: vendor="NVIDIA Corporation"
[    15.079]     compiled for 4.0.2, module version = 1.0.0
[    15.079]     Module class: X.Org Server Extension
[    15.079] (II) NVIDIA GLX Module  304.43  Sun Aug 19 20:41:51 PDT 2012
[    15.079] Loading extension GLX
[    15.079] (II) LoadModule: "openchrome"
[    15.095] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
[    15.095] (II) Module openchrome: vendor="http://openchrome.org/"
[    15.095]     compiled for 1.12.99.905, module version = 0.3.1
[    15.095]     Module class: X.Org Video Driver
[    15.095]     ABI class: X.Org Video Driver, version 13.0
[    15.095] (II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
    K8M800/K8N800, PM800/PM880/CN400, VM800/P4M800Pro/VN800/CN700,
    CX700/VX700, K8M890/K8N890, P4M890, P4M900/VN896/CN896, VX800/VX820,
    VX855/VX875, VX900
[    15.095] (++) using VT number 7

[    15.097] (EE) No devices detected.
[    15.097] (==) Matched nvidia as autoconfigured driver 0
[    15.097] (==) Matched nouveau as autoconfigured driver 1
[    15.097] (==) Matched nv as autoconfigured driver 2
[    15.097] (==) Matched vesa as autoconfigured driver 3
[    15.097] (==) Matched modesetting as autoconfigured driver 4
[    15.097] (==) Matched fbdev as autoconfigured driver 5
[    15.097] (==) Assigned the driver to the xf86ConfigLayout
[    15.097] (II) LoadModule: "nvidia"
[    15.097] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    15.098] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.098]     compiled for 4.0.2, module version = 1.0.0
[    15.098]     Module class: X.Org Video Driver
[    15.098] (II) LoadModule: "nouveau"
[    15.098] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    15.098] (II) Module nouveau: vendor="X.Org Foundation"
[    15.098]     compiled for 1.13.0, module version = 1.0.2
[    15.098]     Module class: X.Org Video Driver
[    15.098]     ABI class: X.Org Video Driver, version 13.0
[    15.098] (II) LoadModule: "nv"
[    15.099] (WW) Warning, couldn't open module nv
[    15.099] (II) UnloadModule: "nv"
[    15.099] (II) Unloading nv
[    15.099] (EE) Failed to load module "nv" (module does not exist, 0)
[    15.099] (II) LoadModule: "vesa"
[    15.099] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.099] (II) Module vesa: vendor="X.Org Foundation"
[    15.099]     compiled for 1.12.99.902, module version = 2.3.2
[    15.099]     Module class: X.Org Video Driver
[    15.099]     ABI class: X.Org Video Driver, version 13.0
[    15.099] (II) LoadModule: "modesetting"
[    15.100] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    15.100] (II) Module modesetting: vendor="X.Org Foundation"
[    15.100]     compiled for 1.13.0, module version = 0.5.0
[    15.100]     Module class: X.Org Video Driver
[    15.100]     ABI class: X.Org Video Driver, version 13.0
[    15.100] (II) LoadModule: "fbdev"
[    15.100] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.100] (II) Module fbdev: vendor="X.Org Foundation"
[    15.100]     compiled for 1.12.99.902, module version = 0.4.3
[    15.100]     Module class: X.Org Video Driver
[    15.100]     ABI class: X.Org Video Driver, version 13.0
[    15.100] (II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
    K8M800/K8N800, PM800/PM880/CN400, VM800/P4M800Pro/VN800/CN700,
    CX700/VX700, K8M890/K8N890, P4M890, P4M900/VN896/CN896, VX800/VX820,
    VX855/VX875, VX900
[    15.100] (II) NVIDIA dlloader X Driver  304.43  Sun Aug 19 20:21:53 PDT 2012
[    15.100] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    15.100] (II) NOUVEAU driver Date:   Wed Sep 12 13:42:43 2012 +0200
[    15.100] (II) NOUVEAU driver for NVIDIA chipset families :
[    15.100]     RIVA TNT        (NV04)
[    15.100]     RIVA TNT2       (NV05)
[    15.100]     GeForce 256     (NV10)
[    15.100]     GeForce 2       (NV11, NV15)
[    15.100]     GeForce 4MX     (NV17, NV18)
[    15.101]     GeForce 3       (NV20)
[    15.101]     GeForce 4Ti     (NV25, NV28)
[    15.101]     GeForce FX      (NV3x)
[    15.101]     GeForce 6       (NV4x)
[    15.101]     GeForce 7       (G7x)
[    15.101]     GeForce 8       (G8x)
[    15.101]     GeForce GTX 200 (NVA0)
[    15.101]     GeForce GTX 400 (NVC0)
[    15.101] (II) VESA: driver for VESA chipsets: vesa
[    15.101] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    15.101] (II) FBDEV: driver for framebuffer: fbdev
[    15.101] (++) using VT number 7

[    15.101] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    15.101] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    15.101] (II) Loading sub module "fb"
[    15.101] (II) LoadModule: "fb"
[    15.101] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.101] (II) Module fb: vendor="X.Org Foundation"
[    15.101]     compiled for 1.13.0, module version = 1.0.0
[    15.101]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.101] (II) Loading sub module "wfb"
[    15.101] (II) LoadModule: "wfb"
[    15.102] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    15.102] (II) Module wfb: vendor="X.Org Foundation"
[    15.102]     compiled for 1.13.0, module version = 1.0.0
[    15.102]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.102] (II) Loading sub module "ramdac"
[    15.102] (II) LoadModule: "ramdac"
[    15.102] (II) Module "ramdac" already built-in
[    15.102] (WW) Falling back to old probe method for vesa
[    15.102] (WW) Falling back to old probe method for modesetting
[    15.102] (EE) open /dev/dri/card0: No such file or directory
[    15.102] (WW) Falling back to old probe method for fbdev
[    15.102] (II) Loading sub module "fbdevhw"
[    15.102] (II) LoadModule: "fbdevhw"
[    15.102] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.102] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.102]     compiled for 1.13.0, module version = 0.0.2
[    15.102]     ABI class: X.Org Video Driver, version 13.0
[    15.102] (EE) open /dev/fb0: No such file or directory
[    15.103] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    15.103] (==) NVIDIA(0): RGB weight 888
[    15.103] (==) NVIDIA(0): Default visual is TrueColor
[    15.103] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    15.103] (**) NVIDIA(0): Option "SWcursor"
[    15.103] (**) NVIDIA(0): Option "DPI" "96 x 96"
[    15.103] (**) NVIDIA(0): Option "MetaModes" "1366x768"
[    15.103] (**) NVIDIA(0): Enabling 2D acceleration
[    17.092] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    17.092] (II) NVIDIA(GPU-0):     Vision stereo.
[    17.094] (II) NVIDIA(0): NVIDIA GPU GeForce G 105M (G98) at PCI:1:0:0 (GPU-0)
[    17.094] (--) NVIDIA(0): Memory: 524288 kBytes
[    17.094] (--) NVIDIA(0): VideoBIOS: 62.98.5a.00.18
[    17.094] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    17.094] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    17.096] (--) NVIDIA(0): Valid display device(s) on GeForce G 105M at PCI:1:0:0
[    17.096] (--) NVIDIA(0):     CRT-0
[    17.096] (--) NVIDIA(0):     Seiko/Epson (DFP-0) (connected)
[    17.096] (--) NVIDIA(0):     DFP-1
[    17.096] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    17.096] (--) NVIDIA(0): Seiko/Epson (DFP-0): 330.0 MHz maximum pixel clock
[    17.096] (--) NVIDIA(0): Seiko/Epson (DFP-0): Internal Dual Link LVDS
[    17.096] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    17.096] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    17.096] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    17.096] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[    17.096] (**) NVIDIA(0):     been enabled on all display devices.)
[    17.097] (II) NVIDIA(0): Validated MetaModes:
[    17.097] (II) NVIDIA(0):     "1366x768"
[    17.097] (II) NVIDIA(0): Virtual screen size determined to be 1366 x 768
[    18.145] (**) NVIDIA(0): DPI set to (96, 96); computed from "DPI" X config option
[    18.145] (II) UnloadModule: "openchrome"
[    18.145] (II) Unloading openchrome
[    18.145] (II) UnloadModule: "nouveau"
[    18.145] (II) Unloading nouveau
[    18.145] (II) UnloadModule: "vesa"
[    18.145] (II) Unloading vesa
[    18.145] (II) UnloadModule: "modesetting"
[    18.145] (II) Unloading modesetting
[    18.145] (II) UnloadModule: "fbdev"
[    18.145] (II) Unloading fbdev
[    18.145] (II) UnloadSubModule: "fbdevhw"
[    18.145] (II) Unloading fbdevhw
[    18.145] (--) Depth 24 pixmap format is 32 bpp
[    18.146] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    18.153] (II) NVIDIA(0): Setting mode "1366x768"
[    18.450] Loading extension NV-GLX
[    18.472] (==) NVIDIA(0): Disabling shared memory pixmaps
[    18.472] (==) NVIDIA(0): Backing store disabled
[    18.472] (==) NVIDIA(0): Silken mouse enabled
[    18.473] Loading extension NV-CONTROL
[    18.473] Loading extension XINERAMA
[    18.473] (WW) NVIDIA(0): Option "PanelSize" is not used
[    18.473] (WW) NVIDIA(0): Option "TwinView" is not used
[    18.473] (II) Loading sub module "dri2"
[    18.473] (II) LoadModule: "dri2"
[    18.473] (II) Module "dri2" already built-in
[    18.473] (II) NVIDIA(0): [DRI2] Setup complete
[    18.473] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    18.473] (--) RandR disabled
[    18.483] (II) Initializing extension GLX
[    18.501] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.504] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    18.504] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.504] (II) LoadModule: "evdev"
[    18.504] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.504] (II) Module evdev: vendor="X.Org Foundation"
[    18.504]     compiled for 1.13.0, module version = 2.7.3
[    18.504]     Module class: X.Org XInput Driver
[    18.504]     ABI class: X.Org XInput driver, version 18.0
[    18.504] (II) Using input driver 'evdev' for 'Power Button'
[    18.505] (**) Power Button: always reports core events
[    18.505] (**) evdev: Power Button: Device: "/dev/input/event2"
[    18.505] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.505] (--) evdev: Power Button: Found keys
[    18.505] (II) evdev: Power Button: Configuring as keyboard
[    18.505] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    18.505] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    18.505] (**) Option "xkb_rules" "evdev"
[    18.505] (**) Option "xkb_model" "pc105"
[    18.505] (**) Option "xkb_layout" "pt"
[    18.507] (II) XKB: reuse xkmfile /var/lib/xkb/server-8F12297C8ADF2DCAF94655EF02F153CE34CF92F1.xkm
[    18.508] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    18.508] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.508] (II) Using input driver 'evdev' for 'Video Bus'
[    18.508] (**) Video Bus: always reports core events
[    18.508] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    18.508] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    18.508] (--) evdev: Video Bus: Found keys
[    18.508] (II) evdev: Video Bus: Configuring as keyboard
[    18.508] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input4/event4"
[    18.508] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    18.508] (**) Option "xkb_rules" "evdev"
[    18.508] (**) Option "xkb_model" "pc105"
[    18.509] (**) Option "xkb_layout" "pt"
[    18.509] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    18.509] (II) No input driver specified, ignoring this device.
[    18.509] (II) This device may have been added with another device file.
[    18.509] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    18.509] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    18.509] (II) Using input driver 'evdev' for 'Sleep Button'
[    18.509] (**) Sleep Button: always reports core events
[    18.509] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    18.510] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    18.510] (--) evdev: Sleep Button: Found keys
[    18.510] (II) evdev: Sleep Button: Configuring as keyboard
[    18.510] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    18.510] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    18.510] (**) Option "xkb_rules" "evdev"
[    18.510] (**) Option "xkb_model" "pc105"
[    18.510] (**) Option "xkb_layout" "pt"
[    18.510] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event7)
[    18.510] (II) No input driver specified, ignoring this device.
[    18.510] (II) This device may have been added with another device file.
[    18.511] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event8)
[    18.511] (II) No input driver specified, ignoring this device.
[    18.511] (II) This device may have been added with another device file.
[    18.511] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event9)
[    18.511] (II) No input driver specified, ignoring this device.
[    18.511] (II) This device may have been added with another device file.
[    18.511] (II) config/udev: Adding input device Video WebCam (/dev/input/event5)
[    18.511] (**) Video WebCam: Applying InputClass "evdev keyboard catchall"
[    18.511] (II) Using input driver 'evdev' for 'Video WebCam'
[    18.511] (**) Video WebCam: always reports core events
[    18.511] (**) evdev: Video WebCam: Device: "/dev/input/event5"
[    18.511] (--) evdev: Video WebCam: Vendor 0x64e Product 0xa103
[    18.511] (--) evdev: Video WebCam: Found keys
[    18.511] (II) evdev: Video WebCam: Configuring as keyboard
[    18.511] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input5/event5"
[    18.511] (II) XINPUT: Adding extended input device "Video WebCam" (type: KEYBOARD, id 9)
[    18.511] (**) Option "xkb_rules" "evdev"
[    18.511] (**) Option "xkb_model" "pc105"
[    18.511] (**) Option "xkb_layout" "pt"
[    18.512] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    18.512] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.512] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    18.512] (**) AT Translated Set 2 keyboard: always reports core events
[    18.512] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    18.512] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    18.512] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    18.512] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    18.512] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    18.512] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    18.512] (**) Option "xkb_rules" "evdev"
[    18.512] (**) Option "xkb_model" "pc105"
[    18.512] (**) Option "xkb_layout" "pt"
[    18.513] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event10)
[    18.513] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    18.513] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    18.513] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    18.513] (II) LoadModule: "synaptics"
[    18.513] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.513] (II) Module synaptics: vendor="X.Org Foundation"
[    18.513]     compiled for 1.12.99.905, module version = 1.6.2
[    18.513]     Module class: X.Org XInput Driver
[    18.513]     ABI class: X.Org XInput driver, version 18.0
[    18.513] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    18.513] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.513] (**) Option "Device" "/dev/input/event10"
[    18.514] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    18.514] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5720
[    18.514] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4780
[    18.514] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    18.514] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    18.514] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple scroll-buttons
[    18.514] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    18.514] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    18.514] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.514] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event10"
[    18.514] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    18.514] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    18.514] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    18.514] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[    18.514] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    18.514] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    18.514] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    18.514] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    18.514] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    18.515] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    18.515] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    18.517] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/event6)
[    18.517] (II) No input driver specified, ignoring this device.
[    18.517] (II) This device may have been added with another device file.
[    18.517] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/js0)
[    18.517] (II) No input driver specified, ignoring this device.
[    18.517] (II) This device may have been added with another device file.
[    19.098] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    19.098] (II) NVIDIA(GPU-0):     Vision stereo.
[    19.098] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    19.098] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[    19.098] (**) NVIDIA(0):     been enabled on all display devices.)
[    19.755] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    19.755] (II) NVIDIA(GPU-0):     Vision stereo.
[    19.755] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    19.755] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[    19.755] (**) NVIDIA(0):     been enabled on all display devices.)
[    25.099] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    25.099] (II) NVIDIA(GPU-0):     Vision stereo.
[    25.099] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    25.099] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[    25.099] (**) NVIDIA(0):     been enabled on all display devices.)
[    26.048] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    26.048] (II) NVIDIA(GPU-0):     Vision stereo.
[    26.048] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    26.048] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[    26.048] (**) NVIDIA(0):     been enabled on all display devices.)
[    26.626] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    26.626] (II) NVIDIA(GPU-0):     Vision stereo.
[    26.626] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    26.626] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[    26.626] (**) NVIDIA(0):     been enabled on all display devices.)
[    34.279] (II) XKB: reuse xkmfile /var/lib/xkb/server-F2C88B7419AC050E88E48E1C101D563358E39BA3.xkm
[   121.068] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[   121.068] (II) NVIDIA(GPU-0):     Vision stereo.
[   121.068] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   121.068] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[   121.068] (**) NVIDIA(0):     been enabled on all display devices.)
[   780.518] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[   780.518] (II) NVIDIA(GPU-0):     Vision stereo.
[   780.518] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   780.518] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[   780.518] (**) NVIDIA(0):     been enabled on all display devices.)
```I honestly don't know what I have done, I don't know where I found them either, too much googling those days, was tired of following guides already.

And yes, I ise unity, I think.
Its the thing that gives you the side bar and stuff, right?

---

### Post by Rexilion on 2012-12-16
That would be:

'[ 17.094] (II) NVIDIA(0): NVIDIA GPU GeForce G 105M (G98) at PCI:1:0:0 (GPU-0)'

nVidia proprietary driver plus nVidia G98. Anyone else?

---

### Post by scbingham on 2012-12-17
I had a trawl through that file & the only video type entries all start with: (II) VESA(0)

This may be of interest: (II) VESA: driver for VESA chipsets: vesa

Manufacturer is SiS.

My laptop is a bog standard Advent 5301.

My mouse pointer has always disappeared since day 1 of a clean installation of 12.04

Is there any other info I should be looking for which may be relevant? There are pages of VESA(0) entries.

---

### Post by Hyvver on 2012-12-17
I got a deathadder u can add macros ti the keys if u wish, there is no physical button to change dpi's but u can set that function to any mouse button afaik. The price ye, its kinda expensive, cost me 60â‚¬ a couple of months ago. Sometimes if u scroll too fast u'll scroll 2 times, this is bad when u set the scroll up and down to switch weapons.

---

### Post by Rexilion on 2012-12-18
Probably a Unity thing. But I don't see any bugs for it.

Is this behaviour persistent?

---

### Post by scbingham on 2012-12-30
This resolved it for me:

My friend installed 12.04.1 64 bit ( I didn't realise I could run it)

Screen resolution set to 1920 x 1280

Not only are web pages now correctly displayed but the mouse pointer never disappears. :D

---

