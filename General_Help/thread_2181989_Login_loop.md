---
title: "Login loop"
date: 2013-10-19
forum: General Help
---

### Post by brabender on 2013-10-19
Since this morning, I can't login on my computer with my account; after entering username and password, the screen goes black, the HDD light blinks, and after some seconds, it returns to the login screen. I can login with my wife's account and also can login in my account on a terminal session. I suspect it has something to do with X or Compiz, but after several hours of googling, reconfiguring the window manager, deleting the .ICEauthority file, changing file permissions in my /home directory, etc.., I don't know what else to do. Yesterday I installed some updates, /var/log/apt/history.log tells me that among them were: xserver-xorg-core:amd64, xserver-common:amd64, libglib2.0-data:amd64,etc..

 The only difference I can think of between my wife's account and mine is Compiz. Both of us use Mate as desktop environment, I had Compiz enabled. System is Xubuntu Studio  64 bits, with Nvidia G210.I have also installed Cinnamon, Gnome-classic and XFCE, none works with my account. Here is my .xsessions-errors file:
```
/etc/mdm/Xsession: Beginning session setup...
localuser:antonio being added to access control list
Setting IM through im-switch for locale=es_ES.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Failed to connect to the VirtualBox kernel service
Failed to connect to the VirtualBox kernel service
Failed to connect to the VirtualBox kernel service
Failed to connect to the VirtualBox kernel service
mate-session[2888]: WARNING: Could not parse desktop file /home/antonio/.config/autostart/xfce4-settings-helper-autostart.desktop: El archivo de claves no tiene la clave «Name»
mate-session[2888]: WARNING: could not read /home/antonio/.config/autostart/xfce4-settings-helper-autostart.desktop
MATE_KEYRING_CONTROL=/tmp/keyring-FrLDsy
GPG_AGENT_INFO=/tmp/keyring-FrLDsy/gpg:0:1
MATE_KEYRING_PID=2979
MATE_KEYRING_CONTROL=/tmp/keyring-FrLDsy
GPG_AGENT_INFO=/tmp/keyring-FrLDsy/gpg:0:1
SSH_AUTH_SOCK=/tmp/keyring-FrLDsy/ssh
MATE_KEYRING_CONTROL=/tmp/keyring-FrLDsy
GPG_AGENT_INFO=/tmp/keyring-FrLDsy/gpg:0:1
MATE_KEYRING_CONTROL=/tmp/keyring-FrLDsy
GPG_AGENT_INFO=/tmp/keyring-FrLDsy/gpg:0:1
SSH_AUTH_SOCK=/tmp/keyring-FrLDsy/ssh
compiz (core) - Error: Screen 0 on display ":0" already has a window manager; try using the --replace option to replace the current window manager.
Backend     : ini
Integration : true
Profile     : default
Adding plugins

** (mate-power-manager:3025): WARNING **: levels is 0!
Initializing core options...done
Initializing composite options...done
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-YgNGBv/pkcs11: No existe el archivo o el directorio
mate-session: Fatal IO error 11 (Recurso no disponible temporalmente) on X server :0.
mate-settings-daemon: Fatal IO error 11 (Recurso no disponible temporalmente) on X server :0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 1211 requests (1211 known processed) with 114 events remaining.
[1382219689,000,xklavier.c:xkl_engine_start_listen/]     The backend does not require manual layout management - but it is provided by the application
```


