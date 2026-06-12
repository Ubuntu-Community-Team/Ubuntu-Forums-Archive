---
title: "Screen Freezes - OS Still operational 14.04"
date: 2015-02-22
forum: General Help
---

### Post by rhys_jones2 on 2015-02-22
Hello all,

Having a bit of an issue, somettimes my screen will randomly freeze. If when this happens i hit CTRL+ALT+DEL and then enter, it will log out, i can log in and it will become operational again. 

There is no event which i can see links the crashes.

I am running stock 14.04 64 bit save for installing Nvidia's drivers

I installed these by doing this 

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
```

and then going into additional drivers and selecting Nvdia's drivers.

my xorg log file is as follows

```
[  1408.341] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[  1408.341] X Protocol Version 11, Revision 0
[  1408.341] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[  1408.341] Current Operating System: Linux rhys-W230SS 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64
[  1408.341] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-30-generic root=UUID=6d70cb50-3da3-4852-b8b5-29174770c11e ro quiet splash
[  1408.341] Build Date: 12 February 2015  11:11:26PM
[  1408.341] xorg-server 2:1.16.0-1ubuntu1.2~trusty2 (For technical support please see http://www.ubuntu.com/support) 
[  1408.341] Current version of pixman: 0.30.2
[  1408.341]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  1408.341] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1408.341] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb 22 14:30:51 2015
[  1408.342] (==) Using config file: "/etc/X11/xorg.conf"
[  1408.342] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1408.342] (==) ServerLayout "layout"
[  1408.342] (**) |-->Screen "nvidia" (0)
[  1408.342] (**) |   |-->Monitor "<default monitor>"
[  1408.342] (**) |   |-->Device "nvidia"
[  1408.342] (==) No monitor specified for screen "nvidia".
    Using a default monitor configuration.
[  1408.342] (**) |-->Inactive Device "intel"
[  1408.342] (==) Automatically adding devices
[  1408.342] (==) Automatically enabling devices
[  1408.342] (==) Automatically adding GPU devices
[  1408.342] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1408.342]     Entry deleted from font path.
[  1408.342] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1408.342]     Entry deleted from font path.
[  1408.342] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1408.342]     Entry deleted from font path.
[  1408.342] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1408.342]     Entry deleted from font path.
[  1408.342] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1408.342]     Entry deleted from font path.
[  1408.342] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  1408.342] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1408.342] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1408.342] (II) Loader magic: 0x7f6430de3c80
[  1408.342] (II) Module ABI versions:
[  1408.342]     X.Org ANSI C Emulation: 0.4
[  1408.342]     X.Org Video Driver: 18.0
[  1408.342]     X.Org XInput driver : 21.0
[  1408.342]     X.Org Server Extension : 8.0
[  1408.342] (II) xfree86: Adding drm device (/dev/dri/card1)
[  1408.342] (II) xfree86: Adding drm device (/dev/dri/card0)
[  1408.343] (--) PCI:*(0:0:2:0) 8086:0416:1558:2300 rev 6, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[  1408.343] (--) PCI: (0:1:0:0) 10de:1392:1558:2300 rev 162, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[  1408.343] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[  1408.343] (II) "glx" will be loaded by default.
[  1408.343] (II) LoadModule: "glx"
[  1408.343] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[  1408.350] (II) Module glx: vendor="NVIDIA Corporation"
[  1408.350]     compiled for 4.0.2, module version = 1.0.0
[  1408.350]     Module class: X.Org Server Extension
[  1408.350] (II) NVIDIA GLX Module  340.76  Thu Jan 22 11:24:42 PST 2015
[  1408.350] (II) LoadModule: "nvidia"
[  1408.350] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  1408.350] (II) Module nvidia: vendor="NVIDIA Corporation"
[  1408.350]     compiled for 4.0.2, module version = 1.0.0
[  1408.350]     Module class: X.Org Video Driver
[  1408.350] (II) LoadModule: "intel"
[  1408.350] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  1408.350] (II) Module intel: vendor="X.Org Foundation"
[  1408.350]     compiled for 1.16.0, module version = 2.99.914
[  1408.350]     Module class: X.Org Video Driver
[  1408.350]     ABI class: X.Org Video Driver, version 18.0
[  1408.350] (II) NVIDIA dlloader X Driver  340.76  Thu Jan 22 11:03:05 PST 2015
[  1408.350] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  1408.350] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[  1408.351] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[  1408.351] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[  1408.351] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[  1408.351] (++) using VT number 7

