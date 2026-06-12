---
title: "libGL can't find i965"
date: 2018-05-03
forum: General Help
---

### Post by Richard_Nai on 2018-05-03
So I was playing around with graphics drivers, and now my libGL can't find i965. When I run it in verbose mode I get
```
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/i965_dri.solibGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/i965_dri.so
libGL: dlopen /usr/X11R6/lib64/modules/dri/i965_dri.so failed (/usr/X11R6/lib64/modules/dri/i965_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib64/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib64/dri/i965_dri.so
libGL: dlopen /usr/lib64/dri/i965_dri.so failed (/usr/lib64/dri/i965_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/i965_dri.so
libGL: dlopen /usr/X11R6/lib/modules/dri/i965_dri.so failed (/usr/X11R6/lib/modules/dri/i965_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib/dri/i965_dri.so
libGL: dlopen /usr/lib/dri/i965_dri.so failed (/usr/lib/dri/i965_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/X11R6/lib32/modules/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/X11R6/lib32/modules/dri/i965_dri.so
libGL: dlopen /usr/X11R6/lib32/modules/dri/i965_dri.so failed (/usr/X11R6/lib32/modules/dri/i965_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib32/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib32/dri/i965_dri.so
libGL: dlopen /usr/lib32/dri/i965_dri.so failed (/usr/lib32/dri/i965_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: i965_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: i965

```
repeated a bunch of times.

When I locate it, however, I do indeed have it.
```

seedship@destiny:~$ locate i965_dri.so
/snap/electronic-wechat/7/usr/lib/x86_64-linux-gnu/dri/i965_dri.so
/snap/springlobby-nsg/185/usr/lib/x86_64-linux-gnu/dri/i965_dri.so
/snap/springlobby-nsg/33/usr/lib/x86_64-linux-gnu/dri/i965_dri.so
/snap/springlobby-nsg/6/usr/lib/x86_64-linux-gnu/dri/i965_dri.so
/snap/vlc/190/usr/lib/x86_64-linux-gnu/dri/i965_dri.so
/usr/lib/i386-linux-gnu/dri/i965_dri.so
/usr/lib/x86_64-linux-gnu/dri/i965_dri.so

```

OpenGL finds it, as it says: libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/i965_dri.so

But why doesn't it accept it?

Here is some helpful info.
```
seedship@destiny:~/Desktop$ inxi -GGraphics:  Card-1: Intel 3rd Gen Core processor Graphics Controller
          Card-2: Advanced Micro Devices [AMD/ATI] Chelsea LP [Radeon HD 7730M]
          Display Server: X.Org 1.18.4 driver: intel Resolution: 1920x1080@60.02hz, 1280x1024@60.02hz
          GLX Renderer: N/A GLX Version: N/A
```

/var/log/Xorg says

