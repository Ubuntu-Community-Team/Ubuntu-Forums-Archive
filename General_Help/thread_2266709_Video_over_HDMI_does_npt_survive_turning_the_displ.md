---
title: "Video over HDMI does npt survive turning the display off - since upgrade to 14.04"
date: 2015-02-24
forum: General Help
---

### Post by ron35 on 2015-02-24
Hi there, I am hoping that this is an easy answer but I have struggled to find a solution so far.

I have a Ubuntu install as a media-center (mythtv) using a Samsung TV as the display.  This computer is always on as it also records TV programs and acts as DNS and DHCP server. 

All was well until I decided it was time to stop ignoring the pesky upgrade advice and upgraded to 14.04. Since the upgrade, I have the following symptoms:

1. When I turn the computer on, it works fine and content is displayed on the TV over the HDMI connection.  If I turn the TV off and on again, there is no output - the TV shows "no signal".
2.  I have to reboot to get the display back.

Obviously, I dont want to leave the TV on 24x7 and thus seeking help to resolve.

This is what I have tried:

1. I have tried different video cards and drivers.  I was using the built-in Intel graphics when the problem first presented.  I have also tried NVidia cards and drivers (Open Source and Proprietary).
2.  I have tried creating xorg.conf to force ***UseEDID ***as "false" as I noticed that I was seeing corrupt EDID information.  This is not showing with the current card/setup.  I have currently used the "***IgnoreEDIDChecksum"***  option but with no change.

This is the latest xorg log:

