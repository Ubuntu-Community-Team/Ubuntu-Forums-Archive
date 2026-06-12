---
title: "Login doesn't create a session"
date: 2014-03-24
forum: General Help
---

### Post by guru102 on 2014-03-24
Hi everyone,

recently I installed a lot of new programs, and then polkit stopped working - whenever application usually asks for authentication, it doesn't do anything for me, nor can I shutdown my computer other than from console with sudo.
So I researched into it a little, and what I found is, that I don't have a session - loginctl list-sessions prints only column names.

I don't know exactly what logs I should look into, but to me x-0-greeter.log seems interesting:
> 
** (process:1289): WARNING **: Failed to open login1 session: GDBus.Error:org.freedesktop.DBus.Error.FileNotFound: No such file or directory
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /var/lib/lightdm/.config/ibus/bus

** (process:1482): WARNING **: Failed to open sessions directory: Error opening directory '/usr/share/lightdm/remote-sessions': No such file or directory



I even googled a little bit about these warnings, but nothing useful came out of it, so I don't know what to do next.

Rather I will also post some other logs.
lightdm.log:

> [+0.03s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.03s] DEBUG: Starting Light Display Manager 1.8.5, UID=0 PID=1051
[+0.03s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.03s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.03s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.03s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.03s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.03s] DEBUG: Registered seat module xlocal
[+0.03s] DEBUG: Registered seat module xremote
[+0.03s] DEBUG: Registered seat module unity
[+0.03s] DEBUG: Registered seat module surfaceflinger
[+0.03s] DEBUG: Adding default seat
[+0.03s] DEBUG: Seat: Starting
[+0.03s] DEBUG: Seat: Creating greeter session
[+0.03s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+0.03s] DEBUG: Seat: Creating display server of type x
[+0.03s] DEBUG: Seat: Starting local X display
[+0.03s] DEBUG: Deactivating Plymouth
[+0.05s] DEBUG: Using VT 7
[+0.05s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.05s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.05s] DEBUG: DisplayServer x-0: Launching X Server
[+0.05s] DEBUG: Launching process 1230: /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.05s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.06s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.06s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+2.33s] DEBUG: Got signal 10 from process 1230
[+2.33s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+2.33s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+2.33s] DEBUG: Quitting Plymouth; retaining splash
[+2.35s] DEBUG: Seat: Display server ready, starting session authentication
[+2.35s] DEBUG: Session: Setting XDG_VTNR=7
[+2.35s] DEBUG: Session pid=1289: Started with service 'lightdm-greeter', username 'lightdm'
[+4.08s] DEBUG: Session pid=1289: Authentication complete with return value 0: Success
[+4.08s] DEBUG: Seat: Session authenticated, running command
[+4.08s] DEBUG: Session pid=1289: Setting XDG_VTNR=7
[+4.08s] DEBUG: Session pid=1289: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-kde-greeter
[+4.08s] DEBUG: Session pid=1289: Logging to /var/log/lightdm/x-0-greeter.log
[+4.84s] DEBUG: Activating VT 7
[+15.96s] DEBUG: Session pid=1289: Greeter connected version=1.8.5
[+1189.63s] DEBUG: Session pid=1289: Greeter start authentication for juraj
[+1189.63s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+1189.63s] DEBUG: Session: Setting XDG_VTNR=7
[+1189.63s] DEBUG: Session pid=2538: Started with service 'lightdm', username 'juraj'
[+1189.64s] DEBUG: Session pid=2538: Got 1 message(s) from PAM
[+1189.64s] DEBUG: Session pid=1289: Prompt greeter with 1 message(s)
[+1189.65s] DEBUG: Session pid=1289: Continue authentication
[+1189.67s] DEBUG: Session pid=2538: Authentication complete with return value 0: Success
[+1189.67s] DEBUG: Session pid=1289: Authenticate result for user juraj: Success
[+1189.68s] DEBUG: Session pid=1289: User juraj authorized
[+1191.89s] DEBUG: Session pid=1289: Greeter requests session kde-plasma
[+1191.91s] DEBUG: Writing /home/juraj/.dmrc
[+1192.15s] DEBUG: Seat: Stopping greeter; display server will be re-used for user session
[+1192.15s] DEBUG: Session pid=1289: Sending SIGTERM
[+1192.16s] DEBUG: Session pid=1289: Greeter closed communication channel
[+1192.16s] DEBUG: Session pid=1289: Exited with return value 0
[+1192.16s] DEBUG: Seat: Session stopped
[+1192.16s] DEBUG: Seat: Greeter stopped, running session
[+1192.16s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+1192.16s] DEBUG: Session pid=2538: Setting XDG_VTNR=7
[+1192.16s] DEBUG: Session pid=2538: Running command /usr/sbin/lightdm-session /usr/bin/startkde
[+1192.16s] DEBUG: Session pid=2538: Logging to .xsession-errors
[+1192.19s] DEBUG: Activating VT 7



