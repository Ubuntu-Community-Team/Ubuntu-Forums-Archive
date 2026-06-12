---
title: "Inconsequenet X behaviour / performance"
date: 2015-10-15
forum: General Help
---

### Post by Joost_Plas on 2015-10-15
I&#7743; having some weird inconsequent behaviour on my setup.

The setup is a minimum kiosk setup, mostly based on [http://thepcspy.com/read/building-a-kiosk-computer-ubuntu-1404-chrome/](http://thepcspy.com/read/building-a-kiosk-computer-ubuntu-1404-chrome/)

For some reason every reboot can mean different performance. Or everything is working or my video playback in Chrome (only function of the setup) is extremely laggy and choppy. I also see a huge difference in CPU usage then (average of 75 % vs. 25 % for a good boot). I&#7743; trying to look at all the relevant logs but I cannot find the problem. So the situation changes with reboots, while all the other factors are constant.

First I thought it was a compton issue (which I use for compositioning), but the bad boots are way worse then a succesfull boot without compton.
It might be due to the kernel. I am using this setup awhile and never had these issues. I might try to downgrade but I would really like to dive into the problem.
Another change lately is that I installed lighttpd on this machine.

I tried comparing all the logs, but nothing is really standing out for me (with my limited knowledge). 1 thing I noticed is the ´fatal error: no screens found´ message, but I think I always had this and this message is during a succesfull boot!

Really hope someone can shed some light on this

Some more info:

Ubuntu 14.04.3

uname -r: 4.1.6-040106-generic

These are the logs of a succesfull boot (so with good performance and low cpu usage):

Xorg.0.log

```
[    18.957] X.Org X Server 1.15.1
Release Date: 2014-04-13
[    18.957] X Protocol Version 11, Revision 0
[    18.958] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[    18.958] Current Operating System: Linux hoogstraat-client-1 4.1.6-040106-generic #201508170230 SMP Mon Aug 17 06:32:14 UTC 2015 x86_64
[    18.958] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.1.6-040106-generic root=UUID=c456624b-f6c2-4dc7-bf92-640922e83f77 ro quiet splash vt.handoff=7
[    18.958] Build Date: 12 February 2015  02:49:29PM
[    18.958] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[    18.958] Current version of pixman: 0.30.2
[    18.958]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    18.958] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.958] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 15 16:09:17 2015
[    18.958] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.959] (==) No Layout section.  Using the first Screen section.
[    18.959] (==) No screen section available. Using defaults.
[    18.959] (**) |-->Screen "Default Screen Section" (0)
[    18.959] (**) |   |-->Monitor "<default monitor>"
[    18.959] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    18.959] (==) Automatically adding devices
[    18.959] (==) Automatically enabling devices
[    18.959] (==) Automatically adding GPU devices
[    18.959] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.959]     Entry deleted from font path.
[    18.959] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.959]     Entry deleted from font path.
[    18.959] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.959]     Entry deleted from font path.
[    18.959] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    18.959]     Entry deleted from font path.
[    18.959] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.959]     Entry deleted from font path.
[    18.959] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.959]     Entry deleted from font path.
[    18.959] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    built-ins
[    18.959] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.959] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.959] (II) Loader magic: 0x55a27a554d40
[    18.959] (II) Module ABI versions:
[    18.959]     X.Org ANSI C Emulation: 0.4
[    18.959]     X.Org Video Driver: 15.0
[    18.959]     X.Org XInput driver : 20.0
[    18.959]     X.Org Server Extension : 8.0
[    18.959] (II) xfree86: Adding drm device (/dev/dri/card0)
[    18.960] (--) PCI:*(0:0:2:0) 8086:1606:1458:1000 rev 8, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, I/O @ 0x0000f000/64
[    18.960] Initializing built-in extension Generic Event Extension
[    18.960] Initializing built-in extension SHAPE
[    18.960] Initializing built-in extension MIT-SHM
[    18.960] Initializing built-in extension XInputExtension
[    18.960] Initializing built-in extension XTEST
[    18.961] Initializing built-in extension BIG-REQUESTS
[    18.961] Initializing built-in extension SYNC
[    18.961] Initializing built-in extension XKEYBOARD
[    18.961] Initializing built-in extension XC-MISC
[    18.961] Initializing built-in extension SECURITY
[    18.961] Initializing built-in extension XINERAMA
[    18.961] Initializing built-in extension XFIXES
[    18.961] Initializing built-in extension RENDER
[    18.961] Initializing built-in extension RANDR
[    18.961] Initializing built-in extension COMPOSITE
[    18.961] Initializing built-in extension DAMAGE
[    18.961] Initializing built-in extension MIT-SCREEN-SAVER
[    18.961] Initializing built-in extension DOUBLE-BUFFER
[    18.961] Initializing built-in extension RECORD
[    18.961] Initializing built-in extension DPMS
[    18.961] Initializing built-in extension Present
[    18.961] Initializing built-in extension DRI3
[    18.961] Initializing built-in extension X-Resource
[    18.961] Initializing built-in extension XVideo
[    18.961] Initializing built-in extension XVideo-MotionCompensation
[    18.961] Initializing built-in extension SELinux
[    18.961] Initializing built-in extension XFree86-VidModeExtension
[    18.961] Initializing built-in extension XFree86-DGA
[    18.961] Initializing built-in extension XFree86-DRI
[    18.961] Initializing built-in extension DRI2
[    18.961] (II) LoadModule: "glx"
[    18.962] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.962] (II) Module glx: vendor="X.Org Foundation"
[    18.962]     compiled for 1.15.1, module version = 1.0.0
[    18.962]     ABI class: X.Org Server Extension, version 8.0
[    18.962] (==) AIGLX enabled
[    18.962] Loading extension GLX
[    18.963] (==) Matched intel as autoconfigured driver 0
[    18.963] (==) Matched intel as autoconfigured driver 1
[    18.963] (==) Matched modesetting as autoconfigured driver 2
[    18.963] (==) Matched fbdev as autoconfigured driver 3
[    18.963] (==) Matched vesa as autoconfigured driver 4
[    18.963] (==) Assigned the driver to the xf86ConfigLayout
[    18.963] (II) LoadModule: "intel"
[    18.963] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.963] (II) Module intel: vendor="X.Org Foundation"
[    18.963]     compiled for 1.15.1, module version = 2.99.910
[    18.963]     Module class: X.Org Video Driver
[    18.963]     ABI class: X.Org Video Driver, version 15.0
[    18.963] (II) LoadModule: "modesetting"
[    18.963] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    18.963] (II) Module modesetting: vendor="X.Org Foundation"
[    18.963]     compiled for 1.15.0, module version = 0.8.1
[    18.963]     Module class: X.Org Video Driver
[    18.963]     ABI class: X.Org Video Driver, version 15.0
[    18.963] (II) LoadModule: "fbdev"
[    18.963] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.963] (II) Module fbdev: vendor="X.Org Foundation"
[    18.963]     compiled for 1.15.0, module version = 0.4.4
[    18.963]     Module class: X.Org Video Driver
[    18.963]     ABI class: X.Org Video Driver, version 15.0
[    18.963] (II) LoadModule: "vesa"
[    18.964] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.964] (II) Module vesa: vendor="X.Org Foundation"
[    18.964]     compiled for 1.15.0, module version = 2.3.3
[    18.964]     Module class: X.Org Video Driver
[    18.964]     ABI class: X.Org Video Driver, version 15.0
[    18.964] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    18.964] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    18.964] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    18.964] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    18.964] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    18.964] (II) FBDEV: driver for framebuffer: fbdev
[    18.964] (II) VESA: driver for VESA chipsets: vesa
[    18.964] (--) using VT number 7


[    18.972] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1.6 (Timo Aaltonen <tjaalton@debian.org>)
[    18.973] (WW) Falling back to old probe method for modesetting
[    18.974] (WW) Falling back to old probe method for fbdev
[    18.974] (II) Loading sub module "fbdevhw"
[    18.974] (II) LoadModule: "fbdevhw"
[    18.974] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    18.974] (II) Module fbdevhw: vendor="X.Org Foundation"
[    18.974]     compiled for 1.15.1, module version = 0.0.2
[    18.974]     ABI class: X.Org Video Driver, version 15.0
[    18.974] (WW) Falling back to old probe method for vesa
[    18.975] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD graphics
[    18.975] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2
[    18.975] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    18.975] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    18.975] (==) intel(0): RGB weight 888
[    18.975] (==) intel(0): Default visual is TrueColor
[    18.975] (**) intel(0): Framebuffer tiled
[    18.975] (**) intel(0): Pixmaps tiled
[    18.975] (**) intel(0): "Tear free" disabled
[    18.975] (**) intel(0): Forcing per-crtc-pixmaps? no
[    18.975] (II) intel(0): Output HDMI1 has no monitor section
[    18.975] (II) intel(0): Output DP1 has no monitor section
[    18.975] (II) intel(0): Output HDMI2 has no monitor section
[    18.975] (II) intel(0): Output VIRTUAL1 has no monitor section
[    18.975] (--) intel(0): Output HDMI1 using initial mode 1920x1080 on pipe 0
[    18.975] (==) intel(0): DPI set to (96, 96)
[    18.976] (II) Loading sub module "dri2"
[    18.976] (II) LoadModule: "dri2"
[    18.976] (II) Module "dri2" already built-in
[    18.976] (II) UnloadModule: "modesetting"
[    18.976] (II) Unloading modesetting
[    18.976] (II) UnloadModule: "fbdev"
[    18.976] (II) Unloading fbdev
[    18.976] (II) UnloadSubModule: "fbdevhw"
[    18.976] (II) Unloading fbdevhw
[    18.976] (II) UnloadModule: "vesa"
[    18.976] (II) Unloading vesa
[    18.976] (==) Depth 24 pixmap format is 32 bpp
[    18.978] (II) intel(0): SNA initialized with Broadwell backend
[    18.978] (==) intel(0): Backing store enabled
[    18.978] (==) intel(0): Silken mouse enabled
[    18.978] (II) intel(0): HW Cursor enabled
[    18.978] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.979] (==) intel(0): DPMS enabled
[    18.979] (II) intel(0): [DRI2] Setup complete
[    18.979] (II) intel(0): [DRI2]   DRI driver: i965
[    18.979] (II) intel(0): [DRI2]   VDPAU driver: i965
[    18.979] (II) intel(0): direct rendering: DRI2 Enabled
[    18.979] (==) intel(0): hotplug detection: "enabled"
[    18.979] (--) RandR disabled
[    18.986] (II) SELinux: Disabled on system
[    19.000] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    19.000] (II) AIGLX: enabled GLX_ARB_create_context
[    19.000] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    19.000] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    19.000] (II) AIGLX: enabled GLX_INTEL_swap_event
[    19.000] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    19.000] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    19.000] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    19.000] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    19.000] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    19.000] (II) AIGLX: Loaded and initialized i965
[    19.000] (II) GLX: Initialized DRI2 GL provider for screen 0
[    19.004] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using pipe 0, position (0, 0), rotation normal, reflection none
[    19.024] (II) intel(0): Setting screen physical size to 508 x 285
[    19.036] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.066] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    19.066] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.066] (II) LoadModule: "evdev"
[    19.066] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.067] (II) Module evdev: vendor="X.Org Foundation"
[    19.067]     compiled for 1.15.0, module version = 2.8.2
[    19.067]     Module class: X.Org XInput Driver
[    19.067]     ABI class: X.Org XInput driver, version 20.0
[    19.067] (II) Using input driver 'evdev' for 'Power Button'
[    19.067] (**) Power Button: always reports core events
[    19.067] (**) evdev: Power Button: Device: "/dev/input/event2"
[    19.067] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.067] (--) evdev: Power Button: Found keys
[    19.067] (II) evdev: Power Button: Configuring as keyboard
[    19.067] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    19.067] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    19.067] (**) Option "xkb_rules" "evdev"
[    19.067] (**) Option "xkb_model" "pc105"
[    19.068] (**) Option "xkb_layout" "us"
[    19.068] (**) Option "xkb_variant" "intl"
[    19.071] (II) XKB: generating xkmfile /tmp/server-A5431D4A34463C892C9E905E2E421B30A3CC30DD.xkm
[    19.092] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    19.092] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    19.092] (II) Using input driver 'evdev' for 'Video Bus'
[    19.092] (**) Video Bus: always reports core events
[    19.092] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    19.092] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    19.092] (--) evdev: Video Bus: Found keys
[    19.092] (II) evdev: Video Bus: Configuring as keyboard
[    19.092] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[    19.092] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    19.092] (**) Option "xkb_rules" "evdev"
[    19.092] (**) Option "xkb_model" "pc105"
[    19.092] (**) Option "xkb_layout" "us"
[    19.092] (**) Option "xkb_variant" "intl"
[    19.092] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    19.092] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.092] (II) Using input driver 'evdev' for 'Power Button'
[    19.092] (**) Power Button: always reports core events
[    19.092] (**) evdev: Power Button: Device: "/dev/input/event1"
[    19.092] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.093] (--) evdev: Power Button: Found keys
[    19.093] (II) evdev: Power Button: Configuring as keyboard
[    19.093] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    19.093] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    19.093] (**) Option "xkb_rules" "evdev"
[    19.093] (**) Option "xkb_model" "pc105"
[    19.093] (**) Option "xkb_layout" "us"
[    19.093] (**) Option "xkb_variant" "intl"
[    19.093] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    19.093] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    19.093] (II) Using input driver 'evdev' for 'Sleep Button'
[    19.093] (**) Sleep Button: always reports core events
[    19.093] (**) evdev: Sleep Button: Device: "/dev/input/event0"
[    19.093] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    19.093] (--) evdev: Sleep Button: Found keys
[    19.093] (II) evdev: Sleep Button: Configuring as keyboard
[    19.093] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"
[    19.093] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    19.093] (**) Option "xkb_rules" "evdev"
[    19.093] (**) Option "xkb_model" "pc105"
[    19.093] (**) Option "xkb_layout" "us"
[    19.093] (**) Option "xkb_variant" "intl"
[    19.093] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    19.093] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    19.094] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event6)
[    19.094] (II) No input driver specified, ignoring this device.
[    19.094] (II) This device may have been added with another device file.
[    19.094] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event7)
[    19.094] (II) No input driver specified, ignoring this device.
[    19.094] (II) This device may have been added with another device file.
[    19.094] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event8)
[    19.094] (II) No input driver specified, ignoring this device.
[    19.094] (II) This device may have been added with another device file.
[    19.094] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event3)
[    19.094] (II) No input driver specified, ignoring this device.
[    19.094] (II) This device may have been added with another device file.
[    19.095] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event4)
[    19.095] (II) No input driver specified, ignoring this device.
[    19.095] (II) This device may have been added with another device file.
[    19.320] (II) intel(0): EDID vendor "DEL", prod id 16498
[    19.320] (II) intel(0): Using EDID range info for horizontal sync
[    19.320] (II) intel(0): Using EDID range info for vertical refresh
[    19.320] (II) intel(0): Printing DDC gathered Modelines:
[    19.320] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    19.320] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    19.320] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    19.320] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    19.320] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    19.320] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    19.320] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    19.320] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    19.320] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    19.320] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    19.320] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    19.320] (II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)



```

kern.log

```
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Initializing cgroup subsys cpusetOct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Initializing cgroup subsys cpuacct
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Linux version 4.1.6-040106-generic (kernel@gomeisa) (gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04) ) #201508170230 SMP Mon Aug 17 06:32:14 UTC 2015
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.1.6-040106-generic root=UUID=c456624b-f6c2-4dc7-bf92-640922e83f77 ro quiet splash vt.handoff=7
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] KERNEL supported cpus:
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   Intel GenuineIntel
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   AMD AuthenticAMD
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   Centaur CentaurHauls
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009efff] usable
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000d1f50fff] usable
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d1f51000-0x00000000d2230fff] reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d2231000-0x00000000d62ecfff] usable
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d62ed000-0x00000000d6332fff] reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d6333000-0x00000000d6521fff] usable
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d6522000-0x00000000d6ca0fff] ACPI NVS
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d6ca1000-0x00000000d6f8afff] reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d6f8b000-0x00000000d6ffdfff] type 20
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d6ffe000-0x00000000d6ffefff] usable
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7800000-0x00000000dfffffff] reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011effffff] usable
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] NX (Execute Disable) protection: active
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] efi: EFI v2.40 by American Megatrends
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] efi:  ACPI=0xd6c66000  ACPI 2.0=0xd6c66000  SMBIOS=0xf05b0  MPS=0xfd640 
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] SMBIOS 2.8 present.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] DMI: GIGABYTE GB-BXCE-3205/MQLPCAP-00, BIOS F3 02/25/2015
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] AGP: No AGP bridge found
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] e820: last_pfn = 0x11f000 max_arch_pfn = 0x400000000
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] MTRR default type: uncachable
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] MTRR fixed ranges enabled:
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   00000-9FFFF write-back
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   A0000-BFFFF uncachable
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   C0000-FFFFF write-protect
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] MTRR variable ranges enabled:
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   0 base 0000000000 mask 7F80000000 write-back
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   1 base 0080000000 mask 7FC0000000 write-back
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   2 base 00C0000000 mask 7FF0000000 write-back
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   3 base 00D0000000 mask 7FFC000000 write-back
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   4 base 00D4000000 mask 7FFE000000 write-back
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   5 base 00D6000000 mask 7FFF000000 write-back
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   6 base 0100000000 mask 7FE0000000 write-back
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   7 base 011F000000 mask 7FFF000000 uncachable
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   8 disabled
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   9 disabled
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] original variable MTRRs
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] reg 2, base: 3GB, range: 256MB, type WB
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] reg 3, base: 3328MB, range: 64MB, type WB
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] reg 4, base: 3392MB, range: 32MB, type WB
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] reg 5, base: 3424MB, range: 16MB, type WB
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] reg 6, base: 4GB, range: 512MB, type WB
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] reg 7, base: 4592MB, range: 16MB, type UC
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] total RAM covered: 3936M
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Found optimal setting for mtrr clean up
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 7      lose cover RAM: 0G
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] New variable MTRRs
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] reg 2, base: 3GB, range: 256MB, type WB
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] reg 3, base: 3328MB, range: 128MB, type WB
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] reg 4, base: 3440MB, range: 16MB, type UC
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] reg 5, base: 4GB, range: 512MB, type WB
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] reg 6, base: 4592MB, range: 16MB, type UC
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] e820: update [mem 0xd7000000-0xffffffff] usable ==> reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] e820: last_pfn = 0xd6fff max_arch_pfn = 0x400000000
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] found SMP MP-table at [mem 0x000fd840-0x000fd84f] mapped at [ffff8800000fd840]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Using GB pages for direct mapping
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BRK [0x02fe9000, 0x02fe9fff] PGTABLE
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BRK [0x02fea000, 0x02feafff] PGTABLE
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BRK [0x02feb000, 0x02febfff] PGTABLE
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] init_memory_mapping: [mem 0x11ee00000-0x11effffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]  [mem 0x11ee00000-0x11effffff] page 2M
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BRK [0x02fec000, 0x02fecfff] PGTABLE
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x11edfffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]  [mem 0x100000000-0x11edfffff] page 2M
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] init_memory_mapping: [mem 0xc0000000-0xd1f50fff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]  [mem 0xc0000000-0xd1dfffff] page 2M
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]  [mem 0xd1e00000-0xd1f50fff] page 4k
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BRK [0x02fed000, 0x02fedfff] PGTABLE
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] BRK [0x02fee000, 0x02feefff] PGTABLE
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] init_memory_mapping: [mem 0xd2231000-0xd62ecfff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]  [mem 0xd2231000-0xd23fffff] page 4k
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]  [mem 0xd2400000-0xd61fffff] page 2M
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]  [mem 0xd6200000-0xd62ecfff] page 4k
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] init_memory_mapping: [mem 0xd6333000-0xd6521fff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]  [mem 0xd6333000-0xd6521fff] page 4k
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] init_memory_mapping: [mem 0xd6ffe000-0xd6ffefff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]  [mem 0xd6ffe000-0xd6ffefff] page 4k
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xbfffffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] RAMDISK: [mem 0x35b68000-0x36dabfff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: Early table checksum verification disabled
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: RSDP 0x00000000D6C66000 000024 (v02 ALASKA)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: XSDT 0x00000000D6C66098 0000AC (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: FACP 0x00000000D6C7A748 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: DSDT 0x00000000D6C661D8 014569 (v02 ALASKA A M I    01072009 INTL 20120913)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: FACS 0x00000000D6C9FF80 000040
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: APIC 0x00000000D6C7A858 000068 (v03 ALASKA A M I    01072009 AMI  00010013)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: FPDT 0x00000000D6C7A8C0 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: FIDT 0x00000000D6C7A908 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: MCFG 0x00000000D6C7A9A8 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: HPET 0x00000000D6C7A9E8 000038 (v01 ALASKA A M I    01072009 AMI. 00000005)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: SSDT 0x00000000D6C7AA20 000315 (v01 SataRe SataTabl 00001000 INTL 20120913)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: UEFI 0x00000000D6C7AD38 000042 (v01                 00000000      00000000)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: SSDT 0x00000000D6C7AD80 000C7D (v02 Ther_R Ther_Rvp 00001000 INTL 20120913)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: ASF! 0x00000000D6C7BA00 0000A0 (v32 INTEL   HCG     00000001 TFSM 000F4240)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: SSDT 0x00000000D6C7BAA0 0004B5 (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: SSDT 0x00000000D6C7BF58 000B74 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: TPM2 0x00000000D6C7CAD0 000034 (v03        Tpm2Tabl 00000001 AMI  00000000)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: SSDT 0x00000000D6C7CB08 000041 (v01 Ssdt   PttSsdt  00001000 INTL 20120913)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: SSDT 0x00000000D6C7CB50 005CF6 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: DMAR 0x00000000D6C82848 0000B0 (v01 INTEL  BDW      00000001 INTL 00000001)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: BGRT 0x00000000D6C828F8 000038 (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] No NUMA configuration found
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011effffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x11eff7000-0x11effbfff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011a800000-ffff88011e5fffff] on node 0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Zone ranges:
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   Normal   [mem 0x0000000100000000-0x000000011effffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Movable zone start for each node
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Early memory node ranges
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000057fff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   node   0: [mem 0x0000000000059000-0x000000000009efff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   node   0: [mem 0x0000000000100000-0x00000000d1f50fff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   node   0: [mem 0x00000000d2231000-0x00000000d62ecfff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   node   0: [mem 0x00000000d6333000-0x00000000d6521fff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   node   0: [mem 0x00000000d6ffe000-0x00000000d6ffefff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   node   0: [mem 0x0000000100000000-0x000000011effffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000011effffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] On node 0 totalpages: 1003930
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   DMA zone: 25 pages reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   DMA zone: 3997 pages, LIFO batch:0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   DMA32 zone: 13640 pages used for memmap
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   DMA32 zone: 872957 pages, LIFO batch:31
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   Normal zone: 1984 pages used for memmap
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]   Normal zone: 126976 pages, LIFO batch:31
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Reserving Intel graphics stolen memory at 0xd8000000-0xdfffffff
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1808
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0xa4])
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl edge lint[0x0])
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd1f51000-0xd2230fff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd62ed000-0xd6332fff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd6522000-0xd6ca0fff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd6ca1000-0xd6f8afff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd6f8b000-0xd6ffdfff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd6fff000-0xd77fffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7800000-0xdfffffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xf7ffffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] e820: [mem 0xe0000000-0xf7ffffff] available for PCI devices
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] clocksource refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PERCPU: Embedded 34 pages/cpu @ffff88011ec00000 s100376 r8192 d30696 u1048576
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] pcpu-alloc: s100376 r8192 d30696 u1048576 alloc=1*2097152
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 988217
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Policy zone: Normal
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.1.6-040106-generic root=UUID=c456624b-f6c2-4dc7-bf92-640922e83f77 ro quiet splash vt.handoff=7
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240 using standard form
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] AGP: Checking aperture...
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] AGP: No AGP bridge found
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Memory: 3793632K/4015720K available (8056K kernel code, 1243K rwdata, 3780K rodata, 1424K init, 1292K bss, 222088K reserved, 0K cma-reserved)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Hierarchical RCU implementation.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=2
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] NR_IRQS:16640 nr_irqs:512 16
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-1.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] Console: colour dummy device 80x25
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] console [tty0] enabled
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] clocksource hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] hpet clockevent registered
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000000] tsc: Detected 1496.622 MHz processor
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000043] Calibrating delay loop (skipped), value calculated using timer frequency.. 2993.24 BogoMIPS (lpj=5986488)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000046] pid_max: default: 32768 minimum: 301
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.000053] ACPI: Core revision 20150410
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.026485] ACPI: All ACPI Tables successfully acquired
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.027393] Security Framework initialized
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.027407] AppArmor: AppArmor initialized
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.027408] Yama: becoming mindful.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.027831] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.029049] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.029592] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.029602] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.029863] Initializing cgroup subsys blkio
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.029867] Initializing cgroup subsys memory
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.029878] Initializing cgroup subsys devices
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.029881] Initializing cgroup subsys freezer
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.029884] Initializing cgroup subsys net_cls
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.029886] Initializing cgroup subsys perf_event
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.029889] Initializing cgroup subsys net_prio
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.029891] Initializing cgroup subsys hugetlb
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.029926] CPU: Physical Processor ID: 0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.029927] CPU: Processor Core ID: 0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.029933] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.029934] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.031251] mce: CPU supports 7 MCE banks
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.031268] CPU0: Thermal monitoring enabled (TM1)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.031281] process: using mwait in idle threads
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.031285] Last level iTLB entries: 4KB 128, 2MB 8, 4MB 8
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.031287] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.031490] Freeing SMP alternatives memory: 32K (ffffffff81e9c000 - ffffffff81ea4000)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.035839] ftrace: allocating 30366 entries in 119 pages
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.054436] dmar: Host address width 39
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.054440] dmar: DRHD base: 0x000000fed90000 flags: 0x0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.054453] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e1ff0505e
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.054455] dmar: DRHD base: 0x000000fed91000 flags: 0x1
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.054462] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.054464] dmar: RMRR base: 0x000000d6ee3000 end: 0x000000d6ef1fff
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.054466] dmar: RMRR base: 0x000000d7800000 end: 0x000000dfffffff
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.054469] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.054471] HPET id 0 under DRHD base 0xfed91000
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.054909] x2apic is disabled because BIOS sets x2apic opt out bit. You can use 'intremap=no_x2apic_optout' to override the BIOS setting.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.054924] Enabled IRQ remapping in xapic mode
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.054926] x2apic: IRQ remapping doesn't support X2APIC mode
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.055593] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.095270] TSC deadline timer enabled
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.095275] smpboot: CPU0: Intel(R) Celeron(R) 3205U @ 1.50GHz (fam: 06, model: 3d, stepping: 04)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.095312] Performance Events: PEBS fmt2+, 16-deep LBR, Broadwell events, full-width counters, Intel PMU driver.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.095341] ... version:                3
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.095342] ... bit width:              48
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.095343] ... generic registers:      8
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.095344] ... value mask:             0000ffffffffffff
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.095346] ... max period:             0000ffffffffffff
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.095347] ... fixed-purpose events:   3
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.095348] ... event mask:             00000007000000ff
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.096518] x86: Booting SMP configuration:
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.096521] .... node  #0, CPUs:      #1
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.111068] x86: Booted up 1 node, 2 CPUs
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.111071] smpboot: Total of 2 processors activated (5986.48 BogoMIPS)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.111111] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.113140] devtmpfs: initialized
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.116295] evm: security.selinux
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.116297] evm: security.SMACK64
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.116299] evm: security.SMACK64EXEC
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.116300] evm: security.SMACK64TRANSMUTE
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.116301] evm: security.SMACK64MMAP
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.116302] evm: security.ima
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.116303] evm: security.capability
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.116382] PM: Registering ACPI NVS region [mem 0xd6522000-0xd6ca0fff] (7860224 bytes)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.116602] clocksource jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.116692] pinctrl core: initialized pinctrl subsystem
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.116825] RTC time: 14:45:17, date: 10/15/15
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.116980] NET: Registered protocol family 16
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.123103] cpuidle: using governor ladder
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.127105] cpuidle: using governor menu
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.127181] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.127185] ACPI: bus type PCI registered
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.127187] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.127276] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.127279] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.127399] PCI: Using configuration type 1 for base access
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.131578] ACPI: Added _OSI(Module Device)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.131581] ACPI: Added _OSI(Processor Device)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.131583] ACPI: Added _OSI(3.0 _SCP Extensions)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.131585] ACPI: Added _OSI(Processor Aggregator Device)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.139768] ACPI: Executed 18 blocks of module-level executable AML code
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.146357] ACPI: Dynamic OEM Table Load:
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.146367] ACPI: SSDT 0xFFFF880119490C00 0003D3 (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.147655] ACPI: Dynamic OEM Table Load:
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.147662] ACPI: SSDT 0xFFFF88011A417800 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.149018] ACPI: Dynamic OEM Table Load:
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.149023] ACPI: SSDT 0xFFFF88011943F600 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.150764] ACPI: Interpreter enabled
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.150775] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150410/hwxface-580)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.150784] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150410/hwxface-580)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.150804] ACPI: (supports S0 S3 S4 S5)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.150806] ACPI: Using IOAPIC for interrupt routing
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.150849] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.153606] ACPI: Power Resource [PG00] (on)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.154116] ACPI: Power Resource [PG01] (on)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.154606] ACPI: Power Resource [PG02] (on)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.167472] ACPI: Power Resource [FN00] (off)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.167576] ACPI: Power Resource [FN01] (off)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.167675] ACPI: Power Resource [FN02] (off)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.167772] ACPI: Power Resource [FN03] (off)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.167870] ACPI: Power Resource [FN04] (off)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.169307] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.169315] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.170050] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.170052] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.170671] PCI host bridge to bus 0000:00
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.170675] pci_bus 0000:00: root bus resource [bus 00-3e]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.170678] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.170680] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.170683] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.170685] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfeafffff window]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.170695] pci 0000:00:00.0: [8086:1604] type 00 class 0x060000
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.170820] pci 0000:00:02.0: [8086:1606] type 00 class 0x030000
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.170834] pci 0000:00:02.0: reg 0x10: [mem 0xf6000000-0xf6ffffff 64bit]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.170843] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.170850] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.170968] pci 0000:00:03.0: [8086:160c] type 00 class 0x040300
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.170978] pci 0000:00:03.0: reg 0x10: [mem 0xf7214000-0xf7217fff 64bit]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.171116] pci 0000:00:14.0: [8086:9cb1] type 00 class 0x0c0330
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.171135] pci 0000:00:14.0: reg 0x10: [mem 0xf7200000-0xf720ffff 64bit]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.171199] pci 0000:00:14.0: PME# supported from D3hot D3cold
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.171266] pci 0000:00:14.0: System wakeup disabled by ACPI
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.171316] pci 0000:00:16.0: [8086:9cba] type 00 class 0x078000
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.171335] pci 0000:00:16.0: reg 0x10: [mem 0xf721c000-0xf721c01f 64bit]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.171401] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.171530] pci 0000:00:1b.0: [8086:9ca0] type 00 class 0x040300
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.171547] pci 0000:00:1b.0: reg 0x10: [mem 0xf7210000-0xf7213fff 64bit]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.171600] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.171679] pci 0000:00:1b.0: System wakeup disabled by ACPI
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.171726] pci 0000:00:1c.0: [8086:9c90] type 01 class 0x060400
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.171792] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.171891] pci 0000:00:1c.0: System wakeup disabled by ACPI
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.171940] pci 0000:00:1c.2: [8086:9c94] type 01 class 0x060400
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172007] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172101] pci 0000:00:1c.2: System wakeup disabled by ACPI
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172148] pci 0000:00:1c.3: [8086:9c96] type 01 class 0x060400
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172216] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172309] pci 0000:00:1c.3: System wakeup disabled by ACPI
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172362] pci 0000:00:1d.0: [8086:9ca6] type 00 class 0x0c0320
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172382] pci 0000:00:1d.0: reg 0x10: [mem 0xf721a000-0xf721a3ff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172471] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172537] pci 0000:00:1d.0: System wakeup disabled by ACPI
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172588] pci 0000:00:1f.0: [8086:9cc5] type 00 class 0x060100
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172793] pci 0000:00:1f.2: [8086:9c83] type 00 class 0x010601
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172808] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172816] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172825] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172833] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172841] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172849] pci 0000:00:1f.2: reg 0x24: [mem 0xf7219000-0xf72197ff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172886] pci 0000:00:1f.2: PME# supported from D3hot
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172977] pci 0000:00:1f.3: [8086:9ca2] type 00 class 0x0c0500
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.172998] pci 0000:00:1f.3: reg 0x10: [mem 0xf7218000-0xf72180ff 64bit]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.173020] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.173205] acpiphp: Slot [1] registered
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.173212] pci 0000:00:1c.0: PCI bridge to [bus 01]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.173306] pci 0000:02:00.0: [8086:08b3] type 00 class 0x028000
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.173343] pci 0000:02:00.0: reg 0x10: [mem 0xf7100000-0xf7101fff 64bit]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.173500] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.173560] pci 0000:02:00.0: System wakeup disabled by ACPI
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.181049] pci 0000:00:1c.2: PCI bridge to [bus 02]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.181055] pci 0000:00:1c.2:   bridge window [mem 0xf7100000-0xf71fffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.181145] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.181167] pci 0000:03:00.0: reg 0x10: [io  0xe000-0xe0ff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.181198] pci 0000:03:00.0: reg 0x18: [mem 0xf7000000-0xf7000fff 64bit]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.181218] pci 0000:03:00.0: reg 0x20: [mem 0xf0000000-0xf0003fff 64bit pref]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.181306] pci 0000:03:00.0: supports D1 D2
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.181308] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.181362] pci 0000:03:00.0: System wakeup disabled by ACPI
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.189060] pci 0000:00:1c.3: PCI bridge to [bus 03]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.189064] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.189068] pci 0000:00:1c.3:   bridge window [mem 0xf7000000-0xf70fffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.189074] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.190093] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.190158] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.190219] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.190277] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.190334] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.190393] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.190453] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.190515] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 10 11 12 14 15)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.191048] ACPI: Enabled 4 GPEs in block 00 to 7F
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.191206] vgaarb: setting as boot device: PCI:0000:00:02.0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.191209] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.191213] vgaarb: loaded
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.191215] vgaarb: bridge control possible 0000:00:02.0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.191495] SCSI subsystem initialized
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.191567] libata version 3.00 loaded.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.191599] ACPI: bus type USB registered
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.191622] usbcore: registered new interface driver usbfs
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.191633] usbcore: registered new interface driver hub
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.191646] usbcore: registered new device driver usb
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.191876] PCI: Using ACPI for IRQ routing
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.193407] PCI: pci_cache_line_size set to 64 bytes
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.193455] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.193457] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.193459] e820: reserve RAM buffer [mem 0xd1f51000-0xd3ffffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.193460] e820: reserve RAM buffer [mem 0xd62ed000-0xd7ffffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.193463] e820: reserve RAM buffer [mem 0xd6522000-0xd7ffffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.193465] e820: reserve RAM buffer [mem 0xd6fff000-0xd7ffffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.193467] e820: reserve RAM buffer [mem 0x11f000000-0x11fffffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.193627] NetLabel: Initializing
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.193629] NetLabel:  domain hash size = 128
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.193630] NetLabel:  protocols = UNLABELED CIPSOv4
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.193645] NetLabel:  unlabeled traffic allowed by default
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.193728] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.193735] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.195777] Switched to clocksource hpet
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.203683] AppArmor: AppArmor Filesystem Enabled
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.203787] pnp: PnP ACPI init
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204090] system 00:00: [io  0x0a00-0x0a2f] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204093] system 00:00: [io  0x0a30-0x0a3f] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204095] system 00:00: [io  0x0a40-0x0a4f] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204100] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204212] system 00:01: [io  0x0680-0x069f] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204215] system 00:01: [io  0xffff] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204217] system 00:01: [io  0xffff] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204219] system 00:01: [io  0xffff] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204222] system 00:01: [io  0x1800-0x18fe] could not be reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204224] system 00:01: [io  0x164e-0x164f] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204227] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204294] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204346] system 00:03: [io  0x1854-0x1857] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204349] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204572] system 00:04: [mem 0xfed1c000-0xfed1ffff] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204574] system 00:04: [mem 0xfed10000-0xfed17fff] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204576] system 00:04: [mem 0xfed18000-0xfed18fff] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204579] system 00:04: [mem 0xfed19000-0xfed19fff] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204581] system 00:04: [mem 0xf8000000-0xfbffffff] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204584] system 00:04: [mem 0xfed20000-0xfed3ffff] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204586] system 00:04: [mem 0xfed90000-0xfed93fff] could not be reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204589] system 00:04: [mem 0xfed45000-0xfed8ffff] could not be reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204591] system 00:04: [mem 0xff000000-0xffffffff] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204594] system 00:04: [mem 0xfee00000-0xfeefffff] could not be reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204596] system 00:04: [mem 0xf7fe0000-0xf7feffff] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204598] system 00:04: [mem 0xf7ff0000-0xf7ffffff] has been reserved
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.204601] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.205175] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.205710] pnp: PnP ACPI: found 6 devices
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212373] clocksource acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212404] pci 0000:00:1c.0: PCI bridge to [bus 01]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212417] pci 0000:00:1c.2: PCI bridge to [bus 02]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212422] pci 0000:00:1c.2:   bridge window [mem 0xf7100000-0xf71fffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212430] pci 0000:00:1c.3: PCI bridge to [bus 03]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212433] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212438] pci 0000:00:1c.3:   bridge window [mem 0xf7000000-0xf70fffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212443] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212450] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212452] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212455] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212457] pci_bus 0000:00: resource 7 [mem 0xe0000000-0xfeafffff window]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212460] pci_bus 0000:02: resource 1 [mem 0xf7100000-0xf71fffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212462] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212464] pci_bus 0000:03: resource 1 [mem 0xf7000000-0xf70fffff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212466] pci_bus 0000:03: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212506] NET: Registered protocol family 2
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212709] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212806] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212889] TCP: Hash tables configured (established 32768 bind 32768)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212924] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.212945] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.213001] NET: Registered protocol family 1
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.213022] pci 0000:00:02.0: Video device with shadowed ROM
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.231906] PCI: CLS 64 bytes, default 64
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.231974] Trying to unpack rootfs image as initramfs...
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.682141] Freeing initrd memory: 18704K (ffff880035b68000 - ffff880036dac000)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.682187] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.682191] software IO TLB [mem 0xca247000-0xce247000] (64MB) mapped at [ffff8800ca247000-ffff8800ce246fff]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.682279] RAPL PMU detected, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.682281] hw unit of domain pp0-core 2^-14 Joules
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.682282] hw unit of domain package 2^-14 Joules
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.682283] hw unit of domain dram 2^-14 Joules
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.682284] hw unit of domain pp1-gpu 2^-14 Joules
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.682376] microcode: CPU0 sig=0x306d4, pf=0x40, revision=0x11
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.682384] microcode: CPU1 sig=0x306d4, pf=0x40, revision=0x11
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.682449] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.682489] Scanning for low memory corruption every 60 seconds
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.682886] futex hash table entries: 512 (order: 3, 32768 bytes)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.682903] Initialise system trusted keyring
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.682926] audit: initializing netlink subsys (disabled)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.682944] audit: type=2000 audit(1444920317.672:1): initialized
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.683433] HugeTLB registered 1 GB page size, pre-allocated 0 pages
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.683435] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.685547] zpool: loaded
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.685550] zbud: loaded
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.685760] VFS: Disk quotas dquot_6.6.0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.685807] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.686413] fuse init (API version 7.23)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.686591] Key type big_key registered
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.686953] Key type asymmetric registered
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.686957] Asymmetric key parser 'x509' registered
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687006] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 251)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687042] io scheduler noop registered
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687047] io scheduler deadline registered (default)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687089] io scheduler cfq registered
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687819] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687824] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687840] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687842] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687846] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687863] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687864] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687868] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687878] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687899] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687952] efifb: probing for efifb
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687984] efifb: framebuffer at 0xe0000000, mapped to 0xffffc90000800000, using 8128k, total 8128k
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687986] efifb: mode is 1920x1080x32, linelength=7680, pages=1
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687987] efifb: scrolling: redraw
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.687989] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.695250] Console: switching to colour frame buffer device 240x67
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.702428] fb0: EFI VGA frame buffer device
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.702444] intel_idle: MWAIT substates: 0x11142120
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.702446] intel_idle: v0.4 model 0x3D
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.702447] intel_idle: lapic_timer_reliable_states 0xffffffff
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.702704] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.702709] ACPI: Sleep Button [SLPB]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.702755] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.702758] ACPI: Power Button [PWRB]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.702805] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.702807] ACPI: Power Button [PWRF]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.703722] thermal LNXTHERM:00: registered as thermal_zone0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.703724] ACPI: Thermal Zone [TZ00] (28 C)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.703970] thermal LNXTHERM:01: registered as thermal_zone1
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.703972] ACPI: Thermal Zone [TZ01] (30 C)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.704078] GHES: HEST is not enabled!
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.704227] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.706233] Linux agpgart interface v0.103
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.708822] brd: module loaded
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.709828] loop: module loaded
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.710087] libphy: Fixed MDIO Bus: probed
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.710092] tun: Universal TUN/TAP device driver, 1.6
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.710093] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.710149] PPP generic driver version 2.4.2
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.710399] xhci_hcd 0000:00:14.0: xHCI Host Controller
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.710406] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.710491] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00009810
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.710497] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.710582] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.710584] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.710586] usb usb1: Product: xHCI Host Controller
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.710588] usb usb1: Manufacturer: Linux 4.1.6-040106-generic xhci-hcd
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.710590] usb usb1: SerialNumber: 0000:00:14.0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.710720] hub 1-0:1.0: USB hub found
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.710733] hub 1-0:1.0: 11 ports detected
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.712538] xhci_hcd 0000:00:14.0: xHCI Host Controller
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.712543] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.712579] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.712581] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.712583] usb usb2: Product: xHCI Host Controller
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.712585] usb usb2: Manufacturer: Linux 4.1.6-040106-generic xhci-hcd
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.712587] usb usb2: SerialNumber: 0000:00:14.0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.712731] hub 2-0:1.0: USB hub found
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.712740] hub 2-0:1.0: 4 ports detected
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.713348] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.713356] ehci-pci: EHCI PCI platform driver
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.713496] ehci-pci 0000:00:1d.0: EHCI Host Controller
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.713502] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 3
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.713514] ehci-pci 0000:00:1d.0: debug port 2
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.717430] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.717445] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf721a000
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.731611] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.731685] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.731687] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.731690] usb usb3: Product: EHCI Host Controller
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.731692] usb usb3: Manufacturer: Linux 4.1.6-040106-generic ehci_hcd
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.731694] usb usb3: SerialNumber: 0000:00:1d.0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.731959] hub 3-0:1.0: USB hub found
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.731967] hub 3-0:1.0: 2 ports detected
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.732136] ehci-platform: EHCI generic platform driver
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.732154] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.732162] ohci-pci: OHCI PCI platform driver
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.732178] ohci-platform: OHCI generic platform driver
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.732189] uhci_hcd: USB Universal Host Controller Interface driver
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    0.732258] i8042: PNP: No PS/2 controller found. Probing ports directly.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.459360] usb 3-1: new high-speed USB device number 2 using ehci-pci
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.679282] tsc: Refined TSC clocksource calibration: 1496.535 MHz
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.679286] clocksource tsc: mask: 0xffffffffffffffff max_cycles: 0x159259799ff, max_idle_ns: 440795263419 ns
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.765856] i8042: No controller found
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.766090] mousedev: PS/2 mouse device common for all mice
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.766607] rtc_cmos 00:02: RTC can wake from S4
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.766769] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.766801] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.766832] i2c /dev entries driver
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.766904] device-mapper: uevent: version 1.0.3
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.767042] device-mapper: ioctl: 4.31.0-ioctl (2015-3-12) initialised: dm-devel@redhat.com
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.767074] Intel P-state driver initializing.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.767157] ledtrig-cpu: registered to indicate activity on CPUs
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.767164] EFI Variables Facility v0.08 2004-May-17
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.769401] PCCT header not found.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.769662] NET: Registered protocol family 10
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.769904] NET: Registered protocol family 17
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.769923] Key type dns_resolver registered
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.770299] Loading compiled-in X.509 certificates
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.771465] Loaded X.509 cert 'Build time autogenerated kernel key: 355479ea572ba7361fe0c75a06c61f90ae79791e'
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.771485] registered taskstats version 1
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.773703] Key type trusted registered
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.777546] Key type encrypted registered
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.777556] AppArmor: AppArmor sha1 policy hashing enabled
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.777561] ima: No TPM chip found, activating TPM-bypass!
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.777589] evm: HMAC attrs: 0x1
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.778079]   Magic number: 3:871:788
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.778200] rtc_cmos 00:02: setting system clock to 2015-10-15 14:45:19 UTC (1444920319)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.778275] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.778276] EDD information not available.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.778395] PM: Hibernation image not present or could not be loaded.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.778835] Freeing unused kernel memory: 1424K (ffffffff81d38000 - ffffffff81e9c000)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.778838] Write protecting the kernel read-only data: 12288k
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.779074] Freeing unused kernel memory: 124K (ffff8800027e1000 - ffff880002800000)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.779190] Freeing unused kernel memory: 316K (ffff880002bb1000 - ffff880002c00000)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.824582] ahci 0000:00:1f.2: version 3.0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.824792] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x1 impl SATA mode
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.824797] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo only pio slum part deso sadm apst 
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.825332] scsi host0: ahci
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.825486] scsi host1: ahci
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.825548] ata1: SATA max UDMA/133 abar m2048@0xf7219000 port 0xf7219100 irq 46
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.825550] ata2: DUMMY
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.830445] sdhci: Secure Digital Host Controller Interface driver
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.830448] sdhci: Copyright(c) Pierre Ossman
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.847905] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.847916] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.856149] r8169 0000:03:00.0 eth0: RTL8168g/8111g at 0xffffc90000782000, fc:aa:14:f1:f4:7b, XID 0c000800 IRQ 47
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.856156] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.884286] r8169 0000:03:00.0 p3p1: renamed from eth0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.895602] usb 3-1: New USB device found, idVendor=8087, idProduct=8001
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.895606] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.896012] hub 3-1:1.0: USB hub found
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.896081] hub 3-1:1.0: 8 ports detected
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    1.931225] usb 1-7: new full-speed USB device number 2 using xhci_hcd
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.060562] usb 1-7: New USB device found, idVendor=8087, idProduct=07dc
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.060567] usb 1-7: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.143156] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.159320] ata1.00: ATA-8: KINGSTON SMS200S330G, 603ABBF0, max UDMA/133
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.159324] ata1.00: 58626288 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.164451] ata1.00: configured for UDMA/133
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.164703] scsi 0:0:0:0: Direct-Access     ATA      KINGSTON SMS200S BBF0 PQ: 0 ANSI: 5
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.165145] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.165150] sd 0:0:0:0: [sda] 58626288 512-byte logical blocks: (30.0 GB/27.9 GiB)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.165210] sd 0:0:0:0: [sda] Write Protect is off
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.165213] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.165237] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.166272]  sda: sda1 sda2 sda3
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.166681] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.199246] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.268623] random: init urandom read with 19 bits of entropy available
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.441763] Adding 4016124k swap on /dev/sda3.  Priority:-1 extents:1 across:4016124k SSFS
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.446749] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.671200] lp: driver loaded but no devices found
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.689559] Switched to clocksource tsc
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.789285] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.919116] [drm] Initialized drm 1.1.0 20060810
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    2.919837] hidraw: raw HID events driver (C) Jiri Kosina
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.027678] snd_hda_intel 0000:00:03.0: enabling device (0000 -> 0002)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.027845] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.080026] [drm] Memory usable by graphics device = 4096M
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.080032] checking generic (e0000000 7f0000) vs hw (e0000000 10000000)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.080034] fb: switching to inteldrmfb from EFI VGA
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.080084] Console: switching to colour dummy device 80x25
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.083045] [drm] Replacing VGA console driver
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.084761] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC283: line_outs=1 (0x21/0x0/0x0/0x0/0x0) type:hp
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.084766] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.084768] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.084770] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.084772] snd_hda_codec_realtek hdaudioC1D0:    inputs:
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.084774] snd_hda_codec_realtek hdaudioC1D0:      Mic=0x19
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.090851] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.090855] [drm] Driver supports precise vblank timestamp query.
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.090984] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.110124] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.113405] acpi device:10: registered as cooling_device7
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.113539] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input3
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.114187] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.114195] [drm] Initialized i915 1.6.0 20150327 for 0000:00:02.0 on minor 0
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.117061] fbcon: inteldrmfb (fb0) is primary device
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.128795] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input4
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.128944] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input5
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.187759] Console: switching to colour frame buffer device 240x67
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.195337] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.195338] i915 0000:00:02.0: registered panic notifier
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.212840] audit: type=1400 audit(1444920320.931:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=452 comm="apparmor_parser"
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.212848] audit: type=1400 audit(1444920320.931:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=452 comm="apparmor_parser"
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.212852] audit: type=1400 audit(1444920320.931:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=452 comm="apparmor_parser"
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.213311] audit: type=1400 audit(1444920320.931:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=452 comm="apparmor_parser"
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.213319] audit: type=1400 audit(1444920320.931:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=452 comm="apparmor_parser"
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.213541] audit: type=1400 audit(1444920320.931:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=452 comm="apparmor_parser"
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.228489] audit: type=1400 audit(1444920320.947:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=453 comm="apparmor_parser"
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.251431] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.259954] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input6
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.260032] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input7
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.260125] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input8
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.260575] Bluetooth: Core ver 2.20
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.260593] NET: Registered protocol family 31
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.260595] Bluetooth: HCI device and connection manager initialized
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.260599] Bluetooth: HCI socket layer initialized
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.260603] Bluetooth: L2CAP socket layer initialized
Oct 15 16:45:20 hoogstraat-client-1 kernel: [    3.260609] Bluetooth: SCO socket layer initialized
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.323833] usbcore: registered new interface driver btusb
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.339361] r8169 0000:03:00.0 p3p1: link down
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.339418] IPv6: ADDRCONF(NETDEV_UP): p3p1: link is not ready
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.339665] r8169 0000:03:00.0 p3p1: link down
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.348671] Intel(R) Wireless WiFi driver for Linux
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.348675] Copyright(c) 2003- 2015 Intel Corporation
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.348735] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.351513] Bluetooth: hci0: read Intel version: 3707100100012d0d0a
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.351518] Bluetooth: hci0: Intel device is already patched. patch num: 0a
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.363690] iwlwifi 0000:02:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.364900] iwlwifi 0000:02:00.0: Unsupported splx structure
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.419346] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.420621] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.420847] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.441781] intel_rapl: Found RAPL domain package
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.441786] intel_rapl: Found RAPL domain core
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.441788] intel_rapl: Found RAPL domain dram
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.572417] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.816360] audit: type=1400 audit(1444920321.535:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=780 comm="apparmor_parser"
Oct 15 16:45:21 hoogstraat-client-1 kernel: [    3.821565] audit: type=1400 audit(1444920321.539:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=779 comm="apparmor_parser"
Oct 15 16:45:22 hoogstraat-client-1 kernel: [    4.279537] random: nonblocking pool is initialized
Oct 15 16:45:23 hoogstraat-client-1 kernel: [    5.877185] r8169 0000:03:00.0 p3p1: link up
Oct 15 16:45:23 hoogstraat-client-1 kernel: [    5.877198] IPv6: ADDRCONF(NETDEV_CHANGE): p3p1: link becomes ready
Oct 15 16:45:24 hoogstraat-client-1 kernel: [    6.405666] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:45:27 hoogstraat-client-1 kernel: [    9.556468] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:45:30 hoogstraat-client-1 kernel: [   12.707381] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:45:33 hoogstraat-client-1 kernel: [   15.858239] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:45:36 hoogstraat-client-1 kernel: [   19.009096] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:45:39 hoogstraat-client-1 kernel: [   22.161380] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:45:43 hoogstraat-client-1 kernel: [   25.313787] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:45:46 hoogstraat-client-1 kernel: [   28.466188] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:45:49 hoogstraat-client-1 kernel: [   31.618606] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:45:52 hoogstraat-client-1 kernel: [   34.771098] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:45:55 hoogstraat-client-1 kernel: [   37.923506] cfg80211: Exceeded CRDA call max attempts. Not calling CRDA



```

boot.log

```
 * Stopping Send an event to indicate plymouth is up[234G[ OK ] * Starting Mount filesystems on boot[234G[ OK ]
 * Stopping Track if upstart is running in a container[234G[ OK ]
 * Starting Initialize or finalize resolvconf[234G[ OK ]
 * Starting set console keymap[234G[ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted[234G[ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted[234G[ OK ]
 * Starting Bridge udev events into upstart[234G[ OK ]
 * Starting device node and kernel event manager[234G[ OK ]
 * Stopping set console keymap[234G[ OK ]
 * Starting Signal sysvinit that remote filesystems are mounted[234G[ OK ]
 * Starting load modules from /etc/modules[234G[ OK ]
 * Starting cold plug devices[234G[ OK ]
 * Starting log initial device creation[234G[ OK ]
 * Starting Signal sysvinit that the rootfs is mounted[234G[ OK ]
 * Stopping load modules from /etc/modules[234G[ OK ]
 * Starting Clean /tmp directory[234G[ OK ]
 * Stopping Clean /tmp directory[234G[ OK ]
 * Starting Signal sysvinit that local filesystems are mounted[234G[ OK ]
 * Stopping Mount filesystems on boot[234G[ OK ]
 * Starting flush early job output to logs[234G[ OK ]
 * Stopping flush early job output to logs[234G[ OK ]
 * Starting D-Bus system message bus[234G[ OK ]
 * Starting SystemD login management service[234G[ OK ]
 * Starting system logging daemon[234G[ OK ]
 * Starting Uncomplicated firewall[234G[ OK ]
 * Starting configure network device security[234G[ OK ]
 * Starting Bridge file events into upstart[234G[ OK ]
 * Starting Mount network filesystems[234G[ OK ]
 * Stopping Mount network filesystems[234G[ OK ]
 * Starting configure network device[234G[ OK ]
 * Starting configure network device security[234G[ OK ]
 * Starting Mount network filesystems[234G[ OK ]
 * Starting Failsafe Boot Delay[234G[ OK ]
 * Stopping Mount network filesystems[234G[ OK ]
 * Stopping Failsafe Boot Delay[234G[ OK ]
 * Starting System V initialisation compatibility[234G[ OK ]
 * Starting configure network device[234G[ OK ]
 * Starting set console font[234G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Stopping set console font[234G[ OK ]
 * Starting userspace bootsplash[234G[ OK ]
 * Stopping cold plug devices[234G[ OK ]
 * Starting AppArmor profiles       [240G 
[234G[ OK ]
 * Starting Send an event to indicate plymouth is up[234G[ OK ]
 * Stopping log initial device creation[234G[ OK ]
 * Stopping userspace bootsplash[234G[ OK ]




X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
Current Operating System: Linux hoogstraat-client-1 4.1.6-040106-generic #201508170230 SMP Mon Aug 17 06:32:14 UTC 2015 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.1.6-040106-generic root=UUID=c456624b-f6c2-4dc7-bf92-640922e83f77 ro quiet splash vt.handoff=7
Build Date: 12 February 2015  02:49:29PM
xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.30.2
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 15 17:52:47 2015
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
 * Setting up X socket directories...       [240GInitializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension Present
Initializing built-in extension DRI3
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
 
 * Starting configure network device security[234G[ OK ]
[234G[ OK ]
Loading extension GLX
 * Stopping Send an event to indicate plymouth is up[234G[ OK ]
 * Stopping System V initialisation compatibility[234G[ OK ]
 * Starting configure network device security[234G[ OK ]
 * Starting configure network device[234G[ OK ]
 * Starting NTP server ntpd       [240G 
[234G[ OK ]
 * Starting System V runlevel compatibility[234G[ OK ]
 * Starting CPU interrupts balancing daemon[234G[ OK ]
 * Starting deferred execution scheduler[234G[ OK ]
 * Starting OpenSSH server[234G[ OK ]
 * Starting regular background program processing daemon[234G[ OK ]
 * Starting ACPI daemon[234G[ OK ]
 * Starting save kernel messages[234G[ OK ]
 * Starting configure virtual network devices[234G[ OK ]
 * Stopping save kernel messages[234G[ OK ]
 * Restoring resolver state...       [240G 
[234G[ OK ]
 * Stopping Restore Sound Card State[234G[ OK ]
 * Starting automatic crash report generation[234G[ OK ]
 * Starting Bridge socket events into upstart[234G[ OK ]
 * Starting web server lighttpd       [240G 
[234G[ OK ]
(EE) 
Fatal server error:
(EE) no screens found(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.
 * Starting daemon monitor monit       [240G 
[234G[ OK ]
 * Stopping System V runlevel compatibility[234G[ OK ]



```

dmesg

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.1.6-040106-generic (kernel@gomeisa) (gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04) ) #201508170230 SMP Mon Aug 17 06:32:14 UTC 2015
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.1.6-040106-generic root=UUID=c456624b-f6c2-4dc7-bf92-640922e83f77 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000d1f50fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d1f51000-0x00000000d2230fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d2231000-0x00000000d62ecfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d62ed000-0x00000000d6332fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d6333000-0x00000000d6521fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d6522000-0x00000000d6ca0fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000d6ca1000-0x00000000d6f8afff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d6f8b000-0x00000000d6ffdfff] type 20
[    0.000000] BIOS-e820: [mem 0x00000000d6ffe000-0x00000000d6ffefff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d7800000-0x00000000dfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.40 by American Megatrends
[    0.000000] efi:  ACPI=0xd6c66000  ACPI 2.0=0xd6c66000  SMBIOS=0xf05b0  MPS=0xfd640 
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: GIGABYTE GB-BXCE-3205/MQLPCAP-00, BIOS F3 02/25/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x11f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7F80000000 write-back
[    0.000000]   1 base 0080000000 mask 7FC0000000 write-back
[    0.000000]   2 base 00C0000000 mask 7FF0000000 write-back
[    0.000000]   3 base 00D0000000 mask 7FFC000000 write-back
[    0.000000]   4 base 00D4000000 mask 7FFE000000 write-back
[    0.000000]   5 base 00D6000000 mask 7FFF000000 write-back
[    0.000000]   6 base 0100000000 mask 7FE0000000 write-back
[    0.000000]   7 base 011F000000 mask 7FFF000000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3328MB, range: 64MB, type WB
[    0.000000] reg 4, base: 3392MB, range: 32MB, type WB
[    0.000000] reg 5, base: 3424MB, range: 16MB, type WB
[    0.000000] reg 6, base: 4GB, range: 512MB, type WB
[    0.000000] reg 7, base: 4592MB, range: 16MB, type UC
[    0.000000] total RAM covered: 3936M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 7      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3328MB, range: 128MB, type WB
[    0.000000] reg 4, base: 3440MB, range: 16MB, type UC
[    0.000000] reg 5, base: 4GB, range: 512MB, type WB
[    0.000000] reg 6, base: 4592MB, range: 16MB, type UC
[    0.000000] e820: update [mem 0xd7000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xd6fff max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd840-0x000fd84f] mapped at [ffff8800000fd840]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02fe9000, 0x02fe9fff] PGTABLE
[    0.000000] BRK [0x02fea000, 0x02feafff] PGTABLE
[    0.000000] BRK [0x02feb000, 0x02febfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x11ee00000-0x11effffff]
[    0.000000]  [mem 0x11ee00000-0x11effffff] page 2M
[    0.000000] BRK [0x02fec000, 0x02fecfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x100000000-0x11edfffff]
[    0.000000]  [mem 0x100000000-0x11edfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0xc0000000-0xd1f50fff]
[    0.000000]  [mem 0xc0000000-0xd1dfffff] page 2M
[    0.000000]  [mem 0xd1e00000-0xd1f50fff] page 4k
[    0.000000] BRK [0x02fed000, 0x02fedfff] PGTABLE
[    0.000000] BRK [0x02fee000, 0x02feefff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xd2231000-0xd62ecfff]
[    0.000000]  [mem 0xd2231000-0xd23fffff] page 4k
[    0.000000]  [mem 0xd2400000-0xd61fffff] page 2M
[    0.000000]  [mem 0xd6200000-0xd62ecfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xd6333000-0xd6521fff]
[    0.000000]  [mem 0xd6333000-0xd6521fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xd6ffe000-0xd6ffefff]
[    0.000000]  [mem 0xd6ffe000-0xd6ffefff] page 4k
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbfffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35b68000-0x36dabfff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000D6C66000 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0x00000000D6C66098 0000AC (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000D6C7A748 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000D6C661D8 014569 (v02 ALASKA A M I    01072009 INTL 20120913)
[    0.000000] ACPI: FACS 0x00000000D6C9FF80 000040
[    0.000000] ACPI: APIC 0x00000000D6C7A858 000068 (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x00000000D6C7A8C0 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x00000000D6C7A908 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x00000000D6C7A9A8 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000D6C7A9E8 000038 (v01 ALASKA A M I    01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 0x00000000D6C7AA20 000315 (v01 SataRe SataTabl 00001000 INTL 20120913)
[    0.000000] ACPI: UEFI 0x00000000D6C7AD38 000042 (v01                 00000000      00000000)
[    0.000000] ACPI: SSDT 0x00000000D6C7AD80 000C7D (v02 Ther_R Ther_Rvp 00001000 INTL 20120913)
[    0.000000] ACPI: ASF! 0x00000000D6C7BA00 0000A0 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] ACPI: SSDT 0x00000000D6C7BAA0 0004B5 (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000D6C7BF58 000B74 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
[    0.000000] ACPI: TPM2 0x00000000D6C7CAD0 000034 (v03        Tpm2Tabl 00000001 AMI  00000000)
[    0.000000] ACPI: SSDT 0x00000000D6C7CB08 000041 (v01 Ssdt   PttSsdt  00001000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000D6C7CB50 005CF6 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
[    0.000000] ACPI: DMAR 0x00000000D6C82848 0000B0 (v01 INTEL  BDW      00000001 INTL 00000001)
[    0.000000] ACPI: BGRT 0x00000000D6C828F8 000038 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011effffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x11eff7000-0x11effbfff]
[    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011a800000-ffff88011e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000011effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000057fff]
[    0.000000]   node   0: [mem 0x0000000000059000-0x000000000009efff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000d1f50fff]
[    0.000000]   node   0: [mem 0x00000000d2231000-0x00000000d62ecfff]
[    0.000000]   node   0: [mem 0x00000000d6333000-0x00000000d6521fff]
[    0.000000]   node   0: [mem 0x00000000d6ffe000-0x00000000d6ffefff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000011effffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000011effffff]
[    0.000000] On node 0 totalpages: 1003930
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 25 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13640 pages used for memmap
[    0.000000]   DMA32 zone: 872957 pages, LIFO batch:31
[    0.000000]   Normal zone: 1984 pages used for memmap
[    0.000000]   Normal zone: 126976 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0xd8000000-0xdfffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0xa4])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl edge lint[0x0])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xd1f51000-0xd2230fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd62ed000-0xd6332fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd6522000-0xd6ca0fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd6ca1000-0xd6f8afff]
[    0.000000] PM: Registered nosave memory: [mem 0xd6f8b000-0xd6ffdfff]
[    0.000000] PM: Registered nosave memory: [mem 0xd6fff000-0xd77fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xd7800000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xe0000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 34 pages/cpu @ffff88011ec00000 s100376 r8192 d30696 u1048576
[    0.000000] pcpu-alloc: s100376 r8192 d30696 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 988217
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.1.6-040106-generic root=UUID=c456624b-f6c2-4dc7-bf92-640922e83f77 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240 using standard form
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3793632K/4015720K available (8056K kernel code, 1243K rwdata, 3780K rodata, 1424K init, 1292K bss, 222088K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=2
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-1.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1496.588 MHz processor
[    0.000043] Calibrating delay loop (skipped), value calculated using timer frequency.. 2993.17 BogoMIPS (lpj=5986352)
[    0.000049] pid_max: default: 32768 minimum: 301
[    0.000056] ACPI: Core revision 20150410
[    0.026464] ACPI: All ACPI Tables successfully acquired
[    0.027364] Security Framework initialized
[    0.027379] AppArmor: AppArmor initialized
[    0.027380] Yama: becoming mindful.
[    0.027795] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.029018] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.029561] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.029570] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.029829] Initializing cgroup subsys blkio
[    0.029835] Initializing cgroup subsys memory
[    0.029844] Initializing cgroup subsys devices
[    0.029847] Initializing cgroup subsys freezer
[    0.029850] Initializing cgroup subsys net_cls
[    0.029852] Initializing cgroup subsys perf_event
[    0.029855] Initializing cgroup subsys net_prio
[    0.029857] Initializing cgroup subsys hugetlb
[    0.029892] CPU: Physical Processor ID: 0
[    0.029894] CPU: Processor Core ID: 0
[    0.029899] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.029901] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.031217] mce: CPU supports 7 MCE banks
[    0.031234] CPU0: Thermal monitoring enabled (TM1)
[    0.031246] process: using mwait in idle threads
[    0.031250] Last level iTLB entries: 4KB 128, 2MB 8, 4MB 8
[    0.031251] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.031455] Freeing SMP alternatives memory: 32K (ffffffff81e9c000 - ffffffff81ea4000)
[    0.035664] ftrace: allocating 30366 entries in 119 pages
[    0.054269] dmar: Host address width 39
[    0.054273] dmar: DRHD base: 0x000000fed90000 flags: 0x0
[    0.054287] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e1ff0505e
[    0.054290] dmar: DRHD base: 0x000000fed91000 flags: 0x1
[    0.054298] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
[    0.054300] dmar: RMRR base: 0x000000d6ee3000 end: 0x000000d6ef1fff
[    0.054302] dmar: RMRR base: 0x000000d7800000 end: 0x000000dfffffff
[    0.054305] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.054306] HPET id 0 under DRHD base 0xfed91000
[    0.054742] x2apic is disabled because BIOS sets x2apic opt out bit. You can use 'intremap=no_x2apic_optout' to override the BIOS setting.
[    0.054758] Enabled IRQ remapping in xapic mode
[    0.054759] x2apic: IRQ remapping doesn't support X2APIC mode
[    0.055414] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.095091] TSC deadline timer enabled
[    0.095094] smpboot: CPU0: Intel(R) Celeron(R) 3205U @ 1.50GHz (fam: 06, model: 3d, stepping: 04)
[    0.095132] Performance Events: PEBS fmt2+, 16-deep LBR, Broadwell events, full-width counters, Intel PMU driver.
[    0.095161] ... version:                3
[    0.095162] ... bit width:              48
[    0.095164] ... generic registers:      8
[    0.095165] ... value mask:             0000ffffffffffff
[    0.095166] ... max period:             0000ffffffffffff
[    0.095167] ... fixed-purpose events:   3
[    0.095168] ... event mask:             00000007000000ff
[    0.096334] x86: Booting SMP configuration:
[    0.096337] .... node  #0, CPUs:      #1
[    0.110887] x86: Booted up 1 node, 2 CPUs
[    0.110891] smpboot: Total of 2 processors activated (5986.35 BogoMIPS)
[    0.110928] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.112952] devtmpfs: initialized
[    0.115883] evm: security.selinux
[    0.115885] evm: security.SMACK64
[    0.115886] evm: security.SMACK64EXEC
[    0.115887] evm: security.SMACK64TRANSMUTE
[    0.115888] evm: security.SMACK64MMAP
[    0.115889] evm: security.ima
[    0.115891] evm: security.capability
[    0.115970] PM: Registering ACPI NVS region [mem 0xd6522000-0xd6ca0fff] (7860224 bytes)
[    0.116189] clocksource jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.116280] pinctrl core: initialized pinctrl subsystem
[    0.116414] RTC time: 15:52:43, date: 10/15/15
[    0.116571] NET: Registered protocol family 16
[    0.122920] cpuidle: using governor ladder
[    0.126922] cpuidle: using governor menu
[    0.126997] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.126999] ACPI: bus type PCI registered
[    0.127001] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.127090] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.127093] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.127212] PCI: Using configuration type 1 for base access
[    0.131394] ACPI: Added _OSI(Module Device)
[    0.131397] ACPI: Added _OSI(Processor Device)
[    0.131399] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.131401] ACPI: Added _OSI(Processor Aggregator Device)
[    0.139580] ACPI: Executed 18 blocks of module-level executable AML code
[    0.146191] ACPI: Dynamic OEM Table Load:
[    0.146200] ACPI: SSDT 0xFFFF880119490C00 0003D3 (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
[    0.147490] ACPI: Dynamic OEM Table Load:
[    0.147497] ACPI: SSDT 0xFFFF88011A417800 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
[    0.148853] ACPI: Dynamic OEM Table Load:
[    0.148859] ACPI: SSDT 0xFFFF88011943F600 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
[    0.150600] ACPI: Interpreter enabled
[    0.150611] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150410/hwxface-580)
[    0.150620] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150410/hwxface-580)
[    0.150640] ACPI: (supports S0 S3 S4 S5)
[    0.150644] ACPI: Using IOAPIC for interrupt routing
[    0.150685] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.153447] ACPI: Power Resource [PG00] (on)
[    0.153959] ACPI: Power Resource [PG01] (on)
[    0.154452] ACPI: Power Resource [PG02] (on)
[    0.167312] ACPI: Power Resource [FN00] (off)
[    0.167415] ACPI: Power Resource [FN01] (off)
[    0.167514] ACPI: Power Resource [FN02] (off)
[    0.167612] ACPI: Power Resource [FN03] (off)
[    0.167709] ACPI: Power Resource [FN04] (off)
[    0.169147] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.169155] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.169892] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.169894] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.170514] PCI host bridge to bus 0000:00
[    0.170518] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.170521] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.170523] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.170525] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.170527] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfeafffff window]
[    0.170537] pci 0000:00:00.0: [8086:1604] type 00 class 0x060000
[    0.170664] pci 0000:00:02.0: [8086:1606] type 00 class 0x030000
[    0.170678] pci 0000:00:02.0: reg 0x10: [mem 0xf6000000-0xf6ffffff 64bit]
[    0.170687] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.170694] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.170811] pci 0000:00:03.0: [8086:160c] type 00 class 0x040300
[    0.170822] pci 0000:00:03.0: reg 0x10: [mem 0xf7214000-0xf7217fff 64bit]
[    0.170960] pci 0000:00:14.0: [8086:9cb1] type 00 class 0x0c0330
[    0.170979] pci 0000:00:14.0: reg 0x10: [mem 0xf7200000-0xf720ffff 64bit]
[    0.171043] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.171109] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.171159] pci 0000:00:16.0: [8086:9cba] type 00 class 0x078000
[    0.171178] pci 0000:00:16.0: reg 0x10: [mem 0xf721c000-0xf721c01f 64bit]
[    0.171244] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.171373] pci 0000:00:1b.0: [8086:9ca0] type 00 class 0x040300
[    0.171390] pci 0000:00:1b.0: reg 0x10: [mem 0xf7210000-0xf7213fff 64bit]
[    0.171444] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.171520] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.171569] pci 0000:00:1c.0: [8086:9c90] type 01 class 0x060400
[    0.171634] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.171732] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.171781] pci 0000:00:1c.2: [8086:9c94] type 01 class 0x060400
[    0.171848] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.171942] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.171989] pci 0000:00:1c.3: [8086:9c96] type 01 class 0x060400
[    0.172057] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.172150] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.172203] pci 0000:00:1d.0: [8086:9ca6] type 00 class 0x0c0320
[    0.172222] pci 0000:00:1d.0: reg 0x10: [mem 0xf721a000-0xf721a3ff]
[    0.172311] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.172377] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.172427] pci 0000:00:1f.0: [8086:9cc5] type 00 class 0x060100
[    0.172633] pci 0000:00:1f.2: [8086:9c83] type 00 class 0x010601
[    0.172648] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
[    0.172656] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
[    0.172665] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
[    0.172673] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
[    0.172681] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
[    0.172690] pci 0000:00:1f.2: reg 0x24: [mem 0xf7219000-0xf72197ff]
[    0.172726] pci 0000:00:1f.2: PME# supported from D3hot
[    0.172825] pci 0000:00:1f.3: [8086:9ca2] type 00 class 0x0c0500
[    0.172841] pci 0000:00:1f.3: reg 0x10: [mem 0xf7218000-0xf72180ff 64bit]
[    0.172864] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    0.173050] acpiphp: Slot [1] registered
[    0.173056] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.173151] pci 0000:02:00.0: [8086:08b3] type 00 class 0x028000
[    0.173187] pci 0000:02:00.0: reg 0x10: [mem 0xf7100000-0xf7101fff 64bit]
[    0.173344] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.173405] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.180859] pci 0000:00:1c.2: PCI bridge to [bus 02]
[    0.180865] pci 0000:00:1c.2:   bridge window [mem 0xf7100000-0xf71fffff]
[    0.180956] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    0.180977] pci 0000:03:00.0: reg 0x10: [io  0xe000-0xe0ff]
[    0.181009] pci 0000:03:00.0: reg 0x18: [mem 0xf7000000-0xf7000fff 64bit]
[    0.181028] pci 0000:03:00.0: reg 0x20: [mem 0xf0000000-0xf0003fff 64bit pref]
[    0.181116] pci 0000:03:00.0: supports D1 D2
[    0.181118] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.181173] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.188872] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    0.188876] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    0.188880] pci 0000:00:1c.3:   bridge window [mem 0xf7000000-0xf70fffff]
[    0.188885] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.189911] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.189975] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.190037] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.190095] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.190152] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.190211] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.190272] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.190334] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.190866] ACPI: Enabled 4 GPEs in block 00 to 7F
[    0.191027] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.191030] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.191034] vgaarb: loaded
[    0.191035] vgaarb: bridge control possible 0000:00:02.0
[    0.191318] SCSI subsystem initialized
[    0.191372] libata version 3.00 loaded.
[    0.191404] ACPI: bus type USB registered
[    0.191427] usbcore: registered new interface driver usbfs
[    0.191438] usbcore: registered new interface driver hub
[    0.191452] usbcore: registered new device driver usb
[    0.191683] PCI: Using ACPI for IRQ routing
[    0.193214] PCI: pci_cache_line_size set to 64 bytes
[    0.193261] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
[    0.193263] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.193265] e820: reserve RAM buffer [mem 0xd1f51000-0xd3ffffff]
[    0.193267] e820: reserve RAM buffer [mem 0xd62ed000-0xd7ffffff]
[    0.193269] e820: reserve RAM buffer [mem 0xd6522000-0xd7ffffff]
[    0.193271] e820: reserve RAM buffer [mem 0xd6fff000-0xd7ffffff]
[    0.193273] e820: reserve RAM buffer [mem 0x11f000000-0x11fffffff]
[    0.193431] NetLabel: Initializing
[    0.193433] NetLabel:  domain hash size = 128
[    0.193434] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.193449] NetLabel:  unlabeled traffic allowed by default
[    0.193534] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.193541] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.195583] Switched to clocksource hpet
[    0.203500] AppArmor: AppArmor Filesystem Enabled
[    0.203603] pnp: PnP ACPI init
[    0.203906] system 00:00: [io  0x0a00-0x0a2f] has been reserved
[    0.203909] system 00:00: [io  0x0a30-0x0a3f] has been reserved
[    0.203911] system 00:00: [io  0x0a40-0x0a4f] has been reserved
[    0.203917] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.204027] system 00:01: [io  0x0680-0x069f] has been reserved
[    0.204030] system 00:01: [io  0xffff] has been reserved
[    0.204032] system 00:01: [io  0xffff] has been reserved
[    0.204034] system 00:01: [io  0xffff] has been reserved
[    0.204037] system 00:01: [io  0x1800-0x18fe] could not be reserved
[    0.204039] system 00:01: [io  0x164e-0x164f] has been reserved
[    0.204042] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.204108] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.204157] system 00:03: [io  0x1854-0x1857] has been reserved
[    0.204160] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.204386] system 00:04: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.204388] system 00:04: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.204391] system 00:04: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.204393] system 00:04: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.204395] system 00:04: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.204398] system 00:04: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.204400] system 00:04: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.204403] system 00:04: [mem 0xfed45000-0xfed8ffff] could not be reserved
[    0.204405] system 00:04: [mem 0xff000000-0xffffffff] has been reserved
[    0.204408] system 00:04: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.204410] system 00:04: [mem 0xf7fe0000-0xf7feffff] has been reserved
[    0.204413] system 00:04: [mem 0xf7ff0000-0xf7ffffff] has been reserved
[    0.204416] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.204990] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.205525] pnp: PnP ACPI: found 6 devices
[    0.212198] clocksource acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.212232] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.212244] pci 0000:00:1c.2: PCI bridge to [bus 02]
[    0.212250] pci 0000:00:1c.2:   bridge window [mem 0xf7100000-0xf71fffff]
[    0.212258] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    0.212261] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    0.212266] pci 0000:00:1c.3:   bridge window [mem 0xf7000000-0xf70fffff]
[    0.212270] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.212278] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.212280] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.212282] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.212285] pci_bus 0000:00: resource 7 [mem 0xe0000000-0xfeafffff window]
[    0.212287] pci_bus 0000:02: resource 1 [mem 0xf7100000-0xf71fffff]
[    0.212290] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.212292] pci_bus 0000:03: resource 1 [mem 0xf7000000-0xf70fffff]
[    0.212294] pci_bus 0000:03: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.212332] NET: Registered protocol family 2
[    0.212536] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.212633] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.212718] TCP: Hash tables configured (established 32768 bind 32768)
[    0.212751] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.212774] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.212828] NET: Registered protocol family 1
[    0.212850] pci 0000:00:02.0: Video device with shadowed ROM
[    0.231712] PCI: CLS 64 bytes, default 64
[    0.231780] Trying to unpack rootfs image as initramfs...
[    0.681848] Freeing initrd memory: 18704K (ffff880035b68000 - ffff880036dac000)
[    0.681895] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.681899] software IO TLB [mem 0xca247000-0xce247000] (64MB) mapped at [ffff8800ca247000-ffff8800ce246fff]
[    0.681984] RAPL PMU detected, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
[    0.681986] hw unit of domain pp0-core 2^-14 Joules
[    0.681988] hw unit of domain package 2^-14 Joules
[    0.681989] hw unit of domain dram 2^-14 Joules
[    0.681990] hw unit of domain pp1-gpu 2^-14 Joules
[    0.682085] microcode: CPU0 sig=0x306d4, pf=0x40, revision=0x11
[    0.682092] microcode: CPU1 sig=0x306d4, pf=0x40, revision=0x11
[    0.682154] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.682193] Scanning for low memory corruption every 60 seconds
[    0.682591] futex hash table entries: 512 (order: 3, 32768 bytes)
[    0.682608] Initialise system trusted keyring
[    0.682631] audit: initializing netlink subsys (disabled)
[    0.682649] audit: type=2000 audit(1444924363.672:1): initialized
[    0.683132] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    0.683133] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.685251] zpool: loaded
[    0.685255] zbud: loaded
[    0.685465] VFS: Disk quotas dquot_6.6.0
[    0.685514] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.686113] fuse init (API version 7.23)
[    0.686290] Key type big_key registered
[    0.686652] Key type asymmetric registered
[    0.686656] Asymmetric key parser 'x509' registered
[    0.686703] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 251)
[    0.686737] io scheduler noop registered
[    0.686743] io scheduler deadline registered (default)
[    0.686786] io scheduler cfq registered
[    0.687515] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.687521] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.687536] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    0.687540] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.687544] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    0.687560] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    0.687562] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.687566] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    0.687576] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.687599] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.687652] efifb: probing for efifb
[    0.687682] efifb: framebuffer at 0xe0000000, mapped to 0xffffc90000800000, using 8128k, total 8128k
[    0.687684] efifb: mode is 1920x1080x32, linelength=7680, pages=1
[    0.687685] efifb: scrolling: redraw
[    0.687687] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.694491] Console: switching to colour frame buffer device 240x67
[    0.701645] fb0: EFI VGA frame buffer device
[    0.701659] intel_idle: MWAIT substates: 0x11142120
[    0.701661] intel_idle: v0.4 model 0x3D
[    0.701663] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.701923] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.701928] ACPI: Sleep Button [SLPB]
[    0.701973] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.701976] ACPI: Power Button [PWRB]
[    0.702023] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.702025] ACPI: Power Button [PWRF]
[    0.702932] thermal LNXTHERM:00: registered as thermal_zone0
[    0.702935] ACPI: Thermal Zone [TZ00] (28 C)
[    0.703182] thermal LNXTHERM:01: registered as thermal_zone1
[    0.703183] ACPI: Thermal Zone [TZ01] (30 C)
[    0.703292] GHES: HEST is not enabled!
[    0.703423] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.705408] Linux agpgart interface v0.103
[    0.707867] brd: module loaded
[    0.708918] loop: module loaded
[    0.709182] libphy: Fixed MDIO Bus: probed
[    0.709187] tun: Universal TUN/TAP device driver, 1.6
[    0.709188] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.709242] PPP generic driver version 2.4.2
[    0.709481] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.709489] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.709573] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00009810
[    0.709579] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.709662] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.709664] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.709666] usb usb1: Product: xHCI Host Controller
[    0.709668] usb usb1: Manufacturer: Linux 4.1.6-040106-generic xhci-hcd
[    0.709670] usb usb1: SerialNumber: 0000:00:14.0
[    0.709803] hub 1-0:1.0: USB hub found
[    0.709815] hub 1-0:1.0: 11 ports detected
[    0.711599] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.711604] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.711639] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.711641] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.711643] usb usb2: Product: xHCI Host Controller
[    0.711645] usb usb2: Manufacturer: Linux 4.1.6-040106-generic xhci-hcd
[    0.711646] usb usb2: SerialNumber: 0000:00:14.0
[    0.711798] hub 2-0:1.0: USB hub found
[    0.711807] hub 2-0:1.0: 4 ports detected
[    0.712407] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.712414] ehci-pci: EHCI PCI platform driver
[    0.712557] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.712563] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    0.712574] ehci-pci 0000:00:1d.0: debug port 2
[    0.716477] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.716492] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf721a000
[    0.731460] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.731537] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.731540] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.731543] usb usb3: Product: EHCI Host Controller
[    0.731545] usb usb3: Manufacturer: Linux 4.1.6-040106-generic ehci_hcd
[    0.731546] usb usb3: SerialNumber: 0000:00:1d.0
[    0.731812] hub 3-0:1.0: USB hub found
[    0.731820] hub 3-0:1.0: 2 ports detected
[    0.731987] ehci-platform: EHCI generic platform driver
[    0.732006] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.732015] ohci-pci: OHCI PCI platform driver
[    0.732030] ohci-platform: OHCI generic platform driver
[    0.732041] uhci_hcd: USB Universal Host Controller Interface driver
[    0.732110] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.459166] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    1.679111] tsc: Refined TSC clocksource calibration: 1496.535 MHz
[    1.679115] clocksource tsc: mask: 0xffffffffffffffff max_cycles: 0x159259799ff, max_idle_ns: 440795263419 ns
[    1.765715] i8042: No controller found
[    1.765945] mousedev: PS/2 mouse device common for all mice
[    1.766464] rtc_cmos 00:02: RTC can wake from S4
[    1.766658] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.766691] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.766716] i2c /dev entries driver
[    1.766789] device-mapper: uevent: version 1.0.3
[    1.766880] device-mapper: ioctl: 4.31.0-ioctl (2015-3-12) initialised: dm-devel@redhat.com
[    1.766908] Intel P-state driver initializing.
[    1.766992] ledtrig-cpu: registered to indicate activity on CPUs
[    1.766996] EFI Variables Facility v0.08 2004-May-17
[    1.769052] PCCT header not found.
[    1.769313] NET: Registered protocol family 10
[    1.769546] NET: Registered protocol family 17
[    1.769564] Key type dns_resolver registered
[    1.769940] Loading compiled-in X.509 certificates
[    1.771094] Loaded X.509 cert 'Build time autogenerated kernel key: 355479ea572ba7361fe0c75a06c61f90ae79791e'
[    1.771113] registered taskstats version 1
[    1.773381] Key type trusted registered
[    1.777226] Key type encrypted registered
[    1.777236] AppArmor: AppArmor sha1 policy hashing enabled
[    1.777241] ima: No TPM chip found, activating TPM-bypass!
[    1.777270] evm: HMAC attrs: 0x1
[    1.777752]   Magic number: 3:83:892
[    1.777868] rtc_cmos 00:02: setting system clock to 2015-10-15 15:52:45 UTC (1444924365)
[    1.777940] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.777942] EDD information not available.
[    1.778054] PM: Hibernation image not present or could not be loaded.
[    1.778496] Freeing unused kernel memory: 1424K (ffffffff81d38000 - ffffffff81e9c000)
[    1.778499] Write protecting the kernel read-only data: 12288k
[    1.778733] Freeing unused kernel memory: 124K (ffff8800027e1000 - ffff880002800000)
[    1.778845] Freeing unused kernel memory: 316K (ffff880002bb1000 - ffff880002c00000)
[    1.793240] systemd-udevd[105]: starting version 204
[    1.829393] sdhci: Secure Digital Host Controller Interface driver
[    1.829396] sdhci: Copyright(c) Pierre Ossman
[    1.831714] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.831724] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.841443] r8169 0000:03:00.0 eth0: RTL8168g/8111g at 0xffffc90000678000, fc:aa:14:f1:f4:7b, XID 0c000800 IRQ 46
[    1.841448] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.846034] ahci 0000:00:1f.2: version 3.0
[    1.846243] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x1 impl SATA mode
[    1.846247] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo only pio slum part deso sadm apst 
[    1.847111] scsi host0: ahci
[    1.848174] scsi host1: ahci
[    1.848250] ata1: SATA max UDMA/133 abar m2048@0xf7219000 port 0xf7219100 irq 47
[    1.848253] ata2: DUMMY
[    1.886213] r8169 0000:03:00.0 p3p1: renamed from eth0
[    1.895444] usb 3-1: New USB device found, idVendor=8087, idProduct=8001
[    1.895448] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.895836] hub 3-1:1.0: USB hub found
[    1.896010] hub 3-1:1.0: 8 ports detected
[    1.903230] systemd-udevd[107]: renamed network interface eth0 to p3p1
[    1.931023] usb 1-7: new full-speed USB device number 2 using xhci_hcd
[    2.060363] usb 1-7: New USB device found, idVendor=8087, idProduct=07dc
[    2.060368] usb 1-7: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.166948] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.179525] ata1.00: ATA-8: KINGSTON SMS200S330G, 603ABBF0, max UDMA/133
[    2.179530] ata1.00: 58626288 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.184653] ata1.00: configured for UDMA/133
[    2.184900] scsi 0:0:0:0: Direct-Access     ATA      KINGSTON SMS200S BBF0 PQ: 0 ANSI: 5
[    2.185359] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.185371] sd 0:0:0:0: [sda] 58626288 512-byte logical blocks: (30.0 GB/27.9 GiB)
[    2.185422] sd 0:0:0:0: [sda] Write Protect is off
[    2.185425] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.185443] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.186231]  sda: sda1 sda2 sda3
[    2.186668] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.218305] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
[    2.218309] EXT4-fs (sda2): write access will be enabled during recovery
[    2.227540] EXT4-fs (sda2): orphan cleanup on readonly fs
[    2.227568] EXT4-fs (sda2): 1 orphan inode deleted
[    2.227570] EXT4-fs (sda2): recovery complete
[    2.228022] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    2.295602] random: init urandom read with 21 bits of entropy available
[    2.319950] init: plymouth-upstart-bridge main process (162) terminated with status 1
[    2.319965] init: plymouth-upstart-bridge main process ended, respawning
[    2.329905] init: plymouth-upstart-bridge main process (172) terminated with status 1
[    2.329918] init: plymouth-upstart-bridge main process ended, respawning
[    2.336437] init: plymouth-upstart-bridge main process (175) terminated with status 1
[    2.336451] init: plymouth-upstart-bridge main process ended, respawning
[    2.353719] init: ureadahead main process (165) terminated with status 5
[    2.493040] Adding 4016124k swap on /dev/sda3.  Priority:-1 extents:1 across:4016124k SSFS
[    2.576835] systemd-udevd[287]: starting version 204
[    2.578250] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    2.677307] lp: driver loaded but no devices found
[    2.684989] Switched to clocksource tsc
[    2.776058] hidraw: raw HID events driver (C) Jiri Kosina
[    2.980350] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    3.092200] audit: type=1400 audit(1444924366.811:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=410 comm="apparmor_parser"
[    3.092208] audit: type=1400 audit(1444924366.811:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=410 comm="apparmor_parser"
[    3.092212] audit: type=1400 audit(1444924366.811:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=410 comm="apparmor_parser"
[    3.092676] audit: type=1400 audit(1444924366.811:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=410 comm="apparmor_parser"
[    3.092680] audit: type=1400 audit(1444924366.811:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=410 comm="apparmor_parser"
[    3.092906] audit: type=1400 audit(1444924366.811:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=410 comm="apparmor_parser"
[    3.105717] audit: type=1400 audit(1444924366.823:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=415 comm="apparmor_parser"
[    3.122465] [drm] Initialized drm 1.1.0 20060810
[    3.124231] Bluetooth: Core ver 2.20
[    3.124255] NET: Registered protocol family 31
[    3.124257] Bluetooth: HCI device and connection manager initialized
[    3.124263] Bluetooth: HCI socket layer initialized
[    3.124266] Bluetooth: L2CAP socket layer initialized
[    3.124273] Bluetooth: SCO socket layer initialized
[    3.132882] cfg80211: Calling CRDA to update world regulatory domain
[    3.215734] Intel(R) Wireless WiFi driver for Linux
[    3.215738] Copyright(c) 2003- 2015 Intel Corporation
[    3.215796] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[    3.223217] snd_hda_intel 0000:00:03.0: enabling device (0000 -> 0002)
[    3.224903] iwlwifi 0000:02:00.0: Unsupported splx structure
[    3.227803] r8169 0000:03:00.0 p3p1: link down
[    3.227824] r8169 0000:03:00.0 p3p1: link down
[    3.231082] iwlwifi 0000:02:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
[    3.231693] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[    3.241882] IPv6: ADDRCONF(NETDEV_UP): p3p1: link is not ready
[    3.252561] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC283: line_outs=1 (0x21/0x0/0x0/0x0/0x0) type:hp
[    3.252566] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.252569] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.252571] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[    3.252572] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[    3.252575] snd_hda_codec_realtek hdaudioC1D0:      Mic=0x19
[    3.259670] usbcore: registered new interface driver btusb
[    3.290316] Bluetooth: hci0: read Intel version: 3707100100012d0d00
[    3.290760] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.0.1.2d.d.bseq
[    3.302009] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input3
[    3.302128] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input4
[    3.305524] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[    3.305598] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[    3.305821] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[    3.308945] [drm] Memory usable by graphics device = 4096M
[    3.308951] checking generic (e0000000 7f0000) vs hw (e0000000 10000000)
[    3.308953] fb: switching to inteldrmfb from EFI VGA
[    3.309004] Console: switching to colour dummy device 80x25
[    3.310153] [drm] Replacing VGA console driver
[    3.319956] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.319959] [drm] Driver supports precise vblank timestamp query.
[    3.320090] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.332486] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.333237] acpi device:10: registered as cooling_device7
[    3.333343] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    3.339607] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    3.339613] [drm] Initialized i915 1.6.0 20150327 for 0000:00:02.0 on minor 0
[    3.345093] fbcon: inteldrmfb (fb0) is primary device
[    3.369293] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    3.407463] Console: switching to colour frame buffer device 240x67
[    3.414746] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    3.414748] i915 0000:00:02.0: registered panic notifier
[    3.472366] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.503086] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input6
[    3.503160] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input7
[    3.503223] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input8
[    3.572366] intel_rapl: Found RAPL domain package
[    3.572372] intel_rapl: Found RAPL domain core
[    3.572376] intel_rapl: Found RAPL domain dram
[    3.690373] init: failsafe main process (644) killed by TERM signal
[    3.838036] audit: type=1400 audit(1444924367.555:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=771 comm="apparmor_parser"
[    3.838046] audit: type=1400 audit(1444924367.555:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=771 comm="apparmor_parser"
[    4.021012] random: nonblocking pool is initialized



```

Not working logs (so really bad performance):

Xorg.0.log

```
[     4.858] X.Org X Server 1.15.1
Release Date: 2014-04-13
[     4.858] X Protocol Version 11, Revision 0
[     4.858] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[     4.858] Current Operating System: Linux hoogstraat-client-1 4.1.6-040106-generic #201508170230 SMP Mon Aug 17 06:32:14 UTC 2015 x86_64
[     4.858] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.1.6-040106-generic root=UUID=c456624b-f6c2-4dc7-bf92-640922e83f77 ro quiet splash vt.handoff=7
[     4.858] Build Date: 12 February 2015  02:49:29PM
[     4.858] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[     4.858] Current version of pixman: 0.30.2
[     4.858]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     4.858] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     4.858] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 15 16:43:06 2015
[     4.859] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     4.861] (==) No Layout section.  Using the first Screen section.
[     4.861] (==) No screen section available. Using defaults.
[     4.861] (**) |-->Screen "Default Screen Section" (0)
[     4.861] (**) |   |-->Monitor "<default monitor>"
[     4.861] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     4.861] (==) Automatically adding devices
[     4.861] (==) Automatically enabling devices
[     4.861] (==) Automatically adding GPU devices
[     4.862] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.862]     Entry deleted from font path.
[     4.862] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     4.862]     Entry deleted from font path.
[     4.862] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     4.862]     Entry deleted from font path.
[     4.862] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[     4.862]     Entry deleted from font path.
[     4.862] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     4.862]     Entry deleted from font path.
[     4.862] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     4.862]     Entry deleted from font path.
[     4.862] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    built-ins
[     4.862] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     4.862] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     4.862] (II) Loader magic: 0x55a8b6aa6d40
[     4.862] (II) Module ABI versions:
[     4.862]     X.Org ANSI C Emulation: 0.4
[     4.862]     X.Org Video Driver: 15.0
[     4.862]     X.Org XInput driver : 20.0
[     4.862]     X.Org Server Extension : 8.0
[     4.863] (II) xfree86: Adding drm device (/dev/dri/card0)
[     4.864] (--) PCI:*(0:0:2:0) 8086:1606:1458:1000 rev 8, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, I/O @ 0x0000f000/64
[     4.864] Initializing built-in extension Generic Event Extension
[     4.864] Initializing built-in extension SHAPE
[     4.864] Initializing built-in extension MIT-SHM
[     4.864] Initializing built-in extension XInputExtension
[     4.864] Initializing built-in extension XTEST
[     4.864] Initializing built-in extension BIG-REQUESTS
[     4.864] Initializing built-in extension SYNC
[     4.864] Initializing built-in extension XKEYBOARD
[     4.864] Initializing built-in extension XC-MISC
[     4.864] Initializing built-in extension SECURITY
[     4.864] Initializing built-in extension XINERAMA
[     4.864] Initializing built-in extension XFIXES
[     4.864] Initializing built-in extension RENDER
[     4.864] Initializing built-in extension RANDR
[     4.864] Initializing built-in extension COMPOSITE
[     4.864] Initializing built-in extension DAMAGE
[     4.864] Initializing built-in extension MIT-SCREEN-SAVER
[     4.864] Initializing built-in extension DOUBLE-BUFFER
[     4.864] Initializing built-in extension RECORD
[     4.864] Initializing built-in extension DPMS
[     4.864] Initializing built-in extension Present
[     4.864] Initializing built-in extension DRI3
[     4.864] Initializing built-in extension X-Resource
[     4.864] Initializing built-in extension XVideo
[     4.864] Initializing built-in extension XVideo-MotionCompensation
[     4.864] Initializing built-in extension SELinux
[     4.864] Initializing built-in extension XFree86-VidModeExtension
[     4.864] Initializing built-in extension XFree86-DGA
[     4.864] Initializing built-in extension XFree86-DRI
[     4.864] Initializing built-in extension DRI2
[     4.864] (II) LoadModule: "glx"
[     4.866] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     4.872] (II) Module glx: vendor="X.Org Foundation"
[     4.872]     compiled for 1.15.1, module version = 1.0.0
[     4.872]     ABI class: X.Org Server Extension, version 8.0
[     4.872] (==) AIGLX enabled
[     4.872] Loading extension GLX
[     4.872] (==) Matched intel as autoconfigured driver 0
[     4.872] (==) Matched intel as autoconfigured driver 1
[     4.872] (==) Matched modesetting as autoconfigured driver 2
[     4.872] (==) Matched fbdev as autoconfigured driver 3
[     4.872] (==) Matched vesa as autoconfigured driver 4
[     4.872] (==) Assigned the driver to the xf86ConfigLayout
[     4.872] (II) LoadModule: "intel"
[     4.872] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     4.875] (II) Module intel: vendor="X.Org Foundation"
[     4.875]     compiled for 1.15.1, module version = 2.99.910
[     4.875]     Module class: X.Org Video Driver
[     4.875]     ABI class: X.Org Video Driver, version 15.0
[     4.875] (II) LoadModule: "modesetting"
[     4.875] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     4.875] (II) Module modesetting: vendor="X.Org Foundation"
[     4.875]     compiled for 1.15.0, module version = 0.8.1
[     4.875]     Module class: X.Org Video Driver
[     4.875]     ABI class: X.Org Video Driver, version 15.0
[     4.875] (II) LoadModule: "fbdev"
[     4.875] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     4.876] (II) Module fbdev: vendor="X.Org Foundation"
[     4.876]     compiled for 1.15.0, module version = 0.4.4
[     4.876]     Module class: X.Org Video Driver
[     4.876]     ABI class: X.Org Video Driver, version 15.0
[     4.876] (II) LoadModule: "vesa"
[     4.876] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     4.876] (II) Module vesa: vendor="X.Org Foundation"
[     4.876]     compiled for 1.15.0, module version = 2.3.3
[     4.876]     Module class: X.Org Video Driver
[     4.876]     ABI class: X.Org Video Driver, version 15.0
[     4.876] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[     4.877] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[     4.877] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[     4.877] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[     4.877] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     4.877] (II) FBDEV: driver for framebuffer: fbdev
[     4.877] (II) VESA: driver for VESA chipsets: vesa
[     4.877] (--) using VT number 8