and my Xorg.0.log:
```
[    38.871] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    38.871] X Protocol Version 11, Revision 0
[    38.871] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    38.871] Current Operating System: Linux Sobremesa-Linux 3.2.0-53-lowlatency #55-Ubuntu SMP PREEMPT Mon Aug 26 22:30:31 UTC 2013 x86_64
[    38.871] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-53-lowlatency root=UUID=3ccd865f-f90e-4318-b494-60962a705ed6 ro quiet splash
[    38.871] Build Date: 16 October 2013  04:41:23PM
[    38.871] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
[    38.872] Current version of pixman: 0.24.4
[    38.872]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    38.872] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    38.872] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 19 23:54:52 2013
[    38.872] (==) Using config file: "/etc/X11/xorg.conf"
[    38.872] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    38.872] (==) ServerLayout "Layout0"
[    38.872] (**) |-->Screen "Screen0" (0)
[    38.872] (**) |   |-->Monitor "Monitor0"
[    38.873] (**) |   |-->Device "Device0"
[    38.873] (**) |-->Input Device "Keyboard0"
[    38.873] (**) |-->Input Device "Mouse0"
[    38.873] (==) Automatically adding devices
[    38.873] (==) Automatically enabling devices
[    38.873] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    38.873]     Entry deleted from font path.
[    38.873] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    38.873]     Entry deleted from font path.
[    38.873] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    38.873]     Entry deleted from font path.
[    38.873] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    38.873]     Entry deleted from font path.
[    38.873] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    38.873]     Entry deleted from font path.
[    38.873] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    38.873]     Entry deleted from font path.
[    38.873] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    38.873] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    38.873] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    38.873] (WW) Disabling Keyboard0
[    38.873] (WW) Disabling Mouse0
[    38.873] (II) Loader magic: 0x7fd4158d1b00
[    38.873] (II) Module ABI versions:
[    38.873]     X.Org ANSI C Emulation: 0.4
[    38.873]     X.Org Video Driver: 11.0
[    38.873]     X.Org XInput driver : 16.0
[    38.873]     X.Org Server Extension : 6.0
[    38.874] (--) PCI:*(0:1:0:0) 10de:0a65:1458:3530 rev 162, Mem @ 0xfd000000/16777216, 0xe0000000/268435456, 0xde000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[    38.874] (II) Open ACPI successful (/var/run/acpid.socket)
[    38.874] (II) LoadModule: "extmod"
[    38.875] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    38.875] (II) Module extmod: vendor="X.Org Foundation"
[    38.875]     compiled for 1.11.3, module version = 1.0.0
[    38.875]     Module class: X.Org Server Extension
[    38.875]     ABI class: X.Org Server Extension, version 6.0
[    38.875] (II) Loading extension MIT-SCREEN-SAVER
[    38.875] (II) Loading extension XFree86-VidModeExtension
[    38.875] (II) Loading extension XFree86-DGA
[    38.875] (II) Loading extension DPMS
[    38.875] (II) Loading extension XVideo
[    38.875] (II) Loading extension XVideo-MotionCompensation
[    38.875] (II) Loading extension X-Resource
[    38.875] (II) LoadModule: "dbe"
[    38.875] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    38.875] (II) Module dbe: vendor="X.Org Foundation"
[    38.875]     compiled for 1.11.3, module version = 1.0.0
[    38.875]     Module class: X.Org Server Extension
[    38.875]     ABI class: X.Org Server Extension, version 6.0
[    38.875] (II) Loading extension DOUBLE-BUFFER
[    38.875] (II) LoadModule: "glx"
[    38.876] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    38.876] (II) Module glx: vendor="X.Org Foundation"
[    38.876]     compiled for 1.11.3, module version = 1.0.0
[    38.876]     ABI class: X.Org Server Extension, version 6.0
[    38.876] (==) AIGLX enabled
[    38.876] (II) Loading extension GLX
[    38.876] (II) LoadModule: "record"
[    38.876] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    38.876] (II) Module record: vendor="X.Org Foundation"
[    38.876]     compiled for 1.11.3, module version = 1.13.0
[    38.876]     Module class: X.Org Server Extension
[    38.876]     ABI class: X.Org Server Extension, version 6.0
[    38.876] (II) Loading extension RECORD
[    38.876] (II) LoadModule: "dri"
[    38.876] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    38.877] (II) Module dri: vendor="X.Org Foundation"
[    38.877]     compiled for 1.11.3, module version = 1.0.0
[    38.877]     ABI class: X.Org Server Extension, version 6.0
[    38.877] (II) Loading extension XFree86-DRI
[    38.877] (II) LoadModule: "dri2"
[    38.877] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    38.877] (II) Module dri2: vendor="X.Org Foundation"
[    38.877]     compiled for 1.11.3, module version = 1.2.0
[    38.877]     ABI class: X.Org Server Extension, version 6.0
[    38.877] (II) Loading extension DRI2
[    38.877] (II) LoadModule: "nvidia"
[    38.877] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    38.878] (II) Module nvidia: vendor="NVIDIA Corporation"
[    38.878]     compiled for 4.0.2, module version = 1.0.0
[    38.878]     Module class: X.Org Video Driver
[    38.878] (II) NVIDIA dlloader X Driver  319.17  Thu Apr 25 21:23:57 PDT 2013
[    38.878] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    38.878] (++) using VT number 7

[    38.882] (II) Loading sub module "fb"
[    38.882] (II) LoadModule: "fb"
[    38.883] (II) Loading /usr/lib/xorg/modules/libfb.so
[    38.883] (II) Module fb: vendor="X.Org Foundation"
[    38.883]     compiled for 1.11.3, module version = 1.0.0
[    38.883]     ABI class: X.Org ANSI C Emulation, version 0.4
[    38.883] (II) Loading sub module "wfb"
[    38.883] (II) LoadModule: "wfb"
[    38.883] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    38.883] (II) Module wfb: vendor="X.Org Foundation"
[    38.883]     compiled for 1.11.3, module version = 1.0.0
[    38.883]     ABI class: X.Org ANSI C Emulation, version 0.4
[    38.883] (II) Loading sub module "shadow"
[    38.883] (II) LoadModule: "shadow"
[    38.884] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    38.884] (II) Module shadow: vendor="X.Org Foundation"
[    38.884]     compiled for 1.11.3, module version = 1.1.0
[    38.884]     ABI class: X.Org ANSI C Emulation, version 0.4
[    38.884] (II) Loading sub module "ramdac"
[    38.884] (II) LoadModule: "ramdac"
[    38.884] (II) Module "ramdac" already built-in
[    38.884] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    38.884] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    38.884] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    38.884] (II) Loading /usr/lib/xorg/modules/libfb.so
[    38.884] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    38.884] (==) NVIDIA(0): RGB weight 888
[    38.884] (==) NVIDIA(0): Default visual is TrueColor
[    38.884] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    38.884] (**) NVIDIA(0): Option "NoLogo" "True"
[    38.884] (**) NVIDIA(0): Enabling 2D acceleration
[    38.884] (EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
[    38.884] (EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
[    38.884] (EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
[    38.884] (EE) NVIDIA(0):     you continue to encounter problems, Please try
[    38.884] (EE) NVIDIA(0):     reinstalling the NVIDIA driver.
[    39.174] drmOpenDevice: node name is /dev/dri/card0
[    39.178] drmOpenByBusid: Searching for BusID PCI:1:0:0
[    39.178] drmOpenDevice: node name is /dev/dri/card0
[    39.182] drmOpenByBusid: drmOpenMinor returns -1
[    39.182] drmOpenDevice: node name is /dev/dri/card1
[    39.186] drmOpenByBusid: drmOpenMinor returns -1
[    39.186] drmOpenDevice: node name is /dev/dri/card2
[    39.190] drmOpenByBusid: drmOpenMinor returns -1
[    39.190] drmOpenDevice: node name is /dev/dri/card3
[    39.194] drmOpenByBusid: drmOpenMinor returns -1
[    39.194] drmOpenDevice: node name is /dev/dri/card4
[    39.198] drmOpenByBusid: drmOpenMinor returns -1
[    39.198] drmOpenDevice: node name is /dev/dri/card5
[    39.203] drmOpenByBusid: drmOpenMinor returns -1
[    39.203] drmOpenDevice: node name is /dev/dri/card6
[    39.206] drmOpenByBusid: drmOpenMinor returns -1
[    39.207] drmOpenDevice: node name is /dev/dri/card7
[    39.211] drmOpenByBusid: drmOpenMinor returns -1
[    39.211] drmOpenDevice: node name is /dev/dri/card8
[    39.215] drmOpenByBusid: drmOpenMinor returns -1
[    39.215] drmOpenDevice: node name is /dev/dri/card9
[    39.219] drmOpenByBusid: drmOpenMinor returns -1
[    39.219] drmOpenDevice: node name is /dev/dri/card10
[    39.223] drmOpenByBusid: drmOpenMinor returns -1
[    39.223] drmOpenDevice: node name is /dev/dri/card11
[    39.228] drmOpenByBusid: drmOpenMinor returns -1
[    39.228] drmOpenDevice: node name is /dev/dri/card12
[    39.232] drmOpenByBusid: drmOpenMinor returns -1
[    39.232] drmOpenDevice: node name is /dev/dri/card13
[    39.236] drmOpenByBusid: drmOpenMinor returns -1
[    39.236] drmOpenDevice: node name is /dev/dri/card14
[    39.240] drmOpenByBusid: drmOpenMinor returns -1
[    39.240] drmOpenDevice: node name is /dev/dri/card15
[    39.244] drmOpenByBusid: drmOpenMinor returns -1
[    39.296] (II) NVIDIA(GPU-0): Display (Acer X203W (CRT-1)) does not support NVIDIA 3D Vision
[    39.296] (II) NVIDIA(GPU-0):     stereo.
[    39.298] (II) NVIDIA(0): NVIDIA GPU GeForce 210 (GT218) at PCI:1:0:0 (GPU-0)
[    39.298] (--) NVIDIA(0): Memory: 1048576 kBytes
[    39.298] (--) NVIDIA(0): VideoBIOS: 70.18.70.00.06
[    39.298] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    39.300] (--) NVIDIA(0): Valid display device(s) on GeForce 210 at PCI:1:0:0
[    39.300] (--) NVIDIA(0):     CRT-0
[    39.300] (--) NVIDIA(0):     Acer X203W (CRT-1) (boot, connected)
[    39.300] (--) NVIDIA(0):     DFP-0
[    39.300] (--) NVIDIA(0):     DFP-1
[    39.300] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    39.300] (--) NVIDIA(0): Acer X203W (CRT-1): 400.0 MHz maximum pixel clock
[    39.300] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    39.300] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    39.300] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    39.300] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    39.300] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    39.300] (**) NVIDIA(0):     device Acer X203W (CRT-1) (Using EDID frequencies has been
[    39.300] (**) NVIDIA(0):     enabled on all display devices.)
[    39.303] (==) NVIDIA(0): 
[    39.303] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    39.303] (==) NVIDIA(0):     will be used as the requested mode.
[    39.303] (==) NVIDIA(0): 
[    39.303] (II) NVIDIA(0): Validated MetaModes:
[    39.303] (II) NVIDIA(0):     "CRT-1:nvidia-auto-select{}"
[    39.303] (II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
[    39.336] (--) NVIDIA(0): DPI set to (99, 98); computed from "UseEdidDpi" X config
[    39.336] (--) NVIDIA(0):     option
[    39.336] (--) Depth 24 pixmap format is 32 bpp
[    39.336] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    39.341] (II) NVIDIA(0): Setting mode "CRT-1:nvidia-auto-select{}"
[    39.367] (II) Loading extension NV-GLX
[    39.391] (==) NVIDIA(0): Disabling shared memory pixmaps
[    39.391] (==) NVIDIA(0): Backing store disabled
[    39.391] (==) NVIDIA(0): Silken mouse enabled
[    39.391] (**) NVIDIA(0): DPMS enabled
[    39.392] (II) Loading extension NV-CONTROL
[    39.392] (II) Loading extension XINERAMA
[    39.392] (II) Loading sub module "dri2"
[    39.392] (II) LoadModule: "dri2"
[    39.392] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    39.392] (II) Module dri2: vendor="X.Org Foundation"
[    39.392]     compiled for 1.11.3, module version = 1.2.0
[    39.392]     ABI class: X.Org Server Extension, version 6.0
[    39.392] (II) NVIDIA(0): [DRI2] Setup complete
[    39.392] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    39.392] (--) RandR disabled
[    39.392] (II) Initializing built-in extension Generic Event Extension
[    39.392] (II) Initializing built-in extension SHAPE
[    39.392] (II) Initializing built-in extension MIT-SHM
[    39.392] (II) Initializing built-in extension XInputExtension
[    39.392] (II) Initializing built-in extension XTEST
[    39.392] (II) Initializing built-in extension BIG-REQUESTS
[    39.392] (II) Initializing built-in extension SYNC
[    39.392] (II) Initializing built-in extension XKEYBOARD
[    39.392] (II) Initializing built-in extension XC-MISC
[    39.392] (II) Initializing built-in extension SECURITY
[    39.392] (II) Initializing built-in extension XINERAMA
[    39.392] (II) Initializing built-in extension XFIXES
[    39.392] (II) Initializing built-in extension RENDER
[    39.392] (II) Initializing built-in extension RANDR
[    39.393] (II) Initializing built-in extension COMPOSITE
[    39.393] (II) Initializing built-in extension DAMAGE
[    39.400] (II) AIGLX: Screen 0 is not DRI2 capable
[    39.400] (II) AIGLX: Screen 0 is not DRI capable
[    39.417] (II) AIGLX: Loaded and initialized swrast
[    39.417] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    39.435] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    39.440] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    39.440] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    39.440] (II) LoadModule: "evdev"
[    39.441] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    39.441] (II) Module evdev: vendor="X.Org Foundation"
[    39.441]     compiled for 1.11.3, module version = 2.7.0
[    39.441]     Module class: X.Org XInput Driver
[    39.441]     ABI class: X.Org XInput driver, version 16.0
[    39.441] (II) Using input driver 'evdev' for 'Power Button'
[    39.441] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    39.441] (**) Power Button: always reports core events
[    39.441] (**) evdev: Power Button: Device: "/dev/input/event1"
[    39.441] (--) evdev: Power Button: Vendor 0 Product 0x1
[    39.441] (--) evdev: Power Button: Found keys
[    39.441] (II) evdev: Power Button: Configuring as keyboard
[    39.441] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    39.441] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    39.441] (**) Option "xkb_rules" "evdev"
[    39.441] (**) Option "xkb_model" "pc105"
[    39.441] (**) Option "xkb_layout" "es"
[    39.446] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[    39.448] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    39.448] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    39.448] (II) Using input driver 'evdev' for 'Power Button'
[    39.448] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    39.448] (**) Power Button: always reports core events
[    39.448] (**) evdev: Power Button: Device: "/dev/input/event0"
[    39.448] (--) evdev: Power Button: Vendor 0 Product 0x1
[    39.448] (--) evdev: Power Button: Found keys
[    39.448] (II) evdev: Power Button: Configuring as keyboard
[    39.448] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    39.448] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    39.448] (**) Option "xkb_rules" "evdev"
[    39.448] (**) Option "xkb_model" "pc105"
[    39.448] (**) Option "xkb_layout" "es"
[    39.449] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event5)
[    39.449] (II) No input driver specified, ignoring this device.
[    39.449] (II) This device may have been added with another device file.
[    39.449] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event6)
[    39.449] (II) No input driver specified, ignoring this device.
[    39.449] (II) This device may have been added with another device file.
[    39.450] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event7)
[    39.450] (II) No input driver specified, ignoring this device.
[    39.450] (II) This device may have been added with another device file.
[    39.450] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event8)
[    39.450] (II) No input driver specified, ignoring this device.
[    39.450] (II) This device may have been added with another device file.
[    39.451] (II) config/udev: Adding input device Wacom Bamboo 2FG 4x5 Pen (/dev/input/event3)
[    39.451] (**) Wacom Bamboo 2FG 4x5 Pen: Applying InputClass "evdev tablet catchall"
[    39.451] (**) Wacom Bamboo 2FG 4x5 Pen: Applying InputClass "Wacom class"
[    39.451] (II) LoadModule: "wacom"
[    39.451] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    39.451] (II) Module wacom: vendor="X.Org Foundation"
[    39.451]     compiled for 1.11.3, module version = 0.14.0
[    39.451]     Module class: X.Org XInput Driver
[    39.451]     ABI class: X.Org XInput driver, version 16.0
[    39.452] (II) Using input driver 'wacom' for 'Wacom Bamboo 2FG 4x5 Pen'
[    39.452] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    39.452] (**) Wacom Bamboo 2FG 4x5 Pen: always reports core events
[    39.452] (**) Option "Device" "/dev/input/event3"
[    39.452] (II) Wacom Bamboo 2FG 4x5 Pen: type not specified, assuming 'stylus'.
[    39.452] (II) Wacom Bamboo 2FG 4x5 Pen: other types will be automatically added.
[    39.452] (--) Wacom Bamboo 2FG 4x5 Pen stylus: using pressure threshold of 27 for button 1
[    39.452] (--) Wacom Bamboo 2FG 4x5 Pen stylus: Wacom USB Bamboo tablet maxX=14720 maxY=9200 maxZ=1023 resX=100000 resY=100000  tilt=disabled
[    39.452] (II) Wacom Bamboo 2FG 4x5 Pen stylus: hotplugging dependent devices.
[    39.452] (EE) Wacom Bamboo 2FG 4x5 Pen stylus: Invalid type 'cursor' for this device.
[    39.452] (EE) Wacom Bamboo 2FG 4x5 Pen stylus: Invalid type 'touch' for this device.
[    39.452] (EE) Wacom Bamboo 2FG 4x5 Pen stylus: Invalid type 'pad' for this device.
[    39.452] (II) Wacom Bamboo 2FG 4x5 Pen stylus: hotplugging completed.
[    39.464] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3/event3"
[    39.464] (II) XINPUT: Adding extended input device "Wacom Bamboo 2FG 4x5 Pen stylus" (type: STYLUS, id 8)
[    39.464] (**) Wacom Bamboo 2FG 4x5 Pen stylus: (accel) keeping acceleration scheme 1
[    39.464] (**) Wacom Bamboo 2FG 4x5 Pen stylus: (accel) acceleration profile 0
[    39.464] (**) Wacom Bamboo 2FG 4x5 Pen stylus: (accel) acceleration factor: 2.000
[    39.464] (**) Wacom Bamboo 2FG 4x5 Pen stylus: (accel) acceleration threshold: 4
[    39.465] (II) config/udev: Adding input device Wacom Bamboo 2FG 4x5 Pen (/dev/input/mouse0)
[    39.465] (II) No input driver specified, ignoring this device.
[    39.465] (II) This device may have been added with another device file.
[    39.466] (II) config/udev: Adding input device Wacom Bamboo 2FG 4x5 Finger (/dev/input/event4)
[    39.466] (**) Wacom Bamboo 2FG 4x5 Finger: Applying InputClass "evdev touchpad catchall"
[    39.466] (**) Wacom Bamboo 2FG 4x5 Finger: Applying InputClass "touchpad catchall"
[    39.466] (**) Wacom Bamboo 2FG 4x5 Finger: Applying InputClass "Wacom class"
[    39.466] (II) Using input driver 'wacom' for 'Wacom Bamboo 2FG 4x5 Finger'
[    39.466] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    39.466] (**) Wacom Bamboo 2FG 4x5 Finger: always reports core events
[    39.466] (**) Option "Device" "/dev/input/event4"
[    39.466] (EE) Wacom Bamboo 2FG 4x5 Finger: Invalid type 'stylus' for this device.
[    39.466] (EE) Wacom Bamboo 2FG 4x5 Finger: Invalid type 'eraser' for this device.
[    39.466] (EE) Wacom Bamboo 2FG 4x5 Finger: Invalid type 'cursor' for this device.
[    39.466] (II) Wacom Bamboo 2FG 4x5 Finger: type not specified, assuming 'touch'.
[    39.466] (II) Wacom Bamboo 2FG 4x5 Finger: other types will be automatically added.
[    39.466] (--) Wacom Bamboo 2FG 4x5 Finger touch: using pressure threshold of 27 for button 1
[    39.466] (--) Wacom Bamboo 2FG 4x5 Finger touch: Wacom USB Bamboo tablet maxX=15360 maxY=10240 maxZ=0 resX=128000 resY=128000 
[    39.466] (II) Wacom Bamboo 2FG 4x5 Finger touch: hotplugging dependent devices.
[    39.466] (EE) Wacom Bamboo 2FG 4x5 Finger touch: Invalid type 'stylus' for this device.
[    39.466] (EE) Wacom Bamboo 2FG 4x5 Finger touch: Invalid type 'eraser' for this device.
[    39.466] (EE) Wacom Bamboo 2FG 4x5 Finger touch: Invalid type 'cursor' for this device.
[    39.466] (II) Wacom Bamboo 2FG 4x5 Finger touch: hotplugging completed.
[    39.484] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input4/event4"
[    39.484] (II) XINPUT: Adding extended input device "Wacom Bamboo 2FG 4x5 Finger touch" (type: TOUCH, id 9)
[    39.484] (**) Wacom Bamboo 2FG 4x5 Finger touch: (accel) keeping acceleration scheme 1
[    39.484] (**) Wacom Bamboo 2FG 4x5 Finger touch: (accel) acceleration profile 0
[    39.484] (**) Wacom Bamboo 2FG 4x5 Finger touch: (accel) acceleration factor: 2.000
[    39.484] (**) Wacom Bamboo 2FG 4x5 Finger touch: (accel) acceleration threshold: 4
[    39.485] (II) config/udev: Adding input device Wacom Bamboo 2FG 4x5 Finger (/dev/input/mouse1)
[    39.485] (**) Wacom Bamboo 2FG 4x5 Finger: Ignoring device from InputClass "touchpad ignore duplicates"
[    39.485] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    39.485] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    39.485] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    39.486] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    39.486] (**) AT Translated Set 2 keyboard: always reports core events
[    39.486] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    39.486] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    39.486] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    39.486] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    39.486] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    39.486] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    39.486] (**) Option "xkb_rules" "evdev"
[    39.486] (**) Option "xkb_model" "pc105"
[    39.486] (**) Option "xkb_layout" "es"
[    39.487] (II) config/udev: Adding input device ImExPS/2 Logitech Explorer Mouse (/dev/input/event9)
[    39.487] (**) ImExPS/2 Logitech Explorer Mouse: Applying InputClass "evdev pointer catchall"
[    39.487] (II) Using input driver 'evdev' for 'ImExPS/2 Logitech Explorer Mouse'
[    39.487] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    39.487] (**) ImExPS/2 Logitech Explorer Mouse: always reports core events
[    39.487] (**) evdev: ImExPS/2 Logitech Explorer Mouse: Device: "/dev/input/event9"
[    39.487] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Vendor 0x2 Product 0x6
[    39.487] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Found 9 mouse buttons
[    39.487] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Found scroll wheel(s)
[    39.487] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Found relative axes
[    39.487] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Found x and y relative axes
[    39.487] (II) evdev: ImExPS/2 Logitech Explorer Mouse: Configuring as mouse
[    39.487] (II) evdev: ImExPS/2 Logitech Explorer Mouse: Adding scrollwheel support
[    39.487] (**) evdev: ImExPS/2 Logitech Explorer Mouse: YAxisMapping: buttons 4 and 5
[    39.487] (**) evdev: ImExPS/2 Logitech Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    39.487] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[    39.488] (II) XINPUT: Adding extended input device "ImExPS/2 Logitech Explorer Mouse" (type: MOUSE, id 11)
[    39.488] (II) evdev: ImExPS/2 Logitech Explorer Mouse: initialized for relative axes.
[    39.488] (**) ImExPS/2 Logitech Explorer Mouse: (accel) keeping acceleration scheme 1
[    39.488] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration profile 0
[    39.488] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration factor: 2.000
[    39.488] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration threshold: 4
[    39.489] (II) config/udev: Adding input device ImExPS/2 Logitech Explorer Mouse (/dev/input/mouse2)
[    39.489] (II) No input driver specified, ignoring this device.
[    39.489] (II) This device may have been added with another device file.
[    39.497] (**) Wacom Bamboo 2FG 4x5 Pen eraser: Applying InputClass "evdev tablet catchall"
[    39.497] (**) Wacom Bamboo 2FG 4x5 Pen eraser: Applying InputClass "Wacom class"
[    39.497] (II) Using input driver 'wacom' for 'Wacom Bamboo 2FG 4x5 Pen eraser'
[    39.497] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    39.497] (**) Wacom Bamboo 2FG 4x5 Pen eraser: always reports core events
[    39.497] (**) Option "Device" "/dev/input/event3"
[    39.497] (**) Option "Type" "eraser"
[    39.497] (--) Wacom Bamboo 2FG 4x5 Pen eraser: Wacom USB Bamboo tablet maxX=14720 maxY=9200 maxZ=1023 resX=100000 resY=100000  tilt=disabled
[    39.509] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3/event3"
[    39.509] (II) XINPUT: Adding extended input device "Wacom Bamboo 2FG 4x5 Pen eraser" (type: ERASER, id 12)
[    39.509] (**) Wacom Bamboo 2FG 4x5 Pen eraser: (accel) keeping acceleration scheme 1
[    39.509] (**) Wacom Bamboo 2FG 4x5 Pen eraser: (accel) acceleration profile 0
[    39.509] (**) Wacom Bamboo 2FG 4x5 Pen eraser: (accel) acceleration factor: 2.000
[    39.509] (**) Wacom Bamboo 2FG 4x5 Pen eraser: (accel) acceleration threshold: 4
[    39.509] (**) Wacom Bamboo 2FG 4x5 Finger pad: Applying InputClass "evdev touchpad catchall"
[    39.509] (**) Wacom Bamboo 2FG 4x5 Finger pad: Applying InputClass "touchpad catchall"
[    39.509] (**) Wacom Bamboo 2FG 4x5 Finger pad: Applying InputClass "Wacom class"
[    39.509] (II) Using input driver 'wacom' for 'Wacom Bamboo 2FG 4x5 Finger pad'
[    39.509] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    39.509] (**) Wacom Bamboo 2FG 4x5 Finger pad: always reports core events
[    39.510] (**) Option "Device" "/dev/input/event4"
[    39.510] (**) Option "Type" "pad"
[    39.510] (--) Wacom Bamboo 2FG 4x5 Finger pad: Wacom USB Bamboo tablet maxX=15360 maxY=10240 maxZ=0 resX=128000 resY=128000 
[    39.526] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input4/event4"
[    39.526] (II) XINPUT: Adding extended input device "Wacom Bamboo 2FG 4x5 Finger pad" (type: PAD, id 13)
[    39.526] (**) Wacom Bamboo 2FG 4x5 Finger pad: (accel) keeping acceleration scheme 1
[    39.526] (**) Wacom Bamboo 2FG 4x5 Finger pad: (accel) acceleration profile 0
[    39.526] (**) Wacom Bamboo 2FG 4x5 Finger pad: (accel) acceleration factor: 2.000
[    39.526] (**) Wacom Bamboo 2FG 4x5 Finger pad: (accel) acceleration threshold: 4
[    85.983] (II) Open ACPI successful (/var/run/acpid.socket)
[    86.038] (II) NVIDIA(0): Setting mode "CRT-1:nvidia-auto-select{}"
[    86.167] (II) NVIDIA(GPU-0): Display (Acer X203W (CRT-1)) does not support NVIDIA 3D Vision
[    86.167] (II) NVIDIA(GPU-0):     stereo.
[    86.167] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    86.167] (**) NVIDIA(0):     device Acer X203W (CRT-1) (Using EDID frequencies has been
[    86.167] (**) NVIDIA(0):     enabled on all display devices.)
[    94.155] (II) NVIDIA(GPU-0): Display (Acer X203W (CRT-1)) does not support NVIDIA 3D Vision
[    94.155] (II) NVIDIA(GPU-0):     stereo.
[    94.155] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    94.155] (**) NVIDIA(0):     device Acer X203W (CRT-1) (Using EDID frequencies has been
[    94.155] (**) NVIDIA(0):     enabled on all display devices.)
[    94.196] (II) NVIDIA(GPU-0): Display (Acer X203W (CRT-1)) does not support NVIDIA 3D Vision
[    94.197] (II) NVIDIA(GPU-0):     stereo.
[    94.197] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    94.197] (**) NVIDIA(0):     device Acer X203W (CRT-1) (Using EDID frequencies has been
[    94.197] (**) NVIDIA(0):     enabled on all display devices.)
[    94.203] (II) NVIDIA(0): Setting mode "VGA-0: nvidia-auto-select @1680x1050 +0+0 {ViewPortIn=1680x1050, ViewPortOut=1680x1050+0+0}"
[    94.247] (II) NVIDIA(GPU-0): Display (Acer X203W (CRT-1)) does not support NVIDIA 3D Vision
[    94.248] (II) NVIDIA(GPU-0):     stereo.
[    94.248] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    94.248] (**) NVIDIA(0):     device Acer X203W (CRT-1) (Using EDID frequencies has been
[    94.248] (**) NVIDIA(0):     enabled on all display devices.)
[    94.285] (II) NVIDIA(GPU-0): Display (Acer X203W (CRT-1)) does not support NVIDIA 3D Vision
[    94.285] (II) NVIDIA(GPU-0):     stereo.
[    94.285] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    94.285] (**) NVIDIA(0):     device Acer X203W (CRT-1) (Using EDID frequencies has been
[    94.285] (**) NVIDIA(0):     enabled on all display devices.)
[    94.861] (II) NVIDIA(GPU-0): Display (Acer X203W (CRT-1)) does not support NVIDIA 3D Vision
[    94.861] (II) NVIDIA(GPU-0):     stereo.
[    94.861] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    94.861] (**) NVIDIA(0):     device Acer X203W (CRT-1) (Using EDID frequencies has been
[    94.861] (**) NVIDIA(0):     enabled on all display devices.)
[    96.390] (II) NVIDIA(GPU-0): Display (Acer X203W (CRT-1)) does not support NVIDIA 3D Vision
[    96.390] (II) NVIDIA(GPU-0):     stereo.
[    96.390] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    96.390] (**) NVIDIA(0):     device Acer X203W (CRT-1) (Using EDID frequencies has been
 [    96.390] (**) NVIDIA(0):     enabled on all display devices.)
```

Hope  someone can help, thanks in advance, and excuse my english.

---

### Post by brabender on 2013-10-23
If it's of interest to anyone, I solved the problem removing Compiz and installing the latest NVidia drivers from the console. After that, I logged normally, reinstalled Compiz and everything seems to be OK

---