```
 

[     6.385] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[     6.386] X Protocol Version 11, Revision 0
[     6.386] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[     6.386] Current Operating System: Linux mythtv-lounge 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64
[     6.386] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-45-generic root=UUID=a941fb14-251f-429a-a0ed-b2866e0f6c00 ro quiet splash nomdmonddf nomdmonisw
[     6.386] Build Date: 12 February 2015  02:49:29PM
[     6.386] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[     6.386] Current version of pixman: 0.30.2
[     6.386]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     6.386] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     6.386] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 25 12:47:47 2015
[     6.386] (==) Using config file: "/etc/X11/xorg.conf"
[     6.386] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     6.388] (==) ServerLayout "Layout0"
[     6.388] (**) |-->Screen "Screen0" (0)
[     6.388] (**) |   |-->Monitor "Monitor0"
[     6.388] (**) |   |-->Device "Device0"
[     6.388] (**) |-->Input Device "Keyboard0"
[     6.388] (**) |-->Input Device "Mouse0"
[     6.388] (**) Option "Xinerama" "0"
[     6.388] (==) Automatically adding devices
[     6.388] (==) Automatically enabling devices
[     6.388] (==) Automatically adding GPU devices
[     6.388] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     6.388]     Entry deleted from font path.
[     6.388] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     6.388]     Entry deleted from font path.
[     6.388] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     6.388]     Entry deleted from font path.
[     6.389] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     6.389]     Entry deleted from font path.
[     6.389] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     6.389]     Entry deleted from font path.
[     6.389] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     6.389] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     6.389] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[     6.389] (WW) Disabling Keyboard0
[     6.389] (WW) Disabling Mouse0
[     6.389] (II) Loader magic: 0x7f33e9b48d40
[     6.389] (II) Module ABI versions:
[     6.389]     X.Org ANSI C Emulation: 0.4
[     6.389]     X.Org Video Driver: 15.0
[     6.389]     X.Org XInput driver : 20.0
[     6.389]     X.Org Server Extension : 8.0
[     6.389] (II) xfree86: Adding drm device (/dev/dri/card0)
[     6.390] (--) PCI:*(0:1:0:0) 10de:1287:1043:84f5 rev 161, Mem @ 0xf6000000/16777216, 0xe8000000/134217728, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     6.390] Initializing built-in extension Generic Event Extension
[     6.390] Initializing built-in extension SHAPE
[     6.390] Initializing built-in extension MIT-SHM
[     6.390] Initializing built-in extension XInputExtension
[     6.390] Initializing built-in extension XTEST
[     6.390] Initializing built-in extension BIG-REQUESTS
[     6.390] Initializing built-in extension SYNC
[     6.390] Initializing built-in extension XKEYBOARD
[     6.390] Initializing built-in extension XC-MISC
[     6.390] Initializing built-in extension SECURITY
[     6.390] Initializing built-in extension XINERAMA
[     6.390] Initializing built-in extension XFIXES
[     6.390] Initializing built-in extension RENDER
[     6.390] Initializing built-in extension RANDR
[     6.390] Initializing built-in extension COMPOSITE
[     6.390] Initializing built-in extension DAMAGE
[     6.390] Initializing built-in extension MIT-SCREEN-SAVER
[     6.390] Initializing built-in extension DOUBLE-BUFFER
[     6.390] Initializing built-in extension RECORD
[     6.390] Initializing built-in extension DPMS
[     6.390] Initializing built-in extension Present
[     6.390] Initializing built-in extension DRI3
[     6.390] Initializing built-in extension X-Resource
[     6.390] Initializing built-in extension XVideo
[     6.390] Initializing built-in extension XVideo-MotionCompensation
[     6.390] Initializing built-in extension SELinux
[     6.390] Initializing built-in extension XFree86-VidModeExtension
[     6.390] Initializing built-in extension XFree86-DGA
[     6.390] Initializing built-in extension XFree86-DRI
[     6.390] Initializing built-in extension DRI2
[     6.390] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     6.390] (II) "glx" will be loaded by default.
[     6.390] (WW) "xmir" is not to be loaded by default. Skipping.
[     6.390] (II) LoadModule: "glx"
[     6.390] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     6.472] (II) Module glx: vendor="NVIDIA Corporation"
[     6.472]     compiled for 4.0.2, module version = 1.0.0
[     6.472]     Module class: X.Org Server Extension
[     6.475] (II) NVIDIA GLX Module  340.76  Thu Jan 22 11:24:42 PST 2015
[     6.475] Loading extension GLX
[     6.475] (II) LoadModule: "nvidia"
[     6.475] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     6.476] (II) Module nvidia: vendor="NVIDIA Corporation"
[     6.476]     compiled for 4.0.2, module version = 1.0.0
[     6.476]     Module class: X.Org Video Driver
[     6.476] (II) NVIDIA dlloader X Driver  340.76  Thu Jan 22 11:03:05 PST 2015
[     6.476] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     6.476] (++) using VT number 7


[     6.477] (II) Loading sub module "fb"
[     6.477] (II) LoadModule: "fb"
[     6.478] (II) Loading /usr/lib/xorg/modules/libfb.so
[     6.478] (II) Module fb: vendor="X.Org Foundation"
[     6.478]     compiled for 1.15.1, module version = 1.0.0
[     6.478]     ABI class: X.Org ANSI C Emulation, version 0.4
[     6.478] (WW) Unresolved symbol: fbGetGCPrivateKey
[     6.478] (II) Loading sub module "wfb"
[     6.478] (II) LoadModule: "wfb"
[     6.478] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     6.478] (II) Module wfb: vendor="X.Org Foundation"
[     6.478]     compiled for 1.15.1, module version = 1.0.0
[     6.478]     ABI class: X.Org ANSI C Emulation, version 0.4
[     6.479] (II) Loading sub module "ramdac"
[     6.479] (II) LoadModule: "ramdac"
[     6.479] (II) Module "ramdac" already built-in
[     6.481] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[     6.481] (==) NVIDIA(0): RGB weight 888
[     6.481] (==) NVIDIA(0): Default visual is TrueColor
[     6.481] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     6.481] (**) NVIDIA(0): Option "Stereo" "0"
[     6.481] (**) NVIDIA(0): Option "SLI" "Off"
[     6.481] (**) NVIDIA(0): Option "MultiGPU" "Off"
[     6.481] (**) NVIDIA(0): Option "BaseMosaic" "off"
[     6.481] (**) NVIDIA(0): Stereo disabled by request
[     6.481] (**) NVIDIA(0): NVIDIA SLI disabled.
[     6.481] (**) NVIDIA(0): NVIDIA Multi-GPU disabled.
[     6.481] (**) NVIDIA(0): Option "IgnoreEDIDChecksum" "DFP-0, DFP-1"
[     6.481] (**) NVIDIA(0): Option "MetaModes" "1920x1080_60 +0+0"
[     6.481] (**) NVIDIA(0): Enabling 2D acceleration
[     7.199] (WW) NVIDIA(0): Ignoring EDID checksum for display DFP-1. Note that an EDID
[     7.199] (WW) NVIDIA(0):     with a bad checksum could indicate a corrupt EDID. A
[     7.199] (WW) NVIDIA(0):     corrupt EDID may have mode timings beyond the capabilities
[     7.199] (WW) NVIDIA(0):     of your display, and could damage your hardware. Please
[     7.199] (WW) NVIDIA(0):     use with care.
[     7.199] (WW) NVIDIA(0): Ignoring EDID checksum for display DFP-1. Note that an EDID
[     7.199] (WW) NVIDIA(0):     with a bad checksum could indicate a corrupt EDID. A
[     7.199] (WW) NVIDIA(0):     corrupt EDID may have mode timings beyond the capabilities
[     7.199] (WW) NVIDIA(0):     of your display, and could damage your hardware. Please
[     7.199] (WW) NVIDIA(0):     use with care.
[     7.200] (II) NVIDIA(0): Display (Pioneer Electronic Corporation VSX-520 (DFP-1)) does
[     7.200] (II) NVIDIA(0):     not support NVIDIA 3D Vision stereo.
[     7.200] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[     7.201] (II) NVIDIA(0): NVIDIA GPU GeForce GT 730 (GK208) at PCI:1:0:0 (GPU-0)
[     7.202] (--) NVIDIA(0): Memory: 2097152 kBytes
[     7.202] (--) NVIDIA(0): VideoBIOS: 80.28.79.00.0b
[     7.202] (II) NVIDIA(0): Detected PCI Express Link width: 8X
[     7.204] (--) NVIDIA(0): Valid display device(s) on GeForce GT 730 at PCI:1:0:0
[     7.204] (--) NVIDIA(0):     CRT-0
[     7.204] (--) NVIDIA(0):     DFP-0
[     7.204] (--) NVIDIA(0):     Pioneer Electronic Corporation VSX-520 (DFP-1) (boot, connected)
[     7.204] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     7.204] (--) NVIDIA(0): DFP-0: Internal TMDS
[     7.204] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[     7.204] (--) NVIDIA(0): Pioneer Electronic Corporation VSX-520 (DFP-1): Internal TMDS
[     7.204] (--) NVIDIA(GPU-0): Pioneer Electronic Corporation VSX-520 (DFP-1): 340.0 MHz maximum pixel clock
[     7.204] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     7.204] (**) NVIDIA(0):     device Pioneer Electronic Corporation VSX-520 (DFP-1)
[     7.204] (**) NVIDIA(0):     (Using EDID frequencies has been enabled on all display
[     7.204] (**) NVIDIA(0):     devices.)
[     7.206] (II) NVIDIA(0): Validated MetaModes:
[     7.206] (II) NVIDIA(0):     "1920x1080_60+0+0"
[     7.206] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[     7.233] (--) NVIDIA(0): DPI set to (47, 48); computed from "UseEdidDpi" X config
[     7.233] (--) NVIDIA(0):     option
[     7.233] (--) Depth 24 pixmap format is 32 bpp
[     7.233] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[     7.233] (II) NVIDIA:     access.
[     7.238] (II) NVIDIA(0): Setting mode "1920x1080_60+0+0"
[     7.285] Loading extension NV-GLX
[     7.298] (==) NVIDIA(0): Disabling shared memory pixmaps
[     7.298] (==) NVIDIA(0): Backing store enabled
[     7.298] (==) NVIDIA(0): Silken mouse enabled
[     7.298] (**) NVIDIA(0): DPMS enabled
[     7.298] Loading extension NV-CONTROL
[     7.298] Loading extension XINERAMA
[     7.298] (WW) NVIDIA(0): Option "PreferredMode" is not used
[     7.298] (II) Loading sub module "dri2"
[     7.298] (II) LoadModule: "dri2"
[     7.298] (II) Module "dri2" already built-in
[     7.298] (II) NVIDIA(0): [DRI2] Setup complete
[     7.298] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     7.298] (--) RandR disabled
[     7.302] (II) SELinux: Disabled on system
[     7.303] (II) Initializing extension GLX
[     7.319] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     7.321] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     7.321] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.321] (II) LoadModule: "evdev"
[     7.321] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.322] (II) Module evdev: vendor="X.Org Foundation"
[     7.322]     compiled for 1.15.0, module version = 2.8.2
[     7.322]     Module class: X.Org XInput Driver
[     7.322]     ABI class: X.Org XInput driver, version 20.0
[     7.322] (II) Using input driver 'evdev' for 'Power Button'
[     7.322] (**) Power Button: always reports core events
[     7.322] (**) evdev: Power Button: Device: "/dev/input/event1"
[     7.322] (--) evdev: Power Button: Vendor 0 Product 0x1
[     7.322] (--) evdev: Power Button: Found keys
[     7.322] (II) evdev: Power Button: Configuring as keyboard
[     7.322] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     7.322] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     7.322] (**) Option "xkb_rules" "evdev"
[     7.322] (**) Option "xkb_model" "pc105"
[     7.322] (**) Option "xkb_layout" "us"
[     7.322] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     7.322] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.322] (II) Using input driver 'evdev' for 'Power Button'
[     7.322] (**) Power Button: always reports core events
[     7.322] (**) evdev: Power Button: Device: "/dev/input/event0"
[     7.322] (--) evdev: Power Button: Vendor 0 Product 0x1
[     7.322] (--) evdev: Power Button: Found keys
[     7.322] (II) evdev: Power Button: Configuring as keyboard
[     7.322] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     7.322] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     7.322] (**) Option "xkb_rules" "evdev"
[     7.322] (**) Option "xkb_model" "pc105"
[     7.322] (**) Option "xkb_layout" "us"
[     7.323] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
[     7.323] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     7.323] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event12)
[     7.323] (II) No input driver specified, ignoring this device.
[     7.323] (II) This device may have been added with another device file.
[     7.323] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event11)
[     7.323] (II) No input driver specified, ignoring this device.
[     7.323] (II) This device may have been added with another device file.
[     7.323] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event7)
[     7.323] (II) No input driver specified, ignoring this device.
[     7.323] (II) This device may have been added with another device file.
[     7.323] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event6)
[     7.323] (II) No input driver specified, ignoring this device.
[     7.323] (II) This device may have been added with another device file.
[     7.323] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event5)
[     7.323] (II) No input driver specified, ignoring this device.
[     7.323] (II) This device may have been added with another device file.
[     7.324] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event4)
[     7.324] (II) No input driver specified, ignoring this device.
[     7.324] (II) This device may have been added with another device file.
[     7.324] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event3)
[     7.324] (II) No input driver specified, ignoring this device.
[     7.324] (II) This device may have been added with another device file.
[     7.324] (II) config/udev: Adding input device Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) (/dev/input/event8)
[     7.324] (**) Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): Applying InputClass "evdev keyboard catchall"
[     7.324] (II) Using input driver 'evdev' for 'Media Center Ed. eHome Infrared Remote Transceiver (0471:0815)'
[     7.324] (**) Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): always reports core events
[     7.324] (**) evdev: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): Device: "/dev/input/event8"
[     7.324] (--) evdev: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): Vendor 0x471 Product 0x815
[     7.324] (--) evdev: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): Found keys
[     7.324] (II) evdev: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): Configuring as keyboard
[     7.324] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/rc/rc0/input8/event8"
[     7.324] (II) XINPUT: Adding extended input device "Media Center Ed. eHome Infrared Remote Transceiver (0471:0815)" (type: KEYBOARD, id 8)
[     7.324] (**) Option "xkb_rules" "evdev"
[     7.324] (**) Option "xkb_model" "pc105"
[     7.324] (**) Option "xkb_layout" "us"
[     7.324] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event10)
[     7.324] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[     7.324] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[     7.324] (**) Logitech USB Receiver: always reports core events
[     7.325] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event10"
[     7.325] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc501
[     7.325] (--) evdev: Logitech USB Receiver: Found 9 mouse buttons
[     7.325] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[     7.325] (--) evdev: Logitech USB Receiver: Found relative axes
[     7.325] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[     7.325] (II) evdev: Logitech USB Receiver: Configuring as mouse
[     7.325] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[     7.325] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[     7.325] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     7.325] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input11/event10"
[     7.325] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 9)
[     7.325] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[     7.325] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[     7.325] (**) Logitech USB Receiver: (accel) acceleration profile 0
[     7.325] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[     7.325] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[     7.325] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[     7.325] (II) No input driver specified, ignoring this device.
[     7.325] (II) This device may have been added with another device file.
[     7.325] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[     7.325] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     7.325] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     7.325] (**) AT Translated Set 2 keyboard: always reports core events
[     7.325] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[     7.325] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     7.325] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     7.325] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     7.325] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[     7.325] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[     7.325] (**) Option "xkb_rules" "evdev"
[     7.325] (**) Option "xkb_model" "pc105"
[     7.325] (**) Option "xkb_layout" "us"
[     7.327] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (mceusb) (/dev/input/event9)
[     7.327] (**) MCE IR Keyboard/Mouse (mceusb): Applying InputClass "evdev pointer catchall"
[     7.327] (**) MCE IR Keyboard/Mouse (mceusb): Applying InputClass "evdev keyboard catchall"
[     7.327] (II) Using input driver 'evdev' for 'MCE IR Keyboard/Mouse (mceusb)'
[     7.327] (**) MCE IR Keyboard/Mouse (mceusb): always reports core events
[     7.327] (**) evdev: MCE IR Keyboard/Mouse (mceusb): Device: "/dev/input/event9"
[     7.327] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Vendor 0 Product 0
[     7.327] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Found 3 mouse buttons
[     7.327] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Found relative axes
[     7.327] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Found x and y relative axes
[     7.327] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Found keys
[     7.327] (II) evdev: MCE IR Keyboard/Mouse (mceusb): Configuring as mouse
[     7.327] (II) evdev: MCE IR Keyboard/Mouse (mceusb): Configuring as keyboard
[     7.327] (**) evdev: MCE IR Keyboard/Mouse (mceusb): YAxisMapping: buttons 4 and 5
[     7.327] (**) evdev: MCE IR Keyboard/Mouse (mceusb): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     7.327] (**) Option "config_info" "udev:/sys/devices/virtual/input/input9/event9"
[     7.327] (II) XINPUT: Adding extended input device "MCE IR Keyboard/Mouse (mceusb)" (type: KEYBOARD, id 11)
[     7.327] (**) Option "xkb_rules" "evdev"
[     7.327] (**) Option "xkb_model" "pc105"
[     7.327] (**) Option "xkb_layout" "us"
[     7.327] (II) evdev: MCE IR Keyboard/Mouse (mceusb): initialized for relative axes.
[     7.327] (**) MCE IR Keyboard/Mouse (mceusb): (accel) keeping acceleration scheme 1
[     7.327] (**) MCE IR Keyboard/Mouse (mceusb): (accel) acceleration profile 0
[     7.327] (**) MCE IR Keyboard/Mouse (mceusb): (accel) acceleration factor: 2.000
[     7.327] (**) MCE IR Keyboard/Mouse (mceusb): (accel) acceleration threshold: 4
[     7.327] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (mceusb) (/dev/input/mouse0)
[     7.327] (II) No input driver specified, ignoring this device.
[     7.327] (II) This device may have been added with another device file.
[     7.824] (WW) NVIDIA(GPU-0): Ignoring EDID checksum for display DFP-1. Note that an EDID
[     7.824] (WW) NVIDIA(GPU-0):     with a bad checksum could indicate a corrupt EDID. A
[     7.824] (WW) NVIDIA(GPU-0):     corrupt EDID may have mode timings beyond the capabilities
[     7.824] (WW) NVIDIA(GPU-0):     of your display, and could damage your hardware. Please
[     7.824] (WW) NVIDIA(GPU-0):     use with care.
[     7.824] (WW) NVIDIA(GPU-0): Ignoring EDID checksum for display DFP-1. Note that an EDID
[     7.824] (WW) NVIDIA(GPU-0):     with a bad checksum could indicate a corrupt EDID. A
[     7.824] (WW) NVIDIA(GPU-0):     corrupt EDID may have mode timings beyond the capabilities
[     7.824] (WW) NVIDIA(GPU-0):     of your display, and could damage your hardware. Please
[     7.824] (WW) NVIDIA(GPU-0):     use with care.
[     7.824] (II) NVIDIA(GPU-0): Display (Pioneer Electronic Corporation VSX-520 (DFP-1)) does
[     7.824] (II) NVIDIA(GPU-0):     not support NVIDIA 3D Vision stereo.
[     7.982] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     8.024] (WW) NVIDIA(GPU-0): Ignoring EDID checksum for display DFP-1. Note that an EDID
[     8.024] (WW) NVIDIA(GPU-0):     with a bad checksum could indicate a corrupt EDID. A
[     8.024] (WW) NVIDIA(GPU-0):     corrupt EDID may have mode timings beyond the capabilities
[     8.024] (WW) NVIDIA(GPU-0):     of your display, and could damage your hardware. Please
[     8.024] (WW) NVIDIA(GPU-0):     use with care.
[     8.024] (WW) NVIDIA(GPU-0): Ignoring EDID checksum for display DFP-1. Note that an EDID
[     8.024] (WW) NVIDIA(GPU-0):     with a bad checksum could indicate a corrupt EDID. A
[     8.024] (WW) NVIDIA(GPU-0):     corrupt EDID may have mode timings beyond the capabilities
[     8.024] (WW) NVIDIA(GPU-0):     of your display, and could damage your hardware. Please
[     8.024] (WW) NVIDIA(GPU-0):     use with care.
[     8.024] (II) NVIDIA(GPU-0): Display (Pioneer Electronic Corporation VSX-520 (DFP-1)) does
[     8.024] (II) NVIDIA(GPU-0):     not support NVIDIA 3D Vision stereo.
[     8.616] (WW) NVIDIA(GPU-0): Ignoring EDID checksum for display DFP-1. Note that an EDID
[     8.616] (WW) NVIDIA(GPU-0):     with a bad checksum could indicate a corrupt EDID. A
[     8.616] (WW) NVIDIA(GPU-0):     corrupt EDID may have mode timings beyond the capabilities
[     8.616] (WW) NVIDIA(GPU-0):     of your display, and could damage your hardware. Please
[     8.616] (WW) NVIDIA(GPU-0):     use with care.
[     8.616] (WW) NVIDIA(GPU-0): Ignoring EDID checksum for display DFP-1. Note that an EDID
[     8.616] (WW) NVIDIA(GPU-0):     with a bad checksum could indicate a corrupt EDID. A
[     8.616] (WW) NVIDIA(GPU-0):     corrupt EDID may have mode timings beyond the capabilities
[     8.616] (WW) NVIDIA(GPU-0):     of your display, and could damage your hardware. Please
[     8.616] (WW) NVIDIA(GPU-0):     use with care.
[     8.617] (II) NVIDIA(GPU-0): Display (Pioneer Electronic Corporation VSX-520 (DFP-1)) does
[     8.617] (II) NVIDIA(GPU-0):     not support NVIDIA 3D Vision stereo.
[     8.649] (WW) NVIDIA(GPU-0): Ignoring EDID checksum for display DFP-1. Note that an EDID
[     8.649] (WW) NVIDIA(GPU-0):     with a bad checksum could indicate a corrupt EDID. A
[     8.649] (WW) NVIDIA(GPU-0):     corrupt EDID may have mode timings beyond the capabilities
[     8.649] (WW) NVIDIA(GPU-0):     of your display, and could damage your hardware. Please
[     8.649] (WW) NVIDIA(GPU-0):     use with care.
[     8.649] (WW) NVIDIA(GPU-0): Ignoring EDID checksum for display DFP-1. Note that an EDID
[     8.649] (WW) NVIDIA(GPU-0):     with a bad checksum could indicate a corrupt EDID. A
[     8.649] (WW) NVIDIA(GPU-0):     corrupt EDID may have mode timings beyond the capabilities
[     8.649] (WW) NVIDIA(GPU-0):     of your display, and could damage your hardware. Please
[     8.649] (WW) NVIDIA(GPU-0):     use with care.
[     8.649] (II) NVIDIA(GPU-0): Display (Pioneer Electronic Corporation VSX-520 (DFP-1)) does
[     8.649] (II) NVIDIA(GPU-0):     not support NVIDIA 3D Vision stereo.
[     8.989] (WW) NVIDIA(GPU-0): Ignoring EDID checksum for display DFP-1. Note that an EDID
[     8.989] (WW) NVIDIA(GPU-0):     with a bad checksum could indicate a corrupt EDID. A
[     8.989] (WW) NVIDIA(GPU-0):     corrupt EDID may have mode timings beyond the capabilities
[     8.989] (WW) NVIDIA(GPU-0):     of your display, and could damage your hardware. Please
[     8.989] (WW) NVIDIA(GPU-0):     use with care.
[     8.989] (WW) NVIDIA(GPU-0): Ignoring EDID checksum for display DFP-1. Note that an EDID
[     8.989] (WW) NVIDIA(GPU-0):     with a bad checksum could indicate a corrupt EDID. A
[     8.989] (WW) NVIDIA(GPU-0):     corrupt EDID may have mode timings beyond the capabilities
[     8.989] (WW) NVIDIA(GPU-0):     of your display, and could damage your hardware. Please
[     8.989] (WW) NVIDIA(GPU-0):     use with care.
[     8.989] (II) NVIDIA(GPU-0): Display (Pioneer Electronic Corporation VSX-520 (DFP-1)) does
[     8.989] (II) NVIDIA(GPU-0):     not support NVIDIA 3D Vision stereo.
[     9.018] (WW) NVIDIA(GPU-0): Ignoring EDID checksum for display DFP-1. Note that an EDID
[     9.018] (WW) NVIDIA(GPU-0):     with a bad checksum could indicate a corrupt EDID. A
[     9.018] (WW) NVIDIA(GPU-0):     corrupt EDID may have mode timings beyond the capabilities
[     9.018] (WW) NVIDIA(GPU-0):     of your display, and could damage your hardware. Please
[     9.018] (WW) NVIDIA(GPU-0):     use with care.
[     9.018] (WW) NVIDIA(GPU-0): Ignoring EDID checksum for display DFP-1. Note that an EDID
[     9.018] (WW) NVIDIA(GPU-0):     with a bad checksum could indicate a corrupt EDID. A
[     9.018] (WW) NVIDIA(GPU-0):     corrupt EDID may have mode timings beyond the capabilities
[     9.018] (WW) NVIDIA(GPU-0):     of your display, and could damage your hardware. Please
[     9.018] (WW) NVIDIA(GPU-0):     use with care.
[     9.018] (II) NVIDIA(GPU-0): Display (Pioneer Electronic Corporation VSX-520 (DFP-1)) does
[     9.018] (II) NVIDIA(GPU-0):     not support NVIDIA 3D Vision stereo.
[    10.000] (WW) NVIDIA(GPU-0): Ignoring EDID checksum for display DFP-1. Note that an EDID
[    10.001] (WW) NVIDIA(GPU-0):     with a bad checksum could indicate a corrupt EDID. A
[    10.001] (WW) NVIDIA(GPU-0):     corrupt EDID may have mode timings beyond the capabilities
[    10.001] (WW) NVIDIA(GPU-0):     of your display, and could damage your hardware. Please
[    10.001] (WW) NVIDIA(GPU-0):     use with care.
[    10.001] (WW) NVIDIA(GPU-0): Ignoring EDID checksum for display DFP-1. Note that an EDID
[    10.001] (WW) NVIDIA(GPU-0):     with a bad checksum could indicate a corrupt EDID. A
[    10.001] (WW) NVIDIA(GPU-0):     corrupt EDID may have mode timings beyond the capabilities
[    10.001] (WW) NVIDIA(GPU-0):     of your display, and could damage your hardware. Please
[    10.001] (WW) NVIDIA(GPU-0):     use with care.
[    10.001] (II) NVIDIA(GPU-0): Display (Pioneer Electronic Corporation VSX-520 (DFP-1)) does
[    10.001] (II) NVIDIA(GPU-0):     not support NVIDIA 3D Vision stereo.



```

