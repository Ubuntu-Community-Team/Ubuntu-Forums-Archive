---
title: "X won't start in 14.04. Bad Nvidia drivers? Bad Plymouth install?"
date: 2015-12-12
forum: General Help
---

### Post by Drone4four on 2015-12-12
I borked my Ubuntu.

The last thing I did was update my kernel (just with dist-update without any third party repos) and proprietary nvidia drivers. I was also playing around with Plymouth manager.  I rebooted and now gdm won't load.  It brings me to a VT login at boot.   So I enter my credentials and issued, **$ startx**.  It hangs.  I tried falling back to a previous kernel installtion from Grub (I tried a few previous installations).  So I tried removing my proprietary nvidia drivers, and now X is giving me a different error. See below for the contents of my /var/log/Xorg.0.log .

I tried ** $ sudo apt-get remove plymouth*** which asked me if I wanted to remove 600MBs of packages, including XFce4, KDE and Gnome which I obviously didn't proceed.

I tried passing the nomodeset parameter from Grub. No dice.

I'm running 64bit 14.04

Is there any other information I can provide?

Thanks for your attention.

Xorg.0.log:
```

[   300.945] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[   300.945] X Protocol Version 11, Revision 0
[   300.945] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[   300.945] Current Operating System: Linux gnosis 3.13.0-71-generic #114-Ubuntu SMP Tue Dec 1 02:34:22 UTC 2015 x86_64
[   300.945] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-71-generic root=UUID=4ca46729-e714-4e8a-9c6b-eedf1d0d1003 ro nomodeset quiet splash vt.handoff=7
[   300.945] Build Date: 12 February 2015  02:49:29PM
[   300.945] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[   300.945] Current version of pixman: 0.30.2
[   300.945] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   300.945] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   300.945] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 11 22:18:56 2015
[   300.945] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   300.946] (==) No Layout section.  Using the first Screen section.
[   300.946] (==) No screen section available. Using defaults.
[   300.946] (**) |-->Screen "Default Screen Section" (0)
[   300.946] (**) |   |-->Monitor "<default monitor>"
[   300.946] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   300.946] (==) Automatically adding devices
[   300.946] (==) Automatically enabling devices
[   300.946] (==) Automatically adding GPU devices
[   300.946] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   300.946] 	Entry deleted from font path.
[   300.946] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   300.946] 	Entry deleted from font path.
[   300.946] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   300.946] 	Entry deleted from font path.
[   300.946] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	built-ins
[   300.946] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   300.946] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   300.946] (II) Loader magic: 0x7fdf873e9d40
[   300.946] (II) Module ABI versions:
[   300.946] 	X.Org ANSI C Emulation: 0.4
[   300.946] 	X.Org Video Driver: 15.0
[   300.946] 	X.Org XInput driver : 20.0
[   300.946] 	X.Org Server Extension : 8.0
[   300.948] (--) PCI:*(0:6:0:0) 10de:1200:3842:1568 rev 161, Mem @ 0xf8000000/33554432, 0xe8000000/134217728, 0xf0000000/67108864, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[   300.948] Initializing built-in extension Generic Event Extension
[   300.948] Initializing built-in extension SHAPE
[   300.949] Initializing built-in extension MIT-SHM
[   300.949] Initializing built-in extension XInputExtension
[   300.949] Initializing built-in extension XTEST
[   300.949] Initializing built-in extension BIG-REQUESTS
[   300.949] Initializing built-in extension SYNC
[   300.949] Initializing built-in extension XKEYBOARD
[   300.949] Initializing built-in extension XC-MISC
[   300.949] Initializing built-in extension SECURITY
[   300.949] Initializing built-in extension XINERAMA
[   300.949] Initializing built-in extension XFIXES
[   300.949] Initializing built-in extension RENDER
[   300.949] Initializing built-in extension RANDR
[   300.949] Initializing built-in extension COMPOSITE
[   300.949] Initializing built-in extension DAMAGE
[   300.949] Initializing built-in extension MIT-SCREEN-SAVER
[   300.949] Initializing built-in extension DOUBLE-BUFFER
[   300.949] Initializing built-in extension RECORD
[   300.949] Initializing built-in extension DPMS
[   300.949] Initializing built-in extension Present
[   300.949] Initializing built-in extension DRI3
[   300.949] Initializing built-in extension X-Resource
[   300.949] Initializing built-in extension XVideo
[   300.949] Initializing built-in extension XVideo-MotionCompensation
[   300.949] Initializing built-in extension SELinux
[   300.949] Initializing built-in extension XFree86-VidModeExtension
[   300.949] Initializing built-in extension XFree86-DGA
[   300.949] Initializing built-in extension XFree86-DRI
[   300.949] Initializing built-in extension DRI2
[   300.949] (II) LoadModule: "glx"
[   300.949] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   300.950] (II) Module glx: vendor="X.Org Foundation"
[   300.950] 	compiled for 1.15.1, module version = 1.0.0
[   300.950] 	ABI class: X.Org Server Extension, version 8.0
[   300.951] (==) AIGLX enabled
[   300.951] Loading extension GLX
[   300.951] (==) Matched nvidia as autoconfigured driver 0
[   300.951] (==) Matched nouveau as autoconfigured driver 1
[   300.951] (==) Matched modesetting as autoconfigured driver 2
[   300.951] (==) Matched fbdev as autoconfigured driver 3
[   300.951] (==) Matched vesa as autoconfigured driver 4
[   300.951] (==) Assigned the driver to the xf86ConfigLayout
[   300.951] (II) LoadModule: "nvidia"
[   300.951] (WW) Warning, couldn't open module nvidia
[   300.951] (II) UnloadModule: "nvidia"
[   300.951] (II) Unloading nvidia
[   300.951] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   300.951] (II) LoadModule: "nouveau"
[   300.951] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   300.952] (II) Module nouveau: vendor="X.Org Foundation"
[   300.952] 	compiled for 1.15.1, module version = 1.0.11
[   300.952] 	Module class: X.Org Video Driver
[   300.952] 	ABI class: X.Org Video Driver, version 15.0
[   300.952] (II) LoadModule: "modesetting"
[   300.952] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   300.952] (II) Module modesetting: vendor="X.Org Foundation"
[   300.952] 	compiled for 1.15.0, module version = 0.8.1
[   300.952] 	Module class: X.Org Video Driver
[   300.952] 	ABI class: X.Org Video Driver, version 15.0
[   300.952] (II) LoadModule: "fbdev"
[   300.952] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   300.952] (II) Module fbdev: vendor="X.Org Foundation"
[   300.952] 	compiled for 1.15.0, module version = 0.4.4
[   300.952] 	Module class: X.Org Video Driver
[   300.952] 	ABI class: X.Org Video Driver, version 15.0
[   300.952] (II) LoadModule: "vesa"
[   300.952] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   300.952] (II) Module vesa: vendor="X.Org Foundation"
[   300.952] 	compiled for 1.15.0, module version = 2.3.3
[   300.952] 	Module class: X.Org Video Driver
[   300.952] 	ABI class: X.Org Video Driver, version 15.0
[   300.952] (==) Matched nvidia as autoconfigured driver 0
[   300.952] (==) Matched nouveau as autoconfigured driver 1
[   300.952] (==) Matched modesetting as autoconfigured driver 2
[   300.952] (==) Matched fbdev as autoconfigured driver 3
[   300.952] (==) Matched vesa as autoconfigured driver 4
[   300.952] (==) Assigned the driver to the xf86ConfigLayout
[   300.952] (II) LoadModule: "nvidia"
[   300.953] (WW) Warning, couldn't open module nvidia
[   300.953] (II) UnloadModule: "nvidia"
[   300.953] (II) Unloading nvidia
[   300.953] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   300.953] (II) LoadModule: "nouveau"
[   300.953] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   300.953] (II) Module nouveau: vendor="X.Org Foundation"
[   300.953] 	compiled for 1.15.1, module version = 1.0.11
[   300.953] 	Module class: X.Org Video Driver
[   300.953] 	ABI class: X.Org Video Driver, version 15.0
[   300.953] (II) UnloadModule: "nouveau"
[   300.953] (II) Unloading nouveau
[   300.953] (II) Failed to load module "nouveau" (already loaded, 0)
[   300.953] (II) LoadModule: "modesetting"
[   300.953] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   300.953] (II) Module modesetting: vendor="X.Org Foundation"
[   300.953] 	compiled for 1.15.0, module version = 0.8.1
[   300.953] 	Module class: X.Org Video Driver
[   300.953] 	ABI class: X.Org Video Driver, version 15.0
[   300.953] (II) UnloadModule: "modesetting"
[   300.953] (II) Unloading modesetting
[   300.953] (II) Failed to load module "modesetting" (already loaded, 0)
[   300.953] (II) LoadModule: "fbdev"
[   300.953] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   300.953] (II) Module fbdev: vendor="X.Org Foundation"
[   300.953] 	compiled for 1.15.0, module version = 0.4.4
[   300.953] 	Module class: X.Org Video Driver
[   300.953] 	ABI class: X.Org Video Driver, version 15.0
[   300.953] (II) UnloadModule: "fbdev"
[   300.953] (II) Unloading fbdev
[   300.953] (II) Failed to load module "fbdev" (already loaded, 0)
[   300.953] (II) LoadModule: "vesa"
[   300.953] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   300.953] (II) Module vesa: vendor="X.Org Foundation"
[   300.953] 	compiled for 1.15.0, module version = 2.3.3
[   300.953] 	Module class: X.Org Video Driver
[   300.953] 	ABI class: X.Org Video Driver, version 15.0
[   300.953] (II) UnloadModule: "vesa"
[   300.953] (II) Unloading vesa
[   300.953] (II) Failed to load module "vesa" (already loaded, 0)
[   300.953] (II) NOUVEAU driver 
[   300.953] (II) NOUVEAU driver for NVIDIA chipset families :
[   300.953] 	RIVA TNT        (NV04)
[   300.953] 	RIVA TNT2       (NV05)
[   300.953] 	GeForce 256     (NV10)
[   300.953] 	GeForce 2       (NV11, NV15)
[   300.954] 	GeForce 4MX     (NV17, NV18)
[   300.954] 	GeForce 3       (NV20)
[   300.954] 	GeForce 4Ti     (NV25, NV28)
[   300.954] 	GeForce FX      (NV3x)
[   300.954] 	GeForce 6       (NV4x)
[   300.954] 	GeForce 7       (G7x)
[   300.954] 	GeForce 8       (G8x)
[   300.954] 	GeForce GTX 200 (NVA0)
[   300.954] 	GeForce GTX 400 (NVC0)
[   300.954] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   300.954] (II) FBDEV: driver for framebuffer: fbdev
[   300.954] (II) VESA: driver for VESA chipsets: vesa
[   300.954] (++) using VT number 7

[   300.959] (EE) [drm] KMS not enabled
[   300.959] (EE) [drm] KMS not enabled
[   300.959] (EE) open /dev/dri/card0: No such file or directory
[   300.959] (EE) open /dev/dri/card0: No such file or directory
[   300.959] (WW) Falling back to old probe method for modesetting
[   300.959] (EE) open /dev/dri/card0: No such file or directory
[   300.959] (EE) open /dev/dri/card0: No such file or directory
[   300.959] (II) Loading sub module "fbdevhw"
[   300.959] (II) LoadModule: "fbdevhw"
[   300.959] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   300.959] (II) Module fbdevhw: vendor="X.Org Foundation"
[   300.959] 	compiled for 1.15.1, module version = 0.0.2
[   300.959] 	ABI class: X.Org Video Driver, version 15.0
[   300.959] (**) FBDEV(2): claimed PCI slot 6@0:0:0
[   300.959] (II) FBDEV(2): using default device
[   300.959] (WW) Falling back to old probe method for vesa
[   300.959] (EE) Screen 0 deleted because of no matching config section.
[   300.959] (II) UnloadModule: "modesetting"
[   300.959] (EE) Screen 0 deleted because of no matching config section.
[   300.959] (II) UnloadModule: "modesetting"
[   300.959] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   300.959] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[   300.959] (==) FBDEV(0): RGB weight 888
[   300.959] (==) FBDEV(0): Default visual is TrueColor
[   300.959] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[   300.959] (II) FBDEV(0): hardware: VESA VGA (video memory: 1216kB)
[   300.959] (II) FBDEV(0): checking modes against framebuffer device...
[   300.959] (II) FBDEV(0): checking modes against monitor...
[   300.959] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)
[   300.959] (**) FBDEV(0):  Built-in mode "current": 30.7 MHz, 36.9 kHz, 73.3 Hz
[   300.959] (II) FBDEV(0): Modeline "current"x0.0   30.72  640 672 752 832  480 484 488 504 -hsync -vsync -csync (36.9 kHz b)
[   300.959] (==) FBDEV(0): DPI set to (96, 96)
[   300.959] (II) Loading sub module "fb"
[   300.959] (II) LoadModule: "fb"
[   300.959] (II) Loading /usr/lib/xorg/modules/libfb.so
[   300.959] (II) Module fb: vendor="X.Org Foundation"
[   300.959] 	compiled for 1.15.1, module version = 1.0.0
[   300.959] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   300.959] (**) FBDEV(0): using shadow framebuffer
[   300.959] (II) Loading sub module "shadow"
[   300.959] (II) LoadModule: "shadow"
[   300.959] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   300.960] (II) Module shadow: vendor="X.Org Foundation"
[   300.960] 	compiled for 1.15.1, module version = 1.1.0
[   300.960] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   300.960] (II) UnloadModule: "vesa"
[   300.960] (II) Unloading vesa
[   300.960] (==) Depth 24 pixmap format is 32 bpp
[   300.960] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   300.960] (==) FBDEV(0): Backing store enabled
[   300.960] (==) FBDEV(0): DPMS enabled
[   300.960] (==) RandR enabled
[   300.963] (II) SELinux: Disabled on system
[   300.963] (II) AIGLX: Screen 0 is not DRI2 capable
[   300.963] (EE) AIGLX: reverting to software rendering
[   300.971] (II) AIGLX: Loaded and initialized swrast
[   300.971] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   300.978] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   300.979] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   300.979] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   300.979] (II) LoadModule: "evdev"
[   300.979] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   300.979] (II) Module evdev: vendor="X.Org Foundation"
[   300.979] 	compiled for 1.15.0, module version = 2.8.2
[   300.979] 	Module class: X.Org XInput Driver
[   300.979] 	ABI class: X.Org XInput driver, version 20.0
[   300.979] (II) Using input driver 'evdev' for 'Power Button'
[   300.979] (**) Power Button: always reports core events
[   300.979] (**) evdev: Power Button: Device: "/dev/input/event1"
[   300.979] (--) evdev: Power Button: Vendor 0 Product 0x1
[   300.979] (--) evdev: Power Button: Found keys
[   300.979] (II) evdev: Power Button: Configuring as keyboard
[   300.980] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   300.980] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   300.980] (**) Option "xkb_rules" "evdev"
[   300.980] (**) Option "xkb_model" "pc105"
[   300.980] (**) Option "xkb_layout" "us"
[   300.980] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   300.980] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   300.980] (II) Using input driver 'evdev' for 'Power Button'
[   300.980] (**) Power Button: always reports core events
[   300.980] (**) evdev: Power Button: Device: "/dev/input/event0"
[   300.980] (--) evdev: Power Button: Vendor 0 Product 0x1
[   300.980] (--) evdev: Power Button: Found keys
[   300.980] (II) evdev: Power Button: Configuring as keyboard
[   300.980] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   300.980] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   300.980] (**) Option "xkb_rules" "evdev"
[   300.980] (**) Option "xkb_model" "pc105"
[   300.980] (**) Option "xkb_layout" "us"
[   300.980] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event14)
[   300.980] (II) No input driver specified, ignoring this device.
[   300.980] (II) This device may have been added with another device file.
[   300.980] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event13)
[   300.980] (II) No input driver specified, ignoring this device.
[   300.980] (II) This device may have been added with another device file.
[   300.980] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event12)
[   300.980] (II) No input driver specified, ignoring this device.
[   300.980] (II) This device may have been added with another device file.
[   300.980] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event11)
[   300.980] (II) No input driver specified, ignoring this device.
[   300.981] (II) This device may have been added with another device file.
[   300.981] (II) config/udev: Adding input device MOSART Semi. 2.4G Keyboard Mouse (/dev/input/event9)
[   300.981] (**) MOSART Semi. 2.4G Keyboard Mouse: Applying InputClass "evdev keyboard catchall"
[   300.981] (II) Using input driver 'evdev' for 'MOSART Semi. 2.4G Keyboard Mouse'
[   300.981] (**) MOSART Semi. 2.4G Keyboard Mouse: always reports core events
[   300.981] (**) evdev: MOSART Semi. 2.4G Keyboard Mouse: Device: "/dev/input/event9"
[   300.981] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Vendor 0x62a Product 0x4101
[   300.981] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Found keys
[   300.981] (II) evdev: MOSART Semi. 2.4G Keyboard Mouse: Configuring as keyboard
[   300.981] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input12/event9"
[   300.981] (II) XINPUT: Adding extended input device "MOSART Semi. 2.4G Keyboard Mouse" (type: KEYBOARD, id 8)
[   300.981] (**) Option "xkb_rules" "evdev"
[   300.981] (**) Option "xkb_model" "pc105"
[   300.981] (**) Option "xkb_layout" "us"
[   300.981] (II) config/udev: Adding input device MOSART Semi. 2.4G Keyboard Mouse (/dev/input/event10)
[   300.981] (**) MOSART Semi. 2.4G Keyboard Mouse: Applying InputClass "evdev pointer catchall"
[   300.981] (**) MOSART Semi. 2.4G Keyboard Mouse: Applying InputClass "evdev keyboard catchall"
[   300.981] (II) Using input driver 'evdev' for 'MOSART Semi. 2.4G Keyboard Mouse'
[   300.981] (**) MOSART Semi. 2.4G Keyboard Mouse: always reports core events
[   300.981] (**) evdev: MOSART Semi. 2.4G Keyboard Mouse: Device: "/dev/input/event10"
[   300.981] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Vendor 0x62a Product 0x4101
[   300.981] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Found 9 mouse buttons
[   300.981] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Found scroll wheel(s)
[   300.981] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Found relative axes
[   300.981] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Found x and y relative axes
[   300.981] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Found absolute axes
[   300.981] (II) evdev: MOSART Semi. 2.4G Keyboard Mouse: Forcing absolute x/y axes to exist.
[   300.981] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Found keys
[   300.981] (II) evdev: MOSART Semi. 2.4G Keyboard Mouse: Configuring as mouse
[   300.981] (II) evdev: MOSART Semi. 2.4G Keyboard Mouse: Configuring as keyboard
[   300.981] (II) evdev: MOSART Semi. 2.4G Keyboard Mouse: Adding scrollwheel support
[   300.981] (**) evdev: MOSART Semi. 2.4G Keyboard Mouse: YAxisMapping: buttons 4 and 5
[   300.981] (**) evdev: MOSART Semi. 2.4G Keyboard Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   300.981] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/input/input13/event10"
[   300.981] (II) XINPUT: Adding extended input device "MOSART Semi. 2.4G Keyboard Mouse" (type: KEYBOARD, id 9)
[   300.981] (**) Option "xkb_rules" "evdev"
[   300.981] (**) Option "xkb_model" "pc105"
[   300.981] (**) Option "xkb_layout" "us"
[   300.981] (II) evdev: MOSART Semi. 2.4G Keyboard Mouse: initialized for relative axes.
[   300.981] (WW) evdev: MOSART Semi. 2.4G Keyboard Mouse: ignoring absolute axes.
[   300.981] (**) MOSART Semi. 2.4G Keyboard Mouse: (accel) keeping acceleration scheme 1
[   300.981] (**) MOSART Semi. 2.4G Keyboard Mouse: (accel) acceleration profile 0
[   300.981] (**) MOSART Semi. 2.4G Keyboard Mouse: (accel) acceleration factor: 2.000
[   300.981] (**) MOSART Semi. 2.4G Keyboard Mouse: (accel) acceleration threshold: 4
[   300.982] (II) config/udev: Adding input device MOSART Semi. 2.4G Keyboard Mouse (/dev/input/mouse0)
[   300.982] (II) No input driver specified, ignoring this device.
[   300.982] (II) This device may have been added with another device file.
[   300.982] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101b (/dev/input/event15)
[   300.982] (**) Logitech Unifying Device. Wireless PID:101b: Applying InputClass "evdev pointer catchall"
[   300.982] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:101b'
[   300.982] (**) Logitech Unifying Device. Wireless PID:101b: always reports core events
[   300.982] (**) evdev: Logitech Unifying Device. Wireless PID:101b: Device: "/dev/input/event15"
[   300.982] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Vendor 0x46d Product 0xc52b
[   300.982] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Found 20 mouse buttons
[   300.982] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Found scroll wheel(s)
[   300.982] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Found relative axes
[   300.982] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Found x and y relative axes
[   300.982] (II) evdev: Logitech Unifying Device. Wireless PID:101b: Configuring as mouse
[   300.982] (II) evdev: Logitech Unifying Device. Wireless PID:101b: Adding scrollwheel support
[   300.982] (**) evdev: Logitech Unifying Device. Wireless PID:101b: YAxisMapping: buttons 4 and 5
[   300.982] (**) evdev: Logitech Unifying Device. Wireless PID:101b: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   300.982] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-8/3-8:1.2/0003:046D:C52B.0005/input/input18/event15"
[   300.982] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:101b" (type: MOUSE, id 10)
[   300.982] (II) evdev: Logitech Unifying Device. Wireless PID:101b: initialized for relative axes.
[   300.982] (**) Logitech Unifying Device. Wireless PID:101b: (accel) keeping acceleration scheme 1
[   300.982] (**) Logitech Unifying Device. Wireless PID:101b: (accel) acceleration profile 0
[   300.982] (**) Logitech Unifying Device. Wireless PID:101b: (accel) acceleration factor: 2.000
[   300.982] (**) Logitech Unifying Device. Wireless PID:101b: (accel) acceleration threshold: 4
[   300.982] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101b (/dev/input/mouse1)
[   300.982] (II) No input driver specified, ignoring this device.
[   300.982] (II) This device may have been added with another device file.
[   300.982] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event3)
[   300.982] (II) No input driver specified, ignoring this device.
[   300.982] (II) This device may have been added with another device file.
[   300.982] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event2)
[   300.982] (II) No input driver specified, ignoring this device.
[   300.982] (II) This device may have been added with another device file.
[   300.982] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event8)
[   300.982] (II) No input driver specified, ignoring this device.
[   300.982] (II) This device may have been added with another device file.
[   300.983] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event7)
[   300.983] (II) No input driver specified, ignoring this device.
[   300.983] (II) This device may have been added with another device file.
[   300.983] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event6)
[   300.983] (II) No input driver specified, ignoring this device.
[   300.983] (II) This device may have been added with another device file.
[   300.983] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event5)
[   300.983] (II) No input driver specified, ignoring this device.
[   300.983] (II) This device may have been added with another device file.
[   300.983] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event4)
[   300.983] (II) No input driver specified, ignoring this device.
[   300.983] (II) This device may have been added with another device file.
[   300.985] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   301.657] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[   301.682] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   301.702] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   301.704] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   301.706] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   302.423] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   302.435] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[   302.442] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[   302.448] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[   302.455] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[   302.768] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   302.816] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[   303.772] (II) evdev: Logitech Unifying Device. Wireless PID:101b: Close
[   303.772] (II) UnloadModule: "evdev"
[   303.772] (II) evdev: MOSART Semi. 2.4G Keyboard Mouse: Close
[   303.772] (II) UnloadModule: "evdev"
[   303.772] (II) evdev: MOSART Semi. 2.4G Keyboard Mouse: Close
[   303.772] (II) UnloadModule: "evdev"
[   303.772] (II) evdev: Power Button: Close
[   303.773] (II) UnloadModule: "evdev"
[   303.773] (II) evdev: Power Button: Close
[   303.773] (II) UnloadModule: "evdev"
[   303.783] (EE) Server terminated successfully (0). Closing log file.
```

