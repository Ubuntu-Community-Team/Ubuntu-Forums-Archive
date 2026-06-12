---
title: "Xorg hangs on exit"
date: 2014-06-14
forum: General Help
---

### Post by samuel-kadolph on 2014-06-14
I'm trying to use Ubuntu 14.04 on an ASUS EB1033 to display a website on a TV. The first one I assembled and configured (about 2 months ago) has been working perfectly. I assembled another and configured it a few days ago and unfortunately I've been having some problems.

The first time I logged in after installing ubuntu I had tty1 freeze up but was able to log into tty2 and got some repeated messages to the console about the task being blocked for more than 120 seconds. A reboot fixed the issue and I thought nothing of it.

After that I started to have issues with restarting lightdm. Stopping lightdm leaves behind a [Xorg] process that's blocked which prevents me from starting lightdm back up. I also get the same console messages about it being blocked. Eventually the process finally dies after about 30 minutes and I can start lightdm up again.

I've tried upgrading the kernel to 1.13.11 and 1.15.0 with no change. As well as changing the SSD and memory in the box. I've also tried installing 12.04 on the same box with the same problem. I have also tried assembling another box which had the same issue. Looking for some help to try to figure out what Xorg is blocked on and fix it.

```
samuelkadolph@tv3:~$ dmesg | tail -n 27
[ 1441.208961] INFO: task Xorg:1221 blocked for more than 120 seconds.
[ 1441.209320]       Tainted: PF          O 3.13.11-03131103-generic #201406131635
[ 1441.209723] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 1441.210159] Xorg            D ffffffff818114c0     0  1221      1 0x00400002
[ 1441.210168]  ffff88000a4e9cb8 0000000000000002 0000000000014440 ffff88000a4e9fd8
[ 1441.210176]  0000000000014440 0000000000014440 ffff88007a4f5fc0 ffff8800369697f0
[ 1441.210183]  ffff88000a4e9c98 ffff88003659ec28 7fffffffffffffff ffff8800369697f0
[ 1441.210191] Call Trace:
[ 1441.210206]  [<ffffffff8174bcf9>] schedule+0x29/0x70
[ 1441.210213]  [<ffffffff8174afc5>] schedule_timeout+0x1e5/0x250
[ 1441.210222]  [<ffffffff8109b996>] ? ttwu_do_activate.constprop.82+0x66/0x70
[ 1441.210228]  [<ffffffff8109ba57>] ? ttwu_queue+0xb7/0xd0
[ 1441.210236]  [<ffffffff8174eea9>] down_write_failed+0xb9/0x210
[ 1441.210243]  [<ffffffff8174f32d>] ldsem_down_write+0x4d/0x60
[ 1441.210250]  [<ffffffff8174f8dd>] tty_ldisc_lock_pair_timeout+0xad/0x130
[ 1441.210257]  [<ffffffff8145e417>] tty_ldisc_hangup+0xc7/0x230
[ 1441.210265]  [<ffffffff814552cd>] __tty_hangup+0x14d/0x2c0
[ 1441.210272]  [<ffffffff8145702d>] disassociate_ctty+0x7d/0x2c0
[ 1441.210280]  [<ffffffff8106c898>] do_exit+0x388/0x470
[ 1441.210287]  [<ffffffff81022735>] ? syscall_trace_enter+0x165/0x280
[ 1441.210293]  [<ffffffff8106ca14>] do_group_exit+0x44/0xa0
[ 1441.210300]  [<ffffffff8106ca87>] SyS_exit_group+0x17/0x20
[ 1441.210306]  [<ffffffff8175897f>] tracesys+0xe1/0xe6
[ 5090.905119] init: lightdm main process (3070) killed by KILL signal
[ 5090.911000] init: lightdm post-stop process (3371) terminated with status 2
[ 5790.550938] init: lightdm main process (3868) killed by KILL signal
[ 5790.556607] init: lightdm post-stop process (4167) terminated with status 2
```

```
samuelkadolph@tv3:~$ ps aux | grep Xorg | grep -v grep
root      3895  0.1  0.0      0     0 ?        Ds   05:44   0:01 [Xorg]
```