x-0.log

> 
X.Org X Server 1.14.5
Release Date: 2013-12-12
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
Current Operating System: Linux matus 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-18-generic root=UUID=bb422444-1dd2-4ac9-959b-3771a0170182 ro quiet splash vt.handoff=7
Build Date: 17 December 2013  10:06:15AM
xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.30.2
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 24 20:49:34 2014
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
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
(II) AIGLX: Suspending AIGLX clients for VT switch



Xorg-0.log

> [    45.275] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[    45.275] X Protocol Version 11, Revision 0
[    45.275] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    45.275] Current Operating System: Linux matus 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64
[    45.275] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-18-generic root=UUID=bb422444-1dd2-4ac9-959b-3771a0170182 ro quiet splash vt.handoff=7
[    45.275] Build Date: 17 December 2013  10:06:15AM
[    45.275] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    45.275] Current version of pixman: 0.30.2
[    45.275]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    45.275] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    45.275] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 24 20:49:34 2014
[    45.371] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    45.371] (==) No Layout section.  Using the first Screen section.
[    45.371] (==) No screen section available. Using defaults.
[    45.371] (**) |-->Screen "Default Screen Section" (0)
[    45.371] (**) |   |-->Monitor "<default monitor>"
[    45.371] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    45.371] (==) Automatically adding devices
[    45.371] (==) Automatically enabling devices
[    45.371] (==) Automatically adding GPU devices
[    45.372] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    45.372]     Entry deleted from font path.
[    45.372] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    45.372]     Entry deleted from font path.
[    45.372] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    45.372]     Entry deleted from font path.
[    45.372] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    45.372]     Entry deleted from font path.
[    45.372] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    45.372]     Entry deleted from font path.
[    45.372] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    45.372] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    45.372] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    45.372] (II) Loader magic: 0x7fcc1d0afd20
[    45.372] (II) Module ABI versions:
[    45.372]     X.Org ANSI C Emulation: 0.4
[    45.372]     X.Org Video Driver: 14.1
[    45.372]     X.Org XInput driver : 19.1
[    45.372]     X.Org Server Extension : 7.0
[    45.372] (II) xfree86: Adding drm device (/dev/dri/card0)
[    45.372] (--) PCI:*(0:0:2:0) 8086:0412:1043:8534 rev 6, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[    45.372] (II) Open ACPI successful (/var/run/acpid.socket)
[    45.372] Initializing built-in extension Generic Event Extension
[    45.372] Initializing built-in extension SHAPE
[    45.372] Initializing built-in extension MIT-SHM
[    45.372] Initializing built-in extension XInputExtension
[    45.372] Initializing built-in extension XTEST
[    45.372] Initializing built-in extension BIG-REQUESTS
[    45.372] Initializing built-in extension SYNC
[    45.372] Initializing built-in extension XKEYBOARD
[    45.372] Initializing built-in extension XC-MISC
[    45.372] Initializing built-in extension SECURITY
[    45.372] Initializing built-in extension XINERAMA
[    45.372] Initializing built-in extension XFIXES
[    45.372] Initializing built-in extension RENDER
[    45.372] Initializing built-in extension RANDR
[    45.372] Initializing built-in extension COMPOSITE
[    45.372] Initializing built-in extension DAMAGE
[    45.372] Initializing built-in extension MIT-SCREEN-SAVER
[    45.372] Initializing built-in extension DOUBLE-BUFFER
[    45.372] Initializing built-in extension RECORD
[    45.372] Initializing built-in extension DPMS
[    45.372] Initializing built-in extension X-Resource
[    45.372] Initializing built-in extension XVideo
[    45.372] Initializing built-in extension XVideo-MotionCompensation
[    45.372] Initializing built-in extension SELinux
[    45.372] Initializing built-in extension XFree86-VidModeExtension
[    45.372] Initializing built-in extension XFree86-DGA
[    45.372] Initializing built-in extension XFree86-DRI
[    45.372] Initializing built-in extension DRI2
[    45.372] (II) "glx" will be loaded by default.
[    45.372] (WW) "xmir" is not to be loaded by default. Skipping.
[    45.372] (II) LoadModule: "dri2"
[    45.373] (II) Module "dri2" already built-in
[    45.373] (II) LoadModule: "glamoregl"
[    45.462] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    46.242] (II) Module glamoregl: vendor="X.Org Foundation"
[    46.242]     compiled for 1.14.3, module version = 0.5.1
[    46.242]     ABI class: X.Org ANSI C Emulation, version 0.4
[    46.242] (II) LoadModule: "glx"
[    46.242] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    46.242] (II) Module glx: vendor="X.Org Foundation"
[    46.242]     compiled for 1.14.5, module version = 1.0.0
[    46.242]     ABI class: X.Org Server Extension, version 7.0
[    46.242] (==) AIGLX enabled
[    46.242] Loading extension GLX
[    46.242] (==) Matched intel as autoconfigured driver 0
[    46.242] (==) Matched intel as autoconfigured driver 1
[    46.242] (==) Matched vesa as autoconfigured driver 2
[    46.242] (==) Matched modesetting as autoconfigured driver 3
[    46.242] (==) Matched fbdev as autoconfigured driver 4
[    46.242] (==) Assigned the driver to the xf86ConfigLayout
[    46.242] (II) LoadModule: "intel"
[    46.242] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    46.278] (II) Module intel: vendor="X.Org Foundation"
[    46.278]     compiled for 1.14.5, module version = 2.99.904
[    46.278]     Module class: X.Org Video Driver
[    46.278]     ABI class: X.Org Video Driver, version 14.1
[    46.278] (II) LoadModule: "vesa"
[    46.278] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    46.278] (II) Module vesa: vendor="X.Org Foundation"
[    46.278]     compiled for 1.14.1, module version = 2.3.2
[    46.278]     Module class: X.Org Video Driver
[    46.278]     ABI class: X.Org Video Driver, version 14.1
[    46.278] (II) LoadModule: "modesetting"
[    46.278] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    46.278] (II) Module modesetting: vendor="X.Org Foundation"
[    46.278]     compiled for 1.14.1, module version = 0.8.0
[    46.278]     Module class: X.Org Video Driver
[    46.278]     ABI class: X.Org Video Driver, version 14.1
[    46.278] (II) LoadModule: "fbdev"
[    46.278] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    46.278] (II) Module fbdev: vendor="X.Org Foundation"
[    46.278]     compiled for 1.14.1, module version = 0.4.3
[    46.278]     Module class: X.Org Video Driver
[    46.278]     ABI class: X.Org Video Driver, version 14.1
[    46.278] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43, HD Graphics,
    HD Graphics 2000, HD Graphics 3000, HD Graphics 2500,
    HD Graphics 4000, HD Graphics P4000, HD Graphics 4600,
    HD Graphics 5000, HD Graphics P4600/P4700, Iris(TM) Graphics 5100,
    HD Graphics 4400, HD Graphics 4200, Iris(TM) Pro Graphics 5200
