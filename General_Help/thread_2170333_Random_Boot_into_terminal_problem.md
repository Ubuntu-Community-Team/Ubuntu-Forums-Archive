---
title: "Random Boot into terminal problem"
date: 2013-08-25
forum: General Help
---

### Post by psilocybin3 on 2013-08-25
Hey guys i am using an acer aspire one
and have been using Xubuntu for 5 months
for the first 3 months i had no problems at all, after a few updates I have the problem that I will randomly boot into a terminal.
and it will ask me to log in. What I notice is this only happens randomly and a simple restart fix's the problem, but this is just a temp fix as it occurs again after a few boots.

I have attached my Xorg.0.log file

```
[    30.232] X.Org X Server 1.11.3
Release Date: 2011-12-16
[    30.232] X Protocol Version 11, Revision 0
[    30.232] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    30.232] Current Operating System: Linux stashb0x 3.2.0-52-generic-pae #78-Ubuntu SMP Fri Jul 26 16:43:19 UTC 2013 i686
[    30.232] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-52-generic-pae root=UUID=331d6d2c-2d1d-48e1-ad62-4e14993a393c ro quiet splash
[    30.232] Build Date: 11 April 2013  01:04:30PM
[    30.232] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support) 
[    30.232] Current version of pixman: 0.24.4
[    30.233]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    30.233] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.233] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug 25 19:47:14 2013
[    30.257] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    30.258] (==) No Layout section.  Using the first Screen section.
[    30.258] (==) No screen section available. Using defaults.
[    30.258] (**) |-->Screen "Default Screen Section" (0)
[    30.258] (**) |   |-->Monitor "<default monitor>"
[    30.258] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    30.258] (==) Automatically adding devices
[    30.258] (==) Automatically enabling devices
[    30.259] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.259]     Entry deleted from font path.
[    30.259] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    30.259]     Entry deleted from font path.
[    30.259] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    30.259]     Entry deleted from font path.
[    30.259] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    30.259]     Entry deleted from font path.
[    30.259] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    30.259]     Entry deleted from font path.
[    30.259] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    30.259]     Entry deleted from font path.
[    30.259] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    30.259] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    30.259] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    30.259] (II) Loader magic: 0xb77ec5a0
[    30.259] (II) Module ABI versions:
[    30.259]     X.Org ANSI C Emulation: 0.4
[    30.259]     X.Org Video Driver: 11.0
[    30.259]     X.Org XInput driver : 16.0
[    30.259]     X.Org Server Extension : 6.0
[    30.261] (--) PCI:*(0:0:2:0) 8086:0be1:1025:061f rev 9, Mem @ 0x46000000/1048576, I/O @ 0x000050d0/8
[    30.261] (II) Open ACPI successful (/var/run/acpid.socket)
[    30.261] (II) LoadModule: "extmod"
[    30.289] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    30.289] (II) Module extmod: vendor="X.Org Foundation"
[    30.289]     compiled for 1.11.3, module version = 1.0.0
[    30.289]     Module class: X.Org Server Extension
[    30.289]     ABI class: X.Org Server Extension, version 6.0
[    30.289] (II) Loading extension MIT-SCREEN-SAVER
[    30.289] (II) Loading extension XFree86-VidModeExtension
[    30.289] (II) Loading extension XFree86-DGA
[    30.289] (II) Loading extension DPMS
[    30.290] (II) Loading extension XVideo
[    30.290] (II) Loading extension XVideo-MotionCompensation
[    30.290] (II) Loading extension X-Resource
[    30.290] (II) LoadModule: "dbe"
[    30.290] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    30.290] (II) Module dbe: vendor="X.Org Foundation"
[    30.290]     compiled for 1.11.3, module version = 1.0.0
[    30.290]     Module class: X.Org Server Extension
[    30.290]     ABI class: X.Org Server Extension, version 6.0
[    30.290] (II) Loading extension DOUBLE-BUFFER
[    30.290] (II) LoadModule: "glx"
[    30.291] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    30.291] (II) Module glx: vendor="X.Org Foundation"
[    30.291]     compiled for 1.11.3, module version = 1.0.0
[    30.291]     ABI class: X.Org Server Extension, version 6.0
[    30.291] (==) AIGLX enabled
[    30.291] (II) Loading extension GLX
[    30.292] (II) LoadModule: "record"
[    30.292] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    30.292] (II) Module record: vendor="X.Org Foundation"
[    30.292]     compiled for 1.11.3, module version = 1.13.0
[    30.292]     Module class: X.Org Server Extension
[    30.292]     ABI class: X.Org Server Extension, version 6.0
[    30.292] (II) Loading extension RECORD
[    30.292] (II) LoadModule: "dri"
[    30.293] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    30.293] (II) Module dri: vendor="X.Org Foundation"
[    30.293]     compiled for 1.11.3, module version = 1.0.0
[    30.293]     ABI class: X.Org Server Extension, version 6.0
[    30.293] (II) Loading extension XFree86-DRI
[    30.294] (II) LoadModule: "dri2"
[    30.294] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    30.294] (II) Module dri2: vendor="X.Org Foundation"
[    30.294]     compiled for 1.11.3, module version = 1.2.0
[    30.294]     ABI class: X.Org Server Extension, version 6.0
[    30.294] (II) Loading extension DRI2
[    30.294] (==) Matched intel as autoconfigured driver 0
[    30.294] (==) Matched vesa as autoconfigured driver 1
[    30.294] (==) Matched fbdev as autoconfigured driver 2
[    30.294] (==) Assigned the driver to the xf86ConfigLayout
[    30.295] (II) LoadModule: "intel"
[    30.295] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    30.296] (II) Module intel: vendor="X.Org Foundation"
[    30.296]     compiled for 1.11.3, module version = 2.17.0
[    30.296]     Module class: X.Org Video Driver
[    30.296]     ABI class: X.Org Video Driver, version 11.0
[    30.296] (II) LoadModule: "vesa"
[    30.297] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.297] (II) Module vesa: vendor="X.Org Foundation"
[    30.297]     compiled for 1.11.3, module version = 2.3.0
[    30.297]     Module class: X.Org Video Driver
[    30.297]     ABI class: X.Org Video Driver, version 11.0
[    30.297] (II) LoadModule: "fbdev"
[    30.298] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.298] (II) Module fbdev: vendor="X.Org Foundation"
[    30.298]     compiled for 1.11.3, module version = 0.4.2
[    30.298]     ABI class: X.Org Video Driver, version 11.0
[    30.298] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2)
[    30.300] (II) VESA: driver for VESA chipsets: vesa
[    30.300] (II) FBDEV: driver for framebuffer: fbdev
[    30.300] (++) using VT number 7


[    30.300] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.300] vesa: Ignoring device with a bound kernel driver
[    30.300] (WW) Falling back to old probe method for vesa
[    30.300] (II) Loading sub module "fbdevhw"
[    30.300] (II) LoadModule: "fbdevhw"
[    30.339] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.339] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.339]     compiled for 1.11.3, module version = 0.0.2
[    30.339]     ABI class: X.Org Video Driver, version 11.0
[    30.339] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.339] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.340] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[    30.340] (II) FBDEV(1): using default device
[    30.340] (II) FBDEV(1): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.340] (==) FBDEV(1): Depth 24, (==) framebuffer bpp 32
[    30.340] (==) FBDEV(1): RGB weight 888
[    30.340] (==) FBDEV(1): Default visual is TrueColor
[    30.340] (==) FBDEV(1): Using gamma correction (1.0, 1.0, 1.0)
[    30.340] (II) FBDEV(1): hardware: psbfb (video memory: 2400kB)
[    30.340] (II) FBDEV(1): checking modes against framebuffer device...
[    30.340] (II) FBDEV(1): checking modes against monitor...
[    30.340] (--) FBDEV(1): Virtual size is 1024x600 (pitch 1024)
[    30.340] (**) FBDEV(1):  Built-in mode "current"
[    30.340] (==) FBDEV(1): DPI set to (96, 96)
[    30.340] (II) Loading sub module "fb"
[    30.340] (II) LoadModule: "fb"
[    30.341] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.341] (II) Module fb: vendor="X.Org Foundation"
[    30.341]     compiled for 1.11.3, module version = 1.0.0
[    30.341]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.341] (**) FBDEV(1): using shadow framebuffer
[    30.341] (II) Loading sub module "shadow"
[    30.341] (II) LoadModule: "shadow"
[    30.342] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    30.342] (II) Module shadow: vendor="X.Org Foundation"
[    30.342]     compiled for 1.11.3, module version = 1.1.0
[    30.342]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.342] (II) UnloadModule: "vesa"
[    30.342] (II) Unloading vesa
[    30.342] (II) UnloadModule: "intel"
[    30.343] (II) Unloading intel
[    30.343] (==) Depth 24 pixmap format is 32 bpp
[    30.695] (==) FBDEV(0): Backing store disabled
[    30.696] (==) FBDEV(0): DPMS enabled
[    30.696] (==) RandR enabled
[    30.696] (II) Initializing built-in extension Generic Event Extension
[    30.696] (II) Initializing built-in extension SHAPE
[    30.696] (II) Initializing built-in extension MIT-SHM
[    30.696] (II) Initializing built-in extension XInputExtension
[    30.696] (II) Initializing built-in extension XTEST
[    30.696] (II) Initializing built-in extension BIG-REQUESTS
[    30.696] (II) Initializing built-in extension SYNC
[    30.696] (II) Initializing built-in extension XKEYBOARD
[    30.696] (II) Initializing built-in extension XC-MISC
[    30.696] (II) Initializing built-in extension SECURITY
[    30.696] (II) Initializing built-in extension XINERAMA
[    30.697] (II) Initializing built-in extension XFIXES
[    30.697] (II) Initializing built-in extension RENDER
[    30.697] (II) Initializing built-in extension RANDR
[    30.697] (II) Initializing built-in extension COMPOSITE
[    30.697] (II) Initializing built-in extension DAMAGE
[    30.734] (II) AIGLX: Screen 0 is not DRI2 capable
[    30.734] (II) AIGLX: Screen 0 is not DRI capable
[    30.785] (II) AIGLX: Loaded and initialized swrast
[    30.785] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    30.814] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.823] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    30.823] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.823] (II) LoadModule: "evdev"
[    30.824] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.824] (II) Module evdev: vendor="X.Org Foundation"
[    30.824]     compiled for 1.11.3, module version = 2.7.0
[    30.824]     Module class: X.Org XInput Driver
[    30.824]     ABI class: X.Org XInput driver, version 16.0
[    30.825] (II) Using input driver 'evdev' for 'Power Button'
[    30.825] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.825] (**) Power Button: always reports core events
[    30.825] (**) evdev: Power Button: Device: "/dev/input/event3"
[    30.825] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.825] (--) evdev: Power Button: Found keys
[    30.825] (II) evdev: Power Button: Configuring as keyboard
[    30.825] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    30.825] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    30.825] (**) Option "xkb_rules" "evdev"
[    30.825] (**) Option "xkb_model" "pc105"
[    30.825] (**) Option "xkb_layout" "us"
[    30.827] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    30.827] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    30.827] (II) Using input driver 'evdev' for 'Video Bus'
[    30.827] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.827] (**) Video Bus: always reports core events
[    30.827] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    30.827] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    30.827] (--) evdev: Video Bus: Found keys
[    30.827] (II) evdev: Video Bus: Configuring as keyboard
[    30.827] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6/event6"
[    30.827] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    30.828] (**) Option "xkb_rules" "evdev"
[    30.828] (**) Option "xkb_model" "pc105"
[    30.828] (**) Option "xkb_layout" "us"
[    30.829] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    30.829] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.829] (II) Using input driver 'evdev' for 'Power Button'
[    30.829] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.829] (**) Power Button: always reports core events
[    30.830] (**) evdev: Power Button: Device: "/dev/input/event0"
[    30.830] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.830] (--) evdev: Power Button: Found keys
[    30.830] (II) evdev: Power Button: Configuring as keyboard
[    30.830] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    30.830] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    30.830] (**) Option "xkb_rules" "evdev"
[    30.830] (**) Option "xkb_model" "pc105"
[    30.830] (**) Option "xkb_layout" "us"
[    30.831] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    30.832] (II) No input driver specified, ignoring this device.
[    30.832] (II) This device may have been added with another device file.
[    30.832] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    30.832] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    30.832] (II) Using input driver 'evdev' for 'Sleep Button'
[    30.832] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.833] (**) Sleep Button: always reports core events
[    30.833] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    30.833] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    30.833] (--) evdev: Sleep Button: Found keys
[    30.833] (II) evdev: Sleep Button: Configuring as keyboard
[    30.833] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    30.833] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    30.833] (**) Option "xkb_rules" "evdev"
[    30.833] (**) Option "xkb_model" "pc105"
[    30.833] (**) Option "xkb_layout" "us"
[    30.835] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event10)
[    30.835] (II) No input driver specified, ignoring this device.
[    30.835] (II) This device may have been added with another device file.
[    30.835] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event11)
[    30.836] (II) No input driver specified, ignoring this device.
[    30.836] (II) This device may have been added with another device file.
[    30.836] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event9)
[    30.836] (II) No input driver specified, ignoring this device.
[    30.836] (II) This device may have been added with another device file.
[    30.837] (II) config/udev: Adding input device WebCam (/dev/input/event7)
[    30.837] (**) WebCam: Applying InputClass "evdev keyboard catchall"
[    30.837] (II) Using input driver 'evdev' for 'WebCam'
[    30.837] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.838] (**) WebCam: always reports core events
[    30.838] (**) evdev: WebCam: Device: "/dev/input/event7"
[    30.838] (--) evdev: WebCam: Vendor 0x402 Product 0x7675
[    30.838] (--) evdev: WebCam: Found keys
[    30.838] (II) evdev: WebCam: Configuring as keyboard
[    30.838] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/input/input7/event7"
[    30.838] (II) XINPUT: Adding extended input device "WebCam" (type: KEYBOARD, id 10)
[    30.838] (**) Option "xkb_rules" "evdev"
[    30.838] (**) Option "xkb_model" "pc105"
[    30.838] (**) Option "xkb_layout" "us"
[    30.840] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    30.840] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    30.840] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    30.840] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.840] (**) AT Translated Set 2 keyboard: always reports core events
[    30.840] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    30.840] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    30.840] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    30.840] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    30.840] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    30.840] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    30.840] (**) Option "xkb_rules" "evdev"
[    30.840] (**) Option "xkb_model" "pc105"
[    30.840] (**) Option "xkb_layout" "us"
[    30.842] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[    30.842] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    30.842] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    30.842] (II) LoadModule: "synaptics"
[    30.843] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    30.843] (II) Module synaptics: vendor="X.Org Foundation"
[    30.843]     compiled for 1.11.3, module version = 1.6.2
[    30.843]     Module class: X.Org XInput Driver
[    30.843]     ABI class: X.Org XInput driver, version 16.0
[    30.844] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    30.844] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    30.844] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    30.844] (**) Option "Device" "/dev/input/event8"
[    30.960] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    30.960] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5612
[    30.960] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4618
[    30.960] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    30.960] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    30.960] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    30.960] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    30.960] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    30.960] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    31.004] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input8/event8"
[    31.004] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    31.005] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    31.005] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    31.005] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.038
[    31.005] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    31.006] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    31.006] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    31.006] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    31.006] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    31.007] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    31.007] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    31.015] (II) config/udev: Adding input device Acer WMI hotkeys (/dev/input/event5)
[    31.015] (**) Acer WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    31.016] (II) Using input driver 'evdev' for 'Acer WMI hotkeys'
[    31.016] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.016] (**) Acer WMI hotkeys: always reports core events
[    31.016] (**) evdev: Acer WMI hotkeys: Device: "/dev/input/event5"
[    31.016] (--) evdev: Acer WMI hotkeys: Vendor 0 Product 0
[    31.016] (--) evdev: Acer WMI hotkeys: Found keys
[    31.016] (II) evdev: Acer WMI hotkeys: Configuring as keyboard
[    31.016] (**) Option "config_info" "udev:/sys/devices/virtual/input/input5/event5"
[    31.016] (II) XINPUT: Adding extended input device "Acer WMI hotkeys" (type: KEYBOARD, id 13)
[    31.016] (**) Option "xkb_rules" "evdev"
[    31.016] (**) Option "xkb_model" "pc105"
[    31.017] (**) Option "xkb_layout" "us"



```

---

### Post by rai_shu2 on 2013-08-26
Okay. Well, we know video isn't the problem. I would suspect the network or perhaps storage problems.

Maybe there's something in ~/.xsession-errors that would help us out here.

---

