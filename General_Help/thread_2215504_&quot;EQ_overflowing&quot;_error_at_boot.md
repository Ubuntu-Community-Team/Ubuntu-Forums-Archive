---
title: "&quot;EQ overflowing&quot; error at boot"
date: 2014-04-07
forum: General Help
---

### Post by grumblebum2 on 2014-04-07
Ububtu 13.10 been running fine but now stalls at error mesage before I get to the greeter.
```
System is running in low graphics mode.
(EE) [mi] EQ overflowing.  Additional events will be discarded until existing events are processed.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x3d) [0x7ff00adcafdd]
(EE) 1: /usr/bin/X (mieqEnqueue+0x22b) [0x7ff00adacf1b]
(EE) 2: /usr/bin/X (QueuePointerEvents+0x52) [0x7ff00ac93a92]
(EE) 3: /usr/lib/xorg/modules/input/evdev_drv.so (0x7ff000e25000+0x566f) [0x7ff000e2a66f]
(EE) 4: /usr/bin/X (0x7ff00ac28000+0x91ee8) [0x7ff00acb9ee8]
(EE) 5: /usr/bin/X (0x7ff00ac28000+0xba930) [0x7ff00ace2930]
(EE) 6: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7ff009d28000+0xfbb0) [0x7ff009d37bb0]
(EE) 7: /lib/x86_64-linux-gnu/libc.so.6 (0x7ff008942000+0x7fbb6) [0x7ff0089c1bb6]
(EE) 8: /lib/x86_64-linux-gnu/libc.so.6 (0x7ff008942000+0x810e1) [0x7ff0089c30e1]
(EE) 9: /lib/x86_64-linux-gnu/libc.so.6 (__libc_calloc+0xbf) [0x7ff0089c606f]
(EE) 10: /usr/bin/X (0x7ff00ac28000+0x7cf6d) [0x7ff00aca4f6d]
(EE) 11: /usr/bin/X (CloseDownClient+0x57) [0x7ff00ac7c727]
(EE) 12: /usr/bin/X (0x7ff00ac28000+0x55194) [0x7ff00ac7d194]
(EE) 13: /usr/bin/X (0x7ff00ac28000+0x447ba) [0x7ff00ac6c7ba]
(EE) 14: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7ff008963de5]
(EE) 15: /usr/bin/X (0x7ff00ac28000+0x44aff) [0x7ff00ac6caff]
(EE) 
(EE) [mi] These backtraces from mieqEnqueue may point to a culprit higher up the stack.
(EE) [mi] mieq is *NOT* the cause.  It is a victim.
[ 35479.423] [mi] Increasing EQ size to 512 to prevent dropped events.
[ 35479.423] [mi] EQ processing has resumed after 15 dropped events.
[ 35479.423] [mi] This may be caused my a misbehaving driver monopolizing the server's resources.
```

Tried booting in failsafe graphics mode ....same result.
Unplugged mouse and keyboard....same result.
Ran a disk check...ok.

I have other installs including 14.04 which I can boot into no problem.
I can boot into an ubuntustudio install on the same disk.

I checked my disk usage....
```
glen@Trusty:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb5        52G  6.6G   43G  14% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            987M   12K  987M   1% /dev
tmpfs           201M  1.2M  199M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1001M  148K 1001M   1% /run/shm
none            100M   80K  100M   1% /run/user
/dev/sdc7       269G   67G  189G  27% /media/Data
[COLOR="#FF0000"]/dev/sdc1        38G   10G   26G  29% /media/glen/SaucySys[/COLOR]
/dev/sdc2        49G  1.7G   45G   4% /media/glen/Saucy
```