[     4.887] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1.6 (Timo Aaltonen <tjaalton@debian.org>)
[     4.887] (WW) Falling back to old probe method for modesetting
[     4.889] (WW) Falling back to old probe method for fbdev
[     4.889] (II) Loading sub module "fbdevhw"
[     4.889] (II) LoadModule: "fbdevhw"
[     4.889] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     4.890] (II) Module fbdevhw: vendor="X.Org Foundation"
[     4.890]     compiled for 1.15.1, module version = 0.0.2
[     4.890]     ABI class: X.Org Video Driver, version 15.0
[     4.890] (WW) Falling back to old probe method for vesa
[     4.891] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD graphics
[     4.891] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2
[     4.891] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     4.891] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     4.891] (==) intel(0): RGB weight 888
[     4.891] (==) intel(0): Default visual is TrueColor
[     4.891] (**) intel(0): Framebuffer tiled
[     4.891] (**) intel(0): Pixmaps tiled
[     4.891] (**) intel(0): "Tear free" disabled
[     4.891] (**) intel(0): Forcing per-crtc-pixmaps? no
[     4.891] (II) intel(0): Output HDMI1 has no monitor section
[     4.891] (II) intel(0): Output DP1 has no monitor section
[     4.891] (II) intel(0): Output HDMI2 has no monitor section
[     4.891] (II) intel(0): Output VIRTUAL1 has no monitor section
[     4.891] (--) intel(0): Output HDMI1 using initial mode 1920x1080 on pipe 0
[     4.891] (==) intel(0): DPI set to (96, 96)
[     4.891] (II) Loading sub module "dri2"
[     4.891] (II) LoadModule: "dri2"
[     4.891] (II) Module "dri2" already built-in
[     4.891] (II) UnloadModule: "modesetting"
[     4.891] (II) Unloading modesetting
[     4.891] (II) UnloadModule: "fbdev"
[     4.891] (II) Unloading fbdev
[     4.891] (II) UnloadSubModule: "fbdevhw"
[     4.891] (II) Unloading fbdevhw
[     4.891] (II) UnloadModule: "vesa"
[     4.891] (II) Unloading vesa
[     4.891] (==) Depth 24 pixmap format is 32 bpp
[     4.893] (II) intel(0): SNA initialized with Broadwell backend
[     4.893] (==) intel(0): Backing store enabled
[     4.893] (==) intel(0): Silken mouse enabled
[     4.894] (II) intel(0): HW Cursor enabled
[     4.894] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     4.894] (==) intel(0): DPMS enabled
[     4.894] (II) intel(0): [DRI2] Setup complete
[     4.894] (II) intel(0): [DRI2]   DRI driver: i965
[     4.894] (II) intel(0): [DRI2]   VDPAU driver: i965
[     4.894] (II) intel(0): direct rendering: DRI2 Enabled
[     4.894] (==) intel(0): hotplug detection: "enabled"
[     4.894] (--) RandR disabled
[     4.901] (II) SELinux: Disabled on system
[     4.915] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     4.915] (II) AIGLX: enabled GLX_ARB_create_context
[     4.915] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     4.915] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[     4.915] (II) AIGLX: enabled GLX_INTEL_swap_event
[     4.915] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     4.915] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[     4.915] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[     4.915] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     4.915] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[     4.915] (II) AIGLX: Loaded and initialized i965
[     4.915] (II) GLX: Initialized DRI2 GL provider for screen 0
[     4.919] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using pipe 0, position (0, 0), rotation normal, reflection none
[     4.949] (II) intel(0): Setting screen physical size to 508 x 285
[     4.961] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     4.992] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     4.992] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.992] (II) LoadModule: "evdev"
[     4.992] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     4.993] (II) Module evdev: vendor="X.Org Foundation"
[     4.993]     compiled for 1.15.0, module version = 2.8.2
[     4.993]     Module class: X.Org XInput Driver
[     4.993]     ABI class: X.Org XInput driver, version 20.0
[     4.993] (II) Using input driver 'evdev' for 'Power Button'
[     4.993] (**) Power Button: always reports core events
[     4.993] (**) evdev: Power Button: Device: "/dev/input/event2"
[     4.993] (--) evdev: Power Button: Vendor 0 Product 0x1
[     4.993] (--) evdev: Power Button: Found keys
[     4.993] (II) evdev: Power Button: Configuring as keyboard
[     4.993] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[     4.993] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     4.993] (**) Option "xkb_rules" "evdev"
[     4.993] (**) Option "xkb_model" "pc105"
[     4.993] (**) Option "xkb_layout" "us"
[     4.993] (**) Option "xkb_variant" "intl"
[     4.997] (II) XKB: generating xkmfile /tmp/server-A5431D4A34463C892C9E905E2E421B30A3CC30DD.xkm
[     5.017] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[     5.017] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     5.017] (II) Using input driver 'evdev' for 'Video Bus'
[     5.017] (**) Video Bus: always reports core events
[     5.017] (**) evdev: Video Bus: Device: "/dev/input/event5"
[     5.017] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     5.017] (--) evdev: Video Bus: Found keys
[     5.018] (II) evdev: Video Bus: Configuring as keyboard
[     5.018] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[     5.018] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     5.018] (**) Option "xkb_rules" "evdev"
[     5.018] (**) Option "xkb_model" "pc105"
[     5.018] (**) Option "xkb_layout" "us"
[     5.018] (**) Option "xkb_variant" "intl"
[     5.018] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     5.018] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.018] (II) Using input driver 'evdev' for 'Power Button'
[     5.018] (**) Power Button: always reports core events
[     5.018] (**) evdev: Power Button: Device: "/dev/input/event1"
[     5.018] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.018] (--) evdev: Power Button: Found keys
[     5.018] (II) evdev: Power Button: Configuring as keyboard
[     5.018] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[     5.018] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     5.018] (**) Option "xkb_rules" "evdev"
[     5.018] (**) Option "xkb_model" "pc105"
[     5.018] (**) Option "xkb_layout" "us"
[     5.018] (**) Option "xkb_variant" "intl"
[     5.019] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[     5.019] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[     5.019] (II) Using input driver 'evdev' for 'Sleep Button'
[     5.019] (**) Sleep Button: always reports core events
[     5.019] (**) evdev: Sleep Button: Device: "/dev/input/event0"
[     5.019] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[     5.019] (--) evdev: Sleep Button: Found keys
[     5.019] (II) evdev: Sleep Button: Configuring as keyboard
[     5.019] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"
[     5.019] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[     5.019] (**) Option "xkb_rules" "evdev"
[     5.019] (**) Option "xkb_model" "pc105"
[     5.019] (**) Option "xkb_layout" "us"
[     5.019] (**) Option "xkb_variant" "intl"
[     5.019] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[     5.019] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     5.019] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event6)
[     5.019] (II) No input driver specified, ignoring this device.
[     5.019] (II) This device may have been added with another device file.
[     5.020] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event7)
[     5.020] (II) No input driver specified, ignoring this device.
[     5.020] (II) This device may have been added with another device file.
[     5.020] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event8)
[     5.020] (II) No input driver specified, ignoring this device.
[     5.020] (II) This device may have been added with another device file.
[     5.020] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event3)
[     5.020] (II) No input driver specified, ignoring this device.
[     5.020] (II) This device may have been added with another device file.
[     5.020] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event4)
[     5.020] (II) No input driver specified, ignoring this device.
[     5.020] (II) This device may have been added with another device file.
[     5.246] (II) intel(0): EDID vendor "DEL", prod id 16498
[     5.246] (II) intel(0): Using EDID range info for horizontal sync
[     5.246] (II) intel(0): Using EDID range info for vertical refresh
[     5.246] (II) intel(0): Printing DDC gathered Modelines:
[     5.246] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     5.246] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     5.246] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     5.246] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     5.246] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     5.246] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     5.246] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     5.246] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     5.246] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     5.246] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     5.246] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     5.246] (II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)