[    46.279] (II) VESA: driver for VESA chipsets: vesa
[    46.279] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    46.279] (II) FBDEV: driver for framebuffer: fbdev
[    46.279] (++) using VT number 7

[    46.279] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.904-0ubuntu2.1 (Robert Hooker <sarvatt@ubuntu.com>)
[    46.279] (WW) Falling back to old probe method for vesa
[    46.279] (WW) Falling back to old probe method for modesetting
[    46.279] (WW) Falling back to old probe method for fbdev
[    46.279] (II) Loading sub module "fbdevhw"
[    46.279] (II) LoadModule: "fbdevhw"
[    46.279] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    46.279] (II) Module fbdevhw: vendor="X.Org Foundation"
[    46.279]     compiled for 1.14.5, module version = 0.0.2
[    46.279]     ABI class: X.Org Video Driver, version 14.1
[    46.279] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    46.279] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    46.279] (==) intel(0): RGB weight 888
[    46.279] (==) intel(0): Default visual is TrueColor
[    46.279] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    46.279] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[    46.279] (**) intel(0): Framebuffer tiled
[    46.279] (**) intel(0): Pixmaps tiled
[    46.279] (**) intel(0): "Tear free" disabled
[    46.279] (**) intel(0): Forcing per-crtc-pixmaps? no
[    46.279] (II) intel(0): Output VGA1 has no monitor section
[    46.279] (II) intel(0): Output DP1 has no monitor section
[    46.279] (II) intel(0): Output HDMI1 has no monitor section
[    46.279] (II) intel(0): Output DP2 has no monitor section
[    46.279] (II) intel(0): Output HDMI2 has no monitor section
[    46.279] (II) intel(0): Output DP3 has no monitor section
[    46.279] (II) intel(0): Output HDMI3 has no monitor section
[    46.279] (II) intel(0): Output VIRTUAL1 has no monitor section
[    46.279] (--) intel(0): Output VGA1 using initial mode 1680x1050 on pipe 0
[    46.279] (==) intel(0): DPI set to (96, 96)
[    46.279] (II) Loading sub module "dri2"
[    46.279] (II) LoadModule: "dri2"
[    46.279] (II) Module "dri2" already built-in
[    46.279] (II) UnloadModule: "vesa"
[    46.279] (II) Unloading vesa
[    46.279] (II) UnloadModule: "modesetting"
[    46.279] (II) Unloading modesetting
[    46.279] (II) UnloadModule: "fbdev"
[    46.279] (II) Unloading fbdev
[    46.279] (II) UnloadSubModule: "fbdevhw"
[    46.279] (II) Unloading fbdevhw
[    46.280] (==) Depth 24 pixmap format is 32 bpp
[    46.280] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[    46.280] (==) intel(0): Backing store disabled
[    46.280] (==) intel(0): Silken mouse enabled
[    46.280] (II) intel(0): HW Cursor enabled
[    46.280] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    46.280] (==) intel(0): DPMS enabled
[    46.280] (II) intel(0): [DRI2] Setup complete
[    46.280] (II) intel(0): [DRI2]   DRI driver: i965
[    46.280] (II) intel(0): direct rendering: DRI2 Enabled
[    46.280] (==) intel(0): hotplug detection: "enabled"
[    46.280] (--) RandR disabled
[    46.282] (II) SELinux: Disabled on system
[    46.686] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    46.686] (II) AIGLX: enabled GLX_INTEL_swap_event
[    46.686] (II) AIGLX: enabled GLX_ARB_create_context
[    46.686] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    46.686] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    46.686] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    46.686] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    46.686] (II) AIGLX: Loaded and initialized i965
[    46.686] (II) GLX: Initialized DRI2 GL provider for screen 0
[    46.687] (II) intel(0): switch to mode 1680x1050@59.9 on pipe 0 using VGA1, position (0, 0), rotation normal
[    46.704] (II) intel(0): Setting screen physical size to 444 x 277
[    46.708] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    46.796] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    46.796] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    46.796] (II) LoadModule: "evdev"
[    46.796] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    46.818] (II) Module evdev: vendor="X.Org Foundation"
[    46.818]     compiled for 1.14.1, module version = 2.7.3
[    46.818]     Module class: X.Org XInput Driver
[    46.818]     ABI class: X.Org XInput driver, version 19.1
[    46.818] (II) Using input driver 'evdev' for 'Power Button'
[    46.818] (**) Power Button: always reports core events
[    46.818] (**) evdev: Power Button: Device: "/dev/input/event1"
[    46.818] (--) evdev: Power Button: Vendor 0 Product 0x1
[    46.818] (--) evdev: Power Button: Found keys
[    46.818] (II) evdev: Power Button: Configuring as keyboard
[    46.818] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    46.818] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    46.818] (**) Option "xkb_rules" "evdev"
[    46.818] (**) Option "xkb_model" "pc105"
[    46.818] (**) Option "xkb_layout" "sk"
[    46.820] (II) XKB: reuse xkmfile /var/lib/xkb/server-93538C06A4A7286C4A48C2D2A28CF10F0898BE0D.xkm
[    46.820] (II) config/udev: Adding input device Video Bus (/dev/input/event2)
[    46.820] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    46.820] (II) Using input driver 'evdev' for 'Video Bus'
[    46.820] (**) Video Bus: always reports core events
[    46.820] (**) evdev: Video Bus: Device: "/dev/input/event2"
[    46.820] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    46.820] (--) evdev: Video Bus: Found keys
[    46.820] (II) evdev: Video Bus: Configuring as keyboard
[    46.820] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input2/event2"
[    46.820] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    46.820] (**) Option "xkb_rules" "evdev"
[    46.820] (**) Option "xkb_model" "pc105"
[    46.820] (**) Option "xkb_layout" "sk"
[    46.820] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    46.820] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    46.820] (II) Using input driver 'evdev' for 'Power Button'
[    46.820] (**) Power Button: always reports core events
[    46.820] (**) evdev: Power Button: Device: "/dev/input/event0"
[    46.820] (--) evdev: Power Button: Vendor 0 Product 0x1
[    46.820] (--) evdev: Power Button: Found keys
[    46.820] (II) evdev: Power Button: Configuring as keyboard
[    46.820] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    46.820] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    46.820] (**) Option "xkb_rules" "evdev"
[    46.820] (**) Option "xkb_model" "pc105"
[    46.820] (**) Option "xkb_layout" "sk"
[    46.820] (II) config/udev: Adding drm device (/dev/dri/card0)
[    46.820] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    46.820] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=7 (/dev/input/event3)
[    46.820] (II) No input driver specified, ignoring this device.
[    46.820] (II) This device may have been added with another device file.
[    46.820] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=3 (/dev/input/event4)
[    46.820] (II) No input driver specified, ignoring this device.
[    46.821] (II) This device may have been added with another device file.
[    46.821] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event14)
[    46.821] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    46.821] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    46.821] (**) Logitech USB Keyboard: always reports core events
[    46.821] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event14"
[    46.821] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31d
[    46.821] (--) evdev: Logitech USB Keyboard: Found keys
[    46.821] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    46.821] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3.3/3-3.3:1.0/input/input14/event14"
[    46.821] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 9)
[    46.821] (**) Option "xkb_rules" "evdev"
[    46.821] (**) Option "xkb_model" "pc105"
[    46.821] (**) Option "xkb_layout" "sk"
[    46.821] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event15)
[    46.821] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    46.821] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    46.821] (**) Logitech USB Keyboard: always reports core events
[    46.821] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event15"
[    46.821] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31d
[    46.821] (--) evdev: Logitech USB Keyboard: Found absolute axes
[    46.821] (II) evdev: Logitech USB Keyboard: Forcing absolute x/y axes to exist.
[    46.821] (--) evdev: Logitech USB Keyboard: Found keys
[    46.821] (II) evdev: Logitech USB Keyboard: Forcing relative x/y axes to exist.
[    46.821] (II) evdev: Logitech USB Keyboard: Configuring as mouse
[    46.821] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    46.821] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3.3/3-3.3:1.1/input/input15/event15"
[    46.821] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 10)
[    46.821] (**) Option "xkb_rules" "evdev"
[    46.821] (**) Option "xkb_model" "pc105"
[    46.821] (**) Option "xkb_layout" "sk"
[    46.821] (II) evdev: Logitech USB Keyboard: initialized for absolute axes.
[    46.821] (**) Logitech USB Keyboard: (accel) keeping acceleration scheme 1
[    46.821] (**) Logitech USB Keyboard: (accel) acceleration profile 0
[    46.821] (**) Logitech USB Keyboard: (accel) acceleration factor: 2.000
[    46.821] (**) Logitech USB Keyboard: (accel) acceleration threshold: 4
[    46.821] (II) config/udev: Adding input device SunplusIT SmartMouse (/dev/input/event16)
[    46.821] (**) SunplusIT SmartMouse: Applying InputClass "evdev keyboard catchall"
[    46.821] (II) Using input driver 'evdev' for 'SunplusIT SmartMouse'
[    46.821] (**) SunplusIT SmartMouse: always reports core events
[    46.821] (**) evdev: SunplusIT SmartMouse: Device: "/dev/input/event16"
[    46.821] (--) evdev: SunplusIT SmartMouse: Vendor 0x1bcf Product 0x824
[    46.821] (--) evdev: SunplusIT SmartMouse: Found keys
[    46.821] (II) evdev: SunplusIT SmartMouse: Configuring as keyboard
[    46.821] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3.4/3-3.4:1.0/input/input16/event16"
[    46.821] (II) XINPUT: Adding extended input device "SunplusIT SmartMouse" (type: KEYBOARD, id 11)
[    46.821] (**) Option "xkb_rules" "evdev"
[    46.821] (**) Option "xkb_model" "pc105"
[    46.821] (**) Option "xkb_layout" "sk"
[    46.821] (II) config/udev: Adding input device SunplusIT SmartMouse (/dev/input/event17)
[    46.821] (**) SunplusIT SmartMouse: Applying InputClass "evdev pointer catchall"
[    46.821] (**) SunplusIT SmartMouse: Applying InputClass "evdev keyboard catchall"
[    46.821] (II) Using input driver 'evdev' for 'SunplusIT SmartMouse'
[    46.821] (**) SunplusIT SmartMouse: always reports core events
[    46.821] (**) evdev: SunplusIT SmartMouse: Device: "/dev/input/event17"
[    46.821] (--) evdev: SunplusIT SmartMouse: Vendor 0x1bcf Product 0x824
[    46.821] (--) evdev: SunplusIT SmartMouse: Found 9 mouse buttons
[    46.821] (--) evdev: SunplusIT SmartMouse: Found scroll wheel(s)
[    46.821] (--) evdev: SunplusIT SmartMouse: Found relative axes
[    46.821] (--) evdev: SunplusIT SmartMouse: Found x and y relative axes
[    46.822] (--) evdev: SunplusIT SmartMouse: Found absolute axes
[    46.822] (II) evdev: SunplusIT SmartMouse: Forcing absolute x/y axes to exist.
[    46.822] (--) evdev: SunplusIT SmartMouse: Found keys
[    46.822] (II) evdev: SunplusIT SmartMouse: Configuring as mouse
[    46.822] (II) evdev: SunplusIT SmartMouse: Configuring as keyboard
[    46.822] (II) evdev: SunplusIT SmartMouse: Adding scrollwheel support
[    46.822] (**) evdev: SunplusIT SmartMouse: YAxisMapping: buttons 4 and 5
[    46.822] (**) evdev: SunplusIT SmartMouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    46.822] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3.4/3-3.4:1.1/input/input17/event17"
[    46.822] (II) XINPUT: Adding extended input device "SunplusIT SmartMouse" (type: KEYBOARD, id 12)
[    46.822] (**) Option "xkb_rules" "evdev"
[    46.822] (**) Option "xkb_model" "pc105"
[    46.822] (**) Option "xkb_layout" "sk"
[    46.822] (II) evdev: SunplusIT SmartMouse: initialized for relative axes.
[    46.822] (WW) evdev: SunplusIT SmartMouse: ignoring absolute axes.
[    46.822] (**) SunplusIT SmartMouse: (accel) keeping acceleration scheme 1
[    46.822] (**) SunplusIT SmartMouse: (accel) acceleration profile 0
[    46.822] (**) SunplusIT SmartMouse: (accel) acceleration factor: 2.000
[    46.822] (**) SunplusIT SmartMouse: (accel) acceleration threshold: 4
[    46.822] (II) config/udev: Adding input device SunplusIT SmartMouse (/dev/input/mouse0)
[    46.822] (II) No input driver specified, ignoring this device.
[    46.822] (II) This device may have been added with another device file.
[    46.822] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event10)
[    46.822] (II) No input driver specified, ignoring this device.
[    46.822] (II) This device may have been added with another device file.
[    46.822] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event11)
[    46.822] (II) No input driver specified, ignoring this device.
[    46.822] (II) This device may have been added with another device file.
[    46.822] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event12)
[    46.822] (II) No input driver specified, ignoring this device.
[    46.822] (II) This device may have been added with another device file.
[    46.822] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event5)
[    46.822] (II) No input driver specified, ignoring this device.
[    46.822] (II) This device may have been added with another device file.
[    46.822] (II) config/udev: Adding input device HDA Intel PCH Line Out Side (/dev/input/event6)
[    46.822] (II) No input driver specified, ignoring this device.
[    46.822] (II) This device may have been added with another device file.
[    46.822] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event7)
[    46.822] (II) No input driver specified, ignoring this device.
[    46.822] (II) This device may have been added with another device file.
[    46.822] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event8)
[    46.822] (II) No input driver specified, ignoring this device.
[    46.822] (II) This device may have been added with another device file.
[    46.822] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event9)
[    46.822] (II) No input driver specified, ignoring this device.
[    46.822] (II) This device may have been added with another device file.
[    46.822] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event13)
[    46.823] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    46.823] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[    46.823] (**) Eee PC WMI hotkeys: always reports core events
[    46.823] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event13"
[    46.823] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[    46.823] (--) evdev: Eee PC WMI hotkeys: Found keys
[    46.823] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[    46.823] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input13/event13"
[    46.823] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 13)
[    46.823] (**) Option "xkb_rules" "evdev"
[    46.823] (**) Option "xkb_model" "pc105"
[    46.823] (**) Option "xkb_layout" "sk"
[  1137.543] (II) intel(0): switch to mode 1680x1050@59.9 on pipe 0 using VGA1, position (0, 0), rotation normal
[  1139.416] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1222.032] (II) Open ACPI successful (/var/run/acpid.socket)
[  1222.032] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1222.032] (II) intel(0): switch to mode 1680x1050@59.9 on pipe 0 using VGA1, position (0, 0), rotation normal
[  1222.061] (II) intel(0): EDID vendor "AOC", prod id 8784
[  1222.061] (II) intel(0): Using EDID range info for horizontal sync
[  1222.061] (II) intel(0): Using EDID range info for vertical refresh
[  1222.061] (II) intel(0): Printing DDC gathered Modelines:
[  1222.061] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[  1222.061] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1222.061] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1222.061] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1222.061] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1222.061] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1222.061] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1222.061] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1222.061] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1222.061] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1222.061] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1222.061] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1222.061] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1222.061] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1222.061] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1222.061] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[  1222.061] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[  1222.061] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1222.061] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1222.061] (II) intel(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1249.902] (II) intel(0): EDID vendor "AOC", prod id 8784
[  1249.902] (II) intel(0): Using hsync ranges from config file
[  1249.902] (II) intel(0): Using vrefresh ranges from config file
[  1249.902] (II) intel(0): Printing DDC gathered Modelines:
[  1249.902] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[  1249.902] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1249.902] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1249.902] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1249.902] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1249.902] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1249.902] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1249.902] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1249.902] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1249.902] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1249.902] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1249.902] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1249.902] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1249.902] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1249.903] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1249.903] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[  1249.903] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[  1249.903] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1249.903] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1249.903] (II) intel(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1250.156] (II) intel(0): EDID vendor "AOC", prod id 8784
[  1250.156] (II) intel(0): Using hsync ranges from config file
[  1250.156] (II) intel(0): Using vrefresh ranges from config file
[  1250.156] (II) intel(0): Printing DDC gathered Modelines:
[  1250.156] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[  1250.156] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1250.156] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1250.156] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1250.156] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1250.156] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1250.156] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1250.156] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1250.156] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1250.156] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1250.156] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1250.156] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1250.156] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1250.156] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1250.156] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1250.156] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[  1250.156] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[  1250.156] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1250.156] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1250.156] (II) intel(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)