What should I be looking at?
Xorg.0.log
```
[ 35221.157] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[ 35221.157] X Protocol Version 11, Revision 0
[ 35221.157] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[ 35221.157] Current Operating System: Linux Saucy 3.11.0-19-generic #33-Ubuntu SMP Tue Mar 11 18:48:34 UTC 2014 x86_64
[ 35221.157] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-19-generic root=UUID=34354461-99dc-4fd8-8122-53365f2e6770 ro quiet splash vt.handoff=7
[ 35221.157] Build Date: 17 December 2013  10:06:15AM
[ 35221.157] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see http://www.ubuntu.com/support) 
[ 35221.157] Current version of pixman: 0.30.2
[ 35221.157] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[ 35221.157] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 35221.158] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr  7 11:43:09 2014
[ 35221.179] (==) Using config file: "/etc/X11/xorg.conf"
[ 35221.179] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 35221.209] (==) ServerLayout "Layout0"
[ 35221.209] (**) |-->Screen "Screen0" (0)
[ 35221.209] (**) |   |-->Monitor "Monitor0"
[ 35221.209] (**) |   |-->Device "Device0"
[ 35221.210] (**) |-->Input Device "Keyboard0"
[ 35221.210] (**) |-->Input Device "Mouse0"
[ 35221.210] (==) Automatically adding devices
[ 35221.210] (==) Automatically enabling devices
[ 35221.210] (==) Automatically adding GPU devices
[ 35221.210] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 35221.210] 	Entry deleted from font path.
[ 35221.210] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 35221.210] 	Entry deleted from font path.
[ 35221.210] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 35221.210] 	Entry deleted from font path.
[ 35221.210] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 35221.210] 	Entry deleted from font path.
[ 35221.210] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 35221.210] 	Entry deleted from font path.
[ 35221.210] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[ 35221.210] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 35221.210] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[ 35221.210] (WW) Disabling Keyboard0
[ 35221.210] (WW) Disabling Mouse0
[ 35221.210] (II) Loader magic: 0x7ff00b04bd20
[ 35221.210] (II) Module ABI versions:
[ 35221.210] 	X.Org ANSI C Emulation: 0.4
[ 35221.210] 	X.Org Video Driver: 14.1
[ 35221.210] 	X.Org XInput driver : 19.1
[ 35221.210] 	X.Org Server Extension : 7.0
[ 35221.211] (II) xfree86: Adding drm device (/dev/dri/card0)
[ 35221.213] (--) PCI:*(0:1:0:0) 10de:1244:1458:351a rev 161, Mem @ 0xf8000000/33554432, 0xc8000000/134217728, 0xd4000000/67108864, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
[ 35221.213] (II) Open ACPI successful (/var/run/acpid.socket)
[ 35221.217] Initializing built-in extension Generic Event Extension
[ 35221.217] Initializing built-in extension SHAPE
[ 35221.217] Initializing built-in extension MIT-SHM
[ 35221.217] Initializing built-in extension XInputExtension
[ 35221.217] Initializing built-in extension XTEST
[ 35221.217] Initializing built-in extension BIG-REQUESTS
[ 35221.217] Initializing built-in extension SYNC
[ 35221.217] Initializing built-in extension XKEYBOARD
[ 35221.217] Initializing built-in extension XC-MISC
[ 35221.217] Initializing built-in extension SECURITY
[ 35221.217] Initializing built-in extension XINERAMA
[ 35221.217] Initializing built-in extension XFIXES
[ 35221.217] Initializing built-in extension RENDER
[ 35221.218] Initializing built-in extension RANDR
[ 35221.218] Initializing built-in extension COMPOSITE
[ 35221.218] Initializing built-in extension DAMAGE
[ 35221.218] Initializing built-in extension MIT-SCREEN-SAVER
[ 35221.218] Initializing built-in extension DOUBLE-BUFFER
[ 35221.218] Initializing built-in extension RECORD
[ 35221.218] Initializing built-in extension DPMS
[ 35221.218] Initializing built-in extension X-Resource
[ 35221.218] Initializing built-in extension XVideo
[ 35221.218] Initializing built-in extension XVideo-MotionCompensation
[ 35221.218] Initializing built-in extension SELinux
[ 35221.218] Initializing built-in extension XFree86-VidModeExtension
[ 35221.218] Initializing built-in extension XFree86-DGA
[ 35221.218] Initializing built-in extension XFree86-DRI
[ 35221.218] Initializing built-in extension DRI2
[ 35221.218] (II) "glx" will be loaded by default.
[ 35221.218] (WW) "xmir" is not to be loaded by default. Skipping.
[ 35221.218] (II) LoadModule: "dri2"
[ 35221.218] (II) Module "dri2" already built-in
[ 35221.218] (II) LoadModule: "glamoregl"
[ 35221.249] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[ 35221.297] (II) Module glamoregl: vendor="X.Org Foundation"
[ 35221.297] 	compiled for 1.14.3, module version = 0.5.1
[ 35221.297] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 35221.297] (II) LoadModule: "glx"
[ 35221.297] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[ 35221.402] (II) Module glx: vendor="NVIDIA Corporation"
[ 35221.402] 	compiled for 4.0.2, module version = 1.0.0
[ 35221.402] 	Module class: X.Org Server Extension
[ 35221.402] (II) NVIDIA GLX Module  319.32  Wed Jun 19 14:55:38 PDT 2013
[ 35221.402] Loading extension GLX
[ 35221.402] (II) LoadModule: "nvidia"
[ 35221.402] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[ 35221.441] (II) Module nvidia: vendor="NVIDIA Corporation"
[ 35221.441] 	compiled for 4.0.2, module version = 1.0.0
[ 35221.441] 	Module class: X.Org Video Driver
[ 35221.452] (II) NVIDIA dlloader X Driver  319.32  Wed Jun 19 14:34:12 PDT 2013
[ 35221.452] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[ 35221.452] (++) using VT number 7

[ 35221.453] (II) Loading sub module "fb"
[ 35221.453] (II) LoadModule: "fb"
[ 35221.476] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 35221.492] (II) Module fb: vendor="X.Org Foundation"
[ 35221.492] 	compiled for 1.14.5, module version = 1.0.0
[ 35221.492] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 35221.493] (WW) Unresolved symbol: fbGetGCPrivateKey
[ 35221.493] (II) Loading sub module "wfb"
[ 35221.493] (II) LoadModule: "wfb"
[ 35221.493] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 35221.507] (II) Module wfb: vendor="X.Org Foundation"
[ 35221.507] 	compiled for 1.14.5, module version = 1.0.0
[ 35221.507] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 35221.507] (II) Loading sub module "shadow"
[ 35221.507] (II) LoadModule: "shadow"
[ 35221.508] (II) Loading /usr/lib/xorg/modules/libshadow.so
[ 35221.518] (II) Module shadow: vendor="X.Org Foundation"
[ 35221.518] 	compiled for 1.14.5, module version = 1.1.0
[ 35221.518] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 35221.518] (II) Loading sub module "ramdac"
[ 35221.518] (II) LoadModule: "ramdac"
[ 35221.518] (II) Module "ramdac" already built-in
[ 35221.519] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[ 35221.519] (==) NVIDIA(0): RGB weight 888
[ 35221.519] (==) NVIDIA(0): Default visual is TrueColor
[ 35221.519] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[ 35221.519] (**) NVIDIA(0): Enabling 2D acceleration
[ 35221.792] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[ 35221.792] (II) NVIDIA(GPU-0):     3D Vision stereo.
[ 35221.794] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 550 Ti (GF116) at PCI:1:0:0 (GPU-0)
[ 35221.794] (--) NVIDIA(0): Memory: 1048576 kBytes
[ 35221.794] (--) NVIDIA(0): VideoBIOS: 70.26.18.00.02
[ 35221.800] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[ 35221.801] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 550 Ti at PCI:1:0:0
[ 35221.801] (--) NVIDIA(0):     CRT-0
[ 35221.801] (--) NVIDIA(0):     CRT-1
[ 35221.801] (--) NVIDIA(0):     Samsung SyncMaster (DFP-0) (boot, connected)
[ 35221.801] (--) NVIDIA(0):     DFP-1
[ 35221.801] (--) NVIDIA(0):     DFP-2
[ 35221.801] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[ 35221.801] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[ 35221.801] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
[ 35221.801] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
[ 35221.801] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[ 35221.801] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[ 35221.801] (--) NVIDIA(0): DFP-2: 330.0 MHz maximum pixel clock
[ 35221.801] (--) NVIDIA(0): DFP-2: Internal Single Link TMDS
[ 35221.801] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 35221.801] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[ 35221.802] (**) NVIDIA(0):     has been enabled on all display devices.)
[ 35221.803] (==) NVIDIA(0): 
[ 35221.803] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[ 35221.803] (==) NVIDIA(0):     will be used as the requested mode.
[ 35221.803] (==) NVIDIA(0): 
[ 35221.803] (II) NVIDIA(0): Validated MetaModes:
[ 35221.803] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select{}"
[ 35221.803] (II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
[ 35221.836] (--) NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
[ 35221.836] (--) NVIDIA(0):     option
[ 35221.836] (--) Depth 24 pixmap format is 32 bpp
[ 35221.837] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[ 35221.837] (II) NVIDIA:     access.
[ 35221.842] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select{}"
[ 35221.898] Loading extension NV-GLX
[ 35221.954] (==) NVIDIA(0): Disabling shared memory pixmaps
[ 35221.954] (==) NVIDIA(0): Backing store disabled
[ 35221.954] (==) NVIDIA(0): Silken mouse enabled
[ 35221.955] (**) NVIDIA(0): DPMS enabled
[ 35222.000] Loading extension NV-CONTROL
[ 35222.000] Loading extension XINERAMA
[ 35222.000] (II) Loading sub module "dri2"
[ 35222.000] (II) LoadModule: "dri2"
[ 35222.000] (II) Module "dri2" already built-in
[ 35222.000] (II) NVIDIA(0): [DRI2] Setup complete
[ 35222.000] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[ 35222.001] (--) RandR disabled
[ 35222.007] (II) SELinux: Disabled on system
[ 35222.009] (II) Initializing extension GLX
[ 35222.061] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 35222.071] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 35222.071] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 35222.071] (II) LoadModule: "evdev"
[ 35222.071] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 35222.100] (II) Module evdev: vendor="X.Org Foundation"
[ 35222.100] 	compiled for 1.14.1, module version = 2.7.3
[ 35222.100] 	Module class: X.Org XInput Driver
[ 35222.100] 	ABI class: X.Org XInput driver, version 19.1
[ 35222.100] (II) Using input driver 'evdev' for 'Power Button'
[ 35222.100] (**) Power Button: always reports core events
[ 35222.100] (**) evdev: Power Button: Device: "/dev/input/event1"
[ 35222.100] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 35222.100] (--) evdev: Power Button: Found keys
[ 35222.100] (II) evdev: Power Button: Configuring as keyboard
[ 35222.101] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[ 35222.101] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[ 35222.101] (**) Option "xkb_rules" "evdev"
[ 35222.101] (**) Option "xkb_model" "pc105"
[ 35222.101] (**) Option "xkb_layout" "us"
[ 35222.102] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[ 35222.102] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 35222.102] (II) Using input driver 'evdev' for 'Power Button'
[ 35222.102] (**) Power Button: always reports core events
[ 35222.102] (**) evdev: Power Button: Device: "/dev/input/event0"
[ 35222.102] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 35222.102] (--) evdev: Power Button: Found keys
[ 35222.102] (II) evdev: Power Button: Configuring as keyboard
[ 35222.102] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[ 35222.102] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[ 35222.102] (**) Option "xkb_rules" "evdev"
[ 35222.102] (**) Option "xkb_model" "pc105"
[ 35222.102] (**) Option "xkb_layout" "us"
[ 35222.103] (II) config/udev: Adding drm device (/dev/dri/card0)
[ 35222.103] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[ 35222.104] (II) config/udev: Adding input device DEXIN Tt eSPORTS BLACK Gaming mouse (/dev/input/event5)
[ 35222.104] (**) DEXIN Tt eSPORTS BLACK Gaming mouse: Applying InputClass "evdev pointer catchall"
[ 35222.104] (II) Using input driver 'evdev' for 'DEXIN Tt eSPORTS BLACK Gaming mouse'
[ 35222.104] (**) DEXIN Tt eSPORTS BLACK Gaming mouse: always reports core events
[ 35222.104] (**) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Device: "/dev/input/event5"
[ 35222.104] (--) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Vendor 0x12cf Product 0x170
[ 35222.104] (--) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Found 9 mouse buttons
[ 35222.104] (--) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Found scroll wheel(s)
[ 35222.104] (--) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Found relative axes
[ 35222.104] (--) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Found x and y relative axes
[ 35222.104] (II) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Configuring as mouse
[ 35222.104] (II) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Adding scrollwheel support
[ 35222.104] (**) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: YAxisMapping: buttons 4 and 5
[ 35222.104] (**) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 35222.104] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input5/event5"
[ 35222.104] (II) XINPUT: Adding extended input device "DEXIN Tt eSPORTS BLACK Gaming mouse" (type: MOUSE, id 8)
[ 35222.105] (II) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: initialized for relative axes.
[ 35222.105] (**) DEXIN Tt eSPORTS BLACK Gaming mouse: (accel) keeping acceleration scheme 1
[ 35222.105] (**) DEXIN Tt eSPORTS BLACK Gaming mouse: (accel) acceleration profile 0
[ 35222.105] (**) DEXIN Tt eSPORTS BLACK Gaming mouse: (accel) acceleration factor: 2.000
[ 35222.105] (**) DEXIN Tt eSPORTS BLACK Gaming mouse: (accel) acceleration threshold: 4
[ 35222.106] (II) config/udev: Adding input device DEXIN Tt eSPORTS BLACK Gaming mouse (/dev/input/mouse1)
[ 35222.106] (II) No input driver specified, ignoring this device.
[ 35222.106] (II) This device may have been added with another device file.
[ 35222.107] (II) config/udev: Adding input device DEXIN Tt eSPORTS BLACK Gaming mouse (/dev/input/event6)
[ 35222.107] (**) DEXIN Tt eSPORTS BLACK Gaming mouse: Applying InputClass "evdev keyboard catchall"
[ 35222.107] (II) Using input driver 'evdev' for 'DEXIN Tt eSPORTS BLACK Gaming mouse'
[ 35222.107] (**) DEXIN Tt eSPORTS BLACK Gaming mouse: always reports core events
[ 35222.107] (**) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Device: "/dev/input/event6"
[ 35222.107] (--) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Vendor 0x12cf Product 0x170
[ 35222.107] (--) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Found 1 mouse buttons
[ 35222.107] (--) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Found scroll wheel(s)
[ 35222.107] (--) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Found relative axes
[ 35222.107] (II) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Forcing relative x/y axes to exist.
[ 35222.107] (--) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Found absolute axes
[ 35222.107] (II) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Forcing absolute x/y axes to exist.
[ 35222.107] (--) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Found keys
[ 35222.107] (II) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Configuring as mouse
[ 35222.107] (II) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Configuring as keyboard
[ 35222.107] (II) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Adding scrollwheel support
[ 35222.107] (**) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: YAxisMapping: buttons 4 and 5
[ 35222.107] (**) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 35222.107] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.1/input/input6/event6"
[ 35222.107] (II) XINPUT: Adding extended input device "DEXIN Tt eSPORTS BLACK Gaming mouse" (type: KEYBOARD, id 9)
[ 35222.108] (**) Option "xkb_rules" "evdev"
[ 35222.108] (**) Option "xkb_model" "pc105"
[ 35222.108] (**) Option "xkb_layout" "us"
[ 35222.108] (II) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: initialized for relative axes.
[ 35222.108] (WW) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: ignoring absolute axes.
[ 35222.108] (**) DEXIN Tt eSPORTS BLACK Gaming mouse: (accel) keeping acceleration scheme 1
[ 35222.108] (**) DEXIN Tt eSPORTS BLACK Gaming mouse: (accel) acceleration profile 0
[ 35222.108] (**) DEXIN Tt eSPORTS BLACK Gaming mouse: (accel) acceleration factor: 2.000
[ 35222.108] (**) DEXIN Tt eSPORTS BLACK Gaming mouse: (accel) acceleration threshold: 4
[ 35222.108] (II) config/udev: Adding input device Honey Bee  Nostromo SpeedPad2  (/dev/input/event2)
[ 35222.108] (**) Honey Bee  Nostromo SpeedPad2 : Applying InputClass "evdev keyboard catchall"
[ 35222.108] (II) Using input driver 'evdev' for 'Honey Bee  Nostromo SpeedPad2 '
[ 35222.108] (**) Honey Bee  Nostromo SpeedPad2 : always reports core events
[ 35222.108] (**) evdev: Honey Bee  Nostromo SpeedPad2 : Device: "/dev/input/event2"
[ 35222.108] (--) evdev: Honey Bee  Nostromo SpeedPad2 : Vendor 0x50d Product 0x815
[ 35222.108] (--) evdev: Honey Bee  Nostromo SpeedPad2 : Found keys
[ 35222.108] (II) evdev: Honey Bee  Nostromo SpeedPad2 : Configuring as keyboard
[ 35222.108] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input2/event2"
[ 35222.108] (II) XINPUT: Adding extended input device "Honey Bee  Nostromo SpeedPad2 " (type: KEYBOARD, id 10)
[ 35222.108] (**) Option "xkb_rules" "evdev"
[ 35222.108] (**) Option "xkb_model" "pc105"
[ 35222.108] (**) Option "xkb_layout" "us"
[ 35222.109] (II) config/udev: Adding input device Honey Bee  Nostromo SpeedPad2  (/dev/input/event3)
[ 35222.109] (**) Honey Bee  Nostromo SpeedPad2 : Applying InputClass "evdev pointer catchall"
[ 35222.109] (II) Using input driver 'evdev' for 'Honey Bee  Nostromo SpeedPad2 '
[ 35222.109] (**) Honey Bee  Nostromo SpeedPad2 : always reports core events
[ 35222.109] (**) evdev: Honey Bee  Nostromo SpeedPad2 : Device: "/dev/input/event3"
[ 35222.109] (--) evdev: Honey Bee  Nostromo SpeedPad2 : Vendor 0x50d Product 0x815
[ 35222.109] (--) evdev: Honey Bee  Nostromo SpeedPad2 : Found 3 mouse buttons
[ 35222.109] (--) evdev: Honey Bee  Nostromo SpeedPad2 : Found scroll wheel(s)
[ 35222.109] (--) evdev: Honey Bee  Nostromo SpeedPad2 : Found relative axes
[ 35222.109] (--) evdev: Honey Bee  Nostromo SpeedPad2 : Found x and y relative axes
[ 35222.109] (II) evdev: Honey Bee  Nostromo SpeedPad2 : Configuring as mouse
[ 35222.109] (II) evdev: Honey Bee  Nostromo SpeedPad2 : Adding scrollwheel support
[ 35222.109] (**) evdev: Honey Bee  Nostromo SpeedPad2 : YAxisMapping: buttons 4 and 5
[ 35222.109] (**) evdev: Honey Bee  Nostromo SpeedPad2 : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 35222.109] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/input/input3/event3"
[ 35222.109] (II) XINPUT: Adding extended input device "Honey Bee  Nostromo SpeedPad2 " (type: MOUSE, id 11)
[ 35222.109] (II) evdev: Honey Bee  Nostromo SpeedPad2 : initialized for relative axes.
[ 35222.109] (**) Honey Bee  Nostromo SpeedPad2 : (accel) keeping acceleration scheme 1
[ 35222.109] (**) Honey Bee  Nostromo SpeedPad2 : (accel) acceleration profile 0
[ 35222.109] (**) Honey Bee  Nostromo SpeedPad2 : (accel) acceleration factor: 2.000
[ 35222.109] (**) Honey Bee  Nostromo SpeedPad2 : (accel) acceleration threshold: 4
[ 35222.109] (II) config/udev: Adding input device Honey Bee  Nostromo SpeedPad2  (/dev/input/mouse0)
[ 35222.109] (II) No input driver specified, ignoring this device.
[ 35222.109] (II) This device may have been added with another device file.
[ 35222.109] (II) config/udev: Adding input device Ideazon Zboard (/dev/input/event4)
[ 35222.109] (**) Ideazon Zboard: Applying InputClass "evdev keyboard catchall"
[ 35222.109] (II) Using input driver 'evdev' for 'Ideazon Zboard'
[ 35222.109] (**) Ideazon Zboard: always reports core events
[ 35222.109] (**) evdev: Ideazon Zboard: Device: "/dev/input/event4"
[ 35222.109] (--) evdev: Ideazon Zboard: Vendor 0x1038 Product 0x100
[ 35222.109] (--) evdev: Ideazon Zboard: Found keys
[ 35222.109] (II) evdev: Ideazon Zboard: Configuring as keyboard
[ 35222.109] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1.4/5-1.4:1.0/input/input13/event4"
[ 35222.109] (II) XINPUT: Adding extended input device "Ideazon Zboard" (type: KEYBOARD, id 12)
[ 35222.109] (**) Option "xkb_rules" "evdev"
[ 35222.109] (**) Option "xkb_model" "pc105"
[ 35222.109] (**) Option "xkb_layout" "us"
[ 35222.110] (II) config/udev: Adding input device Ideazon Zboard (/dev/input/event7)
[ 35222.110] (**) Ideazon Zboard: Applying InputClass "evdev keyboard catchall"
[ 35222.110] (II) Using input driver 'evdev' for 'Ideazon Zboard'
[ 35222.110] (**) Ideazon Zboard: always reports core events
[ 35222.110] (**) evdev: Ideazon Zboard: Device: "/dev/input/event7"
[ 35222.110] (--) evdev: Ideazon Zboard: Vendor 0x1038 Product 0x100
[ 35222.110] (--) evdev: Ideazon Zboard: Found keys
[ 35222.110] (II) evdev: Ideazon Zboard: Configuring as keyboard
[ 35222.110] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1.4/5-1.4:1.1/input/input14/event7"
[ 35222.110] (II) XINPUT: Adding extended input device "Ideazon Zboard" (type: KEYBOARD, id 13)
[ 35222.110] (**) Option "xkb_rules" "evdev"
[ 35222.110] (**) Option "xkb_model" "pc105"
[ 35222.110] (**) Option "xkb_layout" "us"
[ 35222.259] (II) XKB: reuse xkmfile /var/lib/xkb/server-B59E50A6E741E924A50F942B78A8EF54156068A0.xkm
[ 35233.699] (II) XKB: reuse xkmfile /var/lib/xkb/server-B59E50A6E741E924A50F942B78A8EF54156068A0.xkm
[ 35235.506] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[ 35235.506] (II) NVIDIA(GPU-0):     3D Vision stereo.
[ 35235.506] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 35235.506] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[ 35235.506] (**) NVIDIA(0):     has been enabled on all display devices.)
[ 35235.889] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[ 35235.889] (II) NVIDIA(GPU-0):     3D Vision stereo.
[ 35235.890] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 35235.890] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[ 35235.890] (**) NVIDIA(0):     has been enabled on all display devices.)
[ 35236.778] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[ 35236.778] (II) NVIDIA(GPU-0):     3D Vision stereo.
[ 35236.778] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 35236.778] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[ 35236.778] (**) NVIDIA(0):     has been enabled on all display devices.)
[ 35236.891] (II) XKB: reuse xkmfile /var/lib/xkb/server-7902D269265BEF4D73C0BE29955712DF5EEC657E.xkm
[ 35237.832] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[ 35237.832] (II) NVIDIA(GPU-0):     3D Vision stereo.
[ 35237.832] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 35237.832] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[ 35237.832] (**) NVIDIA(0):     has been enabled on all display devices.)
[ 35238.073] (II) XKB: reuse xkmfile /var/lib/xkb/server-7902D269265BEF4D73C0BE29955712DF5EEC657E.xkm
[ 35241.017] (II) XKB: reuse xkmfile /var/lib/xkb/server-6E638BC77378D3365CF40C3F36455C3C313715E7.xkm
[ 35258.071] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[ 35258.071] (II) NVIDIA(GPU-0):     3D Vision stereo.
[ 35258.071] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 35258.071] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[ 35258.071] (**) NVIDIA(0):     has been enabled on all display devices.)
(EE) [mi] EQ overflowing.  Additional events will be discarded until existing events are processed.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x3d) [0x7ff00adcafdd]
(EE) 1: /usr/bin/X (mieqEnqueue+0x22b) [0x7ff00adacf1b]
(EE) 2: /usr/bin/X (QueuePointerEvents+0x52) [0x7ff00ac93a92]
(EE) 3: /usr/lib/xorg/modules/input/evdev_drv.so (0x7ff000e25000+0x566f) [0x7ff000e2a66f]
(EE) 4: /usr/bin/X (0x7ff00ac28000+0x91ee8) [0x7ff00acb9ee8]
(EE) 5: /usr/bin/X (0x7ff00ac28000+0xba930) [0x7ff00ace2930]
(EE) 6: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7ff009d28000+0xfbb0) [0x7ff009d37bb0]
(EE) 7: /lib/x86_64-linux-gnu/libc.so.6 (0x7ff008942000+0x7fbb6) [0x7ff0089c1bb6]
(EE) 8: /lib/x86_64-linux-gnu/libc.so.6 (0x7ff008942000+0x810e1) [0x7ff0089c30e1]
(EE) 9: /lib/x86_64-linux-gnu/libc.so.6 (__libc_calloc+0xbf) [0x7ff0089c606f]
(EE) 10: /usr/bin/X (0x7ff00ac28000+0x7cf6d) [0x7ff00aca4f6d]
(EE) 11: /usr/bin/X (CloseDownClient+0x57) [0x7ff00ac7c727]
(EE) 12: /usr/bin/X (0x7ff00ac28000+0x55194) [0x7ff00ac7d194]
(EE) 13: /usr/bin/X (0x7ff00ac28000+0x447ba) [0x7ff00ac6c7ba]
(EE) 14: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7ff008963de5]
(EE) 15: /usr/bin/X (0x7ff00ac28000+0x44aff) [0x7ff00ac6caff]
(EE) 
(EE) [mi] These backtraces from mieqEnqueue may point to a culprit higher up the stack.
(EE) [mi] mieq is *NOT* the cause.  It is a victim.
[ 35479.423] [mi] Increasing EQ size to 512 to prevent dropped events.
[ 35479.423] [mi] EQ processing has resumed after 15 dropped events.
[ 35479.423] [mi] This may be caused my a misbehaving driver monopolizing the server's resources.
[ 35479.697] (II) evdev: Ideazon Zboard: Close
[ 35479.697] (II) UnloadModule: "evdev"
[ 35479.697] (II) evdev: Ideazon Zboard: Close
[ 35479.697] (II) UnloadModule: "evdev"
[ 35479.697] (II) evdev: Honey Bee  Nostromo SpeedPad2 : Close
[ 35479.697] (II) UnloadModule: "evdev"
[ 35479.697] (II) evdev: Honey Bee  Nostromo SpeedPad2 : Close
[ 35479.697] (II) UnloadModule: "evdev"
[ 35479.697] (II) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Close
[ 35479.697] (II) UnloadModule: "evdev"
[ 35479.697] (II) evdev: DEXIN Tt eSPORTS BLACK Gaming mouse: Close
[ 35479.697] (II) UnloadModule: "evdev"
[ 35479.697] (II) evdev: Power Button: Close
[ 35479.697] (II) UnloadModule: "evdev"
[ 35479.697] (II) evdev: Power Button: Close
[ 35479.697] (II) UnloadModule: "evdev"
[ 35480.131] (EE) Server terminated successfully (0). Closing log file.
```