```
samuelkadolph@tv3:~$ sudo cat /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.10.1, UID=0 PID=13417
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
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
[+0.01s] DEBUG: Seat: Creating user session
[+0.01s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.01s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.05s] DEBUG: User /org/freedesktop/Accounts/User1001 added
[+0.08s] DEBUG: User /org/freedesktop/Accounts/User1002 added
[+0.12s] DEBUG: User /org/freedesktop/Accounts/User1003 added
[+0.15s] DEBUG: Seat: Creating display server of type x
[+0.16s] DEBUG: Using VT 7
[+0.16s] DEBUG: Seat: Starting local X display on VT 7
[+0.16s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.16s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.16s] DEBUG: DisplayServer x-0: Launching X Server
[+0.16s] DEBUG: Launching process 13443: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.16s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.16s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.16s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.94s] DEBUG: Got signal 10 from process 13443
[+0.94s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+0.94s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+0.94s] DEBUG: Seat: Display server ready, starting session authentication
[+0.95s] DEBUG: Session pid=13448: Started with service 'lightdm-autologin', username 'kiosk'
[+1.11s] DEBUG: Session pid=13448: Authentication complete with return value 0: Success
[+1.11s] DEBUG: Seat: Session authenticated, running command
[+1.11s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+1.11s] DEBUG: Session pid=13448: Running command /usr/sbin/lightdm-session /usr/bin/kiosk
[+1.11s] DEBUG: Creating shared data directory /var/lib/lightdm-data/kiosk
[+1.11s] DEBUG: Session pid=13448: Logging to .xsession-errors
[+1.13s] DEBUG: Activating VT 7
[+1.13s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c4
[+2.65s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+2.69s] DEBUG: User /org/freedesktop/Accounts/User1001 changed
[+2.73s] DEBUG: User /org/freedesktop/Accounts/User1003 changed
[+11.74s] DEBUG: Got signal 15 from process 1
[+11.74s] DEBUG: Caught Terminated signal, shutting down
[+11.74s] DEBUG: Stopping display manager
[+11.74s] DEBUG: Seat: Stopping
[+11.74s] DEBUG: Seat: Stopping display server
[+11.74s] DEBUG: Sending signal 15 to process 13443
[+11.74s] DEBUG: Seat: Stopping session
[+11.74s] DEBUG: Session pid=13448: Sending SIGTERM
[+11.79s] DEBUG: Session pid=13448: Exited with return value 15
[+11.79s] DEBUG: Seat: Session stopped
[+13.26s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+13.29s] DEBUG: User /org/freedesktop/Accounts/User1001 changed
[+13.33s] DEBUG: User /org/freedesktop/Accounts/User1003 changed
[+16.75s] DEBUG: Sending signal 9 to process 13443
```

```
samuelkadolph@tv3:~$ sudo lsof | grep Xorg
Xorg      3895               root  cwd   unknown                                        /proc/3895/cwd (readlink: No such file or directory)
Xorg      3895               root  rtd   unknown                                        /proc/3895/root (readlink: No such file or directory)
Xorg      3895               root  txt   unknown                                        /proc/3895/exe
```