Also upstart/dbus.log:

> Unknown username "whoopsie" in message bus configuration file 
Unknown username "whoopsie" in message bus configuration file 
Unknown username "whoopsie" in message bus configuration file 
Unknown username "whoopsie" in message bus configuration file 



upstart/lightdm.log:

>  
** (process:6351): WARNING **: Failed to open login1 session: GDBus.Error:org.freedesktop.DBus.Error.FileNotFound: No such file or directory 
 
** (process:2324): WARNING **: Failed to open login1 session: GDBus.Error:org.freedesktop.DBus.Error.FileNotFound: No such file or directory 
 
** (process:2297): WARNING **: Failed to open login1 session: GDBus.Error:org.freedesktop.DBus.Error.FileNotFound: No such file or directory 
 
** (process:2297): WARNING **: Failed to open login1 session: GDBus.Error:org.freedesktop.DBus.Error.FileNotFound: No such file or directory 
 
** (process:2538): WARNING **: Failed to open login1 session: GDBus.Error:org.freedesktop.DBus.Error.FileNotFound: No such file or directory 



Thanks in advance for any advice.

---

### Post by guru102 on 2014-03-24
Now I found a file /etc/dbus1/system.conf:

> <!-- This configuration file controls the systemwide message bus.
     Add a system-local.conf and edit that rather than changing this 
     file directly. -->