---

### Post by Drone4four on 2015-12-13
TJ- on irc said that nouveau wasn't loading because of the nomodeset parameter. So if I remove that parameter at boot then in *theory* nouveau should load and X should start.  But if that fails, TJ- also suggested that I could try **$ sudo ubuntu-drivers autoinstall** .

I will be sure to report back here with an update if either of these things work.

---

### Post by Drone4four on 2015-12-13
I tried starting Ubuntu from Grub without nomodeset.  nouveau may have loaded but X still wouldn't start.  So I ran, **$ sudo ubuntu-drivers autoinstall**. The latest nvidia drivers installed successfully.  I rebooted but again, gdm wouldn’t start and neither would X using **$ startx**.  I don't have an Xorg log file to share right now.  I have to start a live environment. I'll brb with that.

---

### Post by Drone4four on 2015-12-13
X still won't start even after sudo ubuntu-drivers auto-install.

Latest Xorg.0.log:```
[   113.491] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[   113.491] X Protocol Version 11, Revision 0
[   113.492] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[   113.492] Current Operating System: Linux gnosis 3.13.0-71-generic #114-Ubuntu SMP Tue Dec 1 02:34:22 UTC 2015 x86_64
[   113.492] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-71-generic root=UUID=4ca46729-e714-4e8a-9c6b-eedf1d0d1003 ro nomodeset quiet splash
[   113.492] Build Date: 12 February 2015  02:49:29PM
[   113.492] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   113.493] Current version of pixman: 0.30.2
[   113.493] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[   113.493] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   113.494] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 13 20:47:33 2015
[   113.495] (==) Using config file: "/etc/X11/xorg.conf"
[   113.495] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   113.496] (==) ServerLayout "Layout0"
[   113.496] (**) |-->Screen "Screen0" (0)
[   113.496] (**) |   |-->Monitor "Monitor0"
[   113.496] (**) |   |-->Device "Device0"
[   113.496] (**) |-->Input Device "Keyboard0"
[   113.496] (**) |-->Input Device "Mouse0"
[   113.496] (==) Automatically adding devices
[   113.496] (==) Automatically enabling devices
[   113.496] (==) Automatically adding GPU devices
[   113.496] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   113.496] 	Entry deleted from font path.
[   113.496] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   113.496] 	Entry deleted from font path.
[   113.496] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   113.496] 	Entry deleted from font path.
[   113.496] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	built-ins
[   113.496] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   113.496] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   113.496] (WW) Disabling Keyboard0
[   113.496] (WW) Disabling Mouse0
[   113.496] (II) Loader magic: 0x7fbd17f64d40
[   113.496] (II) Module ABI versions:
[   113.496] 	X.Org ANSI C Emulation: 0.4
[   113.496] 	X.Org Video Driver: 15.0
[   113.496] 	X.Org XInput driver : 20.0
[   113.496] 	X.Org Server Extension : 8.0
[   113.497] (II) xfree86: Adding drm device (/dev/dri/card0)
[   113.500] (--) PCI:*(0:6:0:0) 10de:1200:3842:1568 rev 161, Mem @ 0xf8000000/33554432, 0xe8000000/134217728, 0xf0000000/67108864, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[   113.501] Initializing built-in extension Generic Event Extension
[   113.501] Initializing built-in extension SHAPE
[   113.501] Initializing built-in extension MIT-SHM
[   113.501] Initializing built-in extension XInputExtension
[   113.501] Initializing built-in extension XTEST
[   113.501] Initializing built-in extension BIG-REQUESTS
[   113.501] Initializing built-in extension SYNC
[   113.502] Initializing built-in extension XKEYBOARD
[   113.502] Initializing built-in extension XC-MISC
[   113.502] Initializing built-in extension SECURITY
[   113.502] Initializing built-in extension XINERAMA
[   113.502] Initializing built-in extension XFIXES
[   113.502] Initializing built-in extension RENDER
[   113.502] Initializing built-in extension RANDR
[   113.503] Initializing built-in extension COMPOSITE
[   113.503] Initializing built-in extension DAMAGE
[   113.503] Initializing built-in extension MIT-SCREEN-SAVER
[   113.503] Initializing built-in extension DOUBLE-BUFFER
[   113.503] Initializing built-in extension RECORD
[   113.503] Initializing built-in extension DPMS
[   113.503] Initializing built-in extension Present
[   113.504] Initializing built-in extension DRI3
[   113.504] Initializing built-in extension X-Resource
[   113.504] Initializing built-in extension XVideo
[   113.504] Initializing built-in extension XVideo-MotionCompensation
[   113.504] Initializing built-in extension SELinux
[   113.504] Initializing built-in extension XFree86-VidModeExtension
[   113.504] Initializing built-in extension XFree86-DGA
[   113.505] Initializing built-in extension XFree86-DRI
[   113.505] Initializing built-in extension DRI2
[   113.505] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[   113.505] (II) "glx" will be loaded by default.
[   113.505] (WW) "xmir" is not to be loaded by default. Skipping.
[   113.505] (II) LoadModule: "glx"
[   113.505] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[   113.515] (II) Module glx: vendor="NVIDIA Corporation"
[   113.515] 	compiled for 4.0.2, module version = 1.0.0
[   113.515] 	Module class: X.Org Server Extension
[   113.515] (II) NVIDIA GLX Module  352.63  Sat Nov  7 20:52:00 PST 2015
[   113.515] Loading extension GLX
[   113.515] (II) LoadModule: "nvidia"
[   113.516] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   113.516] (II) Module nvidia: vendor="NVIDIA Corporation"
[   113.516] 	compiled for 4.0.2, module version = 1.0.0
[   113.516] 	Module class: X.Org Video Driver
[   113.516] (II) NVIDIA dlloader X Driver  352.63  Sat Nov  7 20:29:25 PST 2015
[   113.516] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   113.516] (--) using VT number 7

[   113.530] (II) Loading sub module "fb"
[   113.530] (II) LoadModule: "fb"
[   113.531] (II) Loading /usr/lib/xorg/modules/libfb.so
[   113.531] (II) Module fb: vendor="X.Org Foundation"
[   113.531] 	compiled for 1.15.1, module version = 1.0.0
[   113.531] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   113.531] (II) Loading sub module "wfb"
[   113.531] (II) LoadModule: "wfb"
[   113.531] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   113.531] (II) Module wfb: vendor="X.Org Foundation"
[   113.531] 	compiled for 1.15.1, module version = 1.0.0
[   113.531] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   113.531] (II) Loading sub module "ramdac"
[   113.531] (II) LoadModule: "ramdac"
[   113.531] (II) Module "ramdac" already built-in
[   113.532] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   113.532] (==) NVIDIA(0): RGB weight 888
[   113.532] (==) NVIDIA(0): Default visual is TrueColor
[   113.532] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   113.532] (**) NVIDIA(0): Enabling 2D acceleration
[   114.237] (II) NVIDIA: Allocated GPU:0 (GPU-30141a0a-bcec-a603-b500-680a8db80c97) @
[   114.237] (II) NVIDIA:     PCI:0000:06:00.0
[   114.273] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:6:0:0
[   114.273] (--) NVIDIA(0):     CRT-0
[   114.273] (--) NVIDIA(0):     CRT-1
[   114.273] (--) NVIDIA(0):     DFP-0
[   114.273] (--) NVIDIA(0):     DFP-1 (boot)
[   114.273] (--) NVIDIA(0):     DFP-2
[   114.275] (--) NVIDIA(0): CRT-0: disconnected
[   114.275] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[   114.275] (--) NVIDIA(0): 
[   114.278] (--) NVIDIA(0): CRT-1: disconnected
[   114.278] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[   114.278] (--) NVIDIA(0): 
[   114.280] (--) NVIDIA(0): DFP-0: disconnected
[   114.280] (--) NVIDIA(0): DFP-0: Internal TMDS
[   114.280] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[   114.280] (--) NVIDIA(0): 
[   114.310] (--) NVIDIA(0): BenQ GW2765 (DFP-1): connected
[   114.310] (--) NVIDIA(0): BenQ GW2765 (DFP-1): Internal TMDS
[   114.310] (--) NVIDIA(0): BenQ GW2765 (DFP-1): 165.0 MHz maximum pixel clock
[   114.310] (--) NVIDIA(0): 
[   114.313] (--) NVIDIA(0): DFP-2: disconnected
[   114.313] (--) NVIDIA(0): DFP-2: Internal TMDS
[   114.313] (--) NVIDIA(0): DFP-2: 330.0 MHz maximum pixel clock
[   114.313] (--) NVIDIA(0): 
[   114.313] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[   114.315] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 560 Ti (GF114) at PCI:6:0:0 (GPU-0)
[   114.315] (--) NVIDIA(0): Memory: 2097152 kBytes
[   114.315] (--) NVIDIA(0): VideoBIOS: 70.24.21.00.62
[   114.315] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   114.330] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   114.330] (**) NVIDIA(0):     device BenQ GW2765 (DFP-1) (Using EDID frequencies has
[   114.330] (**) NVIDIA(0):     been enabled on all display devices.)
[   114.333] (==) NVIDIA(0): 
[   114.333] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[   114.333] (==) NVIDIA(0):     will be used as the requested mode.
[   114.333] (==) NVIDIA(0): 
[   114.334] (II) NVIDIA(0): Validated MetaModes:
[   114.334] (II) NVIDIA(0):     "DFP-1:nvidia-auto-select"
[   114.334] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[   114.344] (--) NVIDIA(0): DPI set to (81, 80); computed from "UseEdidDpi" X config
[   114.344] (--) NVIDIA(0):     option
[   114.344] (--) Depth 24 pixmap format is 32 bpp
[   114.344] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[   114.344] (II) NVIDIA:     access.
[   114.378] (II) NVIDIA(0): Setting mode "DFP-1:nvidia-auto-select"
[   114.418] Loading extension NV-GLX
[   114.426] (==) NVIDIA(0): Disabling shared memory pixmaps
[   114.426] (==) NVIDIA(0): Backing store enabled
[   114.426] (==) NVIDIA(0): Silken mouse enabled
[   114.426] (**) NVIDIA(0): DPMS enabled
[   114.426] Loading extension NV-CONTROL
[   114.426] Loading extension XINERAMA
[   114.426] (II) Loading sub module "dri2"
[   114.426] (II) LoadModule: "dri2"
[   114.426] (II) Module "dri2" already built-in
[   114.426] (II) NVIDIA(0): [DRI2] Setup complete
[   114.426] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[   114.426] (--) RandR disabled
[   114.429] (II) SELinux: Disabled on system
[   114.430] (II) Initializing extension GLX
[   114.445] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   114.470] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   114.470] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   114.470] (II) LoadModule: "evdev"
[   114.470] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   114.471] (II) Module evdev: vendor="X.Org Foundation"
[   114.471] 	compiled for 1.15.0, module version = 2.8.2
[   114.471] 	Module class: X.Org XInput Driver
[   114.471] 	ABI class: X.Org XInput driver, version 20.0
[   114.471] (II) Using input driver 'evdev' for 'Power Button'
[   114.471] (**) Power Button: always reports core events
[   114.471] (**) evdev: Power Button: Device: "/dev/input/event1"
[   114.471] (--) evdev: Power Button: Vendor 0 Product 0x1
[   114.471] (--) evdev: Power Button: Found keys
[   114.471] (II) evdev: Power Button: Configuring as keyboard
[   114.471] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   114.471] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   114.471] (**) Option "xkb_rules" "evdev"
[   114.471] (**) Option "xkb_model" "pc105"
[   114.471] (**) Option "xkb_layout" "us"
[   114.471] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   114.471] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   114.471] (II) Using input driver 'evdev' for 'Power Button'
[   114.471] (**) Power Button: always reports core events
[   114.471] (**) evdev: Power Button: Device: "/dev/input/event0"
[   114.471] (--) evdev: Power Button: Vendor 0 Product 0x1
[   114.471] (--) evdev: Power Button: Found keys
[   114.471] (II) evdev: Power Button: Configuring as keyboard
[   114.471] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   114.471] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   114.471] (**) Option "xkb_rules" "evdev"
[   114.471] (**) Option "xkb_model" "pc105"
[   114.471] (**) Option "xkb_layout" "us"
[   114.472] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:03.0/0000:06:00.0/drm/card0
[   114.472] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[   114.472] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event14)
[   114.472] (II) No input driver specified, ignoring this device.
[   114.472] (II) This device may have been added with another device file.
[   114.472] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event13)
[   114.472] (II) No input driver specified, ignoring this device.
[   114.472] (II) This device may have been added with another device file.
[   114.472] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event12)
[   114.472] (II) No input driver specified, ignoring this device.
[   114.472] (II) This device may have been added with another device file.
[   114.472] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event11)
[   114.472] (II) No input driver specified, ignoring this device.
[   114.472] (II) This device may have been added with another device file.
[   114.472] (II) config/udev: Adding input device MOSART Semi. 2.4G Keyboard Mouse (/dev/input/event9)
[   114.472] (**) MOSART Semi. 2.4G Keyboard Mouse: Applying InputClass "evdev keyboard catchall"
[   114.472] (II) Using input driver 'evdev' for 'MOSART Semi. 2.4G Keyboard Mouse'
[   114.472] (**) MOSART Semi. 2.4G Keyboard Mouse: always reports core events
[   114.472] (**) evdev: MOSART Semi. 2.4G Keyboard Mouse: Device: "/dev/input/event9"
[   114.472] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Vendor 0x62a Product 0x4101
[   114.472] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Found keys
[   114.472] (II) evdev: MOSART Semi. 2.4G Keyboard Mouse: Configuring as keyboard
[   114.472] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input12/event9"
[   114.472] (II) XINPUT: Adding extended input device "MOSART Semi. 2.4G Keyboard Mouse" (type: KEYBOARD, id 8)
[   114.472] (**) Option "xkb_rules" "evdev"
[   114.472] (**) Option "xkb_model" "pc105"
[   114.472] (**) Option "xkb_layout" "us"
[   114.473] (II) config/udev: Adding input device MOSART Semi. 2.4G Keyboard Mouse (/dev/input/event10)
[   114.473] (**) MOSART Semi. 2.4G Keyboard Mouse: Applying InputClass "evdev pointer catchall"
[   114.473] (**) MOSART Semi. 2.4G Keyboard Mouse: Applying InputClass "evdev keyboard catchall"
[   114.473] (II) Using input driver 'evdev' for 'MOSART Semi. 2.4G Keyboard Mouse'
[   114.473] (**) MOSART Semi. 2.4G Keyboard Mouse: always reports core events
[   114.473] (**) evdev: MOSART Semi. 2.4G Keyboard Mouse: Device: "/dev/input/event10"
[   114.473] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Vendor 0x62a Product 0x4101
[   114.473] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Found 9 mouse buttons
[   114.473] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Found scroll wheel(s)
[   114.473] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Found relative axes
[   114.473] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Found x and y relative axes
[   114.473] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Found absolute axes
[   114.473] (II) evdev: MOSART Semi. 2.4G Keyboard Mouse: Forcing absolute x/y axes to exist.
[   114.473] (--) evdev: MOSART Semi. 2.4G Keyboard Mouse: Found keys
[   114.473] (II) evdev: MOSART Semi. 2.4G Keyboard Mouse: Configuring as mouse
[   114.473] (II) evdev: MOSART Semi. 2.4G Keyboard Mouse: Configuring as keyboard
[   114.473] (II) evdev: MOSART Semi. 2.4G Keyboard Mouse: Adding scrollwheel support
[   114.473] (**) evdev: MOSART Semi. 2.4G Keyboard Mouse: YAxisMapping: buttons 4 and 5
[   114.473] (**) evdev: MOSART Semi. 2.4G Keyboard Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   114.473] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/input/input13/event10"
[   114.473] (II) XINPUT: Adding extended input device "MOSART Semi. 2.4G Keyboard Mouse" (type: KEYBOARD, id 9)
[   114.473] (**) Option "xkb_rules" "evdev"
[   114.473] (**) Option "xkb_model" "pc105"
[   114.473] (**) Option "xkb_layout" "us"
[   114.473] (II) evdev: MOSART Semi. 2.4G Keyboard Mouse: initialized for relative axes.
[   114.473] (WW) evdev: MOSART Semi. 2.4G Keyboard Mouse: ignoring absolute axes.
[   114.473] (**) MOSART Semi. 2.4G Keyboard Mouse: (accel) keeping acceleration scheme 1
[   114.473] (**) MOSART Semi. 2.4G Keyboard Mouse: (accel) acceleration profile 0
[   114.473] (**) MOSART Semi. 2.4G Keyboard Mouse: (accel) acceleration factor: 2.000
[   114.473] (**) MOSART Semi. 2.4G Keyboard Mouse: (accel) acceleration threshold: 4
[   114.473] (II) config/udev: Adding input device MOSART Semi. 2.4G Keyboard Mouse (/dev/input/mouse0)
[   114.473] (II) No input driver specified, ignoring this device.
[   114.473] (II) This device may have been added with another device file.
[   114.473] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101b (/dev/input/event15)
[   114.473] (**) Logitech Unifying Device. Wireless PID:101b: Applying InputClass "evdev pointer catchall"
[   114.473] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:101b'
[   114.473] (**) Logitech Unifying Device. Wireless PID:101b: always reports core events
[   114.473] (**) evdev: Logitech Unifying Device. Wireless PID:101b: Device: "/dev/input/event15"
[   114.474] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Vendor 0x46d Product 0xc52b
[   114.474] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Found 20 mouse buttons
[   114.474] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Found scroll wheel(s)
[   114.474] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Found relative axes
[   114.474] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Found x and y relative axes
[   114.474] (II) evdev: Logitech Unifying Device. Wireless PID:101b: Configuring as mouse
[   114.474] (II) evdev: Logitech Unifying Device. Wireless PID:101b: Adding scrollwheel support
[   114.474] (**) evdev: Logitech Unifying Device. Wireless PID:101b: YAxisMapping: buttons 4 and 5
[   114.474] (**) evdev: Logitech Unifying Device. Wireless PID:101b: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   114.474] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-8/3-8:1.2/0003:046D:C52B.0005/input/input18/event15"
[   114.474] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:101b" (type: MOUSE, id 10)
[   114.474] (II) evdev: Logitech Unifying Device. Wireless PID:101b: initialized for relative axes.
[   114.474] (**) Logitech Unifying Device. Wireless PID:101b: (accel) keeping acceleration scheme 1
[   114.474] (**) Logitech Unifying Device. Wireless PID:101b: (accel) acceleration profile 0
[   114.474] (**) Logitech Unifying Device. Wireless PID:101b: (accel) acceleration factor: 2.000
[   114.474] (**) Logitech Unifying Device. Wireless PID:101b: (accel) acceleration threshold: 4
[   114.474] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101b (/dev/input/mouse1)
[   114.474] (II) No input driver specified, ignoring this device.
[   114.474] (II) This device may have been added with another device file.
[   114.474] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event3)
[   114.474] (II) No input driver specified, ignoring this device.
[   114.474] (II) This device may have been added with another device file.
[   114.474] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event2)
[   114.474] (II) No input driver specified, ignoring this device.
[   114.474] (II) This device may have been added with another device file.
[   114.474] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event8)
[   114.474] (II) No input driver specified, ignoring this device.
[   114.474] (II) This device may have been added with another device file.
[   114.474] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event7)
[   114.474] (II) No input driver specified, ignoring this device.
[   114.474] (II) This device may have been added with another device file.
[   114.474] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event6)
[   114.474] (II) No input driver specified, ignoring this device.
[   114.475] (II) This device may have been added with another device file.
[   114.475] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event5)
[   114.475] (II) No input driver specified, ignoring this device.
[   114.475] (II) This device may have been added with another device file.
[   114.475] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event4)
[   114.475] (II) No input driver specified, ignoring this device.
[   114.475] (II) This device may have been added with another device file.
[   114.757] (--) NVIDIA(GPU-0): BenQ GW2765 (DFP-1): connected
[   114.757] (--) NVIDIA(GPU-0): BenQ GW2765 (DFP-1): Internal TMDS
[   114.757] (--) NVIDIA(GPU-0): BenQ GW2765 (DFP-1): 225.0 MHz maximum pixel clock
[   114.757] (--) NVIDIA(GPU-0): 
[   114.788] (--) NVIDIA(GPU-0): BenQ GW2765 (DFP-1): connected
[   114.788] (--) NVIDIA(GPU-0): BenQ GW2765 (DFP-1): Internal TMDS
[   114.788] (--) NVIDIA(GPU-0): BenQ GW2765 (DFP-1): 225.0 MHz maximum pixel clock
[   114.788] (--) NVIDIA(GPU-0): 
[   114.908] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   127.362] (II) evdev: Logitech Unifying Device. Wireless PID:101b: Close
[   127.362] (II) UnloadModule: "evdev"
[   127.362] (II) evdev: MOSART Semi. 2.4G Keyboard Mouse: Close
[   127.362] (II) UnloadModule: "evdev"
[   127.362] (II) evdev: MOSART Semi. 2.4G Keyboard Mouse: Close
[   127.362] (II) UnloadModule: "evdev"
[   127.362] (II) evdev: Power Button: Close
[   127.362] (II) UnloadModule: "evdev"
[   127.362] (II) evdev: Power Button: Close
[   127.362] (II) UnloadModule: "evdev"
[   127.370] (II) NVIDIA: Freed GPU:0 (GPU-30141a0a-bcec-a603-b500-680a8db80c97) @
[   127.370] (II) NVIDIA:     PCI:0000:06:00.0
[   127.430] (II) NVIDIA(GPU-0): Deleting GPU-0
[   127.431] (EE) Server terminated successfully (0). Closing log file.
```

