---
title: "Wrong resolution"
date: 2016-08-07
forum: General Help
---

### Post by agnostic on 2016-08-07
My troubles started a few days ago when I tried to run "Left 4 Dead 2" via steam. 
This system has been running stable for years. Only addition was the graphics card a year ago. But since the steam incident other applications seem to cause this as well. 

Example: Whenever I try to watch a video on fullscreen, the resolution drops to 1024x768. System settings only allow a resolution of 1360x768 after that. 
Further symptoms: The printscreen button doesn't work anymore, as well as the volume wheel and other hotkeys (eg. Ctrl-Alt-T to bring up the terminal) on my Dell keyboard. 

This happened on 

[LIST]
[*]Ubuntu 14.04
with a
[*]Nvidia GT 750TI
[*]AMD Phenom x965
[*]24" Benq monitor connected via hdmi
[/LIST]

I then did a fresh install of 16.04.1, hoping this would solve itself and because it was due anyway. 
Unfortunately the issues remained.
I've gone through 5 major Nvidia driver releases yielding no improvement. 

*xrandr* before I try a fullscreen video on totem: 

```
user@pc:~$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080      60.0*+   60.0     59.9     50.0     60.1     60.0     50.0  
   1680x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x720       60.0     59.9     50.0  
   1152x720       60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   720x576        50.0     50.1  
   720x480        59.9     60.1  
   640x480        75.0     59.9     59.9  
DVI-D-1 disconnected (normal left inverted right x axis y axis)

```

*xrandr* afterwards: 

```
user@pc:~$ xrandr
Screen 0: minimum 8 x 8, current 1360 x 768, maximum 16384 x 16384
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0*    59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384        60.0     59.8  
   640x480        59.9  
   512x384        60.0  
   400x300        72.2  
   320x240        60.1  
DVI-D-1 disconnected (normal left inverted right x axis y axis)
```

Additionally, since then I'm greeted with this lovely error on startup: 

[ATTACH=CONFIG]270616[/ATTACH]

my Xorg log: 