```

kern.log

```
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Initializing cgroup subsys cpusetOct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Initializing cgroup subsys cpuacct
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Linux version 4.1.6-040106-generic (kernel@gomeisa) (gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04) ) #201508170230 SMP Mon Aug 17 06:32:14 UTC 2015
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.1.6-040106-generic root=UUID=c456624b-f6c2-4dc7-bf92-640922e83f77 ro quiet splash vt.handoff=7
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] KERNEL supported cpus:
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   Intel GenuineIntel
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   AMD AuthenticAMD
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   Centaur CentaurHauls
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009efff] usable
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000d1f50fff] usable
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d1f51000-0x00000000d2230fff] reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d2231000-0x00000000d62ecfff] usable
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d62ed000-0x00000000d6332fff] reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d6333000-0x00000000d6521fff] usable
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d6522000-0x00000000d6ca0fff] ACPI NVS
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d6ca1000-0x00000000d6f8afff] reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d6f8b000-0x00000000d6ffdfff] type 20
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d6ffe000-0x00000000d6ffefff] usable
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000d7800000-0x00000000dfffffff] reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011effffff] usable
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] NX (Execute Disable) protection: active
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] efi: EFI v2.40 by American Megatrends
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] efi:  ACPI=0xd6c66000  ACPI 2.0=0xd6c66000  SMBIOS=0xf05b0  MPS=0xfd640 
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] SMBIOS 2.8 present.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] DMI: GIGABYTE GB-BXCE-3205/MQLPCAP-00, BIOS F3 02/25/2015
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] AGP: No AGP bridge found
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] e820: last_pfn = 0x11f000 max_arch_pfn = 0x400000000
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] MTRR default type: uncachable
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] MTRR fixed ranges enabled:
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   00000-9FFFF write-back
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   A0000-BFFFF uncachable
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   C0000-FFFFF write-protect
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] MTRR variable ranges enabled:
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   0 base 0000000000 mask 7F80000000 write-back
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   1 base 0080000000 mask 7FC0000000 write-back
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   2 base 00C0000000 mask 7FF0000000 write-back
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   3 base 00D0000000 mask 7FFC000000 write-back
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   4 base 00D4000000 mask 7FFE000000 write-back
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   5 base 00D6000000 mask 7FFF000000 write-back
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   6 base 0100000000 mask 7FE0000000 write-back
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   7 base 011F000000 mask 7FFF000000 uncachable
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   8 disabled
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   9 disabled
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] original variable MTRRs
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] reg 2, base: 3GB, range: 256MB, type WB
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] reg 3, base: 3328MB, range: 64MB, type WB
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] reg 4, base: 3392MB, range: 32MB, type WB
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] reg 5, base: 3424MB, range: 16MB, type WB
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] reg 6, base: 4GB, range: 512MB, type WB
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] reg 7, base: 4592MB, range: 16MB, type UC
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] total RAM covered: 3936M
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Found optimal setting for mtrr clean up
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 7      lose cover RAM: 0G
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] New variable MTRRs
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] reg 2, base: 3GB, range: 256MB, type WB
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] reg 3, base: 3328MB, range: 128MB, type WB
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] reg 4, base: 3440MB, range: 16MB, type UC
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] reg 5, base: 4GB, range: 512MB, type WB
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] reg 6, base: 4592MB, range: 16MB, type UC
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] e820: update [mem 0xd7000000-0xffffffff] usable ==> reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] e820: last_pfn = 0xd6fff max_arch_pfn = 0x400000000
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] found SMP MP-table at [mem 0x000fd840-0x000fd84f] mapped at [ffff8800000fd840]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Using GB pages for direct mapping
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BRK [0x02fe9000, 0x02fe9fff] PGTABLE
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BRK [0x02fea000, 0x02feafff] PGTABLE
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BRK [0x02feb000, 0x02febfff] PGTABLE
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] init_memory_mapping: [mem 0x11ee00000-0x11effffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]  [mem 0x11ee00000-0x11effffff] page 2M
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BRK [0x02fec000, 0x02fecfff] PGTABLE
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x11edfffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]  [mem 0x100000000-0x11edfffff] page 2M
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] init_memory_mapping: [mem 0xc0000000-0xd1f50fff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]  [mem 0xc0000000-0xd1dfffff] page 2M
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]  [mem 0xd1e00000-0xd1f50fff] page 4k
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BRK [0x02fed000, 0x02fedfff] PGTABLE
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] BRK [0x02fee000, 0x02feefff] PGTABLE
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] init_memory_mapping: [mem 0xd2231000-0xd62ecfff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]  [mem 0xd2231000-0xd23fffff] page 4k
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]  [mem 0xd2400000-0xd61fffff] page 2M
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]  [mem 0xd6200000-0xd62ecfff] page 4k
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] init_memory_mapping: [mem 0xd6333000-0xd6521fff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]  [mem 0xd6333000-0xd6521fff] page 4k
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] init_memory_mapping: [mem 0xd6ffe000-0xd6ffefff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]  [mem 0xd6ffe000-0xd6ffefff] page 4k
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xbfffffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] RAMDISK: [mem 0x35b68000-0x36dabfff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: Early table checksum verification disabled
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: RSDP 0x00000000D6C66000 000024 (v02 ALASKA)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: XSDT 0x00000000D6C66098 0000AC (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: FACP 0x00000000D6C7A748 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: DSDT 0x00000000D6C661D8 014569 (v02 ALASKA A M I    01072009 INTL 20120913)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: FACS 0x00000000D6C9FF80 000040
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: APIC 0x00000000D6C7A858 000068 (v03 ALASKA A M I    01072009 AMI  00010013)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: FPDT 0x00000000D6C7A8C0 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: FIDT 0x00000000D6C7A908 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: MCFG 0x00000000D6C7A9A8 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: HPET 0x00000000D6C7A9E8 000038 (v01 ALASKA A M I    01072009 AMI. 00000005)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: SSDT 0x00000000D6C7AA20 000315 (v01 SataRe SataTabl 00001000 INTL 20120913)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: UEFI 0x00000000D6C7AD38 000042 (v01                 00000000      00000000)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: SSDT 0x00000000D6C7AD80 000C7D (v02 Ther_R Ther_Rvp 00001000 INTL 20120913)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: ASF! 0x00000000D6C7BA00 0000A0 (v32 INTEL   HCG     00000001 TFSM 000F4240)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: SSDT 0x00000000D6C7BAA0 0004B5 (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: SSDT 0x00000000D6C7BF58 000B74 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: TPM2 0x00000000D6C7CAD0 000034 (v03        Tpm2Tabl 00000001 AMI  00000000)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: SSDT 0x00000000D6C7CB08 000041 (v01 Ssdt   PttSsdt  00001000 INTL 20120913)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: SSDT 0x00000000D6C7CB50 005CF6 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: DMAR 0x00000000D6C82848 0000B0 (v01 INTEL  BDW      00000001 INTL 00000001)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: BGRT 0x00000000D6C828F8 000038 (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] No NUMA configuration found
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011effffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x11eff7000-0x11effbfff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011a800000-ffff88011e5fffff] on node 0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Zone ranges:
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   Normal   [mem 0x0000000100000000-0x000000011effffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Movable zone start for each node
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Early memory node ranges
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000057fff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   node   0: [mem 0x0000000000059000-0x000000000009efff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   node   0: [mem 0x0000000000100000-0x00000000d1f50fff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   node   0: [mem 0x00000000d2231000-0x00000000d62ecfff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   node   0: [mem 0x00000000d6333000-0x00000000d6521fff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   node   0: [mem 0x00000000d6ffe000-0x00000000d6ffefff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   node   0: [mem 0x0000000100000000-0x000000011effffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000011effffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] On node 0 totalpages: 1003930
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   DMA zone: 25 pages reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   DMA zone: 3997 pages, LIFO batch:0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   DMA32 zone: 13640 pages used for memmap
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   DMA32 zone: 872957 pages, LIFO batch:31
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   Normal zone: 1984 pages used for memmap
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]   Normal zone: 126976 pages, LIFO batch:31
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Reserving Intel graphics stolen memory at 0xd8000000-0xdfffffff
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1808
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0xa4])
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl edge lint[0x0])
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd1f51000-0xd2230fff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd62ed000-0xd6332fff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd6522000-0xd6ca0fff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd6ca1000-0xd6f8afff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd6f8b000-0xd6ffdfff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd6fff000-0xd77fffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd7800000-0xdfffffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xf7ffffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] e820: [mem 0xe0000000-0xf7ffffff] available for PCI devices
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] clocksource refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PERCPU: Embedded 34 pages/cpu @ffff88011ec00000 s100376 r8192 d30696 u1048576
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] pcpu-alloc: s100376 r8192 d30696 u1048576 alloc=1*2097152
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 988217
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Policy zone: Normal
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.1.6-040106-generic root=UUID=c456624b-f6c2-4dc7-bf92-640922e83f77 ro quiet splash vt.handoff=7
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240 using standard form
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] AGP: Checking aperture...
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] AGP: No AGP bridge found
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Memory: 3793632K/4015720K available (8056K kernel code, 1243K rwdata, 3780K rodata, 1424K init, 1292K bss, 222088K reserved, 0K cma-reserved)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Hierarchical RCU implementation.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=2
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] NR_IRQS:16640 nr_irqs:512 16
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-1.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] Console: colour dummy device 80x25
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] console [tty0] enabled
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] clocksource hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] hpet clockevent registered
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000000] tsc: Detected 1496.549 MHz processor
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000043] Calibrating delay loop (skipped), value calculated using timer frequency.. 2993.09 BogoMIPS (lpj=5986196)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000048] pid_max: default: 32768 minimum: 301
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.000055] ACPI: Core revision 20150410
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.026524] ACPI: All ACPI Tables successfully acquired
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.027427] Security Framework initialized
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.027441] AppArmor: AppArmor initialized
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.027442] Yama: becoming mindful.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.027863] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.029091] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.029643] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.029653] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.029912] Initializing cgroup subsys blkio
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.029915] Initializing cgroup subsys memory
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.029924] Initializing cgroup subsys devices
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.029927] Initializing cgroup subsys freezer
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.029932] Initializing cgroup subsys net_cls
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.029934] Initializing cgroup subsys perf_event
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.029937] Initializing cgroup subsys net_prio
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.029939] Initializing cgroup subsys hugetlb
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.029973] CPU: Physical Processor ID: 0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.029974] CPU: Processor Core ID: 0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.029980] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.029981] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.031298] mce: CPU supports 7 MCE banks
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.031316] CPU0: Thermal monitoring enabled (TM1)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.031327] process: using mwait in idle threads
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.031331] Last level iTLB entries: 4KB 128, 2MB 8, 4MB 8
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.031333] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.031538] Freeing SMP alternatives memory: 32K (ffffffff81e9c000 - ffffffff81ea4000)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.035897] ftrace: allocating 30366 entries in 119 pages
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.054544] dmar: Host address width 39
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.054548] dmar: DRHD base: 0x000000fed90000 flags: 0x0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.054564] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e1ff0505e
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.054567] dmar: DRHD base: 0x000000fed91000 flags: 0x1
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.054574] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.054576] dmar: RMRR base: 0x000000d6ee3000 end: 0x000000d6ef1fff
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.054578] dmar: RMRR base: 0x000000d7800000 end: 0x000000dfffffff
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.054581] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.054582] HPET id 0 under DRHD base 0xfed91000
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.055017] x2apic is disabled because BIOS sets x2apic opt out bit. You can use 'intremap=no_x2apic_optout' to override the BIOS setting.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.055032] Enabled IRQ remapping in xapic mode
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.055033] x2apic: IRQ remapping doesn't support X2APIC mode
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.055698] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.095374] TSC deadline timer enabled
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.095379] smpboot: CPU0: Intel(R) Celeron(R) 3205U @ 1.50GHz (fam: 06, model: 3d, stepping: 04)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.095416] Performance Events: PEBS fmt2+, 16-deep LBR, Broadwell events, full-width counters, Intel PMU driver.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.095445] ... version:                3
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.095447] ... bit width:              48
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.095448] ... generic registers:      8
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.095449] ... value mask:             0000ffffffffffff
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.095451] ... max period:             0000ffffffffffff
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.095452] ... fixed-purpose events:   3
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.095453] ... event mask:             00000007000000ff
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.096620] x86: Booting SMP configuration:
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.096623] .... node  #0, CPUs:      #1
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.111170] x86: Booted up 1 node, 2 CPUs
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.111173] smpboot: Total of 2 processors activated (5986.19 BogoMIPS)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.111212] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.113243] devtmpfs: initialized
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.116177] evm: security.selinux
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.116179] evm: security.SMACK64
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.116180] evm: security.SMACK64EXEC
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.116181] evm: security.SMACK64TRANSMUTE
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.116182] evm: security.SMACK64MMAP
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.116184] evm: security.ima
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.116185] evm: security.capability
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.116264] PM: Registering ACPI NVS region [mem 0xd6522000-0xd6ca0fff] (7860224 bytes)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.116481] clocksource jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.116573] pinctrl core: initialized pinctrl subsystem
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.116707] RTC time: 14:43:01, date: 10/15/15
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.116861] NET: Registered protocol family 16
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.123203] cpuidle: using governor ladder
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.127205] cpuidle: using governor menu
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.127283] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.127285] ACPI: bus type PCI registered
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.127289] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.127379] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.127382] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.127502] PCI: Using configuration type 1 for base access
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.131676] ACPI: Added _OSI(Module Device)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.131679] ACPI: Added _OSI(Processor Device)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.131681] ACPI: Added _OSI(3.0 _SCP Extensions)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.131682] ACPI: Added _OSI(Processor Aggregator Device)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.139879] ACPI: Executed 18 blocks of module-level executable AML code
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.146487] ACPI: Dynamic OEM Table Load:
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.146496] ACPI: SSDT 0xFFFF880119490C00 0003D3 (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.147785] ACPI: Dynamic OEM Table Load:
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.147793] ACPI: SSDT 0xFFFF88011A417800 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.149147] ACPI: Dynamic OEM Table Load:
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.149153] ACPI: SSDT 0xFFFF88011943F600 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.150893] ACPI: Interpreter enabled
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.150904] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150410/hwxface-580)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.150913] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150410/hwxface-580)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.150933] ACPI: (supports S0 S3 S4 S5)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.150935] ACPI: Using IOAPIC for interrupt routing
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.150976] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.153733] ACPI: Power Resource [PG00] (on)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.154245] ACPI: Power Resource [PG01] (on)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.154738] ACPI: Power Resource [PG02] (on)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.167589] ACPI: Power Resource [FN00] (off)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.167692] ACPI: Power Resource [FN01] (off)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.167790] ACPI: Power Resource [FN02] (off)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.167888] ACPI: Power Resource [FN03] (off)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.167985] ACPI: Power Resource [FN04] (off)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.169419] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.169428] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.170162] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.170164] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.170782] PCI host bridge to bus 0000:00
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.170786] pci_bus 0000:00: root bus resource [bus 00-3e]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.170789] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.170791] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.170793] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.170796] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfeafffff window]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.170806] pci 0000:00:00.0: [8086:1604] type 00 class 0x060000
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.170929] pci 0000:00:02.0: [8086:1606] type 00 class 0x030000
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.170944] pci 0000:00:02.0: reg 0x10: [mem 0xf6000000-0xf6ffffff 64bit]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.170953] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.170959] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.171076] pci 0000:00:03.0: [8086:160c] type 00 class 0x040300
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.171087] pci 0000:00:03.0: reg 0x10: [mem 0xf7214000-0xf7217fff 64bit]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.171225] pci 0000:00:14.0: [8086:9cb1] type 00 class 0x0c0330
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.171245] pci 0000:00:14.0: reg 0x10: [mem 0xf7200000-0xf720ffff 64bit]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.171309] pci 0000:00:14.0: PME# supported from D3hot D3cold
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.171376] pci 0000:00:14.0: System wakeup disabled by ACPI
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.171426] pci 0000:00:16.0: [8086:9cba] type 00 class 0x078000
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.171446] pci 0000:00:16.0: reg 0x10: [mem 0xf721c000-0xf721c01f 64bit]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.171513] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.171642] pci 0000:00:1b.0: [8086:9ca0] type 00 class 0x040300
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.171659] pci 0000:00:1b.0: reg 0x10: [mem 0xf7210000-0xf7213fff 64bit]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.171713] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.171791] pci 0000:00:1b.0: System wakeup disabled by ACPI
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.171838] pci 0000:00:1c.0: [8086:9c90] type 01 class 0x060400
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.171904] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172003] pci 0000:00:1c.0: System wakeup disabled by ACPI
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172051] pci 0000:00:1c.2: [8086:9c94] type 01 class 0x060400
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172119] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172213] pci 0000:00:1c.2: System wakeup disabled by ACPI
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172260] pci 0000:00:1c.3: [8086:9c96] type 01 class 0x060400
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172328] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172420] pci 0000:00:1c.3: System wakeup disabled by ACPI
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172473] pci 0000:00:1d.0: [8086:9ca6] type 00 class 0x0c0320
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172493] pci 0000:00:1d.0: reg 0x10: [mem 0xf721a000-0xf721a3ff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172582] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172648] pci 0000:00:1d.0: System wakeup disabled by ACPI
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172698] pci 0000:00:1f.0: [8086:9cc5] type 00 class 0x060100
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172904] pci 0000:00:1f.2: [8086:9c83] type 00 class 0x010601
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172919] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172928] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172936] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172944] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172953] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172961] pci 0000:00:1f.2: reg 0x24: [mem 0xf7219000-0xf72197ff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.172998] pci 0000:00:1f.2: PME# supported from D3hot
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.173096] pci 0000:00:1f.3: [8086:9ca2] type 00 class 0x0c0500
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.173112] pci 0000:00:1f.3: reg 0x10: [mem 0xf7218000-0xf72180ff 64bit]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.173134] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.173319] acpiphp: Slot [1] registered
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.173326] pci 0000:00:1c.0: PCI bridge to [bus 01]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.173422] pci 0000:02:00.0: [8086:08b3] type 00 class 0x028000
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.173458] pci 0000:02:00.0: reg 0x10: [mem 0xf7100000-0xf7101fff 64bit]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.173615] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.173676] pci 0000:02:00.0: System wakeup disabled by ACPI
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.181144] pci 0000:00:1c.2: PCI bridge to [bus 02]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.181151] pci 0000:00:1c.2:   bridge window [mem 0xf7100000-0xf71fffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.181242] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.181263] pci 0000:03:00.0: reg 0x10: [io  0xe000-0xe0ff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.181294] pci 0000:03:00.0: reg 0x18: [mem 0xf7000000-0xf7000fff 64bit]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.181314] pci 0000:03:00.0: reg 0x20: [mem 0xf0000000-0xf0003fff 64bit pref]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.181402] pci 0000:03:00.0: supports D1 D2
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.181404] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.181457] pci 0000:03:00.0: System wakeup disabled by ACPI
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.189157] pci 0000:00:1c.3: PCI bridge to [bus 03]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.189161] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.189165] pci 0000:00:1c.3:   bridge window [mem 0xf7000000-0xf70fffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.189171] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.190191] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.190256] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.190317] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.190375] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.190432] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.190491] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.190551] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.190614] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 10 11 12 14 15)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.191145] ACPI: Enabled 4 GPEs in block 00 to 7F
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.191308] vgaarb: setting as boot device: PCI:0000:00:02.0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.191310] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.191314] vgaarb: loaded
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.191316] vgaarb: bridge control possible 0000:00:02.0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.191599] SCSI subsystem initialized
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.191658] libata version 3.00 loaded.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.191690] ACPI: bus type USB registered
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.191715] usbcore: registered new interface driver usbfs
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.191726] usbcore: registered new interface driver hub
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.191739] usbcore: registered new device driver usb
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.191973] PCI: Using ACPI for IRQ routing
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.193511] PCI: pci_cache_line_size set to 64 bytes
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.193559] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.193562] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.193563] e820: reserve RAM buffer [mem 0xd1f51000-0xd3ffffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.193565] e820: reserve RAM buffer [mem 0xd62ed000-0xd7ffffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.193567] e820: reserve RAM buffer [mem 0xd6522000-0xd7ffffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.193569] e820: reserve RAM buffer [mem 0xd6fff000-0xd7ffffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.193571] e820: reserve RAM buffer [mem 0x11f000000-0x11fffffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.193729] NetLabel: Initializing
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.193731] NetLabel:  domain hash size = 128
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.193732] NetLabel:  protocols = UNLABELED CIPSOv4
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.193747] NetLabel:  unlabeled traffic allowed by default
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.193832] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.193839] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.195881] Switched to clocksource hpet
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.203770] AppArmor: AppArmor Filesystem Enabled
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.203865] pnp: PnP ACPI init
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204179] system 00:00: [io  0x0a00-0x0a2f] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204182] system 00:00: [io  0x0a30-0x0a3f] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204184] system 00:00: [io  0x0a40-0x0a4f] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204189] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204302] system 00:01: [io  0x0680-0x069f] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204305] system 00:01: [io  0xffff] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204307] system 00:01: [io  0xffff] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204309] system 00:01: [io  0xffff] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204312] system 00:01: [io  0x1800-0x18fe] could not be reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204314] system 00:01: [io  0x164e-0x164f] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204317] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204385] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204434] system 00:03: [io  0x1854-0x1857] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204438] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204663] system 00:04: [mem 0xfed1c000-0xfed1ffff] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204666] system 00:04: [mem 0xfed10000-0xfed17fff] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204668] system 00:04: [mem 0xfed18000-0xfed18fff] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204670] system 00:04: [mem 0xfed19000-0xfed19fff] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204673] system 00:04: [mem 0xf8000000-0xfbffffff] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204675] system 00:04: [mem 0xfed20000-0xfed3ffff] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204678] system 00:04: [mem 0xfed90000-0xfed93fff] could not be reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204680] system 00:04: [mem 0xfed45000-0xfed8ffff] could not be reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204683] system 00:04: [mem 0xff000000-0xffffffff] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204685] system 00:04: [mem 0xfee00000-0xfeefffff] could not be reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204688] system 00:04: [mem 0xf7fe0000-0xf7feffff] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204690] system 00:04: [mem 0xf7ff0000-0xf7ffffff] has been reserved
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.204693] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.205269] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.205805] pnp: PnP ACPI: found 6 devices
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212498] clocksource acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212531] pci 0000:00:1c.0: PCI bridge to [bus 01]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212543] pci 0000:00:1c.2: PCI bridge to [bus 02]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212550] pci 0000:00:1c.2:   bridge window [mem 0xf7100000-0xf71fffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212558] pci 0000:00:1c.3: PCI bridge to [bus 03]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212561] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212566] pci 0000:00:1c.3:   bridge window [mem 0xf7000000-0xf70fffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212571] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212578] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212580] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212583] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212585] pci_bus 0000:00: resource 7 [mem 0xe0000000-0xfeafffff window]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212587] pci_bus 0000:02: resource 1 [mem 0xf7100000-0xf71fffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212590] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212592] pci_bus 0000:03: resource 1 [mem 0xf7000000-0xf70fffff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212594] pci_bus 0000:03: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212634] NET: Registered protocol family 2
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212836] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.212933] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.213018] TCP: Hash tables configured (established 32768 bind 32768)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.213053] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.213074] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.213130] NET: Registered protocol family 1
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.213153] pci 0000:00:02.0: Video device with shadowed ROM
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.232010] PCI: CLS 64 bytes, default 64
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.232077] Trying to unpack rootfs image as initramfs...
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.682304] Freeing initrd memory: 18704K (ffff880035b68000 - ffff880036dac000)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.682351] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.682354] software IO TLB [mem 0xca247000-0xce247000] (64MB) mapped at [ffff8800ca247000-ffff8800ce246fff]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.682442] RAPL PMU detected, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.682444] hw unit of domain pp0-core 2^-14 Joules
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.682445] hw unit of domain package 2^-14 Joules
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.682446] hw unit of domain dram 2^-14 Joules
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.682447] hw unit of domain pp1-gpu 2^-14 Joules
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.682543] microcode: CPU0 sig=0x306d4, pf=0x40, revision=0x11
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.682550] microcode: CPU1 sig=0x306d4, pf=0x40, revision=0x11
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.682614] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.682654] Scanning for low memory corruption every 60 seconds
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.683049] futex hash table entries: 512 (order: 3, 32768 bytes)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.683067] Initialise system trusted keyring
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.683087] audit: initializing netlink subsys (disabled)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.683108] audit: type=2000 audit(1444920181.676:1): initialized
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.683587] HugeTLB registered 1 GB page size, pre-allocated 0 pages
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.683589] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.685704] zpool: loaded
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.685707] zbud: loaded
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.685932] VFS: Disk quotas dquot_6.6.0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.685981] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.686577] fuse init (API version 7.23)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.686754] Key type big_key registered
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.687115] Key type asymmetric registered
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.687119] Asymmetric key parser 'x509' registered
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.687167] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 251)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.687204] io scheduler noop registered
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.687210] io scheduler deadline registered (default)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.687252] io scheduler cfq registered
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.687979] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.687984] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.688000] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.688002] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.688006] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.688023] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.688025] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.688029] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.688038] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.688060] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.688115] efifb: probing for efifb
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.688145] efifb: framebuffer at 0xe0000000, mapped to 0xffffc90000800000, using 8128k, total 8128k
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.688146] efifb: mode is 1920x1080x32, linelength=7680, pages=1
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.688148] efifb: scrolling: redraw
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.688150] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.695327] Console: switching to colour frame buffer device 240x67
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.702526] fb0: EFI VGA frame buffer device
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.702541] intel_idle: MWAIT substates: 0x11142120
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.702543] intel_idle: v0.4 model 0x3D
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.702544] intel_idle: lapic_timer_reliable_states 0xffffffff
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.702799] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.702804] ACPI: Sleep Button [SLPB]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.702850] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.702852] ACPI: Power Button [PWRB]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.702898] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.702900] ACPI: Power Button [PWRF]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.703818] thermal LNXTHERM:00: registered as thermal_zone0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.703821] ACPI: Thermal Zone [TZ00] (28 C)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.704066] thermal LNXTHERM:01: registered as thermal_zone1
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.704068] ACPI: Thermal Zone [TZ01] (30 C)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.704175] GHES: HEST is not enabled!
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.704324] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.706342] Linux agpgart interface v0.103
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.708912] brd: module loaded
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.709921] loop: module loaded
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.710179] libphy: Fixed MDIO Bus: probed
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.710184] tun: Universal TUN/TAP device driver, 1.6
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.710186] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.710240] PPP generic driver version 2.4.2
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.710488] xhci_hcd 0000:00:14.0: xHCI Host Controller
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.710495] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.710581] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00009810
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.710588] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.710673] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.710675] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.710677] usb usb1: Product: xHCI Host Controller
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.710679] usb usb1: Manufacturer: Linux 4.1.6-040106-generic xhci-hcd
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.710681] usb usb1: SerialNumber: 0000:00:14.0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.710813] hub 1-0:1.0: USB hub found
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.710826] hub 1-0:1.0: 11 ports detected
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.712617] xhci_hcd 0000:00:14.0: xHCI Host Controller
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.712624] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.712658] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.712661] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.712662] usb usb2: Product: xHCI Host Controller
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.712664] usb usb2: Manufacturer: Linux 4.1.6-040106-generic xhci-hcd
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.712666] usb usb2: SerialNumber: 0000:00:14.0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.712807] hub 2-0:1.0: USB hub found
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.712816] hub 2-0:1.0: 4 ports detected
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.713425] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.713433] ehci-pci: EHCI PCI platform driver
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.713570] ehci-pci 0000:00:1d.0: EHCI Host Controller
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.713578] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 3
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.713590] ehci-pci 0000:00:1d.0: debug port 2
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.717488] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.717503] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf721a000
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.731714] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.731783] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.731785] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.731788] usb usb3: Product: EHCI Host Controller
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.731790] usb usb3: Manufacturer: Linux 4.1.6-040106-generic ehci_hcd
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.731791] usb usb3: SerialNumber: 0000:00:1d.0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.732025] hub 3-0:1.0: USB hub found
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.732033] hub 3-0:1.0: 2 ports detected
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.732202] ehci-platform: EHCI generic platform driver
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.732221] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.732228] ohci-pci: OHCI PCI platform driver
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.732244] ohci-platform: OHCI generic platform driver
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.732255] uhci_hcd: USB Universal Host Controller Interface driver
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    0.732320] i8042: PNP: No PS/2 controller found. Probing ports directly.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.459463] usb 3-1: new high-speed USB device number 2 using ehci-pci
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.679383] tsc: Refined TSC clocksource calibration: 1496.535 MHz
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.679388] clocksource tsc: mask: 0xffffffffffffffff max_cycles: 0x159259799ff, max_idle_ns: 440795263419 ns
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.765995] i8042: No controller found
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.766225] mousedev: PS/2 mouse device common for all mice
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.766744] rtc_cmos 00:02: RTC can wake from S4
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.766905] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.766937] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.766963] i2c /dev entries driver
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.767035] device-mapper: uevent: version 1.0.3
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.767127] device-mapper: ioctl: 4.31.0-ioctl (2015-3-12) initialised: dm-devel@redhat.com
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.767156] Intel P-state driver initializing.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.767242] ledtrig-cpu: registered to indicate activity on CPUs
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.767246] EFI Variables Facility v0.08 2004-May-17
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.769448] PCCT header not found.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.769707] NET: Registered protocol family 10
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.769953] NET: Registered protocol family 17
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.769971] Key type dns_resolver registered
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.770369] Loading compiled-in X.509 certificates
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.771535] Loaded X.509 cert 'Build time autogenerated kernel key: 355479ea572ba7361fe0c75a06c61f90ae79791e'
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.771553] registered taskstats version 1
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.773815] Key type trusted registered
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.777734] Key type encrypted registered
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.777745] AppArmor: AppArmor sha1 policy hashing enabled
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.777750] ima: No TPM chip found, activating TPM-bypass!
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.777774] evm: HMAC attrs: 0x1
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.778267]   Magic number: 3:321:738
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.778389] rtc_cmos 00:02: setting system clock to 2015-10-15 14:43:03 UTC (1444920183)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.778464] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.778466] EDD information not available.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.778582] PM: Hibernation image not present or could not be loaded.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.779023] Freeing unused kernel memory: 1424K (ffffffff81d38000 - ffffffff81e9c000)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.779026] Write protecting the kernel read-only data: 12288k
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.779259] Freeing unused kernel memory: 124K (ffff8800027e1000 - ffff880002800000)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.779391] Freeing unused kernel memory: 316K (ffff880002bb1000 - ffff880002c00000)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.826626] ahci 0000:00:1f.2: version 3.0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.826842] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x1 impl SATA mode
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.826846] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo only pio slum part deso sadm apst 
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.827541] scsi host0: ahci
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.828195] scsi host1: ahci
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.828274] ata1: SATA max UDMA/133 abar m2048@0xf7219000 port 0xf7219100 irq 46
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.828277] ata2: DUMMY
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.831124] sdhci: Secure Digital Host Controller Interface driver
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.831127] sdhci: Copyright(c) Pierre Ossman
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.845871] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.845884] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.852246] r8169 0000:03:00.0 eth0: RTL8168g/8111g at 0xffffc90000782000, fc:aa:14:f1:f4:7b, XID 0c000800 IRQ 47
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.852251] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.883563] r8169 0000:03:00.0 p3p1: renamed from eth0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.896099] usb 3-1: New USB device found, idVendor=8087, idProduct=8001
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.896104] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.896448] hub 3-1:1.0: USB hub found
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.896519] hub 3-1:1.0: 8 ports detected
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    1.931324] usb 1-7: new full-speed USB device number 2 using xhci_hcd
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.060692] usb 1-7: New USB device found, idVendor=8087, idProduct=07dc
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.060696] usb 1-7: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.147253] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.163577] ata1.00: ATA-8: KINGSTON SMS200S330G, 603ABBF0, max UDMA/133
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.163582] ata1.00: 58626288 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.168706] ata1.00: configured for UDMA/133
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.168952] scsi 0:0:0:0: Direct-Access     ATA      KINGSTON SMS200S BBF0 PQ: 0 ANSI: 5
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.169414] sd 0:0:0:0: [sda] 58626288 512-byte logical blocks: (30.0 GB/27.9 GiB)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.169431] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.169484] sd 0:0:0:0: [sda] Write Protect is off
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.169488] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.169509] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.170657]  sda: sda1 sda2 sda3
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.171026] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.203579] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.274168] random: init urandom read with 17 bits of entropy available
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.470601] Adding 4016124k swap on /dev/sda3.  Priority:-1 extents:1 across:4016124k SSFS
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.473080] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.688242] lp: driver loaded but no devices found
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.689168] Switched to clocksource tsc
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    2.782816] hidraw: raw HID events driver (C) Jiri Kosina
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.041473] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.099372] audit: type=1400 audit(1444920184.819:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=423 comm="apparmor_parser"
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.099380] audit: type=1400 audit(1444920184.819:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=423 comm="apparmor_parser"
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.099384] audit: type=1400 audit(1444920184.819:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=423 comm="apparmor_parser"
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.099843] audit: type=1400 audit(1444920184.819:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=423 comm="apparmor_parser"
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.099848] audit: type=1400 audit(1444920184.819:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=423 comm="apparmor_parser"
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.100073] audit: type=1400 audit(1444920184.819:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=423 comm="apparmor_parser"
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.111038] audit: type=1400 audit(1444920184.831:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=426 comm="apparmor_parser"
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.113577] [drm] Initialized drm 1.1.0 20060810
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.123063] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.153366] Intel(R) Wireless WiFi driver for Linux
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.153370] Copyright(c) 2003- 2015 Intel Corporation
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.153431] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.157413] iwlwifi 0000:02:00.0: Unsupported splx structure
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.198210] snd_hda_intel 0000:00:03.0: enabling device (0000 -> 0002)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.199538] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.201564] Bluetooth: Core ver 2.20
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.201586] NET: Registered protocol family 31
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.201589] Bluetooth: HCI device and connection manager initialized
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.201594] Bluetooth: HCI socket layer initialized
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.201597] Bluetooth: L2CAP socket layer initialized
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.201604] Bluetooth: SCO socket layer initialized
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.206947] iwlwifi 0000:02:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.238826] [drm] Memory usable by graphics device = 4096M
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.238832] checking generic (e0000000 7f0000) vs hw (e0000000 10000000)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.238834] fb: switching to inteldrmfb from EFI VGA
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.238883] Console: switching to colour dummy device 80x25
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.239000] [drm] Replacing VGA console driver
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.240934] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC283: line_outs=1 (0x21/0x0/0x0/0x0/0x0) type:hp
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.240938] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.240940] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.240942] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.240944] snd_hda_codec_realtek hdaudioC1D0:    inputs:
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.240946] snd_hda_codec_realtek hdaudioC1D0:      Mic=0x19
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.253038] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.253042] [drm] Driver supports precise vblank timestamp query.
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.253167] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.266330] r8169 0000:03:00.0 p3p1: link down
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.266413] r8169 0000:03:00.0 p3p1: link down
Oct 15 16:43:04 hoogstraat-client-1 kernel: [    3.267608] IPv6: ADDRCONF(NETDEV_UP): p3p1: link is not ready
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.279383] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.279940] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.280488] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.287753] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input3
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.287876] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input4
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.288345] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.289955] acpi device:10: registered as cooling_device7
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.290717] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.291607] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.291614] [drm] Initialized i915 1.6.0 20150327 for 0000:00:02.0 on minor 0
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.295256] fbcon: inteldrmfb (fb0) is primary device
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.325861] usbcore: registered new interface driver btusb
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.350639] Bluetooth: hci0: read Intel version: 3707100100012d0d0a
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.350640] Bluetooth: hci0: Intel device is already patched. patch num: 0a
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.352982] Console: switching to colour frame buffer device 240x67
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.360313] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.360315] i915 0000:00:02.0: registered panic notifier
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.415289] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input6
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.415485] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input7
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.415610] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input8
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.424805] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.616919] intel_rapl: Found RAPL domain package
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.616920] intel_rapl: Found RAPL domain core
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.616922] intel_rapl: Found RAPL domain dram
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.836925] audit: type=1400 audit(1444920185.555:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=780 comm="apparmor_parser"
Oct 15 16:43:05 hoogstraat-client-1 kernel: [    3.836933] audit: type=1400 audit(1444920185.555:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=780 comm="apparmor_parser"
Oct 15 16:43:06 hoogstraat-client-1 kernel: [    4.305310] random: nonblocking pool is initialized
Oct 15 16:43:07 hoogstraat-client-1 kernel: [    5.746061] r8169 0000:03:00.0 p3p1: link up
Oct 15 16:43:07 hoogstraat-client-1 kernel: [    5.746072] IPv6: ADDRCONF(NETDEV_CHANGE): p3p1: link becomes ready
Oct 15 16:43:08 hoogstraat-client-1 kernel: [    6.273740] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:43:11 hoogstraat-client-1 kernel: [    9.425800] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:43:14 hoogstraat-client-1 kernel: [   12.575522] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:43:17 hoogstraat-client-1 kernel: [   15.726327] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:43:20 hoogstraat-client-1 kernel: [   18.877192] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:43:23 hoogstraat-client-1 kernel: [   22.029385] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:43:26 hoogstraat-client-1 kernel: [   25.181898] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:43:30 hoogstraat-client-1 kernel: [   28.334324] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:43:33 hoogstraat-client-1 kernel: [   31.486762] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:43:36 hoogstraat-client-1 kernel: [   34.639129] cfg80211: Calling CRDA to update world regulatory domain
Oct 15 16:43:39 hoogstraat-client-1 kernel: [   37.791643] cfg80211: Exceeded CRDA call max attempts. Not calling CRDA



```

boot.log

```
 * Starting Mount filesystems on boot[234G[ OK ] * Stopping Track if upstart is running in a container[234G[ OK ]
 * Starting Initialize or finalize resolvconf[234G[ OK ]
 * Starting Signal sysvinit that the rootfs is mounted[234G[ OK ]
 * Starting set console keymap[234G[ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted[234G[ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted[234G[ OK ]
 * Starting Bridge udev events into upstart[234G[ OK ]
 * Starting device node and kernel event manager[234G[ OK ]
 * Starting Signal sysvinit that remote filesystems are mounted[234G[ OK ]
 * Stopping set console keymap[234G[ OK ]
 * Starting load modules from /etc/modules[234G[ OK ]
 * Starting cold plug devices[234G[ OK ]
 * Starting log initial device creation[234G[ OK ]
 * Starting Clean /tmp directory[234G[ OK ]
 * Stopping load modules from /etc/modules[234G[ OK ]
 * Stopping Clean /tmp directory[234G[ OK ]
 * Starting Signal sysvinit that local filesystems are mounted[234G[ OK ]
 * Stopping Mount filesystems on boot[234G[ OK ]
 * Starting flush early job output to logs[234G[ OK ]
 * Starting D-Bus system message bus[234G[ OK ]
 * Stopping flush early job output to logs[234G[ OK ]
 * Starting system logging daemon[234G[ OK ]
 * Starting SystemD login management service[234G[ OK ]
 * Starting Bridge file events into upstart[234G[ OK ]
 * Starting Uncomplicated firewall[234G[ OK ]
 * Starting configure network device security[234G[ OK ]
 * Starting Mount network filesystems[234G[ OK ]
 * Starting configure network device[234G[ OK ]
 * Stopping Mount network filesystems[234G[ OK ]
 * Starting configure network device security[234G[ OK ]
 * Starting Mount network filesystems[234G[ OK ]
 * Starting Failsafe Boot Delay[234G[ OK ]
 * Stopping Mount network filesystems[234G[ OK ]
 * Stopping Failsafe Boot Delay[234G[ OK ]
 * Starting System V initialisation compatibility[234G[ OK ]
 * Stopping cold plug devices[234G[ OK ]
 * Stopping log initial device creation[234G[ OK ]




X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
Current Operating System: Linux hoogstraat-client-1 4.1.6-040106-generic #201508170230 SMP Mon Aug 17 06:32:14 UTC 2015 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.1.6-040106-generic root=UUID=c456624b-f6c2-4dc7-bf92-640922e83f77 ro quiet splash vt.handoff=7
Build Date: 12 February 2015  02:49:29PM
xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.30.2
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 15 17:56:02 2015
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension Present
Initializing built-in extension DRI3
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
 * Starting configure network device security[234G[ OK ]
Loading extension GLX
 * Starting configure network device[234G[ OK ]
 * Starting set console font[234G[ OK ]
 * Stopping set console font[234G[ OK ]
 * Starting userspace bootsplash[234G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting Send an event to indicate plymouth is up[234G[ OK ]
 * Starting configure virtual network devices[234G[ OK ]
 * Starting AppArmor profiles        * Stopping userspace bootsplash[234G[ OK ]
 * Stopping Send an event to indicate plymouth is up[234G[ OK ]
[240G 
[234G[ OK ]
 * Starting configure network device security[234G[ OK ]
 * Setting up X socket directories...       [240G 
 * Starting configure network device[234G[ OK ]
[234G[ OK ]
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
 * Stopping System V initialisation compatibility[234G[ OK ]
 * Starting System V runlevel compatibility[234G[ OK ]
 * Starting CPU interrupts balancing daemon[234G[ OK ]
 * Starting deferred execution scheduler[234G[ OK ]
 * Starting regular background program processing daemon[234G[ OK ]
 * Starting ACPI daemon[234G[ OK ]
 * Starting save kernel messages[234G[ OK ]
 * Starting OpenSSH server[234G[ OK ]
 * Stopping save kernel messages[234G[ OK ]
 * Starting NTP server ntpd       [240G 
[234G[ OK ]
 * Starting automatic crash report generation[234G[ OK ]
 * Stopping Restore Sound Card State[234G[ OK ]
 * Restoring resolver state...       [240G 
[234G[ OK ]
 * Starting Bridge socket events into upstart[234G[ OK ]
 * Starting web server lighttpd       [240G 
[234G[ OK ]
 * Starting daemon monitor monit       [240G 
[234G[ OK ]
 * Stopping System V runlevel compatibility[234G[ OK ]



```

dmesg

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.1.6-040106-generic (kernel@gomeisa) (gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04) ) #201508170230 SMP Mon Aug 17 06:32:14 UTC 2015
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.1.6-040106-generic root=UUID=c456624b-f6c2-4dc7-bf92-640922e83f77 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000d1f50fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d1f51000-0x00000000d2230fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d2231000-0x00000000d62ecfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d62ed000-0x00000000d6332fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d6333000-0x00000000d6521fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d6522000-0x00000000d6ca0fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000d6ca1000-0x00000000d6f8afff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d6f8b000-0x00000000d6ffdfff] type 20
[    0.000000] BIOS-e820: [mem 0x00000000d6ffe000-0x00000000d6ffefff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d7800000-0x00000000dfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.40 by American Megatrends
[    0.000000] efi:  ACPI=0xd6c66000  ACPI 2.0=0xd6c66000  SMBIOS=0xf05b0  MPS=0xfd640 
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: GIGABYTE GB-BXCE-3205/MQLPCAP-00, BIOS F3 02/25/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x11f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7F80000000 write-back
[    0.000000]   1 base 0080000000 mask 7FC0000000 write-back
[    0.000000]   2 base 00C0000000 mask 7FF0000000 write-back
[    0.000000]   3 base 00D0000000 mask 7FFC000000 write-back
[    0.000000]   4 base 00D4000000 mask 7FFE000000 write-back
[    0.000000]   5 base 00D6000000 mask 7FFF000000 write-back
[    0.000000]   6 base 0100000000 mask 7FE0000000 write-back
[    0.000000]   7 base 011F000000 mask 7FFF000000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3328MB, range: 64MB, type WB
[    0.000000] reg 4, base: 3392MB, range: 32MB, type WB
[    0.000000] reg 5, base: 3424MB, range: 16MB, type WB
[    0.000000] reg 6, base: 4GB, range: 512MB, type WB
[    0.000000] reg 7, base: 4592MB, range: 16MB, type UC
[    0.000000] total RAM covered: 3936M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 7      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3328MB, range: 128MB, type WB
[    0.000000] reg 4, base: 3440MB, range: 16MB, type UC
[    0.000000] reg 5, base: 4GB, range: 512MB, type WB
[    0.000000] reg 6, base: 4592MB, range: 16MB, type UC
[    0.000000] e820: update [mem 0xd7000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xd6fff max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd840-0x000fd84f] mapped at [ffff8800000fd840]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02fe9000, 0x02fe9fff] PGTABLE
[    0.000000] BRK [0x02fea000, 0x02feafff] PGTABLE
[    0.000000] BRK [0x02feb000, 0x02febfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x11ee00000-0x11effffff]
[    0.000000]  [mem 0x11ee00000-0x11effffff] page 2M
[    0.000000] BRK [0x02fec000, 0x02fecfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x100000000-0x11edfffff]
[    0.000000]  [mem 0x100000000-0x11edfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0xc0000000-0xd1f50fff]
[    0.000000]  [mem 0xc0000000-0xd1dfffff] page 2M
[    0.000000]  [mem 0xd1e00000-0xd1f50fff] page 4k
[    0.000000] BRK [0x02fed000, 0x02fedfff] PGTABLE
[    0.000000] BRK [0x02fee000, 0x02feefff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xd2231000-0xd62ecfff]
[    0.000000]  [mem 0xd2231000-0xd23fffff] page 4k
[    0.000000]  [mem 0xd2400000-0xd61fffff] page 2M
[    0.000000]  [mem 0xd6200000-0xd62ecfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xd6333000-0xd6521fff]
[    0.000000]  [mem 0xd6333000-0xd6521fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xd6ffe000-0xd6ffefff]
[    0.000000]  [mem 0xd6ffe000-0xd6ffefff] page 4k
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbfffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35b68000-0x36dabfff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000D6C66000 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0x00000000D6C66098 0000AC (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000D6C7A748 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000D6C661D8 014569 (v02 ALASKA A M I    01072009 INTL 20120913)
[    0.000000] ACPI: FACS 0x00000000D6C9FF80 000040
[    0.000000] ACPI: APIC 0x00000000D6C7A858 000068 (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x00000000D6C7A8C0 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x00000000D6C7A908 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x00000000D6C7A9A8 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000D6C7A9E8 000038 (v01 ALASKA A M I    01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 0x00000000D6C7AA20 000315 (v01 SataRe SataTabl 00001000 INTL 20120913)
[    0.000000] ACPI: UEFI 0x00000000D6C7AD38 000042 (v01                 00000000      00000000)
[    0.000000] ACPI: SSDT 0x00000000D6C7AD80 000C7D (v02 Ther_R Ther_Rvp 00001000 INTL 20120913)
[    0.000000] ACPI: ASF! 0x00000000D6C7BA00 0000A0 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] ACPI: SSDT 0x00000000D6C7BAA0 0004B5 (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000D6C7BF58 000B74 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
[    0.000000] ACPI: TPM2 0x00000000D6C7CAD0 000034 (v03        Tpm2Tabl 00000001 AMI  00000000)
[    0.000000] ACPI: SSDT 0x00000000D6C7CB08 000041 (v01 Ssdt   PttSsdt  00001000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000D6C7CB50 005CF6 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
[    0.000000] ACPI: DMAR 0x00000000D6C82848 0000B0 (v01 INTEL  BDW      00000001 INTL 00000001)
[    0.000000] ACPI: BGRT 0x00000000D6C828F8 000038 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011effffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x11eff7000-0x11effbfff]
[    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011a800000-ffff88011e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000011effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000057fff]
[    0.000000]   node   0: [mem 0x0000000000059000-0x000000000009efff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000d1f50fff]
[    0.000000]   node   0: [mem 0x00000000d2231000-0x00000000d62ecfff]
[    0.000000]   node   0: [mem 0x00000000d6333000-0x00000000d6521fff]
[    0.000000]   node   0: [mem 0x00000000d6ffe000-0x00000000d6ffefff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000011effffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000011effffff]
[    0.000000] On node 0 totalpages: 1003930
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 25 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13640 pages used for memmap
[    0.000000]   DMA32 zone: 872957 pages, LIFO batch:31
[    0.000000]   Normal zone: 1984 pages used for memmap
[    0.000000]   Normal zone: 126976 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0xd8000000-0xdfffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0xa4])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl edge lint[0x0])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xd1f51000-0xd2230fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd62ed000-0xd6332fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd6522000-0xd6ca0fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd6ca1000-0xd6f8afff]
[    0.000000] PM: Registered nosave memory: [mem 0xd6f8b000-0xd6ffdfff]
[    0.000000] PM: Registered nosave memory: [mem 0xd6fff000-0xd77fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xd7800000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xe0000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 34 pages/cpu @ffff88011ec00000 s100376 r8192 d30696 u1048576
[    0.000000] pcpu-alloc: s100376 r8192 d30696 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 988217
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.1.6-040106-generic root=UUID=c456624b-f6c2-4dc7-bf92-640922e83f77 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240 using standard form
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3793632K/4015720K available (8056K kernel code, 1243K rwdata, 3780K rodata, 1424K init, 1292K bss, 222088K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=2
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-1.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] tsc: Detected 1496.534 MHz processor
[    0.000043] Calibrating delay loop (skipped), value calculated using timer frequency.. 2993.06 BogoMIPS (lpj=5986136)
[    0.000047] pid_max: default: 32768 minimum: 301
[    0.000054] ACPI: Core revision 20150410
[    0.026456] ACPI: All ACPI Tables successfully acquired
[    0.027362] Security Framework initialized
[    0.027375] AppArmor: AppArmor initialized
[    0.027377] Yama: becoming mindful.
[    0.027795] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.029018] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.029569] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.029578] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.029837] Initializing cgroup subsys blkio
[    0.029840] Initializing cgroup subsys memory
[    0.029849] Initializing cgroup subsys devices
[    0.029852] Initializing cgroup subsys freezer
[    0.029855] Initializing cgroup subsys net_cls
[    0.029858] Initializing cgroup subsys perf_event
[    0.029860] Initializing cgroup subsys net_prio
[    0.029863] Initializing cgroup subsys hugetlb
[    0.029897] CPU: Physical Processor ID: 0
[    0.029899] CPU: Processor Core ID: 0
[    0.029904] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.029906] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.031223] mce: CPU supports 7 MCE banks
[    0.031240] CPU0: Thermal monitoring enabled (TM1)
[    0.031251] process: using mwait in idle threads
[    0.031255] Last level iTLB entries: 4KB 128, 2MB 8, 4MB 8
[    0.031257] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.031462] Freeing SMP alternatives memory: 32K (ffffffff81e9c000 - ffffffff81ea4000)
[    0.035825] ftrace: allocating 30366 entries in 119 pages
[    0.054419] dmar: Host address width 39
[    0.054423] dmar: DRHD base: 0x000000fed90000 flags: 0x0
[    0.054439] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e1ff0505e
[    0.054441] dmar: DRHD base: 0x000000fed91000 flags: 0x1
[    0.054448] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
[    0.054450] dmar: RMRR base: 0x000000d6ee3000 end: 0x000000d6ef1fff
[    0.054452] dmar: RMRR base: 0x000000d7800000 end: 0x000000dfffffff
[    0.054455] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.054457] HPET id 0 under DRHD base 0xfed91000
[    0.054892] x2apic is disabled because BIOS sets x2apic opt out bit. You can use 'intremap=no_x2apic_optout' to override the BIOS setting.
[    0.054907] Enabled IRQ remapping in xapic mode
[    0.054909] x2apic: IRQ remapping doesn't support X2APIC mode
[    0.055573] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.095249] TSC deadline timer enabled
[    0.095252] smpboot: CPU0: Intel(R) Celeron(R) 3205U @ 1.50GHz (fam: 06, model: 3d, stepping: 04)
[    0.095290] Performance Events: PEBS fmt2+, 16-deep LBR, Broadwell events, full-width counters, Intel PMU driver.
[    0.095320] ... version:                3
[    0.095321] ... bit width:              48
[    0.095322] ... generic registers:      8
[    0.095323] ... value mask:             0000ffffffffffff
[    0.095325] ... max period:             0000ffffffffffff
[    0.095326] ... fixed-purpose events:   3
[    0.095327] ... event mask:             00000007000000ff
[    0.096497] x86: Booting SMP configuration:
[    0.096499] .... node  #0, CPUs:      #1
[    0.111044] x86: Booted up 1 node, 2 CPUs
[    0.111047] smpboot: Total of 2 processors activated (5986.13 BogoMIPS)
[    0.111087] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.113114] devtmpfs: initialized
[    0.116271] evm: security.selinux
[    0.116273] evm: security.SMACK64
[    0.116275] evm: security.SMACK64EXEC
[    0.116276] evm: security.SMACK64TRANSMUTE
[    0.116277] evm: security.SMACK64MMAP
[    0.116278] evm: security.ima
[    0.116279] evm: security.capability
[    0.116355] PM: Registering ACPI NVS region [mem 0xd6522000-0xd6ca0fff] (7860224 bytes)
[    0.116575] clocksource jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.116667] pinctrl core: initialized pinctrl subsystem
[    0.116803] RTC time: 15:55:58, date: 10/15/15
[    0.116958] NET: Registered protocol family 16
[    0.123077] cpuidle: using governor ladder
[    0.127079] cpuidle: using governor menu
[    0.127155] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.127157] ACPI: bus type PCI registered
[    0.127159] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.127249] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.127252] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.127371] PCI: Using configuration type 1 for base access
[    0.131547] ACPI: Added _OSI(Module Device)
[    0.131550] ACPI: Added _OSI(Processor Device)
[    0.131552] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.131554] ACPI: Added _OSI(Processor Aggregator Device)
[    0.139732] ACPI: Executed 18 blocks of module-level executable AML code
[    0.146348] ACPI: Dynamic OEM Table Load:
[    0.146357] ACPI: SSDT 0xFFFF880119490C00 0003D3 (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
[    0.147647] ACPI: Dynamic OEM Table Load:
[    0.147654] ACPI: SSDT 0xFFFF88011A417800 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
[    0.149011] ACPI: Dynamic OEM Table Load:
[    0.149016] ACPI: SSDT 0xFFFF88011943F600 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
[    0.150758] ACPI: Interpreter enabled
[    0.150769] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150410/hwxface-580)
[    0.150778] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150410/hwxface-580)
[    0.150798] ACPI: (supports S0 S3 S4 S5)
[    0.150800] ACPI: Using IOAPIC for interrupt routing
[    0.150842] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.153611] ACPI: Power Resource [PG00] (on)
[    0.154123] ACPI: Power Resource [PG01] (on)
[    0.154613] ACPI: Power Resource [PG02] (on)
[    0.167468] ACPI: Power Resource [FN00] (off)
[    0.167571] ACPI: Power Resource [FN01] (off)
[    0.167670] ACPI: Power Resource [FN02] (off)
[    0.167767] ACPI: Power Resource [FN03] (off)
[    0.167864] ACPI: Power Resource [FN04] (off)
[    0.169301] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.169309] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.170048] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.170050] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.170669] PCI host bridge to bus 0000:00
[    0.170673] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.170676] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.170678] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.170681] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.170683] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfeafffff window]
[    0.170693] pci 0000:00:00.0: [8086:1604] type 00 class 0x060000
[    0.170819] pci 0000:00:02.0: [8086:1606] type 00 class 0x030000
[    0.170834] pci 0000:00:02.0: reg 0x10: [mem 0xf6000000-0xf6ffffff 64bit]
[    0.170843] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.170849] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.170967] pci 0000:00:03.0: [8086:160c] type 00 class 0x040300
[    0.170978] pci 0000:00:03.0: reg 0x10: [mem 0xf7214000-0xf7217fff 64bit]
[    0.171115] pci 0000:00:14.0: [8086:9cb1] type 00 class 0x0c0330
[    0.171134] pci 0000:00:14.0: reg 0x10: [mem 0xf7200000-0xf720ffff 64bit]
[    0.171199] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.171266] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.171315] pci 0000:00:16.0: [8086:9cba] type 00 class 0x078000
[    0.171335] pci 0000:00:16.0: reg 0x10: [mem 0xf721c000-0xf721c01f 64bit]
[    0.171401] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.171533] pci 0000:00:1b.0: [8086:9ca0] type 00 class 0x040300
[    0.171550] pci 0000:00:1b.0: reg 0x10: [mem 0xf7210000-0xf7213fff 64bit]
[    0.171604] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.171683] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.171730] pci 0000:00:1c.0: [8086:9c90] type 01 class 0x060400
[    0.171796] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.171894] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.171943] pci 0000:00:1c.2: [8086:9c94] type 01 class 0x060400
[    0.172010] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.172104] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.172151] pci 0000:00:1c.3: [8086:9c96] type 01 class 0x060400
[    0.172219] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.172312] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.172365] pci 0000:00:1d.0: [8086:9ca6] type 00 class 0x0c0320
[    0.172384] pci 0000:00:1d.0: reg 0x10: [mem 0xf721a000-0xf721a3ff]
[    0.172474] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.172540] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.172591] pci 0000:00:1f.0: [8086:9cc5] type 00 class 0x060100
[    0.172797] pci 0000:00:1f.2: [8086:9c83] type 00 class 0x010601
[    0.172812] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
[    0.172820] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
[    0.172829] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
[    0.172837] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
[    0.172845] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
[    0.172854] pci 0000:00:1f.2: reg 0x24: [mem 0xf7219000-0xf72197ff]
[    0.172890] pci 0000:00:1f.2: PME# supported from D3hot
[    0.172988] pci 0000:00:1f.3: [8086:9ca2] type 00 class 0x0c0500
[    0.173005] pci 0000:00:1f.3: reg 0x10: [mem 0xf7218000-0xf72180ff 64bit]
[    0.173027] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    0.173213] acpiphp: Slot [1] registered
[    0.173219] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.173315] pci 0000:02:00.0: [8086:08b3] type 00 class 0x028000
[    0.173351] pci 0000:02:00.0: reg 0x10: [mem 0xf7100000-0xf7101fff 64bit]
[    0.173509] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.173570] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.181019] pci 0000:00:1c.2: PCI bridge to [bus 02]
[    0.181026] pci 0000:00:1c.2:   bridge window [mem 0xf7100000-0xf71fffff]
[    0.181117] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    0.181138] pci 0000:03:00.0: reg 0x10: [io  0xe000-0xe0ff]
[    0.181169] pci 0000:03:00.0: reg 0x18: [mem 0xf7000000-0xf7000fff 64bit]
[    0.181189] pci 0000:03:00.0: reg 0x20: [mem 0xf0000000-0xf0003fff 64bit pref]
[    0.181277] pci 0000:03:00.0: supports D1 D2
[    0.181279] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.181333] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.189031] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    0.189035] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    0.189039] pci 0000:00:1c.3:   bridge window [mem 0xf7000000-0xf70fffff]
[    0.189045] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.190064] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.190128] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.190189] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.190247] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.190304] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.190363] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.190423] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.190486] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.191017] ACPI: Enabled 4 GPEs in block 00 to 7F
[    0.191178] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.191181] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.191185] vgaarb: loaded
[    0.191186] vgaarb: bridge control possible 0000:00:02.0
[    0.191471] SCSI subsystem initialized
[    0.191528] libata version 3.00 loaded.
[    0.191561] ACPI: bus type USB registered
[    0.191583] usbcore: registered new interface driver usbfs
[    0.191594] usbcore: registered new interface driver hub
[    0.191607] usbcore: registered new device driver usb
[    0.191838] PCI: Using ACPI for IRQ routing
[    0.193378] PCI: pci_cache_line_size set to 64 bytes
[    0.193425] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
[    0.193427] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.193428] e820: reserve RAM buffer [mem 0xd1f51000-0xd3ffffff]
[    0.193430] e820: reserve RAM buffer [mem 0xd62ed000-0xd7ffffff]
[    0.193432] e820: reserve RAM buffer [mem 0xd6522000-0xd7ffffff]
[    0.193434] e820: reserve RAM buffer [mem 0xd6fff000-0xd7ffffff]
[    0.193436] e820: reserve RAM buffer [mem 0x11f000000-0x11fffffff]
[    0.193596] NetLabel: Initializing
[    0.193598] NetLabel:  domain hash size = 128
[    0.193599] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.193615] NetLabel:  unlabeled traffic allowed by default
[    0.193699] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.193706] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.195748] Switched to clocksource hpet
[    0.203636] AppArmor: AppArmor Filesystem Enabled
[    0.203725] pnp: PnP ACPI init
[    0.204039] system 00:00: [io  0x0a00-0x0a2f] has been reserved
[    0.204042] system 00:00: [io  0x0a30-0x0a3f] has been reserved
[    0.204045] system 00:00: [io  0x0a40-0x0a4f] has been reserved
[    0.204049] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.204164] system 00:01: [io  0x0680-0x069f] has been reserved
[    0.204167] system 00:01: [io  0xffff] has been reserved
[    0.204169] system 00:01: [io  0xffff] has been reserved
[    0.204172] system 00:01: [io  0xffff] has been reserved
[    0.204174] system 00:01: [io  0x1800-0x18fe] could not be reserved
[    0.204176] system 00:01: [io  0x164e-0x164f] has been reserved
[    0.204180] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.204247] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.204297] system 00:03: [io  0x1854-0x1857] has been reserved
[    0.204300] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.204525] system 00:04: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.204528] system 00:04: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.204530] system 00:04: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.204532] system 00:04: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.204535] system 00:04: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.204537] system 00:04: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.204539] system 00:04: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.204542] system 00:04: [mem 0xfed45000-0xfed8ffff] could not be reserved
[    0.204544] system 00:04: [mem 0xff000000-0xffffffff] has been reserved
[    0.204547] system 00:04: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.204549] system 00:04: [mem 0xf7fe0000-0xf7feffff] has been reserved
[    0.204552] system 00:04: [mem 0xf7ff0000-0xf7ffffff] has been reserved
[    0.204555] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.205133] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.205668] pnp: PnP ACPI: found 6 devices
[    0.212352] clocksource acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.212385] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.212398] pci 0000:00:1c.2: PCI bridge to [bus 02]
[    0.212403] pci 0000:00:1c.2:   bridge window [mem 0xf7100000-0xf71fffff]
[    0.212411] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    0.212414] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    0.212419] pci 0000:00:1c.3:   bridge window [mem 0xf7000000-0xf70fffff]
[    0.212424] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.212432] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.212435] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.212437] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.212439] pci_bus 0000:00: resource 7 [mem 0xe0000000-0xfeafffff window]
[    0.212442] pci_bus 0000:02: resource 1 [mem 0xf7100000-0xf71fffff]
[    0.212444] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.212446] pci_bus 0000:03: resource 1 [mem 0xf7000000-0xf70fffff]
[    0.212448] pci_bus 0000:03: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.212489] NET: Registered protocol family 2
[    0.212691] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.212788] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.212870] TCP: Hash tables configured (established 32768 bind 32768)
[    0.212905] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.212925] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.212982] NET: Registered protocol family 1
[    0.213003] pci 0000:00:02.0: Video device with shadowed ROM
[    0.231881] PCI: CLS 64 bytes, default 64
[    0.231949] Trying to unpack rootfs image as initramfs...
[    0.682089] Freeing initrd memory: 18704K (ffff880035b68000 - ffff880036dac000)
[    0.682135] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.682140] software IO TLB [mem 0xca247000-0xce247000] (64MB) mapped at [ffff8800ca247000-ffff8800ce246fff]
[    0.682226] RAPL PMU detected, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
[    0.682228] hw unit of domain pp0-core 2^-14 Joules
[    0.682229] hw unit of domain package 2^-14 Joules
[    0.682230] hw unit of domain dram 2^-14 Joules
[    0.682231] hw unit of domain pp1-gpu 2^-14 Joules
[    0.682324] microcode: CPU0 sig=0x306d4, pf=0x40, revision=0x11
[    0.682332] microcode: CPU1 sig=0x306d4, pf=0x40, revision=0x11
[    0.682395] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.682434] Scanning for low memory corruption every 60 seconds
[    0.682823] futex hash table entries: 512 (order: 3, 32768 bytes)
[    0.682843] Initialise system trusted keyring
[    0.682866] audit: initializing netlink subsys (disabled)
[    0.682884] audit: type=2000 audit(1444924558.672:1): initialized
[    0.683361] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    0.683362] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.685480] zpool: loaded
[    0.685483] zbud: loaded
[    0.685693] VFS: Disk quotas dquot_6.6.0
[    0.685742] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.686343] fuse init (API version 7.23)
[    0.686518] Key type big_key registered
[    0.686861] Key type asymmetric registered
[    0.686865] Asymmetric key parser 'x509' registered
[    0.686914] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 251)
[    0.686947] io scheduler noop registered
[    0.686952] io scheduler deadline registered (default)
[    0.686994] io scheduler cfq registered
[    0.687723] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.687728] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.687744] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    0.687746] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.687750] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    0.687767] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    0.687769] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.687772] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    0.687782] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.687804] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.687859] efifb: probing for efifb
[    0.687889] efifb: framebuffer at 0xe0000000, mapped to 0xffffc90000800000, using 8128k, total 8128k
[    0.687891] efifb: mode is 1920x1080x32, linelength=7680, pages=1
[    0.687892] efifb: scrolling: redraw
[    0.687894] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.694676] Console: switching to colour frame buffer device 240x67
[    0.700824] fb0: EFI VGA frame buffer device
[    0.700839] intel_idle: MWAIT substates: 0x11142120
[    0.700841] intel_idle: v0.4 model 0x3D
[    0.700842] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.701099] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.701104] ACPI: Sleep Button [SLPB]
[    0.701150] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.701152] ACPI: Power Button [PWRB]
[    0.701199] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.701201] ACPI: Power Button [PWRF]
[    0.702111] thermal LNXTHERM:00: registered as thermal_zone0
[    0.702114] ACPI: Thermal Zone [TZ00] (28 C)
[    0.702359] thermal LNXTHERM:01: registered as thermal_zone1
[    0.702361] ACPI: Thermal Zone [TZ01] (30 C)
[    0.702468] GHES: HEST is not enabled!
[    0.702591] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.704632] Linux agpgart interface v0.103
[    0.707120] brd: module loaded
[    0.708182] loop: module loaded
[    0.708436] libphy: Fixed MDIO Bus: probed
[    0.708441] tun: Universal TUN/TAP device driver, 1.6
[    0.708442] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.708508] PPP generic driver version 2.4.2
[    0.708770] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.708778] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.708864] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00009810
[    0.708871] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.708953] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.708955] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.708957] usb usb1: Product: xHCI Host Controller
[    0.708959] usb usb1: Manufacturer: Linux 4.1.6-040106-generic xhci-hcd
[    0.708961] usb usb1: SerialNumber: 0000:00:14.0
[    0.709104] hub 1-0:1.0: USB hub found
[    0.709118] hub 1-0:1.0: 11 ports detected
[    0.710888] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.710893] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.710928] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.710930] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.710932] usb usb2: Product: xHCI Host Controller
[    0.710934] usb usb2: Manufacturer: Linux 4.1.6-040106-generic xhci-hcd
[    0.710936] usb usb2: SerialNumber: 0000:00:14.0
[    0.711064] hub 2-0:1.0: USB hub found
[    0.711074] hub 2-0:1.0: 4 ports detected
[    0.711715] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.711723] ehci-pci: EHCI PCI platform driver
[    0.711864] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.711871] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    0.711883] ehci-pci 0000:00:1d.0: debug port 2
[    0.715775] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.715790] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf721a000
[    0.731620] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.731692] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.731695] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.731697] usb usb3: Product: EHCI Host Controller
[    0.731700] usb usb3: Manufacturer: Linux 4.1.6-040106-generic ehci_hcd
[    0.731701] usb usb3: SerialNumber: 0000:00:1d.0
[    0.731944] hub 3-0:1.0: USB hub found
[    0.731952] hub 3-0:1.0: 2 ports detected
[    0.732122] ehci-platform: EHCI generic platform driver
[    0.732140] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.732148] ohci-pci: OHCI PCI platform driver
[    0.732164] ohci-platform: OHCI generic platform driver
[    0.732175] uhci_hcd: USB Universal Host Controller Interface driver
[    0.732242] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.459331] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    1.679251] tsc: Refined TSC clocksource calibration: 1496.535 MHz
[    1.679256] clocksource tsc: mask: 0xffffffffffffffff max_cycles: 0x159259799ff, max_idle_ns: 440795263419 ns
[    1.765921] i8042: No controller found
[    1.766153] mousedev: PS/2 mouse device common for all mice
[    1.766652] rtc_cmos 00:02: RTC can wake from S4
[    1.766866] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.766902] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.766930] i2c /dev entries driver
[    1.767002] device-mapper: uevent: version 1.0.3
[    1.767100] device-mapper: ioctl: 4.31.0-ioctl (2015-3-12) initialised: dm-devel@redhat.com
[    1.767128] Intel P-state driver initializing.
[    1.767228] ledtrig-cpu: registered to indicate activity on CPUs
[    1.767233] EFI Variables Facility v0.08 2004-May-17
[    1.769420] PCCT header not found.
[    1.769677] NET: Registered protocol family 10
[    1.769907] NET: Registered protocol family 17
[    1.769923] Key type dns_resolver registered
[    1.770306] Loading compiled-in X.509 certificates
[    1.771473] Loaded X.509 cert 'Build time autogenerated kernel key: 355479ea572ba7361fe0c75a06c61f90ae79791e'
[    1.771492] registered taskstats version 1
[    1.773714] Key type trusted registered
[    1.777567] Key type encrypted registered
[    1.777578] AppArmor: AppArmor sha1 policy hashing enabled
[    1.777583] ima: No TPM chip found, activating TPM-bypass!
[    1.777622] evm: HMAC attrs: 0x1
[    1.778117]   Magic number: 3:633:942
[    1.778235] rtc_cmos 00:02: setting system clock to 2015-10-15 15:56:00 UTC (1444924560)
[    1.778311] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.778313] EDD information not available.
[    1.778424] PM: Hibernation image not present or could not be loaded.
[    1.778865] Freeing unused kernel memory: 1424K (ffffffff81d38000 - ffffffff81e9c000)
[    1.778867] Write protecting the kernel read-only data: 12288k
[    1.779107] Freeing unused kernel memory: 124K (ffff8800027e1000 - ffff880002800000)
[    1.779235] Freeing unused kernel memory: 316K (ffff880002bb1000 - ffff880002c00000)
[    1.793625] systemd-udevd[105]: starting version 204
[    1.826360] ahci 0000:00:1f.2: version 3.0
[    1.826579] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x1 impl SATA mode
[    1.826583] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo only pio slum part deso sadm apst 
[    1.827252] scsi host0: ahci
[    1.827361] scsi host1: ahci
[    1.827426] ata1: SATA max UDMA/133 abar m2048@0xf7219000 port 0xf7219100 irq 46
[    1.827428] ata2: DUMMY
[    1.829560] sdhci: Secure Digital Host Controller Interface driver
[    1.829563] sdhci: Copyright(c) Pierre Ossman
[    1.849839] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.849850] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.856117] r8169 0000:03:00.0 eth0: RTL8168g/8111g at 0xffffc90000782000, fc:aa:14:f1:f4:7b, XID 0c000800 IRQ 47
[    1.856122] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.889950] r8169 0000:03:00.0 p3p1: renamed from eth0
[    1.899619] usb 3-1: New USB device found, idVendor=8087, idProduct=8001
[    1.899623] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.899982] hub 3-1:1.0: USB hub found
[    1.900033] hub 3-1:1.0: 8 ports detected
[    1.903420] systemd-udevd[126]: renamed network interface eth0 to p3p1
[    1.931195] usb 1-7: new full-speed USB device number 2 using xhci_hcd
[    2.060558] usb 1-7: New USB device found, idVendor=8087, idProduct=07dc
[    2.060563] usb 1-7: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.147122] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.163969] ata1.00: ATA-8: KINGSTON SMS200S330G, 603ABBF0, max UDMA/133
[    2.163974] ata1.00: 58626288 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.169046] ata1.00: configured for UDMA/133
[    2.169304] scsi 0:0:0:0: Direct-Access     ATA      KINGSTON SMS200S BBF0 PQ: 0 ANSI: 5
[    2.169727] sd 0:0:0:0: [sda] 58626288 512-byte logical blocks: (30.0 GB/27.9 GiB)
[    2.169759] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.169778] sd 0:0:0:0: [sda] Write Protect is off
[    2.169782] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.169798] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.171077]  sda: sda1 sda2 sda3
[    2.171460] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.204303] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    2.271209] random: init urandom read with 19 bits of entropy available
[    2.297621] init: plymouth-upstart-bridge main process (160) terminated with status 1
[    2.297635] init: plymouth-upstart-bridge main process ended, respawning
[    2.307747] init: plymouth-upstart-bridge main process (170) terminated with status 1
[    2.307760] init: plymouth-upstart-bridge main process ended, respawning
[    2.313792] init: plymouth-upstart-bridge main process (173) terminated with status 1
[    2.313804] init: plymouth-upstart-bridge main process ended, respawning
[    2.331434] init: ureadahead main process (163) terminated with status 5
[    2.469335] Adding 4016124k swap on /dev/sda3.  Priority:-1 extents:1 across:4016124k SSFS
[    2.472397] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    2.603663] systemd-udevd[306]: starting version 204
[    2.686064] Switched to clocksource tsc
[    2.687498] lp: driver loaded but no devices found
[    2.809919] hidraw: raw HID events driver (C) Jiri Kosina
[    3.010985] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    3.089104] audit: type=1400 audit(1444924561.808:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=426 comm="apparmor_parser"
[    3.089111] audit: type=1400 audit(1444924561.808:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=426 comm="apparmor_parser"
[    3.089115] audit: type=1400 audit(1444924561.808:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=426 comm="apparmor_parser"
[    3.089574] audit: type=1400 audit(1444924561.808:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=426 comm="apparmor_parser"
[    3.089579] audit: type=1400 audit(1444924561.808:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=426 comm="apparmor_parser"
[    3.089805] audit: type=1400 audit(1444924561.808:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=426 comm="apparmor_parser"
[    3.099483] audit: type=1400 audit(1444924561.820:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=430 comm="apparmor_parser"
[    3.101768] Bluetooth: Core ver 2.20
[    3.104012] NET: Registered protocol family 31
[    3.104017] Bluetooth: HCI device and connection manager initialized
[    3.104023] Bluetooth: HCI socket layer initialized
[    3.104027] Bluetooth: L2CAP socket layer initialized
[    3.104042] Bluetooth: SCO socket layer initialized
[    3.143479] cfg80211: Calling CRDA to update world regulatory domain
[    3.144145] [drm] Initialized drm 1.1.0 20060810
[    3.156638] snd_hda_intel 0000:00:03.0: enabling device (0000 -> 0002)
[    3.156807] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[    3.206603] [drm] Memory usable by graphics device = 4096M
[    3.206612] checking generic (e0000000 7f0000) vs hw (e0000000 10000000)
[    3.206614] fb: switching to inteldrmfb from EFI VGA
[    3.206873] Console: switching to colour dummy device 80x25
[    3.207062] [drm] Replacing VGA console driver
[    3.223892] r8169 0000:03:00.0 p3p1: link down
[    3.224076] r8169 0000:03:00.0 p3p1: link down
[    3.227120] IPv6: ADDRCONF(NETDEV_UP): p3p1: link is not ready
[    3.228773] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.228777] [drm] Driver supports precise vblank timestamp query.
[    3.228908] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.241123] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.242814] acpi device:10: registered as cooling_device7
[    3.242938] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input3
[    3.243103] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    3.243108] [drm] Initialized i915 1.6.0 20150327 for 0000:00:02.0 on minor 0
[    3.249491] usbcore: registered new interface driver btusb
[    3.254782] fbcon: inteldrmfb (fb0) is primary device
[    3.256562] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC283: line_outs=1 (0x21/0x0/0x0/0x0/0x0) type:hp
[    3.256564] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.256565] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.256566] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[    3.256567] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[    3.256569] snd_hda_codec_realtek hdaudioC1D0:      Mic=0x19
[    3.269540] Bluetooth: hci0: read Intel version: 3707100100012d0d0a
[    3.269541] Bluetooth: hci0: Intel device is already patched. patch num: 0a
[    3.303246] Intel(R) Wireless WiFi driver for Linux
[    3.303247] Copyright(c) 2003- 2015 Intel Corporation
[    3.303312] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[    3.306278] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input4
[    3.306444] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input5
[    3.316678] iwlwifi 0000:02:00.0: Unsupported splx structure
[    3.320611] iwlwifi 0000:02:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
[    3.320961] Console: switching to colour frame buffer device 240x67
[    3.328478] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    3.328480] i915 0000:00:02.0: registered panic notifier
[    3.410951] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input6
[    3.411053] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input7
[    3.411178] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input8
[    3.416566] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[    3.416759] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[    3.416985] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[    3.580512] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.583359] intel_rapl: Found RAPL domain package
[    3.583366] intel_rapl: Found RAPL domain core
[    3.583368] intel_rapl: Found RAPL domain dram
[    3.681116] init: failsafe main process (644) killed by TERM signal
[    3.973473] audit: type=1400 audit(1444924562.692:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=855 comm="apparmor_parser"
[    3.992789] audit: type=1400 audit(1444924562.712:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=854 comm="apparmor_parser"
[    4.083123] random: nonblocking pool is initialized



```

---