```
samuelkadolph@tv3:~$ sudo cat /var/log/Xorg.0.log
[  8150.997]
X.Org X Server 1.15.1
Release Date: 2014-04-13
[  8150.998] X Protocol Version 11, Revision 0
[  8150.998] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[  8150.998] Current Operating System: Linux tv3.ottawa.shopify.com 3.13.11-03131103-generic #201406131635 SMP Fri Jun 13 20:36:17 UTC 2014 x86_64
[  8150.998] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.11-03131103-generic root=/dev/mapper/ubuntu--vg-root ro
[  8150.998] Build Date: 16 April 2014  01:36:29PM
[  8150.998] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support)
[  8150.998] Current version of pixman: 0.30.2
[  8150.998]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  8150.998] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  8150.999] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun 14 06:23:52 2014
[  8150.999] (==) Using config file: "/etc/X11/xorg.conf"
[  8150.999] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  8151.000] (==) ServerLayout "Layout0"
[  8151.000] (**) |-->Screen "Screen0" (0)
[  8151.000] (**) |   |-->Monitor "Monitor0"
[  8151.001] (**) |   |-->Device "Device0"
[  8151.001] (**) |-->Input Device "Keyboard0"
[  8151.001] (**) |-->Input Device "Mouse0"
[  8151.001] (==) Automatically adding devices
[  8151.001] (==) Automatically enabling devices
[  8151.001] (==) Automatically adding GPU devices
[  8151.001] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  8151.001]     Entry deleted from font path.
[  8151.001] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  8151.001]     Entry deleted from font path.
[  8151.001] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  8151.002]     Entry deleted from font path.
[  8151.002] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[  8151.002]     Entry deleted from font path.
[  8151.002] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  8151.002]     Entry deleted from font path.
[  8151.002] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  8151.002]     Entry deleted from font path.
[  8151.002] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    built-ins
[  8151.002] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  8151.002] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[  8151.002] (WW) Disabling Keyboard0
[  8151.002] (WW) Disabling Mouse0
[  8151.002] (II) Loader magic: 0x7fabbfd74d60
[  8151.002] (II) Module ABI versions:
[  8151.002]     X.Org ANSI C Emulation: 0.4
[  8151.002]     X.Org Video Driver: 15.0
[  8151.002]     X.Org XInput driver : 20.0
[  8151.002]     X.Org Server Extension : 8.0
[  8151.006] (--) PCI:*(0:4:0:0) 10de:1058:1043:8536 rev 161, Mem @ 0xda000000/16777216, 0xd0000000/134217728, 0xd8000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[  8151.006] Initializing built-in extension Generic Event Extension
[  8151.006] Initializing built-in extension SHAPE
[  8151.006] Initializing built-in extension MIT-SHM
[  8151.006] Initializing built-in extension XInputExtension
[  8151.006] Initializing built-in extension XTEST
[  8151.006] Initializing built-in extension BIG-REQUESTS
[  8151.006] Initializing built-in extension SYNC
[  8151.006] Initializing built-in extension XKEYBOARD
[  8151.006] Initializing built-in extension XC-MISC
[  8151.006] Initializing built-in extension SECURITY
[  8151.006] Initializing built-in extension XINERAMA
[  8151.006] Initializing built-in extension XFIXES
[  8151.006] Initializing built-in extension RENDER
[  8151.007] Initializing built-in extension RANDR
[  8151.007] Initializing built-in extension COMPOSITE
[  8151.007] Initializing built-in extension DAMAGE
[  8151.007] Initializing built-in extension MIT-SCREEN-SAVER
[  8151.007] Initializing built-in extension DOUBLE-BUFFER
[  8151.007] Initializing built-in extension RECORD
[  8151.007] Initializing built-in extension DPMS
[  8151.007] Initializing built-in extension Present
[  8151.007] Initializing built-in extension DRI3
[  8151.007] Initializing built-in extension X-Resource
[  8151.007] Initializing built-in extension XVideo
[  8151.007] Initializing built-in extension XVideo-MotionCompensation
[  8151.007] Initializing built-in extension SELinux
[  8151.007] Initializing built-in extension XFree86-VidModeExtension
[  8151.007] Initializing built-in extension XFree86-DGA
[  8151.007] Initializing built-in extension XFree86-DRI
[  8151.007] Initializing built-in extension DRI2
[  8151.007] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[  8151.007] (II) "glx" will be loaded by default.
[  8151.007] (WW) "xmir" is not to be loaded by default. Skipping.
[  8151.007] (II) LoadModule: "glx"
[  8151.008] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[  8151.038] (II) Module glx: vendor="NVIDIA Corporation"
[  8151.038]     compiled for 4.0.2, module version = 1.0.0
[  8151.038]     Module class: X.Org Server Extension
[  8151.038] (II) NVIDIA GLX Module  304.117  Tue Nov 26 21:45:09 PST 2013
[  8151.038] Loading extension GLX
[  8151.038] (II) LoadModule: "nvidia"
[  8151.038] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  8151.040] (II) Module nvidia: vendor="NVIDIA Corporation"
[  8151.040]     compiled for 4.0.2, module version = 1.0.0
[  8151.040]     Module class: X.Org Video Driver
[  8151.040] (II) NVIDIA dlloader X Driver  304.117  Tue Nov 26 21:27:08 PST 2013
[  8151.040] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  8151.040] (++) using VT number 7


[  8151.041] (II) Loading sub module "fb"
[  8151.041] (II) LoadModule: "fb"
[  8151.041] (II) Loading /usr/lib/xorg/modules/libfb.so
[  8151.042] (II) Module fb: vendor="X.Org Foundation"
[  8151.042]     compiled for 1.15.1, module version = 1.0.0
[  8151.042]     ABI class: X.Org ANSI C Emulation, version 0.4
[  8151.042] (II) Loading sub module "wfb"
[  8151.042] (II) LoadModule: "wfb"
[  8151.043] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  8151.043] (II) Module wfb: vendor="X.Org Foundation"
[  8151.043]     compiled for 1.15.1, module version = 1.0.0
[  8151.043]     ABI class: X.Org ANSI C Emulation, version 0.4
[  8151.043] (II) Loading sub module "ramdac"
[  8151.043] (II) LoadModule: "ramdac"
[  8151.043] (II) Module "ramdac" already built-in
[  8151.044] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[  8151.044] (==) NVIDIA(0): RGB weight 888
[  8151.044] (==) NVIDIA(0): Default visual is TrueColor
[  8151.044] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  8151.044] (**) NVIDIA(0): Option "NoLogo" "True"
[  8151.044] (**) NVIDIA(0): Enabling 2D acceleration
[  8151.495] (II) NVIDIA(GPU-0): Display (Ancor Communications Inc ASUS VW266H (DFP-0)) does
[  8151.495] (II) NVIDIA(GPU-0):     not support NVIDIA 3D Vision stereo.
[  8151.500] (II) NVIDIA(0): NVIDIA GPU GeForce 610M (GF119) at PCI:4:0:0 (GPU-0)
[  8151.500] (--) NVIDIA(0): Memory: 524288 kBytes
[  8151.500] (--) NVIDIA(0): VideoBIOS: 75.19.50.00.09
[  8151.501] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  8151.501] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  8151.503] (--) NVIDIA(0): Valid display device(s) on GeForce 610M at PCI:4:0:0
[  8151.503] (--) NVIDIA(0):     CRT-0
[  8151.503] (--) NVIDIA(0):     Ancor Communications Inc ASUS VW266H (DFP-0) (connected)
[  8151.503] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[  8151.503] (--) NVIDIA(0): Ancor Communications Inc ASUS VW266H (DFP-0): 165.0 MHz maximum pixel clock
[  8151.503] (--) NVIDIA(0): Ancor Communications Inc ASUS VW266H (DFP-0): Internal Single Link TMDS
[  8151.503] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  8151.503] (**) NVIDIA(0):     device Ancor Communications Inc ASUS VW266H (DFP-0) (Using
[  8151.503] (**) NVIDIA(0):     EDID frequencies has been enabled on all display
[  8151.503] (**) NVIDIA(0):     devices.)
[  8151.505] (WW) NVIDIA(GPU-0): The EDID for Ancor Communications Inc ASUS VW266H (DFP-0)
[  8151.505] (WW) NVIDIA(GPU-0):     contradicts itself: mode "1440x576" is specified in the
[  8151.505] (WW) NVIDIA(GPU-0):     EDID; however, the EDID's valid HorizSync range
[  8151.505] (WW) NVIDIA(GPU-0):     (30.000-85.000 kHz) would exclude this mode's HorizSync
[  8151.505] (WW) NVIDIA(GPU-0):     (15.6 kHz); ignoring HorizSync check for mode "1440x576".
[  8151.505] (WW) NVIDIA(GPU-0): The EDID for Ancor Communications Inc ASUS VW266H (DFP-0)
[  8151.505] (WW) NVIDIA(GPU-0):     contradicts itself: mode "1920x1080" is specified in the
[  8151.505] (WW) NVIDIA(GPU-0):     EDID; however, the EDID's valid HorizSync range
[  8151.505] (WW) NVIDIA(GPU-0):     (30.000-85.000 kHz) would exclude this mode's HorizSync
[  8151.506] (WW) NVIDIA(GPU-0):     (28.1 kHz); ignoring HorizSync check for mode
[  8151.506] (WW) NVIDIA(GPU-0):     "1920x1080".
[  8151.507] (WW) NVIDIA(GPU-0): The EDID for Ancor Communications Inc ASUS VW266H (DFP-0)
[  8151.507] (WW) NVIDIA(GPU-0):     contradicts itself: mode "720x480" is specified in the
[  8151.507] (WW) NVIDIA(GPU-0):     EDID; however, the EDID's valid HorizSync range
[  8151.507] (WW) NVIDIA(GPU-0):     (30.000-85.000 kHz) would exclude this mode's HorizSync
[  8151.507] (WW) NVIDIA(GPU-0):     (15.7 kHz); ignoring HorizSync check for mode "720x480".
[  8151.508] (WW) NVIDIA(GPU-0): The EDID for Ancor Communications Inc ASUS VW266H (DFP-0)
[  8151.508] (WW) NVIDIA(GPU-0):     contradicts itself: mode "720x576" is specified in the
[  8151.508] (WW) NVIDIA(GPU-0):     EDID; however, the EDID's valid HorizSync range
[  8151.508] (WW) NVIDIA(GPU-0):     (30.000-85.000 kHz) would exclude this mode's HorizSync
[  8151.508] (WW) NVIDIA(GPU-0):     (15.6 kHz); ignoring HorizSync check for mode "720x576".
[  8151.509] (WW) NVIDIA(GPU-0): The EDID for Ancor Communications Inc ASUS VW266H (DFP-0)
[  8151.509] (WW) NVIDIA(GPU-0):     contradicts itself: mode "720x480" is specified in the
[  8151.509] (WW) NVIDIA(GPU-0):     EDID; however, the EDID's valid HorizSync range
[  8151.509] (WW) NVIDIA(GPU-0):     (30.000-85.000 kHz) would exclude this mode's HorizSync
[  8151.509] (WW) NVIDIA(GPU-0):     (15.7 kHz); ignoring HorizSync check for mode "720x480".
[  8151.510] (WW) NVIDIA(GPU-0): The EDID for Ancor Communications Inc ASUS VW266H (DFP-0)
[  8151.510] (WW) NVIDIA(GPU-0):     contradicts itself: mode "720x576" is specified in the
[  8151.510] (WW) NVIDIA(GPU-0):     EDID; however, the EDID's valid HorizSync range
[  8151.510] (WW) NVIDIA(GPU-0):     (30.000-85.000 kHz) would exclude this mode's HorizSync
[  8151.510] (WW) NVIDIA(GPU-0):     (15.6 kHz); ignoring HorizSync check for mode "720x576".
[  8151.514] (==) NVIDIA(0):
[  8151.514] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[  8151.514] (==) NVIDIA(0):     will be used as the requested mode.
[  8151.515] (==) NVIDIA(0):
[  8151.515] (II) NVIDIA(0): Validated MetaModes:
[  8151.515] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[  8151.515] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[  8151.555] (--) NVIDIA(0): DPI set to (88, 89); computed from "UseEdidDpi" X config
[  8151.555] (--) NVIDIA(0):     option
[  8151.556] (--) Depth 24 pixmap format is 32 bpp
[  8151.556] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[  8151.556] (II) NVIDIA:     access.
[  8151.563] (WW) NVIDIA(0): ACPI: AC power state information is not available under
[  8151.563] (WW) NVIDIA(0):     /sys/class/power_supply/ , nor under
[  8151.563] (WW) NVIDIA(0):     /proc/acpi/ac_adapter/
[  8151.566] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[  8151.602] Loading extension NV-GLX
[  8151.655] (==) NVIDIA(0): Disabling shared memory pixmaps
[  8151.655] (==) NVIDIA(0): Backing store enabled
[  8151.655] (==) NVIDIA(0): Silken mouse enabled
[  8151.655] (**) NVIDIA(0): DPMS enabled
[  8151.656] Loading extension NV-CONTROL
[  8151.657] Loading extension XINERAMA
[  8151.657] (II) Loading sub module "dri2"
[  8151.657] (II) LoadModule: "dri2"
[  8151.657] (II) Module "dri2" already built-in
[  8151.657] (II) NVIDIA(0): [DRI2] Setup complete
[  8151.657] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[  8151.657] (--) RandR disabled
[  8151.673] (II) SELinux: Disabled on system
[  8151.675] (II) Initializing extension GLX
[  8151.710] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  8151.719] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[  8151.720] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  8151.720] (II) LoadModule: "evdev"
[  8151.721] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  8151.721] (II) Module evdev: vendor="X.Org Foundation"
[  8151.721]     compiled for 1.15.0, module version = 2.8.2
[  8151.721]     Module class: X.Org XInput Driver
[  8151.722]     ABI class: X.Org XInput driver, version 20.0
[  8151.722] (II) Using input driver 'evdev' for 'Power Button'
[  8151.722] (**) Power Button: always reports core events
[  8151.722] (**) evdev: Power Button: Device: "/dev/input/event2"
[  8151.722] (--) evdev: Power Button: Vendor 0 Product 0x1
[  8151.722] (--) evdev: Power Button: Found keys
[  8151.722] (II) evdev: Power Button: Configuring as keyboard
[  8151.722] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[  8151.722] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  8151.722] (**) Option "xkb_rules" "evdev"
[  8151.722] (**) Option "xkb_model" "pc105"
[  8151.722] (**) Option "xkb_layout" "us"
[  8151.724] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  8151.724] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  8151.724] (II) Using input driver 'evdev' for 'Power Button'
[  8151.724] (**) Power Button: always reports core events
[  8151.724] (**) evdev: Power Button: Device: "/dev/input/event0"
[  8151.724] (--) evdev: Power Button: Vendor 0 Product 0x1
[  8151.724] (--) evdev: Power Button: Found keys
[  8151.724] (II) evdev: Power Button: Configuring as keyboard
[  8151.724] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[  8151.725] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[  8151.725] (**) Option "xkb_rules" "evdev"
[  8151.725] (**) Option "xkb_model" "pc105"
[  8151.725] (**) Option "xkb_layout" "us"
[  8151.726] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[  8151.727] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  8151.727] (II) Using input driver 'evdev' for 'Sleep Button'
[  8151.727] (**) Sleep Button: always reports core events
[  8151.727] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[  8151.727] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[  8151.727] (--) evdev: Sleep Button: Found keys
[  8151.727] (II) evdev: Sleep Button: Configuring as keyboard
[  8151.727] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[  8151.727] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[  8151.727] (**) Option "xkb_rules" "evdev"
[  8151.727] (**) Option "xkb_model" "pc105"
[  8151.727] (**) Option "xkb_layout" "us"
[  8151.729] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event6)
[  8151.729] (II) No input driver specified, ignoring this device.
[  8151.729] (II) This device may have been added with another device file.
[  8151.730] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event7)
[  8151.730] (II) No input driver specified, ignoring this device.
[  8151.730] (II) This device may have been added with another device file.
[  8151.731] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event3)
[  8151.731] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[  8151.731] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[  8151.731] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[  8151.731] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event3"
[  8151.731] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Vendor 0x45e Product 0x800
[  8151.731] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found keys
[  8151.732] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as keyboard
[  8151.732] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/usb6/6-2/6-2:1.0/input/input6/event3"
[  8151.732] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: KEYBOARD, id 9)
[  8151.732] (**) Option "xkb_rules" "evdev"
[  8151.732] (**) Option "xkb_model" "pc105"
[  8151.732] (**) Option "xkb_layout" "us"
[  8151.734] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event4)
[  8151.734] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev pointer catchall"
[  8151.734] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[  8151.734] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[  8151.734] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event4"
[  8151.734] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Vendor 0x45e Product 0x800
[  8151.734] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found 9 mouse buttons
[  8151.734] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found scroll wheel(s)
[  8151.734] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found relative axes
[  8151.734] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found x and y relative axes
[  8151.734] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as mouse
[  8151.734] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Adding scrollwheel support
[  8151.734] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: YAxisMapping: buttons 4 and 5
[  8151.734] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  8151.734] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/usb6/6-2/6-2:1.1/input/input7/event4"
[  8151.735] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: MOUSE, id 10)
[  8151.735] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: initialized for relative axes.
[  8151.735] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) keeping acceleration scheme 1
[  8151.735] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration profile 0
[  8151.735] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration factor: 2.000
[  8151.735] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration threshold: 4
[  8151.737] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/mouse0)
[  8151.737] (II) No input driver specified, ignoring this device.
[  8151.737] (II) This device may have been added with another device file.
[  8151.738] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event5)
[  8151.738] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[  8151.738] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[  8151.738] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[  8151.738] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event5"
[  8151.738] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Using mtdev for this device
[  8151.739] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Vendor 0x45e Product 0x800
[  8151.739] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found 1 mouse buttons
[  8151.739] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found scroll wheel(s)
[  8151.739] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found relative axes
[  8151.739] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found absolute axes
[  8151.739] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found absolute multitouch axes
[  8151.739] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found x and y absolute axes
[  8151.739] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found keys
[  8151.739] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Forcing relative x/y axes to exist.
[  8151.739] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as mouse
[  8151.739] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as keyboard
[  8151.739] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Adding scrollwheel support
[  8151.739] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: YAxisMapping: buttons 4 and 5
[  8151.739] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  8151.739] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/usb6/6-2/6-2:1.2/input/input8/event5"
[  8151.739] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: KEYBOARD, id 11)
[  8151.739] (**) Option "xkb_rules" "evdev"
[  8151.739] (**) Option "xkb_model" "pc105"
[  8151.739] (**) Option "xkb_layout" "us"
[  8151.740] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: initialized for relative axes.
[  8151.740] (WW) evdev: Microsoft Microsoft® Nano Transceiver v2.0: ignoring absolute axes.
[  8151.741] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) keeping acceleration scheme 1
[  8151.741] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration profile 0
[  8151.741] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration factor: 2.000
[  8151.741] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration threshold: 4
[  8151.742] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/js0)
[  8151.742] (II) No input driver specified, ignoring this device.
[  8151.742] (II) This device may have been added with another device file.
[  8151.743] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event8)
[  8151.743] (II) No input driver specified, ignoring this device.
[  8151.743] (II) This device may have been added with another device file.
[  8151.744] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event9)
[  8151.744] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[  8151.744] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[  8151.744] (**) Eee PC WMI hotkeys: always reports core events
[  8151.744] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event9"
[  8151.745] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[  8151.745] (--) evdev: Eee PC WMI hotkeys: Found keys
[  8151.745] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[  8151.745] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input12/event9"
[  8151.745] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 12)
[  8151.745] (**) Option "xkb_rules" "evdev"
[  8151.745] (**) Option "xkb_model" "pc105"
[  8151.745] (**) Option "xkb_layout" "us"
[  8152.380] (II) NVIDIA(GPU-0): Display (Ancor Communications Inc ASUS VW266H (DFP-0)) does
[  8152.380] (II) NVIDIA(GPU-0):     not support NVIDIA 3D Vision stereo.
[  8152.380] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  8152.380] (**) NVIDIA(0):     device Ancor Communications Inc ASUS VW266H (DFP-0) (Using
[  8152.380] (**) NVIDIA(0):     EDID frequencies has been enabled on all display
[  8152.380] (**) NVIDIA(0):     devices.)
[  8152.382] (WW) NVIDIA(GPU-0): The EDID for Ancor Communications Inc ASUS VW266H (DFP-0)
[  8152.382] (WW) NVIDIA(GPU-0):     contradicts itself: mode "1440x576" is specified in the
[  8152.382] (WW) NVIDIA(GPU-0):     EDID; however, the EDID's valid HorizSync range
[  8152.382] (WW) NVIDIA(GPU-0):     (30.000-85.000 kHz) would exclude this mode's HorizSync
[  8152.382] (WW) NVIDIA(GPU-0):     (15.6 kHz); ignoring HorizSync check for mode "1440x576".
[  8152.383] (WW) NVIDIA(GPU-0): The EDID for Ancor Communications Inc ASUS VW266H (DFP-0)
[  8152.383] (WW) NVIDIA(GPU-0):     contradicts itself: mode "1920x1080" is specified in the
[  8152.383] (WW) NVIDIA(GPU-0):     EDID; however, the EDID's valid HorizSync range
[  8152.383] (WW) NVIDIA(GPU-0):     (30.000-85.000 kHz) would exclude this mode's HorizSync
[  8152.383] (WW) NVIDIA(GPU-0):     (28.1 kHz); ignoring HorizSync check for mode
[  8152.383] (WW) NVIDIA(GPU-0):     "1920x1080".
[  8152.386] (WW) NVIDIA(GPU-0): The EDID for Ancor Communications Inc ASUS VW266H (DFP-0)
[  8152.386] (WW) NVIDIA(GPU-0):     contradicts itself: mode "720x480" is specified in the
[  8152.386] (WW) NVIDIA(GPU-0):     EDID; however, the EDID's valid HorizSync range
[  8152.386] (WW) NVIDIA(GPU-0):     (30.000-85.000 kHz) would exclude this mode's HorizSync
[  8152.386] (WW) NVIDIA(GPU-0):     (15.7 kHz); ignoring HorizSync check for mode "720x480".
[  8152.386] (WW) NVIDIA(GPU-0): The EDID for Ancor Communications Inc ASUS VW266H (DFP-0)
[  8152.386] (WW) NVIDIA(GPU-0):     contradicts itself: mode "720x576" is specified in the
[  8152.386] (WW) NVIDIA(GPU-0):     EDID; however, the EDID's valid HorizSync range
[  8152.386] (WW) NVIDIA(GPU-0):     (30.000-85.000 kHz) would exclude this mode's HorizSync
[  8152.386] (WW) NVIDIA(GPU-0):     (15.6 kHz); ignoring HorizSync check for mode "720x576".
[  8152.389] (WW) NVIDIA(GPU-0): The EDID for Ancor Communications Inc ASUS VW266H (DFP-0)
[  8152.389] (WW) NVIDIA(GPU-0):     contradicts itself: mode "720x480" is specified in the
[  8152.389] (WW) NVIDIA(GPU-0):     EDID; however, the EDID's valid HorizSync range
[  8152.389] (WW) NVIDIA(GPU-0):     (30.000-85.000 kHz) would exclude this mode's HorizSync
[  8152.389] (WW) NVIDIA(GPU-0):     (15.7 kHz); ignoring HorizSync check for mode "720x480".
[  8152.389] (WW) NVIDIA(GPU-0): The EDID for Ancor Communications Inc ASUS VW266H (DFP-0)
[  8152.389] (WW) NVIDIA(GPU-0):     contradicts itself: mode "720x576" is specified in the
[  8152.389] (WW) NVIDIA(GPU-0):     EDID; however, the EDID's valid HorizSync range
[  8152.389] (WW) NVIDIA(GPU-0):     (30.000-85.000 kHz) would exclude this mode's HorizSync
[  8152.389] (WW) NVIDIA(GPU-0):     (15.6 kHz); ignoring HorizSync check for mode "720x576".
[  8152.472] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[  8152.936] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  8162.715] (II) evdev: Eee PC WMI hotkeys: Close
[  8162.716] (II) UnloadModule: "evdev"
[  8162.716] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Close
[  8162.716] (II) UnloadModule: "evdev"
[  8162.716] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Close
[  8162.716] (II) UnloadModule: "evdev"
[  8162.716] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Close
[  8162.716] (II) UnloadModule: "evdev"
[  8162.716] (II) evdev: Sleep Button: Close
[  8162.716] (II) UnloadModule: "evdev"
[  8162.716] (II) evdev: Power Button: Close
[  8162.717] (II) UnloadModule: "evdev"
[  8162.717] (II) evdev: Power Button: Close
[  8162.717] (II) UnloadModule: "evdev"
[  8163.311] (EE) Server terminated successfully (0). Closing log file.
```

---

### Post by alexandari on 2014-06-14
If it's just about killing the X,how about trying 
```
 sudo init 3 
``` 

after that you can re-open X with
```
 sudo init 5 
```

what this does is change the system's runlevel. I won't go into details,try if this works for you. note that it is kind of a dull solution

---

### Post by samuel-kadolph on 2014-06-14
Does not kill Xorg. I forgot to put it in my first post but I am unable to kill -9 the Xorg process.

---