[  1408.351] (II) Loading sub module "fb"
[  1408.351] (II) LoadModule: "fb"
[  1408.351] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1408.351] (II) Module fb: vendor="X.Org Foundation"
[  1408.351]     compiled for 1.16.0, module version = 1.0.0
[  1408.351]     ABI class: X.Org ANSI C Emulation, version 0.4
[  1408.351] (WW) Unresolved symbol: fbGetGCPrivateKey
[  1408.351] (II) Loading sub module "wfb"
[  1408.351] (II) LoadModule: "wfb"
[  1408.351] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  1408.351] (II) Module wfb: vendor="X.Org Foundation"
[  1408.351]     compiled for 1.16.0, module version = 1.0.0
[  1408.351]     ABI class: X.Org ANSI C Emulation, version 0.4
[  1408.351] (II) Loading sub module "ramdac"
[  1408.351] (II) LoadModule: "ramdac"
[  1408.351] (II) Module "ramdac" already built-in
[  1408.351] (II) intel(G0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[  1408.351] (II) intel(G0): SNA compiled: xserver-xorg-video-intel-lts-utopic 2:2.99.914-1~exp1ubuntu4.2~trusty1 (Maarten Lankhorst <maarten.lankhorst@ubuntu.com>)
[  1408.351] (II) intel(G0): SNA compiled for use with valgrind
[  1408.352] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "nvidia" for depth/fbbpp 24/32
[  1408.352] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[  1408.352] (==) NVIDIA(0): RGB weight 888
[  1408.352] (==) NVIDIA(0): Default visual is TrueColor
[  1408.352] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  1408.352] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[  1408.352] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[  1408.352] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[  1408.352] (**) NVIDIA(0): Enabling 2D acceleration
[  1408.654] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[  1408.655] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 860M (GM107-A) at PCI:1:0:0 (GPU-0)
[  1408.655] (--) NVIDIA(0): Memory: 2097152 kBytes
[  1408.655] (--) NVIDIA(0): VideoBIOS: 82.07.27.00.0a
[  1408.655] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  1408.655] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 860M at PCI:1:0:0
[  1408.655] (--) NVIDIA(0):     none
[  1408.655] (II) NVIDIA(0): Validated MetaModes:
[  1408.655] (II) NVIDIA(0):     "NULL"
[  1408.655] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[  1408.655] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[  1408.655] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[  1408.655] (--) intel(G0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[  1408.655] (--) intel(G0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[  1408.655] (==) intel(G0): Depth 24, (--) framebuffer bpp 32
[  1408.655] (==) intel(G0): RGB weight 888
[  1408.655] (==) intel(G0): Default visual is TrueColor
[  1408.655] (**) intel(G0): Option "AccelMethod" "SNA"
[  1408.655] (II) intel(G0): Output eDP1 has no monitor section
[  1408.656] (--) intel(G0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[  1408.656] (II) intel(G0): Output VGA1 has no monitor section
[  1408.656] (II) intel(G0): Output DP1 has no monitor section
[  1408.656] (II) intel(G0): Output HDMI1 has no monitor section
[  1408.656] (--) intel(G0): Using a maximum size of 256x256 for hardware cursors
[  1408.656] (II) intel(G0): Output VIRTUAL1 has no monitor section
[  1408.656] (==) intel(G0): TearFree disabled
[  1408.656] (==) intel(G0): DPI set to (96, 96)
[  1408.656] (II) Loading sub module "dri2"
[  1408.656] (II) LoadModule: "dri2"
[  1408.656] (II) Module "dri2" already built-in
[  1408.656] (II) Loading sub module "present"
[  1408.656] (II) LoadModule: "present"
[  1408.656] (II) Module "present" already built-in
[  1408.656] (--) Depth 24 pixmap format is 32 bpp
[  1408.656] (II) intel(G0): SNA initialized with Haswell (gen7.5, gt2) backend
[  1408.656] (==) intel(G0): Backing store enabled
[  1408.656] (==) intel(G0): Silken mouse enabled
[  1408.656] (II) intel(G0): HW Cursor enabled
[  1408.656] (II) intel(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  1408.656] (==) intel(G0): DPMS enabled
[  1408.656] (II) intel(G0): [DRI2] Setup complete
[  1408.656] (II) intel(G0): [DRI2]   DRI driver: i965
[  1408.656] (II) intel(G0): [DRI2]   VDPAU driver: i965
[  1408.656] (II) intel(G0): direct rendering: DRI2 enabled
[  1408.656] (II) intel(G0): hardware support for Present enabled
[  1408.656] (WW) intel(G0): Option "AllowEmptyInitialConfiguration" is not used
[  1408.656] (WW) intel(G0): Option "IgnoreDisplayDevices" is not used
[  1408.656] (==) intel(G0): display hotplug detection enabled
[  1408.656] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[  1408.656] (II) NVIDIA:     access.
[  1408.659] (II) NVIDIA(0): Setting mode "NULL"
[  1408.659] (EE) NVIDIA(0): Failed to initiate mode change.
[  1408.659] (EE) NVIDIA(0): Failed to complete mode change
[  1408.667] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[  1408.669] (==) NVIDIA(0): Disabling shared memory pixmaps
[  1408.669] (==) NVIDIA(0): Backing store enabled
[  1408.669] (==) NVIDIA(0): Silken mouse enabled
[  1408.669] (==) NVIDIA(0): DPMS enabled
[  1408.669] (II) Loading sub module "dri2"
[  1408.669] (II) LoadModule: "dri2"
[  1408.669] (II) Module "dri2" already built-in
[  1408.669] (II) NVIDIA(0): [DRI2] Setup complete
[  1408.669] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[  1408.669] (--) RandR disabled
[  1408.673] (II) Initializing extension GLX
[  1409.949] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1409.950] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[  1409.950] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1409.950] (II) LoadModule: "evdev"
[  1409.950] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1409.951] (II) Module evdev: vendor="X.Org Foundation"
[  1409.951]     compiled for 1.16.0, module version = 2.9.0
[  1409.951]     Module class: X.Org XInput Driver
[  1409.951]     ABI class: X.Org XInput driver, version 21.0
[  1409.951] (II) Using input driver 'evdev' for 'Power Button'
[  1409.951] (**) Power Button: always reports core events
[  1409.951] (**) evdev: Power Button: Device: "/dev/input/event3"
[  1409.951] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1409.951] (--) evdev: Power Button: Found keys
[  1409.951] (II) evdev: Power Button: Configuring as keyboard
[  1409.951] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[  1409.951] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  1409.951] (**) Option "xkb_rules" "evdev"
[  1409.951] (**) Option "xkb_model" "pc105"
[  1409.951] (**) Option "xkb_layout" "gb"
[  1409.952] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[  1409.952] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[  1409.952] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  1409.952] (II) Using input driver 'evdev' for 'Video Bus'
[  1409.952] (**) Video Bus: always reports core events
[  1409.952] (**) evdev: Video Bus: Device: "/dev/input/event8"
[  1409.952] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  1409.952] (--) evdev: Video Bus: Found keys
[  1409.952] (II) evdev: Video Bus: Configuring as keyboard
[  1409.952] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input16/event8"
[  1409.952] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[  1409.952] (**) Option "xkb_rules" "evdev"
[  1409.952] (**) Option "xkb_model" "pc105"
[  1409.952] (**) Option "xkb_layout" "gb"
[  1409.953] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[  1409.953] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  1409.953] (II) Using input driver 'evdev' for 'Video Bus'
[  1409.953] (**) Video Bus: always reports core events
[  1409.953] (**) evdev: Video Bus: Device: "/dev/input/event7"
[  1409.953] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  1409.953] (--) evdev: Video Bus: Found keys
[  1409.953] (II) evdev: Video Bus: Configuring as keyboard
[  1409.953] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:4c/LNXVIDEO:00/input/input15/event7"
[  1409.953] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[  1409.953] (**) Option "xkb_rules" "evdev"
[  1409.953] (**) Option "xkb_model" "pc105"
[  1409.953] (**) Option "xkb_layout" "gb"
[  1409.953] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  1409.953] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1409.953] (II) Using input driver 'evdev' for 'Power Button'
[  1409.953] (**) Power Button: always reports core events
[  1409.953] (**) evdev: Power Button: Device: "/dev/input/event0"
[  1409.953] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1409.953] (--) evdev: Power Button: Found keys
[  1409.953] (II) evdev: Power Button: Configuring as keyboard
[  1409.953] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[  1409.953] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[  1409.953] (**) Option "xkb_rules" "evdev"
[  1409.953] (**) Option "xkb_model" "pc105"
[  1409.953] (**) Option "xkb_layout" "gb"
[  1409.953] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[  1409.953] (II) No input driver specified, ignoring this device.
[  1409.953] (II) This device may have been added with another device file.
[  1409.953] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[  1409.953] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  1409.953] (II) Using input driver 'evdev' for 'Sleep Button'
[  1409.953] (**) Sleep Button: always reports core events
[  1409.953] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[  1409.953] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[  1409.953] (--) evdev: Sleep Button: Found keys
[  1409.953] (II) evdev: Sleep Button: Configuring as keyboard
[  1409.953] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[  1409.953] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[  1409.953] (**) Option "xkb_rules" "evdev"
[  1409.953] (**) Option "xkb_model" "pc105"
[  1409.953] (**) Option "xkb_layout" "gb"
[  1409.954] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event11)
[  1409.954] (II) No input driver specified, ignoring this device.
[  1409.954] (II) This device may have been added with another device file.
[  1409.954] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event12)
[  1409.954] (II) No input driver specified, ignoring this device.
[  1409.954] (II) This device may have been added with another device file.
[  1409.954] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event13)
[  1409.954] (II) No input driver specified, ignoring this device.
[  1409.954] (II) This device may have been added with another device file.
[  1409.954] (II) config/udev: Adding input device BisonCam, NB Pro (/dev/input/event5)
[  1409.954] (**) BisonCam, NB Pro: Applying InputClass "evdev keyboard catchall"
[  1409.954] (II) Using input driver 'evdev' for 'BisonCam, NB Pro'
[  1409.954] (**) BisonCam, NB Pro: always reports core events
[  1409.954] (**) evdev: BisonCam, NB Pro: Device: "/dev/input/event5"
[  1409.954] (--) evdev: BisonCam, NB Pro: Vendor 0x5986 Product 0x55c
[  1409.954] (--) evdev: BisonCam, NB Pro: Found keys
[  1409.954] (II) evdev: BisonCam, NB Pro: Configuring as keyboard
[  1409.954] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-8/3-8:1.0/input/input11/event5"
[  1409.954] (II) XINPUT: Adding extended input device "BisonCam, NB Pro" (type: KEYBOARD, id 11)
[  1409.954] (**) Option "xkb_rules" "evdev"
[  1409.954] (**) Option "xkb_model" "pc105"
[  1409.954] (**) Option "xkb_layout" "gb"
[  1409.954] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event9)
[  1409.954] (II) No input driver specified, ignoring this device.
[  1409.954] (II) This device may have been added with another device file.
[  1409.954] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event10)
[  1409.954] (II) No input driver specified, ignoring this device.
[  1409.954] (II) This device may have been added with another device file.
[  1409.954] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[  1409.954] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  1409.954] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  1409.954] (**) AT Translated Set 2 keyboard: always reports core events
[  1409.954] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[  1409.954] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[  1409.954] (--) evdev: AT Translated Set 2 keyboard: Found keys
[  1409.954] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[  1409.954] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[  1409.954] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[  1409.954] (**) Option "xkb_rules" "evdev"
[  1409.954] (**) Option "xkb_model" "pc105"
[  1409.954] (**) Option "xkb_layout" "gb"
[  1409.955] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[  1409.955] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  1409.955] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  1409.955] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[  1409.955] (II) LoadModule: "synaptics"
[  1409.955] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  1409.955] (II) Module synaptics: vendor="X.Org Foundation"
[  1409.955]     compiled for 1.16.0, module version = 1.8.99
[  1409.955]     Module class: X.Org XInput Driver
[  1409.955]     ABI class: X.Org XInput driver, version 21.0
[  1409.955] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  1409.955] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  1409.955] (**) Option "Device" "/dev/input/event6"
[  1409.972] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[  1409.972] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5692 (res 66)
[  1409.972] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4680 (res 102)
[  1409.972] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  1409.972] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  1409.972] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[  1409.972] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[  1409.972] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  1409.972] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  1409.984] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event6"
[  1409.984] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[  1409.984] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  1409.984] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[  1409.984] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.037
[  1409.984] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  1409.984] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  1409.984] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  1409.984] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  1409.984] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  1409.984] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[  1409.984] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[  1410.816] (II) intel(G0): EDID vendor "SDC", prod id 16970
[  1410.816] (II) intel(G0): Printing DDC gathered Modelines:
[  1410.816] (II) intel(G0): Modeline "3200x1800"x0.0  361.31  3200 3248 3280 3316  1800 1802 1807 1816 -hsync -vsync (109.0 kHz eP)
[  1410.816] (II) intel(G0): Modeline "3200x1800"x0.0  361.31  3200 3248 3280 3680  1800 1802 1807 2045 -hsync -vsync (98.2 kHz e)
[  1410.832] reporting 4 5 23 195
[  1410.850] (II) intel(G0): switch to mode 3200x1800@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[  1411.180] reporting 4 5 23 195
[  1411.196] reporting 4 5 23 195
[  1413.344] reporting 4 5 23 195
[  1413.362] (II) intel(G0): switch to mode 3200x1800@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[  1413.720] reporting 4 5 23 195
[  1413.812] reporting 4 5 23 195
[  1413.824] reporting 4 5 23 195
[  1413.832] reporting 4 5 23 195
[  1413.872] reporting 4 5 23 195
[  1413.938] reporting 4 5 23 195
[  1413.948] reporting 4 5 23 195
[  1413.948] reporting 4 5 23 195
[  1413.948] reporting 4 5 23 195
[  1413.949] reporting 4 5 23 195
[  1413.951] reporting 4 5 23 195
[  1413.996] reporting 4 5 23 195
[  1416.557] reporting 4 5 23 195
[  1416.587] reporting 4 5 23 195
[  1416.589] reporting 4 5 23 195
[  1416.601] reporting 4 5 23 195
[  1416.615] reporting 4 5 23 195
[  1416.617] reporting 4 5 23 195
[  1416.652] reporting 4 5 23 195
[  1416.653] reporting 4 5 23 195
[  1416.740] reporting 4 5 23 195
[  1416.745] reporting 4 5 23 195
[  1416.756] reporting 4 5 23 195
[  1416.777] reporting 4 5 23 195
[  1416.806] reporting 4 5 23 195
[  1416.820] reporting 4 5 23 195
[  1416.845] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1416.970] reporting 4 5 23 195
[  1416.975] reporting 4 5 23 195
[  1416.979] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[  1416.984] reporting 4 5 23 195
[  1416.988] reporting 4 5 23 195
[  1416.996] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[  1417.007] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[  1417.013] reporting 4 5 23 195
[  1417.021] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[  1417.036] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[  1417.066] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[  1417.100] reporting 4 5 23 195
[  1417.105] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[  1417.123] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[  1417.226] reporting 4 5 23 195
[  1417.543] (II) XKB: reuse xkmfile /var/lib/xkb/server-314DD79035E9F035CB16F21BBDC5087F36438642.xkm
[  1432.422] reporting 4 5 23 195
[  1432.425] reporting 4 5 23 195
[  1432.547] reporting 4 5 23 195
[  1432.561] reporting 4 5 23 195
[  1435.243] reporting 4 5 23 195
[  1477.425] reporting 4 5 23 195
[  1571.467] reporting 4 5 23 195
[  1610.778] reporting 4 5 23 195
[  1642.456] reporting 4 5 23 195
[  1676.814] reporting 4 5 23 195
[  1737.381] reporting 4 5 23 195
[  1737.682] reporting 4 5 23 195
[  2108.816] reporting 4 5 23 195
[  2289.705] reporting 4 5 23 195
[  3510.208] reporting 4 5 23 195
[  3705.652] reporting 4 5 23 195
[  4298.907] reporting 4 5 23 195
[  4330.399] reporting 4 5 23 195
[  4739.896] reporting 4 5 23 195
```

There is a GPU manager log here 

```
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
grep dmesg status 256
dmesg status 256 == 0? No
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is fglrx kernel module available? no
Is nvidia kernel module available? yes
Vendor/Device Id: 8086:416
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1392
BusID "PCI:1@0:0:0"
Is boot vga? no
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Found "/dev/dri/card0", driven by "i915"
output 0:
    eDP connector
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/nvidia-340/ld.so.conf
Current core alternative: (null)
Is nvidia enabled? yes
Is fglrx enabled? no
Is mesa enabled? no
Is pxpress enabled? no
Is prime enabled? no
Is nvidia available? yes
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is pxpress available? no
Is prime available? yes
Intel IGP detected
Intel hybrid system
Nvidia driver version 340.76 detected
intel_matches: 1, nvidia_matches: 1, intel_set: 1, nvidia_set: 1 x_options_matches: 4
No need to modify xorg.conf. Path: /etc/X11/xorg.conf
No need to change the current bbswitch status
```

let me know if you need anything else

Thanks

Rhys

---

### Post by rhys_jones2 on 2015-02-24
Just an update,

I have tried 

```