```
[    10.250] 
X.Org X Server 1.18.3
Release Date: 2016-04-04
[    10.250] X Protocol Version 11, Revision 0
[    10.250] Build Operating System: Linux 3.13.0-92-generic x86_64 Ubuntu
[    10.250] Current Operating System: Linux newby 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64
[    10.250] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-31-generic root=UUID=16c42d7d-926d-4bb9-936b-fe6f8ca0c02f ro quiet splash
[    10.250] Build Date: 22 July 2016  07:50:34AM
[    10.250] xorg-server 2:1.18.3-1ubuntu2.3 (For technical support please see http://www.ubuntu.com/support) 
[    10.250] Current version of pixman: 0.33.6
[    10.250] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    10.250] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    10.250] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug  7 18:03:24 2016
[    10.252] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    10.253] (==) No Layout section.  Using the first Screen section.
[    10.253] (==) No screen section available. Using defaults.
[    10.253] (**) |-->Screen "Default Screen Section" (0)
[    10.253] (**) |   |-->Monitor "<default monitor>"
[    10.254] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    10.254] (==) Automatically adding devices
[    10.254] (==) Automatically enabling devices
[    10.254] (==) Automatically adding GPU devices
[    10.254] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    10.256] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    10.256] 	Entry deleted from font path.
[    10.256] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    10.256] 	Entry deleted from font path.
[    10.256] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    10.256] 	Entry deleted from font path.
[    10.256] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    10.256] 	Entry deleted from font path.
[    10.256] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    10.256] 	Entry deleted from font path.
[    10.256] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    10.256] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    10.256] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    10.256] (II) Loader magic: 0x55fd4e150da0
[    10.256] (II) Module ABI versions:
[    10.256] 	X.Org ANSI C Emulation: 0.4
[    10.256] 	X.Org Video Driver: 20.0
[    10.256] 	X.Org XInput driver : 22.1
[    10.256] 	X.Org Server Extension : 9.0
[    10.256] (++) using VT number 7

[    10.256] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    10.257] (II) xfree86: Adding drm device (/dev/dri/card0)
[    10.258] (--) PCI:*(0:1:0:0) 10de:1380:1043:84bb rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[    10.258] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    10.258] (II) "glx" will be loaded by default.
[    10.258] (II) LoadModule: "glx"
[    10.258] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    10.321] (II) Module glx: vendor="NVIDIA Corporation"
[    10.321] 	compiled for 4.0.2, module version = 1.0.0
[    10.321] 	Module class: X.Org Server Extension
[    10.322] (II) NVIDIA GLX Module  361.42  Tue Mar 22 17:25:45 PDT 2016
[    10.323] (==) Matched nvidia as autoconfigured driver 0
[    10.323] (==) Matched nouveau as autoconfigured driver 1
[    10.323] (==) Matched nvidia as autoconfigured driver 2
[    10.323] (==) Matched nouveau as autoconfigured driver 3
[    10.323] (==) Matched modesetting as autoconfigured driver 4
[    10.323] (==) Matched fbdev as autoconfigured driver 5
[    10.323] (==) Matched vesa as autoconfigured driver 6
[    10.323] (==) Assigned the driver to the xf86ConfigLayout
[    10.323] (II) LoadModule: "nvidia"
[    10.323] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    10.329] (II) Module nvidia: vendor="NVIDIA Corporation"
[    10.329] 	compiled for 4.0.2, module version = 1.0.0
[    10.329] 	Module class: X.Org Video Driver
[    10.329] (II) LoadModule: "nouveau"
[    10.331] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    10.332] (II) Module nouveau: vendor="X.Org Foundation"
[    10.332] 	compiled for 1.18.1, module version = 1.0.12
[    10.332] 	Module class: X.Org Video Driver
[    10.332] 	ABI class: X.Org Video Driver, version 20.0
[    10.333] (II) LoadModule: "modesetting"
[    10.333] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    10.333] (II) Module modesetting: vendor="X.Org Foundation"
[    10.333] 	compiled for 1.18.3, module version = 1.18.3
[    10.333] 	Module class: X.Org Video Driver
[    10.333] 	ABI class: X.Org Video Driver, version 20.0
[    10.333] (II) LoadModule: "fbdev"
[    10.333] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    10.334] (II) Module fbdev: vendor="X.Org Foundation"
[    10.334] 	compiled for 1.18.1, module version = 0.4.4
[    10.334] 	Module class: X.Org Video Driver
[    10.334] 	ABI class: X.Org Video Driver, version 20.0
[    10.334] (II) LoadModule: "vesa"
[    10.334] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    10.334] (II) Module vesa: vendor="X.Org Foundation"
[    10.334] 	compiled for 1.18.1, module version = 2.3.4
[    10.334] 	Module class: X.Org Video Driver
[    10.334] 	ABI class: X.Org Video Driver, version 20.0
[    10.334] (II) NVIDIA dlloader X Driver  361.42  Tue Mar 22 17:04:20 PDT 2016
[    10.334] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    10.335] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[    10.335] (II) NOUVEAU driver for NVIDIA chipset families :
[    10.335] 	RIVA TNT        (NV04)
[    10.335] 	RIVA TNT2       (NV05)
[    10.335] 	GeForce 256     (NV10)
[    10.335] 	GeForce 2       (NV11, NV15)
[    10.335] 	GeForce 4MX     (NV17, NV18)
[    10.335] 	GeForce 3       (NV20)
[    10.335] 	GeForce 4Ti     (NV25, NV28)
[    10.335] 	GeForce FX      (NV3x)
[    10.335] 	GeForce 6       (NV4x)
[    10.335] 	GeForce 7       (G7x)
[    10.335] 	GeForce 8       (G8x)
[    10.335] 	GeForce GTX 200 (NVA0)
[    10.335] 	GeForce GTX 400 (NVC0)
[    10.335] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    10.335] (II) FBDEV: driver for framebuffer: fbdev
[    10.335] (II) VESA: driver for VESA chipsets: vesa
[    10.502] (II) Loading sub module "fb"
[    10.502] (II) LoadModule: "fb"
[    10.502] (II) Loading /usr/lib/xorg/modules/libfb.so
[    10.504] (II) Module fb: vendor="X.Org Foundation"
[    10.504] 	compiled for 1.18.3, module version = 1.0.0
[    10.504] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    10.504] (II) Loading sub module "wfb"
[    10.504] (II) LoadModule: "wfb"
[    10.504] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    10.505] (II) Module wfb: vendor="X.Org Foundation"
[    10.505] 	compiled for 1.18.3, module version = 1.0.0
[    10.505] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    10.505] (II) Loading sub module "ramdac"
[    10.505] (II) LoadModule: "ramdac"
[    10.505] (II) Module "ramdac" already built-in
[    10.511] (WW) Falling back to old probe method for modesetting
[    10.511] (WW) Falling back to old probe method for fbdev
[    10.511] (II) Loading sub module "fbdevhw"
[    10.511] (II) LoadModule: "fbdevhw"
[    10.511] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    10.511] (II) Module fbdevhw: vendor="X.Org Foundation"
[    10.511] 	compiled for 1.18.3, module version = 0.0.2
[    10.511] 	ABI class: X.Org Video Driver, version 20.0
[    10.511] (EE) open /dev/fb0: No such file or directory
[    10.511] (WW) Falling back to old probe method for vesa
[    10.512] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    10.512] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    10.512] (==) NVIDIA(0): RGB weight 888
[    10.512] (==) NVIDIA(0): Default visual is TrueColor
[    10.512] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    10.512] (**) NVIDIA(0): Enabling 2D acceleration
[    11.021] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[    11.021] (--) NVIDIA(0):     CRT-0
[    11.021] (--) NVIDIA(0):     DFP-0
[    11.021] (--) NVIDIA(0):     DFP-1 (boot)
[    11.021] (--) NVIDIA(0):     DFP-2
[    11.022] (--) NVIDIA(0): CRT-0: disconnected
[    11.022] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    11.022] (--) NVIDIA(0): 
[    11.022] (--) NVIDIA(0): DFP-0: disconnected
[    11.022] (--) NVIDIA(0): DFP-0: Internal TMDS
[    11.022] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    11.022] (--) NVIDIA(0): 
[    11.035] (--) NVIDIA(0): BenQ G2420HD (DFP-1): connected
[    11.035] (--) NVIDIA(0): BenQ G2420HD (DFP-1): Internal TMDS
[    11.035] (--) NVIDIA(0): BenQ G2420HD (DFP-1): 340.0 MHz maximum pixel clock
[    11.035] (--) NVIDIA(0): 
[    11.035] (--) NVIDIA(0): DFP-2: disconnected
[    11.035] (--) NVIDIA(0): DFP-2: Internal TMDS
[    11.035] (--) NVIDIA(0): DFP-2: 330.0 MHz maximum pixel clock
[    11.035] (--) NVIDIA(0): 
[    11.035] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[    11.036] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 750 Ti (GM107-A) at PCI:1:0:0 (GPU-0)
[    11.036] (--) NVIDIA(0): Memory: 2097152 kBytes
[    11.036] (--) NVIDIA(0): VideoBIOS: 82.07.32.00.20
[    11.036] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    11.036] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    11.036] (**) NVIDIA(0):     device BenQ G2420HD (DFP-1) (Using EDID frequencies has
[    11.036] (**) NVIDIA(0):     been enabled on all display devices.)
[    11.039] (==) NVIDIA(0): 
[    11.039] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    11.039] (==) NVIDIA(0):     will be used as the requested mode.
[    11.039] (==) NVIDIA(0): 
[    11.040] (II) NVIDIA(0): Validated MetaModes:
[    11.040] (II) NVIDIA(0):     "DFP-1:nvidia-auto-select"
[    11.040] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    11.050] (--) NVIDIA(0): DPI set to (92, 91); computed from "UseEdidDpi" X config
[    11.050] (--) NVIDIA(0):     option
[    11.050] (II) UnloadModule: "nouveau"
[    11.050] (II) Unloading nouveau
[    11.050] (II) UnloadModule: "modesetting"
[    11.050] (II) Unloading modesetting
[    11.050] (II) UnloadModule: "fbdev"
[    11.050] (II) Unloading fbdev
[    11.050] (II) UnloadSubModule: "fbdevhw"
[    11.050] (II) Unloading fbdevhw
[    11.050] (II) UnloadModule: "vesa"
[    11.050] (II) Unloading vesa
[    11.050] (--) Depth 24 pixmap format is 32 bpp
[    11.051] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    11.051] (II) NVIDIA:     access.
[    11.087] (II) NVIDIA(0): Setting mode "DFP-1:nvidia-auto-select"
[    11.135] (==) NVIDIA(0): Disabling shared memory pixmaps
[    11.135] (==) NVIDIA(0): Backing store enabled
[    11.135] (==) NVIDIA(0): Silken mouse enabled
[    11.136] (==) NVIDIA(0): DPMS enabled
[    11.137] (II) Loading sub module "x11glvnd"
[    11.137] (II) LoadModule: "x11glvnd"
[    11.137] (WW) Warning, couldn't open module x11glvnd
[    11.137] (II) UnloadModule: "x11glvnd"
[    11.137] (II) Unloading x11glvnd
[    11.137] (II) x11glvnd Loading
[    11.137] (II) Loading sub module "dri2"
[    11.137] (II) LoadModule: "dri2"
[    11.137] (II) Module "dri2" already built-in
[    11.137] (II) NVIDIA(0): [DRI2] Setup complete
[    11.137] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    11.137] (--) RandR disabled
[    11.141] (II) SELinux: Disabled on system
[    11.142] (II) Initializing extension GLX
[    11.142] (II) Indirect GLX disabled.
[    11.204] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    11.204] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    11.204] (II) LoadModule: "evdev"
[    11.204] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.206] (II) Module evdev: vendor="X.Org Foundation"
[    11.206] 	compiled for 1.18.1, module version = 2.10.1
[    11.206] 	Module class: X.Org XInput Driver
[    11.206] 	ABI class: X.Org XInput driver, version 22.1
[    11.206] (II) Using input driver 'evdev' for 'Power Button'
[    11.206] (**) Power Button: always reports core events
[    11.206] (**) evdev: Power Button: Device: "/dev/input/event1"
[    11.206] (--) evdev: Power Button: Vendor 0 Product 0x1
[    11.206] (--) evdev: Power Button: Found keys
[    11.206] (II) evdev: Power Button: Configuring as keyboard
[    11.206] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    11.206] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    11.206] (**) Option "xkb_rules" "evdev"
[    11.206] (**) Option "xkb_model" "pc105"
[    11.206] (**) Option "xkb_layout" "de"
[    11.206] (**) Option "xkb_variant" "nodeadkeys"
[    11.226] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    11.226] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    11.226] (II) Using input driver 'evdev' for 'Power Button'
[    11.226] (**) Power Button: always reports core events
[    11.226] (**) evdev: Power Button: Device: "/dev/input/event0"
[    11.226] (--) evdev: Power Button: Vendor 0 Product 0x1
[    11.226] (--) evdev: Power Button: Found keys
[    11.226] (II) evdev: Power Button: Configuring as keyboard
[    11.226] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    11.226] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    11.226] (**) Option "xkb_rules" "evdev"
[    11.226] (**) Option "xkb_model" "pc105"
[    11.226] (**) Option "xkb_layout" "de"
[    11.226] (**) Option "xkb_variant" "nodeadkeys"
[    11.227] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[    11.227] (II) No input driver specified, ignoring this device.
[    11.227] (II) This device may have been added with another device file.
[    11.227] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[    11.227] (II) No input driver specified, ignoring this device.
[    11.227] (II) This device may have been added with another device file.
[    11.227] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[    11.227] (II) No input driver specified, ignoring this device.
[    11.227] (II) This device may have been added with another device file.
[    11.227] (II) config/udev: Adding input device Dell Dell Multimedia Pro Keyboard (/dev/input/event2)
[    11.227] (**) Dell Dell Multimedia Pro Keyboard: Applying InputClass "evdev keyboard catchall"
[    11.227] (II) Using input driver 'evdev' for 'Dell Dell Multimedia Pro Keyboard'
[    11.227] (**) Dell Dell Multimedia Pro Keyboard: always reports core events
[    11.227] (**) evdev: Dell Dell Multimedia Pro Keyboard: Device: "/dev/input/event2"
[    11.227] (--) evdev: Dell Dell Multimedia Pro Keyboard: Vendor 0x413c Product 0x2011
[    11.227] (--) evdev: Dell Dell Multimedia Pro Keyboard: Found keys
[    11.227] (II) evdev: Dell Dell Multimedia Pro Keyboard: Configuring as keyboard
[    11.227] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2.1/3-2.1:1.0/0003:413C:2011.0001/input/input5/event2"
[    11.227] (II) XINPUT: Adding extended input device "Dell Dell Multimedia Pro Keyboard" (type: KEYBOARD, id 8)
[    11.228] (**) Option "xkb_rules" "evdev"
[    11.228] (**) Option "xkb_model" "pc105"
[    11.228] (**) Option "xkb_layout" "de"
[    11.228] (**) Option "xkb_variant" "nodeadkeys"
[    11.228] (II) config/udev: Adding input device Dell Dell Multimedia Pro Keyboard (/dev/input/event3)
[    11.228] (**) Dell Dell Multimedia Pro Keyboard: Applying InputClass "evdev keyboard catchall"
[    11.228] (II) Using input driver 'evdev' for 'Dell Dell Multimedia Pro Keyboard'
[    11.228] (**) Dell Dell Multimedia Pro Keyboard: always reports core events
[    11.228] (**) evdev: Dell Dell Multimedia Pro Keyboard: Device: "/dev/input/event3"
[    11.228] (--) evdev: Dell Dell Multimedia Pro Keyboard: Vendor 0x413c Product 0x2011
[    11.228] (--) evdev: Dell Dell Multimedia Pro Keyboard: Found absolute axes
[    11.228] (II) evdev: Dell Dell Multimedia Pro Keyboard: Forcing absolute x/y axes to exist.
[    11.228] (--) evdev: Dell Dell Multimedia Pro Keyboard: Found keys
[    11.228] (II) evdev: Dell Dell Multimedia Pro Keyboard: Forcing relative x/y axes to exist.
[    11.228] (II) evdev: Dell Dell Multimedia Pro Keyboard: Configuring as mouse
[    11.228] (II) evdev: Dell Dell Multimedia Pro Keyboard: Configuring as keyboard
[    11.228] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2.1/3-2.1:1.1/0003:413C:2011.0002/input/input6/event3"
[    11.228] (II) XINPUT: Adding extended input device "Dell Dell Multimedia Pro Keyboard" (type: KEYBOARD, id 9)
[    11.228] (**) Option "xkb_rules" "evdev"
[    11.228] (**) Option "xkb_model" "pc105"
[    11.228] (**) Option "xkb_layout" "de"
[    11.228] (**) Option "xkb_variant" "nodeadkeys"
[    11.228] (II) evdev: Dell Dell Multimedia Pro Keyboard: initialized for absolute axes.
[    11.229] (**) Dell Dell Multimedia Pro Keyboard: (accel) keeping acceleration scheme 1
[    11.229] (**) Dell Dell Multimedia Pro Keyboard: (accel) acceleration profile 0
[    11.229] (**) Dell Dell Multimedia Pro Keyboard: (accel) acceleration factor: 2.000
[    11.229] (**) Dell Dell Multimedia Pro Keyboard: (accel) acceleration threshold: 4
[    11.229] (II) config/udev: Adding input device Logitech Gaming Mouse G400 (/dev/input/event4)
[    11.229] (**) Logitech Gaming Mouse G400: Applying InputClass "evdev pointer catchall"
[    11.229] (II) Using input driver 'evdev' for 'Logitech Gaming Mouse G400'
[    11.229] (**) Logitech Gaming Mouse G400: always reports core events
[    11.229] (**) evdev: Logitech Gaming Mouse G400: Device: "/dev/input/event4"
[    11.288] (--) evdev: Logitech Gaming Mouse G400: Vendor 0x46d Product 0xc245
[    11.288] (--) evdev: Logitech Gaming Mouse G400: Found 12 mouse buttons
[    11.288] (--) evdev: Logitech Gaming Mouse G400: Found scroll wheel(s)
[    11.288] (--) evdev: Logitech Gaming Mouse G400: Found relative axes
[    11.288] (--) evdev: Logitech Gaming Mouse G400: Found x and y relative axes
[    11.288] (II) evdev: Logitech Gaming Mouse G400: Configuring as mouse
[    11.288] (II) evdev: Logitech Gaming Mouse G400: Adding scrollwheel support
[    11.288] (**) evdev: Logitech Gaming Mouse G400: YAxisMapping: buttons 4 and 5
[    11.288] (**) evdev: Logitech Gaming Mouse G400: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    11.288] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2.2/3-2.2:1.0/0003:046D:C245.0003/input/input7/event4"
[    11.288] (II) XINPUT: Adding extended input device "Logitech Gaming Mouse G400" (type: MOUSE, id 10)
[    11.288] (II) evdev: Logitech Gaming Mouse G400: initialized for relative axes.
[    11.288] (**) Logitech Gaming Mouse G400: (accel) keeping acceleration scheme 1
[    11.288] (**) Logitech Gaming Mouse G400: (accel) acceleration profile 0
[    11.288] (**) Logitech Gaming Mouse G400: (accel) acceleration factor: 2.000
[    11.288] (**) Logitech Gaming Mouse G400: (accel) acceleration threshold: 4
[    11.288] (II) config/udev: Adding input device Logitech Gaming Mouse G400 (/dev/input/mouse0)
[    11.288] (II) No input driver specified, ignoring this device.
[    11.288] (II) This device may have been added with another device file.
[    11.289] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event7)
[    11.289] (II) No input driver specified, ignoring this device.
[    11.289] (II) This device may have been added with another device file.
[    11.289] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event8)
[    11.289] (II) No input driver specified, ignoring this device.
[    11.289] (II) This device may have been added with another device file.
[    11.289] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event9)
[    11.289] (II) No input driver specified, ignoring this device.
[    11.289] (II) This device may have been added with another device file.
[    11.289] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event10)
[    11.289] (II) No input driver specified, ignoring this device.
[    11.289] (II) This device may have been added with another device file.
[    11.289] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event11)
[    11.289] (II) No input driver specified, ignoring this device.
[    11.289] (II) This device may have been added with another device file.
[    11.290] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event12)
[    11.290] (II) No input driver specified, ignoring this device.
[    11.290] (II) This device may have been added with another device file.
[    11.290] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event5)
[    11.290] (II) No input driver specified, ignoring this device.
[    11.290] (II) This device may have been added with another device file.
[    11.290] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event6)
[    11.290] (II) No input driver specified, ignoring this device.
[    11.290] (II) This device may have been added with another device file.
[    12.007] (--) NVIDIA(GPU-0): CRT-0: disconnected
[    12.007] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    12.007] (--) NVIDIA(GPU-0): 
[    12.007] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    12.007] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    12.007] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    12.007] (--) NVIDIA(GPU-0): 
[    12.020] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): connected
[    12.020] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): Internal TMDS
[    12.020] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): 340.0 MHz maximum pixel clock
[    12.020] (--) NVIDIA(GPU-0): 
[    12.020] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    12.020] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    12.020] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    12.020] (--) NVIDIA(GPU-0): 
[    12.420] (--) NVIDIA(GPU-0): CRT-0: disconnected
[    12.420] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    12.420] (--) NVIDIA(GPU-0): 
[    12.420] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    12.420] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    12.420] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    12.420] (--) NVIDIA(GPU-0): 
[    12.433] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): connected
[    12.433] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): Internal TMDS
[    12.433] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): 340.0 MHz maximum pixel clock
[    12.433] (--) NVIDIA(GPU-0): 
[    12.433] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    12.433] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    12.433] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    12.433] (--) NVIDIA(GPU-0): 
[    21.703] (--) NVIDIA(GPU-0): CRT-0: disconnected
[    21.703] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    21.703] (--) NVIDIA(GPU-0): 
[    21.703] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    21.703] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    21.703] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    21.703] (--) NVIDIA(GPU-0): 
[    21.721] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): connected
[    21.721] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): Internal TMDS
[    21.721] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): 340.0 MHz maximum pixel clock
[    21.721] (--) NVIDIA(GPU-0): 
[    21.721] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    21.722] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    21.722] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    21.722] (--) NVIDIA(GPU-0): 
[    21.950] (--) NVIDIA(GPU-0): CRT-0: disconnected
[    21.950] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    21.950] (--) NVIDIA(GPU-0): 
[    21.950] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    21.950] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    21.950] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    21.950] (--) NVIDIA(GPU-0): 
[    21.963] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): connected
[    21.963] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): Internal TMDS
[    21.963] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): 340.0 MHz maximum pixel clock
[    21.963] (--) NVIDIA(GPU-0): 
[    21.963] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    21.963] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    21.963] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    21.963] (--) NVIDIA(GPU-0): 
[   318.379] (--) NVIDIA(GPU-0): CRT-0: disconnected
[   318.379] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[   318.379] (--) NVIDIA(GPU-0): 
[   318.379] (--) NVIDIA(GPU-0): DFP-0: disconnected
[   318.379] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[   318.379] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[   318.379] (--) NVIDIA(GPU-0): 
[   318.392] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): connected
[   318.392] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): Internal TMDS
[   318.392] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): 340.0 MHz maximum pixel clock
[   318.392] (--) NVIDIA(GPU-0): 
[   318.392] (--) NVIDIA(GPU-0): DFP-2: disconnected
[   318.392] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[   318.392] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[   318.392] (--) NVIDIA(GPU-0): 
[   320.061] (--) NVIDIA(GPU-0): CRT-0: disconnected
[   320.061] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[   320.061] (--) NVIDIA(GPU-0): 
[   320.061] (--) NVIDIA(GPU-0): DFP-0: disconnected
[   320.061] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[   320.061] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[   320.061] (--) NVIDIA(GPU-0): 
[   320.074] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): connected
[   320.074] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): Internal TMDS
[   320.074] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): 340.0 MHz maximum pixel clock
[   320.074] (--) NVIDIA(GPU-0): 
[   320.074] (--) NVIDIA(GPU-0): DFP-2: disconnected
[   320.074] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[   320.074] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[   320.074] (--) NVIDIA(GPU-0): 
[   486.022] (--) NVIDIA(GPU-0): CRT-0: disconnected
[   486.022] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[   486.022] (--) NVIDIA(GPU-0): 
[   486.022] (--) NVIDIA(GPU-0): DFP-0: disconnected
[   486.022] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[   486.022] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[   486.022] (--) NVIDIA(GPU-0): 
[   486.036] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): connected
[   486.036] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): Internal TMDS
[   486.036] (--) NVIDIA(GPU-0): BenQ G2420HD (DFP-1): 340.0 MHz maximum pixel clock
[   486.036] (--) NVIDIA(GPU-0): 
[   486.036] (--) NVIDIA(GPU-0): DFP-2: disconnected
[   486.036] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[   486.036] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[   486.036] (--) NVIDIA(GPU-0): 

```

Everything is updated, tried updating drivers from the default repositories and installed via "additional drivers" and via apt-get.

Any help would be appreciated. Thanks in advance.

---

