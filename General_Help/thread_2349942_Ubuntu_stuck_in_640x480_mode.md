---
title: "Ubuntu stuck in 640x480 mode"
date: 2017-01-19
forum: General Help
---

### Post by virgodave61 on 2017-01-19
I shut my computer off and went to work then turned it back on when I got home and now it boots up in 640x480 mode. If I go into the settings it says internal monitor, which isn't the case and nothing can be changed. I'm using Ubuntu 16.04.1 LTS, with a Geforce 6150SE Nforce 430 graphics chipset. I spent about six hours last night googleing this, then tried reinstalling the driver, but it said I need to shut down the X-server first, so I used the iightdm stop command or something like that and the screen turned black with one line of type at the top, like you get when shutting it down and it was locked up that way, it also gave me an error something about needing to use the legacy driver instead of the one Nvidia said I needed. If I use the Nvidia settings program it opens with pretty much nothing in it and nothing much to change or set like resolution, not even a mention of x-server on the left side. If anyone has any ideas I would appreciate the help I'm really lost and a noob when it comes to Ubuntu internals, so please don't assume when you say something that I know what your talking about.

---

### Post by gdesilva on 2017-01-20
Check out the following link
[http://askubuntu.com/questions/231972/nvidia-geforce-6150se-nforce-430](http://askubuntu.com/questions/231972/nvidia-geforce-6150se-nforce-430)

It appears nouveau driver is the way to go but I would do more research on this before settling on nouveau driver. Good luck.

---

### Post by virgodave61 on 2017-01-21
Thanks!

When I try to check my current driver, it seams there isn't one.???????
```
dave@dave:~$ lshw -c video
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: C61 [GeForce 6150SE nForce 430]
       vendor: NVIDIA Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fb000000-fbffffff memory:e0000000-efffffff memory:fa000000-faffffff memory:febc0000-febdffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

---

### Post by mörgæs on 2017-01-21
Does [this]("https://ubuntuforums.org/showthread.php?t=2349266&p=13595345&viewfull=1#post13595345") help?

---

### Post by virgodave61 on 2017-01-21
No that doesn't help, a live boot works and It wasn't a new install or upgrade, so am still stuck. "Don't use this space for a list of your hardware. It only creates false hits in the search engines.", what does this mean?
Dave

---

### Post by gdesilva on 2017-01-22
What does the /var/log/Xorg.0.log say? This should indicate any issues with loading the driver. Post the log - someone might be able to quickly work out what the issue is.

---

### Post by mörgæs on 2017-01-22
> **virgodave61 said:**
> No that doesn't help...

Because you tried and it failed or because you didn't try?

> **virgodave61 said:**
> "Don't use this space for a list of your hardware. It only creates false hits in the search engines.", what does this mean?

Some people use their footnote as an option for showing (or showing off) a list of their hardware, often quite detailed, for no known purpose. The footnote is visible in all posts, also in threads not dealing with hardware and in threads dealing with unrelated hardware. This confuses both users and search engines.

---

### Post by virgodave61 on 2017-01-22
The log says:
```
[    22.959] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    22.959] X Protocol Version 11, Revision 0
[    22.959] Build Operating System: Linux 4.4.0-45-generic i686 Ubuntu
[    22.959] Current Operating System: Linux dave 4.4.0-59-generic #80-Ubuntu SMP Fri Jan 6 17:36:54 UTC 2017 i686
[    22.959] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-59-generic root=UUID=708ff812-7177-4332-a25c-d22821d34c69 ro quiet splash vt.handoff=7
[    22.959] Build Date: 02 November 2016  10:05:16PM
[    22.959] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    22.959] Current version of pixman: 0.33.6
[    22.959] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    22.959] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.959] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 21 08:06:29 2017
[    22.991] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.992] (==) No Layout section.  Using the first Screen section.
[    22.992] (==) No screen section available. Using defaults.
[    22.992] (**) |-->Screen "Default Screen Section" (0)
[    22.992] (**) |   |-->Monitor "<default monitor>"
[    23.016] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    23.017] (==) Automatically adding devices
[    23.017] (==) Automatically enabling devices
[    23.017] (==) Automatically adding GPU devices
[    23.017] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    23.017] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.017] 	Entry deleted from font path.
[    23.017] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    23.017] 	Entry deleted from font path.
[    23.017] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    23.017] 	Entry deleted from font path.
[    23.017] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    23.017] 	Entry deleted from font path.
[    23.017] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    23.017] 	Entry deleted from font path.
[    23.017] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    23.017] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.017] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.045] (II) Loader magic: 0x802dd700
[    23.045] (II) Module ABI versions:
[    23.046] 	X.Org ANSI C Emulation: 0.4
[    23.046] 	X.Org Video Driver: 20.0
[    23.046] 	X.Org XInput driver : 22.1
[    23.046] 	X.Org Server Extension : 9.0
[    23.047] (++) using VT number 7