---

### Post by grumblebum2 on 2014-04-07
Tried...
[LIST]
[*]Purging nvidia and using nouveau
[*]Reinstalling nvidia
[*]Reinstalling lightdm
[*]Creating an /etc/X11/xorg.conf
[*]Using an xorg.conf created in my Trusty install
[/LIST]

Everthying just takes me to low graphics mode and left with black screen and flashing cursor.
Ideas???

---

### Post by grumblebum2 on 2014-04-08
**Ahem**

---

### Post by lecoeur-jeremy on 2014-04-28
I have the exact same problem. My Ubuntu has been working fine for  months and all of a sudden, it started to stall and flicker at boot. I  can go to the login screen but that's it. I looked at my Xorg.0.log but  that did not help.

```
[    24.657] (--) NVIDIA(0):     option
[    24.657] (--) Depth 24 pixmap format is 32 bpp
[    24.657] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    24.666] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select,DFP-1:nvidia-auto-select"
[    24.808] Loading extension NV-GLX
[    24.957] (==) NVIDIA(0): Disabling shared memory pixmaps
[    24.957] (==) NVIDIA(0): Backing store disabled
[    24.957] (==) NVIDIA(0): Silken mouse enabled
[    24.957] (**) NVIDIA(0): DPMS enabled
[    24.957] Loading extension NV-CONTROL
[    24.958] Loading extension XINERAMA
[    24.958] (II) Loading sub module "dri2"
[    24.958] (II) LoadModule: "dri2"
[    24.958] (II) Module "dri2" already built-in
[    24.958] (II) NVIDIA(0): [DRI2] Setup complete
[    24.958] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    24.958] (--) RandR disabled
[    24.961] (II) Initializing extension GLX
[    25.142] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.143] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    25.144] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.144] (II) LoadModule: "evdev"
[    25.144] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.144] (II) Module evdev: vendor="X.Org Foundation"
[    25.144]    compiled for 1.13.0, module version = 2.7.3
[    25.144]    Module class: X.Org XInput Driver
[    25.144]    ABI class: X.Org XInput driver, version 18.0
[    25.144] (II) Using input driver 'evdev' for 'Power Button'
[    25.144] (**) Power Button: always reports core events
[    25.144] (**) evdev: Power Button: Device: "/dev/input/event1"
[    25.144] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.144] (--) evdev: Power Button: Found keys
[    25.144] (II) evdev: Power Button: Configuring as keyboard
[    25.144] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    25.144] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    25.144] (**) Option "xkb_rules" "evdev"
[    25.144] (**) Option "xkb_model" "pc105"
[    25.144] (**) Option "xkb_layout" "us"
[    25.144] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    25.144] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.144] (II) Using input driver 'evdev' for 'Power Button'
[    25.144] (**) Power Button: always reports core events
[    25.144] (**) evdev: Power Button: Device: "/dev/input/event0"
[    25.144] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.144] (--) evdev: Power Button: Found keys
[    25.144] (II) evdev: Power Button: Configuring as keyboard
[    25.144] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    25.144] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    25.144] (**) Option "xkb_rules" "evdev"
[    25.144] (**) Option "xkb_model" "pc105"
[    25.144] (**) Option "xkb_layout" "us"
[    25.145] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event10)
[    25.145] (II) No input driver specified, ignoring this device.
[    25.145] (II) This device may have been added with another device file.
[    25.145] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event11)
[    25.145] (II) No input driver specified, ignoring this device.
[    25.145] (II) This device may have been added with another device file.
[    25.145] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event12)
[    25.145] (II) No input driver specified, ignoring this device.
[    25.145] (II) This device may have been added with another device file.
[    25.145] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event9)
[    25.145] (II) No input driver specified, ignoring this device.
[    25.145] (II) This device may have been added with another device file.
[    25.145] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event4)
[    25.145] (II) No input driver specified, ignoring this device.
[    25.145] (II) This device may have been added with another device file.
[    25.145] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event5)
[    25.145] (II) No input driver specified, ignoring this device.
[    25.145] (II) This device may have been added with another device file.
[    25.146] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event6)
[    25.146] (II) No input driver specified, ignoring this device.
[    25.146] (II) This device may have been added with another device file.
[    25.146] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event7)
[    25.146] (II) No input driver specified, ignoring this device.
[    25.146] (II) This device may have been added with another device file.
[    25.146] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event2)
[    25.146] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    25.146] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    25.146] (**) Logitech USB Optical Mouse: always reports core events
[    25.146] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event2"
[    25.146] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05a
[    25.146] (--) evdev: Logitech USB Optical Mouse: Found 12 mouse buttons
[    25.146] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[    25.146] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[    25.146] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[    25.146] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[    25.146] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[    25.146] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    25.146] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    25.146] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input2/event2"
[    25.146] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 8)
[    25.146] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[    25.146] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    25.146] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    25.146] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    25.146] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    25.146] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[    25.146] (II) No input driver specified, ignoring this device.
[    25.146] (II) This device may have been added with another device file.
[    25.147] (II) config/udev: Adding input device DELL Dell QuietKey Keyboard (/dev/input/event3)
[    25.147] (**) DELL Dell QuietKey Keyboard: Applying InputClass "evdev keyboard catchall"
[    25.147] (II) Using input driver 'evdev' for 'DELL Dell QuietKey Keyboard'
[    25.147] (**) DELL Dell QuietKey Keyboard: always reports core events
[    25.147] (**) evdev: DELL Dell QuietKey Keyboard: Device: "/dev/input/event3"
[    25.147] (--) evdev: DELL Dell QuietKey Keyboard: Vendor 0x413c Product 0x2106
[    25.147] (--) evdev: DELL Dell QuietKey Keyboard: Found keys
[    25.147] (II) evdev: DELL Dell QuietKey Keyboard: Configuring as keyboard
[    25.147] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input3/event3"
[    25.147] (II) XINPUT: Adding extended input device "DELL Dell QuietKey Keyboard" (type: KEYBOARD, id 9)
[    25.147] (**) Option "xkb_rules" "evdev"
[    25.147] (**) Option "xkb_model" "pc105"
[    25.147] (**) Option "xkb_layout" "us"
[    25.147] (II) config/udev: Adding input device gspca_sn9c20x (/dev/input/event13)
[    25.147] (**) gspca_sn9c20x: Applying InputClass "evdev keyboard catchall"
[    25.147] (II) Using input driver 'evdev' for 'gspca_sn9c20x'
[    25.147] (**) gspca_sn9c20x: always reports core events
[    25.147] (**) evdev: gspca_sn9c20x: Device: "/dev/input/event13"
[    25.147] (--) evdev: gspca_sn9c20x: Vendor 0x45e Product 0xf4
[    25.147] (--) evdev: gspca_sn9c20x: Found keys
[    25.147] (II) evdev: gspca_sn9c20x: Configuring as keyboard
[    25.147] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/input/input13/event13"
[    25.147] (II) XINPUT: Adding extended input device "gspca_sn9c20x" (type: KEYBOARD, id 10)
[    25.147] (**) Option "xkb_rules" "evdev"
[    25.147] (**) Option "xkb_model" "pc105"
[    25.147] (**) Option "xkb_layout" "us"
[    25.148] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event8)
[    25.148] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    25.148] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    25.148] (**) Dell WMI hotkeys: always reports core events
[    25.148] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event8"
[    25.148] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    25.148] (--) evdev: Dell WMI hotkeys: Found keys
[    25.148] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    25.148] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event8"
[    25.148] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 11)
[    25.148] (**) Option "xkb_rules" "evdev"
[    25.148] (**) Option "xkb_model" "pc105"
[    25.148] (**) Option "xkb_layout" "us"
[    25.836] (II) NVIDIA(GPU-0): Display (DELL 1900FP (DFP-0)) does not support NVIDIA 3D
[    25.836] (II) NVIDIA(GPU-0):     Vision stereo.
[    25.836] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    25.836] (**) NVIDIA(0):     device DELL 1900FP (DFP-0) (Using EDID frequencies has
[    25.836] (**) NVIDIA(0):     been enabled on all display devices.)
[    25.853] (II) NVIDIA(GPU-0): Display (DELL 1900FP (DFP-1)) does not support NVIDIA 3D
[    25.853] (II) NVIDIA(GPU-0):     Vision stereo.
[    25.853] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    25.853] (**) NVIDIA(0):     device DELL 1900FP (DFP-1) (Using EDID frequencies has
[    25.853] (**) NVIDIA(0):     been enabled on all display devices.)
[    26.749] (II) NVIDIA(GPU-0): Display (DELL 1900FP (DFP-0)) does not support NVIDIA 3D
[    26.749] (II) NVIDIA(GPU-0):     Vision stereo.
[    26.749] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    26.749] (**) NVIDIA(0):     device DELL 1900FP (DFP-0) (Using EDID frequencies has
[    26.749] (**) NVIDIA(0):     been enabled on all display devices.)
[    26.765] (II) NVIDIA(GPU-0): Display (DELL 1900FP (DFP-1)) does not support NVIDIA 3D
[    26.765] (II) NVIDIA(GPU-0):     Vision stereo.
[    26.765] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    26.765] (**) NVIDIA(0):     device DELL 1900FP (DFP-1) (Using EDID frequencies has
[    26.765] (**) NVIDIA(0):     been enabled on all display devices.)
[    71.168] (II) NVIDIA(GPU-0): Display (DELL 1900FP (DFP-0)) does not support NVIDIA 3D
[    71.168] (II) NVIDIA(GPU-0):     Vision stereo.
[    71.168] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    71.168] (**) NVIDIA(0):     device DELL 1900FP (DFP-0) (Using EDID frequencies has
[    71.168] (**) NVIDIA(0):     been enabled on all display devices.)
[    71.184] (II) NVIDIA(GPU-0): Display (DELL 1900FP (DFP-1)) does not support NVIDIA 3D
[    71.184] (II) NVIDIA(GPU-0):     Vision stereo.
[    71.184] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    71.184] (**) NVIDIA(0):     device DELL 1900FP (DFP-1) (Using EDID frequencies has
[    71.184] (**) NVIDIA(0):     been enabled on all display devices.)
[    71.293] (II) NVIDIA(GPU-0): Display (DELL 1900FP (DFP-0)) does not support NVIDIA 3D
[    71.293] (II) NVIDIA(GPU-0):     Vision stereo.
[    71.293] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    71.293] (**) NVIDIA(0):     device DELL 1900FP (DFP-0) (Using EDID frequencies has
[    71.293] (**) NVIDIA(0):     been enabled on all display devices.)
[    71.309] (II) NVIDIA(GPU-0): Display (DELL 1900FP (DFP-1)) does not support NVIDIA 3D
[    71.309] (II) NVIDIA(GPU-0):     Vision stereo.
[    71.309] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    71.309] (**) NVIDIA(0):     device DELL 1900FP (DFP-1) (Using EDID frequencies has
[    71.309] (**) NVIDIA(0):     been enabled on all display devices.)
[    71.407] (II) NVIDIA(GPU-0): Display (DELL 1900FP (DFP-0)) does not support NVIDIA 3D
[    71.407] (II) NVIDIA(GPU-0):     Vision stereo.
[    71.407] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    71.407] (**) NVIDIA(0):     device DELL 1900FP (DFP-0) (Using EDID frequencies has
[    71.407] (**) NVIDIA(0):     been enabled on all display devices.)
[    71.423] (II) NVIDIA(GPU-0): Display (DELL 1900FP (DFP-1)) does not support NVIDIA 3D
[    71.423] (II) NVIDIA(GPU-0):     Vision stereo.
[    71.423] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    71.423] (**) NVIDIA(0):     device DELL 1900FP (DFP-1) (Using EDID frequencies has
[    71.423] (**) NVIDIA(0):     been enabled on all display devices.)
[    93.280] (II) NVIDIA(GPU-0): Display (DELL 1900FP (DFP-0)) does not support NVIDIA 3D
[    93.280] (II) NVIDIA(GPU-0):     Vision stereo.
[    93.280] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    93.280] (**) NVIDIA(0):     device DELL 1900FP (DFP-0) (Using EDID frequencies has
[    93.280] (**) NVIDIA(0):     been enabled on all display devices.)
[    93.297] (II) NVIDIA(GPU-0): Display (DELL 1900FP (DFP-1)) does not support NVIDIA 3D
[    93.297] (II) NVIDIA(GPU-0):     Vision stereo.
[    93.297] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    93.298] (**) NVIDIA(0):     device DELL 1900FP (DFP-1) (Using EDID frequencies has
[    93.298] (**) NVIDIA(0):     been enabled on all display devices.)
(EE) [mi] EQ overflowing.  Additional events will be discarded until existing events are processed.
(EE)
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7ff8bd941bc6]
(EE) 1: /usr/bin/X (mieqEnqueue+0x26b) [0x7ff8bd922fab]
(EE) 2: /usr/bin/X (0x7ff8bd799000+0x6a4e2) [0x7ff8bd8034e2]
(EE) 3: /usr/lib/xorg/modules/input/evdev_drv.so (0x7ff8b6273000+0x5f34) [0x7ff8b6278f34]
(EE) 4: /usr/bin/X (0x7ff8bd799000+0x93707) [0x7ff8bd82c707]
(EE) 5: /usr/bin/X (0x7ff8bd799000+0xbcee8) [0x7ff8bd855ee8]
(EE) 6: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7ff8bcabf000+0xfcb0) [0x7ff8bcacecb0]
(EE) 7: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x97450) [0x7ff8b6e57450]
(EE) 8: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x98cd5) [0x7ff8b6e58cd5]
(EE) 9: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x11476a) [0x7ff8b6ed476a]
(EE) 10: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x114a4d) [0x7ff8b6ed4a4d]
(EE) 11: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0xfc2b1) [0x7ff8b6ebc2b1]
(EE) 12: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0xee891) [0x7ff8b6eae891]
(EE) 13: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0xe6f74) [0x7ff8b6ea6f74]
(EE) 14: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0xe76b0) [0x7ff8b6ea76b0]
(EE) 15: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x98ca3) [0x7ff8b6e58ca3]
(EE) 16: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x111e2e) [0x7ff8b6ed1e2e]
(EE) 17: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x5a6d90) [0x7ff8b7366d90]
(EE) 18: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x5a5815) [0x7ff8b7365815]
(EE) 19: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x5a6fcd) [0x7ff8b7366fcd]
(EE) 20: /usr/bin/X (0x7ff8bd799000+0x135912) [0x7ff8bd8ce912]
(EE) 21: /usr/bin/X (0x7ff8bd799000+0x52643) [0x7ff8bd7eb643]
(EE) 22: /usr/bin/X (0x7ff8bd799000+0x55a91) [0x7ff8bd7eea91]
(EE) 23: /usr/bin/X (0x7ff8bd799000+0x4456a) [0x7ff8bd7dd56a]
(EE) 24: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7ff8bb71f76d]
(EE) 25: /usr/bin/X (0x7ff8bd799000+0x448ad) [0x7ff8bd7dd8ad]
(EE)
(EE) [mi] These backtraces from mieqEnqueue may point to a culprit higher up the stack.
(EE) [mi] mieq is *NOT* the cause.  It is a victim.
(EE) [mi] EQ overflow continuing.  100 events have been dropped.
(EE)
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7ff8bd941bc6]
(EE) 1: /usr/bin/X (0x7ff8bd799000+0x6a4e2) [0x7ff8bd8034e2]
(EE) 2: /usr/lib/xorg/modules/input/evdev_drv.so (0x7ff8b6273000+0x5f34) [0x7ff8b6278f34]
(EE) 3: /usr/bin/X (0x7ff8bd799000+0x93707) [0x7ff8bd82c707]
(EE) 4: /usr/bin/X (0x7ff8bd799000+0xbcee8) [0x7ff8bd855ee8]
(EE) 5: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7ff8bcabf000+0xfcb0) [0x7ff8bcacecb0]
(EE) 6: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x97450) [0x7ff8b6e57450]
(EE) 7: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x98cd5) [0x7ff8b6e58cd5]
(EE) 8: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x11476a) [0x7ff8b6ed476a]
(EE) 9: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x114a4d) [0x7ff8b6ed4a4d]
(EE) 10: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0xfc2b1) [0x7ff8b6ebc2b1]
(EE) 11: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0xee891) [0x7ff8b6eae891]
(EE) 12: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0xe6f74) [0x7ff8b6ea6f74]
(EE) 13: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0xe76b0) [0x7ff8b6ea76b0]
(EE) 14: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x98ca3) [0x7ff8b6e58ca3]
(EE) 15: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x111e2e) [0x7ff8b6ed1e2e]
(EE) 16: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x5a6d90) [0x7ff8b7366d90]
(EE) 17: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x5a5815) [0x7ff8b7365815]
(EE) 18: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7ff8b6dc0000+0x5a6fcd) [0x7ff8b7366fcd]
(EE) 19: /usr/bin/X (0x7ff8bd799000+0x135912) [0x7ff8bd8ce912]
(EE) 20: /usr/bin/X (0x7ff8bd799000+0x52643) [0x7ff8bd7eb643]
(EE) 21: /usr/bin/X (0x7ff8bd799000+0x55a91) [0x7ff8bd7eea91]
(EE) 22: /usr/bin/X (0x7ff8bd799000+0x4456a) [0x7ff8bd7dd56a]
(EE) 23: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7ff8bb71f76d]
(EE) 24: /usr/bin/X (0x7ff8bd799000+0x448ad) [0x7ff8bd7dd8ad]
(EE)


```

---

### Post by grumblebum2 on 2014-04-28
I put it in the too hard basket and switched over to trusty on another partition....Saucy still won't boot.

---