<!-- Note that there are any number of ways you can hose yourself
     security-wise by screwing up this file; in particular, you
     probably don't want to listen on any more addresses, add any more
     auth mechanisms, run as a different user, etc. -->

<!DOCTYPE busconfig PUBLIC "-//freedesktop//DTD D-Bus Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>

  <!-- Our well-known bus type, do not change this -->
  <type>system</type>

  <!-- Run as special user -->
  <user>messagebus</user>

  <!-- Fork into daemon mode -->
  <fork/>

  <!-- We use system service launching using a helper -->
  <standard_system_servicedirs/>

  <!-- This is a setuid helper that is used to launch system services -->
  <servicehelper>/usr/lib/dbus-1.0/dbus-daemon-launch-helper</servicehelper>

  <!-- Write a pid file -->
  <pidfile>/var/run/dbus/pid</pidfile>

  <!-- Enable logging to syslog -->
  <syslog/>

  <!-- Only allow socket-credentials-based authentication -->
  <auth>EXTERNAL</auth>

  <!-- Only listen on a local socket. (abstract=/path/to/socket 
       means use abstract namespace, don't really create filesystem 
       file; only Linux supports this. Use path=/whatever on other 
       systems.) -->
  <listen>unix:path=/var/run/dbus/system_bus_socket</listen>

  <policy context="default">
    <!-- All users can connect to system bus -->
    <allow user="*"/>

    <!-- Holes must be punched in service configuration files for
         name ownership and sending method calls -->
    <deny own="*"/>
    <deny send_type="method_call"/>

    <!-- Signals and reply messages (method returns, errors) are allowed
         by default -->
    <allow send_type="signal"/>
    <allow send_requested_reply="true" send_type="method_return"/>
    <allow send_requested_reply="true" send_type="error"/>

    <!-- All messages may be received by default -->
    <allow receive_type="method_call"/>
    <allow receive_type="method_return"/>
    <allow receive_type="error"/>
    <allow receive_type="signal"/>

    <!-- Allow anyone to talk to the message bus -->
    <allow send_destination="org.freedesktop.DBus"/>
    <!-- But disallow some specific bus services -->
    <deny send_destination="org.freedesktop.DBus"
          send_interface="org.freedesktop.DBus"
          send_member="UpdateActivationEnvironment"/>
  </policy>

  <!-- Config files are placed here that among other things, punch 
       holes in the above policy for specific services. -->
  <includedir>system.d</includedir>

  <!-- This is included last so local configuration can override what's 
       in this standard file -->
  <include ignore_missing="yes">system-local.conf</include>

  <include if_selinux_enabled="yes" selinux_root_relative="yes">contexts/dbus_contexts</include>

  <!-- increase default match rules limit from 512 to 5000 because the
       aptdaemon needs relatively many per package in the queue -->
  <limit name="max_match_rules_per_connection">5000</limit>
</busconfig>

There seems to be denied org.freedesktop.dbus, exactly the service throwing warning in lightdm.

Can it be the cause, and can it be somehow changed to be allowed without unwanted consequences?

---