Edit: Its also worth noting that when all that failed, I tried: $ nvidia-xconfig .

Now I'm gonna try, **$ service gdm start** instead of **$ startx**.

brb

---

### Post by Drone4four on 2015-12-13
**$ service gdm start** and **$ service lightdm start** breaks with this traceback:

```
start.Rejected send message, 1matched rules; type=”method_call”, sender=”:1.53” uid=1000 pid 2745 comm=”start gdm”) interface=”com.ubuntu.Upstart0_6.Job” member=”start” error name=”(unset)” request_reply=”0” destination=”(ubuntu.Upstart”(uid=0 pid=1 comm=”/sbin/init”)
```

dmesg: [http://paste.ubuntu.com/14001029/](http://paste.ubuntu.com/14001029/)

It was a bitch having to scrawl that traceback with pen and paper.  I tried **$ service gdm start >>error.txt** but there error.txt file was empty.  **$ dmesg>>dmesgerror.txt** worked perfectly but I couldn't figure out how to capture the $ service gdm start traceback in a similar way.  I even tried **$ service gdm start | >>error.txt** and **$ service gdm start . >>error.txt**  . How do I capture **$ service gdm start >>error.txt** so as to avoid spelling mistakes and be quicker?

---

### Post by Drone4four on 2015-12-14
All I had to do was add 'sudo' before 'service'.  

Although I'm still curious as to how to capture the output of a given command into a text file for troubleshooting.  Anyone?

---

### Post by efflandt on 2015-12-15
To redirect both stdout and stderr to a file, example from **man bash**:```
ls > dirlist 2>&1
```Or if you want to append to existing file instead of replace it (would still create the file if it does not exist):```
command >> file 2>&1
```

---