```
[    34.684] X.Org X Server 1.18.4
Release Date: 2016-07-19
[    34.684] X Protocol Version 11, Revision 0
[    34.684] Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
[    34.684] Current Operating System: Linux destiny 4.13.0-39-generic #44~16.04.1-Ubuntu SMP Thu Apr 5 16:43:10 UTC 2018 x86_64
[    34.684] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-39-generic root=UUID=876f6578-3b5a-4826-938d-1095cde307d4 ro quiet splash vt.handoff=7
[    34.684] Build Date: 13 October 2017  01:57:05PM
[    34.684] xorg-server 2:1.18.4-0ubuntu0.7 (For technical support please see http://www.ubuntu.com/support) 
[    34.684] Current version of pixman: 0.33.6
[    34.684] Before reporting problems, check http://wiki.x.org
to make sure that you have the latest version.
[    34.684] Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    34.684] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May  3 17:01:34 2018
[    34.695] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    34.695] (==) No Layout section.  Using the first Screen section.
[    34.695] (==) No screen section available. Using defaults.
[    34.695] (**) |-->Screen "Default Screen Section" (0)
[    34.695] (**) |   |-->Monitor "<default monitor>"
[    34.695] (==) No device specified for screen "Default Screen Section".
Using the first device section listed.
[    34.695] (**) |   |-->Device "card0"
[    34.695] (==) No monitor specified for screen "Default Screen Section".
Using a default monitor configuration.
[    34.695] (==) Automatically adding devices
[    34.695] (==) Automatically enabling devices
[    34.695] (==) Automatically adding GPU devices
[    34.695] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    34.695] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    34.695] Entry deleted from font path.
[    34.695] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    34.695] Entry deleted from font path.
[    34.695] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    34.695] Entry deleted from font path.
[    34.695] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    34.695] Entry deleted from font path.
[    34.696] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    34.696] Entry deleted from font path.
[    34.696] (==) FontPath set to:
/usr/share/fonts/X11/misc,
/usr/share/fonts/X11/Type1,
built-ins
[    34.696] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    34.696] (II) The server relies on udev to provide the list of input devices.
If no devices become available, reconfigure udev or disable AutoAddDevices.
[    34.696] (II) Loader magic: 0x55d8572fddc0
[    34.696] (II) Module ABI versions:
[    34.696] X.Org ANSI C Emulation: 0.4
[    34.696] X.Org Video Driver: 20.0
[    34.696] X.Org XInput driver : 22.1
[    34.696] X.Org Server Extension : 9.0
[    34.696] (++) using VT number 7


[    34.696] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    34.697] (II) xfree86: Adding drm device (/dev/dri/card1)
[    34.697] (II) xfree86: Adding drm device (/dev/dri/card0)
[    34.712] (--) PCI:*(0:0:2:0) 8086:0166:1028:0572 rev 9, Mem @ 0xc1000000/4194304, 0xb0000000/268435456, I/O @ 0x00004000/64, BIOS @ 0x????????/131072
[    34.712] (--) PCI: (0:1:0:0) 1002:682f:1028:0572 rev 0, Mem @ 0xa0000000/268435456, 0xc0000000/262144, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[    34.712] (II) LoadModule: "glx"
[    34.729] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    34.854] (II) Module glx: vendor="X.Org Foundation"
[    34.854] compiled for 1.18.4, module version = 1.0.0
[    34.854] ABI class: X.Org Server Extension, version 9.0
[    34.854] (==) AIGLX enabled
[    34.854] (II) LoadModule: "intel"
[    34.854] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    34.898] (II) Module intel: vendor="X.Org Foundation"
[    34.898] compiled for 1.18.4, module version = 2.99.917
[    34.898] Module class: X.Org Video Driver
[    34.898] ABI class: X.Org Video Driver, version 20.0
[    34.898] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    34.898] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    34.898] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    34.898] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    34.905] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20170619
[    34.905] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20160325-1ubuntu1.2 (Timo Aaltonen <tjaalton@debian.org>)
[    34.905] (II) intel(0): SNA compiled for use with valgrind
[    34.925] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4000
[    34.925] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx; using a maximum of 4 threads
[    34.925] (II) intel(0): Creating default Display subsection in Screen section
"Default Screen Section" for depth/fbbpp 24/32
[    34.925] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    34.925] (==) intel(0): RGB weight 888
[    34.925] (==) intel(0): Default visual is TrueColor
[    34.925] (**) intel(0): Option "Backlight" "intel_backlight"
[    34.925] (II) intel(0): Output LVDS1 has no monitor section
[    34.940] (**) intel(0): Found backlight control interface intel_backlight (type 'raw') for output LVDS1
[    34.940] (II) intel(0): Enabled output LVDS1
[    34.940] (II) intel(0): Output VGA1 has no monitor section
[    34.940] (II) intel(0): Enabled output VGA1
[    34.940] (II) intel(0): Output HDMI1 has no monitor section
[    34.940] (II) intel(0): Enabled output HDMI1
[    34.940] (II) intel(0): Output DP1 has no monitor section
[    34.940] (II) intel(0): Enabled output DP1
[    34.940] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    34.940] (II) intel(0): Output VIRTUAL1 has no monitor section
[    34.940] (II) intel(0): Enabled output VIRTUAL1
[    34.940] (--) intel(0): Output LVDS1 using initial mode 1920x1080 on pipe 0
[    34.940] (--) intel(0): Output VGA1 using initial mode 1280x1024 on pipe 1
[    34.940] (==) intel(0): TearFree disabled
[    34.940] (==) intel(0): DPI set to (96, 96)
[    34.940] (II) Loading sub module "dri2"
[    34.940] (II) LoadModule: "dri2"
[    34.940] (II) Module "dri2" already built-in
[    34.940] (II) Loading sub module "present"
[    34.940] (II) LoadModule: "present"
[    34.940] (II) Module "present" already built-in
[    34.940] (==) Depth 24 pixmap format is 32 bpp
[    34.944] (II) intel(0): SNA initialized with Ivybridge (gen7, gt2) backend
[    34.944] (==) intel(0): Backing store enabled
[    34.944] (==) intel(0): Silken mouse enabled
[    34.945] (II) intel(0): HW Cursor enabled
[    34.945] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    34.945] (==) intel(0): DPMS enabled
[    34.945] (==) intel(0): Display hotplug detection enabled
[    34.945] (II) intel(0): [DRI2] Setup complete
[    34.945] (II) intel(0): [DRI2]   DRI driver: i965
[    34.945] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    34.945] (II) intel(0): direct rendering: DRI2 enabled
[    34.945] (II) intel(0): hardware support for Present enabled
[    34.945] (--) RandR disabled
[    34.958] (II) SELinux: Disabled on system
[    35.135] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    35.135] (II) AIGLX: enabled GLX_ARB_create_context
[    35.135] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    35.135] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    35.135] (II) AIGLX: enabled GLX_INTEL_swap_event
[    35.135] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    35.135] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    35.135] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    35.135] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    35.135] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    35.135] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    35.135] (II) AIGLX: Loaded and initialized i965
[    35.135] (II) GLX: Initialized DRI2 GL provider for screen 0
[    35.138] (II) intel(0): switch to mode 1920x1080@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    35.148] (II) intel(0): switch to mode 1280x1024@60.0 on VGA1 using pipe 1, position (0, 0), rotation normal, reflection none
[    35.161] (II) intel(0): Setting screen physical size to 508 x 285
[    35.245] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    35.245] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    35.245] (II) LoadModule: "evdev"
[    35.245] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.264] (II) Module evdev: vendor="X.Org Foundation"
[    35.264] compiled for 1.18.1, module version = 2.10.1
[    35.264] Module class: X.Org XInput Driver
[    35.264] ABI class: X.Org XInput driver, version 22.1
[    35.264] (II) Using input driver 'evdev' for 'Power Button'
[    35.264] (**) Power Button: always reports core events
[    35.264] (**) evdev: Power Button: Device: "/dev/input/event2"
[    35.264] (--) evdev: Power Button: Vendor 0 Product 0x1
[    35.264] (--) evdev: Power Button: Found keys
[    35.264] (II) evdev: Power Button: Configuring as keyboard
[    35.264] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    35.264] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    35.264] (**) Option "xkb_rules" "evdev"
[    35.264] (**) Option "xkb_model" "pc105"
[    35.264] (**) Option "xkb_layout" "us"
[    35.265] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    35.265] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    35.265] (II) Using input driver 'evdev' for 'Video Bus'
[    35.265] (**) Video Bus: always reports core events
[    35.265] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    35.265] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    35.265] (--) evdev: Video Bus: Found keys
[    35.265] (II) evdev: Video Bus: Configuring as keyboard
[    35.265] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:02/input/input9/event7"
[    35.265] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    35.265] (**) Option "xkb_rules" "evdev"
[    35.265] (**) Option "xkb_model" "pc105"
[    35.265] (**) Option "xkb_layout" "us"
[    35.266] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    35.266] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    35.266] (II) Using input driver 'evdev' for 'Power Button'
[    35.266] (**) Power Button: always reports core events
[    35.266] (**) evdev: Power Button: Device: "/dev/input/event0"
[    35.266] (--) evdev: Power Button: Vendor 0 Product 0x1
[    35.266] (--) evdev: Power Button: Found keys
[    35.266] (II) evdev: Power Button: Configuring as keyboard
[    35.266] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[    35.266] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    35.266] (**) Option "xkb_rules" "evdev"
[    35.266] (**) Option "xkb_model" "pc105"
[    35.266] (**) Option "xkb_layout" "us"
[    35.266] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    35.266] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    35.266] (II) Using input driver 'evdev' for 'Video Bus'
[    35.266] (**) Video Bus: always reports core events
[    35.266] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    35.266] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    35.266] (--) evdev: Video Bus: Found keys
[    35.266] (II) evdev: Video Bus: Configuring as keyboard
[    35.266] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/LNXVIDEO:00/input/input8/event6"
[    35.266] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 9)
[    35.266] (**) Option "xkb_rules" "evdev"
[    35.266] (**) Option "xkb_model" "pc105"
[    35.266] (**) Option "xkb_layout" "us"
[    35.267] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    35.267] (II) No input driver specified, ignoring this device.
[    35.267] (II) This device may have been added with another device file.
[    35.268] (II) config/udev: Adding input device Logitech Lenovo USB Optical Mouse (/dev/input/event5)
[    35.268] (**) Logitech Lenovo USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    35.268] (II) Using input driver 'evdev' for 'Logitech Lenovo USB Optical Mouse'
[    35.268] (**) Logitech Lenovo USB Optical Mouse: always reports core events
[    35.268] (**) evdev: Logitech Lenovo USB Optical Mouse: Device: "/dev/input/event5"
[    35.328] (--) evdev: Logitech Lenovo USB Optical Mouse: Vendor 0x17ef Product 0x6019
[    35.328] (--) evdev: Logitech Lenovo USB Optical Mouse: Found 3 mouse buttons
[    35.328] (--) evdev: Logitech Lenovo USB Optical Mouse: Found scroll wheel(s)
[    35.328] (--) evdev: Logitech Lenovo USB Optical Mouse: Found relative axes
[    35.328] (--) evdev: Logitech Lenovo USB Optical Mouse: Found x and y relative axes
[    35.328] (II) evdev: Logitech Lenovo USB Optical Mouse: Configuring as mouse
[    35.328] (II) evdev: Logitech Lenovo USB Optical Mouse: Adding scrollwheel support
[    35.328] (**) evdev: Logitech Lenovo USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    35.328] (**) evdev: Logitech Lenovo USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    35.328] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/0003:17EF:6019.0001/input/input7/event5"
[    35.328] (II) XINPUT: Adding extended input device "Logitech Lenovo USB Optical Mouse" (type: MOUSE, id 10)
[    35.328] (II) evdev: Logitech Lenovo USB Optical Mouse: initialized for relative axes.
[    35.328] (**) Logitech Lenovo USB Optical Mouse: (accel) keeping acceleration scheme 1
[    35.328] (**) Logitech Lenovo USB Optical Mouse: (accel) acceleration profile 0
[    35.328] (**) Logitech Lenovo USB Optical Mouse: (accel) acceleration factor: 2.000
[    35.328] (**) Logitech Lenovo USB Optical Mouse: (accel) acceleration threshold: 4
[    35.328] (II) config/udev: Adding input device Logitech Lenovo USB Optical Mouse (/dev/input/mouse1)
[    35.328] (II) No input driver specified, ignoring this device.
[    35.328] (II) This device may have been added with another device file.
[    35.329] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD: In (/dev/input/event9)
[    35.329] (**) Laptop_Integrated_Webcam_HD: In: Applying InputClass "evdev keyboard catchall"
[    35.329] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD: In'
[    35.329] (**) Laptop_Integrated_Webcam_HD: In: always reports core events
[    35.329] (**) evdev: Laptop_Integrated_Webcam_HD: In: Device: "/dev/input/event9"
[    35.329] (--) evdev: Laptop_Integrated_Webcam_HD: In: Vendor 0xc45 Product 0x644a
[    35.329] (--) evdev: Laptop_Integrated_Webcam_HD: In: Found keys
[    35.329] (II) evdev: Laptop_Integrated_Webcam_HD: In: Configuring as keyboard
[    35.329] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input11/event9"
[    35.329] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD: In" (type: KEYBOARD, id 11)
[    35.329] (**) Option "xkb_rules" "evdev"
[    35.329] (**) Option "xkb_model" "pc105"
[    35.329] (**) Option "xkb_layout" "us"
[    35.329] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    35.329] (II) No input driver specified, ignoring this device.
[    35.329] (II) This device may have been added with another device file.
[    35.330] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    35.330] (II) No input driver specified, ignoring this device.
[    35.330] (II) This device may have been added with another device file.
[    35.330] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    35.330] (II) No input driver specified, ignoring this device.
[    35.330] (II) This device may have been added with another device file.
[    35.330] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event8)
[    35.330] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    35.330] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    35.330] (**) Dell WMI hotkeys: always reports core events
[    35.330] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event8"
[    35.330] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    35.330] (--) evdev: Dell WMI hotkeys: Found keys
[    35.330] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    35.330] (**) Option "config_info" "udev:/sys/devices/platform/PNP0C14:00/wmi_bus/wmi_bus-PNP0C14:00/9DBB5994-A997-11DA-B012-B622A1EF5492/input/input10/event8"
[    35.330] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 12)
[    35.330] (**) Option "xkb_rules" "evdev"
[    35.330] (**) Option "xkb_model" "pc105"
[    35.330] (**) Option "xkb_layout" "us"
[    35.331] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    35.331] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    35.331] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    35.331] (**) AT Translated Set 2 keyboard: always reports core events
[    35.331] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    35.331] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    35.331] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    35.331] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    35.331] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    35.331] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    35.331] (**) Option "xkb_rules" "evdev"
[    35.331] (**) Option "xkb_model" "pc105"
[    35.331] (**) Option "xkb_layout" "us"
[    35.332] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event4)
[    35.332] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    35.332] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchscreen catchall"
[    35.332] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    35.332] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    35.332] (II) LoadModule: "synaptics"
[    35.332] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    35.332] (II) Module synaptics: vendor="X.Org Foundation"
[    35.332] compiled for 1.18.1, module version = 1.8.2
[    35.332] Module class: X.Org XInput Driver
[    35.332] ABI class: X.Org XInput driver, version 22.1
[    35.332] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    35.332] (**) ETPS/2 Elantech Touchpad: always reports core events
[    35.332] (**) Option "Device" "/dev/input/event4"
[    35.412] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[    35.412] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2940 (res 31)
[    35.412] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1400 (res 31)
[    35.412] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    35.412] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    35.412] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    35.412] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    35.412] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    35.412] (**) ETPS/2 Elantech Touchpad: always reports core events
[    35.444] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event4"
[    35.444] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 14)
[    35.444] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    35.444] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    35.444] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.061
[    35.444] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    35.444] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    35.444] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    35.444] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    35.444] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    35.444] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    35.444] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    36.940] (II) intel(0): EDID vendor "AUO", prod id 8685
[    36.940] (II) intel(0): Printing DDC gathered Modelines:
[    36.940] (II) intel(0): Modeline "1920x1080"x0.0  148.00  1920 2020 2040 2186  1080 1090 1100 1128 +hsync -vsync (67.7 kHz eP)
[    36.940] (II) intel(0): Modeline "1920x1080"x0.0   98.67  1920 2020 2040 2186  1080 1090 1100 1128 +hsync -vsync (45.1 kHz e)
[    87.857] (II) intel(0): resizing framebuffer to 3200x1080
[    87.906] (II) intel(0): switch to mode 1280x1024@60.0 on VGA1 using pipe 1, position (1920, 0), rotation normal, reflection none
```

---