[    23.047] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    23.047] (--) PCI:*(0:0:13:0) 10de:03d0:1025:0394 rev 162, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xfa000000/16777216, BIOS @ 0x????????/131072
[    23.056] (II) LoadModule: "glx"
[    23.078] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    23.224] (II) Module glx: vendor="X.Org Foundation"
[    23.224] 	compiled for 1.18.4, module version = 1.0.0
[    23.224] 	ABI class: X.Org Server Extension, version 9.0
[    23.224] (==) AIGLX enabled
[    23.224] (==) Matched nvidia as autoconfigured driver 0
[    23.224] (==) Matched nouveau as autoconfigured driver 1
[    23.224] (==) Matched modesetting as autoconfigured driver 2
[    23.224] (==) Matched fbdev as autoconfigured driver 3
[    23.224] (==) Matched vesa as autoconfigured driver 4
[    23.224] (==) Assigned the driver to the xf86ConfigLayout
[    23.224] (II) LoadModule: "nvidia"
[    23.225] (WW) Warning, couldn't open module nvidia
[    23.225] (II) UnloadModule: "nvidia"
[    23.225] (II) Unloading nvidia
[    23.225] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    23.225] (II) LoadModule: "nouveau"
[    23.225] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    23.262] (II) Module nouveau: vendor="X.Org Foundation"
[    23.262] 	compiled for 1.18.4, module version = 1.0.13
[    23.262] 	Module class: X.Org Video Driver
[    23.262] 	ABI class: X.Org Video Driver, version 20.0
[    23.262] (II) LoadModule: "modesetting"
[    23.263] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    23.263] (II) Module modesetting: vendor="X.Org Foundation"
[    23.263] 	compiled for 1.18.4, module version = 1.18.4
[    23.263] 	Module class: X.Org Video Driver
[    23.263] 	ABI class: X.Org Video Driver, version 20.0
[    23.263] (II) LoadModule: "fbdev"
[    23.263] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.263] (II) Module fbdev: vendor="X.Org Foundation"
[    23.263] 	compiled for 1.18.1, module version = 0.4.4
[    23.263] 	Module class: X.Org Video Driver
[    23.263] 	ABI class: X.Org Video Driver, version 20.0
[    23.263] (II) LoadModule: "vesa"
[    23.263] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.263] (II) Module vesa: vendor="X.Org Foundation"
[    23.263] 	compiled for 1.18.1, module version = 2.3.4
[    23.263] 	Module class: X.Org Video Driver
[    23.263] 	ABI class: X.Org Video Driver, version 20.0
[    23.263] (==) Matched nvidia as autoconfigured driver 0
[    23.263] (==) Matched nouveau as autoconfigured driver 1
[    23.263] (==) Matched modesetting as autoconfigured driver 2
[    23.263] (==) Matched fbdev as autoconfigured driver 3
[    23.263] (==) Matched vesa as autoconfigured driver 4
[    23.263] (==) Assigned the driver to the xf86ConfigLayout
[    23.263] (II) LoadModule: "nvidia"
[    23.263] (WW) Warning, couldn't open module nvidia
[    23.263] (II) UnloadModule: "nvidia"
[    23.263] (II) Unloading nvidia
[    23.263] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    23.263] (II) LoadModule: "nouveau"
[    23.263] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    23.263] (II) Module nouveau: vendor="X.Org Foundation"
[    23.263] 	compiled for 1.18.4, module version = 1.0.13
[    23.263] 	Module class: X.Org Video Driver
[    23.263] 	ABI class: X.Org Video Driver, version 20.0
[    23.263] (II) UnloadModule: "nouveau"
[    23.263] (II) Unloading nouveau
[    23.263] (II) Failed to load module "nouveau" (already loaded, 0)
[    23.263] (II) LoadModule: "modesetting"
[    23.264] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    23.264] (II) Module modesetting: vendor="X.Org Foundation"
[    23.264] 	compiled for 1.18.4, module version = 1.18.4
[    23.264] 	Module class: X.Org Video Driver
[    23.264] 	ABI class: X.Org Video Driver, version 20.0
[    23.264] (II) UnloadModule: "modesetting"
[    23.264] (II) Unloading modesetting
[    23.264] (II) Failed to load module "modesetting" (already loaded, 0)
[    23.264] (II) LoadModule: "fbdev"
[    23.264] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.264] (II) Module fbdev: vendor="X.Org Foundation"
[    23.264] 	compiled for 1.18.1, module version = 0.4.4
[    23.264] 	Module class: X.Org Video Driver
[    23.264] 	ABI class: X.Org Video Driver, version 20.0
[    23.264] (II) UnloadModule: "fbdev"
[    23.264] (II) Unloading fbdev
[    23.264] (II) Failed to load module "fbdev" (already loaded, 0)
[    23.264] (II) LoadModule: "vesa"
[    23.264] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.264] (II) Module vesa: vendor="X.Org Foundation"
[    23.264] 	compiled for 1.18.1, module version = 2.3.4
[    23.264] 	Module class: X.Org Video Driver
[    23.264] 	ABI class: X.Org Video Driver, version 20.0
[    23.264] (II) UnloadModule: "vesa"
[    23.264] (II) Unloading vesa
[    23.264] (II) Failed to load module "vesa" (already loaded, 0)
[    23.264] (II) NOUVEAU driver 
[    23.264] (II) NOUVEAU driver for NVIDIA chipset families :
[    23.264] 	RIVA TNT        (NV04)
[    23.264] 	RIVA TNT2       (NV05)
[    23.264] 	GeForce 256     (NV10)
[    23.264] 	GeForce 2       (NV11, NV15)
[    23.264] 	GeForce 4MX     (NV17, NV18)
[    23.264] 	GeForce 3       (NV20)
[    23.264] 	GeForce 4Ti     (NV25, NV28)
[    23.264] 	GeForce FX      (NV3x)
[    23.264] 	GeForce 6       (NV4x)
[    23.264] 	GeForce 7       (G7x)
[    23.264] 	GeForce 8       (G8x)
[    23.264] 	GeForce GTX 200 (NVA0)
[    23.264] 	GeForce GTX 400 (NVC0)
[    23.264] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    23.264] (II) FBDEV: driver for framebuffer: fbdev
[    23.264] (II) VESA: driver for VESA chipsets: vesa
[    23.440] (EE) [drm] Failed to open DRM device for pci:0000:00:0d.0: -19
[    23.609] (EE) [drm] Failed to open DRM device for pci:0000:00:0d.0: -19
[    23.609] (EE) open /dev/dri/card0: No such file or directory
[    23.609] (EE) open /dev/dri/card0: No such file or directory
[    23.609] (WW) Falling back to old probe method for modesetting
[    23.609] (EE) open /dev/dri/card0: No such file or directory
[    23.609] (EE) open /dev/dri/card0: No such file or directory
[    23.609] (II) Loading sub module "fbdevhw"
[    23.609] (II) LoadModule: "fbdevhw"
[    23.609] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    23.609] (II) Module fbdevhw: vendor="X.Org Foundation"
[    23.609] 	compiled for 1.18.4, module version = 0.0.2
[    23.609] 	ABI class: X.Org Video Driver, version 20.0
[    23.609] (**) FBDEV(2): claimed PCI slot 0@0:13:0
[    23.609] (II) FBDEV(2): using default device
[    23.609] (WW) Falling back to old probe method for vesa
[    23.609] (EE) Screen 0 deleted because of no matching config section.
[    23.609] (II) UnloadModule: "modesetting"
[    23.609] (EE) Screen 0 deleted because of no matching config section.
[    23.609] (II) UnloadModule: "modesetting"
[    23.610] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    23.610] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    23.610] (==) FBDEV(0): RGB weight 888
[    23.610] (==) FBDEV(0): Default visual is TrueColor
[    23.610] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    23.610] (II) FBDEV(0): hardware: VESA VGA (video memory: 1216kB)
[    23.610] (II) FBDEV(0): checking modes against framebuffer device...
[    23.610] (II) FBDEV(0): checking modes against monitor...
[    23.610] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)
[    23.610] (**) FBDEV(0):  Built-in mode "current": 30.7 MHz, 36.9 kHz, 73.3 Hz
[    23.610] (II) FBDEV(0): Modeline "current"x0.0   30.72  640 672 752 832  480 484 488 504 -hsync -vsync -csync (36.9 kHz b)
[    23.610] (==) FBDEV(0): DPI set to (96, 96)
[    23.610] (II) Loading sub module "fb"
[    23.610] (II) LoadModule: "fb"
[    23.610] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.610] (II) Module fb: vendor="X.Org Foundation"
[    23.610] 	compiled for 1.18.4, module version = 1.0.0
[    23.610] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.610] (**) FBDEV(0): using shadow framebuffer
[    23.610] (II) Loading sub module "shadow"
[    23.610] (II) LoadModule: "shadow"
[    23.610] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    23.610] (II) Module shadow: vendor="X.Org Foundation"
[    23.610] 	compiled for 1.18.4, module version = 1.1.0
[    23.610] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.610] (II) UnloadModule: "vesa"
[    23.610] (II) Unloading vesa
[    23.610] (==) Depth 24 pixmap format is 32 bpp
[    23.610] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[    23.627] (==) FBDEV(0): Backing store enabled
[    23.630] (==) FBDEV(0): DPMS enabled
[    23.631] (==) RandR enabled
[    23.636] (II) SELinux: Disabled on system
[    23.637] (II) AIGLX: Screen 0 is not DRI2 capable
[    23.637] (EE) AIGLX: reverting to software rendering
[    24.008] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    24.009] (II) AIGLX: Loaded and initialized swrast
[    24.009] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    24.075] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    24.075] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.075] (II) LoadModule: "evdev"
[    24.075] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.092] (II) Module evdev: vendor="X.Org Foundation"
[    24.092] 	compiled for 1.18.1, module version = 2.10.1
[    24.092] 	Module class: X.Org XInput Driver
[    24.092] 	ABI class: X.Org XInput driver, version 22.1
[    24.092] (II) Using input driver 'evdev' for 'Power Button'
[    24.092] (**) Power Button: always reports core events
[    24.092] (**) evdev: Power Button: Device: "/dev/input/event1"
[    24.092] (--) evdev: Power Button: Vendor 0 Product 0x1
[    24.092] (--) evdev: Power Button: Found keys
[    24.092] (II) evdev: Power Button: Configuring as keyboard
[    24.092] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    24.092] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    24.092] (**) Option "xkb_rules" "evdev"
[    24.092] (**) Option "xkb_model" "pc105"
[    24.092] (**) Option "xkb_layout" "us"
[    24.093] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    24.093] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.093] (II) Using input driver 'evdev' for 'Power Button'
[    24.093] (**) Power Button: always reports core events
[    24.093] (**) evdev: Power Button: Device: "/dev/input/event0"
[    24.093] (--) evdev: Power Button: Vendor 0 Product 0x1
[    24.093] (--) evdev: Power Button: Found keys
[    24.093] (II) evdev: Power Button: Configuring as keyboard
[    24.093] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    24.093] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    24.093] (**) Option "xkb_rules" "evdev"
[    24.093] (**) Option "xkb_model" "pc105"
[    24.093] (**) Option "xkb_layout" "us"
[    24.094] (II) config/udev: Adding input device Logitech K360 (/dev/input/event2)
[    24.094] (**) Logitech K360: Applying InputClass "evdev keyboard catchall"
[    24.094] (II) Using input driver 'evdev' for 'Logitech K360'
[    24.094] (**) Logitech K360: always reports core events
[    24.094] (**) evdev: Logitech K360: Device: "/dev/input/event2"
[    24.094] (--) evdev: Logitech K360: Vendor 0x46d Product 0x4004
[    24.094] (--) evdev: Logitech K360: Found 1 mouse buttons
[    24.094] (--) evdev: Logitech K360: Found scroll wheel(s)
[    24.094] (--) evdev: Logitech K360: Found relative axes
[    24.094] (II) evdev: Logitech K360: Forcing relative x/y axes to exist.
[    24.094] (--) evdev: Logitech K360: Found absolute axes
[    24.094] (II) evdev: Logitech K360: Forcing absolute x/y axes to exist.
[    24.094] (--) evdev: Logitech K360: Found keys
[    24.094] (II) evdev: Logitech K360: Configuring as mouse
[    24.094] (II) evdev: Logitech K360: Configuring as keyboard
[    24.094] (II) evdev: Logitech K360: Adding scrollwheel support
[    24.094] (**) evdev: Logitech K360: YAxisMapping: buttons 4 and 5
[    24.094] (**) evdev: Logitech K360: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.094] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-7/2-7:1.2/0003:046D:C52B.0003/0003:046D:4004.0004/input/input5/event2"
[    24.094] (II) XINPUT: Adding extended input device "Logitech K360" (type: KEYBOARD, id 8)
[    24.094] (**) Option "xkb_rules" "evdev"
[    24.094] (**) Option "xkb_model" "pc105"
[    24.094] (**) Option "xkb_layout" "us"
[    24.094] (II) evdev: Logitech K360: initialized for relative axes.
[    24.094] (WW) evdev: Logitech K360: ignoring absolute axes.
[    24.094] (**) Logitech K360: (accel) keeping acceleration scheme 1
[    24.094] (**) Logitech K360: (accel) acceleration profile 0
[    24.094] (**) Logitech K360: (accel) acceleration factor: 2.000
[    24.094] (**) Logitech K360: (accel) acceleration threshold: 4
[    24.095] (II) config/udev: Adding input device Logitech K330 (/dev/input/event4)
[    24.095] (**) Logitech K330: Applying InputClass "evdev keyboard catchall"
[    24.095] (II) Using input driver 'evdev' for 'Logitech K330'
[    24.095] (**) Logitech K330: always reports core events
[    24.095] (**) evdev: Logitech K330: Device: "/dev/input/event4"
[    24.095] (--) evdev: Logitech K330: Vendor 0x46d Product 0x4016
[    24.095] (--) evdev: Logitech K330: Found 1 mouse buttons
[    24.095] (--) evdev: Logitech K330: Found scroll wheel(s)
[    24.095] (--) evdev: Logitech K330: Found relative axes
[    24.095] (II) evdev: Logitech K330: Forcing relative x/y axes to exist.
[    24.095] (--) evdev: Logitech K330: Found absolute axes
[    24.095] (II) evdev: Logitech K330: Forcing absolute x/y axes to exist.
[    24.095] (--) evdev: Logitech K330: Found keys
[    24.095] (II) evdev: Logitech K330: Configuring as mouse
[    24.095] (II) evdev: Logitech K330: Configuring as keyboard
[    24.095] (II) evdev: Logitech K330: Adding scrollwheel support
[    24.095] (**) evdev: Logitech K330: YAxisMapping: buttons 4 and 5
[    24.095] (**) evdev: Logitech K330: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.095] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-7/2-7:1.2/0003:046D:C52B.0003/0003:046D:4016.0006/input/input7/event4"
[    24.095] (II) XINPUT: Adding extended input device "Logitech K330" (type: KEYBOARD, id 9)
[    24.095] (**) Option "xkb_rules" "evdev"
[    24.095] (**) Option "xkb_model" "pc105"
[    24.095] (**) Option "xkb_layout" "us"
[    24.095] (II) evdev: Logitech K330: initialized for relative axes.
[    24.095] (WW) evdev: Logitech K330: ignoring absolute axes.
[    24.096] (**) Logitech K330: (accel) keeping acceleration scheme 1
[    24.096] (**) Logitech K330: (accel) acceleration profile 0
[    24.096] (**) Logitech K330: (accel) acceleration factor: 2.000
[    24.096] (**) Logitech K330: (accel) acceleration threshold: 4
[    24.096] (II) config/udev: Adding input device Logitech M215 2nd Gen (/dev/input/event3)
[    24.096] (**) Logitech M215 2nd Gen: Applying InputClass "evdev pointer catchall"
[    24.096] (II) Using input driver 'evdev' for 'Logitech M215 2nd Gen'
[    24.096] (**) Logitech M215 2nd Gen: always reports core events
[    24.096] (**) evdev: Logitech M215 2nd Gen: Device: "/dev/input/event3"
[    24.096] (--) evdev: Logitech M215 2nd Gen: Vendor 0x46d Product 0x401b
[    24.096] (--) evdev: Logitech M215 2nd Gen: Found 20 mouse buttons
[    24.096] (--) evdev: Logitech M215 2nd Gen: Found scroll wheel(s)
[    24.096] (--) evdev: Logitech M215 2nd Gen: Found relative axes
[    24.096] (--) evdev: Logitech M215 2nd Gen: Found x and y relative axes
[    24.096] (II) evdev: Logitech M215 2nd Gen: Configuring as mouse
[    24.096] (II) evdev: Logitech M215 2nd Gen: Adding scrollwheel support
[    24.096] (**) evdev: Logitech M215 2nd Gen: YAxisMapping: buttons 4 and 5
[    24.096] (**) evdev: Logitech M215 2nd Gen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.096] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-7/2-7:1.2/0003:046D:C52B.0003/0003:046D:401B.0005/input/input6/event3"
[    24.096] (II) XINPUT: Adding extended input device "Logitech M215 2nd Gen" (type: MOUSE, id 10)
[    24.096] (II) evdev: Logitech M215 2nd Gen: initialized for relative axes.
[    24.097] (**) Logitech M215 2nd Gen: (accel) keeping acceleration scheme 1
[    24.097] (**) Logitech M215 2nd Gen: (accel) acceleration profile 0
[    24.097] (**) Logitech M215 2nd Gen: (accel) acceleration factor: 2.000
[    24.097] (**) Logitech M215 2nd Gen: (accel) acceleration threshold: 4
[    24.097] (II) config/udev: Adding input device Logitech M215 2nd Gen (/dev/input/mouse0)
[    24.097] (II) No input driver specified, ignoring this device.
[    24.097] (II) This device may have been added with another device file.
[    24.097] (II) config/udev: Adding input device HDA NVidia Line (/dev/input/event7)
[    24.097] (II) No input driver specified, ignoring this device.
[    24.097] (II) This device may have been added with another device file.
[    24.098] (II) config/udev: Adding input device HDA NVidia Line Out (/dev/input/event8)
[    24.098] (II) No input driver specified, ignoring this device.
[    24.098] (II) This device may have been added with another device file.
[    24.098] (II) config/udev: Adding input device HDA NVidia Front Headphone (/dev/input/event9)
[    24.098] (II) No input driver specified, ignoring this device.
[    24.098] (II) This device may have been added with another device file.
[    24.098] (II) config/udev: Adding input device HDA NVidia Front Mic (/dev/input/event5)
[    24.098] (II) No input driver specified, ignoring this device.
[    24.098] (II) This device may have been added with another device file.
[    24.099] (II) config/udev: Adding input device HDA NVidia Rear Mic (/dev/input/event6)
[    24.099] (II) No input driver specified, ignoring this device.
[    24.099] (II) This device may have been added with another device file.
```

---

### Post by Yellow Pasque on 2017-01-22
What driver were you using before the trouble started? Proprietary nvidia or open source nouveau driver?

If you are trying to use nvidia proprietary driver, this is all you should need to do to install it:
```
sudo apt-get install --reinstall nvidia-304
```
DO NOT try to download the driver from nvidia's site and install it manually.

If you are trying to use open source nouveau driver, make sure it is not blacklisted (following command should return nothing):
```
cat /etc/modprobe.d/* | grep nouv
```
Then, try and load the module manually:
```
sudo modprobe -v nouveau
```
If it loads (modprobe doesn't give an error), try to log out and log back in and see if you get correct resolution.

---

### Post by gdesilva on 2017-01-22
Your Xorg log states that nvidia module is not found which probably means that it was not installed(?)

[    23.263] (EE) Failed to load module "nvidia" (module does not exist, 0)

I would do the following;

1. Boot into text mode
2. run 'sudo apt install nvidia-current' which should install the proprietary nvidia driver.
3. reboot.

---

### Post by virgodave61 on 2017-01-23
If I reinstall Nvidia when I boot I get a black screen with a cursor flashing in the upper left corner, then I have to go and purge all Nvidia to get a good boot again.

[code]cat /etc/modprobe.d/* | grep nouv, gives me:
# do not automatically load nouveau as it may prevent nvidia from loading
blacklist nouveau
options nouveau modeset=0
options nouveau modeset=0[]/code

I don't get this I just want to use my computer I turn it on and all of the sudden its messed up, this has never happened with Windows, I use Ubuntu because I hate the greed of Microsoft!

---

### Post by gdesilva on 2017-01-23
Hi, I can understand your frustration but please know that this is  most likely because of nVidia and NOT because of Ubuntu - and no, I have no  affiliations with Ubuntu and I am just an Ubuntu user for the exact  reasons why you are trying to become one. 

The reason why you  have to fiddle around with the config is because nVidia cards do not  work well unless one uses their proprietary drivers. I had to hack my  scripts to get the boot splash image working in one of machines that  uses an old nVidia card. And it appears that Windows also have their share of problems with this card - check it out [here]("https://answers.microsoft.com/en-us/windows/forum/windows_10-hardware/nvidia-geforce-6150se-nforce-430-and-windows-10/00f72dea-df1f-4493-9530-7044b71ba099") - of course this is no consolation for you!

Having said all that, check out the following link,

[http://www.nvidia.com/download/driverResults.aspx/112990/en-us](http://www.nvidia.com/download/driverResults.aspx/112990/en-us)

which indicates that the proprietary driver you need is version 304.134 which supports the GeForce 6150SE nForce 430 (scroll down to find the model number of your card). So, it will be important to make sure you are loading version 304.134 and not a newer version. [This link]("http://www.howtogeek.com/howto/ubuntu/see-what-version-of-a-package-is-installed-on-ubuntu/") will show how to check version number. If the version number is correct, I would re-install the nvidia package to see what happens. If it is not, use Synaptic package manager and see whether you can find the exact version listed and install that one. Sometimes, nvidia-current package may be newer than what you need.


Alternative is to use the open source  driver which is the nouveau driver which may or may not work as well as  the proprietary driver depending what you are trying to do. As mentioned  by Temujin above, if you are going to try out nouveau driver you will  need to 'un-blacklist' the nouveau driver and then load it. It is worth a  try to see whether nouveau driver works without any problems with  screen resolution.

With another Linux distro, the only way I was able to get the proprietary driver working was to download the compatible version from nVidia and install it  - I have not had to do this on Ubuntu so cannot say how easy or difficult it is going to be on Ubuntu. However, when you download and install the driver and when some dependent libraries get automatically updated it screws up your display and on such occasions I had to recompile the nVidia package - not a big deal but something one should not have to do too often.

---

### Post by virgodave61 on 2017-01-23
Thanks 
gdesilva

I appreciate your time, but this is a Ubuntu issue not nVidia, I didn't do a install, upgrade or approve any updates, I just shut my working computer off and when I turned it back on it was messed up!
I went to the nVidia website to find out which driver to use, when I tried to install it I had errors, first was it told me I had to shut down xserver, when I tried that my computer locked up. It also told me I shouldn't use that driver but the legacy driver from ubuntu. Most people on the net say not to use the nVidia drivers.
Thanks for your input, I plan to spend the entire day tomorrow trying to fix this and your advice will help hopefully. I never had to spend much of anytime fixing windows issues, sorry I'm getting frustrated again. I just wish there was a way to lock my computer up to prevent it from being messed up by external forces.

A few months ago my working computer was shut down I came home, turned on my computer, it booted and when I went to type my password I was locked out (login loop), how does this happen? The only option that worked was to backup my files and reinstall Ubuntu.

---

### Post by QIII on 2017-01-23
hello, virgodave61!

It is best to have only one issue going on in a thread.  Otherwise, thing get confusing.

It would probably be best to leave this one to continue with the original question and start a new thread about the login loop.

Thanks!

---

### Post by gdesilva on 2017-01-24
> **virgodave61 said:**
> 

I appreciate your time, but this is a Ubuntu issue not nVidia, I didn't do a install, upgrade or approve any updates, I just shut my working computer off and when I turned it back on it was messed up!


Not saying you are wrong but I am not convinced. Perhaps it would be an issue with your hardware? The only way you are going to find this out is by installing another widely used distro and see whether the issue goes away.

> **virgodave61 said:**
> 
I went to the nVidia website to find out which driver to use, when I tried to install it I had errors, first was it told me I had to shut down xserver, when I tried that my computer locked up. It also told me I shouldn't use that driver but the legacy driver from ubuntu. Most people on the net say not to use the nVidia drivers.

Yes you would need to kill xserver if you want to download and install the version from nVidia site. The way to do would be to boot into recovery mode and drop down to a command prompt and then install the driver. After installing either you can reboot or as a normal user (non root) run startx - I would do the first.

> **virgodave61 said:**
> 
Thanks for your input, I plan to spend the entire day tomorrow trying to fix this and your advice will help hopefully. I never had to spend much of anytime fixing windows issues, sorry I'm getting frustrated again. I just wish there was a way to lock my computer up to prevent it from being messed up by external forces.

In this particular case it would be far better to do a fresh install and take a disk image using something like Clonezilla, in case you run into similar problems again. Of course, this depends on how much data you want to save but given that you have already done so many tweaks, a fresh install seems more logical. Good luck.

---

### Post by mörgæs on 2017-01-24
> **virgodave61 said:**
> I plan to spend the entire day tomorrow trying to fix this 

Post #6 should take around 20 minutes. An additional benefit is that you will get rid of Ubuntu, which is likely too heavy for your hardware.

---

### Post by virgodave61 on 2017-01-24
The login loop was in the past and solved by reinstall. I'm just babbling about my Ubuntu frustration. I do understand the basics of forum use. Thanks for all your help, QIII with solving my issues.

I decided after confronting my attitude problems with Ubuntu to follow mörgæs advice and install Lubuntu, my hardware isn't old, but I've had to many strange problems. Thanks all of you for your help, I will repost when I'm done with the results.

20 minutes right it took two hours just to backup my files. I'm now up in running with 64bit Lbuntu 16.10 with full graphics, yes! Will see what happens in the future. You guys don't understand how much I appreciate your input esp. mörgæs, Thanks! I will mark this issue solved and see what happens. Oh I love my new desktop, I hated that new one they have, forgot what they call it.
Many thanks to all,
Dave

PS Cant figure out how to mark as solved, but it is.

---

### Post by azertyuiop2 on 2017-11-06
> **gdesilva said:**
> Check out the following link
[http://askubuntu.com/questions/231972/nvidia-geforce-6150se-nforce-430](http://askubuntu.com/questions/231972/nvidia-geforce-6150se-nforce-430)

It appears nouveau driver is the way to go but I would do more research on this before settling on nouveau driver. Good luck.

You are absolutely right. I have a latitude D800 that can do 1680x1050 yet on a custom live-dvd it would only get 1024x768, and with forcing vesa video modes, only 1400x1050. Eventually figured out that older live dvd's like the ubuntu 10.04 install, or backtrack 5, will correctly identify the display and get 1680x1050 at 60 Hz, and that the difference was they were loading "nouveau", while a "modprobe nouveau" on my customized DVD, on which I have updated the kernel from the original image, would give me a "cannot find nouveau in /lib/modules ..."

The problem is the new initrd that comes with the newer kernels is much lighter (in size) that the initial one (which by the way had a lot of crapware inside - lots of obscure firmware drivers some of them encrypted, which are really a security risk to keep on your machine, when you are minimally security aware - the "don't talk to strangers", or "don't put things in your mouth that you find on the street" comes to mind) and therefore has probably fewer modules included by default. Why it doesn't have nouveau beats me, as Nvidia are rather popular cards, and nouveau got so uch better lately.

---

### Post by QIII on 2017-11-06
Old thread closed.

---