This is the xorg.conf file I am currently using, though the problem is there without any xorg.conf at all:

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 331.20  (buildd@roseapple)  Mon Feb  3 15:07:22 UTC 2014


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection


Section "Files"
EndSection


Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection


Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection


Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Pioneer Electronic Corporation VSX-520"
    HorizSync       26.0 - 81.0
    VertRefresh     24.0 - 75.0
    Option         "DPMS"
##    Modeline "1920x1080_rwb"  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync
    Option          "PreferredMode" "1920x1080_rwb"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 730"
    Option          "IgnoreEDIDChecksum" "DFP-0, DFP-1"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "1920x1080_60 +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
##    Modes    "1920x1080_rwb"
    EndSubSection
EndSection



```

Any pointers to help resolve or further diagnose the problem will be appreciated.

thanks,

Ron

---

### Post by pqwoerituytrueiwoq on 2015-02-24
iv had this issues since before upgrading, it is a issue with nvidia's driver that they will not admit exists
right now i am using my raspberry pi to fix it with a button press
it runs this command over ssh to restore the display
```
DISPLAY=":0.0" sudo -u pqwoerituytrueiwoq xrandr --output HDMI-0 --auto
```
this command is run via a root ssh login session (root ssh is restricted to my pi's ip address)
on my pi only the root user can ssh into root with ssh keys

---

### Post by ron35 on 2015-02-24
Thanks for the reply.  I have had the problem originally with non NVidia hardware.  I am currently investigating this thread with appears relevant:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105)

---

### Post by ron35 on 2015-02-24
Yes, it appears that xfce4-settings is the culprit as identified at post #18 in the referenced thread.  Reverting to the version from saucy resolved the problem.

---

### Post by ron35 on 2015-02-25
Its always the way, you spend days trying to work something out, only to find the answer after you have posted a help-me-please.

This is SOLVED.

I managed to undo all my kludges.  No longer need the xorg.conf etc.

---