sudo apt-get install build-essential
sudo apt-get install linux-source
sudo apt-get install linux-headers-generic
sudo nvidia-xconfig
```

all to no avail.

I have also updated to 14.10 and have the same issue

any more ideas?

---

### Post by rhys_jones2 on 2015-02-24
i have found another way to clear the problem without logging out

Simply enter tty by CTRL+ALT+F1 and then exit it again.

The output of

```
 cat /location/of/syslog | grep -i "error"
```

is

```
Feb 24 20:55:37 minu-W230SS kernel: [    1.234488] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 24 20:55:38 minu-W230SS kernel: [    2.438034] nouveau 0000:01:00.0: Direct firmware load failed with error -2
Feb 24 20:55:38 minu-W230SS kernel: [    2.438459] nouveau 0000:01:00.0: Direct firmware load failed with error -2
Feb 24 20:55:38 minu-W230SS kernel: [    2.439864] nouveau: probe of 0000:01:00.0 failed with error -22
Feb 24 20:55:41 minu-W230SS gnome-session[1530]: WARNING: Error getting login monitor: -2
Feb 24 20:55:44 minu-W230SS NetworkManager[809]: <error> [1424811344.371219] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Feb 24 20:55:54 minu-W230SS gnome-session[2178]: WARNING: Error getting login monitor: -2
Feb 24 20:59:18 minu-W230SS NetworkManager[809]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Feb 24 20:59:45 minu-W230SS kernel: [    1.461708] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 24 20:59:53 minu-W230SS kernel: [    9.168710] nouveau 0000:01:00.0: Direct firmware load failed with error -2
Feb 24 20:59:53 minu-W230SS kernel: [    9.169461] nouveau 0000:01:00.0: Direct firmware load failed with error -2
Feb 24 20:59:53 minu-W230SS kernel: [    9.170655] nouveau: probe of 0000:01:00.0 failed with error -22
Feb 24 20:59:54 minu-W230SS NetworkManager[800]: <error> [1424811594.272907] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Feb 24 21:08:25 minu-W230SS kernel: [    1.567234] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 24 21:08:26 minu-W230SS kernel: [    2.402045] nouveau 0000:01:00.0: Direct firmware load failed with error -2
Feb 24 21:08:26 minu-W230SS kernel: [    2.402398] nouveau 0000:01:00.0: Direct firmware load failed with error -2
Feb 24 21:08:26 minu-W230SS kernel: [    2.403486] nouveau: probe of 0000:01:00.0 failed with error -22
Feb 24 21:08:34 minu-W230SS NetworkManager[799]: <error> [1424812114.864497] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Feb 24 21:14:24 minu-W230SS kernel: [    1.247117] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 24 21:14:32 minu-W230SS NetworkManager[788]: <error> [1424812472.748219] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-network: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.sleep-wake: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wifi: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wwan: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wimax: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.network-control: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.system: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.own: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.hostname: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-network: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.sleep-wake: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wifi: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wwan: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wimax: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.network-control: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.system: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.own: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:14:42 minu-W230SS NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.hostname: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.39': no such name
Feb 24 21:16:42 minu-W230SS NetworkManager[788]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Feb 24 21:22:17 minu-W230SS kernel: [  475.861326] Chrome_ChildThr[6331]: segfault at 0 ip 00007fb9810ca40a sp 00007fb9773a4410 error 6 in libmozalloc.so[7fb9810c9000+2000]
Feb 24 21:31:47 minu-W230SS gnome-session[7367]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
Feb 24 21:37:33 minu-W230SS kernel: [    1.367405] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 24 21:37:43 minu-W230SS NetworkManager[802]: <error> [1424813863.104810] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Feb 24 21:50:58 minu-W230SS NetworkManager[802]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
```

Dont know whether it helps but my full syslog is here, the file was too large for pastebin so i have used tinypaste instead, hope that is ok

[URL="http://tny.cz/ec72fe7e"]http://tny.cz/ec72fe7e


[/URL]

---

### Post by rhys_jones2 on 2015-02-25
The only update to syslog at the time of an event is as follows

```
Feb 25 12:44:01 minu-W230SS acpid: client 1421[0:0] has disconnected
Feb 25 12:44:01 minu-W230SS acpid: client connected from 1421[0:0]
Feb 25 12:44:01 minu-W230SS acpid: 1 client rule loaded
Feb 25 12:44:02 minu-W230SS kernel: [ 2896.278903] vgaarb: this pci device is not a vga device
Feb 25 12:44:04 minu-W230SS dbus[511]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Feb 25 12:44:04 minu-W230SS dbus[511]: [system] Successfully activated service 'org.freedesktop.hostname1'
```

---

### Post by cdoebbler on 2015-10-06
Same problem. Screen freezes, requires reboot. Options above don't work. Running Ubuntu 14.04.3 LTS

---

