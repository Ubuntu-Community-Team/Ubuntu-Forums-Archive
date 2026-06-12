---
title: "Lubuntu 18.04.5 32 bits How install using standard vga driver 1280X1024 16 bits 60HZ?"
date: 2020-11-14
forum: General Help
---

### Post by aug7744 on 2020-11-14
Hello.
Unhappily my notebook video card has problems in VRAM. If using video driver crash the system, but if using vga standard driver in windows run without problems.
Thus being I had installed Lubuntu 18.04.5 32 bits and when the nouveau driver is loaded crash the installation exactly how happen in windows.
Trying to install Lubuntu 18.04.5 32 bits using nomodeset is correctly done, but in Preferences \ Monitor Configuration only is displayed 1280X780 77 HZ not being possible use another resolution and the HZ is much high. Another detail is thar perhaps is using 32 bits color how the video card VRAM is damaged create artifacts in screen in windows if using 32 bits, but if using 16 bits color the screen colors not has artifacts and is possible to use without problems.
Lubuntu 18.04.5 installed using nomodeset is using an standard vga driver ? If not how I can configure to use an standard vga driver ?
I want to use 1024X768 or 1280X1024 both using 16 bits color and 60 HZ.

Thanks for reply.

---

### Post by Yellow Pasque on 2020-11-14
Can you copy and paste your /var/log/Xorg.0.log file? (Use code tags as it's a lot of text.)

There are two "generic" video drivers for X - fbdev and vesa. Your log should show which is being used and more details.

---

### Post by aug7744 on 2020-11-15
Thanks for your reply.
I have loaded Lubuntu 18.04.5 32 bits in try mode using nouveau.modeset=0 vga=791 and now the system not is crashing and the colors are good, but if installing using the same command nouveau.modeset=0 vga=791 the installed sysmtem will use 1024X768X32 77 HZ.
I want 1024X768 16 bits 60 HZ using standard vga driver to use less possible GPU power thus not has artifacts in screen.


Here is the Xorg.0.log
```

[    26.213] 
X.Org X Server 1.20.8
X Protocol Version 11, Revision 0
[    26.213] Build Operating System: Linux 4.4.0-184-generic i686 Ubuntu
[    26.213] Current Operating System: Linux augusto 5.4.0-42-generic #46~18.04.1-Ubuntu SMP Fri Jul 10 07:09:27 UTC 2020 i686
[    26.213] Kernel command line: BOOT_IMAGE=/@/boot/vmlinuz-5.4.0-42-generic root=UUID=3f646e2e-5017-42c7-bb4b-a1f809dd322b ro rootflags=subvol=@ nouveau.modeset=0 quiet splash vt.handoff=1
[    26.213] Build Date: 03 July 2020  07:00:25AM
[    26.213] xorg-server-hwe-18.04 2:1.20.8-2ubuntu2.2~18.04.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    26.213] Current version of pixman: 0.34.0
[    26.213]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    26.213] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.214] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 14 10:56:42 2020
[    26.264] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.264] (==) No Layout section.  Using the first Screen section.
[    26.264] (==) No screen section available. Using defaults.
[    26.264] (**) |-->Screen "Default Screen Section" (0)
[    26.264] (**) |   |-->Monitor "<default monitor>"
[    26.265] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    26.265] (==) Automatically adding devices
[    26.265] (==) Automatically enabling devices
[    26.265] (==) Automatically adding GPU devices
[    26.265] (==) Automatically binding GPU devices
[    26.265] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    26.265] (WW) The directory "/usr/share/fonts/X11/misc" does not exist.
[    26.265]     Entry deleted from font path.
[    26.265] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.265]     Entry deleted from font path.
[    26.265] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    26.265]     Entry deleted from font path.
[    26.265] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.265]     Entry deleted from font path.
[    26.265] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    26.265]     Entry deleted from font path.
[    26.265] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    26.265]     Entry deleted from font path.
[    26.265] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.265]     Entry deleted from font path.
[    26.265] (==) FontPath set to:
    built-ins
[    26.265] (==) ModulePath set to "/usr/lib/xorg/modules"
[    26.265] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.265] (II) Loader magic: 0x6a9020
[    26.265] (II) Module ABI versions:
[    26.265]     X.Org ANSI C Emulation: 0.4
[    26.265]     X.Org Video Driver: 24.1
[    26.265]     X.Org XInput driver : 24.1
[    26.265]     X.Org Server Extension : 10.0
[    26.267] (++) using VT number 7

[    26.267] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    26.272] (--) PCI:*(1@0:0:0) 10de:00c8:1028:019c rev 162, Mem @ 0xdd000000/16777216, 0xc0000000/268435456, 0xde000000/16777216, BIOS @ 0x????????/131072
[    26.272] (II) LoadModule: "glx"
[    26.316] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    26.490] (II) Module glx: vendor="X.Org Foundation"
[    26.492]     compiled for 1.20.8, module version = 1.0.0
[    26.492]     ABI class: X.Org Server Extension, version 10.0
[    26.694] (==) Matched nouveau as autoconfigured driver 0
[    26.694] (==) Matched modesetting as autoconfigured driver 1
[    26.694] (==) Matched fbdev as autoconfigured driver 2
[    26.695] (==) Matched vesa as autoconfigured driver 3
[    26.695] (==) Assigned the driver to the xf86ConfigLayout
[    26.695] (II) LoadModule: "nouveau"
[    26.695] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    26.797] (II) Module nouveau: vendor="X.Org Foundation"
[    26.797]     compiled for 1.20.4, module version = 1.0.16
[    26.797]     Module class: X.Org Video Driver
[    26.797]     ABI class: X.Org Video Driver, version 24.0
[    26.797] (II) LoadModule: "modesetting"
[    26.797] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    26.804] (II) Module modesetting: vendor="X.Org Foundation"
[    26.804]     compiled for 1.20.8, module version = 1.20.8
[    26.804]     Module class: X.Org Video Driver
[    26.804]     ABI class: X.Org Video Driver, version 24.1
[    26.804] (II) LoadModule: "fbdev"
[    26.804] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.828] (II) Module fbdev: vendor="X.Org Foundation"
[    26.828]     compiled for 1.20.1, module version = 0.5.0
[    26.828]     Module class: X.Org Video Driver
[    26.828]     ABI class: X.Org Video Driver, version 24.0
[    26.828] (II) LoadModule: "vesa"
[    26.829] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.839] (II) Module vesa: vendor="X.Org Foundation"
[    26.839]     compiled for 1.20.1, module version = 2.4.0
[    26.839]     Module class: X.Org Video Driver
[    26.839]     ABI class: X.Org Video Driver, version 24.0
[    26.839] (II) NOUVEAU driver Date:   Mon Jan 28 23:25:58 2019 -0500
[    26.839] (II) NOUVEAU driver for NVIDIA chipset families :
[    26.839]     RIVA TNT            (NV04)
[    26.839]     RIVA TNT2           (NV05)
[    26.839]     GeForce 256         (NV10)
[    26.840]     GeForce 2           (NV11, NV15)
[    26.840]     GeForce 4MX         (NV17, NV18)
[    26.840]     GeForce 3           (NV20)
[    26.840]     GeForce 4Ti         (NV25, NV28)
[    26.840]     GeForce FX          (NV3x)
[    26.841]     GeForce 6           (NV4x)
[    26.841]     GeForce 7           (G7x)
[    26.841]     GeForce 8           (G8x)
[    26.841]     GeForce 9           (G9x)
[    26.841]     GeForce GTX 2xx/3xx (GT2xx)
[    26.841]     GeForce GTX 4xx/5xx (GFxxx)
[    26.841]     GeForce GTX 6xx/7xx (GKxxx)
[    26.842]     GeForce GTX 9xx     (GMxxx)
[    26.842]     GeForce GTX 10xx    (GPxxx)
[    26.842] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    26.842] (II) FBDEV: driver for framebuffer: fbdev
[    26.842] (II) VESA: driver for VESA chipsets: vesa
[    27.079] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -19
[    27.080] (EE) open /dev/dri/card0: No such file or directory
[    27.080] (WW) Falling back to old probe method for modesetting
[    27.080] (EE) open /dev/dri/card0: No such file or directory
[    27.080] (II) Loading sub module "fbdevhw"
[    27.080] (II) LoadModule: "fbdevhw"
[    27.080] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    27.091] (II) Module fbdevhw: vendor="X.Org Foundation"
[    27.091]     compiled for 1.20.8, module version = 0.0.2
[    27.091]     ABI class: X.Org Video Driver, version 24.1
[    27.091] (**) FBDEV(1): claimed PCI slot 1@0:0:0
[    27.091] (II) FBDEV(1): using default device
[    27.091] (EE) Screen 0 deleted because of no matching config section.
[    27.091] (II) UnloadModule: "modesetting"
[    27.091] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    27.091] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    27.091] (==) FBDEV(0): RGB weight 888
[    27.091] (==) FBDEV(0): Default visual is TrueColor
[    27.091] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    27.092] (II) FBDEV(0): hardware: VESA VGA (video memory: 5120kB)
[    27.092] (II) FBDEV(0): checking modes against framebuffer device...
[    27.092] (II) FBDEV(0): checking modes against monitor...
[    27.092] (II) FBDEV(0): Virtual size is 1280x1024 (pitch 1280)
[    27.092] (**) FBDEV(0):  Built-in mode "current": 131.1 MHz, 80.3 kHz, 76.6 Hz
[    27.092] (II) FBDEV(0): Modeline "current"x0.0  131.09  1280 1312 1472 1632  1024 1028 1032 1048 -hsync -vsync -csync (80.3 kHz b)
[    27.092] (==) FBDEV(0): DPI set to (96, 96)
[    27.092] (II) Loading sub module "fb"
[    27.092] (II) LoadModule: "fb"
[    27.092] (II) Loading /usr/lib/xorg/modules/libfb.so
[    27.095] (II) Module fb: vendor="X.Org Foundation"
[    27.095]     compiled for 1.20.8, module version = 1.0.0
[    27.095]     ABI class: X.Org ANSI C Emulation, version 0.4
[    27.095] (**) FBDEV(0): using shadow framebuffer
[    27.095] (II) Loading sub module "shadow"
[    27.095] (II) LoadModule: "shadow"
[    27.095] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    27.101] (II) Module shadow: vendor="X.Org Foundation"
[    27.101]     compiled for 1.20.8, module version = 1.1.0
[    27.101]     ABI class: X.Org ANSI C Emulation, version 0.4
[    27.101] (II) UnloadModule: "vesa"
[    27.101] (II) Unloading vesa
[    27.102] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[    27.102] (==) FBDEV(0): Backing store enabled
[    27.103] (==) FBDEV(0): DPMS enabled
[    27.103] (II) Initializing extension Generic Event Extension
[    27.105] (II) Initializing extension SHAPE
[    27.106] (II) Initializing extension MIT-SHM
[    27.106] (II) Initializing extension XInputExtension
[    27.107] (II) Initializing extension XTEST
[    27.108] (II) Initializing extension BIG-REQUESTS
[    27.108] (II) Initializing extension SYNC
[    27.109] (II) Initializing extension XKEYBOARD
[    27.109] (II) Initializing extension XC-MISC
[    27.110] (II) Initializing extension SECURITY
[    27.110] (II) Initializing extension XFIXES
[    27.111] (II) Initializing extension RENDER
[    27.112] (II) Initializing extension RANDR
[    27.113] (II) Initializing extension COMPOSITE
[    27.113] (II) Initializing extension DAMAGE
[    27.113] (II) Initializing extension MIT-SCREEN-SAVER
[    27.114] (II) Initializing extension DOUBLE-BUFFER
[    27.114] (II) Initializing extension RECORD
[    27.115] (II) Initializing extension DPMS
[    27.115] (II) Initializing extension Present
[    27.115] (II) Initializing extension DRI3
[    27.115] (II) Initializing extension X-Resource
[    27.116] (II) Initializing extension XVideo
[    27.116] (II) Initializing extension XVideo-MotionCompensation
[    27.116] (II) Initializing extension SELinux
[    27.116] (II) SELinux: Disabled on system
[    27.116] (II) Initializing extension GLX
[    27.117] (II) AIGLX: Screen 0 is not DRI2 capable
[    30.062] (II) IGLX: Loaded and initialized swrast
[    30.062] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    30.062] (II) Initializing extension XFree86-VidModeExtension
[    30.062] (II) Initializing extension XFree86-DGA
[    30.063] (II) Initializing extension XFree86-DRI
[    30.063] (II) Initializing extension DRI2
[    30.387] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    30.388] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[    30.388] (II) LoadModule: "libinput"
[    30.388] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    30.431] (II) Module libinput: vendor="X.Org Foundation"
[    30.431]     compiled for 1.20.1, module version = 0.28.1
[    30.431]     Module class: X.Org XInput Driver
[    30.431]     ABI class: X.Org XInput driver, version 24.1
[    30.431] (II) Using input driver 'libinput' for 'Video Bus'
[    30.431] (**) Video Bus: always reports core events
[    30.431] (**) Option "Device" "/dev/input/event4"
[    30.432] (**) Option "_source" "server/udev"
[    30.434] (II) event4  - Video Bus: is tagged by udev as: Keyboard
[    30.434] (II) event4  - Video Bus: device is a keyboard
[    30.434] (II) event4  - Video Bus: device removed
[    30.434] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:20/LNXVIDEO:00/input/input5/event4"
[    30.434] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[    30.434] (**) Option "xkb_model" "pc105"
[    30.434] (**) Option "xkb_layout" "br"
[    30.507] (II) event4  - Video Bus: is tagged by udev as: Keyboard
[    30.507] (II) event4  - Video Bus: device is a keyboard
[    30.508] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    30.508] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    30.508] (II) Using input driver 'libinput' for 'Power Button'
[    30.508] (**) Power Button: always reports core events
[    30.508] (**) Option "Device" "/dev/input/event1"
[    30.508] (**) Option "_source" "server/udev"
[    30.509] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    30.509] (II) event1  - Power Button: device is a keyboard
[    30.509] (II) event1  - Power Button: device removed
[    30.509] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    30.509] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    30.509] (**) Option "xkb_model" "pc105"
[    30.510] (**) Option "xkb_layout" "br"
[    30.511] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    30.511] (II) event1  - Power Button: device is a keyboard
[    30.512] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    30.512] (II) No input driver specified, ignoring this device.
[    30.512] (II) This device may have been added with another device file.
[    30.513] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    30.513] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[    30.513] (II) Using input driver 'libinput' for 'Sleep Button'
[    30.513] (**) Sleep Button: always reports core events
[    30.513] (**) Option "Device" "/dev/input/event2"
[    30.513] (**) Option "_source" "server/udev"
[    30.514] (II) event2  - Sleep Button: is tagged by udev as: Keyboard
[    30.514] (II) event2  - Sleep Button: device is a keyboard
[    30.514] (II) event2  - Sleep Button: device removed
[    30.514] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    30.514] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    30.514] (**) Option "xkb_model" "pc105"
[    30.514] (**) Option "xkb_layout" "br"
[    30.516] (II) event2  - Sleep Button: is tagged by udev as: Keyboard
[    30.516] (II) event2  - Sleep Button: device is a keyboard
[    30.518] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event5)
[    30.518] (**) Logitech USB Keyboard: Applying InputClass "libinput keyboard catchall"
[    30.518] (II) Using input driver 'libinput' for 'Logitech USB Keyboard'
[    30.518] (**) Logitech USB Keyboard: always reports core events
[    30.518] (**) Option "Device" "/dev/input/event5"
[    30.518] (**) Option "_source" "server/udev"
[    30.519] (II) event5  - Logitech USB Keyboard: is tagged by udev as: Keyboard
[    30.519] (II) event5  - Logitech USB Keyboard: device is a keyboard
[    30.519] (II) event5  - Logitech USB Keyboard: device removed
[    30.519] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/0003:046D:C31C.0001/input/input7/event5"
[    30.519] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 9)
[    30.519] (**) Option "xkb_model" "pc105"
[    30.519] (**) Option "xkb_layout" "br"
[    30.521] (II) event5  - Logitech USB Keyboard: is tagged by udev as: Keyboard
[    30.521] (II) event5  - Logitech USB Keyboard: device is a keyboard
[    30.523] (II) config/udev: Adding input device Logitech USB Keyboard Consumer Control (/dev/input/event6)
[    30.523] (**) Logitech USB Keyboard Consumer Control: Applying InputClass "libinput keyboard catchall"
[    30.523] (II) Using input driver 'libinput' for 'Logitech USB Keyboard Consumer Control'
[    30.523] (**) Logitech USB Keyboard Consumer Control: always reports core events
[    30.523] (**) Option "Device" "/dev/input/event6"
[    30.523] (**) Option "_source" "server/udev"
[    30.524] (II) event6  - Logitech USB Keyboard Consumer Control: is tagged by udev as: Keyboard
[    30.524] (II) event6  - Logitech USB Keyboard Consumer Control: device is a keyboard
[    30.524] (II) event6  - Logitech USB Keyboard Consumer Control: device removed
[    30.524] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/0003:046D:C31C.0002/input/input8/event6"
[    30.524] (II) XINPUT: Adding extended input device "Logitech USB Keyboard Consumer Control" (type: KEYBOARD, id 10)
[    30.524] (**) Option "xkb_model" "pc105"
[    30.525] (**) Option "xkb_layout" "br"
[    30.526] (II) event6  - Logitech USB Keyboard Consumer Control: is tagged by udev as: Keyboard
[    30.526] (II) event6  - Logitech USB Keyboard Consumer Control: device is a keyboard
[    30.528] (II) config/udev: Adding input device Logitech USB Keyboard System Control (/dev/input/event7)
[    30.528] (**) Logitech USB Keyboard System Control: Applying InputClass "libinput keyboard catchall"
[    30.528] (II) Using input driver 'libinput' for 'Logitech USB Keyboard System Control'
[    30.528] (**) Logitech USB Keyboard System Control: always reports core events
[    30.528] (**) Option "Device" "/dev/input/event7"
[    30.528] (**) Option "_source" "server/udev"
[    30.529] (II) event7  - Logitech USB Keyboard System Control: is tagged by udev as: Keyboard
[    30.529] (II) event7  - Logitech USB Keyboard System Control: device is a keyboard
[    30.529] (II) event7  - Logitech USB Keyboard System Control: device removed
[    30.529] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/0003:046D:C31C.0002/input/input9/event7"
[    30.529] (II) XINPUT: Adding extended input device "Logitech USB Keyboard System Control" (type: KEYBOARD, id 11)
[    30.529] (**) Option "xkb_model" "pc105"
[    30.530] (**) Option "xkb_layout" "br"
[    30.531] (II) event7  - Logitech USB Keyboard System Control: is tagged by udev as: Keyboard
[    30.531] (II) event7  - Logitech USB Keyboard System Control: device is a keyboard
[    30.532] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    30.533] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"
[    30.533] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[    30.533] (**) AT Translated Set 2 keyboard: always reports core events
[    30.533] (**) Option "Device" "/dev/input/event3"
[    30.533] (**) Option "_source" "server/udev"
[    30.534] (II) event3  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[    30.534] (II) event3  - AT Translated Set 2 keyboard: device is a keyboard
[    30.534] (II) event3  - AT Translated Set 2 keyboard: device removed
[    30.534] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    30.534] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    30.534] (**) Option "xkb_model" "pc105"
[    30.534] (**) Option "xkb_layout" "br"
[    30.536] (II) event3  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[    30.536] (II) event3  - AT Translated Set 2 keyboard: device is a keyboard
[    30.537] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event8)
[    30.537] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "libinput touchpad catchall"
[    30.537] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    30.537] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "Default clickpad buttons"
[    30.537] (II) LoadModule: "synaptics"
[    30.537] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    30.548] (II) Module synaptics: vendor="X.Org Foundation"
[    30.548]     compiled for 1.20.1, module version = 1.9.1
[    30.549]     Module class: X.Org XInput Driver
[    30.549]     ABI class: X.Org XInput driver, version 24.1
[    30.549] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    30.549] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    30.549] (**) Option "Device" "/dev/input/event8"
[    30.549] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023 (res 0)
[    30.549] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767 (res 0)
[    30.549] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    30.549] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[    30.549] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    30.550] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[    30.550] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[    30.550] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    30.550] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    30.550] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event8"
[    30.550] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 13)
[    30.550] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    30.550] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MaxSpeed is now 1.75
[    30.550] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) AccelFactor is now 0.156
[    30.551] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    30.551] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    30.551] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    30.551] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    30.551] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    30.553] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse0)
[    30.553] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"

```

---

### Post by Yellow Pasque on 2020-11-15
```
[ 27.091] (**) FBDEV(1): claimed PCI slot 1@0:0:0
```

So it's defaulting to fbdev.  Try removing xserver-xorg-video-fbdev package to force vesa driver.

---

### Post by aug7744 on 2020-11-15
I had used sudo apt remove xserver-xorg-video-fbdev and not remove the package. That command is correct ? How remove correctly ?
between fbdev and vesa what use less cpu resources being more fast ?
I wait use 1024X768 16 bits 60 HZ vsync off and disabled any others graphics acceleration because I will use the system only for text, internet and video in low resolution.

---

### Post by Yellow Pasque on 2020-11-16
> I had used sudo apt remove xserver-xorg-video-fbdev and not remove the package. That command is correct ? How remove correctly ?

I believe it is correct. If it did not work, please give the terminal output.

> between fbdev and vesa what use less cpu resources being more fast ?

Neither one of them uses the GPU for accelerating graphics. They are both going to use a lot of CPU and be relatively slow. The problem is that if your GPU doesn't work, you don't really have alternatives..

---

### Post by aug7744 on 2020-11-16
the terminal results are

 The package 'xserver-xorg-video-fbdev' not is installed

  Strange in log is listed
 [    36.136] (**) VESA(0): Depth 16, (--) framebuffer bpp 16
[    36.136] (==) VESA(0): RGB weight 565
[    36.136] (==) VESA(0): Default visual is TrueColor
[    36.136] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)


Is listed default color True Color, but I not understand if exactly is being used 24 or 32 bits. Is using anything in 32 bits, but in output being 16 bits ?
I had used vga=791 being 16 bits and is displayed the refresh rate being 76 HZ in Monitor Configuration.

  Now I has configurated an xorg.conf and configurated to use vesa and 16 bits colors. Perhaps now is being used VESA because is using less CPU and in log not is listed fbdev.
 Monitor Configuration display HZ being 0 perhaps is 60 HZ ?

---

### Post by Yellow Pasque on 2020-11-17
> Monitor Configuration display HZ being 0 perhaps is 60 HZ 

What does xrandr say?
```
xrandr -q
```

---

### Post by aug7744 on 2020-11-17
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1600 x 1200
default connected 1280x1024+0+0 0mm x 0mm
   1600x1200      0.00  
   1400x1050      0.00  
   1280x1024      0.00* 
   1024x768       0.00  
   800x600        0.00  
   640x480        0.00

---

