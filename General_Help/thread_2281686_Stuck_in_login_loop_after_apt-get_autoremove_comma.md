---
title: "Stuck in login loop after apt-get autoremove command - kubuntu 14.04"
date: 2015-06-08
forum: General Help
---

### Post by nagendra_k on 2015-06-08
[COLOR=#000000][FONT=Verdana]Hi,[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Yesterday, when I was installing certain packages, I saw that apt-get throw a message saying there were old kernels that I could remove use the "apt-get autoremove" command. I didn't pay much attention and just ended up doing it anyway. However, I am stuck in a login loop ever since.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I did a google and have tried a number of things - removing the .Xauthority file, checking its permission (which were OK BTW), removing .kde directory, sudo dpkg-reconfigure lightdm etc. Nothing seems to work so far.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I can login to the terminal and if I do a startx from the terminal, that works. However, I try to login using the default login screen presented upon boot, it just throws me back to the same screen and I am unable to determine or fix why this is happening.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Any help will be greatly appreciated![/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Thanks![/FONT][/COLOR]

---

### Post by sandyd on 2015-06-08
Can you do the following:
1. Reboot without any changes, let Xorg do its login loop
2. Press control + alt +f1
3. Login using username/pass
4.

Run
```

mkdir ~/tmplogs
sudo cp /var/log/lightdm/*.log ~/tmplogs/
cp /var/log/Xorg.0.log ~/tmplogs/Xorg.0.log
cp ~/.xsession-errors ~/tmplogs/xsession-errors
sudo chown $(whoami):$(whoami) ~/tmplogs/*.log
```

5. Login with startx. There should now be a few files in a folder named "tmplogs" in your home folder. Please post their contents here. Please use code tags to post.

---

### Post by nagendra_k on 2015-06-09
Here are the outputs of the different files:

**lightdm.log**
```

[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.10.5, UID=0 PID=1153
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/40-kde-plasma.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/40-lightdm-kde-greeter.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Registered seat module surfaceflinger
[+0.01s] DEBUG: Adding default seat
[+0.01s] DEBUG: Seat: Starting
[+0.01s] DEBUG: Seat: Creating greeter session
[+0.02s] DEBUG: Seat: Creating display server of type x
[+0.03s] DEBUG: Deactivating Plymouth
[+0.05s] DEBUG: Using VT 7
[+0.05s] DEBUG: Seat: Starting local X display on VT 7
[+0.05s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.05s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.05s] DEBUG: DisplayServer x-0: Launching X Server
[+0.05s] DEBUG: Launching process 1170: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.05s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.05s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.05s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.67s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.67s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+1.26s] DEBUG: Got signal 10 from process 1170
[+1.26s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+1.26s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+1.26s] DEBUG: Quitting Plymouth; retaining splash
[+1.29s] DEBUG: Seat: Display server ready, starting session authentication
[+1.29s] DEBUG: Session pid=1197: Started with service 'lightdm-greeter', username 'lightdm'
[+1.33s] DEBUG: Session pid=1197: Authentication complete with return value 0: Success
[+1.33s] DEBUG: Seat: Session authenticated, running command
[+1.34s] DEBUG: Session pid=1197: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-kde-greeter
[+1.34s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+1.34s] DEBUG: Session pid=1197: Logging to /var/log/lightdm/x-0-greeter.log
[+1.36s] DEBUG: Activating VT 7
[+1.36s] DEBUG: Activating login1 session c1
[+10.50s] DEBUG: Session pid=1197: Greeter connected version=1.10.5
[+33.03s] DEBUG: Session pid=1197: Greeter start authentication for nagendra
[+33.03s] DEBUG: Session pid=1647: Started with service 'lightdm', username 'nagendra'
[+33.08s] DEBUG: Session pid=1647: Got 1 message(s) from PAM
[+33.08s] DEBUG: Session pid=1197: Prompt greeter with 1 message(s)
[+33.08s] DEBUG: Session pid=1197: Continue authentication
[+33.68s] DEBUG: Session pid=1647: Authentication complete with return value 0: Success
[+33.68s] DEBUG: Session pid=1197: Authenticate result for user nagendra: Success
[+33.68s] DEBUG: Session pid=1197: User nagendra authorized
[+35.55s] DEBUG: Session pid=1197: Greeter requests session kde-plasma
[+35.55s] DEBUG: Seat: Stopping greeter; display server will be re-used for user session
[+35.55s] DEBUG: Session pid=1197: Sending SIGTERM
[+35.56s] DEBUG: Session pid=1197: Greeter closed communication channel
[+35.56s] DEBUG: Session pid=1197: Exited with return value 0
[+35.56s] DEBUG: Seat: Session stopped
[+35.56s] DEBUG: Seat: Greeter stopped, running session
[+35.56s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+35.56s] DEBUG: Session pid=1647: Running command /usr/sbin/lightdm-session /usr/bin/startkde
[+35.56s] DEBUG: Creating shared data directory /var/lib/lightdm-data/nagendra
[+35.56s] DEBUG: Session pid=1647: Logging to .xsession-errors
[+35.59s] DEBUG: Activating VT 7
[+35.59s] DEBUG: Activating login1 session c2
[+37.07s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+68.16s] DEBUG: Session pid=1647: Exited with return value 139
[+68.16s] DEBUG: Seat: Session stopped
[+68.16s] DEBUG: Seat: Stopping display server, no sessions require it
[+68.16s] DEBUG: Sending signal 15 to process 1170
[+68.17s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+68.35s] DEBUG: Process 1170 exited with return value 0
[+68.35s] DEBUG: DisplayServer x-0: X server stopped
[+68.35s] DEBUG: Releasing VT 7
[+68.35s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+68.35s] DEBUG: Seat: Display server stopped
[+68.35s] DEBUG: Seat: Active display server stopped, starting greeter
[+68.35s] DEBUG: Seat: Creating greeter session
[+68.35s] DEBUG: Seat: Creating display server of type x
[+68.35s] DEBUG: Using VT 7
[+68.35s] DEBUG: Seat: Starting local X display on VT 7
[+68.35s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+68.35s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+68.35s] DEBUG: DisplayServer x-0: Launching X Server
[+68.35s] DEBUG: Launching process 3655: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+68.35s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+68.47s] DEBUG: Got signal 10 from process 3655
[+68.47s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+68.47s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+68.48s] DEBUG: Seat: Display server ready, starting session authentication
[+68.48s] DEBUG: Session pid=3661: Started with service 'lightdm-greeter', username 'lightdm'
[+68.49s] DEBUG: Session pid=3661: Authentication complete with return value 0: Success
[+68.49s] DEBUG: Seat: Session authenticated, running command
[+68.49s] DEBUG: Session pid=3661: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-kde-greeter
[+68.49s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+68.49s] DEBUG: Session pid=3661: Logging to /var/log/lightdm/x-0-greeter.log
[+68.50s] DEBUG: Activating VT 7
[+68.50s] DEBUG: Activating login1 session c3
[+68.79s] DEBUG: Session pid=3661: Greeter connected version=1.10.5
[+90.24s] DEBUG: User /org/freedesktop/Accounts/User1000 changed

```

**x-0-greeter.log:**
```

QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /var/lib/lightdm/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
file:///usr/share/kde4/apps/lightdm-kde-greeter/themes/userbar/main.qml:135: Unable to assign [undefined] to QString usersession

```

**x-0.log:**
```


X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
Current Operating System: Linux Inspiron-1525-Kubuntu 3.13.0-53-generic #89-Ubuntu SMP Wed May 20 10:34:39 UTC 2015 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-53-generic root=UUID=ec6e6c09-c091-42ea-a2ce-0808923a09b5 ro quiet splash vt.handoff=7
Build Date: 12 February 2015  02:49:29PM
xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.30.2
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun  9 08:24:02 2015
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
Loading extension GLX
(II) AIGLX: Suspending AIGLX clients for VT switch

```

**Xorg.0.log:**
```

[    95.348] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    95.348] X Protocol Version 11, Revision 0
[    95.348] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[    95.348] Current Operating System: Linux Inspiron-1525-Kubuntu 3.13.0-53-generic #89-Ubuntu SMP Wed May 20 10:34:39 UTC 2015 x86_64
[    95.348] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-53-generic root=UUID=ec6e6c09-c091-42ea-a2ce-0808923a09b5 ro quiet splash vt.handoff=7
[    95.348] Build Date: 12 February 2015  02:49:29PM
[    95.348] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[    95.349] Current version of pixman: 0.30.2
[    95.349]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    95.349] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    95.349] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun  9 08:24:02 2015
[    95.349] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    95.349] (==) No Layout section.  Using the first Screen section.
[    95.349] (==) No screen section available. Using defaults.
[    95.349] (**) |-->Screen "Default Screen Section" (0)
[    95.349] (**) |   |-->Monitor "<default monitor>"
[    95.349] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    95.349] (==) Automatically adding devices
[    95.349] (==) Automatically enabling devices
[    95.349] (==) Automatically adding GPU devices
[    95.349] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    95.349]     Entry deleted from font path.
[    95.349] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    95.349]     Entry deleted from font path.
[    95.349] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    95.349]     Entry deleted from font path.
[    95.349] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    95.349]     Entry deleted from font path.
[    95.349] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    95.349]     Entry deleted from font path.
[    95.349] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    95.350] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    95.350] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    95.350] (II) Loader magic: 0x7fb2f8d74d40
[    95.350] (II) Module ABI versions:
[    95.350]     X.Org ANSI C Emulation: 0.4
[    95.350]     X.Org Video Driver: 15.0
[    95.350]     X.Org XInput driver : 20.0
[    95.350]     X.Org Server Extension : 8.0
[    95.350] (II) xfree86: Adding drm device (/dev/dri/card0)
[    95.352] (--) PCI:*(0:0:2:0) 8086:2a02:1028:022f rev 12, Mem @ 0xfea00000/1048576, 0xe0000000/268435456, I/O @ 0x0000eff8/8
[    95.352] (--) PCI: (0:0:2:1) 8086:2a03:1028:022f rev 12, Mem @ 0xfeb00000/1048576
[    95.352] Initializing built-in extension Generic Event Extension
[    95.352] Initializing built-in extension SHAPE
[    95.352] Initializing built-in extension MIT-SHM
[    95.352] Initializing built-in extension XInputExtension
[    95.352] Initializing built-in extension XTEST
[    95.352] Initializing built-in extension BIG-REQUESTS
[    95.352] Initializing built-in extension SYNC
[    95.352] Initializing built-in extension XKEYBOARD
[    95.352] Initializing built-in extension XC-MISC
[    95.352] Initializing built-in extension SECURITY
[    95.352] Initializing built-in extension XINERAMA
[    95.352] Initializing built-in extension XFIXES
[    95.352] Initializing built-in extension RENDER
[    95.352] Initializing built-in extension RANDR
[    95.352] Initializing built-in extension COMPOSITE
[    95.352] Initializing built-in extension DAMAGE
[    95.352] Initializing built-in extension MIT-SCREEN-SAVER
[    95.352] Initializing built-in extension DOUBLE-BUFFER
[    95.352] Initializing built-in extension RECORD
[    95.352] Initializing built-in extension DPMS
[    95.352] Initializing built-in extension Present
[    95.352] Initializing built-in extension DRI3
[    95.352] Initializing built-in extension X-Resource
[    95.352] Initializing built-in extension XVideo
[    95.352] Initializing built-in extension XVideo-MotionCompensation
[    95.352] Initializing built-in extension SELinux
[    95.352] Initializing built-in extension XFree86-VidModeExtension
[    95.352] Initializing built-in extension XFree86-DGA
[    95.352] Initializing built-in extension XFree86-DRI
[    95.352] Initializing built-in extension DRI2
[    95.352] (II) LoadModule: "glx"
[    95.353] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    95.354] (II) Module glx: vendor="X.Org Foundation"
[    95.354]     compiled for 1.15.1, module version = 1.0.0
[    95.354]     ABI class: X.Org Server Extension, version 8.0
[    95.354] (==) AIGLX enabled
[    95.354] Loading extension GLX
[    95.354] (==) Matched intel as autoconfigured driver 0
[    95.354] (==) Matched intel as autoconfigured driver 1
[    95.354] (==) Matched modesetting as autoconfigured driver 2
[    95.354] (==) Matched fbdev as autoconfigured driver 3
[    95.354] (==) Matched vesa as autoconfigured driver 4
[    95.354] (==) Assigned the driver to the xf86ConfigLayout
[    95.354] (II) LoadModule: "intel"
[    95.354] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    95.355] (II) Module intel: vendor="X.Org Foundation"
[    95.355]     compiled for 1.15.1, module version = 2.99.910
[    95.355]     Module class: X.Org Video Driver
[    95.355]     ABI class: X.Org Video Driver, version 15.0
[    95.355] (II) LoadModule: "modesetting"
[    95.355] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    95.355] (II) Module modesetting: vendor="X.Org Foundation"
[    95.355]     compiled for 1.15.0, module version = 0.8.1
[    95.355]     Module class: X.Org Video Driver
[    95.355]     ABI class: X.Org Video Driver, version 15.0
[    95.355] (II) LoadModule: "fbdev"
[    95.355] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    95.355] (II) Module fbdev: vendor="X.Org Foundation"
[    95.355]     compiled for 1.15.0, module version = 0.4.4
[    95.355]     Module class: X.Org Video Driver
[    95.355]     ABI class: X.Org Video Driver, version 15.0
[    95.355] (II) LoadModule: "vesa"
[    95.355] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    95.356] (II) Module vesa: vendor="X.Org Foundation"
[    95.356]     compiled for 1.15.0, module version = 2.3.3
[    95.356]     Module class: X.Org Video Driver
[    95.356]     ABI class: X.Org Video Driver, version 15.0
[    95.356] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    95.356] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    95.356] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    95.356] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    95.356] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    95.356] (II) FBDEV: driver for framebuffer: fbdev
[    95.356] (II) VESA: driver for VESA chipsets: vesa
[    95.356] (++) using VT number 7

[    95.356] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1.6 (Timo Aaltonen <tjaalton@debian.org>)
[    95.356] (WW) Falling back to old probe method for modesetting
[    95.356] (WW) Falling back to old probe method for fbdev
[    95.356] (II) Loading sub module "fbdevhw"
[    95.356] (II) LoadModule: "fbdevhw"
[    95.357] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    95.357] (II) Module fbdevhw: vendor="X.Org Foundation"
[    95.357]     compiled for 1.15.1, module version = 0.0.2
[    95.357]     ABI class: X.Org Video Driver, version 15.0
[    95.357] (WW) Falling back to old probe method for vesa
[    95.357] (--) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    95.357] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3
[    95.357] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    95.357] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    95.357] (==) intel(0): RGB weight 888
[    95.357] (==) intel(0): Default visual is TrueColor
[    95.358] (**) intel(0): Framebuffer tiled
[    95.358] (**) intel(0): Pixmaps tiled
[    95.358] (**) intel(0): "Tear free" disabled
[    95.358] (**) intel(0): Forcing per-crtc-pixmaps? no
[    95.358] (II) intel(0): Output LVDS1 has no monitor section
[    95.359] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
[    95.359] (II) intel(0): Output VGA1 has no monitor section
[    95.359] (II) intel(0): Output HDMI1 has no monitor section
[    95.359] (II) intel(0): Output TV1 has no monitor section
[    95.359] (II) intel(0): Output VIRTUAL1 has no monitor section
[    95.359] (--) intel(0): Output LVDS1 using initial mode 1280x800 on pipe 0
[    95.359] (==) intel(0): DPI set to (96, 96)
[    95.359] (II) Loading sub module "dri2"
[    95.359] (II) LoadModule: "dri2"
[    95.359] (II) Module "dri2" already built-in
[    95.359] (II) UnloadModule: "modesetting"
[    95.359] (II) Unloading modesetting
[    95.359] (II) UnloadModule: "fbdev"
[    95.359] (II) Unloading fbdev
[    95.359] (II) UnloadSubModule: "fbdevhw"
[    95.359] (II) Unloading fbdevhw
[    95.359] (II) UnloadModule: "vesa"
[    95.359] (II) Unloading vesa
[    95.359] (==) Depth 24 pixmap format is 32 bpp
[    95.360] (II) intel(0): SNA initialized with Broadwater (gen4) backend
[    95.360] (==) intel(0): Backing store enabled
[    95.360] (==) intel(0): Silken mouse enabled
[    95.360] (II) intel(0): HW Cursor enabled
[    95.360] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    95.360] (==) intel(0): DPMS enabled
[    95.360] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    95.360] (II) intel(0): [DRI2] Setup complete
[    95.360] (II) intel(0): [DRI2]   DRI driver: i965
[    95.360] (II) intel(0): [DRI2]   VDPAU driver: i965
[    95.360] (II) intel(0): direct rendering: DRI2 Enabled
[    95.360] (==) intel(0): hotplug detection: "enabled"
[    95.361] (--) RandR disabled
[    95.371] (II) SELinux: Disabled on system
[    95.376] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    95.376] (II) AIGLX: enabled GLX_ARB_create_context
[    95.376] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    95.376] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    95.376] (II) AIGLX: enabled GLX_INTEL_swap_event
[    95.376] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    95.376] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    95.376] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    95.376] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    95.376] (II) AIGLX: Loaded and initialized i965
[    95.376] (II) GLX: Initialized DRI2 GL provider for screen 0
[    95.382] (II) intel(0): switch to mode 1280x800@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    95.394] (II) intel(0): Setting screen physical size to 338 x 211
[    95.409] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    95.414] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    95.414] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    95.414] (II) LoadModule: "evdev"
[    95.414] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    95.414] (II) Module evdev: vendor="X.Org Foundation"
[    95.414]     compiled for 1.15.0, module version = 2.8.2
[    95.414]     Module class: X.Org XInput Driver
[    95.414]     ABI class: X.Org XInput driver, version 20.0
[    95.414] (II) Using input driver 'evdev' for 'Video Bus'
[    95.414] (**) Video Bus: always reports core events
[    95.414] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    95.414] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    95.414] (--) evdev: Video Bus: Found keys
[    95.414] (II) evdev: Video Bus: Configuring as keyboard
[    95.414] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input13/event6"
[    95.414] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[    95.414] (**) Option "xkb_rules" "evdev"
[    95.414] (**) Option "xkb_model" "pc105"
[    95.414] (**) Option "xkb_layout" "us"
[    95.415] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    95.415] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    95.415] (II) Using input driver 'evdev' for 'Power Button'
[    95.415] (**) Power Button: always reports core events
[    95.415] (**) evdev: Power Button: Device: "/dev/input/event1"
[    95.415] (--) evdev: Power Button: Vendor 0 Product 0x1
[    95.415] (--) evdev: Power Button: Found keys
[    95.415] (II) evdev: Power Button: Configuring as keyboard
[    95.415] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    95.415] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    95.415] (**) Option "xkb_rules" "evdev"
[    95.415] (**) Option "xkb_model" "pc105"
[    95.415] (**) Option "xkb_layout" "us"
[    95.416] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    95.416] (II) No input driver specified, ignoring this device.
[    95.416] (II) This device may have been added with another device file.
[    95.416] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    95.416] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    95.416] (II) Using input driver 'evdev' for 'Sleep Button'
[    95.416] (**) Sleep Button: always reports core events
[    95.416] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    95.416] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    95.416] (--) evdev: Sleep Button: Found keys
[    95.416] (II) evdev: Sleep Button: Configuring as keyboard
[    95.416] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    95.416] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    95.416] (**) Option "xkb_rules" "evdev"
[    95.416] (**) Option "xkb_model" "pc105"
[    95.416] (**) Option "xkb_layout" "us"
[    95.417] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    95.417] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    95.417] (II) config/udev: Adding input device Laptop Integrated Webcam (/dev/input/event7)
[    95.417] (**) Laptop Integrated Webcam: Applying InputClass "evdev keyboard catchall"
[    95.417] (II) Using input driver 'evdev' for 'Laptop Integrated Webcam'
[    95.417] (**) Laptop Integrated Webcam: always reports core events
[    95.417] (**) evdev: Laptop Integrated Webcam: Device: "/dev/input/event7"
[    95.417] (--) evdev: Laptop Integrated Webcam: Vendor 0x5a9 Product 0x2640
[    95.417] (--) evdev: Laptop Integrated Webcam: Found keys
[    95.417] (II) evdev: Laptop Integrated Webcam: Configuring as keyboard
[    95.417] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input14/event7"
[    95.417] (II) XINPUT: Adding extended input device "Laptop Integrated Webcam" (type: KEYBOARD, id 9)
[    95.417] (**) Option "xkb_rules" "evdev"
[    95.417] (**) Option "xkb_model" "pc105"
[    95.417] (**) Option "xkb_layout" "us"
[    95.418] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event11)
[    95.418] (II) No input driver specified, ignoring this device.
[    95.418] (II) This device may have been added with another device file.
[    95.418] (II) config/udev: Adding input device HDA Intel Front Headphone Front (/dev/input/event10)
[    95.418] (II) No input driver specified, ignoring this device.
[    95.418] (II) This device may have been added with another device file.
[    95.419] (II) config/udev: Adding input device HDA Intel Front Headphone Surround (/dev/input/event9)
[    95.419] (II) No input driver specified, ignoring this device.
[    95.419] (II) This device may have been added with another device file.
[    95.419] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    95.419] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    95.419] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    95.419] (**) AT Translated Set 2 keyboard: always reports core events
[    95.419] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    95.419] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    95.419] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    95.419] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    95.419] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    95.419] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    95.419] (**) Option "xkb_rules" "evdev"
[    95.419] (**) Option "xkb_model" "pc105"
[    95.419] (**) Option "xkb_layout" "us"
[    95.420] (II) config/udev: Adding input device ALPS PS/2 Device (/dev/input/event4)
[    95.420] (**) ALPS PS/2 Device: Applying InputClass "evdev pointer catchall"
[    95.420] (II) Using input driver 'evdev' for 'ALPS PS/2 Device'
[    95.420] (**) ALPS PS/2 Device: always reports core events
[    95.420] (**) evdev: ALPS PS/2 Device: Device: "/dev/input/event4"
[    95.420] (--) evdev: ALPS PS/2 Device: Vendor 0x2 Product 0x8
[    95.420] (--) evdev: ALPS PS/2 Device: Found 3 mouse buttons
[    95.420] (--) evdev: ALPS PS/2 Device: Found relative axes
[    95.420] (--) evdev: ALPS PS/2 Device: Found x and y relative axes
[    95.420] (II) evdev: ALPS PS/2 Device: Configuring as mouse
[    95.420] (**) evdev: ALPS PS/2 Device: YAxisMapping: buttons 4 and 5
[    95.420] (**) evdev: ALPS PS/2 Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    95.420] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event4"
[    95.420] (II) XINPUT: Adding extended input device "ALPS PS/2 Device" (type: MOUSE, id 11)
[    95.420] (II) evdev: ALPS PS/2 Device: initialized for relative axes.
[    95.420] (**) ALPS PS/2 Device: (accel) keeping acceleration scheme 1
[    95.420] (**) ALPS PS/2 Device: (accel) acceleration profile 0
[    95.420] (**) ALPS PS/2 Device: (accel) acceleration factor: 2.000
[    95.420] (**) ALPS PS/2 Device: (accel) acceleration threshold: 4
[    95.420] (II) config/udev: Adding input device ALPS PS/2 Device (/dev/input/mouse0)
[    95.420] (II) No input driver specified, ignoring this device.
[    95.420] (II) This device may have been added with another device file.
[    95.421] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event5)
[    95.421] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    95.421] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    95.421] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "Default clickpad buttons"
[    95.421] (II) LoadModule: "synaptics"
[    95.421] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    95.421] (II) Module synaptics: vendor="X.Org Foundation"
[    95.421]     compiled for 1.15.0, module version = 1.7.4
[    95.421]     Module class: X.Org XInput Driver
[    95.421]     ABI class: X.Org XInput driver, version 20.0
[    95.421] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    95.421] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    95.421] (**) Option "Device" "/dev/input/event5"
[    95.440] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023 (res 0)
[    95.440] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767 (res 0)
[    95.440] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    95.440] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[    95.440] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    95.440] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[    95.440] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[    95.440] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    95.440] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    95.456] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input9/event5"
[    95.456] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 12)
[    95.456] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    95.456] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MaxSpeed is now 1.75
[    95.456] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) AccelFactor is now 0.156
[    95.456] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    95.457] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    95.457] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    95.457] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    95.457] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    95.457] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[    95.458] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[    95.463] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event8)
[    95.463] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    95.463] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    95.463] (**) Dell WMI hotkeys: always reports core events
[    95.463] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event8"
[    95.463] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    95.463] (--) evdev: Dell WMI hotkeys: Found keys
[    95.463] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    95.463] (**) Option "config_info" "udev:/sys/devices/virtual/input/input16/event8"
[    95.463] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 13)
[    95.463] (**) Option "xkb_rules" "evdev"
[    95.463] (**) Option "xkb_model" "pc105"
[    95.463] (**) Option "xkb_layout" "us"
[   110.284] (II) AIGLX: Suspending AIGLX clients for VT switch

```

**xsession-errors** (empty file)

Thanks a bunch for trying to help!

---

### Post by nagendra_k on 2015-06-11
Any other ideas on what might be wrong?

---

