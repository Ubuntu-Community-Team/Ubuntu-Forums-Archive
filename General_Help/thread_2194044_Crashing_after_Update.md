---
title: "Crashing after Update"
date: 2013-12-16
forum: General Help
---

### Post by nwordz on 2013-12-16
I am using ubuntu 12.04LTS
Its an older system that I built about 4 years ago. Built on budget parts. (still perfect for what I use it for)

I ran the update manager, it downloaded and installed the new updates (as of a month or so ago) the it asked to restart so I did. Afterwords it would not boot fully in to ubuntu.
I believe that i created the problem when around september I was trying to get a wifi usb adapter to work. I got frustrated and used some make files and did some other stuff that I found out later can make a system unstable.
I was able to boot up with a bootable USB stick, and installed ubuntu on to another HDD (an old 10gig one that some how still works) I have access to the files and I have saved all my data in my home folder. Side note, I couldn't copy and paste the whole drive because of lacking permissions or something, is there a way to go through terminal and copy everything over? End side note.
I would like to be able to repair my old OS and get in to the wxBanker program to export my accounts. Its been at least a month since I have had access to my finance books and it would be really nice to get back in touch with them.
Once I got everything that I want, I wold do a clean install on that drive and start over fresh.

My system boots up, I can select which HDD or device I want to boot from, then it will start to boot, flash the purple screen, then goes to black screen with about a page of text scrolling through and finally getting stuck with this on the screen. Or atleast as best as I can read my hand writing from a month ago (might be spelling mistakes).
```
Speeh-dipatcher disubed;elt /etc/default/speech-dispacher
*Stopping system V initialistation compatibility                             [ok]
*Starting system V runlevel compatibility                                    [ok]
*Starting crash report submission daemon                                     [ok]
*Starting CPU interrupts Balancing daemon                                    [ok]
*Starting restore sound card(s') mixer state(s)                              [ok]
*Starting ACPI daemon                                                        [ok]
*Starting anac (L) ranistic cron                                             [ok]
*Starting save kernal messages                                               [ok]
*Starting regular backend program processing daemon                          [ok]
*deferred execution scheduler                                                [ok]
*Stopping restore sound card(s') mixer state(s)                              [ok]
*Stopping cold plug devices                                                  [ok]
*Stopping log inital device creation                                         [ok]
*Starting network connection manager wcid                                    [ok]
*Starting configure virtual network devices                                  [ok]
*Stopping save kernal messages                                               [ok]
*Stopping configure virtual network devices                                  [ok]
*Starting configure network device security                                  [ok]
*Starting send an event to indicate plymouth is up                           [ok]
*Starting light DM display manager                                           [ok]
*Stopping send an event to indicate plymouth is up                           [ok]

```

From here nothing happen, keys do nothing and even letting it sit 60 min leads to nothing.

Thanks for the help everyone!
Im looking forward to some challenges and some learning along the way!

---

### Post by ian-weisser on 2013-12-16
Any helpful error messages in /var/log/syslog or /var/log/dmesg or /var/log/Xorg.0.log?

---

### Post by nwordz on 2013-12-16
Thanks for the help! I do not know if there is any helpful info in there, but there is a ton of text, too much to post here. Ill upload the files.
I dont know how to even understand the report.

The syslog and dmesg are too large of text files to upload through the forum uploader. I may try to split them up to make them smaller.

Thanks for the help Ian!

EDIT: Figured that I may as well add the code and take the attachment down for easier use.

Xorg.0.log

```
[    20.999] X.Org X Server 1.13.0
Release Date: 2012-09-05
[    20.999] X Protocol Version 11, Revision 0
[    20.999] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    20.999] Current Operating System: Linux zack-A880G 3.5.0-43-generic #66~precise1-Ubuntu SMP Thu Oct 24 14:55:08 UTC 2013 i686
[    21.010] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-43-generic root=UUID=a5baa10f-bb69-49cc-998b-f6e8c4f55e7d ro quiet splash
[    21.010] Build Date: 16 October 2013  04:45:28PM
[    21.010] xorg-server 2:1.13.0-0ubuntu6.1~precise4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    21.010] Current version of pixman: 0.24.4
[    21.010]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    21.010] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.010] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 15 15:14:36 2013
[    21.010] (==) Using config file: "/etc/X11/xorg.conf"
[    21.010] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.011] (==) No Layout section.  Using the first Screen section.
[    21.011] (==) No screen section available. Using defaults.
[    21.011] (**) |-->Screen "Default Screen Section" (0)
[    21.011] (**) |   |-->Monitor "<default monitor>"
[    21.011] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    21.011] (**) |   |-->Device "Default Device"
[    21.011] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    21.011] (==) Automatically adding devices
[    21.011] (==) Automatically enabling devices
[    21.011] (==) Automatically adding GPU devices
[    21.208] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.208]     Entry deleted from font path.
[    21.208] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    21.208]     Entry deleted from font path.
[    21.208] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    21.208]     Entry deleted from font path.
[    21.209] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    21.209]     Entry deleted from font path.
[    21.209] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    21.209]     Entry deleted from font path.
[    21.209] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    21.209]     Entry deleted from font path.
[    21.209] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    21.209] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.209] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.209] (II) Loader magic: 0xb77a1620
[    21.209] (II) Module ABI versions:
[    21.209]     X.Org ANSI C Emulation: 0.4
[    21.209]     X.Org Video Driver: 13.0
[    21.209]     X.Org XInput driver : 18.0
[    21.209]     X.Org Server Extension : 7.0
[    21.210] (--) PCI:*(0:1:0:0) 10de:0de1:19da:1167 rev 161, Mem @ 0xfd000000/16777216, 0xd8000000/134217728, 0xd6000000/33554432, I/O @ 0x0000c800/128, BIOS @ 0x????????/524288
[    21.210] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.210] Initializing built-in extension Generic Event Extension
[    21.210] Initializing built-in extension SHAPE
[    21.210] Initializing built-in extension MIT-SHM
[    21.210] Initializing built-in extension XInputExtension
[    21.210] Initializing built-in extension XTEST
[    21.210] Initializing built-in extension BIG-REQUESTS
[    21.210] Initializing built-in extension SYNC
[    21.210] Initializing built-in extension XKEYBOARD
[    21.210] Initializing built-in extension XC-MISC
[    21.210] Initializing built-in extension SECURITY
[    21.210] Initializing built-in extension XINERAMA
[    21.210] Initializing built-in extension XFIXES
[    21.210] Initializing built-in extension RENDER
[    21.210] Initializing built-in extension RANDR
[    21.210] Initializing built-in extension COMPOSITE
[    21.210] Initializing built-in extension DAMAGE
[    21.210] Initializing built-in extension MIT-SCREEN-SAVER
[    21.210] Initializing built-in extension DOUBLE-BUFFER
[    21.210] Initializing built-in extension RECORD
[    21.210] Initializing built-in extension DPMS
[    21.210] Initializing built-in extension X-Resource
[    21.210] Initializing built-in extension XVideo
[    21.210] Initializing built-in extension XVideo-MotionCompensation
[    21.210] Initializing built-in extension XFree86-VidModeExtension
[    21.210] Initializing built-in extension XFree86-DGA
[    21.210] Initializing built-in extension XFree86-DRI
[    21.210] Initializing built-in extension DRI2
[    21.210] (II) LoadModule: "glx"
[    21.210] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    21.247] (II) Module glx: vendor="NVIDIA Corporation"
[    21.247]     compiled for 4.0.2, module version = 1.0.0
[    21.247]     Module class: X.Org Server Extension
[    21.252] (II) NVIDIA GLX Module  319.32  Wed Jun 19 14:13:45 PDT 2013
[    21.252] Loading extension GLX
[    21.252] (==) Matched nvidia as autoconfigured driver 0
[    21.252] (==) Matched nouveau as autoconfigured driver 1
[    21.252] (==) Matched nv as autoconfigured driver 2
[    21.252] (==) Matched vesa as autoconfigured driver 3
[    21.252] (==) Matched modesetting as autoconfigured driver 4
[    21.252] (==) Matched fbdev as autoconfigured driver 5
[    21.252] (==) Assigned the driver to the xf86ConfigLayout
[    21.252] (II) LoadModule: "nvidia"
[    21.252] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    21.252] (II) Module nvidia: vendor="NVIDIA Corporation"
[    21.252]     compiled for 4.0.2, module version = 1.0.0
[    21.252]     Module class: X.Org Video Driver
[    21.252] (II) LoadModule: "nouveau"
[    21.252] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    21.252] (II) Module nouveau: vendor="X.Org Foundation"
[    21.252]     compiled for 1.13.0, module version = 1.0.2
[    21.252]     Module class: X.Org Video Driver
[    21.252]     ABI class: X.Org Video Driver, version 13.0
[    21.252] (II) LoadModule: "nv"
[    21.269] (WW) Warning, couldn't open module nv
[    21.269] (II) UnloadModule: "nv"
[    21.269] (II) Unloading nv
[    21.269] (EE) Failed to load module "nv" (module does not exist, 0)
[    21.269] (II) LoadModule: "vesa"
[    21.269] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.269] (II) Module vesa: vendor="X.Org Foundation"
[    21.269]     compiled for 1.13.0, module version = 2.3.2
[    21.269]     Module class: X.Org Video Driver
[    21.269]     ABI class: X.Org Video Driver, version 13.0
[    21.269] (II) LoadModule: "modesetting"
[    21.270] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    21.270] (II) Module modesetting: vendor="X.Org Foundation"
[    21.270]     compiled for 1.13.0, module version = 0.5.0
[    21.270]     Module class: X.Org Video Driver
[    21.270]     ABI class: X.Org Video Driver, version 13.0
[    21.270] (II) LoadModule: "fbdev"
[    21.270] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.270] (II) Module fbdev: vendor="X.Org Foundation"
[    21.270]     compiled for 1.13.0, module version = 0.4.3
[    21.270]     Module class: X.Org Video Driver
[    21.270]     ABI class: X.Org Video Driver, version 13.0
[    21.270] (==) Matched nvidia as autoconfigured driver 0
[    21.270] (==) Matched nouveau as autoconfigured driver 1
[    21.270] (==) Matched nv as autoconfigured driver 2
[    21.270] (==) Matched vesa as autoconfigured driver 3
[    21.270] (==) Matched modesetting as autoconfigured driver 4
[    21.270] (==) Matched fbdev as autoconfigured driver 5
[    21.270] (==) Assigned the driver to the xf86ConfigLayout
[    21.270] (II) LoadModule: "nvidia"
[    21.270] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    21.270] (II) Module nvidia: vendor="NVIDIA Corporation"
[    21.270]     compiled for 4.0.2, module version = 1.0.0
[    21.270]     Module class: X.Org Video Driver
[    21.270] (II) UnloadModule: "nvidia"
[    21.270] (II) Unloading nvidia
[    21.270] (II) Failed to load module "nvidia" (already loaded, -1217002558)
[    21.270] (II) LoadModule: "nouveau"
[    21.270] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    21.270] (II) Module nouveau: vendor="X.Org Foundation"
[    21.270]     compiled for 1.13.0, module version = 1.0.2
[    21.270]     Module class: X.Org Video Driver
[    21.270]     ABI class: X.Org Video Driver, version 13.0
[    21.270] (II) UnloadModule: "nouveau"
[    21.270] (II) Unloading nouveau
[    21.270] (II) Failed to load module "nouveau" (already loaded, -1217002558)
[    21.270] (II) LoadModule: "nv"
[    21.270] (WW) Warning, couldn't open module nv
[    21.270] (II) UnloadModule: "nv"
[    21.270] (II) Unloading nv
[    21.270] (EE) Failed to load module "nv" (module does not exist, 0)
[    21.270] (II) LoadModule: "vesa"
[    21.271] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.271] (II) Module vesa: vendor="X.Org Foundation"
[    21.271]     compiled for 1.13.0, module version = 2.3.2
[    21.271]     Module class: X.Org Video Driver
[    21.271]     ABI class: X.Org Video Driver, version 13.0
[    21.271] (II) UnloadModule: "vesa"
[    21.271] (II) Unloading vesa
[    21.271] (II) Failed to load module "vesa" (already loaded, 0)
[    21.271] (II) LoadModule: "modesetting"
[    21.271] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    21.271] (II) Module modesetting: vendor="X.Org Foundation"
[    21.271]     compiled for 1.13.0, module version = 0.5.0
[    21.271]     Module class: X.Org Video Driver
[    21.271]     ABI class: X.Org Video Driver, version 13.0
[    21.271] (II) UnloadModule: "modesetting"
[    21.271] (II) Unloading modesetting
[    21.271] (II) Failed to load module "modesetting" (already loaded, 0)
[    21.271] (II) LoadModule: "fbdev"
[    21.271] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.271] (II) Module fbdev: vendor="X.Org Foundation"
[    21.271]     compiled for 1.13.0, module version = 0.4.3
[    21.271]     Module class: X.Org Video Driver
[    21.271]     ABI class: X.Org Video Driver, version 13.0
[    21.271] (II) UnloadModule: "fbdev"
[    21.271] (II) Unloading fbdev
[    21.271] (II) Failed to load module "fbdev" (already loaded, 0)
[    21.271] (II) NVIDIA dlloader X Driver  319.32  Wed Jun 19 13:52:27 PDT 2013
[    21.271] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    21.271] (II) NOUVEAU driver Date:   Wed Sep 12 13:42:43 2012 +0200
[    21.271] (II) NOUVEAU driver for NVIDIA chipset families :
[    21.271]     RIVA TNT        (NV04)
[    21.271]     RIVA TNT2       (NV05)
[    21.271]     GeForce 256     (NV10)
[    21.271]     GeForce 2       (NV11, NV15)
[    21.271]     GeForce 4MX     (NV17, NV18)
[    21.271]     GeForce 3       (NV20)
[    21.271]     GeForce 4Ti     (NV25, NV28)
[    21.271]     GeForce FX      (NV3x)
[    21.271]     GeForce 6       (NV4x)
[    21.271]     GeForce 7       (G7x)
[    21.271]     GeForce 8       (G8x)
[    21.271]     GeForce GTX 200 (NVA0)
[    21.271]     GeForce GTX 400 (NVC0)
[    21.271] (II) VESA: driver for VESA chipsets: vesa
[    21.271] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    21.271] (II) FBDEV: driver for framebuffer: fbdev
[    21.271] (++) using VT number 7


[    21.273] (II) Loading sub module "fb"
[    21.273] (II) LoadModule: "fb"
[    21.273] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.273] (II) Module fb: vendor="X.Org Foundation"
[    21.273]     compiled for 1.13.0, module version = 1.0.0
[    21.273]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.273] (WW) Unresolved symbol: fbGetGCPrivateKey
[    21.273] (II) Loading sub module "wfb"
[    21.273] (II) LoadModule: "wfb"
[    21.273] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.274] (II) Module wfb: vendor="X.Org Foundation"
[    21.274]     compiled for 1.13.0, module version = 1.0.0
[    21.274]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.274] (II) Loading sub module "shadow"
[    21.274] (II) LoadModule: "shadow"
[    21.274] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    21.274] (II) Module shadow: vendor="X.Org Foundation"
[    21.274]     compiled for 1.13.0, module version = 1.1.0
[    21.274]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.274] (II) Loading sub module "ramdac"
[    21.274] (II) LoadModule: "ramdac"
[    21.274] (II) Module "ramdac" already built-in
[    21.274] (WW) Falling back to old probe method for vesa
[    21.274] (WW) Falling back to old probe method for modesetting
[    21.274] (EE) open /dev/dri/card0: No such file or directory
[    21.274] (EE) open /dev/dri/card0: No such file or directory
[    21.274] (WW) Falling back to old probe method for fbdev
[    21.274] (II) Loading sub module "fbdevhw"
[    21.274] (II) LoadModule: "fbdevhw"
[    21.274] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.274] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.274]     compiled for 1.13.0, module version = 0.0.2
[    21.274]     ABI class: X.Org Video Driver, version 13.0
[    21.274] (EE) open /dev/fb0: No such file or directory
[    21.274] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    21.274] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    21.274] (==) NVIDIA(0): RGB weight 888
[    21.274] (==) NVIDIA(0): Default visual is TrueColor
[    21.274] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.274] (**) NVIDIA(0): Option "NoLogo" "True"
[    21.274] (**) NVIDIA(0): Enabling 2D acceleration
[    21.280] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[    21.280] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[    21.280] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[    21.280] (EE) NVIDIA(0):  *** Aborting ***
[    21.280] (EE) NVIDIA(0): Failing initialization of X screen 0
[    21.280] (II) UnloadModule: "nvidia"
[    21.280] (II) UnloadSubModule: "shadow"
[    21.280] (II) UnloadSubModule: "wfb"
[    21.280] (II) UnloadSubModule: "fb"
[    21.280] (EE) Screen(s) found, but none have a usable configuration.
[    21.280] 
Fatal server error:
[    21.280] no screens found
[    21.280] (EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    21.280] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    21.280] (EE) 
[    21.281] Server terminated with error (1). Closing log file.

```

---

### Post by nwordz on 2013-12-16
Testing out how much text will fit in a code block...
Seems like it worked, this is the syslog
```
Nov 18 22:19:35 zack-A880G rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="659" x-info="http://www.rsyslog.com"] rsyslogd was HUPedNov 18 22:22:45 zack-A880G anacron[949]: Job `cron.daily' terminated
Nov 18 22:22:45 zack-A880G anacron[949]: Job `cron.weekly' started
Nov 18 22:22:45 zack-A880G anacron[1868]: Updated timestamp for job `cron.weekly' to 2013-11-18
Nov 18 22:22:55 zack-A880G anacron[949]: Job `cron.weekly' terminated
Nov 18 22:22:55 zack-A880G anacron[949]: Normal exit (2 jobs run)
Nov 18 22:28:05 zack-A880G acpid: client 1153[0:0] has disconnected
Nov 18 22:28:05 zack-A880G dbus[595]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Nov 18 22:28:05 zack-A880G dbus[595]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Nov 18 22:28:05 zack-A880G kernel: Kernel logging (proc) stopped.
Nov 18 22:28:05 zack-A880G rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="659" x-info="http://www.rsyslog.com"] exiting on signal 15.
Dec 15 15:10:48 zack-A880G kernel: imklog 5.8.6, log source = /proc/kmsg started.
Dec 15 15:10:48 zack-A880G rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="691" x-info="http://www.rsyslog.com"] start
Dec 15 15:10:48 zack-A880G rsyslogd: rsyslogd's groupid changed to 103
Dec 15 15:10:48 zack-A880G rsyslogd: rsyslogd's userid changed to 101
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Linux version 3.5.0-43-generic (buildd@akateko) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #66~precise1-Ubuntu SMP Thu Oct 24 14:55:08 UTC 2013 (Ubuntu 3.5.0-43.66~precise1-generic 3.5.7.23)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] KERNEL supported cpus:
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   Intel GenuineIntel
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   AMD AuthenticAMD
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   NSC Geode by NSC
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   Cyrix CyrixInstead
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   Centaur CentaurHauls
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   Transmeta GenuineTMx86
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   Transmeta TransmetaCPU
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   UMC UMC UMC UMC
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ffaffff] usable
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x000000007ffb0000-0x000000007ffbdfff] ACPI data
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x000000007ffbe000-0x000000007ffdffff] ACPI NVS
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x000000007ffe0000-0x000000007fffffff] reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] SMBIOS 2.6 present.
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] DMI: BIOSTAR Group A880G+/A880G+, BIOS 080016  08/30/2010
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] e820: last_pfn = 0x7ffb0 max_arch_pfn = 0x1000000
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] MTRR default type: uncachable
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   00000-9FFFF write-back
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   A0000-EFFFF uncachable
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   F0000-FFFFF write-protect
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] MTRR variable ranges enabled:
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   1 disabled
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   2 disabled
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   3 disabled
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   4 disabled
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   5 disabled
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   6 disabled
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   7 disabled
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [c00ff780]
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]  [mem 0x00000000-0x001fffff] page 4k
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]  [mem 0x00200000-0x379fffff] page 2M
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] RAMDISK: [mem 0x36244000-0x37119fff]
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: RSDP 000faf80 00014 (v00 ACPIAM)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: RSDT 7ffb0000 00044 (v01 083010 RSDT1638 20100830 MSFT 00000097)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: FACP 7ffb0200 00084 (v01 083010 FACP1638 20100830 MSFT 00000097)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20120320/tbfadt-579)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: DSDT 7ffb0450 0A1DA (v01  88PCP 88PCP830 00000002 INTL 20051117)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: FACS 7ffbe000 00040
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: APIC 7ffb0390 0007C (v01 083010 APIC1638 20100830 MSFT 00000097)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: MCFG 7ffb0410 0003C (v01 083010 OEMMCFG  20100830 MSFT 00000097)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: OEMB 7ffbe040 00072 (v01 083010 OEMB1638 20100830 MSFT 00000097)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: SRAT 7ffba630 00090 (v03 AMD    FAM_F_10 00000002 AMD  00000001)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: MSCT 7ffba6c0 0004E (v01 A M I  OEMBOARD 00000001 AMD  00000001)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: HPET 7ffba710 00038 (v01 083010 OEMHPET  20100830 MSFT 00000097)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: SSDT 7ffba750 0023E (v01 A M I  POWERNOW 00000001 AMD  00000001)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] 1155MB HIGHMEM available.
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] 891MB LOWMEM available.
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   low ram: 0 - 37bfe000
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Zone ranges:
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   HighMem  [mem 0x37bfe000-0x7ffaffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Movable zone start for each node
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Early memory node ranges
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   node   0: [mem 0x00010000-0x0009efff]
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   node   0: [mem 0x00100000-0x7ffaffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] On node 0 totalpages: 524095
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] free_area_init_node: node 0, pgdat c18c85c0, node_mem_map f5244200
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   HighMem zone: 2312 pages used for memmap
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]   HighMem zone: 293546 pages, LIFO batch:31
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Using APIC driver default
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] SMP: Allowing 6 CPUs, 5 hotplug CPUs
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] nr_irqs_gsi: 40
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] e820: [mem 0x80000000-0xffefffff] available for PCI devices
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:6 nr_node_ids:1
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f7b9d000 s34176 r0 d23168 u57344
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] pcpu-alloc: s34176 r0 d23168 u57344 alloc=14*4096
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 [0] 4 [0] 5 
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519999
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-43-generic root=UUID=a5baa10f-bb69-49cc-998b-f6e8c4f55e7d ro quiet splash
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] __ex_table already sorted, skipping sort
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Initializing CPU#0
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] allocated 4193536 bytes of page_cgroup
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:0007ffb0)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Memory: 2048744k/2096832k available (6059k kernel code, 47636k reserved, 2985k data, 764k init, 1183432k highmem)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] virtual kernel memory layout:
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]       .init : 0xc18d6000 - 0xc1995000   ( 764 kB)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]       .data : 0xc15eaf15 - 0xc18d54c0   (2985 kB)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]       .text : 0xc1000000 - 0xc15eaf15   (6059 kB)
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Hierarchical RCU implementation.
Dec 15 15:10:48 zack-A880G kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] NR_IRQS:2304 nr_irqs:728 16
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] CPU 0 irqstacks, hard=f4c0a000 soft=f4c0c000
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] Console: colour VGA+ 80x25
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] console [tty0] enabled
Dec 15 15:10:48 zack-A880G kernel: [    0.000000] hpet clockevent registered
Dec 15 15:10:48 zack-A880G kernel: [    0.004000] Fast TSC calibration using PIT
Dec 15 15:10:48 zack-A880G kernel: [    0.008000] Detected 2800.308 MHz processor.
Dec 15 15:10:48 zack-A880G kernel: [    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 5600.61 BogoMIPS (lpj=11201232)
Dec 15 15:10:48 zack-A880G kernel: [    0.000004] pid_max: default: 32768 minimum: 301
Dec 15 15:10:48 zack-A880G kernel: [    0.000024] Security Framework initialized
Dec 15 15:10:48 zack-A880G kernel: [    0.000038] AppArmor: AppArmor initialized
Dec 15 15:10:48 zack-A880G kernel: [    0.000039] Yama: becoming mindful.
Dec 15 15:10:48 zack-A880G kernel: [    0.000085] Mount-cache hash table entries: 512
Dec 15 15:10:48 zack-A880G kernel: [    0.000253] Initializing cgroup subsys cpuacct
Dec 15 15:10:48 zack-A880G kernel: [    0.000256] Initializing cgroup subsys memory
Dec 15 15:10:48 zack-A880G kernel: [    0.000262] Initializing cgroup subsys devices
Dec 15 15:10:48 zack-A880G kernel: [    0.000263] Initializing cgroup subsys freezer
Dec 15 15:10:48 zack-A880G kernel: [    0.000265] Initializing cgroup subsys blkio
Dec 15 15:10:48 zack-A880G kernel: [    0.000267] Initializing cgroup subsys perf_event
Dec 15 15:10:48 zack-A880G kernel: [    0.000287] mce: CPU supports 6 MCE banks
Dec 15 15:10:48 zack-A880G kernel: [    0.000292] LVT offset 0 assigned for vector 0xf9
Dec 15 15:10:48 zack-A880G kernel: [    0.000471] SMP alternatives: switching to UP code
Dec 15 15:10:48 zack-A880G kernel: [    0.007113] ACPI: Core revision 20120320
Dec 15 15:10:48 zack-A880G kernel: [    0.018092] ftrace: allocating 27161 entries in 54 pages
Dec 15 15:10:48 zack-A880G kernel: [    0.027366] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 15 15:10:48 zack-A880G kernel: [    0.027713] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 15 15:10:48 zack-A880G kernel: [    0.067325] CPU0: AMD Sempron(tm) 145 Processor stepping 03
Dec 15 15:10:48 zack-A880G kernel: [    0.174832] Performance Events: AMD PMU driver.
Dec 15 15:10:48 zack-A880G kernel: [    0.174836] ... version:                0
Dec 15 15:10:48 zack-A880G kernel: [    0.174837] ... bit width:              48
Dec 15 15:10:48 zack-A880G kernel: [    0.174838] ... generic registers:      4
Dec 15 15:10:48 zack-A880G kernel: [    0.174839] ... value mask:             0000ffffffffffff
Dec 15 15:10:48 zack-A880G kernel: [    0.174840] ... max period:             00007fffffffffff
Dec 15 15:10:48 zack-A880G kernel: [    0.174841] ... fixed-purpose events:   0
Dec 15 15:10:48 zack-A880G kernel: [    0.174842] ... event mask:             000000000000000f
Dec 15 15:10:48 zack-A880G kernel: [    0.174977] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Dec 15 15:10:48 zack-A880G kernel: [    0.175021] Brought up 1 CPUs
Dec 15 15:10:48 zack-A880G kernel: [    0.175023] Total of 1 processors activated (5600.61 BogoMIPS).
Dec 15 15:10:48 zack-A880G kernel: [    0.175467] devtmpfs: initialized
Dec 15 15:10:48 zack-A880G kernel: [    0.175586] EVM: security.selinux
Dec 15 15:10:48 zack-A880G kernel: [    0.175587] EVM: security.SMACK64
Dec 15 15:10:48 zack-A880G kernel: [    0.175588] EVM: security.capability
Dec 15 15:10:48 zack-A880G kernel: [    0.175629] PM: Registering ACPI NVS region [mem 0x7ffbe000-0x7ffdffff] (139264 bytes)
Dec 15 15:10:48 zack-A880G kernel: [    0.176388] dummy: 
Dec 15 15:10:48 zack-A880G kernel: [    0.176416] RTC time: 23:10:31, date: 12/15/13
Dec 15 15:10:48 zack-A880G kernel: [    0.176446] NET: Registered protocol family 16
Dec 15 15:10:48 zack-A880G kernel: [    0.176528] EISA bus registered
Dec 15 15:10:48 zack-A880G kernel: [    0.176531] node 0 link 0: io port [1000, ffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.176535] TOM: 0000000080000000 aka 2048M
Dec 15 15:10:48 zack-A880G kernel: [    0.176537] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.176539] node 0 link 0: mmio [a0000, bffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.176541] node 0 link 0: mmio [80000000, dfffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.176543] node 0 link 0: mmio [e0000000, efffffff] ==> none
Dec 15 15:10:48 zack-A880G kernel: [    0.176545] node 0 link 0: mmio [f0000000, ffefffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.176546] bus: [00, 07] on node 0 link 0
Dec 15 15:10:48 zack-A880G kernel: [    0.176548] bus: 00 [io  0x0000-0xffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.176549] bus: 00 [mem 0x000a0000-0x000bffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.176551] bus: 00 [mem 0x80000000-0xdfffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.176552] bus: 00 [mem 0xf0000000-0xfcffffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.176603] ACPI: bus type pci registered
Dec 15 15:10:48 zack-A880G kernel: [    0.176643] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Dec 15 15:10:48 zack-A880G kernel: [    0.176644] PCI: not using MMCONFIG
Dec 15 15:10:48 zack-A880G kernel: [    0.177222] PCI : PCI BIOS area is rw and x. Use pci=nobios if you want it NX.
Dec 15 15:10:48 zack-A880G kernel: [    0.177290] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
Dec 15 15:10:48 zack-A880G kernel: [    0.177291] PCI: Using configuration type 1 for base access
Dec 15 15:10:48 zack-A880G kernel: [    0.177292] PCI: Using configuration type 1 for extended access
Dec 15 15:10:48 zack-A880G kernel: [    0.177914] bio: create slab <bio-0> at 0
Dec 15 15:10:48 zack-A880G kernel: [    0.177976] ACPI: Added _OSI(Module Device)
Dec 15 15:10:48 zack-A880G kernel: [    0.177978] ACPI: Added _OSI(Processor Device)
Dec 15 15:10:48 zack-A880G kernel: [    0.177979] ACPI: Added _OSI(3.0 _SCP Extensions)
Dec 15 15:10:48 zack-A880G kernel: [    0.177980] ACPI: Added _OSI(Processor Aggregator Device)
Dec 15 15:10:48 zack-A880G kernel: [    0.178548] ACPI: EC: Look up EC in DSDT
Dec 15 15:10:48 zack-A880G kernel: [    0.179758] ACPI: Executed 4 blocks of module-level executable AML code
Dec 15 15:10:48 zack-A880G kernel: [    0.182622] ACPI: Interpreter enabled
Dec 15 15:10:48 zack-A880G kernel: [    0.182627] ACPI: (supports S0 S1 S4 S5)
Dec 15 15:10:48 zack-A880G kernel: [    0.182642] ACPI: Using IOAPIC for interrupt routing
Dec 15 15:10:48 zack-A880G kernel: [    0.182658] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Dec 15 15:10:48 zack-A880G kernel: [    0.183877] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Dec 15 15:10:48 zack-A880G kernel: [    0.183878] PCI: Using MMCONFIG for extended config space
Dec 15 15:10:48 zack-A880G kernel: [    0.188441] ACPI: No dock devices found.
Dec 15 15:10:48 zack-A880G kernel: [    0.188445] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Dec 15 15:10:48 zack-A880G kernel: [    0.188507] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Dec 15 15:10:48 zack-A880G kernel: [    0.188612] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Dec 15 15:10:48 zack-A880G kernel: [    0.188614] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.188616] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.188618] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.188620] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xdfffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.188622] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.188645] PCI host bridge to bus 0000:00
Dec 15 15:10:48 zack-A880G kernel: [    0.188647] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Dec 15 15:10:48 zack-A880G kernel: [    0.188649] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.188651] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.188653] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.188655] pci_bus 0000:00: root bus resource [mem 0x80000000-0xdfffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.188657] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.188667] pci 0000:00:00.0: [1022:9601] type 00 class 0x060000
Dec 15 15:10:48 zack-A880G kernel: [    0.188711] pci 0000:00:02.0: [1022:9603] type 01 class 0x060400
Dec 15 15:10:48 zack-A880G kernel: [    0.188741] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Dec 15 15:10:48 zack-A880G kernel: [    0.188757] pci 0000:00:07.0: [1022:9607] type 01 class 0x060400
Dec 15 15:10:48 zack-A880G kernel: [    0.188786] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Dec 15 15:10:48 zack-A880G kernel: [    0.188826] pci 0000:00:11.0: [1002:4390] type 00 class 0x01018f
Dec 15 15:10:48 zack-A880G kernel: [    0.188844] pci 0000:00:11.0: reg 10: [io  0xb000-0xb007]
Dec 15 15:10:48 zack-A880G kernel: [    0.188854] pci 0000:00:11.0: reg 14: [io  0xa000-0xa003]
Dec 15 15:10:48 zack-A880G kernel: [    0.188863] pci 0000:00:11.0: reg 18: [io  0x9000-0x9007]
Dec 15 15:10:48 zack-A880G kernel: [    0.188872] pci 0000:00:11.0: reg 1c: [io  0x8000-0x8003]
Dec 15 15:10:48 zack-A880G kernel: [    0.188881] pci 0000:00:11.0: reg 20: [io  0x7000-0x700f]
Dec 15 15:10:48 zack-A880G kernel: [    0.188890] pci 0000:00:11.0: reg 24: [mem 0xfeaffc00-0xfeafffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.188909] pci 0000:00:11.0: set SATA to AHCI mode
Dec 15 15:10:48 zack-A880G kernel: [    0.188953] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
Dec 15 15:10:48 zack-A880G kernel: [    0.188966] pci 0000:00:12.0: reg 10: [mem 0xfeafe000-0xfeafefff]
Dec 15 15:10:48 zack-A880G kernel: [    0.189027] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
Dec 15 15:10:48 zack-A880G kernel: [    0.189039] pci 0000:00:12.1: reg 10: [mem 0xfeafd000-0xfeafdfff]
Dec 15 15:10:48 zack-A880G kernel: [    0.189106] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
Dec 15 15:10:48 zack-A880G kernel: [    0.189124] pci 0000:00:12.2: reg 10: [mem 0xfeaff800-0xfeaff8ff]
Dec 15 15:10:48 zack-A880G kernel: [    0.189203] pci 0000:00:12.2: supports D1 D2
Dec 15 15:10:48 zack-A880G kernel: [    0.189205] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Dec 15 15:10:48 zack-A880G kernel: [    0.189226] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
Dec 15 15:10:48 zack-A880G kernel: [    0.189239] pci 0000:00:13.0: reg 10: [mem 0xfeafc000-0xfeafcfff]
Dec 15 15:10:48 zack-A880G kernel: [    0.189300] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
Dec 15 15:10:48 zack-A880G kernel: [    0.189313] pci 0000:00:13.1: reg 10: [mem 0xfeafb000-0xfeafbfff]
Dec 15 15:10:48 zack-A880G kernel: [    0.189379] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
Dec 15 15:10:48 zack-A880G kernel: [    0.189398] pci 0000:00:13.2: reg 10: [mem 0xfeaff400-0xfeaff4ff]
Dec 15 15:10:48 zack-A880G kernel: [    0.189477] pci 0000:00:13.2: supports D1 D2
Dec 15 15:10:48 zack-A880G kernel: [    0.189478] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Dec 15 15:10:48 zack-A880G kernel: [    0.189503] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
Dec 15 15:10:48 zack-A880G kernel: [    0.189597] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
Dec 15 15:10:48 zack-A880G kernel: [    0.189613] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Dec 15 15:10:48 zack-A880G kernel: [    0.189622] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Dec 15 15:10:48 zack-A880G kernel: [    0.189631] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Dec 15 15:10:48 zack-A880G kernel: [    0.189640] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Dec 15 15:10:48 zack-A880G kernel: [    0.189649] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
Dec 15 15:10:48 zack-A880G kernel: [    0.189707] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
Dec 15 15:10:48 zack-A880G kernel: [    0.189727] pci 0000:00:14.2: reg 10: [mem 0xfeaf4000-0xfeaf7fff 64bit]
Dec 15 15:10:48 zack-A880G kernel: [    0.189791] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Dec 15 15:10:48 zack-A880G kernel: [    0.189806] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
Dec 15 15:10:48 zack-A880G kernel: [    0.189878] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
Dec 15 15:10:48 zack-A880G kernel: [    0.189918] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
Dec 15 15:10:48 zack-A880G kernel: [    0.189931] pci 0000:00:14.5: reg 10: [mem 0xfeafa000-0xfeafafff]
Dec 15 15:10:48 zack-A880G kernel: [    0.189994] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
Dec 15 15:10:48 zack-A880G kernel: [    0.190008] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
Dec 15 15:10:48 zack-A880G kernel: [    0.190018] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
Dec 15 15:10:48 zack-A880G kernel: [    0.190030] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
Dec 15 15:10:48 zack-A880G kernel: [    0.190043] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
Dec 15 15:10:48 zack-A880G kernel: [    0.190088] pci 0000:01:00.0: [10de:0de1] type 00 class 0x030000
Dec 15 15:10:48 zack-A880G kernel: [    0.190097] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.190107] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
Dec 15 15:10:48 zack-A880G kernel: [    0.190117] pci 0000:01:00.0: reg 1c: [mem 0xd6000000-0xd7ffffff 64bit pref]
Dec 15 15:10:48 zack-A880G kernel: [    0.190124] pci 0000:01:00.0: reg 24: [io  0xc800-0xc87f]
Dec 15 15:10:48 zack-A880G kernel: [    0.190131] pci 0000:01:00.0: reg 30: [mem 0xfcf80000-0xfcffffff pref]
Dec 15 15:10:48 zack-A880G kernel: [    0.190182] pci 0000:01:00.1: [10de:0bea] type 00 class 0x040300
Dec 15 15:10:48 zack-A880G kernel: [    0.190192] pci 0000:01:00.1: reg 10: [mem 0xfcf7c000-0xfcf7ffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.194831] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Dec 15 15:10:48 zack-A880G kernel: [    0.194837] pci 0000:00:02.0:   bridge window [io  0xc000-0xcfff]
Dec 15 15:10:48 zack-A880G kernel: [    0.194840] pci 0000:00:02.0:   bridge window [mem 0xfcf00000-0xfdffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.194844] pci 0000:00:02.0:   bridge window [mem 0xd6000000-0xdfffffff 64bit pref]
Dec 15 15:10:48 zack-A880G kernel: [    0.194881] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
Dec 15 15:10:48 zack-A880G kernel: [    0.194895] pci 0000:02:00.0: reg 10: [io  0xd800-0xd8ff]
Dec 15 15:10:48 zack-A880G kernel: [    0.194915] pci 0000:02:00.0: reg 18: [mem 0xfbffb000-0xfbffbfff 64bit pref]
Dec 15 15:10:48 zack-A880G kernel: [    0.194928] pci 0000:02:00.0: reg 20: [mem 0xfbffc000-0xfbffffff 64bit pref]
Dec 15 15:10:48 zack-A880G kernel: [    0.194936] pci 0000:02:00.0: reg 30: [mem 0xfebe0000-0xfebfffff pref]
Dec 15 15:10:48 zack-A880G kernel: [    0.194983] pci 0000:02:00.0: supports D1 D2
Dec 15 15:10:48 zack-A880G kernel: [    0.194985] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 15 15:10:48 zack-A880G kernel: [    0.202814] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Dec 15 15:10:48 zack-A880G kernel: [    0.202821] pci 0000:00:07.0:   bridge window [io  0xd000-0xdfff]
Dec 15 15:10:48 zack-A880G kernel: [    0.202824] pci 0000:00:07.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.202827] pci 0000:00:07.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
Dec 15 15:10:48 zack-A880G kernel: [    0.202867] pci 0000:03:06.0: [1274:1371] type 00 class 0x040100
Dec 15 15:10:48 zack-A880G kernel: [    0.202888] pci 0000:03:06.0: reg 10: [io  0xe800-0xe83f]
Dec 15 15:10:48 zack-A880G kernel: [    0.202986] pci 0000:03:06.0: supports D2
Dec 15 15:10:48 zack-A880G kernel: [    0.202987] pci 0000:03:06.0: PME# supported from D0 D2 D3hot
Dec 15 15:10:48 zack-A880G kernel: [    0.203035] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
Dec 15 15:10:48 zack-A880G kernel: [    0.203038] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
Dec 15 15:10:48 zack-A880G kernel: [    0.203045] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Dec 15 15:10:48 zack-A880G kernel: [    0.203047] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Dec 15 15:10:48 zack-A880G kernel: [    0.203048] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Dec 15 15:10:48 zack-A880G kernel: [    0.203050] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
Dec 15 15:10:48 zack-A880G kernel: [    0.203052] pci 0000:00:14.4:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
Dec 15 15:10:48 zack-A880G kernel: [    0.203054] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
Dec 15 15:10:48 zack-A880G kernel: [    0.203065] pci_bus 0000:00: on NUMA node 0
Dec 15 15:10:48 zack-A880G kernel: [    0.203070] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 15 15:10:48 zack-A880G kernel: [    0.203246] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Dec 15 15:10:48 zack-A880G kernel: [    0.203273] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Dec 15 15:10:48 zack-A880G kernel: [    0.203310] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
Dec 15 15:10:48 zack-A880G kernel: [    0.203369]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Dec 15 15:10:48 zack-A880G kernel: [    0.203371]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Dec 15 15:10:48 zack-A880G kernel: [    0.203372] ACPI _OSC control for PCIe not granted, disabling ASPM
Dec 15 15:10:48 zack-A880G kernel: [    0.206360] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 12 14 15)
Dec 15 15:10:48 zack-A880G kernel: [    0.206391] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
Dec 15 15:10:48 zack-A880G kernel: [    0.206418] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
Dec 15 15:10:48 zack-A880G kernel: [    0.206445] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
Dec 15 15:10:48 zack-A880G kernel: [    0.206472] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Dec 15 15:10:48 zack-A880G kernel: [    0.206499] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 *10 11 12 14 15)
Dec 15 15:10:48 zack-A880G kernel: [    0.206525] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 *9 12 14 15)
Dec 15 15:10:48 zack-A880G kernel: [    0.206551] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Dec 15 15:10:48 zack-A880G kernel: [    0.206629] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Dec 15 15:10:48 zack-A880G kernel: [    0.206630] vgaarb: loaded
Dec 15 15:10:48 zack-A880G kernel: [    0.206631] vgaarb: bridge control possible 0000:01:00.0
Dec 15 15:10:48 zack-A880G kernel: [    0.206766] SCSI subsystem initialized
Dec 15 15:10:48 zack-A880G kernel: [    0.206800] libata version 3.00 loaded.
Dec 15 15:10:48 zack-A880G kernel: [    0.206814] ACPI: bus type usb registered
Dec 15 15:10:48 zack-A880G kernel: [    0.206829] usbcore: registered new interface driver usbfs
Dec 15 15:10:48 zack-A880G kernel: [    0.206836] usbcore: registered new interface driver hub
Dec 15 15:10:48 zack-A880G kernel: [    0.206850] usbcore: registered new device driver usb
Dec 15 15:10:48 zack-A880G kernel: [    0.206903] PCI: Using ACPI for IRQ routing
Dec 15 15:10:48 zack-A880G kernel: [    0.206906] PCI: pci_cache_line_size set to 64 bytes
Dec 15 15:10:48 zack-A880G kernel: [    0.206972] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.206974] e820: reserve RAM buffer [mem 0x7ffb0000-0x7fffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.207041] NetLabel: Initializing
Dec 15 15:10:48 zack-A880G kernel: [    0.207042] NetLabel:  domain hash size = 128
Dec 15 15:10:48 zack-A880G kernel: [    0.207043] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 15 15:10:48 zack-A880G kernel: [    0.207050] NetLabel:  unlabeled traffic allowed by default
Dec 15 15:10:48 zack-A880G kernel: [    0.207107] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Dec 15 15:10:48 zack-A880G kernel: [    0.207110] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Dec 15 15:10:48 zack-A880G kernel: [    0.209130] Switching to clocksource hpet
Dec 15 15:10:48 zack-A880G kernel: [    0.213734] AppArmor: AppArmor Filesystem Enabled
Dec 15 15:10:48 zack-A880G kernel: [    0.213759] pnp: PnP ACPI init
Dec 15 15:10:48 zack-A880G kernel: [    0.213772] ACPI: bus type pnp registered
Dec 15 15:10:48 zack-A880G kernel: [    0.213871] pnp 00:00: [bus 00-ff]
Dec 15 15:10:48 zack-A880G kernel: [    0.213874] pnp 00:00: [io  0x0cf8-0x0cff]
Dec 15 15:10:48 zack-A880G kernel: [    0.213876] pnp 00:00: [io  0x0000-0x0cf7 window]
Dec 15 15:10:48 zack-A880G kernel: [    0.213878] pnp 00:00: [io  0x0d00-0xffff window]
Dec 15 15:10:48 zack-A880G kernel: [    0.213880] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Dec 15 15:10:48 zack-A880G kernel: [    0.213881] pnp 00:00: [mem 0x000d0000-0x000dffff window]
Dec 15 15:10:48 zack-A880G kernel: [    0.213883] pnp 00:00: [mem 0x80000000-0xdfffffff window]
Dec 15 15:10:48 zack-A880G kernel: [    0.213885] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
Dec 15 15:10:48 zack-A880G kernel: [    0.213923] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Dec 15 15:10:48 zack-A880G kernel: [    0.213996] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Dec 15 15:10:48 zack-A880G kernel: [    0.213998] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Dec 15 15:10:48 zack-A880G kernel: [    0.214036] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 15 15:10:48 zack-A880G kernel: [    0.214069] pnp 00:02: [dma 4]
Dec 15 15:10:48 zack-A880G kernel: [    0.214070] pnp 00:02: [io  0x0000-0x000f]
Dec 15 15:10:48 zack-A880G kernel: [    0.214072] pnp 00:02: [io  0x0081-0x0083]
Dec 15 15:10:48 zack-A880G kernel: [    0.214074] pnp 00:02: [io  0x0087]
Dec 15 15:10:48 zack-A880G kernel: [    0.214075] pnp 00:02: [io  0x0089-0x008b]
Dec 15 15:10:48 zack-A880G kernel: [    0.214077] pnp 00:02: [io  0x008f]
Dec 15 15:10:48 zack-A880G kernel: [    0.214078] pnp 00:02: [io  0x00c0-0x00df]
Dec 15 15:10:48 zack-A880G kernel: [    0.214095] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Dec 15 15:10:48 zack-A880G kernel: [    0.214102] pnp 00:03: [io  0x0070-0x0071]
Dec 15 15:10:48 zack-A880G kernel: [    0.214112] pnp 00:03: [irq 8]
Dec 15 15:10:48 zack-A880G kernel: [    0.214128] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Dec 15 15:10:48 zack-A880G kernel: [    0.214133] pnp 00:04: [io  0x0061]
Dec 15 15:10:48 zack-A880G kernel: [    0.214152] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Dec 15 15:10:48 zack-A880G kernel: [    0.214158] pnp 00:05: [io  0x00f0-0x00ff]
Dec 15 15:10:48 zack-A880G kernel: [    0.214166] pnp 00:05: [irq 13]
Dec 15 15:10:48 zack-A880G kernel: [    0.214182] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Dec 15 15:10:48 zack-A880G kernel: [    0.214571] pnp 00:06: [io  0x03f8-0x03ff]
Dec 15 15:10:48 zack-A880G kernel: [    0.214575] pnp 00:06: [irq 4]
Dec 15 15:10:48 zack-A880G kernel: [    0.214576] pnp 00:06: [dma 0 disabled]
Dec 15 15:10:48 zack-A880G kernel: [    0.214644] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
Dec 15 15:10:48 zack-A880G kernel: [    0.215350] pnp 00:07: [io  0x0378-0x037f]
Dec 15 15:10:48 zack-A880G kernel: [    0.215354] pnp 00:07: [irq 7]
Dec 15 15:10:48 zack-A880G kernel: [    0.215355] pnp 00:07: [dma 0 disabled]
Dec 15 15:10:48 zack-A880G kernel: [    0.215546] pnp 00:07: Plug and Play ACPI device, IDs PNP0400 (active)
Dec 15 15:10:48 zack-A880G kernel: [    0.215725] pnp 00:08: [mem 0xfed00000-0xfed003ff]
Dec 15 15:10:48 zack-A880G kernel: [    0.215744] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (active)
Dec 15 15:10:48 zack-A880G kernel: [    0.215799] pnp 00:09: [io  0x0060]
Dec 15 15:10:48 zack-A880G kernel: [    0.215801] pnp 00:09: [io  0x0064]
Dec 15 15:10:48 zack-A880G kernel: [    0.215802] pnp 00:09: [mem 0xfec00000-0xfec00fff]
Dec 15 15:10:48 zack-A880G kernel: [    0.215804] pnp 00:09: [mem 0xfee00000-0xfee00fff]
Dec 15 15:10:48 zack-A880G kernel: [    0.215834] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.215836] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.215839] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 15 15:10:48 zack-A880G kernel: [    0.215940] pnp 00:0a: [io  0x0010-0x001f]
Dec 15 15:10:48 zack-A880G kernel: [    0.215942] pnp 00:0a: [io  0x0022-0x003f]
Dec 15 15:10:48 zack-A880G kernel: [    0.215943] pnp 00:0a: [io  0x0062-0x0063]
Dec 15 15:10:48 zack-A880G kernel: [    0.215945] pnp 00:0a: [io  0x0065-0x006f]
Dec 15 15:10:48 zack-A880G kernel: [    0.215946] pnp 00:0a: [io  0x0072-0x007f]
Dec 15 15:10:48 zack-A880G kernel: [    0.215948] pnp 00:0a: [io  0x0080]
Dec 15 15:10:48 zack-A880G kernel: [    0.215949] pnp 00:0a: [io  0x0084-0x0086]
Dec 15 15:10:48 zack-A880G kernel: [    0.215951] pnp 00:0a: [io  0x0088]
Dec 15 15:10:48 zack-A880G kernel: [    0.215952] pnp 00:0a: [io  0x008c-0x008e]
Dec 15 15:10:48 zack-A880G kernel: [    0.215954] pnp 00:0a: [io  0x0090-0x009f]
Dec 15 15:10:48 zack-A880G kernel: [    0.215955] pnp 00:0a: [io  0x00a2-0x00bf]
Dec 15 15:10:48 zack-A880G kernel: [    0.215957] pnp 00:0a: [io  0x00b1]
Dec 15 15:10:48 zack-A880G kernel: [    0.215958] pnp 00:0a: [io  0x00e0-0x00ef]
Dec 15 15:10:48 zack-A880G kernel: [    0.215960] pnp 00:0a: [io  0x04d0-0x04d1]
Dec 15 15:10:48 zack-A880G kernel: [    0.215962] pnp 00:0a: [io  0x040b]
Dec 15 15:10:48 zack-A880G kernel: [    0.215963] pnp 00:0a: [io  0x04d6]
Dec 15 15:10:48 zack-A880G kernel: [    0.215965] pnp 00:0a: [io  0x0c00-0x0c01]
Dec 15 15:10:48 zack-A880G kernel: [    0.215966] pnp 00:0a: [io  0x0c14]
Dec 15 15:10:48 zack-A880G kernel: [    0.215968] pnp 00:0a: [io  0x0c50-0x0c51]
Dec 15 15:10:48 zack-A880G kernel: [    0.215969] pnp 00:0a: [io  0x0c52]
Dec 15 15:10:48 zack-A880G kernel: [    0.215971] pnp 00:0a: [io  0x0c6c]
Dec 15 15:10:48 zack-A880G kernel: [    0.215972] pnp 00:0a: [io  0x0c6f]
Dec 15 15:10:48 zack-A880G kernel: [    0.215974] pnp 00:0a: [io  0x0cd0-0x0cd1]
Dec 15 15:10:48 zack-A880G kernel: [    0.215975] pnp 00:0a: [io  0x0cd2-0x0cd3]
Dec 15 15:10:48 zack-A880G kernel: [    0.215977] pnp 00:0a: [io  0x0cd4-0x0cd5]
Dec 15 15:10:48 zack-A880G kernel: [    0.215979] pnp 00:0a: [io  0x0cd6-0x0cd7]
Dec 15 15:10:48 zack-A880G kernel: [    0.215980] pnp 00:0a: [io  0x0cd8-0x0cdf]
Dec 15 15:10:48 zack-A880G kernel: [    0.215982] pnp 00:0a: [io  0x0800-0x089f]
Dec 15 15:10:48 zack-A880G kernel: [    0.215983] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
Dec 15 15:10:48 zack-A880G kernel: [    0.215986] pnp 00:0a: [io  0x0b00-0x0b0f]
Dec 15 15:10:48 zack-A880G kernel: [    0.215988] pnp 00:0a: [io  0x0b20-0x0b3f]
Dec 15 15:10:48 zack-A880G kernel: [    0.215989] pnp 00:0a: [io  0x0900-0x090f]
Dec 15 15:10:48 zack-A880G kernel: [    0.215991] pnp 00:0a: [io  0x0910-0x091f]
Dec 15 15:10:48 zack-A880G kernel: [    0.215992] pnp 00:0a: [io  0xfe00-0xfefe]
Dec 15 15:10:48 zack-A880G kernel: [    0.215994] pnp 00:0a: [io  0x0060]
Dec 15 15:10:48 zack-A880G kernel: [    0.215995] pnp 00:0a: [io  0x0064]
Dec 15 15:10:48 zack-A880G kernel: [    0.215997] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.215999] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
Dec 15 15:10:48 zack-A880G kernel: [    0.216058] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216060] system 00:0a: [io  0x040b] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216062] system 00:0a: [io  0x04d6] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216064] system 00:0a: [io  0x0c00-0x0c01] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216066] system 00:0a: [io  0x0c14] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216068] system 00:0a: [io  0x0c50-0x0c51] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216070] system 00:0a: [io  0x0c52] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216071] system 00:0a: [io  0x0c6c] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216073] system 00:0a: [io  0x0c6f] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216075] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216077] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216079] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216081] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216083] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216085] system 00:0a: [io  0x0800-0x089f] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216087] system 00:0a: [io  0x0b00-0x0b0f] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216089] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216091] system 00:0a: [io  0x0900-0x090f] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216093] system 00:0a: [io  0x0910-0x091f] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216095] system 00:0a: [io  0xfe00-0xfefe] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216098] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216100] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216102] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 15 15:10:48 zack-A880G kernel: [    0.216224] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
Dec 15 15:10:48 zack-A880G kernel: [    0.216226] pnp 00:0b: [io  0x0e00-0x0e0f]
Dec 15 15:10:48 zack-A880G kernel: [    0.216227] pnp 00:0b: [io  0x0e80-0x0e8f]
Dec 15 15:10:48 zack-A880G kernel: [    0.216229] pnp 00:0b: [io  0x0f40-0x0f4f]
Dec 15 15:10:48 zack-A880G kernel: [    0.216230] pnp 00:0b: [io  0x0a30-0x0a3f]
Dec 15 15:10:48 zack-A880G kernel: [    0.216261] system 00:0b: [io  0x0e00-0x0e0f] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216263] system 00:0b: [io  0x0e80-0x0e8f] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216265] system 00:0b: [io  0x0f40-0x0f4f] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216267] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216270] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 15 15:10:48 zack-A880G kernel: [    0.216292] pnp 00:0c: [mem 0xe0000000-0xefffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.216320] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216322] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 15 15:10:48 zack-A880G kernel: [    0.216516] pnp 00:0d: [mem 0x00000000-0x0009ffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.216518] pnp 00:0d: [mem 0x000c0000-0x000cffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.216519] pnp 00:0d: [mem 0x000e0000-0x000fffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.216521] pnp 00:0d: [mem 0x00100000-0x7fffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.216523] pnp 00:0d: [mem 0xfec00000-0xffffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.216557] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216559] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216561] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216563] system 00:0d: [mem 0x00100000-0x7fffffff] could not be reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216565] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
Dec 15 15:10:48 zack-A880G kernel: [    0.216567] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
Dec 15 15:10:48 zack-A880G kernel: [    0.216643] pnp: PnP ACPI: found 14 devices
Dec 15 15:10:48 zack-A880G kernel: [    0.216644] ACPI: ACPI bus type pnp unregistered
Dec 15 15:10:48 zack-A880G kernel: [    0.216646] PnPBIOS: Disabled by ACPI PNP
Dec 15 15:10:48 zack-A880G kernel: [    0.252123] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Dec 15 15:10:48 zack-A880G kernel: [    0.252126] pci 0000:00:02.0:   bridge window [io  0xc000-0xcfff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252129] pci 0000:00:02.0:   bridge window [mem 0xfcf00000-0xfdffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252132] pci 0000:00:02.0:   bridge window [mem 0xd6000000-0xdfffffff 64bit pref]
Dec 15 15:10:48 zack-A880G kernel: [    0.252135] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Dec 15 15:10:48 zack-A880G kernel: [    0.252137] pci 0000:00:07.0:   bridge window [io  0xd000-0xdfff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252140] pci 0000:00:07.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252142] pci 0000:00:07.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
Dec 15 15:10:48 zack-A880G kernel: [    0.252146] pci 0000:00:14.4: PCI bridge to [bus 03-03]
Dec 15 15:10:48 zack-A880G kernel: [    0.252148] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252177] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Dec 15 15:10:48 zack-A880G kernel: [    0.252179] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252181] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252183] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252185] pci_bus 0000:00: resource 8 [mem 0x80000000-0xdfffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252187] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252189] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252191] pci_bus 0000:01: resource 1 [mem 0xfcf00000-0xfdffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252193] pci_bus 0000:01: resource 2 [mem 0xd6000000-0xdfffffff 64bit pref]
Dec 15 15:10:48 zack-A880G kernel: [    0.252194] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252196] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252198] pci_bus 0000:02: resource 2 [mem 0xfbf00000-0xfbffffff 64bit pref]
Dec 15 15:10:48 zack-A880G kernel: [    0.252200] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252202] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
Dec 15 15:10:48 zack-A880G kernel: [    0.252204] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252206] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252208] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252209] pci_bus 0000:03: resource 8 [mem 0x80000000-0xdfffffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252211] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
Dec 15 15:10:48 zack-A880G kernel: [    0.252238] NET: Registered protocol family 2
Dec 15 15:10:48 zack-A880G kernel: [    0.252283] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 15 15:10:48 zack-A880G kernel: [    0.252391] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 15 15:10:48 zack-A880G kernel: [    0.252822] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 15 15:10:48 zack-A880G kernel: [    0.253075] TCP: Hash tables configured (established 131072 bind 65536)
Dec 15 15:10:48 zack-A880G kernel: [    0.253077] TCP: reno registered
Dec 15 15:10:48 zack-A880G kernel: [    0.253079] UDP hash table entries: 512 (order: 2, 16384 bytes)
Dec 15 15:10:48 zack-A880G kernel: [    0.253087] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Dec 15 15:10:48 zack-A880G kernel: [    0.253151] NET: Registered protocol family 1
Dec 15 15:10:48 zack-A880G kernel: [    1.279164] pci 0000:01:00.0: Boot video device
Dec 15 15:10:48 zack-A880G kernel: [    1.279180] PCI: CLS 64 bytes, default 64
Dec 15 15:10:48 zack-A880G kernel: [    1.279345] LVT offset 1 assigned for vector 0x400
Dec 15 15:10:48 zack-A880G kernel: [    1.279351] IBS: LVT offset 1 assigned
Dec 15 15:10:48 zack-A880G kernel: [    1.279367] perf: AMD IBS detected (0x0000001f)
Dec 15 15:10:48 zack-A880G kernel: [    1.279476] audit: initializing netlink socket (disabled)
Dec 15 15:10:48 zack-A880G kernel: [    1.279484] type=2000 audit(1387149032.172:1): initialized
Dec 15 15:10:48 zack-A880G kernel: [    1.297161] Trying to unpack rootfs image as initramfs...
Dec 15 15:10:48 zack-A880G kernel: [    1.319565] highmem bounce pool size: 64 pages
Dec 15 15:10:48 zack-A880G kernel: [    1.319578] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 15 15:10:48 zack-A880G kernel: [    1.331084] VFS: Disk quotas dquot_6.5.2
Dec 15 15:10:48 zack-A880G kernel: [    1.331130] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 15 15:10:48 zack-A880G kernel: [    1.331544] fuse init (API version 7.19)
Dec 15 15:10:48 zack-A880G kernel: [    1.331595] msgmni has been set to 1690
Dec 15 15:10:48 zack-A880G kernel: [    1.343063] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Dec 15 15:10:48 zack-A880G kernel: [    1.343099] io scheduler noop registered
Dec 15 15:10:48 zack-A880G kernel: [    1.343101] io scheduler deadline registered (default)
Dec 15 15:10:48 zack-A880G kernel: [    1.343106] io scheduler cfq registered
Dec 15 15:10:48 zack-A880G kernel: [    1.343213] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
Dec 15 15:10:48 zack-A880G kernel: [    1.343265] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
Dec 15 15:10:48 zack-A880G kernel: [    1.343307] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 15 15:10:48 zack-A880G kernel: [    1.343319] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 15 15:10:48 zack-A880G kernel: [    1.343412] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Dec 15 15:10:48 zack-A880G kernel: [    1.343416] ACPI: Power Button [PWRB]
Dec 15 15:10:48 zack-A880G kernel: [    1.343447] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Dec 15 15:10:48 zack-A880G kernel: [    1.343449] ACPI: Power Button [PWRF]
Dec 15 15:10:48 zack-A880G kernel: [    1.347130] thermal LNXTHERM:00: registered as thermal_zone0
Dec 15 15:10:48 zack-A880G kernel: [    1.347131] ACPI: Thermal Zone [THRM] (30 C)
Dec 15 15:10:48 zack-A880G kernel: [    1.347149] GHES: HEST is not enabled!
Dec 15 15:10:48 zack-A880G kernel: [    1.351131] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Dec 15 15:10:48 zack-A880G kernel: [    1.371550] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 15 15:10:48 zack-A880G kernel: [    1.371571] isapnp: Scanning for PnP cards...
Dec 15 15:10:48 zack-A880G kernel: [    1.459884] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 15 15:10:48 zack-A880G kernel: [    1.527035] Linux agpgart interface v0.103
Dec 15 15:10:48 zack-A880G kernel: [    1.528100] brd: module loaded
Dec 15 15:10:48 zack-A880G kernel: [    1.528566] loop: module loaded
Dec 15 15:10:48 zack-A880G kernel: [    1.528699] pata_acpi 0000:00:14.1: setting latency timer to 64
Dec 15 15:10:48 zack-A880G kernel: [    1.528888] Fixed MDIO Bus: probed
Dec 15 15:10:48 zack-A880G kernel: [    1.528917] tun: Universal TUN/TAP device driver, 1.6
Dec 15 15:10:48 zack-A880G kernel: [    1.528919] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 15 15:10:48 zack-A880G kernel: [    1.528943] PPP generic driver version 2.4.2
Dec 15 15:10:48 zack-A880G kernel: [    1.528967] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 15 15:10:48 zack-A880G kernel: [    1.528991] ehci_hcd 0000:00:12.2: EHCI Host Controller
Dec 15 15:10:48 zack-A880G kernel: [    1.528996] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Dec 15 15:10:48 zack-A880G kernel: [    1.529003] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Dec 15 15:10:48 zack-A880G kernel: [    1.529022] ehci_hcd 0000:00:12.2: debug port 1
Dec 15 15:10:48 zack-A880G kernel: [    1.529042] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfeaff800
Dec 15 15:10:48 zack-A880G kernel: [    1.538718] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Dec 15 15:10:48 zack-A880G kernel: [    1.538760] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Dec 15 15:10:48 zack-A880G kernel: [    1.538763] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:10:48 zack-A880G kernel: [    1.538765] usb usb1: Product: EHCI Host Controller
Dec 15 15:10:48 zack-A880G kernel: [    1.538767] usb usb1: Manufacturer: Linux 3.5.0-43-generic ehci_hcd
Dec 15 15:10:48 zack-A880G kernel: [    1.538768] usb usb1: SerialNumber: 0000:00:12.2
Dec 15 15:10:48 zack-A880G kernel: [    1.538856] hub 1-0:1.0: USB hub found
Dec 15 15:10:48 zack-A880G kernel: [    1.538860] hub 1-0:1.0: 6 ports detected
Dec 15 15:10:48 zack-A880G kernel: [    1.538942] ehci_hcd 0000:00:13.2: EHCI Host Controller
Dec 15 15:10:48 zack-A880G kernel: [    1.538947] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Dec 15 15:10:48 zack-A880G kernel: [    1.538953] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Dec 15 15:10:48 zack-A880G kernel: [    1.538973] ehci_hcd 0000:00:13.2: debug port 1
Dec 15 15:10:48 zack-A880G kernel: [    1.538995] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfeaff400
Dec 15 15:10:48 zack-A880G kernel: [    1.550788] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Dec 15 15:10:48 zack-A880G kernel: [    1.550811] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Dec 15 15:10:48 zack-A880G kernel: [    1.550813] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:10:48 zack-A880G kernel: [    1.550815] usb usb2: Product: EHCI Host Controller
Dec 15 15:10:48 zack-A880G kernel: [    1.550817] usb usb2: Manufacturer: Linux 3.5.0-43-generic ehci_hcd
Dec 15 15:10:48 zack-A880G kernel: [    1.550818] usb usb2: SerialNumber: 0000:00:13.2
Dec 15 15:10:48 zack-A880G kernel: [    1.550906] hub 2-0:1.0: USB hub found
Dec 15 15:10:48 zack-A880G kernel: [    1.550909] hub 2-0:1.0: 6 ports detected
Dec 15 15:10:48 zack-A880G kernel: [    1.550978] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 15 15:10:48 zack-A880G kernel: [    1.551031] ohci_hcd 0000:00:12.0: OHCI Host Controller
Dec 15 15:10:48 zack-A880G kernel: [    1.551035] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Dec 15 15:10:48 zack-A880G kernel: [    1.551059] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfeafe000
Dec 15 15:10:48 zack-A880G kernel: [    1.630645] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Dec 15 15:10:48 zack-A880G kernel: [    1.630648] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:10:48 zack-A880G kernel: [    1.630651] usb usb3: Product: OHCI Host Controller
Dec 15 15:10:48 zack-A880G kernel: [    1.630653] usb usb3: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
Dec 15 15:10:48 zack-A880G kernel: [    1.630654] usb usb3: SerialNumber: 0000:00:12.0
Dec 15 15:10:48 zack-A880G kernel: [    1.630749] hub 3-0:1.0: USB hub found
Dec 15 15:10:48 zack-A880G kernel: [    1.630755] hub 3-0:1.0: 3 ports detected
Dec 15 15:10:48 zack-A880G kernel: [    1.630820] ohci_hcd 0000:00:12.1: OHCI Host Controller
Dec 15 15:10:48 zack-A880G kernel: [    1.630825] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Dec 15 15:10:48 zack-A880G kernel: [    1.630842] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfeafd000
Dec 15 15:10:48 zack-A880G kernel: [    1.718421] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Dec 15 15:10:48 zack-A880G kernel: [    1.718425] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:10:48 zack-A880G kernel: [    1.718427] usb usb4: Product: OHCI Host Controller
Dec 15 15:10:48 zack-A880G kernel: [    1.718429] usb usb4: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
Dec 15 15:10:48 zack-A880G kernel: [    1.718431] usb usb4: SerialNumber: 0000:00:12.1
Dec 15 15:10:48 zack-A880G kernel: [    1.718518] hub 4-0:1.0: USB hub found
Dec 15 15:10:48 zack-A880G kernel: [    1.718524] hub 4-0:1.0: 3 ports detected
Dec 15 15:10:48 zack-A880G kernel: [    1.718592] ohci_hcd 0000:00:13.0: OHCI Host Controller
Dec 15 15:10:48 zack-A880G kernel: [    1.718596] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Dec 15 15:10:48 zack-A880G kernel: [    1.718623] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfeafc000
Dec 15 15:10:48 zack-A880G kernel: [    1.786194] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Dec 15 15:10:48 zack-A880G kernel: [    1.786198] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:10:48 zack-A880G kernel: [    1.786200] usb usb5: Product: OHCI Host Controller
Dec 15 15:10:48 zack-A880G kernel: [    1.786202] usb usb5: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
Dec 15 15:10:48 zack-A880G kernel: [    1.786203] usb usb5: SerialNumber: 0000:00:13.0
Dec 15 15:10:48 zack-A880G kernel: [    1.786289] hub 5-0:1.0: USB hub found
Dec 15 15:10:48 zack-A880G kernel: [    1.786298] hub 5-0:1.0: 3 ports detected
Dec 15 15:10:48 zack-A880G kernel: [    1.786365] ohci_hcd 0000:00:13.1: OHCI Host Controller
Dec 15 15:10:48 zack-A880G kernel: [    1.786370] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Dec 15 15:10:48 zack-A880G kernel: [    1.786386] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfeafb000
Dec 15 15:10:48 zack-A880G kernel: [    1.850061] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
Dec 15 15:10:48 zack-A880G kernel: [    1.850065] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:10:48 zack-A880G kernel: [    1.850067] usb usb6: Product: OHCI Host Controller
Dec 15 15:10:48 zack-A880G kernel: [    1.850069] usb usb6: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
Dec 15 15:10:48 zack-A880G kernel: [    1.850070] usb usb6: SerialNumber: 0000:00:13.1
Dec 15 15:10:48 zack-A880G kernel: [    1.850159] hub 6-0:1.0: USB hub found
Dec 15 15:10:48 zack-A880G kernel: [    1.850168] hub 6-0:1.0: 3 ports detected
Dec 15 15:10:48 zack-A880G kernel: [    1.850235] ohci_hcd 0000:00:14.5: OHCI Host Controller
Dec 15 15:10:48 zack-A880G kernel: [    1.850240] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
Dec 15 15:10:48 zack-A880G kernel: [    1.850256] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfeafa000
Dec 15 15:10:48 zack-A880G kernel: [    1.925394] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
Dec 15 15:10:48 zack-A880G kernel: [    1.925398] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:10:48 zack-A880G kernel: [    1.925400] usb usb7: Product: OHCI Host Controller
Dec 15 15:10:48 zack-A880G kernel: [    1.925402] usb usb7: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
Dec 15 15:10:48 zack-A880G kernel: [    1.925403] usb usb7: SerialNumber: 0000:00:14.5
Dec 15 15:10:48 zack-A880G kernel: [    1.928846] Freeing initrd memory: 15192k freed
Dec 15 15:10:48 zack-A880G kernel: [    1.934118] hub 7-0:1.0: USB hub found
Dec 15 15:10:48 zack-A880G kernel: [    1.934129] hub 7-0:1.0: 2 ports detected
Dec 15 15:10:48 zack-A880G kernel: [    1.934183] uhci_hcd: USB Universal Host Controller Interface driver
Dec 15 15:10:48 zack-A880G kernel: [    1.934249] usbcore: registered new interface driver libusual
Dec 15 15:10:48 zack-A880G kernel: [    1.934283] i8042: PNP: No PS/2 controller found. Probing ports directly.
Dec 15 15:10:48 zack-A880G kernel: [    1.978482] isapnp: No Plug & Play device found
Dec 15 15:10:48 zack-A880G kernel: [    1.978557] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 15 15:10:48 zack-A880G kernel: [    1.978560] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 15 15:10:48 zack-A880G kernel: [    1.978655] mousedev: PS/2 mouse device common for all mice
Dec 15 15:10:48 zack-A880G kernel: [    1.978737] rtc_cmos 00:03: RTC can wake from S4
Dec 15 15:10:48 zack-A880G kernel: [    1.978833] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Dec 15 15:10:48 zack-A880G kernel: [    1.978856] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Dec 15 15:10:48 zack-A880G kernel: [    1.978894] device-mapper: uevent: version 1.0.3
Dec 15 15:10:48 zack-A880G kernel: [    1.978936] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Dec 15 15:10:48 zack-A880G kernel: [    1.978948] EISA: Probing bus 0 at eisa.0
Dec 15 15:10:48 zack-A880G kernel: [    1.978949] EISA: Cannot allocate resource for mainboard
Dec 15 15:10:48 zack-A880G kernel: [    1.978951] Cannot allocate resource for EISA slot 1
Dec 15 15:10:48 zack-A880G kernel: [    1.978952] Cannot allocate resource for EISA slot 2
Dec 15 15:10:48 zack-A880G kernel: [    1.978953] Cannot allocate resource for EISA slot 3
Dec 15 15:10:48 zack-A880G kernel: [    1.978954] Cannot allocate resource for EISA slot 4
Dec 15 15:10:48 zack-A880G kernel: [    1.978955] Cannot allocate resource for EISA slot 5
Dec 15 15:10:48 zack-A880G kernel: [    1.978956] Cannot allocate resource for EISA slot 6
Dec 15 15:10:48 zack-A880G kernel: [    1.978957] Cannot allocate resource for EISA slot 7
Dec 15 15:10:48 zack-A880G kernel: [    1.978958] Cannot allocate resource for EISA slot 8
Dec 15 15:10:48 zack-A880G kernel: [    1.978959] EISA: Detected 0 cards.
Dec 15 15:10:48 zack-A880G kernel: [    1.978966] cpuidle: using governor ladder
Dec 15 15:10:48 zack-A880G kernel: [    1.978967] cpuidle: using governor menu
Dec 15 15:10:48 zack-A880G kernel: [    1.978968] EFI Variables Facility v0.08 2004-May-17
Dec 15 15:10:48 zack-A880G kernel: [    1.979121] ashmem: initialized
Dec 15 15:10:48 zack-A880G kernel: [    1.979210] TCP: cubic registered
Dec 15 15:10:48 zack-A880G kernel: [    1.979279] NET: Registered protocol family 10
Dec 15 15:10:48 zack-A880G kernel: [    1.979420] NET: Registered protocol family 17
Dec 15 15:10:48 zack-A880G kernel: [    1.979428] Key type dns_resolver registered
Dec 15 15:10:48 zack-A880G kernel: [    1.979464] Using IPI No-Shortcut mode
Dec 15 15:10:48 zack-A880G kernel: [    1.979511] PM: Hibernation image not present or could not be loaded.
Dec 15 15:10:48 zack-A880G kernel: [    1.979521] registered taskstats version 1
Dec 15 15:10:48 zack-A880G kernel: [    1.981288] Key type trusted registered
Dec 15 15:10:48 zack-A880G kernel: [    1.982695] Key type encrypted registered
Dec 15 15:10:48 zack-A880G kernel: [    1.984325]   Magic number: 9:222:201
Dec 15 15:10:48 zack-A880G kernel: [    1.984411] rtc_cmos 00:03: setting system clock to 2013-12-15 23:10:33 UTC (1387149033)
Dec 15 15:10:48 zack-A880G kernel: [    1.984437] powernow-k8: Found 1 AMD Sempron(tm) 145 Processor (1 cpu cores) (version 2.20.00)
Dec 15 15:10:48 zack-A880G kernel: [    1.984464] powernow-k8:    0 : pstate 0 (2800 MHz)
Dec 15 15:10:48 zack-A880G kernel: [    1.984465] powernow-k8:    1 : pstate 1 (2000 MHz)
Dec 15 15:10:48 zack-A880G kernel: [    1.984466] powernow-k8:    2 : pstate 2 (1600 MHz)
Dec 15 15:10:48 zack-A880G kernel: [    1.984467] powernow-k8:    3 : pstate 3 (800 MHz)
Dec 15 15:10:48 zack-A880G kernel: [    1.984519] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 15 15:10:48 zack-A880G kernel: [    1.984521] EDD information not available.
Dec 15 15:10:48 zack-A880G kernel: [    1.984613] Freeing unused kernel memory: 764k freed
Dec 15 15:10:48 zack-A880G kernel: [    1.984840] Write protecting the kernel text: 6060k
Dec 15 15:10:48 zack-A880G kernel: [    1.984852] Write protecting the kernel read-only data: 2484k
Dec 15 15:10:48 zack-A880G kernel: [    1.984853] NX-protecting the kernel data: 4180k
Dec 15 15:10:48 zack-A880G kernel: [    2.051846] ahci 0000:00:11.0: version 3.0
Dec 15 15:10:48 zack-A880G kernel: [    2.051964] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Dec 15 15:10:48 zack-A880G kernel: [    2.051967] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
Dec 15 15:10:48 zack-A880G kernel: [    2.067564] scsi0 : ahci
Dec 15 15:10:48 zack-A880G kernel: [    2.070332] scsi1 : ahci
Dec 15 15:10:48 zack-A880G kernel: [    2.072046] scsi2 : ahci
Dec 15 15:10:48 zack-A880G kernel: [    2.073689] scsi3 : ahci
Dec 15 15:10:48 zack-A880G kernel: [    2.073785] ata1: SATA max UDMA/133 abar m1024@0xfeaffc00 port 0xfeaffd00 irq 22
Dec 15 15:10:48 zack-A880G kernel: [    2.073788] ata2: SATA max UDMA/133 abar m1024@0xfeaffc00 port 0xfeaffd80 irq 22
Dec 15 15:10:48 zack-A880G kernel: [    2.073791] ata3: SATA max UDMA/133 abar m1024@0xfeaffc00 port 0xfeaffe00 irq 22
Dec 15 15:10:48 zack-A880G kernel: [    2.073793] ata4: SATA max UDMA/133 abar m1024@0xfeaffc00 port 0xfeaffe80 irq 22
Dec 15 15:10:48 zack-A880G kernel: [    2.081267] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 15 15:10:48 zack-A880G kernel: [    2.081342] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
Dec 15 15:10:48 zack-A880G kernel: [    2.081472] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xf8428000, 00:30:67:8c:c9:b2, XID 081000c0 IRQ 42
Dec 15 15:10:48 zack-A880G kernel: [    2.081474] r8169 0000:02:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Dec 15 15:10:48 zack-A880G kernel: [    2.092483] scsi4 : pata_atiixp
Dec 15 15:10:48 zack-A880G kernel: [    2.095712] scsi5 : pata_atiixp
Dec 15 15:10:48 zack-A880G kernel: [    2.096236] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Dec 15 15:10:48 zack-A880G kernel: [    2.096238] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Dec 15 15:10:48 zack-A880G kernel: [    2.273255] usb 3-3: new low-speed USB device number 2 using ohci_hcd
Dec 15 15:10:48 zack-A880G kernel: [    2.275309] ata6.00: ATA-7: Maxtor 6L200P0, BAH41G10, max UDMA/133
Dec 15 15:10:48 zack-A880G kernel: [    2.275313] ata6.00: 398297088 sectors, multi 16: LBA48 
Dec 15 15:10:48 zack-A880G kernel: [    2.275723] ata6.01: ATA-5: QUANTUM FIREBALLlct20 10, APL.0900, max UDMA/100
Dec 15 15:10:48 zack-A880G kernel: [    2.275727] ata6.01: 20044080 sectors, multi 8: LBA 
Dec 15 15:10:48 zack-A880G kernel: [    2.299545] Refined TSC clocksource calibration: 2800.158 MHz.
Dec 15 15:10:48 zack-A880G kernel: [    2.299550] Switching to clocksource tsc
Dec 15 15:10:48 zack-A880G kernel: [    2.301163] ata6.00: configured for UDMA/100
Dec 15 15:10:48 zack-A880G kernel: [    2.317914] ata6.01: configured for UDMA/100
Dec 15 15:10:48 zack-A880G kernel: [    2.393053] ata2: SATA link down (SStatus 0 SControl 300)
Dec 15 15:10:48 zack-A880G kernel: [    2.393087] ata4: SATA link down (SStatus 0 SControl 300)
Dec 15 15:10:48 zack-A880G kernel: [    2.393115] ata3: SATA link down (SStatus 0 SControl 300)
Dec 15 15:10:48 zack-A880G kernel: [    2.442167] usb 3-3: New USB device found, idVendor=046d, idProduct=c512
Dec 15 15:10:48 zack-A880G kernel: [    2.442171] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Dec 15 15:10:48 zack-A880G kernel: [    2.442174] usb 3-3: Product: USB Receiver
Dec 15 15:10:48 zack-A880G kernel: [    2.442175] usb 3-3: Manufacturer: Logitech
Dec 15 15:10:48 zack-A880G kernel: [    2.460377] usbcore: registered new interface driver usbhid
Dec 15 15:10:48 zack-A880G kernel: [    2.460380] usbhid: USB HID core driver
Dec 15 15:10:48 zack-A880G kernel: [    2.564697] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 15 15:10:48 zack-A880G kernel: [    2.567175] ata1.00: ATAPI: ASUS    DRW-24B3LT, 1.00, max UDMA/100
Dec 15 15:10:48 zack-A880G kernel: [    2.568010] ata1.00: configured for UDMA/100
Dec 15 15:10:48 zack-A880G kernel: [    2.569952] scsi 0:0:0:0: CD-ROM            ASUS     DRW-24B3LT       1.00 PQ: 0 ANSI: 5
Dec 15 15:10:48 zack-A880G kernel: [    2.573333] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 15 15:10:48 zack-A880G kernel: [    2.573337] cdrom: Uniform CD-ROM driver Revision: 3.20
Dec 15 15:10:48 zack-A880G kernel: [    2.573436] sr 0:0:0:0: Attached scsi CD-ROM sr0
Dec 15 15:10:48 zack-A880G kernel: [    2.573500] sr 0:0:0:0: Attached scsi generic sg0 type 5
Dec 15 15:10:48 zack-A880G kernel: [    2.573610] scsi 5:0:0:0: Direct-Access     ATA      Maxtor 6L200P0   BAH4 PQ: 0 ANSI: 5
Dec 15 15:10:48 zack-A880G kernel: [    2.573695] sd 5:0:0:0: [sda] 398297088 512-byte logical blocks: (203 GB/189 GiB)
Dec 15 15:10:48 zack-A880G kernel: [    2.573724] sd 5:0:0:0: [sda] Write Protect is off
Dec 15 15:10:48 zack-A880G kernel: [    2.573727] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 15 15:10:48 zack-A880G kernel: [    2.573738] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 15 15:10:48 zack-A880G kernel: [    2.573909] sd 5:0:0:0: Attached scsi generic sg1 type 0
Dec 15 15:10:48 zack-A880G kernel: [    2.614215]  sda: sda1 sda2 < sda5 >
Dec 15 15:10:48 zack-A880G kernel: [    2.614436] sd 5:0:0:0: [sda] Attached SCSI disk
Dec 15 15:10:48 zack-A880G kernel: [    2.614493] scsi 5:0:1:0: Direct-Access     ATA      QUANTUM FIREBALL APL. PQ: 0 ANSI: 5
Dec 15 15:10:48 zack-A880G kernel: [    2.614584] sd 5:0:1:0: Attached scsi generic sg2 type 0
Dec 15 15:10:48 zack-A880G kernel: [    2.614620] sd 5:0:1:0: [sdb] 20044080 512-byte logical blocks: (10.2 GB/9.55 GiB)
Dec 15 15:10:48 zack-A880G kernel: [    2.614644] sd 5:0:1:0: [sdb] Write Protect is off
Dec 15 15:10:48 zack-A880G kernel: [    2.614646] sd 5:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Dec 15 15:10:48 zack-A880G kernel: [    2.614657] sd 5:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 15 15:10:48 zack-A880G kernel: [    2.648592]  sdb: sdb1 sdb2 < sdb5 >
Dec 15 15:10:48 zack-A880G kernel: [    2.648812] sd 5:0:1:0: [sdb] Attached SCSI disk
Dec 15 15:10:48 zack-A880G kernel: [    2.660450] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input2
Dec 15 15:10:48 zack-A880G kernel: [    2.660570] logitech 0003:046D:C512.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:12.0-3/input0
Dec 15 15:10:48 zack-A880G kernel: [    2.661276] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1/input/input3
Dec 15 15:10:48 zack-A880G kernel: [    2.661398] logitech 0003:046D:C512.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:12.0-3/input1
Dec 15 15:10:48 zack-A880G kernel: [    5.553591] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Dec 15 15:10:48 zack-A880G kernel: [   16.199706] Adding 6141948k swap on /dev/sda5.  Priority:-1 extents:1 across:6141948k 
Dec 15 15:10:48 zack-A880G kernel: [   16.206175] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 15 15:10:48 zack-A880G kernel: [   16.300329] lp: driver loaded but no devices found
Dec 15 15:10:48 zack-A880G kernel: [   16.366993] ACPI Warning: 0x00000b00-0x00000b07 SystemIO conflicts with Region \SOR1 1 (20120320/utaddress-251)
Dec 15 15:10:48 zack-A880G kernel: [   16.367001] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Dec 15 15:10:48 zack-A880G kernel: [   16.372969] sp5100_tco: SP5100 TCO WatchDog Timer Driver v0.01
Dec 15 15:10:48 zack-A880G kernel: [   16.373096] sp5100_tco: mmio address 0xfec000f0 already in use
Dec 15 15:10:48 zack-A880G kernel: [   16.432279] wmi: Mapper loaded
Dec 15 15:10:48 zack-A880G kernel: [   16.465402] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Dec 15 15:10:48 zack-A880G kernel: [   16.577930] parport_pc 00:07: reported by Plug and Play ACPI
Dec 15 15:10:48 zack-A880G kernel: [   16.577987] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Dec 15 15:10:48 zack-A880G kernel: [   16.628687] nvidia: module license 'NVIDIA' taints kernel.
Dec 15 15:10:48 zack-A880G kernel: [   16.628691] Disabling lock debugging due to kernel taint
Dec 15 15:10:48 zack-A880G kernel: [   16.648380] type=1400 audit(1387149048.187:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=581 comm="apparmor_parser"
Dec 15 15:10:48 zack-A880G kernel: [   16.648758] type=1400 audit(1387149048.187:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=581 comm="apparmor_parser"
Dec 15 15:10:48 zack-A880G kernel: [   16.648974] type=1400 audit(1387149048.187:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=581 comm="apparmor_parser"
Dec 15 15:10:48 zack-A880G kernel: [   16.703453] lp0: using parport0 (interrupt-driven).
Dec 15 15:10:48 zack-A880G kernel: [   16.717794] microcode: CPU0: patch_level=0x010000c8
Dec 15 15:10:48 zack-A880G kernel: [   16.822343] Bluetooth: Core ver 2.16
Dec 15 15:10:48 zack-A880G kernel: [   16.822362] NET: Registered protocol family 31
Dec 15 15:10:48 zack-A880G kernel: [   16.822362] Bluetooth: HCI device and connection manager initialized
Dec 15 15:10:48 zack-A880G kernel: [   16.822364] Bluetooth: HCI socket layer initialized
Dec 15 15:10:48 zack-A880G kernel: [   16.822364] Bluetooth: L2CAP socket layer initialized
Dec 15 15:10:48 zack-A880G kernel: [   16.822367] Bluetooth: SCO socket layer initialized
Dec 15 15:10:48 zack-A880G kernel: [   16.829302] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Dec 15 15:10:48 zack-A880G kernel: [   16.836733] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Dec 15 15:10:48 zack-A880G kernel: [   16.836737] Bluetooth: BNEP filters: protocol multicast
Dec 15 15:10:48 zack-A880G kernel: [   16.853914] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.88  Wed Mar 27 14:31:12 PDT 2013
Dec 15 15:10:48 zack-A880G kernel: [   16.930787] ppdev: user-space parallel port driver
Dec 15 15:10:48 zack-A880G udev-configure-printer: add /module/lp
Dec 15 15:10:48 zack-A880G udev-configure-printer: Failed to get parent
Dec 15 15:10:48 zack-A880G rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Dec 15 15:10:48 zack-A880G kernel: [   17.104256] Bluetooth: RFCOMM TTY layer initialized
Dec 15 15:10:48 zack-A880G kernel: [   17.104264] Bluetooth: RFCOMM socket layer initialized
Dec 15 15:10:48 zack-A880G kernel: [   17.104265] Bluetooth: RFCOMM ver 1.11
Dec 15 15:10:48 zack-A880G udev-configure-printer: add /devices/pnp0/00:07/printer/lp0
Dec 15 15:10:48 zack-A880G udev-configure-printer: Failed to get parent
Dec 15 15:10:48 zack-A880G avahi-daemon[739]: Found user 'avahi' (UID 107) and group 'avahi' (GID 118).
Dec 15 15:10:48 zack-A880G avahi-daemon[739]: Successfully dropped root privileges.
Dec 15 15:10:48 zack-A880G avahi-daemon[739]: avahi-daemon 0.6.30 starting up.
Dec 15 15:10:48 zack-A880G avahi-daemon[739]: Successfully called chroot().
Dec 15 15:10:48 zack-A880G avahi-daemon[739]: Successfully dropped remaining capabilities.
Dec 15 15:10:48 zack-A880G kernel: [   17.138163] type=1400 audit(1387149048.679:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=741 comm="apparmor_parser"
Dec 15 15:10:48 zack-A880G kernel: [   17.138642] type=1400 audit(1387149048.679:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=741 comm="apparmor_parser"
Dec 15 15:10:48 zack-A880G kernel: [   17.140834] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Dec 15 15:10:48 zack-A880G avahi-daemon[739]: Loading service file /services/udisks.service.
Dec 15 15:10:48 zack-A880G kernel: [   17.165105] kvm: Nested Virtualization enabled
Dec 15 15:10:48 zack-A880G kernel: [   17.165109] kvm: Nested Paging enabled
Dec 15 15:10:48 zack-A880G failsafe: Failsafe of 120 seconds reached.
Dec 15 15:10:48 zack-A880G avahi-daemon[739]: Network interface enumeration completed.
Dec 15 15:10:48 zack-A880G avahi-daemon[739]: Registering HINFO record with values 'I686'/'LINUX'.
Dec 15 15:10:48 zack-A880G avahi-daemon[739]: Server startup complete. Host name is zack-A880G.local. Local service cookie is 2658245394.
Dec 15 15:10:48 zack-A880G avahi-daemon[739]: Service "zack-A880G" (/services/udisks.service) successfully established.
Dec 15 15:10:48 zack-A880G kernel: [   17.220925] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
Dec 15 15:10:48 zack-A880G kernel: [   17.221079] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
Dec 15 15:10:48 zack-A880G kernel: [   17.221780] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
Dec 15 15:10:48 zack-A880G kernel: [   17.221930] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
Dec 15 15:10:48 zack-A880G kernel: [   17.222068] input: HDA ATI SB Line Out as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
Dec 15 15:10:48 zack-A880G kernel: [   17.235449] hda_intel: Disabling MSI
Dec 15 15:10:48 zack-A880G kernel: [   17.235457] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  ModemManager (version 0.5.2.0) starting...
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin Nokia
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin Option
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin Sierra
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin Novatel
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin ZTE
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin Linktop
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin MotoC
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin Gobi
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin X22X
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin Longcheer
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin Generic
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin Huawei
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin Ericsson MBM
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin SimTech
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin AnyData
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin Option High-Speed
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin Samsung
Dec 15 15:10:48 zack-A880G modem-manager[814]: <info>  Loaded plugin Wavecom
Dec 15 15:10:48 zack-A880G NetworkManager[818]: <info> NetworkManager (version 0.9.4.0) is starting...
Dec 15 15:10:48 zack-A880G NetworkManager[818]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Dec 15 15:10:48 zack-A880G NetworkManager[818]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Dec 15 15:10:48 zack-A880G NetworkManager[818]: <info> DNS: loaded plugin dnsmasq
Dec 15 15:10:48 zack-A880G dbus[638]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Dec 15 15:10:48 zack-A880G kernel: [   17.406725] type=1400 audit(1387149048.947:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=856 comm="apparmor_parser"
Dec 15 15:10:48 zack-A880G kernel: [   17.407064] type=1400 audit(1387149048.947:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=856 comm="apparmor_parser"
Dec 15 15:10:48 zack-A880G kernel: [   17.409246] type=1400 audit(1387149048.951:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=857 comm="apparmor_parser"
Dec 15 15:10:48 zack-A880G kernel: [   17.409628] type=1400 audit(1387149048.951:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=857 comm="apparmor_parser"
Dec 15 15:10:48 zack-A880G kernel: [   17.409844] type=1400 audit(1387149048.951:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=857 comm="apparmor_parser"
Dec 15 15:10:49 zack-A880G polkitd[824]: started daemon version 0.104 using authority implementation `local' version `0.104'
Dec 15 15:10:49 zack-A880G dbus[638]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Dec 15 15:10:49 zack-A880G NetworkManager[818]:    SCPlugin-Ifupdown: init!
Dec 15 15:10:49 zack-A880G NetworkManager[818]:    SCPlugin-Ifupdown: update_system_hostname
Dec 15 15:10:49 zack-A880G NetworkManager[818]:    SCPluginIfupdown: management mode: unmanaged
Dec 15 15:10:49 zack-A880G NetworkManager[818]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0/net/eth0, iface: eth0)
Dec 15 15:10:49 zack-A880G NetworkManager[818]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec 15 15:10:49 zack-A880G NetworkManager[818]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Dec 15 15:10:49 zack-A880G NetworkManager[818]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Dec 15 15:10:49 zack-A880G NetworkManager[818]:    SCPlugin-Ifupdown: end _init.
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dec 15 15:10:49 zack-A880G NetworkManager[818]:    Ifupdown: get unmanaged devices count: 0
Dec 15 15:10:49 zack-A880G NetworkManager[818]:    SCPlugin-Ifupdown: (153823144) ... get_connections.
Dec 15 15:10:49 zack-A880G NetworkManager[818]:    SCPlugin-Ifupdown: (153823144) ... get_connections (managed=false): return empty list.
Dec 15 15:10:49 zack-A880G NetworkManager[818]:    keyfile: parsing Zoom Zoom 1 ... 
Dec 15 15:10:49 zack-A880G NetworkManager[818]:    keyfile:     read connection 'Zoom Zoom 1'
Dec 15 15:10:49 zack-A880G NetworkManager[818]:    keyfile: parsing Zoom Zoom ... 
Dec 15 15:10:49 zack-A880G NetworkManager[818]:    keyfile:     read connection 'Zoom Zoom'
Dec 15 15:10:49 zack-A880G NetworkManager[818]:    Ifupdown: get unmanaged devices count: 0
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> modem-manager is now available
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> WiFi enabled by radio killswitch; enabled by state file
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> WWAN enabled by radio killswitch; enabled by state file
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> WiMAX enabled by radio killswitch; enabled by state file
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> Networking is enabled by state file
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <warn> failed to allocate link cache: (-10) Operation not supported
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> (eth0): carrier is OFF
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> (eth0): now managed
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> (eth0): bringing up device.
Dec 15 15:10:49 zack-A880G kernel: [   17.600009] r8169 0000:02:00.0: eth0: link down
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> (eth0): preparing device.
Dec 15 15:10:49 zack-A880G kernel: [   17.619461] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> (eth0): deactivating device (reason 'managed') [2]
Dec 15 15:10:49 zack-A880G NetworkManager[818]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0/net/eth0
Dec 15 15:10:49 zack-A880G kernel: [   17.620616] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 15 15:10:49 zack-A880G kernel: [   17.636048] r8169 0000:02:00.0: eth0: link down
Dec 15 15:10:49 zack-A880G udev-configure-printer: add /devices/pnp0/00:07/printer/lp0
Dec 15 15:10:49 zack-A880G udev-configure-printer: Failed to get parent
Dec 15 15:10:49 zack-A880G udev-configure-printer: add /module/lp
Dec 15 15:10:49 zack-A880G udev-configure-printer: Failed to get parent
Dec 15 15:10:49 zack-A880G cron[934]: (CRON) INFO (pidfile fd = 3)
Dec 15 15:10:49 zack-A880G anacron[952]: Anacron 2.3 started on 2013-12-15
Dec 15 15:10:49 zack-A880G acpid: starting up with proc fs
Dec 15 15:10:49 zack-A880G acpid: skipping conf file /etc/acpi/events/RadioPower.sh
Dec 15 15:10:49 zack-A880G acpid: 35 rules loaded
Dec 15 15:10:49 zack-A880G acpid: waiting for events: event logging is off
Dec 15 15:10:49 zack-A880G cron[976]: (CRON) STARTUP (fork ok)
Dec 15 15:10:49 zack-A880G cron[976]: (CRON) INFO (Running @reboot jobs)
Dec 15 15:10:49 zack-A880G kernel: [   18.219133] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input9
Dec 15 15:10:49 zack-A880G kernel: [   18.219282] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input10
Dec 15 15:10:49 zack-A880G kernel: [   18.219408] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input11
Dec 15 15:10:49 zack-A880G kernel: [   18.219530] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input12
Dec 15 15:10:49 zack-A880G anacron[952]: Will run job `cron.daily' in 5 min.
Dec 15 15:10:49 zack-A880G anacron[952]: Will run job `cron.weekly' in 10 min.
Dec 15 15:10:49 zack-A880G anacron[952]: Will run job `cron.monthly' in 15 min.
Dec 15 15:10:49 zack-A880G anacron[952]: Jobs will be executed sequentially
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> (eth0): carrier now ON (device state 20)
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> Auto-activating connection 'Wired connection 1'.
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> Activation (eth0) starting connection 'Wired connection 1'
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 15 15:10:50 zack-A880G kernel: [   19.347018] r8169 0000:02:00.0: eth0: link up
Dec 15 15:10:50 zack-A880G kernel: [   19.347190] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> dhclient started with pid 1071
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> Activation (eth0) Beginning IP6 addrconf.
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec 15 15:10:50 zack-A880G dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Dec 15 15:10:50 zack-A880G dhclient: Copyright 2004-2011 Internet Systems Consortium.
Dec 15 15:10:50 zack-A880G dhclient: All rights reserved.
Dec 15 15:10:50 zack-A880G dhclient: For info, please visit https://www.isc.org/software/dhcp/
Dec 15 15:10:50 zack-A880G dhclient: 
Dec 15 15:10:50 zack-A880G NetworkManager[818]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec 15 15:10:50 zack-A880G dhclient: Listening on LPF/eth0/00:30:67:8c:c9:b2
Dec 15 15:10:50 zack-A880G dhclient: Sending on   LPF/eth0/00:30:67:8c:c9:b2
Dec 15 15:10:50 zack-A880G dhclient: Sending on   Socket/fallback
Dec 15 15:10:50 zack-A880G dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec 15 15:10:51 zack-A880G dhclient: DHCPREQUEST of 192.168.1.47 on eth0 to 255.255.255.255 port 67
Dec 15 15:10:51 zack-A880G dhclient: DHCPOFFER of 192.168.1.47 from 192.168.1.1
Dec 15 15:10:51 zack-A880G dhclient: DHCPACK of 192.168.1.47 from 192.168.1.1
Dec 15 15:10:51 zack-A880G NetworkManager[818]: <info> (eth0): DHCPv4 state changed preinit -> bound
Dec 15 15:10:51 zack-A880G NetworkManager[818]: <info>   address 192.168.1.47
Dec 15 15:10:51 zack-A880G NetworkManager[818]: <info>   prefix 24 (255.255.255.0)
Dec 15 15:10:51 zack-A880G NetworkManager[818]: <info>   gateway 192.168.1.1
Dec 15 15:10:51 zack-A880G NetworkManager[818]: <info>   nameserver '192.168.1.1'
Dec 15 15:10:51 zack-A880G NetworkManager[818]: <info>   nameserver '192.168.1.1'
Dec 15 15:10:51 zack-A880G NetworkManager[818]: <info>   domain name 'myhome.westell.com'
Dec 15 15:10:51 zack-A880G NetworkManager[818]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Dec 15 15:10:51 zack-A880G NetworkManager[818]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Dec 15 15:10:51 zack-A880G avahi-daemon[739]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.47.
Dec 15 15:10:51 zack-A880G avahi-daemon[739]: New relevant interface eth0.IPv4 for mDNS.
Dec 15 15:10:51 zack-A880G avahi-daemon[739]: Registering new address record for 192.168.1.47 on eth0.IPv4.
Dec 15 15:10:52 zack-A880G dhclient: bound to 192.168.1.47 -- renewal in 41684 seconds.
Dec 15 15:10:52 zack-A880G avahi-daemon[739]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::230:67ff:fe8c:c9b2.
Dec 15 15:10:52 zack-A880G avahi-daemon[739]: New relevant interface eth0.IPv6 for mDNS.
Dec 15 15:10:52 zack-A880G avahi-daemon[739]: Registering new address record for fe80::230:67ff:fe8c:c9b2 on eth0.*.
Dec 15 15:10:52 zack-A880G dhclient: isc-dhclient-4.1-ESV-R4
Dec 15 15:10:52 zack-A880G dhclient: isc-dhclient-4.1-ESV-R4
Dec 15 15:10:52 zack-A880G acpid: client connected from 1227[0:0]
Dec 15 15:10:52 zack-A880G acpid: 1 client rule loaded
Dec 15 15:10:52 zack-A880G kernel: [   21.081571] NVRM: API mismatch: the client has the version 319.32, but
Dec 15 15:10:52 zack-A880G kernel: [   21.081571] NVRM: this kernel module has the version 304.88.  Please
Dec 15 15:10:52 zack-A880G kernel: [   21.081571] NVRM: make sure that this kernel module and all NVIDIA driver
Dec 15 15:10:52 zack-A880G kernel: [   21.081571] NVRM: components have the same version.
Dec 15 15:10:52 zack-A880G acpid: client 1227[0:0] has disconnected
Dec 15 15:10:52 zack-A880G acpid: client connected from 1268[0:0]
Dec 15 15:10:52 zack-A880G acpid: 1 client rule loaded
Dec 15 15:10:52 zack-A880G kernel: [   21.180869] NVRM: API mismatch: the client has the version 319.32, but
Dec 15 15:10:52 zack-A880G kernel: [   21.180869] NVRM: this kernel module has the version 304.88.  Please
Dec 15 15:10:52 zack-A880G kernel: [   21.180869] NVRM: make sure that this kernel module and all NVIDIA driver
Dec 15 15:10:52 zack-A880G kernel: [   21.180869] NVRM: components have the same version.
Dec 15 15:10:52 zack-A880G NetworkManager[818]: <info> DNS: starting dnsmasq...
Dec 15 15:10:52 zack-A880G NetworkManager[818]: <error> [1387149052.919952] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
Dec 15 15:10:52 zack-A880G NetworkManager[818]: <error> [1387149052.920008] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
Dec 15 15:10:52 zack-A880G NetworkManager[818]: <warn> DNS: plugin dnsmasq update failed
Dec 15 15:10:52 zack-A880G NetworkManager[818]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Dec 15 15:10:52 zack-A880G dnsmasq[1269]: started, version 2.59 cache disabled
Dec 15 15:10:52 zack-A880G dnsmasq[1269]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Dec 15 15:10:52 zack-A880G dnsmasq[1269]: DBus support enabled: connected to system bus
Dec 15 15:10:52 zack-A880G dnsmasq[1269]: warning: no upstream servers configured
Dec 15 15:10:52 zack-A880G NetworkManager[818]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Dec 15 15:10:53 zack-A880G NetworkManager[818]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Dec 15 15:10:53 zack-A880G NetworkManager[818]: <info> Activation (eth0) successful, device activated.
Dec 15 15:10:53 zack-A880G NetworkManager[818]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Dec 15 15:10:53 zack-A880G NetworkManager[818]: <warn> dnsmasq appeared on DBus: :1.14
Dec 15 15:10:53 zack-A880G dbus[638]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec 15 15:10:53 zack-A880G NetworkManager[818]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Dec 15 15:10:53 zack-A880G dnsmasq[1269]: setting upstream servers from DBus
Dec 15 15:10:53 zack-A880G dnsmasq[1269]: using nameserver 192.168.1.1#53
Dec 15 15:10:53 zack-A880G dbus[638]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 15 23:11:05 zack-A880G ntpdate[1387]: step time server 91.189.94.4 offset 28801.836078 sec
Dec 15 23:11:13 zack-A880G NetworkManager[818]: <info> (eth0): IP6 addrconf timed out or failed.
Dec 15 23:11:13 zack-A880G NetworkManager[818]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Dec 15 23:11:13 zack-A880G NetworkManager[818]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Dec 15 23:11:13 zack-A880G NetworkManager[818]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Dec 15 15:13:01 zack-A880G kernel: imklog 5.8.6, log source = /proc/kmsg started.
Dec 15 15:13:01 zack-A880G rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="583" x-info="http://www.rsyslog.com"] start
Dec 15 15:13:01 zack-A880G rsyslogd: rsyslogd's groupid changed to 103
Dec 15 15:13:01 zack-A880G rsyslogd: rsyslogd's userid changed to 101
Dec 15 15:13:01 zack-A880G rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Linux version 3.5.0-43-generic (buildd@akateko) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #66~precise1-Ubuntu SMP Thu Oct 24 14:55:08 UTC 2013 (Ubuntu 3.5.0-43.66~precise1-generic 3.5.7.23)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] KERNEL supported cpus:
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   Intel GenuineIntel
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   AMD AuthenticAMD
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   NSC Geode by NSC
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   Cyrix CyrixInstead
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   Centaur CentaurHauls
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   Transmeta GenuineTMx86
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   Transmeta TransmetaCPU
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   UMC UMC UMC UMC
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ffaffff] usable
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x000000007ffb0000-0x000000007ffbdfff] ACPI data
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x000000007ffbe000-0x000000007ffdffff] ACPI NVS
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x000000007ffe0000-0x000000007fffffff] reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] SMBIOS 2.6 present.
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] DMI: BIOSTAR Group A880G+/A880G+, BIOS 080016  08/30/2010
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] e820: last_pfn = 0x7ffb0 max_arch_pfn = 0x1000000
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] MTRR default type: uncachable
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   00000-9FFFF write-back
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   A0000-EFFFF uncachable
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   F0000-FFFFF write-protect
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] MTRR variable ranges enabled:
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   1 disabled
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   2 disabled
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   3 disabled
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   4 disabled
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   5 disabled
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   6 disabled
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   7 disabled
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [c00ff780]
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]  [mem 0x00000000-0x001fffff] page 4k
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]  [mem 0x00200000-0x379fffff] page 2M
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] RAMDISK: [mem 0x36244000-0x37119fff]
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: RSDP 000faf80 00014 (v00 ACPIAM)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: RSDT 7ffb0000 00044 (v01 083010 RSDT1638 20100830 MSFT 00000097)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: FACP 7ffb0200 00084 (v01 083010 FACP1638 20100830 MSFT 00000097)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20120320/tbfadt-579)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: DSDT 7ffb0450 0A1DA (v01  88PCP 88PCP830 00000002 INTL 20051117)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: FACS 7ffbe000 00040
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: APIC 7ffb0390 0007C (v01 083010 APIC1638 20100830 MSFT 00000097)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: MCFG 7ffb0410 0003C (v01 083010 OEMMCFG  20100830 MSFT 00000097)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: OEMB 7ffbe040 00072 (v01 083010 OEMB1638 20100830 MSFT 00000097)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: SRAT 7ffba630 00090 (v03 AMD    FAM_F_10 00000002 AMD  00000001)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: MSCT 7ffba6c0 0004E (v01 A M I  OEMBOARD 00000001 AMD  00000001)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: HPET 7ffba710 00038 (v01 083010 OEMHPET  20100830 MSFT 00000097)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: SSDT 7ffba750 0023E (v01 A M I  POWERNOW 00000001 AMD  00000001)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] 1155MB HIGHMEM available.
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] 891MB LOWMEM available.
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   low ram: 0 - 37bfe000
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Zone ranges:
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   HighMem  [mem 0x37bfe000-0x7ffaffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Movable zone start for each node
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Early memory node ranges
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   node   0: [mem 0x00010000-0x0009efff]
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   node   0: [mem 0x00100000-0x7ffaffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] On node 0 totalpages: 524095
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] free_area_init_node: node 0, pgdat c18c85c0, node_mem_map f5244200
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   HighMem zone: 2312 pages used for memmap
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]   HighMem zone: 293546 pages, LIFO batch:31
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Using APIC driver default
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] SMP: Allowing 6 CPUs, 5 hotplug CPUs
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] nr_irqs_gsi: 40
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] e820: [mem 0x80000000-0xffefffff] available for PCI devices
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:6 nr_node_ids:1
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f7b9d000 s34176 r0 d23168 u57344
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] pcpu-alloc: s34176 r0 d23168 u57344 alloc=14*4096
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 [0] 4 [0] 5 
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519999
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-43-generic root=UUID=a5baa10f-bb69-49cc-998b-f6e8c4f55e7d ro quiet splash
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] __ex_table already sorted, skipping sort
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Initializing CPU#0
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] allocated 4193536 bytes of page_cgroup
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:0007ffb0)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Memory: 2048744k/2096832k available (6059k kernel code, 47636k reserved, 2985k data, 764k init, 1183432k highmem)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] virtual kernel memory layout:
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]       .init : 0xc18d6000 - 0xc1995000   ( 764 kB)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]       .data : 0xc15eaf15 - 0xc18d54c0   (2985 kB)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]       .text : 0xc1000000 - 0xc15eaf15   (6059 kB)
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Hierarchical RCU implementation.
Dec 15 15:13:01 zack-A880G kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] NR_IRQS:2304 nr_irqs:728 16
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] CPU 0 irqstacks, hard=f4c0a000 soft=f4c0c000
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Console: colour VGA+ 80x25
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] console [tty0] enabled
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] hpet clockevent registered
Dec 15 15:13:01 zack-A880G kernel: [    0.000000] Fast TSC calibration using PIT
Dec 15 15:13:01 zack-A880G kernel: [    0.004000] Detected 2800.134 MHz processor.
Dec 15 15:13:01 zack-A880G kernel: [    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 5600.26 BogoMIPS (lpj=11200536)
Dec 15 15:13:01 zack-A880G kernel: [    0.000004] pid_max: default: 32768 minimum: 301
Dec 15 15:13:01 zack-A880G kernel: [    0.000024] Security Framework initialized
Dec 15 15:13:01 zack-A880G kernel: [    0.000038] AppArmor: AppArmor initialized
Dec 15 15:13:01 zack-A880G kernel: [    0.000039] Yama: becoming mindful.
Dec 15 15:13:01 zack-A880G kernel: [    0.000084] Mount-cache hash table entries: 512
Dec 15 15:13:01 zack-A880G kernel: [    0.000254] Initializing cgroup subsys cpuacct
Dec 15 15:13:01 zack-A880G kernel: [    0.000256] Initializing cgroup subsys memory
Dec 15 15:13:01 zack-A880G kernel: [    0.000262] Initializing cgroup subsys devices
Dec 15 15:13:01 zack-A880G kernel: [    0.000264] Initializing cgroup subsys freezer
Dec 15 15:13:01 zack-A880G kernel: [    0.000265] Initializing cgroup subsys blkio
Dec 15 15:13:01 zack-A880G kernel: [    0.000267] Initializing cgroup subsys perf_event
Dec 15 15:13:01 zack-A880G kernel: [    0.000287] mce: CPU supports 6 MCE banks
Dec 15 15:13:01 zack-A880G kernel: [    0.000292] LVT offset 0 assigned for vector 0xf9
Dec 15 15:13:01 zack-A880G kernel: [    0.000472] SMP alternatives: switching to UP code
Dec 15 15:13:01 zack-A880G kernel: [    0.007117] ACPI: Core revision 20120320
Dec 15 15:13:01 zack-A880G kernel: [    0.018109] ftrace: allocating 27161 entries in 54 pages
Dec 15 15:13:01 zack-A880G kernel: [    0.027374] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 15 15:13:01 zack-A880G kernel: [    0.027723] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 15 15:13:01 zack-A880G kernel: [    0.067332] CPU0: AMD Sempron(tm) 145 Processor stepping 03
Dec 15 15:13:01 zack-A880G kernel: [    0.174838] Performance Events: AMD PMU driver.
Dec 15 15:13:01 zack-A880G kernel: [    0.174842] ... version:                0
Dec 15 15:13:01 zack-A880G kernel: [    0.174843] ... bit width:              48
Dec 15 15:13:01 zack-A880G kernel: [    0.174844] ... generic registers:      4
Dec 15 15:13:01 zack-A880G kernel: [    0.174845] ... value mask:             0000ffffffffffff
Dec 15 15:13:01 zack-A880G kernel: [    0.174846] ... max period:             00007fffffffffff
Dec 15 15:13:01 zack-A880G kernel: [    0.174847] ... fixed-purpose events:   0
Dec 15 15:13:01 zack-A880G kernel: [    0.174848] ... event mask:             000000000000000f
Dec 15 15:13:01 zack-A880G kernel: [    0.174984] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Dec 15 15:13:01 zack-A880G kernel: [    0.175030] Brought up 1 CPUs
Dec 15 15:13:01 zack-A880G kernel: [    0.175032] Total of 1 processors activated (5600.26 BogoMIPS).
Dec 15 15:13:01 zack-A880G kernel: [    0.175485] devtmpfs: initialized
Dec 15 15:13:01 zack-A880G kernel: [    0.175603] EVM: security.selinux
Dec 15 15:13:01 zack-A880G kernel: [    0.175604] EVM: security.SMACK64
Dec 15 15:13:01 zack-A880G kernel: [    0.175605] EVM: security.capability
Dec 15 15:13:01 zack-A880G kernel: [    0.175646] PM: Registering ACPI NVS region [mem 0x7ffbe000-0x7ffdffff] (139264 bytes)
Dec 15 15:13:01 zack-A880G kernel: [    0.176405] dummy: 
Dec 15 15:13:01 zack-A880G kernel: [    0.176433] RTC time: 23:12:43, date: 12/15/13
Dec 15 15:13:01 zack-A880G kernel: [    0.176463] NET: Registered protocol family 16
Dec 15 15:13:01 zack-A880G kernel: [    0.176545] EISA bus registered
Dec 15 15:13:01 zack-A880G kernel: [    0.176549] node 0 link 0: io port [1000, ffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.176552] TOM: 0000000080000000 aka 2048M
Dec 15 15:13:01 zack-A880G kernel: [    0.176554] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.176556] node 0 link 0: mmio [a0000, bffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.176558] node 0 link 0: mmio [80000000, dfffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.176560] node 0 link 0: mmio [e0000000, efffffff] ==> none
Dec 15 15:13:01 zack-A880G kernel: [    0.176562] node 0 link 0: mmio [f0000000, ffefffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.176564] bus: [00, 07] on node 0 link 0
Dec 15 15:13:01 zack-A880G kernel: [    0.176565] bus: 00 [io  0x0000-0xffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.176567] bus: 00 [mem 0x000a0000-0x000bffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.176568] bus: 00 [mem 0x80000000-0xdfffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.176569] bus: 00 [mem 0xf0000000-0xfcffffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.176620] ACPI: bus type pci registered
Dec 15 15:13:01 zack-A880G kernel: [    0.176660] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Dec 15 15:13:01 zack-A880G kernel: [    0.176662] PCI: not using MMCONFIG
Dec 15 15:13:01 zack-A880G kernel: [    0.177239] PCI : PCI BIOS area is rw and x. Use pci=nobios if you want it NX.
Dec 15 15:13:01 zack-A880G kernel: [    0.177308] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
Dec 15 15:13:01 zack-A880G kernel: [    0.177309] PCI: Using configuration type 1 for base access
Dec 15 15:13:01 zack-A880G kernel: [    0.177310] PCI: Using configuration type 1 for extended access
Dec 15 15:13:01 zack-A880G kernel: [    0.177928] bio: create slab <bio-0> at 0
Dec 15 15:13:01 zack-A880G kernel: [    0.177991] ACPI: Added _OSI(Module Device)
Dec 15 15:13:01 zack-A880G kernel: [    0.177993] ACPI: Added _OSI(Processor Device)
Dec 15 15:13:01 zack-A880G kernel: [    0.177994] ACPI: Added _OSI(3.0 _SCP Extensions)
Dec 15 15:13:01 zack-A880G kernel: [    0.177995] ACPI: Added _OSI(Processor Aggregator Device)
Dec 15 15:13:01 zack-A880G kernel: [    0.178559] ACPI: EC: Look up EC in DSDT
Dec 15 15:13:01 zack-A880G kernel: [    0.179773] ACPI: Executed 4 blocks of module-level executable AML code
Dec 15 15:13:01 zack-A880G kernel: [    0.182634] ACPI: Interpreter enabled
Dec 15 15:13:01 zack-A880G kernel: [    0.182639] ACPI: (supports S0 S1 S4 S5)
Dec 15 15:13:01 zack-A880G kernel: [    0.182655] ACPI: Using IOAPIC for interrupt routing
Dec 15 15:13:01 zack-A880G kernel: [    0.182670] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Dec 15 15:13:01 zack-A880G kernel: [    0.183892] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Dec 15 15:13:01 zack-A880G kernel: [    0.183893] PCI: Using MMCONFIG for extended config space
Dec 15 15:13:01 zack-A880G kernel: [    0.188465] ACPI: No dock devices found.
Dec 15 15:13:01 zack-A880G kernel: [    0.188469] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Dec 15 15:13:01 zack-A880G kernel: [    0.188530] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Dec 15 15:13:01 zack-A880G kernel: [    0.188635] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Dec 15 15:13:01 zack-A880G kernel: [    0.188638] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.188640] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.188642] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.188644] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xdfffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.188645] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.188669] PCI host bridge to bus 0000:00
Dec 15 15:13:01 zack-A880G kernel: [    0.188671] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Dec 15 15:13:01 zack-A880G kernel: [    0.188673] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.188675] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.188677] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.188679] pci_bus 0000:00: root bus resource [mem 0x80000000-0xdfffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.188681] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.188691] pci 0000:00:00.0: [1022:9601] type 00 class 0x060000
Dec 15 15:13:01 zack-A880G kernel: [    0.188738] pci 0000:00:02.0: [1022:9603] type 01 class 0x060400
Dec 15 15:13:01 zack-A880G kernel: [    0.188768] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Dec 15 15:13:01 zack-A880G kernel: [    0.188795] pci 0000:00:07.0: [1022:9607] type 01 class 0x060400
Dec 15 15:13:01 zack-A880G kernel: [    0.188824] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Dec 15 15:13:01 zack-A880G kernel: [    0.188864] pci 0000:00:11.0: [1002:4390] type 00 class 0x01018f
Dec 15 15:13:01 zack-A880G kernel: [    0.188883] pci 0000:00:11.0: reg 10: [io  0xb000-0xb007]
Dec 15 15:13:01 zack-A880G kernel: [    0.188892] pci 0000:00:11.0: reg 14: [io  0xa000-0xa003]
Dec 15 15:13:01 zack-A880G kernel: [    0.188901] pci 0000:00:11.0: reg 18: [io  0x9000-0x9007]
Dec 15 15:13:01 zack-A880G kernel: [    0.188910] pci 0000:00:11.0: reg 1c: [io  0x8000-0x8003]
Dec 15 15:13:01 zack-A880G kernel: [    0.188919] pci 0000:00:11.0: reg 20: [io  0x7000-0x700f]
Dec 15 15:13:01 zack-A880G kernel: [    0.188929] pci 0000:00:11.0: reg 24: [mem 0xfeaffc00-0xfeafffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.188948] pci 0000:00:11.0: set SATA to AHCI mode
Dec 15 15:13:01 zack-A880G kernel: [    0.188992] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
Dec 15 15:13:01 zack-A880G kernel: [    0.189005] pci 0000:00:12.0: reg 10: [mem 0xfeafe000-0xfeafefff]
Dec 15 15:13:01 zack-A880G kernel: [    0.189067] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
Dec 15 15:13:01 zack-A880G kernel: [    0.189079] pci 0000:00:12.1: reg 10: [mem 0xfeafd000-0xfeafdfff]
Dec 15 15:13:01 zack-A880G kernel: [    0.189146] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
Dec 15 15:13:01 zack-A880G kernel: [    0.189164] pci 0000:00:12.2: reg 10: [mem 0xfeaff800-0xfeaff8ff]
Dec 15 15:13:01 zack-A880G kernel: [    0.189243] pci 0000:00:12.2: supports D1 D2
Dec 15 15:13:01 zack-A880G kernel: [    0.189245] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Dec 15 15:13:01 zack-A880G kernel: [    0.189266] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
Dec 15 15:13:01 zack-A880G kernel: [    0.189279] pci 0000:00:13.0: reg 10: [mem 0xfeafc000-0xfeafcfff]
Dec 15 15:13:01 zack-A880G kernel: [    0.189341] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
Dec 15 15:13:01 zack-A880G kernel: [    0.189354] pci 0000:00:13.1: reg 10: [mem 0xfeafb000-0xfeafbfff]
Dec 15 15:13:01 zack-A880G kernel: [    0.189420] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
Dec 15 15:13:01 zack-A880G kernel: [    0.189438] pci 0000:00:13.2: reg 10: [mem 0xfeaff400-0xfeaff4ff]
Dec 15 15:13:01 zack-A880G kernel: [    0.189518] pci 0000:00:13.2: supports D1 D2
Dec 15 15:13:01 zack-A880G kernel: [    0.189519] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Dec 15 15:13:01 zack-A880G kernel: [    0.189543] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
Dec 15 15:13:01 zack-A880G kernel: [    0.189638] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
Dec 15 15:13:01 zack-A880G kernel: [    0.189654] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Dec 15 15:13:01 zack-A880G kernel: [    0.189663] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Dec 15 15:13:01 zack-A880G kernel: [    0.189672] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Dec 15 15:13:01 zack-A880G kernel: [    0.189681] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Dec 15 15:13:01 zack-A880G kernel: [    0.189690] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
Dec 15 15:13:01 zack-A880G kernel: [    0.189748] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
Dec 15 15:13:01 zack-A880G kernel: [    0.189768] pci 0000:00:14.2: reg 10: [mem 0xfeaf4000-0xfeaf7fff 64bit]
Dec 15 15:13:01 zack-A880G kernel: [    0.189832] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Dec 15 15:13:01 zack-A880G kernel: [    0.189847] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
Dec 15 15:13:01 zack-A880G kernel: [    0.189920] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
Dec 15 15:13:01 zack-A880G kernel: [    0.189960] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
Dec 15 15:13:01 zack-A880G kernel: [    0.189972] pci 0000:00:14.5: reg 10: [mem 0xfeafa000-0xfeafafff]
Dec 15 15:13:01 zack-A880G kernel: [    0.190036] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
Dec 15 15:13:01 zack-A880G kernel: [    0.190050] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
Dec 15 15:13:01 zack-A880G kernel: [    0.190060] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
Dec 15 15:13:01 zack-A880G kernel: [    0.190072] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
Dec 15 15:13:01 zack-A880G kernel: [    0.190085] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
Dec 15 15:13:01 zack-A880G kernel: [    0.190129] pci 0000:01:00.0: [10de:0de1] type 00 class 0x030000
Dec 15 15:13:01 zack-A880G kernel: [    0.190139] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.190149] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
Dec 15 15:13:01 zack-A880G kernel: [    0.190158] pci 0000:01:00.0: reg 1c: [mem 0xd6000000-0xd7ffffff 64bit pref]
Dec 15 15:13:01 zack-A880G kernel: [    0.190165] pci 0000:01:00.0: reg 24: [io  0xc800-0xc87f]
Dec 15 15:13:01 zack-A880G kernel: [    0.190172] pci 0000:01:00.0: reg 30: [mem 0xfcf80000-0xfcffffff pref]
Dec 15 15:13:01 zack-A880G kernel: [    0.190223] pci 0000:01:00.1: [10de:0bea] type 00 class 0x040300
Dec 15 15:13:01 zack-A880G kernel: [    0.190233] pci 0000:01:00.1: reg 10: [mem 0xfcf7c000-0xfcf7ffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.194836] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Dec 15 15:13:01 zack-A880G kernel: [    0.194843] pci 0000:00:02.0:   bridge window [io  0xc000-0xcfff]
Dec 15 15:13:01 zack-A880G kernel: [    0.194847] pci 0000:00:02.0:   bridge window [mem 0xfcf00000-0xfdffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.194850] pci 0000:00:02.0:   bridge window [mem 0xd6000000-0xdfffffff 64bit pref]
Dec 15 15:13:01 zack-A880G kernel: [    0.194887] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
Dec 15 15:13:01 zack-A880G kernel: [    0.194901] pci 0000:02:00.0: reg 10: [io  0xd800-0xd8ff]
Dec 15 15:13:01 zack-A880G kernel: [    0.194920] pci 0000:02:00.0: reg 18: [mem 0xfbffb000-0xfbffbfff 64bit pref]
Dec 15 15:13:01 zack-A880G kernel: [    0.194933] pci 0000:02:00.0: reg 20: [mem 0xfbffc000-0xfbffffff 64bit pref]
Dec 15 15:13:01 zack-A880G kernel: [    0.194942] pci 0000:02:00.0: reg 30: [mem 0xfebe0000-0xfebfffff pref]
Dec 15 15:13:01 zack-A880G kernel: [    0.194988] pci 0000:02:00.0: supports D1 D2
Dec 15 15:13:01 zack-A880G kernel: [    0.194990] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 15 15:13:01 zack-A880G kernel: [    0.202820] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Dec 15 15:13:01 zack-A880G kernel: [    0.202826] pci 0000:00:07.0:   bridge window [io  0xd000-0xdfff]
Dec 15 15:13:01 zack-A880G kernel: [    0.202829] pci 0000:00:07.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.202833] pci 0000:00:07.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
Dec 15 15:13:01 zack-A880G kernel: [    0.202873] pci 0000:03:06.0: [1274:1371] type 00 class 0x040100
Dec 15 15:13:01 zack-A880G kernel: [    0.202895] pci 0000:03:06.0: reg 10: [io  0xe800-0xe83f]
Dec 15 15:13:01 zack-A880G kernel: [    0.202992] pci 0000:03:06.0: supports D2
Dec 15 15:13:01 zack-A880G kernel: [    0.202993] pci 0000:03:06.0: PME# supported from D0 D2 D3hot
Dec 15 15:13:01 zack-A880G kernel: [    0.203041] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
Dec 15 15:13:01 zack-A880G kernel: [    0.203045] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
Dec 15 15:13:01 zack-A880G kernel: [    0.203051] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Dec 15 15:13:01 zack-A880G kernel: [    0.203053] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Dec 15 15:13:01 zack-A880G kernel: [    0.203055] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Dec 15 15:13:01 zack-A880G kernel: [    0.203057] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
Dec 15 15:13:01 zack-A880G kernel: [    0.203058] pci 0000:00:14.4:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
Dec 15 15:13:01 zack-A880G kernel: [    0.203060] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
Dec 15 15:13:01 zack-A880G kernel: [    0.203071] pci_bus 0000:00: on NUMA node 0
Dec 15 15:13:01 zack-A880G kernel: [    0.203076] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 15 15:13:01 zack-A880G kernel: [    0.203252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Dec 15 15:13:01 zack-A880G kernel: [    0.203279] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Dec 15 15:13:01 zack-A880G kernel: [    0.203316] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
Dec 15 15:13:01 zack-A880G kernel: [    0.203375]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Dec 15 15:13:01 zack-A880G kernel: [    0.203377]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Dec 15 15:13:01 zack-A880G kernel: [    0.203378] ACPI _OSC control for PCIe not granted, disabling ASPM
Dec 15 15:13:01 zack-A880G kernel: [    0.206367] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 12 14 15)
Dec 15 15:13:01 zack-A880G kernel: [    0.206398] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
Dec 15 15:13:01 zack-A880G kernel: [    0.206426] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
Dec 15 15:13:01 zack-A880G kernel: [    0.206452] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
Dec 15 15:13:01 zack-A880G kernel: [    0.206479] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Dec 15 15:13:01 zack-A880G kernel: [    0.206506] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 *10 11 12 14 15)
Dec 15 15:13:01 zack-A880G kernel: [    0.206533] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 *9 12 14 15)
Dec 15 15:13:01 zack-A880G kernel: [    0.206559] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Dec 15 15:13:01 zack-A880G kernel: [    0.206637] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Dec 15 15:13:01 zack-A880G kernel: [    0.206638] vgaarb: loaded
Dec 15 15:13:01 zack-A880G kernel: [    0.206639] vgaarb: bridge control possible 0000:01:00.0
Dec 15 15:13:01 zack-A880G kernel: [    0.206774] SCSI subsystem initialized
Dec 15 15:13:01 zack-A880G kernel: [    0.206808] libata version 3.00 loaded.
Dec 15 15:13:01 zack-A880G kernel: [    0.206822] ACPI: bus type usb registered
Dec 15 15:13:01 zack-A880G kernel: [    0.206837] usbcore: registered new interface driver usbfs
Dec 15 15:13:01 zack-A880G kernel: [    0.206844] usbcore: registered new interface driver hub
Dec 15 15:13:01 zack-A880G kernel: [    0.206858] usbcore: registered new device driver usb
Dec 15 15:13:01 zack-A880G kernel: [    0.206911] PCI: Using ACPI for IRQ routing
Dec 15 15:13:01 zack-A880G kernel: [    0.206914] PCI: pci_cache_line_size set to 64 bytes
Dec 15 15:13:01 zack-A880G kernel: [    0.206977] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.206979] e820: reserve RAM buffer [mem 0x7ffb0000-0x7fffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.207046] NetLabel: Initializing
Dec 15 15:13:01 zack-A880G kernel: [    0.207047] NetLabel:  domain hash size = 128
Dec 15 15:13:01 zack-A880G kernel: [    0.207048] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 15 15:13:01 zack-A880G kernel: [    0.207055] NetLabel:  unlabeled traffic allowed by default
Dec 15 15:13:01 zack-A880G kernel: [    0.207116] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Dec 15 15:13:01 zack-A880G kernel: [    0.207119] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Dec 15 15:13:01 zack-A880G kernel: [    0.209139] Switching to clocksource hpet
Dec 15 15:13:01 zack-A880G kernel: [    0.213765] AppArmor: AppArmor Filesystem Enabled
Dec 15 15:13:01 zack-A880G kernel: [    0.213790] pnp: PnP ACPI init
Dec 15 15:13:01 zack-A880G kernel: [    0.213804] ACPI: bus type pnp registered
Dec 15 15:13:01 zack-A880G kernel: [    0.213903] pnp 00:00: [bus 00-ff]
Dec 15 15:13:01 zack-A880G kernel: [    0.213905] pnp 00:00: [io  0x0cf8-0x0cff]
Dec 15 15:13:01 zack-A880G kernel: [    0.213907] pnp 00:00: [io  0x0000-0x0cf7 window]
Dec 15 15:13:01 zack-A880G kernel: [    0.213909] pnp 00:00: [io  0x0d00-0xffff window]
Dec 15 15:13:01 zack-A880G kernel: [    0.213911] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Dec 15 15:13:01 zack-A880G kernel: [    0.213913] pnp 00:00: [mem 0x000d0000-0x000dffff window]
Dec 15 15:13:01 zack-A880G kernel: [    0.213914] pnp 00:00: [mem 0x80000000-0xdfffffff window]
Dec 15 15:13:01 zack-A880G kernel: [    0.213916] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
Dec 15 15:13:01 zack-A880G kernel: [    0.213955] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Dec 15 15:13:01 zack-A880G kernel: [    0.214027] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Dec 15 15:13:01 zack-A880G kernel: [    0.214029] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Dec 15 15:13:01 zack-A880G kernel: [    0.214066] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 15 15:13:01 zack-A880G kernel: [    0.214099] pnp 00:02: [dma 4]
Dec 15 15:13:01 zack-A880G kernel: [    0.214100] pnp 00:02: [io  0x0000-0x000f]
Dec 15 15:13:01 zack-A880G kernel: [    0.214102] pnp 00:02: [io  0x0081-0x0083]
Dec 15 15:13:01 zack-A880G kernel: [    0.214104] pnp 00:02: [io  0x0087]
Dec 15 15:13:01 zack-A880G kernel: [    0.214105] pnp 00:02: [io  0x0089-0x008b]
Dec 15 15:13:01 zack-A880G kernel: [    0.214107] pnp 00:02: [io  0x008f]
Dec 15 15:13:01 zack-A880G kernel: [    0.214108] pnp 00:02: [io  0x00c0-0x00df]
Dec 15 15:13:01 zack-A880G kernel: [    0.214126] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Dec 15 15:13:01 zack-A880G kernel: [    0.214133] pnp 00:03: [io  0x0070-0x0071]
Dec 15 15:13:01 zack-A880G kernel: [    0.214145] pnp 00:03: [irq 8]
Dec 15 15:13:01 zack-A880G kernel: [    0.214162] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Dec 15 15:13:01 zack-A880G kernel: [    0.214167] pnp 00:04: [io  0x0061]
Dec 15 15:13:01 zack-A880G kernel: [    0.214186] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Dec 15 15:13:01 zack-A880G kernel: [    0.214192] pnp 00:05: [io  0x00f0-0x00ff]
Dec 15 15:13:01 zack-A880G kernel: [    0.214199] pnp 00:05: [irq 13]
Dec 15 15:13:01 zack-A880G kernel: [    0.214216] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Dec 15 15:13:01 zack-A880G kernel: [    0.214603] pnp 00:06: [io  0x03f8-0x03ff]
Dec 15 15:13:01 zack-A880G kernel: [    0.214606] pnp 00:06: [irq 4]
Dec 15 15:13:01 zack-A880G kernel: [    0.214608] pnp 00:06: [dma 0 disabled]
Dec 15 15:13:01 zack-A880G kernel: [    0.214675] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
Dec 15 15:13:01 zack-A880G kernel: [    0.215388] pnp 00:07: [io  0x0378-0x037f]
Dec 15 15:13:01 zack-A880G kernel: [    0.215391] pnp 00:07: [irq 7]
Dec 15 15:13:01 zack-A880G kernel: [    0.215393] pnp 00:07: [dma 0 disabled]
Dec 15 15:13:01 zack-A880G kernel: [    0.215583] pnp 00:07: Plug and Play ACPI device, IDs PNP0400 (active)
Dec 15 15:13:01 zack-A880G kernel: [    0.215766] pnp 00:08: [mem 0xfed00000-0xfed003ff]
Dec 15 15:13:01 zack-A880G kernel: [    0.215785] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (active)
Dec 15 15:13:01 zack-A880G kernel: [    0.215840] pnp 00:09: [io  0x0060]
Dec 15 15:13:01 zack-A880G kernel: [    0.215842] pnp 00:09: [io  0x0064]
Dec 15 15:13:01 zack-A880G kernel: [    0.215844] pnp 00:09: [mem 0xfec00000-0xfec00fff]
Dec 15 15:13:01 zack-A880G kernel: [    0.215845] pnp 00:09: [mem 0xfee00000-0xfee00fff]
Dec 15 15:13:01 zack-A880G kernel: [    0.215876] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.215878] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.215880] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 15 15:13:01 zack-A880G kernel: [    0.215982] pnp 00:0a: [io  0x0010-0x001f]
Dec 15 15:13:01 zack-A880G kernel: [    0.215984] pnp 00:0a: [io  0x0022-0x003f]
Dec 15 15:13:01 zack-A880G kernel: [    0.215985] pnp 00:0a: [io  0x0062-0x0063]
Dec 15 15:13:01 zack-A880G kernel: [    0.215987] pnp 00:0a: [io  0x0065-0x006f]
Dec 15 15:13:01 zack-A880G kernel: [    0.215988] pnp 00:0a: [io  0x0072-0x007f]
Dec 15 15:13:01 zack-A880G kernel: [    0.215990] pnp 00:0a: [io  0x0080]
Dec 15 15:13:01 zack-A880G kernel: [    0.215991] pnp 00:0a: [io  0x0084-0x0086]
Dec 15 15:13:01 zack-A880G kernel: [    0.215993] pnp 00:0a: [io  0x0088]
Dec 15 15:13:01 zack-A880G kernel: [    0.215994] pnp 00:0a: [io  0x008c-0x008e]
Dec 15 15:13:01 zack-A880G kernel: [    0.215996] pnp 00:0a: [io  0x0090-0x009f]
Dec 15 15:13:01 zack-A880G kernel: [    0.215998] pnp 00:0a: [io  0x00a2-0x00bf]
Dec 15 15:13:01 zack-A880G kernel: [    0.215999] pnp 00:0a: [io  0x00b1]
Dec 15 15:13:01 zack-A880G kernel: [    0.216001] pnp 00:0a: [io  0x00e0-0x00ef]
Dec 15 15:13:01 zack-A880G kernel: [    0.216002] pnp 00:0a: [io  0x04d0-0x04d1]
Dec 15 15:13:01 zack-A880G kernel: [    0.216004] pnp 00:0a: [io  0x040b]
Dec 15 15:13:01 zack-A880G kernel: [    0.216005] pnp 00:0a: [io  0x04d6]
Dec 15 15:13:01 zack-A880G kernel: [    0.216007] pnp 00:0a: [io  0x0c00-0x0c01]
Dec 15 15:13:01 zack-A880G kernel: [    0.216008] pnp 00:0a: [io  0x0c14]
Dec 15 15:13:01 zack-A880G kernel: [    0.216010] pnp 00:0a: [io  0x0c50-0x0c51]
Dec 15 15:13:01 zack-A880G kernel: [    0.216011] pnp 00:0a: [io  0x0c52]
Dec 15 15:13:01 zack-A880G kernel: [    0.216013] pnp 00:0a: [io  0x0c6c]
Dec 15 15:13:01 zack-A880G kernel: [    0.216014] pnp 00:0a: [io  0x0c6f]
Dec 15 15:13:01 zack-A880G kernel: [    0.216016] pnp 00:0a: [io  0x0cd0-0x0cd1]
Dec 15 15:13:01 zack-A880G kernel: [    0.216017] pnp 00:0a: [io  0x0cd2-0x0cd3]
Dec 15 15:13:01 zack-A880G kernel: [    0.216019] pnp 00:0a: [io  0x0cd4-0x0cd5]
Dec 15 15:13:01 zack-A880G kernel: [    0.216021] pnp 00:0a: [io  0x0cd6-0x0cd7]
Dec 15 15:13:01 zack-A880G kernel: [    0.216022] pnp 00:0a: [io  0x0cd8-0x0cdf]
Dec 15 15:13:01 zack-A880G kernel: [    0.216024] pnp 00:0a: [io  0x0800-0x089f]
Dec 15 15:13:01 zack-A880G kernel: [    0.216026] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
Dec 15 15:13:01 zack-A880G kernel: [    0.216028] pnp 00:0a: [io  0x0b00-0x0b0f]
Dec 15 15:13:01 zack-A880G kernel: [    0.216030] pnp 00:0a: [io  0x0b20-0x0b3f]
Dec 15 15:13:01 zack-A880G kernel: [    0.216032] pnp 00:0a: [io  0x0900-0x090f]
Dec 15 15:13:01 zack-A880G kernel: [    0.216033] pnp 00:0a: [io  0x0910-0x091f]
Dec 15 15:13:01 zack-A880G kernel: [    0.216035] pnp 00:0a: [io  0xfe00-0xfefe]
Dec 15 15:13:01 zack-A880G kernel: [    0.216036] pnp 00:0a: [io  0x0060]
Dec 15 15:13:01 zack-A880G kernel: [    0.216038] pnp 00:0a: [io  0x0064]
Dec 15 15:13:01 zack-A880G kernel: [    0.216039] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.216041] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
Dec 15 15:13:01 zack-A880G kernel: [    0.216100] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216102] system 00:0a: [io  0x040b] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216104] system 00:0a: [io  0x04d6] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216106] system 00:0a: [io  0x0c00-0x0c01] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216108] system 00:0a: [io  0x0c14] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216110] system 00:0a: [io  0x0c50-0x0c51] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216112] system 00:0a: [io  0x0c52] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216114] system 00:0a: [io  0x0c6c] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216115] system 00:0a: [io  0x0c6f] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216117] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216119] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216121] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216123] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216125] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216127] system 00:0a: [io  0x0800-0x089f] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216129] system 00:0a: [io  0x0b00-0x0b0f] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216131] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216133] system 00:0a: [io  0x0900-0x090f] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216135] system 00:0a: [io  0x0910-0x091f] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216137] system 00:0a: [io  0xfe00-0xfefe] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216140] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216142] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216144] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 15 15:13:01 zack-A880G kernel: [    0.216266] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
Dec 15 15:13:01 zack-A880G kernel: [    0.216268] pnp 00:0b: [io  0x0e00-0x0e0f]
Dec 15 15:13:01 zack-A880G kernel: [    0.216269] pnp 00:0b: [io  0x0e80-0x0e8f]
Dec 15 15:13:01 zack-A880G kernel: [    0.216271] pnp 00:0b: [io  0x0f40-0x0f4f]
Dec 15 15:13:01 zack-A880G kernel: [    0.216272] pnp 00:0b: [io  0x0a30-0x0a3f]
Dec 15 15:13:01 zack-A880G kernel: [    0.216303] system 00:0b: [io  0x0e00-0x0e0f] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216305] system 00:0b: [io  0x0e80-0x0e8f] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216307] system 00:0b: [io  0x0f40-0x0f4f] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216309] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216312] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 15 15:13:01 zack-A880G kernel: [    0.216334] pnp 00:0c: [mem 0xe0000000-0xefffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.216362] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216364] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 15 15:13:01 zack-A880G kernel: [    0.216554] pnp 00:0d: [mem 0x00000000-0x0009ffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.216556] pnp 00:0d: [mem 0x000c0000-0x000cffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.216558] pnp 00:0d: [mem 0x000e0000-0x000fffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.216559] pnp 00:0d: [mem 0x00100000-0x7fffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.216561] pnp 00:0d: [mem 0xfec00000-0xffffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.216595] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216597] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216599] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216601] system 00:0d: [mem 0x00100000-0x7fffffff] could not be reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216604] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
Dec 15 15:13:01 zack-A880G kernel: [    0.216606] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
Dec 15 15:13:01 zack-A880G kernel: [    0.216685] pnp: PnP ACPI: found 14 devices
Dec 15 15:13:01 zack-A880G kernel: [    0.216687] ACPI: ACPI bus type pnp unregistered
Dec 15 15:13:01 zack-A880G kernel: [    0.216689] PnPBIOS: Disabled by ACPI PNP
Dec 15 15:13:01 zack-A880G kernel: [    0.252171] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Dec 15 15:13:01 zack-A880G kernel: [    0.252174] pci 0000:00:02.0:   bridge window [io  0xc000-0xcfff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252177] pci 0000:00:02.0:   bridge window [mem 0xfcf00000-0xfdffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252180] pci 0000:00:02.0:   bridge window [mem 0xd6000000-0xdfffffff 64bit pref]
Dec 15 15:13:01 zack-A880G kernel: [    0.252183] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Dec 15 15:13:01 zack-A880G kernel: [    0.252186] pci 0000:00:07.0:   bridge window [io  0xd000-0xdfff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252188] pci 0000:00:07.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252191] pci 0000:00:07.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
Dec 15 15:13:01 zack-A880G kernel: [    0.252194] pci 0000:00:14.4: PCI bridge to [bus 03-03]
Dec 15 15:13:01 zack-A880G kernel: [    0.252197] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252225] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Dec 15 15:13:01 zack-A880G kernel: [    0.252227] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252229] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252231] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252233] pci_bus 0000:00: resource 8 [mem 0x80000000-0xdfffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252235] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252237] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252239] pci_bus 0000:01: resource 1 [mem 0xfcf00000-0xfdffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252241] pci_bus 0000:01: resource 2 [mem 0xd6000000-0xdfffffff 64bit pref]
Dec 15 15:13:01 zack-A880G kernel: [    0.252243] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252244] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252247] pci_bus 0000:02: resource 2 [mem 0xfbf00000-0xfbffffff 64bit pref]
Dec 15 15:13:01 zack-A880G kernel: [    0.252248] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252250] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
Dec 15 15:13:01 zack-A880G kernel: [    0.252252] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252254] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252256] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252258] pci_bus 0000:03: resource 8 [mem 0x80000000-0xdfffffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252259] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
Dec 15 15:13:01 zack-A880G kernel: [    0.252286] NET: Registered protocol family 2
Dec 15 15:13:01 zack-A880G kernel: [    0.252331] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 15 15:13:01 zack-A880G kernel: [    0.252438] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 15 15:13:01 zack-A880G kernel: [    0.252869] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 15 15:13:01 zack-A880G kernel: [    0.253122] TCP: Hash tables configured (established 131072 bind 65536)
Dec 15 15:13:01 zack-A880G kernel: [    0.253124] TCP: reno registered
Dec 15 15:13:01 zack-A880G kernel: [    0.253126] UDP hash table entries: 512 (order: 2, 16384 bytes)
Dec 15 15:13:01 zack-A880G kernel: [    0.253134] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Dec 15 15:13:01 zack-A880G kernel: [    0.253199] NET: Registered protocol family 1
Dec 15 15:13:01 zack-A880G kernel: [    1.279174] pci 0000:01:00.0: Boot video device
Dec 15 15:13:01 zack-A880G kernel: [    1.279190] PCI: CLS 64 bytes, default 64
Dec 15 15:13:01 zack-A880G kernel: [    1.279355] LVT offset 1 assigned for vector 0x400
Dec 15 15:13:01 zack-A880G kernel: [    1.279361] IBS: LVT offset 1 assigned
Dec 15 15:13:01 zack-A880G kernel: [    1.279377] perf: AMD IBS detected (0x0000001f)
Dec 15 15:13:01 zack-A880G kernel: [    1.279486] audit: initializing netlink socket (disabled)
Dec 15 15:13:01 zack-A880G kernel: [    1.279493] type=2000 audit(1387149164.168:1): initialized
Dec 15 15:13:01 zack-A880G kernel: [    1.297170] Trying to unpack rootfs image as initramfs...
Dec 15 15:13:01 zack-A880G kernel: [    1.319577] highmem bounce pool size: 64 pages
Dec 15 15:13:01 zack-A880G kernel: [    1.319590] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 15 15:13:01 zack-A880G kernel: [    1.331087] VFS: Disk quotas dquot_6.5.2
Dec 15 15:13:01 zack-A880G kernel: [    1.331133] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 15 15:13:01 zack-A880G kernel: [    1.331542] fuse init (API version 7.19)
Dec 15 15:13:01 zack-A880G kernel: [    1.331594] msgmni has been set to 1690
Dec 15 15:13:01 zack-A880G kernel: [    1.343068] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Dec 15 15:13:01 zack-A880G kernel: [    1.343104] io scheduler noop registered
Dec 15 15:13:01 zack-A880G kernel: [    1.343105] io scheduler deadline registered (default)
Dec 15 15:13:01 zack-A880G kernel: [    1.343110] io scheduler cfq registered
Dec 15 15:13:01 zack-A880G kernel: [    1.343217] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
Dec 15 15:13:01 zack-A880G kernel: [    1.343269] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
Dec 15 15:13:01 zack-A880G kernel: [    1.343312] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 15 15:13:01 zack-A880G kernel: [    1.343324] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 15 15:13:01 zack-A880G kernel: [    1.343416] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Dec 15 15:13:01 zack-A880G kernel: [    1.343421] ACPI: Power Button [PWRB]
Dec 15 15:13:01 zack-A880G kernel: [    1.343452] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Dec 15 15:13:01 zack-A880G kernel: [    1.343454] ACPI: Power Button [PWRF]
Dec 15 15:13:01 zack-A880G kernel: [    1.347152] thermal LNXTHERM:00: registered as thermal_zone0
Dec 15 15:13:01 zack-A880G kernel: [    1.347154] ACPI: Thermal Zone [THRM] (29 C)
Dec 15 15:13:01 zack-A880G kernel: [    1.347171] GHES: HEST is not enabled!
Dec 15 15:13:01 zack-A880G kernel: [    1.351144] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Dec 15 15:13:01 zack-A880G kernel: [    1.371566] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 15 15:13:01 zack-A880G kernel: [    1.371588] isapnp: Scanning for PnP cards...
Dec 15 15:13:01 zack-A880G kernel: [    1.459903] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 15 15:13:01 zack-A880G kernel: [    1.527041] Linux agpgart interface v0.103
Dec 15 15:13:01 zack-A880G kernel: [    1.528107] brd: module loaded
Dec 15 15:13:01 zack-A880G kernel: [    1.528572] loop: module loaded
Dec 15 15:13:01 zack-A880G kernel: [    1.528706] pata_acpi 0000:00:14.1: setting latency timer to 64
Dec 15 15:13:01 zack-A880G kernel: [    1.528894] Fixed MDIO Bus: probed
Dec 15 15:13:01 zack-A880G kernel: [    1.528925] tun: Universal TUN/TAP device driver, 1.6
Dec 15 15:13:01 zack-A880G kernel: [    1.528926] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 15 15:13:01 zack-A880G kernel: [    1.528950] PPP generic driver version 2.4.2
Dec 15 15:13:01 zack-A880G kernel: [    1.528974] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 15 15:13:01 zack-A880G kernel: [    1.528998] ehci_hcd 0000:00:12.2: EHCI Host Controller
Dec 15 15:13:01 zack-A880G kernel: [    1.529003] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Dec 15 15:13:01 zack-A880G kernel: [    1.529010] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Dec 15 15:13:01 zack-A880G kernel: [    1.529029] ehci_hcd 0000:00:12.2: debug port 1
Dec 15 15:13:01 zack-A880G kernel: [    1.529050] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfeaff800
Dec 15 15:13:01 zack-A880G kernel: [    1.538713] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Dec 15 15:13:01 zack-A880G kernel: [    1.538757] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Dec 15 15:13:01 zack-A880G kernel: [    1.538759] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:13:01 zack-A880G kernel: [    1.538761] usb usb1: Product: EHCI Host Controller
Dec 15 15:13:01 zack-A880G kernel: [    1.538763] usb usb1: Manufacturer: Linux 3.5.0-43-generic ehci_hcd
Dec 15 15:13:01 zack-A880G kernel: [    1.538765] usb usb1: SerialNumber: 0000:00:12.2
Dec 15 15:13:01 zack-A880G kernel: [    1.538853] hub 1-0:1.0: USB hub found
Dec 15 15:13:01 zack-A880G kernel: [    1.538857] hub 1-0:1.0: 6 ports detected
Dec 15 15:13:01 zack-A880G kernel: [    1.538940] ehci_hcd 0000:00:13.2: EHCI Host Controller
Dec 15 15:13:01 zack-A880G kernel: [    1.538945] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Dec 15 15:13:01 zack-A880G kernel: [    1.538951] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Dec 15 15:13:01 zack-A880G kernel: [    1.538972] ehci_hcd 0000:00:13.2: debug port 1
Dec 15 15:13:01 zack-A880G kernel: [    1.538994] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfeaff400
Dec 15 15:13:01 zack-A880G kernel: [    1.550745] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Dec 15 15:13:01 zack-A880G kernel: [    1.550767] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Dec 15 15:13:01 zack-A880G kernel: [    1.550769] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:13:01 zack-A880G kernel: [    1.550771] usb usb2: Product: EHCI Host Controller
Dec 15 15:13:01 zack-A880G kernel: [    1.550773] usb usb2: Manufacturer: Linux 3.5.0-43-generic ehci_hcd
Dec 15 15:13:01 zack-A880G kernel: [    1.550774] usb usb2: SerialNumber: 0000:00:13.2
Dec 15 15:13:01 zack-A880G kernel: [    1.550863] hub 2-0:1.0: USB hub found
Dec 15 15:13:01 zack-A880G kernel: [    1.550866] hub 2-0:1.0: 6 ports detected
Dec 15 15:13:01 zack-A880G kernel: [    1.550936] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 15 15:13:01 zack-A880G kernel: [    1.550988] ohci_hcd 0000:00:12.0: OHCI Host Controller
Dec 15 15:13:01 zack-A880G kernel: [    1.550993] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Dec 15 15:13:01 zack-A880G kernel: [    1.551017] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfeafe000
Dec 15 15:13:01 zack-A880G kernel: [    1.630615] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Dec 15 15:13:01 zack-A880G kernel: [    1.630619] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:13:01 zack-A880G kernel: [    1.630621] usb usb3: Product: OHCI Host Controller
Dec 15 15:13:01 zack-A880G kernel: [    1.630623] usb usb3: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
Dec 15 15:13:01 zack-A880G kernel: [    1.630625] usb usb3: SerialNumber: 0000:00:12.0
Dec 15 15:13:01 zack-A880G kernel: [    1.630720] hub 3-0:1.0: USB hub found
Dec 15 15:13:01 zack-A880G kernel: [    1.630726] hub 3-0:1.0: 3 ports detected
Dec 15 15:13:01 zack-A880G kernel: [    1.630790] ohci_hcd 0000:00:12.1: OHCI Host Controller
Dec 15 15:13:01 zack-A880G kernel: [    1.630795] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Dec 15 15:13:01 zack-A880G kernel: [    1.630812] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfeafd000
Dec 15 15:13:01 zack-A880G kernel: [    1.718511] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Dec 15 15:13:01 zack-A880G kernel: [    1.718515] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:13:01 zack-A880G kernel: [    1.718517] usb usb4: Product: OHCI Host Controller
Dec 15 15:13:01 zack-A880G kernel: [    1.718519] usb usb4: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
Dec 15 15:13:01 zack-A880G kernel: [    1.718521] usb usb4: SerialNumber: 0000:00:12.1
Dec 15 15:13:01 zack-A880G kernel: [    1.718607] hub 4-0:1.0: USB hub found
Dec 15 15:13:01 zack-A880G kernel: [    1.718617] hub 4-0:1.0: 3 ports detected
Dec 15 15:13:01 zack-A880G kernel: [    1.718683] ohci_hcd 0000:00:13.0: OHCI Host Controller
Dec 15 15:13:01 zack-A880G kernel: [    1.718688] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Dec 15 15:13:01 zack-A880G kernel: [    1.718714] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfeafc000
Dec 15 15:13:01 zack-A880G kernel: [    1.786292] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Dec 15 15:13:01 zack-A880G kernel: [    1.786296] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:13:01 zack-A880G kernel: [    1.786298] usb usb5: Product: OHCI Host Controller
Dec 15 15:13:01 zack-A880G kernel: [    1.786300] usb usb5: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
Dec 15 15:13:01 zack-A880G kernel: [    1.786301] usb usb5: SerialNumber: 0000:00:13.0
Dec 15 15:13:01 zack-A880G kernel: [    1.786388] hub 5-0:1.0: USB hub found
Dec 15 15:13:01 zack-A880G kernel: [    1.786396] hub 5-0:1.0: 3 ports detected
Dec 15 15:13:01 zack-A880G kernel: [    1.786463] ohci_hcd 0000:00:13.1: OHCI Host Controller
Dec 15 15:13:01 zack-A880G kernel: [    1.786468] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Dec 15 15:13:01 zack-A880G kernel: [    1.786484] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfeafb000
Dec 15 15:13:01 zack-A880G kernel: [    1.850172] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
Dec 15 15:13:01 zack-A880G kernel: [    1.850175] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:13:01 zack-A880G kernel: [    1.850177] usb usb6: Product: OHCI Host Controller
Dec 15 15:13:01 zack-A880G kernel: [    1.850179] usb usb6: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
Dec 15 15:13:01 zack-A880G kernel: [    1.850181] usb usb6: SerialNumber: 0000:00:13.1
Dec 15 15:13:01 zack-A880G kernel: [    1.850269] hub 6-0:1.0: USB hub found
Dec 15 15:13:01 zack-A880G kernel: [    1.850274] hub 6-0:1.0: 3 ports detected
Dec 15 15:13:01 zack-A880G kernel: [    1.850340] ohci_hcd 0000:00:14.5: OHCI Host Controller
Dec 15 15:13:01 zack-A880G kernel: [    1.850345] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
Dec 15 15:13:01 zack-A880G kernel: [    1.850361] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfeafa000
Dec 15 15:13:01 zack-A880G kernel: [    1.925505] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
Dec 15 15:13:01 zack-A880G kernel: [    1.925509] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:13:01 zack-A880G kernel: [    1.925511] usb usb7: Product: OHCI Host Controller
Dec 15 15:13:01 zack-A880G kernel: [    1.925513] usb usb7: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
Dec 15 15:13:01 zack-A880G kernel: [    1.925515] usb usb7: SerialNumber: 0000:00:14.5
Dec 15 15:13:01 zack-A880G kernel: [    1.928960] Freeing initrd memory: 15192k freed
Dec 15 15:13:01 zack-A880G kernel: [    1.934229] hub 7-0:1.0: USB hub found
Dec 15 15:13:01 zack-A880G kernel: [    1.934243] hub 7-0:1.0: 2 ports detected
Dec 15 15:13:01 zack-A880G kernel: [    1.934298] uhci_hcd: USB Universal Host Controller Interface driver
Dec 15 15:13:01 zack-A880G kernel: [    1.934365] usbcore: registered new interface driver libusual
Dec 15 15:13:01 zack-A880G kernel: [    1.934399] i8042: PNP: No PS/2 controller found. Probing ports directly.
Dec 15 15:13:01 zack-A880G kernel: [    1.978631] isapnp: No Plug & Play device found
Dec 15 15:13:01 zack-A880G kernel: [    1.978705] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 15 15:13:01 zack-A880G kernel: [    1.978708] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 15 15:13:01 zack-A880G kernel: [    1.978804] mousedev: PS/2 mouse device common for all mice
Dec 15 15:13:01 zack-A880G kernel: [    1.978886] rtc_cmos 00:03: RTC can wake from S4
Dec 15 15:13:01 zack-A880G kernel: [    1.978981] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Dec 15 15:13:01 zack-A880G kernel: [    1.979004] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Dec 15 15:13:01 zack-A880G kernel: [    1.979042] device-mapper: uevent: version 1.0.3
Dec 15 15:13:01 zack-A880G kernel: [    1.979084] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Dec 15 15:13:01 zack-A880G kernel: [    1.979095] EISA: Probing bus 0 at eisa.0
Dec 15 15:13:01 zack-A880G kernel: [    1.979097] EISA: Cannot allocate resource for mainboard
Dec 15 15:13:01 zack-A880G kernel: [    1.979098] Cannot allocate resource for EISA slot 1
Dec 15 15:13:01 zack-A880G kernel: [    1.979100] Cannot allocate resource for EISA slot 2
Dec 15 15:13:01 zack-A880G kernel: [    1.979101] Cannot allocate resource for EISA slot 3
Dec 15 15:13:01 zack-A880G kernel: [    1.979102] Cannot allocate resource for EISA slot 4
Dec 15 15:13:01 zack-A880G kernel: [    1.979103] Cannot allocate resource for EISA slot 5
Dec 15 15:13:01 zack-A880G kernel: [    1.979104] Cannot allocate resource for EISA slot 6
Dec 15 15:13:01 zack-A880G kernel: [    1.979105] Cannot allocate resource for EISA slot 7
Dec 15 15:13:01 zack-A880G kernel: [    1.979106] Cannot allocate resource for EISA slot 8
Dec 15 15:13:01 zack-A880G kernel: [    1.979107] EISA: Detected 0 cards.
Dec 15 15:13:01 zack-A880G kernel: [    1.979117] cpuidle: using governor ladder
Dec 15 15:13:01 zack-A880G kernel: [    1.979118] cpuidle: using governor menu
Dec 15 15:13:01 zack-A880G kernel: [    1.979119] EFI Variables Facility v0.08 2004-May-17
Dec 15 15:13:01 zack-A880G kernel: [    1.979276] ashmem: initialized
Dec 15 15:13:01 zack-A880G kernel: [    1.979365] TCP: cubic registered
Dec 15 15:13:01 zack-A880G kernel: [    1.979434] NET: Registered protocol family 10
Dec 15 15:13:01 zack-A880G kernel: [    1.979576] NET: Registered protocol family 17
Dec 15 15:13:01 zack-A880G kernel: [    1.979583] Key type dns_resolver registered
Dec 15 15:13:01 zack-A880G kernel: [    1.979620] Using IPI No-Shortcut mode
Dec 15 15:13:01 zack-A880G kernel: [    1.979667] PM: Hibernation image not present or could not be loaded.
Dec 15 15:13:01 zack-A880G kernel: [    1.979676] registered taskstats version 1
Dec 15 15:13:01 zack-A880G kernel: [    1.981443] Key type trusted registered
Dec 15 15:13:01 zack-A880G kernel: [    1.982855] Key type encrypted registered
Dec 15 15:13:01 zack-A880G kernel: [    1.984470]   Magic number: 9:772:251
Dec 15 15:13:01 zack-A880G kernel: [    1.984555] rtc_cmos 00:03: setting system clock to 2013-12-15 23:12:45 UTC (1387149165)
Dec 15 15:13:01 zack-A880G kernel: [    1.984580] powernow-k8: Found 1 AMD Sempron(tm) 145 Processor (1 cpu cores) (version 2.20.00)
Dec 15 15:13:01 zack-A880G kernel: [    1.984607] powernow-k8:    0 : pstate 0 (2800 MHz)
Dec 15 15:13:01 zack-A880G kernel: [    1.984608] powernow-k8:    1 : pstate 1 (2000 MHz)
Dec 15 15:13:01 zack-A880G kernel: [    1.984609] powernow-k8:    2 : pstate 2 (1600 MHz)
Dec 15 15:13:01 zack-A880G kernel: [    1.984610] powernow-k8:    3 : pstate 3 (800 MHz)
Dec 15 15:13:01 zack-A880G kernel: [    1.984663] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 15 15:13:01 zack-A880G kernel: [    1.984664] EDD information not available.
Dec 15 15:13:01 zack-A880G kernel: [    1.984757] Freeing unused kernel memory: 764k freed
Dec 15 15:13:01 zack-A880G kernel: [    1.984986] Write protecting the kernel text: 6060k
Dec 15 15:13:01 zack-A880G kernel: [    1.984998] Write protecting the kernel read-only data: 2484k
Dec 15 15:13:01 zack-A880G kernel: [    1.984999] NX-protecting the kernel data: 4180k
Dec 15 15:13:01 zack-A880G kernel: [    2.059015] ahci 0000:00:11.0: version 3.0
Dec 15 15:13:01 zack-A880G kernel: [    2.059135] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Dec 15 15:13:01 zack-A880G kernel: [    2.059139] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
Dec 15 15:13:01 zack-A880G kernel: [    2.060948] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 15 15:13:01 zack-A880G kernel: [    2.061021] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
Dec 15 15:13:01 zack-A880G kernel: [    2.061153] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xf842e000, 00:30:67:8c:c9:b2, XID 081000c0 IRQ 42
Dec 15 15:13:01 zack-A880G kernel: [    2.061155] r8169 0000:02:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Dec 15 15:13:01 zack-A880G kernel: [    2.074080] scsi0 : ahci
Dec 15 15:13:01 zack-A880G kernel: [    2.076923] scsi1 : ahci
Dec 15 15:13:01 zack-A880G kernel: [    2.078639] scsi2 : ahci
Dec 15 15:13:01 zack-A880G kernel: [    2.080338] scsi3 : ahci
Dec 15 15:13:01 zack-A880G kernel: [    2.080431] ata1: SATA max UDMA/133 abar m1024@0xfeaffc00 port 0xfeaffd00 irq 22
Dec 15 15:13:01 zack-A880G kernel: [    2.080434] ata2: SATA max UDMA/133 abar m1024@0xfeaffc00 port 0xfeaffd80 irq 22
Dec 15 15:13:01 zack-A880G kernel: [    2.080436] ata3: SATA max UDMA/133 abar m1024@0xfeaffc00 port 0xfeaffe00 irq 22
Dec 15 15:13:01 zack-A880G kernel: [    2.080439] ata4: SATA max UDMA/133 abar m1024@0xfeaffc00 port 0xfeaffe80 irq 22
Dec 15 15:13:01 zack-A880G kernel: [    2.106516] scsi4 : pata_atiixp
Dec 15 15:13:01 zack-A880G kernel: [    2.109170] scsi5 : pata_atiixp
Dec 15 15:13:01 zack-A880G kernel: [    2.109700] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Dec 15 15:13:01 zack-A880G kernel: [    2.109702] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Dec 15 15:13:01 zack-A880G kernel: [    2.276561] usb 3-3: new low-speed USB device number 2 using ohci_hcd
Dec 15 15:13:01 zack-A880G kernel: [    2.291301] ata6.00: ATA-7: Maxtor 6L200P0, BAH41G10, max UDMA/133
Dec 15 15:13:01 zack-A880G kernel: [    2.291305] ata6.00: 398297088 sectors, multi 16: LBA48 
Dec 15 15:13:01 zack-A880G kernel: [    2.291709] ata6.01: ATA-5: QUANTUM FIREBALLlct20 10, APL.0900, max UDMA/100
Dec 15 15:13:01 zack-A880G kernel: [    2.291713] ata6.01: 20044080 sectors, multi 8: LBA 
Dec 15 15:13:01 zack-A880G kernel: [    2.293220] Refined TSC clocksource calibration: 2800.157 MHz.
Dec 15 15:13:01 zack-A880G kernel: [    2.293226] Switching to clocksource tsc
Dec 15 15:13:01 zack-A880G kernel: [    2.311149] ata6.00: configured for UDMA/100
Dec 15 15:13:01 zack-A880G kernel: [    2.325922] ata6.01: configured for UDMA/100
Dec 15 15:13:01 zack-A880G kernel: [    2.397054] ata2: SATA link down (SStatus 0 SControl 300)
Dec 15 15:13:01 zack-A880G kernel: [    2.401024] ata4: SATA link down (SStatus 0 SControl 300)
Dec 15 15:13:01 zack-A880G kernel: [    2.401059] ata3: SATA link down (SStatus 0 SControl 300)
Dec 15 15:13:01 zack-A880G kernel: [    2.446145] usb 3-3: New USB device found, idVendor=046d, idProduct=c512
Dec 15 15:13:01 zack-A880G kernel: [    2.446149] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Dec 15 15:13:01 zack-A880G kernel: [    2.446151] usb 3-3: Product: USB Receiver
Dec 15 15:13:01 zack-A880G kernel: [    2.446153] usb 3-3: Manufacturer: Logitech
Dec 15 15:13:01 zack-A880G kernel: [    2.564156] usbcore: registered new interface driver usbhid
Dec 15 15:13:01 zack-A880G kernel: [    2.564159] usbhid: USB HID core driver
Dec 15 15:13:01 zack-A880G kernel: [    2.568703] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 15 15:13:01 zack-A880G kernel: [    2.572145] ata1.00: ATAPI: ASUS    DRW-24B3LT, 1.00, max UDMA/100
Dec 15 15:13:01 zack-A880G kernel: [    2.572980] ata1.00: configured for UDMA/100
Dec 15 15:13:01 zack-A880G kernel: [    2.574982] scsi 0:0:0:0: CD-ROM            ASUS     DRW-24B3LT       1.00 PQ: 0 ANSI: 5
Dec 15 15:13:01 zack-A880G kernel: [    2.578364] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 15 15:13:01 zack-A880G kernel: [    2.578368] cdrom: Uniform CD-ROM driver Revision: 3.20
Dec 15 15:13:01 zack-A880G kernel: [    2.578466] sr 0:0:0:0: Attached scsi CD-ROM sr0
Dec 15 15:13:01 zack-A880G kernel: [    2.578518] sr 0:0:0:0: Attached scsi generic sg0 type 5
Dec 15 15:13:01 zack-A880G kernel: [    2.578627] scsi 5:0:0:0: Direct-Access     ATA      Maxtor 6L200P0   BAH4 PQ: 0 ANSI: 5
Dec 15 15:13:01 zack-A880G kernel: [    2.578714] sd 5:0:0:0: [sda] 398297088 512-byte logical blocks: (203 GB/189 GiB)
Dec 15 15:13:01 zack-A880G kernel: [    2.578747] sd 5:0:0:0: [sda] Write Protect is off
Dec 15 15:13:01 zack-A880G kernel: [    2.578750] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 15 15:13:01 zack-A880G kernel: [    2.578762] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 15 15:13:01 zack-A880G kernel: [    2.578930] sd 5:0:0:0: Attached scsi generic sg1 type 0
Dec 15 15:13:01 zack-A880G kernel: [    2.617435]  sda: sda1 sda2 < sda5 >
Dec 15 15:13:01 zack-A880G kernel: [    2.617650] sd 5:0:0:0: [sda] Attached SCSI disk
Dec 15 15:13:01 zack-A880G kernel: [    2.617703] scsi 5:0:1:0: Direct-Access     ATA      QUANTUM FIREBALL APL. PQ: 0 ANSI: 5
Dec 15 15:13:01 zack-A880G kernel: [    2.617795] sd 5:0:1:0: Attached scsi generic sg2 type 0
Dec 15 15:13:01 zack-A880G kernel: [    2.617832] sd 5:0:1:0: [sdb] 20044080 512-byte logical blocks: (10.2 GB/9.55 GiB)
Dec 15 15:13:01 zack-A880G kernel: [    2.617856] sd 5:0:1:0: [sdb] Write Protect is off
Dec 15 15:13:01 zack-A880G kernel: [    2.617858] sd 5:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Dec 15 15:13:01 zack-A880G kernel: [    2.617869] sd 5:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 15 15:13:01 zack-A880G kernel: [    2.649987]  sdb: sdb1 sdb2 < sdb5 >
Dec 15 15:13:01 zack-A880G kernel: [    2.650201] sd 5:0:1:0: [sdb] Attached SCSI disk
Dec 15 15:13:01 zack-A880G kernel: [    2.661427] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input2
Dec 15 15:13:01 zack-A880G kernel: [    2.661526] logitech 0003:046D:C512.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:12.0-3/input0
Dec 15 15:13:01 zack-A880G kernel: [    2.662142] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1/input/input3
Dec 15 15:13:01 zack-A880G kernel: [    2.662260] logitech 0003:046D:C512.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:12.0-3/input1
Dec 15 15:13:01 zack-A880G kernel: [    5.362072] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Dec 15 15:13:01 zack-A880G kernel: [    5.362075] EXT4-fs (sda1): write access will be enabled during recovery
Dec 15 15:13:01 zack-A880G kernel: [    7.031578] EXT4-fs (sda1): recovery complete
Dec 15 15:13:01 zack-A880G kernel: [    7.044126] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Dec 15 15:13:01 zack-A880G kernel: [   16.953233] Adding 6141948k swap on /dev/sda5.  Priority:-1 extents:1 across:6141948k 
Dec 15 15:13:01 zack-A880G kernel: [   16.960714] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 15 15:13:01 zack-A880G kernel: [   17.028708] lp: driver loaded but no devices found
Dec 15 15:13:01 zack-A880G kernel: [   17.166947] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Dec 15 15:13:01 zack-A880G kernel: [   17.193960] wmi: Mapper loaded
Dec 15 15:13:01 zack-A880G kernel: [   17.336687] ACPI Warning: 0x00000b00-0x00000b07 SystemIO conflicts with Region \SOR1 1 (20120320/utaddress-251)
Dec 15 15:13:01 zack-A880G kernel: [   17.336694] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Dec 15 15:13:01 zack-A880G kernel: [   17.344682] sp5100_tco: SP5100 TCO WatchDog Timer Driver v0.01
Dec 15 15:13:01 zack-A880G kernel: [   17.344855] sp5100_tco: mmio address 0xfec000f0 already in use
Dec 15 15:13:01 zack-A880G kernel: [   17.349742] parport_pc 00:07: reported by Plug and Play ACPI
Dec 15 15:13:01 zack-A880G kernel: [   17.349800] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Dec 15 15:13:01 zack-A880G kernel: [   17.397312] Bluetooth: Core ver 2.16
Dec 15 15:13:01 zack-A880G kernel: [   17.397644] NET: Registered protocol family 31
Dec 15 15:13:01 zack-A880G kernel: [   17.397646] Bluetooth: HCI device and connection manager initialized
Dec 15 15:13:01 zack-A880G kernel: [   17.397648] Bluetooth: HCI socket layer initialized
Dec 15 15:13:01 zack-A880G kernel: [   17.397649] Bluetooth: L2CAP socket layer initialized
Dec 15 15:13:01 zack-A880G kernel: [   17.397657] Bluetooth: SCO socket layer initialized
Dec 15 15:13:01 zack-A880G kernel: [   17.413608] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Dec 15 15:13:01 zack-A880G kernel: [   17.413612] Bluetooth: BNEP filters: protocol multicast
Dec 15 15:13:01 zack-A880G kernel: [   17.470992] nvidia: module license 'NVIDIA' taints kernel.
Dec 15 15:13:01 zack-A880G kernel: [   17.470996] Disabling lock debugging due to kernel taint
Dec 15 15:13:01 zack-A880G kernel: [   17.492337] ppdev: user-space parallel port driver
Dec 15 15:13:01 zack-A880G kernel: [   17.502567] type=1400 audit(1387149181.042:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=600 comm="apparmor_parser"
Dec 15 15:13:01 zack-A880G kernel: [   17.502977] type=1400 audit(1387149181.042:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=600 comm="apparmor_parser"
Dec 15 15:13:01 zack-A880G kernel: [   17.503213] type=1400 audit(1387149181.042:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=600 comm="apparmor_parser"
Dec 15 15:13:01 zack-A880G kernel: [   17.516922] lp0: using parport0 (interrupt-driven).
Dec 15 15:13:01 zack-A880G kernel: [   17.518934] Bluetooth: RFCOMM TTY layer initialized
Dec 15 15:13:01 zack-A880G kernel: [   17.518939] Bluetooth: RFCOMM socket layer initialized
Dec 15 15:13:01 zack-A880G kernel: [   17.518940] Bluetooth: RFCOMM ver 1.11
Dec 15 15:13:01 zack-A880G kernel: [   17.602927] type=1400 audit(1387149181.142:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=671 comm="apparmor_parser"
Dec 15 15:13:01 zack-A880G kernel: [   17.604685] type=1400 audit(1387149181.146:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=671 comm="apparmor_parser"
Dec 15 15:13:01 zack-A880G kernel: [   17.635167] microcode: CPU0: patch_level=0x010000c8
Dec 15 15:13:01 zack-A880G failsafe: Failsafe of 120 seconds reached.
Dec 15 15:13:01 zack-A880G kernel: [   17.893291] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Dec 15 15:13:01 zack-A880G kernel: [   17.965077] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.88  Wed Mar 27 14:31:12 PDT 2013
Dec 15 15:13:01 zack-A880G kernel: [   17.998834] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
Dec 15 15:13:01 zack-A880G kernel: [   17.999126] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
Dec 15 15:13:01 zack-A880G kernel: [   17.999211] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
Dec 15 15:13:01 zack-A880G kernel: [   17.999438] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
Dec 15 15:13:01 zack-A880G kernel: [   18.001052] input: HDA ATI SB Line Out as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
Dec 15 15:13:01 zack-A880G kernel: [   18.027417] hda_intel: Disabling MSI
Dec 15 15:13:01 zack-A880G kernel: [   18.027428] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  ModemManager (version 0.5.2.0) starting...
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin Nokia
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin Option
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin Sierra
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin Novatel
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin ZTE
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin Linktop
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin MotoC
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> NetworkManager (version 0.9.4.0) is starting...
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> DNS: loaded plugin dnsmasq
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin Gobi
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin X22X
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin Longcheer
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin Generic
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin Huawei
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin Ericsson MBM
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin SimTech
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin AnyData
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin Option High-Speed
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin Samsung
Dec 15 15:13:01 zack-A880G modem-manager[779]: <info>  Loaded plugin Wavecom
Dec 15 15:13:01 zack-A880G dbus[549]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Dec 15 15:13:01 zack-A880G udev-configure-printer: add /devices/pnp0/00:07/printer/lp0
Dec 15 15:13:01 zack-A880G udev-configure-printer: Failed to get parent
Dec 15 15:13:01 zack-A880G udev-configure-printer: add /devices/pnp0/00:07/printer/lp0
Dec 15 15:13:01 zack-A880G udev-configure-printer: Failed to get parent
Dec 15 15:13:01 zack-A880G udev-configure-printer: add /module/lp
Dec 15 15:13:01 zack-A880G udev-configure-printer: Failed to get parent
Dec 15 15:13:01 zack-A880G kernel: [   18.121541] type=1400 audit(1387149181.662:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=822 comm="apparmor_parser"
Dec 15 15:13:01 zack-A880G kernel: [   18.121894] type=1400 audit(1387149181.662:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=822 comm="apparmor_parser"
Dec 15 15:13:01 zack-A880G kernel: [   18.129185] type=1400 audit(1387149181.670:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=823 comm="apparmor_parser"
Dec 15 15:13:01 zack-A880G kernel: [   18.131603] type=1400 audit(1387149181.674:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=823 comm="apparmor_parser"
Dec 15 15:13:01 zack-A880G kernel: [   18.131824] type=1400 audit(1387149181.674:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=823 comm="apparmor_parser"
Dec 15 15:13:01 zack-A880G kernel: [   18.138944] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Dec 15 15:13:01 zack-A880G kernel: [   18.156081] kvm: Nested Virtualization enabled
Dec 15 15:13:01 zack-A880G kernel: [   18.156086] kvm: Nested Paging enabled
Dec 15 15:13:01 zack-A880G polkitd[793]: started daemon version 0.104 using authority implementation `local' version `0.104'
Dec 15 15:13:01 zack-A880G dbus[549]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Dec 15 15:13:01 zack-A880G NetworkManager[781]:    SCPlugin-Ifupdown: init!
Dec 15 15:13:01 zack-A880G NetworkManager[781]:    SCPlugin-Ifupdown: update_system_hostname
Dec 15 15:13:01 zack-A880G NetworkManager[781]:    SCPluginIfupdown: management mode: unmanaged
Dec 15 15:13:01 zack-A880G NetworkManager[781]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0/net/eth0, iface: eth0)
Dec 15 15:13:01 zack-A880G NetworkManager[781]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec 15 15:13:01 zack-A880G NetworkManager[781]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Dec 15 15:13:01 zack-A880G NetworkManager[781]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Dec 15 15:13:01 zack-A880G NetworkManager[781]:    SCPlugin-Ifupdown: end _init.
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dec 15 15:13:01 zack-A880G NetworkManager[781]:    Ifupdown: get unmanaged devices count: 0
Dec 15 15:13:01 zack-A880G NetworkManager[781]:    SCPlugin-Ifupdown: (145815888) ... get_connections.
Dec 15 15:13:01 zack-A880G NetworkManager[781]:    SCPlugin-Ifupdown: (145815888) ... get_connections (managed=false): return empty list.
Dec 15 15:13:01 zack-A880G NetworkManager[781]:    keyfile: parsing Zoom Zoom 1 ... 
Dec 15 15:13:01 zack-A880G NetworkManager[781]:    keyfile:     read connection 'Zoom Zoom 1'
Dec 15 15:13:01 zack-A880G NetworkManager[781]:    keyfile: parsing Zoom Zoom ... 
Dec 15 15:13:01 zack-A880G NetworkManager[781]:    keyfile:     read connection 'Zoom Zoom'
Dec 15 15:13:01 zack-A880G NetworkManager[781]:    Ifupdown: get unmanaged devices count: 0
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> modem-manager is now available
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> WiFi enabled by radio killswitch; enabled by state file
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> WWAN enabled by radio killswitch; enabled by state file
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> WiMAX enabled by radio killswitch; enabled by state file
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> Networking is enabled by state file
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <warn> failed to allocate link cache: (-10) Operation not supported
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> (eth0): carrier is OFF
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> (eth0): now managed
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> (eth0): bringing up device.
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> (eth0): preparing device.
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> (eth0): deactivating device (reason 'managed') [2]
Dec 15 15:13:01 zack-A880G NetworkManager[781]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0/net/eth0
Dec 15 15:13:01 zack-A880G kernel: [   18.264120] r8169 0000:02:00.0: eth0: link down
Dec 15 15:13:01 zack-A880G kernel: [   18.264168] r8169 0000:02:00.0: eth0: link down
Dec 15 15:13:01 zack-A880G kernel: [   18.264563] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 15 15:13:01 zack-A880G kernel: [   18.264889] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 15 15:13:01 zack-A880G anacron[906]: Anacron 2.3 started on 2013-12-15
Dec 15 15:13:01 zack-A880G acpid: starting up with proc fs
Dec 15 15:13:01 zack-A880G acpid: skipping conf file /etc/acpi/events/RadioPower.sh
Dec 15 15:13:01 zack-A880G acpid: 35 rules loaded
Dec 15 15:13:01 zack-A880G acpid: waiting for events: event logging is off
Dec 15 15:13:01 zack-A880G cron[881]: (CRON) INFO (pidfile fd = 3)
Dec 15 15:13:02 zack-A880G cron[913]: (CRON) STARTUP (fork ok)
Dec 15 15:13:02 zack-A880G cron[913]: (CRON) INFO (Running @reboot jobs)
Dec 15 15:13:02 zack-A880G anacron[906]: Will run job `cron.daily' in 5 min.
Dec 15 15:13:02 zack-A880G anacron[906]: Will run job `cron.weekly' in 10 min.
Dec 15 15:13:02 zack-A880G anacron[906]: Will run job `cron.monthly' in 15 min.
Dec 15 15:13:02 zack-A880G anacron[906]: Jobs will be executed sequentially
Dec 15 15:13:02 zack-A880G kernel: [   19.029470] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input9
Dec 15 15:13:02 zack-A880G kernel: [   19.029670] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input10
Dec 15 15:13:02 zack-A880G kernel: [   19.029791] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input11
Dec 15 15:13:02 zack-A880G kernel: [   19.029905] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input12
Dec 15 15:13:02 zack-A880G dhclient: isc-dhclient-4.1-ESV-R4
Dec 15 15:13:02 zack-A880G dhclient: isc-dhclient-4.1-ESV-R4
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> (eth0): carrier now ON (device state 20)
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> Auto-activating connection 'Wired connection 1'.
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> Activation (eth0) starting connection 'Wired connection 1'
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 15 15:13:03 zack-A880G kernel: [   19.916831] r8169 0000:02:00.0: eth0: link up
Dec 15 15:13:03 zack-A880G kernel: [   19.917002] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> dhclient started with pid 1173
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> Activation (eth0) Beginning IP6 addrconf.
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec 15 15:13:03 zack-A880G dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Dec 15 15:13:03 zack-A880G dhclient: Copyright 2004-2011 Internet Systems Consortium.
Dec 15 15:13:03 zack-A880G dhclient: All rights reserved.
Dec 15 15:13:03 zack-A880G dhclient: For info, please visit https://www.isc.org/software/dhcp/
Dec 15 15:13:03 zack-A880G dhclient: 
Dec 15 15:13:03 zack-A880G NetworkManager[781]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec 15 15:13:03 zack-A880G dhclient: Listening on LPF/eth0/00:30:67:8c:c9:b2
Dec 15 15:13:03 zack-A880G dhclient: Sending on   LPF/eth0/00:30:67:8c:c9:b2
Dec 15 15:13:03 zack-A880G dhclient: Sending on   Socket/fallback
Dec 15 15:13:03 zack-A880G dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec 15 15:13:04 zack-A880G dhclient: DHCPREQUEST of 192.168.1.47 on eth0 to 255.255.255.255 port 67
Dec 15 15:13:04 zack-A880G dhclient: DHCPOFFER of 192.168.1.47 from 192.168.1.1
Dec 15 15:13:04 zack-A880G dhclient: DHCPACK of 192.168.1.47 from 192.168.1.1
Dec 15 15:13:04 zack-A880G dhclient: bound to 192.168.1.47 -- renewal in 34086 seconds.
Dec 15 15:13:04 zack-A880G NetworkManager[781]: <info> (eth0): DHCPv4 state changed preinit -> bound
Dec 15 15:13:04 zack-A880G NetworkManager[781]: <info>   address 192.168.1.47
Dec 15 15:13:04 zack-A880G NetworkManager[781]: <info>   prefix 24 (255.255.255.0)
Dec 15 15:13:04 zack-A880G NetworkManager[781]: <info>   gateway 192.168.1.1
Dec 15 15:13:04 zack-A880G NetworkManager[781]: <info>   nameserver '192.168.1.1'
Dec 15 15:13:04 zack-A880G NetworkManager[781]: <info>   nameserver '192.168.1.1'
Dec 15 15:13:04 zack-A880G NetworkManager[781]: <info>   domain name 'myhome.westell.com'
Dec 15 15:13:04 zack-A880G NetworkManager[781]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Dec 15 15:13:04 zack-A880G NetworkManager[781]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Dec 15 15:13:05 zack-A880G NetworkManager[781]: <info> DNS: starting dnsmasq...
Dec 15 15:13:05 zack-A880G NetworkManager[781]: <error> [1387149185.675402] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
Dec 15 15:13:05 zack-A880G NetworkManager[781]: <error> [1387149185.675461] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
Dec 15 15:13:05 zack-A880G NetworkManager[781]: <warn> DNS: plugin dnsmasq update failed
Dec 15 15:13:05 zack-A880G NetworkManager[781]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Dec 15 15:13:05 zack-A880G dnsmasq[1219]: started, version 2.59 cache disabled
Dec 15 15:13:05 zack-A880G dnsmasq[1219]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Dec 15 15:13:05 zack-A880G dnsmasq[1219]: DBus support enabled: connected to system bus
Dec 15 15:13:05 zack-A880G dnsmasq[1219]: warning: no upstream servers configured
Dec 15 15:13:05 zack-A880G acpid: client connected from 1216[0:0]
Dec 15 15:13:05 zack-A880G acpid: 1 client rule loaded
Dec 15 15:13:05 zack-A880G NetworkManager[781]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Dec 15 15:13:05 zack-A880G NetworkManager[781]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Dec 15 15:13:05 zack-A880G NetworkManager[781]: <info> Activation (eth0) successful, device activated.
Dec 15 15:13:05 zack-A880G NetworkManager[781]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Dec 15 15:13:05 zack-A880G dbus[549]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec 15 15:13:05 zack-A880G NetworkManager[781]: <warn> dnsmasq appeared on DBus: :1.14
Dec 15 15:13:05 zack-A880G NetworkManager[781]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Dec 15 15:13:05 zack-A880G dnsmasq[1219]: setting upstream servers from DBus
Dec 15 15:13:05 zack-A880G dnsmasq[1219]: using nameserver 192.168.1.1#53
Dec 15 15:13:05 zack-A880G dbus[549]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 15 15:13:05 zack-A880G kernel: [   22.433497] NVRM: API mismatch: the client has the version 319.32, but
Dec 15 15:13:05 zack-A880G kernel: [   22.433497] NVRM: this kernel module has the version 304.88.  Please
Dec 15 15:13:05 zack-A880G kernel: [   22.433497] NVRM: make sure that this kernel module and all NVIDIA driver
Dec 15 15:13:05 zack-A880G kernel: [   22.433497] NVRM: components have the same version.
Dec 15 15:13:06 zack-A880G acpid: client 1216[0:0] has disconnected
Dec 15 15:13:06 zack-A880G acpid: client connected from 1327[0:0]
Dec 15 15:13:06 zack-A880G acpid: 1 client rule loaded
Dec 15 15:13:06 zack-A880G kernel: [   22.588053] NVRM: API mismatch: the client has the version 319.32, but
Dec 15 15:13:06 zack-A880G kernel: [   22.588053] NVRM: this kernel module has the version 304.88.  Please
Dec 15 15:13:06 zack-A880G kernel: [   22.588053] NVRM: make sure that this kernel module and all NVIDIA driver
Dec 15 15:13:06 zack-A880G kernel: [   22.588053] NVRM: components have the same version.
Dec 15 23:13:16 zack-A880G ntpdate[1360]: step time server 91.189.94.4 offsDec 15 15:14:32 zack-A880G kernel: imklog 5.8.6, log source = /proc/kmsg started.
Dec 15 15:14:32 zack-A880G rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="602" x-info="http://www.rsyslog.com"] start
Dec 15 15:14:32 zack-A880G rsyslogd: rsyslogd's groupid changed to 103
Dec 15 15:14:32 zack-A880G rsyslogd: rsyslogd's userid changed to 101
Dec 15 15:14:32 zack-A880G rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Linux version 3.5.0-43-generic (buildd@akateko) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #66~precise1-Ubuntu SMP Thu Oct 24 14:55:08 UTC 2013 (Ubuntu 3.5.0-43.66~precise1-generic 3.5.7.23)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] KERNEL supported cpus:
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   Intel GenuineIntel
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   AMD AuthenticAMD
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   NSC Geode by NSC
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   Cyrix CyrixInstead
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   Centaur CentaurHauls
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   Transmeta GenuineTMx86
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   Transmeta TransmetaCPU
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   UMC UMC UMC UMC
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ffaffff] usable
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x000000007ffb0000-0x000000007ffbdfff] ACPI data
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x000000007ffbe000-0x000000007ffdffff] ACPI NVS
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x000000007ffe0000-0x000000007fffffff] reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] SMBIOS 2.6 present.
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] DMI: BIOSTAR Group A880G+/A880G+, BIOS 080016  08/30/2010
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] e820: last_pfn = 0x7ffb0 max_arch_pfn = 0x1000000
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] MTRR default type: uncachable
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   00000-9FFFF write-back
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   A0000-EFFFF uncachable
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   F0000-FFFFF write-protect
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] MTRR variable ranges enabled:
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   1 disabled
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   2 disabled
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   3 disabled
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   4 disabled
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   5 disabled
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   6 disabled
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   7 disabled
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [c00ff780]
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]  [mem 0x00000000-0x001fffff] page 4k
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]  [mem 0x00200000-0x379fffff] page 2M
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] RAMDISK: [mem 0x36244000-0x37119fff]
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: RSDP 000faf80 00014 (v00 ACPIAM)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: RSDT 7ffb0000 00044 (v01 083010 RSDT1638 20100830 MSFT 00000097)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: FACP 7ffb0200 00084 (v01 083010 FACP1638 20100830 MSFT 00000097)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20120320/tbfadt-579)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: DSDT 7ffb0450 0A1DA (v01  88PCP 88PCP830 00000002 INTL 20051117)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: FACS 7ffbe000 00040
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: APIC 7ffb0390 0007C (v01 083010 APIC1638 20100830 MSFT 00000097)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: MCFG 7ffb0410 0003C (v01 083010 OEMMCFG  20100830 MSFT 00000097)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: OEMB 7ffbe040 00072 (v01 083010 OEMB1638 20100830 MSFT 00000097)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: SRAT 7ffba630 00090 (v03 AMD    FAM_F_10 00000002 AMD  00000001)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: MSCT 7ffba6c0 0004E (v01 A M I  OEMBOARD 00000001 AMD  00000001)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: HPET 7ffba710 00038 (v01 083010 OEMHPET  20100830 MSFT 00000097)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: SSDT 7ffba750 0023E (v01 A M I  POWERNOW 00000001 AMD  00000001)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] 1155MB HIGHMEM available.
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] 891MB LOWMEM available.
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   low ram: 0 - 37bfe000
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Zone ranges:
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   HighMem  [mem 0x37bfe000-0x7ffaffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Movable zone start for each node
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Early memory node ranges
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   node   0: [mem 0x00010000-0x0009efff]
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   node   0: [mem 0x00100000-0x7ffaffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] On node 0 totalpages: 524095
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] free_area_init_node: node 0, pgdat c18c85c0, node_mem_map f5244200
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   HighMem zone: 2312 pages used for memmap
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]   HighMem zone: 293546 pages, LIFO batch:31
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Using APIC driver default
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] SMP: Allowing 6 CPUs, 5 hotplug CPUs
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] nr_irqs_gsi: 40
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] e820: [mem 0x80000000-0xffefffff] available for PCI devices
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:6 nr_node_ids:1
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f7b9d000 s34176 r0 d23168 u57344
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] pcpu-alloc: s34176 r0 d23168 u57344 alloc=14*4096
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 [0] 4 [0] 5 
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519999
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-43-generic root=UUID=a5baa10f-bb69-49cc-998b-f6e8c4f55e7d ro quiet splash
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] __ex_table already sorted, skipping sort
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Initializing CPU#0
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] allocated 4193536 bytes of page_cgroup
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:0007ffb0)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Memory: 2048744k/2096832k available (6059k kernel code, 47636k reserved, 2985k data, 764k init, 1183432k highmem)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] virtual kernel memory layout:
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]       .init : 0xc18d6000 - 0xc1995000   ( 764 kB)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]       .data : 0xc15eaf15 - 0xc18d54c0   (2985 kB)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]       .text : 0xc1000000 - 0xc15eaf15   (6059 kB)
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Hierarchical RCU implementation.
Dec 15 15:14:32 zack-A880G kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] NR_IRQS:2304 nr_irqs:728 16
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] CPU 0 irqstacks, hard=f4c0a000 soft=f4c0c000
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Console: colour VGA+ 80x25
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] console [tty0] enabled
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] hpet clockevent registered
Dec 15 15:14:32 zack-A880G kernel: [    0.000000] Fast TSC calibration failed
Dec 15 15:14:32 zack-A880G kernel: [    0.008000] TSC: PIT calibration matches HPET. 1 loops
Dec 15 15:14:32 zack-A880G kernel: [    0.008000] Detected 2800.151 MHz processor.
Dec 15 15:14:32 zack-A880G kernel: [    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5600.30 BogoMIPS (lpj=11200604)
Dec 15 15:14:32 zack-A880G kernel: [    0.000004] pid_max: default: 32768 minimum: 301
Dec 15 15:14:32 zack-A880G kernel: [    0.000024] Security Framework initialized
Dec 15 15:14:32 zack-A880G kernel: [    0.000038] AppArmor: AppArmor initialized
Dec 15 15:14:32 zack-A880G kernel: [    0.000040] Yama: becoming mindful.
Dec 15 15:14:32 zack-A880G kernel: [    0.000085] Mount-cache hash table entries: 512
Dec 15 15:14:32 zack-A880G kernel: [    0.000253] Initializing cgroup subsys cpuacct
Dec 15 15:14:32 zack-A880G kernel: [    0.000256] Initializing cgroup subsys memory
Dec 15 15:14:32 zack-A880G kernel: [    0.000262] Initializing cgroup subsys devices
Dec 15 15:14:32 zack-A880G kernel: [    0.000263] Initializing cgroup subsys freezer
Dec 15 15:14:32 zack-A880G kernel: [    0.000265] Initializing cgroup subsys blkio
Dec 15 15:14:32 zack-A880G kernel: [    0.000267] Initializing cgroup subsys perf_event
Dec 15 15:14:32 zack-A880G kernel: [    0.000287] mce: CPU supports 6 MCE banks
Dec 15 15:14:32 zack-A880G kernel: [    0.000292] LVT offset 0 assigned for vector 0xf9
Dec 15 15:14:32 zack-A880G kernel: [    0.000470] SMP alternatives: switching to UP code
Dec 15 15:14:32 zack-A880G kernel: [    0.007540] ACPI: Core revision 20120320
Dec 15 15:14:32 zack-A880G kernel: [    0.018517] ftrace: allocating 27161 entries in 54 pages
Dec 15 15:14:32 zack-A880G kernel: [    0.028177] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 15 15:14:32 zack-A880G kernel: [    0.028537] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 15 15:14:32 zack-A880G kernel: [    0.068664] CPU0: AMD Sempron(tm) 145 Processor stepping 03
Dec 15 15:14:32 zack-A880G kernel: [    0.173608] Performance Events: AMD PMU driver.
Dec 15 15:14:32 zack-A880G kernel: [    0.173612] ... version:                0
Dec 15 15:14:32 zack-A880G kernel: [    0.173613] ... bit width:              48
Dec 15 15:14:32 zack-A880G kernel: [    0.173614] ... generic registers:      4
Dec 15 15:14:32 zack-A880G kernel: [    0.173615] ... value mask:             0000ffffffffffff
Dec 15 15:14:32 zack-A880G kernel: [    0.173616] ... max period:             00007fffffffffff
Dec 15 15:14:32 zack-A880G kernel: [    0.173617] ... fixed-purpose events:   0
Dec 15 15:14:32 zack-A880G kernel: [    0.173618] ... event mask:             000000000000000f
Dec 15 15:14:32 zack-A880G kernel: [    0.173751] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Dec 15 15:14:32 zack-A880G kernel: [    0.173797] Brought up 1 CPUs
Dec 15 15:14:32 zack-A880G kernel: [    0.173799] Total of 1 processors activated (5600.30 BogoMIPS).
Dec 15 15:14:32 zack-A880G kernel: [    0.174245] devtmpfs: initialized
Dec 15 15:14:32 zack-A880G kernel: [    0.174363] EVM: security.selinux
Dec 15 15:14:32 zack-A880G kernel: [    0.174364] EVM: security.SMACK64
Dec 15 15:14:32 zack-A880G kernel: [    0.174365] EVM: security.capability
Dec 15 15:14:32 zack-A880G kernel: [    0.174406] PM: Registering ACPI NVS region [mem 0x7ffbe000-0x7ffdffff] (139264 bytes)
Dec 15 15:14:32 zack-A880G kernel: [    0.175163] dummy: 
Dec 15 15:14:32 zack-A880G kernel: [    0.175188] RTC time: 23:14:15, date: 12/15/13
Dec 15 15:14:32 zack-A880G kernel: [    0.175217] NET: Registered protocol family 16
Dec 15 15:14:32 zack-A880G kernel: [    0.175299] EISA bus registered
Dec 15 15:14:32 zack-A880G kernel: [    0.175303] node 0 link 0: io port [1000, ffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.175306] TOM: 0000000080000000 aka 2048M
Dec 15 15:14:32 zack-A880G kernel: [    0.175308] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.175310] node 0 link 0: mmio [a0000, bffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.175312] node 0 link 0: mmio [80000000, dfffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.175314] node 0 link 0: mmio [e0000000, efffffff] ==> none
Dec 15 15:14:32 zack-A880G kernel: [    0.175316] node 0 link 0: mmio [f0000000, ffefffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.175318] bus: [00, 07] on node 0 link 0
Dec 15 15:14:32 zack-A880G kernel: [    0.175319] bus: 00 [io  0x0000-0xffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.175320] bus: 00 [mem 0x000a0000-0x000bffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.175322] bus: 00 [mem 0x80000000-0xdfffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.175323] bus: 00 [mem 0xf0000000-0xfcffffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.175374] ACPI: bus type pci registered
Dec 15 15:14:32 zack-A880G kernel: [    0.175417] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Dec 15 15:14:32 zack-A880G kernel: [    0.175419] PCI: not using MMCONFIG
Dec 15 15:14:32 zack-A880G kernel: [    0.175986] PCI : PCI BIOS area is rw and x. Use pci=nobios if you want it NX.
Dec 15 15:14:32 zack-A880G kernel: [    0.176055] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
Dec 15 15:14:32 zack-A880G kernel: [    0.176056] PCI: Using configuration type 1 for base access
Dec 15 15:14:32 zack-A880G kernel: [    0.176057] PCI: Using configuration type 1 for extended access
Dec 15 15:14:32 zack-A880G kernel: [    0.176678] bio: create slab <bio-0> at 0
Dec 15 15:14:32 zack-A880G kernel: [    0.176740] ACPI: Added _OSI(Module Device)
Dec 15 15:14:32 zack-A880G kernel: [    0.176741] ACPI: Added _OSI(Processor Device)
Dec 15 15:14:32 zack-A880G kernel: [    0.176742] ACPI: Added _OSI(3.0 _SCP Extensions)
Dec 15 15:14:32 zack-A880G kernel: [    0.176744] ACPI: Added _OSI(Processor Aggregator Device)
Dec 15 15:14:32 zack-A880G kernel: [    0.177308] ACPI: EC: Look up EC in DSDT
Dec 15 15:14:32 zack-A880G kernel: [    0.178519] ACPI: Executed 4 blocks of module-level executable AML code
Dec 15 15:14:32 zack-A880G kernel: [    0.181800] ACPI: Interpreter enabled
Dec 15 15:14:32 zack-A880G kernel: [    0.181805] ACPI: (supports S0 S1 S4 S5)
Dec 15 15:14:32 zack-A880G kernel: [    0.181821] ACPI: Using IOAPIC for interrupt routing
Dec 15 15:14:32 zack-A880G kernel: [    0.181840] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Dec 15 15:14:32 zack-A880G kernel: [    0.183044] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Dec 15 15:14:32 zack-A880G kernel: [    0.183045] PCI: Using MMCONFIG for extended config space
Dec 15 15:14:32 zack-A880G kernel: [    0.187595] ACPI: No dock devices found.
Dec 15 15:14:32 zack-A880G kernel: [    0.187599] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Dec 15 15:14:32 zack-A880G kernel: [    0.187661] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Dec 15 15:14:32 zack-A880G kernel: [    0.187766] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Dec 15 15:14:32 zack-A880G kernel: [    0.187769] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.187771] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.187773] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.187775] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xdfffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.187776] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.187800] PCI host bridge to bus 0000:00
Dec 15 15:14:32 zack-A880G kernel: [    0.187802] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Dec 15 15:14:32 zack-A880G kernel: [    0.187804] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.187806] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.187807] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.187809] pci_bus 0000:00: root bus resource [mem 0x80000000-0xdfffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.187811] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.187821] pci 0000:00:00.0: [1022:9601] type 00 class 0x060000
Dec 15 15:14:32 zack-A880G kernel: [    0.187869] pci 0000:00:02.0: [1022:9603] type 01 class 0x060400
Dec 15 15:14:32 zack-A880G kernel: [    0.187899] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Dec 15 15:14:32 zack-A880G kernel: [    0.187926] pci 0000:00:07.0: [1022:9607] type 01 class 0x060400
Dec 15 15:14:32 zack-A880G kernel: [    0.187955] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Dec 15 15:14:32 zack-A880G kernel: [    0.187995] pci 0000:00:11.0: [1002:4390] type 00 class 0x01018f
Dec 15 15:14:32 zack-A880G kernel: [    0.188013] pci 0000:00:11.0: reg 10: [io  0xb000-0xb007]
Dec 15 15:14:32 zack-A880G kernel: [    0.188023] pci 0000:00:11.0: reg 14: [io  0xa000-0xa003]
Dec 15 15:14:32 zack-A880G kernel: [    0.188032] pci 0000:00:11.0: reg 18: [io  0x9000-0x9007]
Dec 15 15:14:32 zack-A880G kernel: [    0.188041] pci 0000:00:11.0: reg 1c: [io  0x8000-0x8003]
Dec 15 15:14:32 zack-A880G kernel: [    0.188050] pci 0000:00:11.0: reg 20: [io  0x7000-0x700f]
Dec 15 15:14:32 zack-A880G kernel: [    0.188059] pci 0000:00:11.0: reg 24: [mem 0xfeaffc00-0xfeafffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.188079] pci 0000:00:11.0: set SATA to AHCI mode
Dec 15 15:14:32 zack-A880G kernel: [    0.188123] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
Dec 15 15:14:32 zack-A880G kernel: [    0.188136] pci 0000:00:12.0: reg 10: [mem 0xfeafe000-0xfeafefff]
Dec 15 15:14:32 zack-A880G kernel: [    0.188197] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
Dec 15 15:14:32 zack-A880G kernel: [    0.188210] pci 0000:00:12.1: reg 10: [mem 0xfeafd000-0xfeafdfff]
Dec 15 15:14:32 zack-A880G kernel: [    0.188276] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
Dec 15 15:14:32 zack-A880G kernel: [    0.188294] pci 0000:00:12.2: reg 10: [mem 0xfeaff800-0xfeaff8ff]
Dec 15 15:14:32 zack-A880G kernel: [    0.188374] pci 0000:00:12.2: supports D1 D2
Dec 15 15:14:32 zack-A880G kernel: [    0.188375] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Dec 15 15:14:32 zack-A880G kernel: [    0.188397] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
Dec 15 15:14:32 zack-A880G kernel: [    0.188410] pci 0000:00:13.0: reg 10: [mem 0xfeafc000-0xfeafcfff]
Dec 15 15:14:32 zack-A880G kernel: [    0.188471] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
Dec 15 15:14:32 zack-A880G kernel: [    0.188484] pci 0000:00:13.1: reg 10: [mem 0xfeafb000-0xfeafbfff]
Dec 15 15:14:32 zack-A880G kernel: [    0.188551] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
Dec 15 15:14:32 zack-A880G kernel: [    0.188569] pci 0000:00:13.2: reg 10: [mem 0xfeaff400-0xfeaff4ff]
Dec 15 15:14:32 zack-A880G kernel: [    0.188648] pci 0000:00:13.2: supports D1 D2
Dec 15 15:14:32 zack-A880G kernel: [    0.188650] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Dec 15 15:14:32 zack-A880G kernel: [    0.188674] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
Dec 15 15:14:32 zack-A880G kernel: [    0.188768] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
Dec 15 15:14:32 zack-A880G kernel: [    0.188784] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Dec 15 15:14:32 zack-A880G kernel: [    0.188793] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Dec 15 15:14:32 zack-A880G kernel: [    0.188802] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Dec 15 15:14:32 zack-A880G kernel: [    0.188811] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Dec 15 15:14:32 zack-A880G kernel: [    0.188820] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
Dec 15 15:14:32 zack-A880G kernel: [    0.188878] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
Dec 15 15:14:32 zack-A880G kernel: [    0.188898] pci 0000:00:14.2: reg 10: [mem 0xfeaf4000-0xfeaf7fff 64bit]
Dec 15 15:14:32 zack-A880G kernel: [    0.188962] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Dec 15 15:14:32 zack-A880G kernel: [    0.188977] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
Dec 15 15:14:32 zack-A880G kernel: [    0.189050] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
Dec 15 15:14:32 zack-A880G kernel: [    0.189089] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
Dec 15 15:14:32 zack-A880G kernel: [    0.189102] pci 0000:00:14.5: reg 10: [mem 0xfeafa000-0xfeafafff]
Dec 15 15:14:32 zack-A880G kernel: [    0.189166] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
Dec 15 15:14:32 zack-A880G kernel: [    0.189179] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
Dec 15 15:14:32 zack-A880G kernel: [    0.189190] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
Dec 15 15:14:32 zack-A880G kernel: [    0.189201] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
Dec 15 15:14:32 zack-A880G kernel: [    0.189215] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
Dec 15 15:14:32 zack-A880G kernel: [    0.189263] pci 0000:01:00.0: [10de:0de1] type 00 class 0x030000
Dec 15 15:14:32 zack-A880G kernel: [    0.189272] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.189282] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
Dec 15 15:14:32 zack-A880G kernel: [    0.189292] pci 0000:01:00.0: reg 1c: [mem 0xd6000000-0xd7ffffff 64bit pref]
Dec 15 15:14:32 zack-A880G kernel: [    0.189298] pci 0000:01:00.0: reg 24: [io  0xc800-0xc87f]
Dec 15 15:14:32 zack-A880G kernel: [    0.189305] pci 0000:01:00.0: reg 30: [mem 0xfcf80000-0xfcffffff pref]
Dec 15 15:14:32 zack-A880G kernel: [    0.189357] pci 0000:01:00.1: [10de:0bea] type 00 class 0x040300
Dec 15 15:14:32 zack-A880G kernel: [    0.189366] pci 0000:01:00.1: reg 10: [mem 0xfcf7c000-0xfcf7ffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.193606] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Dec 15 15:14:32 zack-A880G kernel: [    0.193613] pci 0000:00:02.0:   bridge window [io  0xc000-0xcfff]
Dec 15 15:14:32 zack-A880G kernel: [    0.193617] pci 0000:00:02.0:   bridge window [mem 0xfcf00000-0xfdffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.193620] pci 0000:00:02.0:   bridge window [mem 0xd6000000-0xdfffffff 64bit pref]
Dec 15 15:14:32 zack-A880G kernel: [    0.193657] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
Dec 15 15:14:32 zack-A880G kernel: [    0.193671] pci 0000:02:00.0: reg 10: [io  0xd800-0xd8ff]
Dec 15 15:14:32 zack-A880G kernel: [    0.193690] pci 0000:02:00.0: reg 18: [mem 0xfbffb000-0xfbffbfff 64bit pref]
Dec 15 15:14:32 zack-A880G kernel: [    0.193703] pci 0000:02:00.0: reg 20: [mem 0xfbffc000-0xfbffffff 64bit pref]
Dec 15 15:14:32 zack-A880G kernel: [    0.193711] pci 0000:02:00.0: reg 30: [mem 0xfebe0000-0xfebfffff pref]
Dec 15 15:14:32 zack-A880G kernel: [    0.193758] pci 0000:02:00.0: supports D1 D2
Dec 15 15:14:32 zack-A880G kernel: [    0.193760] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 15 15:14:32 zack-A880G kernel: [    0.201590] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Dec 15 15:14:32 zack-A880G kernel: [    0.201597] pci 0000:00:07.0:   bridge window [io  0xd000-0xdfff]
Dec 15 15:14:32 zack-A880G kernel: [    0.201599] pci 0000:00:07.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.201603] pci 0000:00:07.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
Dec 15 15:14:32 zack-A880G kernel: [    0.201648] pci 0000:03:06.0: [1274:1371] type 00 class 0x040100
Dec 15 15:14:32 zack-A880G kernel: [    0.201670] pci 0000:03:06.0: reg 10: [io  0xe800-0xe83f]
Dec 15 15:14:32 zack-A880G kernel: [    0.201767] pci 0000:03:06.0: supports D2
Dec 15 15:14:32 zack-A880G kernel: [    0.201769] pci 0000:03:06.0: PME# supported from D0 D2 D3hot
Dec 15 15:14:32 zack-A880G kernel: [    0.201816] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
Dec 15 15:14:32 zack-A880G kernel: [    0.201820] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
Dec 15 15:14:32 zack-A880G kernel: [    0.201826] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Dec 15 15:14:32 zack-A880G kernel: [    0.201828] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Dec 15 15:14:32 zack-A880G kernel: [    0.201830] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Dec 15 15:14:32 zack-A880G kernel: [    0.201832] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
Dec 15 15:14:32 zack-A880G kernel: [    0.201834] pci 0000:00:14.4:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
Dec 15 15:14:32 zack-A880G kernel: [    0.201836] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
Dec 15 15:14:32 zack-A880G kernel: [    0.201846] pci_bus 0000:00: on NUMA node 0
Dec 15 15:14:32 zack-A880G kernel: [    0.201851] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 15 15:14:32 zack-A880G kernel: [    0.202028] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Dec 15 15:14:32 zack-A880G kernel: [    0.202055] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Dec 15 15:14:32 zack-A880G kernel: [    0.202091] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
Dec 15 15:14:32 zack-A880G kernel: [    0.202150]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Dec 15 15:14:32 zack-A880G kernel: [    0.202152]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Dec 15 15:14:32 zack-A880G kernel: [    0.202153] ACPI _OSC control for PCIe not granted, disabling ASPM
Dec 15 15:14:32 zack-A880G kernel: [    0.205138] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 12 14 15)
Dec 15 15:14:32 zack-A880G kernel: [    0.205169] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
Dec 15 15:14:32 zack-A880G kernel: [    0.205197] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
Dec 15 15:14:32 zack-A880G kernel: [    0.205224] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
Dec 15 15:14:32 zack-A880G kernel: [    0.205250] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Dec 15 15:14:32 zack-A880G kernel: [    0.205277] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 *10 11 12 14 15)
Dec 15 15:14:32 zack-A880G kernel: [    0.205304] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 *9 12 14 15)
Dec 15 15:14:32 zack-A880G kernel: [    0.205330] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Dec 15 15:14:32 zack-A880G kernel: [    0.205407] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Dec 15 15:14:32 zack-A880G kernel: [    0.205409] vgaarb: loaded
Dec 15 15:14:32 zack-A880G kernel: [    0.205410] vgaarb: bridge control possible 0000:01:00.0
Dec 15 15:14:32 zack-A880G kernel: [    0.205545] SCSI subsystem initialized
Dec 15 15:14:32 zack-A880G kernel: [    0.205579] libata version 3.00 loaded.
Dec 15 15:14:32 zack-A880G kernel: [    0.205593] ACPI: bus type usb registered
Dec 15 15:14:32 zack-A880G kernel: [    0.205608] usbcore: registered new interface driver usbfs
Dec 15 15:14:32 zack-A880G kernel: [    0.205615] usbcore: registered new interface driver hub
Dec 15 15:14:32 zack-A880G kernel: [    0.205629] usbcore: registered new device driver usb
Dec 15 15:14:32 zack-A880G kernel: [    0.205681] PCI: Using ACPI for IRQ routing
Dec 15 15:14:32 zack-A880G kernel: [    0.205684] PCI: pci_cache_line_size set to 64 bytes
Dec 15 15:14:32 zack-A880G kernel: [    0.205747] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.205749] e820: reserve RAM buffer [mem 0x7ffb0000-0x7fffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.205817] NetLabel: Initializing
Dec 15 15:14:32 zack-A880G kernel: [    0.205818] NetLabel:  domain hash size = 128
Dec 15 15:14:32 zack-A880G kernel: [    0.205818] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 15 15:14:32 zack-A880G kernel: [    0.205826] NetLabel:  unlabeled traffic allowed by default
Dec 15 15:14:32 zack-A880G kernel: [    0.205886] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Dec 15 15:14:32 zack-A880G kernel: [    0.205889] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Dec 15 15:14:32 zack-A880G kernel: [    0.207908] Switching to clocksource hpet
Dec 15 15:14:32 zack-A880G kernel: [    0.212520] AppArmor: AppArmor Filesystem Enabled
Dec 15 15:14:32 zack-A880G kernel: [    0.212545] pnp: PnP ACPI init
Dec 15 15:14:32 zack-A880G kernel: [    0.212558] ACPI: bus type pnp registered
Dec 15 15:14:32 zack-A880G kernel: [    0.212656] pnp 00:00: [bus 00-ff]
Dec 15 15:14:32 zack-A880G kernel: [    0.212659] pnp 00:00: [io  0x0cf8-0x0cff]
Dec 15 15:14:32 zack-A880G kernel: [    0.212661] pnp 00:00: [io  0x0000-0x0cf7 window]
Dec 15 15:14:32 zack-A880G kernel: [    0.212663] pnp 00:00: [io  0x0d00-0xffff window]
Dec 15 15:14:32 zack-A880G kernel: [    0.212665] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Dec 15 15:14:32 zack-A880G kernel: [    0.212666] pnp 00:00: [mem 0x000d0000-0x000dffff window]
Dec 15 15:14:32 zack-A880G kernel: [    0.212668] pnp 00:00: [mem 0x80000000-0xdfffffff window]
Dec 15 15:14:32 zack-A880G kernel: [    0.212670] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
Dec 15 15:14:32 zack-A880G kernel: [    0.212708] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Dec 15 15:14:32 zack-A880G kernel: [    0.212781] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Dec 15 15:14:32 zack-A880G kernel: [    0.212783] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Dec 15 15:14:32 zack-A880G kernel: [    0.212820] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 15 15:14:32 zack-A880G kernel: [    0.212853] pnp 00:02: [dma 4]
Dec 15 15:14:32 zack-A880G kernel: [    0.212855] pnp 00:02: [io  0x0000-0x000f]
Dec 15 15:14:32 zack-A880G kernel: [    0.212856] pnp 00:02: [io  0x0081-0x0083]
Dec 15 15:14:32 zack-A880G kernel: [    0.212858] pnp 00:02: [io  0x0087]
Dec 15 15:14:32 zack-A880G kernel: [    0.212860] pnp 00:02: [io  0x0089-0x008b]
Dec 15 15:14:32 zack-A880G kernel: [    0.212861] pnp 00:02: [io  0x008f]
Dec 15 15:14:32 zack-A880G kernel: [    0.212863] pnp 00:02: [io  0x00c0-0x00df]
Dec 15 15:14:32 zack-A880G kernel: [    0.212880] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Dec 15 15:14:32 zack-A880G kernel: [    0.212887] pnp 00:03: [io  0x0070-0x0071]
Dec 15 15:14:32 zack-A880G kernel: [    0.212900] pnp 00:03: [irq 8]
Dec 15 15:14:32 zack-A880G kernel: [    0.212917] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Dec 15 15:14:32 zack-A880G kernel: [    0.212922] pnp 00:04: [io  0x0061]
Dec 15 15:14:32 zack-A880G kernel: [    0.212941] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Dec 15 15:14:32 zack-A880G kernel: [    0.212947] pnp 00:05: [io  0x00f0-0x00ff]
Dec 15 15:14:32 zack-A880G kernel: [    0.212954] pnp 00:05: [irq 13]
Dec 15 15:14:32 zack-A880G kernel: [    0.212971] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Dec 15 15:14:32 zack-A880G kernel: [    0.213764] pnp 00:06: [io  0x03f8-0x03ff]
Dec 15 15:14:32 zack-A880G kernel: [    0.213767] pnp 00:06: [irq 4]
Dec 15 15:14:32 zack-A880G kernel: [    0.213769] pnp 00:06: [dma 0 disabled]
Dec 15 15:14:32 zack-A880G kernel: [    0.213837] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
Dec 15 15:14:32 zack-A880G kernel: [    0.214541] pnp 00:07: [io  0x0378-0x037f]
Dec 15 15:14:32 zack-A880G kernel: [    0.214544] pnp 00:07: [irq 7]
Dec 15 15:14:32 zack-A880G kernel: [    0.214546] pnp 00:07: [dma 0 disabled]
Dec 15 15:14:32 zack-A880G kernel: [    0.214732] pnp 00:07: Plug and Play ACPI device, IDs PNP0400 (active)
Dec 15 15:14:32 zack-A880G kernel: [    0.214914] pnp 00:08: [mem 0xfed00000-0xfed003ff]
Dec 15 15:14:32 zack-A880G kernel: [    0.214934] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (active)
Dec 15 15:14:32 zack-A880G kernel: [    0.214989] pnp 00:09: [io  0x0060]
Dec 15 15:14:32 zack-A880G kernel: [    0.214990] pnp 00:09: [io  0x0064]
Dec 15 15:14:32 zack-A880G kernel: [    0.214992] pnp 00:09: [mem 0xfec00000-0xfec00fff]
Dec 15 15:14:32 zack-A880G kernel: [    0.214994] pnp 00:09: [mem 0xfee00000-0xfee00fff]
Dec 15 15:14:32 zack-A880G kernel: [    0.215024] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215026] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215029] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 15 15:14:32 zack-A880G kernel: [    0.215130] pnp 00:0a: [io  0x0010-0x001f]
Dec 15 15:14:32 zack-A880G kernel: [    0.215132] pnp 00:0a: [io  0x0022-0x003f]
Dec 15 15:14:32 zack-A880G kernel: [    0.215133] pnp 00:0a: [io  0x0062-0x0063]
Dec 15 15:14:32 zack-A880G kernel: [    0.215135] pnp 00:0a: [io  0x0065-0x006f]
Dec 15 15:14:32 zack-A880G kernel: [    0.215136] pnp 00:0a: [io  0x0072-0x007f]
Dec 15 15:14:32 zack-A880G kernel: [    0.215138] pnp 00:0a: [io  0x0080]
Dec 15 15:14:32 zack-A880G kernel: [    0.215139] pnp 00:0a: [io  0x0084-0x0086]
Dec 15 15:14:32 zack-A880G kernel: [    0.215141] pnp 00:0a: [io  0x0088]
Dec 15 15:14:32 zack-A880G kernel: [    0.215142] pnp 00:0a: [io  0x008c-0x008e]
Dec 15 15:14:32 zack-A880G kernel: [    0.215144] pnp 00:0a: [io  0x0090-0x009f]
Dec 15 15:14:32 zack-A880G kernel: [    0.215145] pnp 00:0a: [io  0x00a2-0x00bf]
Dec 15 15:14:32 zack-A880G kernel: [    0.215147] pnp 00:0a: [io  0x00b1]
Dec 15 15:14:32 zack-A880G kernel: [    0.215148] pnp 00:0a: [io  0x00e0-0x00ef]
Dec 15 15:14:32 zack-A880G kernel: [    0.215150] pnp 00:0a: [io  0x04d0-0x04d1]
Dec 15 15:14:32 zack-A880G kernel: [    0.215152] pnp 00:0a: [io  0x040b]
Dec 15 15:14:32 zack-A880G kernel: [    0.215153] pnp 00:0a: [io  0x04d6]
Dec 15 15:14:32 zack-A880G kernel: [    0.215155] pnp 00:0a: [io  0x0c00-0x0c01]
Dec 15 15:14:32 zack-A880G kernel: [    0.215156] pnp 00:0a: [io  0x0c14]
Dec 15 15:14:32 zack-A880G kernel: [    0.215158] pnp 00:0a: [io  0x0c50-0x0c51]
Dec 15 15:14:32 zack-A880G kernel: [    0.215159] pnp 00:0a: [io  0x0c52]
Dec 15 15:14:32 zack-A880G kernel: [    0.215161] pnp 00:0a: [io  0x0c6c]
Dec 15 15:14:32 zack-A880G kernel: [    0.215162] pnp 00:0a: [io  0x0c6f]
Dec 15 15:14:32 zack-A880G kernel: [    0.215164] pnp 00:0a: [io  0x0cd0-0x0cd1]
Dec 15 15:14:32 zack-A880G kernel: [    0.215165] pnp 00:0a: [io  0x0cd2-0x0cd3]
Dec 15 15:14:32 zack-A880G kernel: [    0.215167] pnp 00:0a: [io  0x0cd4-0x0cd5]
Dec 15 15:14:32 zack-A880G kernel: [    0.215168] pnp 00:0a: [io  0x0cd6-0x0cd7]
Dec 15 15:14:32 zack-A880G kernel: [    0.215170] pnp 00:0a: [io  0x0cd8-0x0cdf]
Dec 15 15:14:32 zack-A880G kernel: [    0.215172] pnp 00:0a: [io  0x0800-0x089f]
Dec 15 15:14:32 zack-A880G kernel: [    0.215173] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
Dec 15 15:14:32 zack-A880G kernel: [    0.215176] pnp 00:0a: [io  0x0b00-0x0b0f]
Dec 15 15:14:32 zack-A880G kernel: [    0.215178] pnp 00:0a: [io  0x0b20-0x0b3f]
Dec 15 15:14:32 zack-A880G kernel: [    0.215179] pnp 00:0a: [io  0x0900-0x090f]
Dec 15 15:14:32 zack-A880G kernel: [    0.215181] pnp 00:0a: [io  0x0910-0x091f]
Dec 15 15:14:32 zack-A880G kernel: [    0.215183] pnp 00:0a: [io  0xfe00-0xfefe]
Dec 15 15:14:32 zack-A880G kernel: [    0.215184] pnp 00:0a: [io  0x0060]
Dec 15 15:14:32 zack-A880G kernel: [    0.215185] pnp 00:0a: [io  0x0064]
Dec 15 15:14:32 zack-A880G kernel: [    0.215187] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.215189] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
Dec 15 15:14:32 zack-A880G kernel: [    0.215248] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215250] system 00:0a: [io  0x040b] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215252] system 00:0a: [io  0x04d6] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215254] system 00:0a: [io  0x0c00-0x0c01] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215256] system 00:0a: [io  0x0c14] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215258] system 00:0a: [io  0x0c50-0x0c51] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215260] system 00:0a: [io  0x0c52] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215262] system 00:0a: [io  0x0c6c] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215263] system 00:0a: [io  0x0c6f] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215265] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215267] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215269] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215271] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215273] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215275] system 00:0a: [io  0x0800-0x089f] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215277] system 00:0a: [io  0x0b00-0x0b0f] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215279] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215281] system 00:0a: [io  0x0900-0x090f] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215283] system 00:0a: [io  0x0910-0x091f] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215286] system 00:0a: [io  0xfe00-0xfefe] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215288] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215290] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215292] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 15 15:14:32 zack-A880G kernel: [    0.215414] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
Dec 15 15:14:32 zack-A880G kernel: [    0.215415] pnp 00:0b: [io  0x0e00-0x0e0f]
Dec 15 15:14:32 zack-A880G kernel: [    0.215417] pnp 00:0b: [io  0x0e80-0x0e8f]
Dec 15 15:14:32 zack-A880G kernel: [    0.215419] pnp 00:0b: [io  0x0f40-0x0f4f]
Dec 15 15:14:32 zack-A880G kernel: [    0.215420] pnp 00:0b: [io  0x0a30-0x0a3f]
Dec 15 15:14:32 zack-A880G kernel: [    0.215451] system 00:0b: [io  0x0e00-0x0e0f] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215453] system 00:0b: [io  0x0e80-0x0e8f] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215455] system 00:0b: [io  0x0f40-0x0f4f] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215457] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215459] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 15 15:14:32 zack-A880G kernel: [    0.215481] pnp 00:0c: [mem 0xe0000000-0xefffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.215510] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215512] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 15 15:14:32 zack-A880G kernel: [    0.215703] pnp 00:0d: [mem 0x00000000-0x0009ffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.215705] pnp 00:0d: [mem 0x000c0000-0x000cffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.215706] pnp 00:0d: [mem 0x000e0000-0x000fffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.215708] pnp 00:0d: [mem 0x00100000-0x7fffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.215710] pnp 00:0d: [mem 0xfec00000-0xffffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.215744] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215746] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215748] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215750] system 00:0d: [mem 0x00100000-0x7fffffff] could not be reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215753] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
Dec 15 15:14:32 zack-A880G kernel: [    0.215755] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
Dec 15 15:14:32 zack-A880G kernel: [    0.215835] pnp: PnP ACPI: found 14 devices
Dec 15 15:14:32 zack-A880G kernel: [    0.215836] ACPI: ACPI bus type pnp unregistered
Dec 15 15:14:32 zack-A880G kernel: [    0.215838] PnPBIOS: Disabled by ACPI PNP
Dec 15 15:14:32 zack-A880G kernel: [    0.251323] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Dec 15 15:14:32 zack-A880G kernel: [    0.251326] pci 0000:00:02.0:   bridge window [io  0xc000-0xcfff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251329] pci 0000:00:02.0:   bridge window [mem 0xfcf00000-0xfdffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251332] pci 0000:00:02.0:   bridge window [mem 0xd6000000-0xdfffffff 64bit pref]
Dec 15 15:14:32 zack-A880G kernel: [    0.251335] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Dec 15 15:14:32 zack-A880G kernel: [    0.251337] pci 0000:00:07.0:   bridge window [io  0xd000-0xdfff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251340] pci 0000:00:07.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251342] pci 0000:00:07.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
Dec 15 15:14:32 zack-A880G kernel: [    0.251346] pci 0000:00:14.4: PCI bridge to [bus 03-03]
Dec 15 15:14:32 zack-A880G kernel: [    0.251348] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251378] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Dec 15 15:14:32 zack-A880G kernel: [    0.251380] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251382] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251383] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251385] pci_bus 0000:00: resource 8 [mem 0x80000000-0xdfffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251387] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251389] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251391] pci_bus 0000:01: resource 1 [mem 0xfcf00000-0xfdffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251393] pci_bus 0000:01: resource 2 [mem 0xd6000000-0xdfffffff 64bit pref]
Dec 15 15:14:32 zack-A880G kernel: [    0.251395] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251397] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251399] pci_bus 0000:02: resource 2 [mem 0xfbf00000-0xfbffffff 64bit pref]
Dec 15 15:14:32 zack-A880G kernel: [    0.251401] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251403] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
Dec 15 15:14:32 zack-A880G kernel: [    0.251404] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251406] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251408] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251410] pci_bus 0000:03: resource 8 [mem 0x80000000-0xdfffffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251412] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
Dec 15 15:14:32 zack-A880G kernel: [    0.251438] NET: Registered protocol family 2
Dec 15 15:14:32 zack-A880G kernel: [    0.251482] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 15 15:14:32 zack-A880G kernel: [    0.251589] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 15 15:14:32 zack-A880G kernel: [    0.252034] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 15 15:14:32 zack-A880G kernel: [    0.252262] TCP: Hash tables configured (established 131072 bind 65536)
Dec 15 15:14:32 zack-A880G kernel: [    0.252263] TCP: reno registered
Dec 15 15:14:32 zack-A880G kernel: [    0.252266] UDP hash table entries: 512 (order: 2, 16384 bytes)
Dec 15 15:14:32 zack-A880G kernel: [    0.252273] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Dec 15 15:14:32 zack-A880G kernel: [    0.252340] NET: Registered protocol family 1
Dec 15 15:14:32 zack-A880G kernel: [    1.277942] pci 0000:01:00.0: Boot video device
Dec 15 15:14:32 zack-A880G kernel: [    1.277958] PCI: CLS 64 bytes, default 64
Dec 15 15:14:32 zack-A880G kernel: [    1.278123] LVT offset 1 assigned for vector 0x400
Dec 15 15:14:32 zack-A880G kernel: [    1.278129] IBS: LVT offset 1 assigned
Dec 15 15:14:32 zack-A880G kernel: [    1.278145] perf: AMD IBS detected (0x0000001f)
Dec 15 15:14:32 zack-A880G kernel: [    1.278254] audit: initializing netlink socket (disabled)
Dec 15 15:14:32 zack-A880G kernel: [    1.278262] type=2000 audit(1387149256.172:1): initialized
Dec 15 15:14:32 zack-A880G kernel: [    1.295938] Trying to unpack rootfs image as initramfs...
Dec 15 15:14:32 zack-A880G kernel: [    1.318337] highmem bounce pool size: 64 pages
Dec 15 15:14:32 zack-A880G kernel: [    1.318350] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 15 15:14:32 zack-A880G kernel: [    1.329837] VFS: Disk quotas dquot_6.5.2
Dec 15 15:14:32 zack-A880G kernel: [    1.329883] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 15 15:14:32 zack-A880G kernel: [    1.330295] fuse init (API version 7.19)
Dec 15 15:14:32 zack-A880G kernel: [    1.330348] msgmni has been set to 1690
Dec 15 15:14:32 zack-A880G kernel: [    1.342087] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Dec 15 15:14:32 zack-A880G kernel: [    1.342124] io scheduler noop registered
Dec 15 15:14:32 zack-A880G kernel: [    1.342125] io scheduler deadline registered (default)
Dec 15 15:14:32 zack-A880G kernel: [    1.342131] io scheduler cfq registered
Dec 15 15:14:32 zack-A880G kernel: [    1.342237] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
Dec 15 15:14:32 zack-A880G kernel: [    1.342288] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
Dec 15 15:14:32 zack-A880G kernel: [    1.342331] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 15 15:14:32 zack-A880G kernel: [    1.342343] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 15 15:14:32 zack-A880G kernel: [    1.342435] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Dec 15 15:14:32 zack-A880G kernel: [    1.342439] ACPI: Power Button [PWRB]
Dec 15 15:14:32 zack-A880G kernel: [    1.342470] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Dec 15 15:14:32 zack-A880G kernel: [    1.342472] ACPI: Power Button [PWRF]
Dec 15 15:14:32 zack-A880G kernel: [    1.346171] thermal LNXTHERM:00: registered as thermal_zone0
Dec 15 15:14:32 zack-A880G kernel: [    1.346173] ACPI: Thermal Zone [THRM] (32 C)
Dec 15 15:14:32 zack-A880G kernel: [    1.346191] GHES: HEST is not enabled!
Dec 15 15:14:32 zack-A880G kernel: [    1.346252] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Dec 15 15:14:32 zack-A880G kernel: [    1.366657] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 15 15:14:32 zack-A880G kernel: [    1.369744] isapnp: Scanning for PnP cards...
Dec 15 15:14:32 zack-A880G kernel: [    1.458826] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 15 15:14:32 zack-A880G kernel: [    1.481978] Linux agpgart interface v0.103
Dec 15 15:14:32 zack-A880G kernel: [    1.483043] brd: module loaded
Dec 15 15:14:32 zack-A880G kernel: [    1.483509] loop: module loaded
Dec 15 15:14:32 zack-A880G kernel: [    1.483643] pata_acpi 0000:00:14.1: setting latency timer to 64
Dec 15 15:14:32 zack-A880G kernel: [    1.483830] Fixed MDIO Bus: probed
Dec 15 15:14:32 zack-A880G kernel: [    1.483861] tun: Universal TUN/TAP device driver, 1.6
Dec 15 15:14:32 zack-A880G kernel: [    1.483862] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 15 15:14:32 zack-A880G kernel: [    1.483886] PPP generic driver version 2.4.2
Dec 15 15:14:32 zack-A880G kernel: [    1.483910] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 15 15:14:32 zack-A880G kernel: [    1.483935] ehci_hcd 0000:00:12.2: EHCI Host Controller
Dec 15 15:14:32 zack-A880G kernel: [    1.483940] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Dec 15 15:14:32 zack-A880G kernel: [    1.483947] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Dec 15 15:14:32 zack-A880G kernel: [    1.483966] ehci_hcd 0000:00:12.2: debug port 1
Dec 15 15:14:32 zack-A880G kernel: [    1.483986] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfeaff800
Dec 15 15:14:32 zack-A880G kernel: [    1.527981] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Dec 15 15:14:32 zack-A880G kernel: [    1.528014] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Dec 15 15:14:32 zack-A880G kernel: [    1.528016] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:14:32 zack-A880G kernel: [    1.528017] usb usb1: Product: EHCI Host Controller
Dec 15 15:14:32 zack-A880G kernel: [    1.528019] usb usb1: Manufacturer: Linux 3.5.0-43-generic ehci_hcd
Dec 15 15:14:32 zack-A880G kernel: [    1.528021] usb usb1: SerialNumber: 0000:00:12.2
Dec 15 15:14:32 zack-A880G kernel: [    1.605555] hub 1-0:1.0: USB hub found
Dec 15 15:14:32 zack-A880G kernel: [    1.605561] hub 1-0:1.0: 6 ports detected
Dec 15 15:14:32 zack-A880G kernel: [    1.605648] ehci_hcd 0000:00:13.2: EHCI Host Controller
Dec 15 15:14:32 zack-A880G kernel: [    1.605653] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Dec 15 15:14:32 zack-A880G kernel: [    1.605660] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Dec 15 15:14:32 zack-A880G kernel: [    1.605680] ehci_hcd 0000:00:13.2: debug port 1
Dec 15 15:14:32 zack-A880G kernel: [    1.605703] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfeaff400
Dec 15 15:14:32 zack-A880G kernel: [    1.617319] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Dec 15 15:14:32 zack-A880G kernel: [    1.617341] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Dec 15 15:14:32 zack-A880G kernel: [    1.617344] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:14:32 zack-A880G kernel: [    1.617346] usb usb2: Product: EHCI Host Controller
Dec 15 15:14:32 zack-A880G kernel: [    1.617347] usb usb2: Manufacturer: Linux 3.5.0-43-generic ehci_hcd
Dec 15 15:14:32 zack-A880G kernel: [    1.617349] usb usb2: SerialNumber: 0000:00:13.2
Dec 15 15:14:32 zack-A880G kernel: [    1.617437] hub 2-0:1.0: USB hub found
Dec 15 15:14:32 zack-A880G kernel: [    1.617441] hub 2-0:1.0: 6 ports detected
Dec 15 15:14:32 zack-A880G kernel: [    1.617510] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 15 15:14:32 zack-A880G kernel: [    1.617562] ohci_hcd 0000:00:12.0: OHCI Host Controller
Dec 15 15:14:32 zack-A880G kernel: [    1.617567] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Dec 15 15:14:32 zack-A880G kernel: [    1.617591] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfeafe000
Dec 15 15:14:32 zack-A880G kernel: [    1.681167] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Dec 15 15:14:32 zack-A880G kernel: [    1.681171] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:14:32 zack-A880G kernel: [    1.681173] usb usb3: Product: OHCI Host Controller
Dec 15 15:14:32 zack-A880G kernel: [    1.681175] usb usb3: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
Dec 15 15:14:32 zack-A880G kernel: [    1.681176] usb usb3: SerialNumber: 0000:00:12.0
Dec 15 15:14:32 zack-A880G kernel: [    1.681271] hub 3-0:1.0: USB hub found
Dec 15 15:14:32 zack-A880G kernel: [    1.681280] hub 3-0:1.0: 3 ports detected
Dec 15 15:14:32 zack-A880G kernel: [    1.681346] ohci_hcd 0000:00:12.1: OHCI Host Controller
Dec 15 15:14:32 zack-A880G kernel: [    1.681350] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Dec 15 15:14:32 zack-A880G kernel: [    1.681366] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfeafd000
Dec 15 15:14:32 zack-A880G kernel: [    1.844963] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Dec 15 15:14:32 zack-A880G kernel: [    1.844967] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:14:32 zack-A880G kernel: [    1.844969] usb usb4: Product: OHCI Host Controller
Dec 15 15:14:32 zack-A880G kernel: [    1.844971] usb usb4: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
Dec 15 15:14:32 zack-A880G kernel: [    1.844973] usb usb4: SerialNumber: 0000:00:12.1
Dec 15 15:14:32 zack-A880G kernel: [    1.845064] hub 4-0:1.0: USB hub found
Dec 15 15:14:32 zack-A880G kernel: [    1.845074] hub 4-0:1.0: 3 ports detected
Dec 15 15:14:32 zack-A880G kernel: [    1.845141] ohci_hcd 0000:00:13.0: OHCI Host Controller
Dec 15 15:14:32 zack-A880G kernel: [    1.845146] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Dec 15 15:14:32 zack-A880G kernel: [    1.845173] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfeafc000
Dec 15 15:14:32 zack-A880G kernel: [    1.908921] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Dec 15 15:14:32 zack-A880G kernel: [    1.908925] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:14:32 zack-A880G kernel: [    1.908927] usb usb5: Product: OHCI Host Controller
Dec 15 15:14:32 zack-A880G kernel: [    1.908929] usb usb5: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
Dec 15 15:14:32 zack-A880G kernel: [    1.908930] usb usb5: SerialNumber: 0000:00:13.0
Dec 15 15:14:32 zack-A880G kernel: [    1.909018] hub 5-0:1.0: USB hub found
Dec 15 15:14:32 zack-A880G kernel: [    1.909028] hub 5-0:1.0: 3 ports detected
Dec 15 15:14:32 zack-A880G kernel: [    1.909093] ohci_hcd 0000:00:13.1: OHCI Host Controller
Dec 15 15:14:32 zack-A880G kernel: [    1.909098] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Dec 15 15:14:32 zack-A880G kernel: [    1.909114] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfeafb000
Dec 15 15:14:32 zack-A880G kernel: [    1.919228] Freeing initrd memory: 15192k freed
Dec 15 15:14:32 zack-A880G kernel: [    1.968386] isapnp: No Plug & Play device found
Dec 15 15:14:32 zack-A880G kernel: [    1.972415] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
Dec 15 15:14:32 zack-A880G kernel: [    1.972417] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:14:32 zack-A880G kernel: [    1.972419] usb usb6: Product: OHCI Host Controller
Dec 15 15:14:32 zack-A880G kernel: [    1.972421] usb usb6: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
Dec 15 15:14:32 zack-A880G kernel: [    1.972423] usb usb6: SerialNumber: 0000:00:13.1
Dec 15 15:14:32 zack-A880G kernel: [    1.972522] hub 6-0:1.0: USB hub found
Dec 15 15:14:32 zack-A880G kernel: [    1.972531] hub 6-0:1.0: 3 ports detected
Dec 15 15:14:32 zack-A880G kernel: [    1.972607] ohci_hcd 0000:00:14.5: OHCI Host Controller
Dec 15 15:14:32 zack-A880G kernel: [    1.972611] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
Dec 15 15:14:32 zack-A880G kernel: [    1.972631] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfeafa000
Dec 15 15:14:32 zack-A880G kernel: [    2.032518] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
Dec 15 15:14:32 zack-A880G kernel: [    2.032522] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 15 15:14:32 zack-A880G kernel: [    2.032524] usb usb7: Product: OHCI Host Controller
Dec 15 15:14:32 zack-A880G kernel: [    2.032526] usb usb7: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
Dec 15 15:14:32 zack-A880G kernel: [    2.032527] usb usb7: SerialNumber: 0000:00:14.5
Dec 15 15:14:32 zack-A880G kernel: [    2.032616] hub 7-0:1.0: USB hub found
Dec 15 15:14:32 zack-A880G kernel: [    2.032626] hub 7-0:1.0: 2 ports detected
Dec 15 15:14:32 zack-A880G kernel: [    2.032672] uhci_hcd: USB Universal Host Controller Interface driver
Dec 15 15:14:32 zack-A880G kernel: [    2.032729] usbcore: registered new interface driver libusual
Dec 15 15:14:32 zack-A880G kernel: [    2.032760] i8042: PNP: No PS/2 controller found. Probing ports directly.
Dec 15 15:14:32 zack-A880G kernel: [    2.033198] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 15 15:14:32 zack-A880G kernel: [    2.033202] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 15 15:14:32 zack-A880G kernel: [    2.033268] mousedev: PS/2 mouse device common for all mice
Dec 15 15:14:32 zack-A880G kernel: [    2.033342] rtc_cmos 00:03: RTC can wake from S4
Dec 15 15:14:32 zack-A880G kernel: [    2.033434] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Dec 15 15:14:32 zack-A880G kernel: [    2.033457] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Dec 15 15:14:32 zack-A880G kernel: [    2.033495] device-mapper: uevent: version 1.0.3
Dec 15 15:14:32 zack-A880G kernel: [    2.033535] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Dec 15 15:14:32 zack-A880G kernel: [    2.033547] EISA: Probing bus 0 at eisa.0
Dec 15 15:14:32 zack-A880G kernel: [    2.033548] EISA: Cannot allocate resource for mainboard
Dec 15 15:14:32 zack-A880G kernel: [    2.033550] Cannot allocate resource for EISA slot 1
Dec 15 15:14:32 zack-A880G kernel: [    2.033551] Cannot allocate resource for EISA slot 2
Dec 15 15:14:32 zack-A880G kernel: [    2.033552] Cannot allocate resource for EISA slot 3
Dec 15 15:14:32 zack-A880G kernel: [    2.033553] Cannot allocate resource for EISA slot 4
Dec 15 15:14:32 zack-A880G kernel: [    2.033554] Cannot allocate resource for EISA slot 5
Dec 15 15:14:32 zack-A880G kernel: [    2.033555] Cannot allocate resource for EISA slot 6
Dec 15 15:14:32 zack-A880G kernel: [    2.033556] Cannot allocate resource for EISA slot 7
Dec 15 15:14:32 zack-A880G kernel: [    2.033557] Cannot allocate resource for EISA slot 8
Dec 15 15:14:32 zack-A880G kernel: [    2.033558] EISA: Detected 0 cards.
Dec 15 15:14:32 zack-A880G kernel: [    2.033567] cpuidle: using governor ladder
Dec 15 15:14:32 zack-A880G kernel: [    2.033568] cpuidle: using governor menu
Dec 15 15:14:32 zack-A880G kernel: [    2.033570] EFI Variables Facility v0.08 2004-May-17
Dec 15 15:14:32 zack-A880G kernel: [    2.033711] ashmem: initialized
Dec 15 15:14:32 zack-A880G kernel: [    2.033791] TCP: cubic registered
Dec 15 15:14:32 zack-A880G kernel: [    2.033856] NET: Registered protocol family 10
Dec 15 15:14:32 zack-A880G kernel: [    2.033985] NET: Registered protocol family 17
Dec 15 15:14:32 zack-A880G kernel: [    2.033991] Key type dns_resolver registered
Dec 15 15:14:32 zack-A880G kernel: [    2.034026] Using IPI No-Shortcut mode
Dec 15 15:14:32 zack-A880G kernel: [    2.034071] PM: Hibernation image not present or could not be loaded.
Dec 15 15:14:32 zack-A880G kernel: [    2.034079] registered taskstats version 1
Dec 15 15:14:32 zack-A880G kernel: [    2.035799] Key type trusted registered
Dec 15 15:14:32 zack-A880G kernel: [    2.037209] Key type encrypted registered
Dec 15 15:14:32 zack-A880G kernel: [    2.038824]   Magic number: 9:772:251
Dec 15 15:14:32 zack-A880G kernel: [    2.038909] rtc_cmos 00:03: setting system clock to 2013-12-15 23:14:17 UTC (1387149257)
Dec 15 15:14:32 zack-A880G kernel: [    2.038934] powernow-k8: Found 1 AMD Sempron(tm) 145 Processor (1 cpu cores) (version 2.20.00)
Dec 15 15:14:32 zack-A880G kernel: [    2.038960] powernow-k8:    0 : pstate 0 (2800 MHz)
Dec 15 15:14:32 zack-A880G kernel: [    2.038961] powernow-k8:    1 : pstate 1 (2000 MHz)
Dec 15 15:14:32 zack-A880G kernel: [    2.038962] powernow-k8:    2 : pstate 2 (1600 MHz)
Dec 15 15:14:32 zack-A880G kernel: [    2.038963] powernow-k8:    3 : pstate 3 (800 MHz)
Dec 15 15:14:32 zack-A880G kernel: [    2.039016] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 15 15:14:32 zack-A880G kernel: [    2.039017] EDD information not available.
Dec 15 15:14:32 zack-A880G kernel: [    2.039111] Freeing unused kernel memory: 764k freed
Dec 15 15:14:32 zack-A880G kernel: [    2.039340] Write protecting the kernel text: 6060k
Dec 15 15:14:32 zack-A880G kernel: [    2.039352] Write protecting the kernel read-only data: 2484k
Dec 15 15:14:32 zack-A880G kernel: [    2.039353] NX-protecting the kernel data: 4180k
Dec 15 15:14:32 zack-A880G kernel: [    2.107929] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 15 15:14:32 zack-A880G kernel: [    2.108005] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
Dec 15 15:14:32 zack-A880G kernel: [    2.108139] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xf8418000, 00:30:67:8c:c9:b2, XID 081000c0 IRQ 42
Dec 15 15:14:32 zack-A880G kernel: [    2.108141] r8169 0000:02:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Dec 15 15:14:32 zack-A880G kernel: [    2.111251] ahci 0000:00:11.0: version 3.0
Dec 15 15:14:32 zack-A880G kernel: [    2.111371] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Dec 15 15:14:32 zack-A880G kernel: [    2.111374] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
Dec 15 15:14:32 zack-A880G kernel: [    2.125557] scsi0 : ahci
Dec 15 15:14:32 zack-A880G kernel: [    2.128396] scsi1 : ahci
Dec 15 15:14:32 zack-A880G kernel: [    2.130127] scsi2 : ahci
Dec 15 15:14:32 zack-A880G kernel: [    2.131794] scsi3 : ahci
Dec 15 15:14:32 zack-A880G kernel: [    2.131885] ata1: SATA max UDMA/133 abar m1024@0xfeaffc00 port 0xfeaffd00 irq 22
Dec 15 15:14:32 zack-A880G kernel: [    2.131888] ata2: SATA max UDMA/133 abar m1024@0xfeaffc00 port 0xfeaffd80 irq 22
Dec 15 15:14:32 zack-A880G kernel: [    2.131891] ata3: SATA max UDMA/133 abar m1024@0xfeaffc00 port 0xfeaffe00 irq 22
Dec 15 15:14:32 zack-A880G kernel: [    2.131894] ata4: SATA max UDMA/133 abar m1024@0xfeaffc00 port 0xfeaffe80 irq 22
Dec 15 15:14:32 zack-A880G kernel: [    2.152321] scsi4 : pata_atiixp
Dec 15 15:14:32 zack-A880G kernel: [    2.155321] scsi5 : pata_atiixp
Dec 15 15:14:32 zack-A880G kernel: [    2.155827] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Dec 15 15:14:32 zack-A880G kernel: [    2.155829] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Dec 15 15:14:32 zack-A880G kernel: [    2.291984] Refined TSC clocksource calibration: 2800.158 MHz.
Dec 15 15:14:32 zack-A880G kernel: [    2.291990] Switching to clocksource tsc
Dec 15 15:14:32 zack-A880G kernel: [    2.303960] usb 3-3: new low-speed USB device number 2 using ohci_hcd
Dec 15 15:14:32 zack-A880G kernel: [    2.337932] ata6.00: ATA-7: Maxtor 6L200P0, BAH41G10, max UDMA/133
Dec 15 15:14:32 zack-A880G kernel: [    2.337936] ata6.00: 398297088 sectors, multi 16: LBA48 
Dec 15 15:14:32 zack-A880G kernel: [    2.338354] ata6.01: ATA-5: QUANTUM FIREBALLlct20 10, APL.0900, max UDMA/100
Dec 15 15:14:32 zack-A880G kernel: [    2.338358] ata6.01: 20044080 sectors, multi 8: LBA 
Dec 15 15:14:32 zack-A880G kernel: [    2.353859] ata6.00: configured for UDMA/100
Dec 15 15:14:32 zack-A880G kernel: [    2.368595] ata6.01: configured for UDMA/100
Dec 15 15:14:32 zack-A880G kernel: [    2.447697] ata2: SATA link down (SStatus 0 SControl 300)
Dec 15 15:14:32 zack-A880G kernel: [    2.451690] ata3: SATA link down (SStatus 0 SControl 300)
Dec 15 15:14:32 zack-A880G kernel: [    2.451726] ata4: SATA link down (SStatus 0 SControl 300)
Dec 15 15:14:32 zack-A880G kernel: [    2.472639] usb 3-3: New USB device found, idVendor=046d, idProduct=c512
Dec 15 15:14:32 zack-A880G kernel: [    2.472643] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Dec 15 15:14:32 zack-A880G kernel: [    2.472645] usb 3-3: Product: USB Receiver
Dec 15 15:14:32 zack-A880G kernel: [    2.472647] usb 3-3: Manufacturer: Logitech
Dec 15 15:14:32 zack-A880G kernel: [    2.590650] usbcore: registered new interface driver usbhid
Dec 15 15:14:32 zack-A880G kernel: [    2.590653] usbhid: USB HID core driver
Dec 15 15:14:32 zack-A880G kernel: [    2.619368] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 15 15:14:32 zack-A880G kernel: [    2.621845] ata1.00: ATAPI: ASUS    DRW-24B3LT, 1.00, max UDMA/100
Dec 15 15:14:32 zack-A880G kernel: [    2.622684] ata1.00: configured for UDMA/100
Dec 15 15:14:32 zack-A880G kernel: [    2.624641] scsi 0:0:0:0: CD-ROM            ASUS     DRW-24B3LT       1.00 PQ: 0 ANSI: 5
Dec 15 15:14:32 zack-A880G kernel: [    2.628023] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 15 15:14:32 zack-A880G kernel: [    2.628027] cdrom: Uniform CD-ROM driver Revision: 3.20
Dec 15 15:14:32 zack-A880G kernel: [    2.628125] sr 0:0:0:0: Attached scsi CD-ROM sr0
Dec 15 15:14:32 zack-A880G kernel: [    2.628176] sr 0:0:0:0: Attached scsi generic sg0 type 5
Dec 15 15:14:32 zack-A880G kernel: [    2.628283] scsi 5:0:0:0: Direct-Access     ATA      Maxtor 6L200P0   BAH4 PQ: 0 ANSI: 5
Dec 15 15:14:32 zack-A880G kernel: [    2.628369] sd 5:0:0:0: [sda] 398297088 512-byte logical blocks: (203 GB/189 GiB)
Dec 15 15:14:32 zack-A880G kernel: [    2.628402] sd 5:0:0:0: [sda] Write Protect is off
Dec 15 15:14:32 zack-A880G kernel: [    2.628405] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 15 15:14:32 zack-A880G kernel: [    2.628416] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 15 15:14:32 zack-A880G kernel: [    2.628584] sd 5:0:0:0: Attached scsi generic sg1 type 0
Dec 15 15:14:32 zack-A880G kernel: [    2.667821]  sda: sda1 sda2 < sda5 >
Dec 15 15:14:32 zack-A880G kernel: [    2.668034] sd 5:0:0:0: [sda] Attached SCSI disk
Dec 15 15:14:32 zack-A880G kernel: [    2.668087] scsi 5:0:1:0: Direct-Access     ATA      QUANTUM FIREBALL APL. PQ: 0 ANSI: 5
Dec 15 15:14:32 zack-A880G kernel: [    2.668178] sd 5:0:1:0: Attached scsi generic sg2 type 0
Dec 15 15:14:32 zack-A880G kernel: [    2.668215] sd 5:0:1:0: [sdb] 20044080 512-byte logical blocks: (10.2 GB/9.55 GiB)
Dec 15 15:14:32 zack-A880G kernel: [    2.668239] sd 5:0:1:0: [sdb] Write Protect is off
Dec 15 15:14:32 zack-A880G kernel: [    2.668241] sd 5:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Dec 15 15:14:32 zack-A880G kernel: [    2.668252] sd 5:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 15 15:14:32 zack-A880G kernel: [    2.702020]  sdb: sdb1 sdb2 < sdb5 >
Dec 15 15:14:32 zack-A880G kernel: [    2.702233] sd 5:0:1:0: [sdb] Attached SCSI disk
Dec 15 15:14:32 zack-A880G kernel: [    2.713440] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input2
Dec 15 15:14:32 zack-A880G kernel: [    2.713539] logitech 0003:046D:C512.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:12.0-3/input0
Dec 15 15:14:32 zack-A880G kernel: [    2.714182] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1/input/input3
Dec 15 15:14:32 zack-A880G kernel: [    2.714332] logitech 0003:046D:C512.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:12.0-3/input1
Dec 15 15:14:32 zack-A880G kernel: [    5.387448] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Dec 15 15:14:32 zack-A880G kernel: [    5.387452] EXT4-fs (sda1): write access will be enabled during recovery
Dec 15 15:14:32 zack-A880G kernel: [    6.383926] EXT4-fs (sda1): recovery complete
Dec 15 15:14:32 zack-A880G kernel: [    6.396480] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Dec 15 15:14:32 zack-A880G kernel: [   16.438068] Adding 6141948k swap on /dev/sda5.  Priority:-1 extents:1 across:6141948k 
Dec 15 15:14:32 zack-A880G kernel: [   16.445565] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 15 15:14:32 zack-A880G kernel: [   16.517474] lp: driver loaded but no devices found
Dec 15 15:14:32 zack-A880G kernel: [   16.654027] wmi: Mapper loaded
Dec 15 15:14:32 zack-A880G kernel: [   16.720974] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Dec 15 15:14:32 zack-A880G kernel: [   16.724074] type=1400 audit(1387149272.208:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=522 comm="apparmor_parser"
Dec 15 15:14:32 zack-A880G kernel: [   16.724456] type=1400 audit(1387149272.208:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=522 comm="apparmor_parser"
Dec 15 15:14:32 zack-A880G kernel: [   16.724671] type=1400 audit(1387149272.212:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=522 comm="apparmor_parser"
Dec 15 15:14:32 zack-A880G kernel: [   16.823074] parport_pc 00:07: reported by Plug and Play ACPI
Dec 15 15:14:32 zack-A880G kernel: [   16.823131] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Dec 15 15:14:32 zack-A880G kernel: [   16.837032] ACPI Warning: 0x00000b00-0x00000b07 SystemIO conflicts with Region \SOR1 1 (20120320/utaddress-251)
Dec 15 15:14:32 zack-A880G kernel: [   16.837039] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Dec 15 15:14:32 zack-A880G kernel: [   16.861088] sp5100_tco: SP5100 TCO WatchDog Timer Driver v0.01
Dec 15 15:14:32 zack-A880G kernel: [   16.862164] sp5100_tco: mmio address 0xfec000f0 already in use
Dec 15 15:14:32 zack-A880G kernel: [   16.862636] Bluetooth: Core ver 2.16
Dec 15 15:14:32 zack-A880G kernel: [   16.862648] NET: Registered protocol family 31
Dec 15 15:14:32 zack-A880G kernel: [   16.862649] Bluetooth: HCI device and connection manager initialized
Dec 15 15:14:32 zack-A880G kernel: [   16.862651] Bluetooth: HCI socket layer initialized
Dec 15 15:14:32 zack-A880G kernel: [   16.862652] Bluetooth: L2CAP socket layer initialized
Dec 15 15:14:32 zack-A880G kernel: [   16.862655] Bluetooth: SCO socket layer initialized
Dec 15 15:14:32 zack-A880G kernel: [   16.869978] nvidia: module license 'NVIDIA' taints kernel.
Dec 15 15:14:32 zack-A880G kernel: [   16.869982] Disabling lock debugging due to kernel taint
Dec 15 15:14:32 zack-A880G kernel: [   16.875276] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Dec 15 15:14:32 zack-A880G kernel: [   16.875279] Bluetooth: BNEP filters: protocol multicast
Dec 15 15:14:32 zack-A880G kernel: [   16.891715] ppdev: user-space parallel port driver
Dec 15 15:14:32 zack-A880G avahi-daemon[614]: Found user 'avahi' (UID 107) and group 'avahi' (GID 118).
Dec 15 15:14:32 zack-A880G avahi-daemon[614]: Successfully dropped root privileges.
Dec 15 15:14:32 zack-A880G avahi-daemon[614]: avahi-daemon 0.6.30 starting up.
Dec 15 15:14:32 zack-A880G avahi-daemon[614]: Successfully called chroot().
Dec 15 15:14:32 zack-A880G avahi-daemon[614]: Successfully dropped remaining capabilities.
Dec 15 15:14:32 zack-A880G avahi-daemon[614]: Loading service file /services/udisks.service.
Dec 15 15:14:32 zack-A880G kernel: [   16.967926] Bluetooth: RFCOMM TTY layer initialized
Dec 15 15:14:32 zack-A880G kernel: [   16.967932] Bluetooth: RFCOMM socket layer initialized
Dec 15 15:14:32 zack-A880G kernel: [   16.967933] Bluetooth: RFCOMM ver 1.11
Dec 15 15:14:32 zack-A880G avahi-daemon[614]: Network interface enumeration completed.
Dec 15 15:14:32 zack-A880G avahi-daemon[614]: Registering HINFO record with values 'I686'/'LINUX'.
Dec 15 15:14:32 zack-A880G avahi-daemon[614]: Server startup complete. Host name is zack-A880G.local. Local service cookie is 2304385720.
Dec 15 15:14:32 zack-A880G avahi-daemon[614]: Service "zack-A880G" (/services/udisks.service) successfully established.
Dec 15 15:14:32 zack-A880G udev-configure-printer: add /module/lp
Dec 15 15:14:32 zack-A880G udev-configure-printer: Failed to get parent
Dec 15 15:14:32 zack-A880G kernel: [   16.999263] lp0: using parport0 (interrupt-driven).
Dec 15 15:14:32 zack-A880G kernel: [   17.099204] type=1400 audit(1387149272.584:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=679 comm="apparmor_parser"
Dec 15 15:14:32 zack-A880G kernel: [   17.102161] type=1400 audit(1387149272.588:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=679 comm="apparmor_parser"
Dec 15 15:14:32 zack-A880G kernel: [   17.114567] microcode: CPU0: patch_level=0x010000c8
Dec 15 15:14:32 zack-A880G failsafe: Failsafe of 120 seconds reached.
Dec 15 15:14:32 zack-A880G kernel: [   17.228656] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  ModemManager (version 0.5.2.0) starting...
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin Nokia
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin Option
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin Sierra
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin Novatel
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin ZTE
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin Linktop
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin MotoC
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin Gobi
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin X22X
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin Longcheer
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin Generic
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin Huawei
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin Ericsson MBM
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin SimTech
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin AnyData
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> NetworkManager (version 0.9.4.0) is starting...
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin Option High-Speed
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin Samsung
Dec 15 15:14:32 zack-A880G modem-manager[765]: <info>  Loaded plugin Wavecom
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> DNS: loaded plugin dnsmasq
Dec 15 15:14:32 zack-A880G dbus[564]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Dec 15 15:14:32 zack-A880G kernel: [   17.304996] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.88  Wed Mar 27 14:31:12 PDT 2013
Dec 15 15:14:32 zack-A880G kernel: [   17.457093] type=1400 audit(1387149272.944:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=811 comm="apparmor_parser"
Dec 15 15:14:32 zack-A880G kernel: [   17.457433] type=1400 audit(1387149272.944:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=811 comm="apparmor_parser"
Dec 15 15:14:32 zack-A880G kernel: [   17.461715] type=1400 audit(1387149272.948:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=813 comm="apparmor_parser"
Dec 15 15:14:32 zack-A880G kernel: [   17.469672] type=1400 audit(1387149272.956:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=813 comm="apparmor_parser"
Dec 15 15:14:32 zack-A880G kernel: [   17.469909] type=1400 audit(1387149272.956:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=813 comm="apparmor_parser"
Dec 15 15:14:32 zack-A880G polkitd[781]: started daemon version 0.104 using authority implementation `local' version `0.104'
Dec 15 15:14:32 zack-A880G dbus[564]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Dec 15 15:14:32 zack-A880G NetworkManager[772]:    SCPlugin-Ifupdown: init!
Dec 15 15:14:32 zack-A880G NetworkManager[772]:    SCPlugin-Ifupdown: update_system_hostname
Dec 15 15:14:32 zack-A880G NetworkManager[772]:    SCPluginIfupdown: management mode: unmanaged
Dec 15 15:14:32 zack-A880G NetworkManager[772]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0/net/eth0, iface: eth0)
Dec 15 15:14:32 zack-A880G NetworkManager[772]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec 15 15:14:32 zack-A880G NetworkManager[772]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Dec 15 15:14:32 zack-A880G NetworkManager[772]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Dec 15 15:14:32 zack-A880G NetworkManager[772]:    SCPlugin-Ifupdown: end _init.
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dec 15 15:14:32 zack-A880G NetworkManager[772]:    Ifupdown: get unmanaged devices count: 0
Dec 15 15:14:32 zack-A880G NetworkManager[772]:    SCPlugin-Ifupdown: (143034136) ... get_connections.
Dec 15 15:14:32 zack-A880G NetworkManager[772]:    SCPlugin-Ifupdown: (143034136) ... get_connections (managed=false): return empty list.
Dec 15 15:14:32 zack-A880G NetworkManager[772]:    keyfile: parsing Zoom Zoom 1 ... 
Dec 15 15:14:32 zack-A880G NetworkManager[772]:    keyfile:     read connection 'Zoom Zoom 1'
Dec 15 15:14:32 zack-A880G NetworkManager[772]:    keyfile: parsing Zoom Zoom ... 
Dec 15 15:14:32 zack-A880G NetworkManager[772]:    keyfile:     read connection 'Zoom Zoom'
Dec 15 15:14:32 zack-A880G NetworkManager[772]:    Ifupdown: get unmanaged devices count: 0
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> modem-manager is now available
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> WiFi enabled by radio killswitch; enabled by state file
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> WWAN enabled by radio killswitch; enabled by state file
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> WiMAX enabled by radio killswitch; enabled by state file
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> Networking is enabled by state file
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <warn> failed to allocate link cache: (-10) Operation not supported
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> (eth0): carrier is OFF
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> (eth0): now managed
Dec 15 15:14:32 zack-A880G NetworkManager[772]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 15 15:14:33 zack-A880G NetworkManager[772]: <info> (eth0): bringing up device.
Dec 15 15:14:33 zack-A880G udev-configure-printer: add /module/lp
Dec 15 15:14:33 zack-A880G udev-configure-printer: Failed to get parent
Dec 15 15:14:33 zack-A880G kernel: [   17.679175] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
Dec 15 15:14:33 zack-A880G kernel: [   17.716402] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
Dec 15 15:14:33 zack-A880G kernel: [   17.716605] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
Dec 15 15:14:33 zack-A880G kernel: [   17.734195] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
Dec 15 15:14:33 zack-A880G kernel: [   17.755979] input: HDA ATI SB Line Out as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
Dec 15 15:14:33 zack-A880G cron[881]: (CRON) INFO (pidfile fd = 3)
Dec 15 15:14:33 zack-A880G kernel: [   17.784972] hda_intel: Disabling MSI
Dec 15 15:14:33 zack-A880G kernel: [   17.784983] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
Dec 15 15:14:33 zack-A880G anacron[904]: Anacron 2.3 started on 2013-12-15
Dec 15 15:14:33 zack-A880G cron[913]: (CRON) STARTUP (fork ok)
Dec 15 15:14:33 zack-A880G NetworkManager[772]: <info> (eth0): preparing device.
Dec 15 15:14:33 zack-A880G NetworkManager[772]: <info> (eth0): deactivating device (reason 'managed') [2]
Dec 15 15:14:33 zack-A880G NetworkManager[772]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0/net/eth0
Dec 15 15:14:33 zack-A880G udev-configure-printer: add /devices/pnp0/00:07/printer/lp0
Dec 15 15:14:33 zack-A880G udev-configure-printer: Failed to get parent
Dec 15 15:14:33 zack-A880G kernel: [   17.812121] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Dec 15 15:14:33 zack-A880G kernel: [   17.870025] r8169 0000:02:00.0: eth0: link down
Dec 15 15:14:33 zack-A880G kernel: [   17.874063] r8169 0000:02:00.0: eth0: link down
Dec 15 15:14:33 zack-A880G kernel: [   17.874276] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 15 15:14:33 zack-A880G kernel: [   17.874610] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 15 15:14:33 zack-A880G kernel: [   17.884771] kvm: Nested Virtualization enabled
Dec 15 15:14:33 zack-A880G kernel: [   17.884773] kvm: Nested Paging enabled
Dec 15 15:14:33 zack-A880G acpid: starting up with proc fs
Dec 15 15:14:33 zack-A880G acpid: skipping conf file /etc/acpi/events/RadioPower.sh
Dec 15 15:14:33 zack-A880G acpid: 35 rules loaded
Dec 15 15:14:33 zack-A880G acpid: waiting for events: event logging is off
Dec 15 15:14:33 zack-A880G anacron[904]: Will run job `cron.daily' in 5 min.
Dec 15 15:14:33 zack-A880G anacron[904]: Will run job `cron.weekly' in 10 min.
Dec 15 15:14:33 zack-A880G anacron[904]: Will run job `cron.monthly' in 15 min.
Dec 15 15:14:33 zack-A880G anacron[904]: Jobs will be executed sequentially
Dec 15 15:14:33 zack-A880G cron[913]: (CRON) INFO (Running @reboot jobs)
Dec 15 15:14:34 zack-A880G kernel: [   18.752884] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input9
Dec 15 15:14:34 zack-A880G kernel: [   18.753034] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input10
Dec 15 15:14:34 zack-A880G kernel: [   18.753168] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input11
Dec 15 15:14:34 zack-A880G kernel: [   18.753289] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input12
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> (eth0): carrier now ON (device state 20)
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> Auto-activating connection 'Wired connection 1'.
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> Activation (eth0) starting connection 'Wired connection 1'
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 15 15:14:35 zack-A880G kernel: [   19.784414] r8169 0000:02:00.0: eth0: link up
Dec 15 15:14:35 zack-A880G kernel: [   19.784586] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> dhclient started with pid 1181
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> Activation (eth0) Beginning IP6 addrconf.
Dec 15 15:14:35 zack-A880G NetworkManager[772]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec 15 15:14:35 zack-A880G dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Dec 15 15:14:35 zack-A880G dhclient: Copyright 2004-2011 Internet Systems Consortium.
Dec 15 15:14:35 zack-A880G dhclient: All rights reserved.
Dec 15 15:14:35 zack-A880G dhclient: For info, please visit https://www.isc.org/software/dhcp/
Dec 15 15:14:35 zack-A880G dhclient: 
Dec 15 15:14:36 zack-A880G dhclient: Listening on LPF/eth0/00:30:67:8c:c9:b2
Dec 15 15:14:36 zack-A880G dhclient: Sending on   LPF/eth0/00:30:67:8c:c9:b2
Dec 15 15:14:36 zack-A880G dhclient: Sending on   Socket/fallback
Dec 15 15:14:36 zack-A880G dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec 15 15:14:36 zack-A880G NetworkManager[772]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec 15 15:14:36 zack-A880G dhclient: isc-dhclient-4.1-ESV-R4
Dec 15 15:14:36 zack-A880G dhclient: isc-dhclient-4.1-ESV-R4
Dec 15 15:14:36 zack-A880G acpid: client connected from 1213[0:0]
Dec 15 15:14:36 zack-A880G acpid: 1 client rule loaded
Dec 15 15:14:36 zack-A880G kernel: [   21.343855] NVRM: API mismatch: the client has the version 319.32, but
Dec 15 15:14:36 zack-A880G kernel: [   21.343855] NVRM: this kernel module has the version 304.88.  Please
Dec 15 15:14:36 zack-A880G kernel: [   21.343855] NVRM: make sure that this kernel module and all NVIDIA driver
Dec 15 15:14:36 zack-A880G kernel: [   21.343855] NVRM: components have the same version.
Dec 15 15:14:36 zack-A880G acpid: client 1213[0:0] has disconnected
Dec 15 15:14:36 zack-A880G acpid: client connected from 1253[0:0]
Dec 15 15:14:36 zack-A880G acpid: 1 client rule loaded
Dec 15 15:14:36 zack-A880G kernel: [   21.440197] NVRM: API mismatch: the client has the version 319.32, but
Dec 15 15:14:36 zack-A880G kernel: [   21.440197] NVRM: this kernel module has the version 304.88.  Please
Dec 15 15:14:36 zack-A880G kernel: [   21.440197] NVRM: make sure that this kernel module and all NVIDIA driver
Dec 15 15:14:36 zack-A880G kernel: [   21.440197] NVRM: components have the same version.
Dec 15 15:14:37 zack-A880G avahi-daemon[614]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::230:67ff:fe8c:c9b2.
Dec 15 15:14:37 zack-A880G avahi-daemon[614]: New relevant interface eth0.IPv6 for mDNS.
Dec 15 15:14:37 zack-A880G avahi-daemon[614]: Registering new address record for fe80::230:67ff:fe8c:c9b2 on eth0.*.
Dec 15 15:14:37 zack-A880G dhclient: DHCPREQUEST of 192.168.1.47 on eth0 to 255.255.255.255 port 67
Dec 15 15:14:37 zack-A880G dhclient: DHCPOFFER of 192.168.1.47 from 192.168.1.1
Dec 15 15:14:37 zack-A880G dhclient: DHCPACK of 192.168.1.47 from 192.168.1.1
Dec 15 15:14:37 zack-A880G dhclient: bound to 192.168.1.47 -- renewal in 41980 seconds.
Dec 15 15:14:37 zack-A880G NetworkManager[772]: <info> (eth0): DHCPv4 state changed preinit -> bound
Dec 15 15:14:37 zack-A880G NetworkManager[772]: <info>   address 192.168.1.47
Dec 15 15:14:37 zack-A880G NetworkManager[772]: <info>   prefix 24 (255.255.255.0)
Dec 15 15:14:37 zack-A880G NetworkManager[772]: <info>   gateway 192.168.1.1
Dec 15 15:14:37 zack-A880G NetworkManager[772]: <info>   nameserver '192.168.1.1'
Dec 15 15:14:37 zack-A880G NetworkManager[772]: <info>   nameserver '192.168.1.1'
Dec 15 15:14:37 zack-A880G NetworkManager[772]: <info>   domain name 'myhome.westell.com'
Dec 15 15:14:37 zack-A880G NetworkManager[772]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Dec 15 15:14:37 zack-A880G NetworkManager[772]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Dec 15 15:14:37 zack-A880G avahi-daemon[614]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.47.
Dec 15 15:14:37 zack-A880G avahi-daemon[614]: New relevant interface eth0.IPv4 for mDNS.
Dec 15 15:14:37 zack-A880G avahi-daemon[614]: Registering new address record for 192.168.1.47 on eth0.IPv4.
Dec 15 15:14:38 zack-A880G NetworkManager[772]: <info> DNS: starting dnsmasq...
Dec 15 15:14:38 zack-A880G NetworkManager[772]: <error> [1387149278.406380] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
Dec 15 15:14:38 zack-A880G NetworkManager[772]: <error> [1387149278.406463] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
Dec 15 15:14:38 zack-A880G NetworkManager[772]: <warn> DNS: plugin dnsmasq update failed
Dec 15 15:14:38 zack-A880G NetworkManager[772]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Dec 15 15:14:38 zack-A880G dnsmasq[1255]: started, version 2.59 cache disabled
Dec 15 15:14:38 zack-A880G dnsmasq[1255]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Dec 15 15:14:38 zack-A880G dnsmasq[1255]: DBus support enabled: connected to system bus
Dec 15 15:14:38 zack-A880G dnsmasq[1255]: warning: no upstream servers configured
Dec 15 15:14:38 zack-A880G NetworkManager[772]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Dec 15 15:14:38 zack-A880G NetworkManager[772]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Dec 15 15:14:38 zack-A880G NetworkManager[772]: <info> Activation (eth0) successful, device activated.
Dec 15 15:14:38 zack-A880G dbus[564]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec 15 15:14:38 zack-A880G NetworkManager[772]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Dec 15 15:14:38 zack-A880G NetworkManager[772]: <warn> dnsmasq appeared on DBus: :1.14
Dec 15 15:14:38 zack-A880G dbus[564]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 15 15:14:38 zack-A880G NetworkManager[772]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Dec 15 15:14:38 zack-A880G dnsmasq[1255]: setting upstream servers from DBus
Dec 15 15:14:38 zack-A880G dnsmasq[1255]: using nameserver 192.168.1.1#53
Dec 15 23:14:49 zack-A880G ntpdate[1372]: step time server 91.189.94.4 offset 28801.860765 sec
Dec 15 23:14:57 zack-A880G NetworkManager[772]: <info> (eth0): IP6 addrconf timed out or failed.
Dec 15 23:14:57 zack-A880G NetworkManager[772]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Dec 15 23:14:57 zack-A880G NetworkManager[772]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Dec 15 23:14:57 zack-A880G NetworkManager[772]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Dec 15 23:15:16 zack-A880G acpid: client 1253[0:0] has disconnected
Dec 15 23:15:16 zack-A880G dbus[564]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Dec 15 23:15:16 zack-A880G dbus[564]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Dec 15 23:15:16 zack-A880G kernel: Kernel logging (proc) stopped.
Dec 15 23:15:16 zack-A880G rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="602" x-info="http://www.rsyslog.com"] exiting on signal 15.

```

---

### Post by nwordz on 2013-12-16
And this is the dmesg:
Thanks again for the help!

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-43-generic (buildd@akateko) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #66~precise1-Ubuntu SMP Thu Oct 24 14:55:08 UTC 2013 (Ubuntu 3.5.0-43.66~precise1-generic 3.5.7.23)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ffaffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007ffb0000-0x000000007ffbdfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007ffbe000-0x000000007ffdffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007ffe0000-0x000000007fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: BIOSTAR Group A880G+/A880G+, BIOS 080016  08/30/2010
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x7ffb0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [c00ff780]
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x379fffff] page 2M
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x36244000-0x37119fff]
[    0.000000] ACPI: RSDP 000faf80 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7ffb0000 00044 (v01 083010 RSDT1638 20100830 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffb0200 00084 (v01 083010 FACP1638 20100830 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20120320/tbfadt-579)
[    0.000000] ACPI: DSDT 7ffb0450 0A1DA (v01  88PCP 88PCP830 00000002 INTL 20051117)
[    0.000000] ACPI: FACS 7ffbe000 00040
[    0.000000] ACPI: APIC 7ffb0390 0007C (v01 083010 APIC1638 20100830 MSFT 00000097)
[    0.000000] ACPI: MCFG 7ffb0410 0003C (v01 083010 OEMMCFG  20100830 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffbe040 00072 (v01 083010 OEMB1638 20100830 MSFT 00000097)
[    0.000000] ACPI: SRAT 7ffba630 00090 (v03 AMD    FAM_F_10 00000002 AMD  00000001)
[    0.000000] ACPI: MSCT 7ffba6c0 0004E (v01 A M I  OEMBOARD 00000001 AMD  00000001)
[    0.000000] ACPI: HPET 7ffba710 00038 (v01 083010 OEMHPET  20100830 MSFT 00000097)
[    0.000000] ACPI: SSDT 7ffba750 0023E (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1155MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x7ffaffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x7ffaffff]
[    0.000000] On node 0 totalpages: 524095
[    0.000000] free_area_init_node: node 0, pgdat c18c85c0, node_mem_map f5244200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2312 pages used for memmap
[    0.000000]   HighMem zone: 293546 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 6 CPUs, 5 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] e820: [mem 0x80000000-0xffefffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7b9d000 s34176 r0 d23168 u57344
[    0.000000] pcpu-alloc: s34176 r0 d23168 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 [0] 4 [0] 5 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519999
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-43-generic root=UUID=a5baa10f-bb69-49cc-998b-f6e8c4f55e7d ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4193536 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007ffb0)
[    0.000000] Memory: 2048744k/2096832k available (6059k kernel code, 47636k reserved, 2985k data, 764k init, 1183432k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc18d6000 - 0xc1995000   ( 764 kB)
[    0.000000]       .data : 0xc15eaf15 - 0xc18d54c0   (2985 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15eaf15   (6059 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:728 16
[    0.000000] CPU 0 irqstacks, hard=f4c0a000 soft=f4c0c000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration failed
[    0.008000] TSC: PIT calibration matches HPET. 1 loops
[    0.008000] Detected 2800.151 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5600.30 BogoMIPS (lpj=11200604)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000024] Security Framework initialized
[    0.000038] AppArmor: AppArmor initialized
[    0.000040] Yama: becoming mindful.
[    0.000085] Mount-cache hash table entries: 512
[    0.000253] Initializing cgroup subsys cpuacct
[    0.000256] Initializing cgroup subsys memory
[    0.000262] Initializing cgroup subsys devices
[    0.000263] Initializing cgroup subsys freezer
[    0.000265] Initializing cgroup subsys blkio
[    0.000267] Initializing cgroup subsys perf_event
[    0.000287] mce: CPU supports 6 MCE banks
[    0.000292] LVT offset 0 assigned for vector 0xf9
[    0.000470] SMP alternatives: switching to UP code
[    0.007540] ACPI: Core revision 20120320
[    0.018517] ftrace: allocating 27161 entries in 54 pages
[    0.028177] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028537] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.068664] CPU0: AMD Sempron(tm) 145 Processor stepping 03
[    0.173608] Performance Events: AMD PMU driver.
[    0.173612] ... version:                0
[    0.173613] ... bit width:              48
[    0.173614] ... generic registers:      4
[    0.173615] ... value mask:             0000ffffffffffff
[    0.173616] ... max period:             00007fffffffffff
[    0.173617] ... fixed-purpose events:   0
[    0.173618] ... event mask:             000000000000000f
[    0.173751] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.173797] Brought up 1 CPUs
[    0.173799] Total of 1 processors activated (5600.30 BogoMIPS).
[    0.174245] devtmpfs: initialized
[    0.174363] EVM: security.selinux
[    0.174364] EVM: security.SMACK64
[    0.174365] EVM: security.capability
[    0.174406] PM: Registering ACPI NVS region [mem 0x7ffbe000-0x7ffdffff] (139264 bytes)
[    0.175163] dummy: 
[    0.175188] RTC time: 23:14:15, date: 12/15/13
[    0.175217] NET: Registered protocol family 16
[    0.175299] EISA bus registered
[    0.175303] node 0 link 0: io port [1000, ffffff]
[    0.175306] TOM: 0000000080000000 aka 2048M
[    0.175308] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
[    0.175310] node 0 link 0: mmio [a0000, bffff]
[    0.175312] node 0 link 0: mmio [80000000, dfffffff]
[    0.175314] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.175316] node 0 link 0: mmio [f0000000, ffefffff]
[    0.175318] bus: [00, 07] on node 0 link 0
[    0.175319] bus: 00 [io  0x0000-0xffff]
[    0.175320] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.175322] bus: 00 [mem 0x80000000-0xdfffffff]
[    0.175323] bus: 00 [mem 0xf0000000-0xfcffffffff]
[    0.175374] ACPI: bus type pci registered
[    0.175417] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.175419] PCI: not using MMCONFIG
[    0.175986] PCI : PCI BIOS area is rw and x. Use pci=nobios if you want it NX.
[    0.176055] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.176056] PCI: Using configuration type 1 for base access
[    0.176057] PCI: Using configuration type 1 for extended access
[    0.176678] bio: create slab <bio-0> at 0
[    0.176740] ACPI: Added _OSI(Module Device)
[    0.176741] ACPI: Added _OSI(Processor Device)
[    0.176742] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.176744] ACPI: Added _OSI(Processor Aggregator Device)
[    0.177308] ACPI: EC: Look up EC in DSDT
[    0.178519] ACPI: Executed 4 blocks of module-level executable AML code
[    0.181800] ACPI: Interpreter enabled
[    0.181805] ACPI: (supports S0 S1 S4 S5)
[    0.181821] ACPI: Using IOAPIC for interrupt routing
[    0.181840] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.183044] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.183045] PCI: Using MMCONFIG for extended config space
[    0.187595] ACPI: No dock devices found.
[    0.187599] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.187661] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.187766] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.187769] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.187771] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.187773] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.187775] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xdfffffff]
[    0.187776] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.187800] PCI host bridge to bus 0000:00
[    0.187802] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.187804] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.187806] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.187807] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.187809] pci_bus 0000:00: root bus resource [mem 0x80000000-0xdfffffff]
[    0.187811] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
[    0.187821] pci 0000:00:00.0: [1022:9601] type 00 class 0x060000
[    0.187869] pci 0000:00:02.0: [1022:9603] type 01 class 0x060400
[    0.187899] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.187926] pci 0000:00:07.0: [1022:9607] type 01 class 0x060400
[    0.187955] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.187995] pci 0000:00:11.0: [1002:4390] type 00 class 0x01018f
[    0.188013] pci 0000:00:11.0: reg 10: [io  0xb000-0xb007]
[    0.188023] pci 0000:00:11.0: reg 14: [io  0xa000-0xa003]
[    0.188032] pci 0000:00:11.0: reg 18: [io  0x9000-0x9007]
[    0.188041] pci 0000:00:11.0: reg 1c: [io  0x8000-0x8003]
[    0.188050] pci 0000:00:11.0: reg 20: [io  0x7000-0x700f]
[    0.188059] pci 0000:00:11.0: reg 24: [mem 0xfeaffc00-0xfeafffff]
[    0.188079] pci 0000:00:11.0: set SATA to AHCI mode
[    0.188123] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.188136] pci 0000:00:12.0: reg 10: [mem 0xfeafe000-0xfeafefff]
[    0.188197] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
[    0.188210] pci 0000:00:12.1: reg 10: [mem 0xfeafd000-0xfeafdfff]
[    0.188276] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.188294] pci 0000:00:12.2: reg 10: [mem 0xfeaff800-0xfeaff8ff]
[    0.188374] pci 0000:00:12.2: supports D1 D2
[    0.188375] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.188397] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.188410] pci 0000:00:13.0: reg 10: [mem 0xfeafc000-0xfeafcfff]
[    0.188471] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
[    0.188484] pci 0000:00:13.1: reg 10: [mem 0xfeafb000-0xfeafbfff]
[    0.188551] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.188569] pci 0000:00:13.2: reg 10: [mem 0xfeaff400-0xfeaff4ff]
[    0.188648] pci 0000:00:13.2: supports D1 D2
[    0.188650] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.188674] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.188768] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
[    0.188784] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.188793] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.188802] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.188811] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.188820] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.188878] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.188898] pci 0000:00:14.2: reg 10: [mem 0xfeaf4000-0xfeaf7fff 64bit]
[    0.188962] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.188977] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.189050] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.189089] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.189102] pci 0000:00:14.5: reg 10: [mem 0xfeafa000-0xfeafafff]
[    0.189166] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
[    0.189179] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
[    0.189190] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
[    0.189201] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
[    0.189215] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
[    0.189263] pci 0000:01:00.0: [10de:0de1] type 00 class 0x030000
[    0.189272] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.189282] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
[    0.189292] pci 0000:01:00.0: reg 1c: [mem 0xd6000000-0xd7ffffff 64bit pref]
[    0.189298] pci 0000:01:00.0: reg 24: [io  0xc800-0xc87f]
[    0.189305] pci 0000:01:00.0: reg 30: [mem 0xfcf80000-0xfcffffff pref]
[    0.189357] pci 0000:01:00.1: [10de:0bea] type 00 class 0x040300
[    0.189366] pci 0000:01:00.1: reg 10: [mem 0xfcf7c000-0xfcf7ffff]
[    0.193606] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.193613] pci 0000:00:02.0:   bridge window [io  0xc000-0xcfff]
[    0.193617] pci 0000:00:02.0:   bridge window [mem 0xfcf00000-0xfdffffff]
[    0.193620] pci 0000:00:02.0:   bridge window [mem 0xd6000000-0xdfffffff 64bit pref]
[    0.193657] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
[    0.193671] pci 0000:02:00.0: reg 10: [io  0xd800-0xd8ff]
[    0.193690] pci 0000:02:00.0: reg 18: [mem 0xfbffb000-0xfbffbfff 64bit pref]
[    0.193703] pci 0000:02:00.0: reg 20: [mem 0xfbffc000-0xfbffffff 64bit pref]
[    0.193711] pci 0000:02:00.0: reg 30: [mem 0xfebe0000-0xfebfffff pref]
[    0.193758] pci 0000:02:00.0: supports D1 D2
[    0.193760] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.201590] pci 0000:00:07.0: PCI bridge to [bus 02-02]
[    0.201597] pci 0000:00:07.0:   bridge window [io  0xd000-0xdfff]
[    0.201599] pci 0000:00:07.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.201603] pci 0000:00:07.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.201648] pci 0000:03:06.0: [1274:1371] type 00 class 0x040100
[    0.201670] pci 0000:03:06.0: reg 10: [io  0xe800-0xe83f]
[    0.201767] pci 0000:03:06.0: supports D2
[    0.201769] pci 0000:03:06.0: PME# supported from D0 D2 D3hot
[    0.201816] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.201820] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
[    0.201826] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.201828] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.201830] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.201832] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.201834] pci 0000:00:14.4:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
[    0.201836] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.201846] pci_bus 0000:00: on NUMA node 0
[    0.201851] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.202028] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.202055] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.202091] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.202150]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.202152]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.202153] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.205138] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 12 14 15)
[    0.205169] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
[    0.205197] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.205224] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
[    0.205250] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.205277] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 *10 11 12 14 15)
[    0.205304] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 *9 12 14 15)
[    0.205330] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.205407] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.205409] vgaarb: loaded
[    0.205410] vgaarb: bridge control possible 0000:01:00.0
[    0.205545] SCSI subsystem initialized
[    0.205579] libata version 3.00 loaded.
[    0.205593] ACPI: bus type usb registered
[    0.205608] usbcore: registered new interface driver usbfs
[    0.205615] usbcore: registered new interface driver hub
[    0.205629] usbcore: registered new device driver usb
[    0.205681] PCI: Using ACPI for IRQ routing
[    0.205684] PCI: pci_cache_line_size set to 64 bytes
[    0.205747] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.205749] e820: reserve RAM buffer [mem 0x7ffb0000-0x7fffffff]
[    0.205817] NetLabel: Initializing
[    0.205818] NetLabel:  domain hash size = 128
[    0.205818] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.205826] NetLabel:  unlabeled traffic allowed by default
[    0.205886] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.205889] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.207908] Switching to clocksource hpet
[    0.212520] AppArmor: AppArmor Filesystem Enabled
[    0.212545] pnp: PnP ACPI init
[    0.212558] ACPI: bus type pnp registered
[    0.212656] pnp 00:00: [bus 00-ff]
[    0.212659] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.212661] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.212663] pnp 00:00: [io  0x0d00-0xffff window]
[    0.212665] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.212666] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.212668] pnp 00:00: [mem 0x80000000-0xdfffffff window]
[    0.212670] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.212708] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.212781] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.212783] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.212820] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.212853] pnp 00:02: [dma 4]
[    0.212855] pnp 00:02: [io  0x0000-0x000f]
[    0.212856] pnp 00:02: [io  0x0081-0x0083]
[    0.212858] pnp 00:02: [io  0x0087]
[    0.212860] pnp 00:02: [io  0x0089-0x008b]
[    0.212861] pnp 00:02: [io  0x008f]
[    0.212863] pnp 00:02: [io  0x00c0-0x00df]
[    0.212880] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.212887] pnp 00:03: [io  0x0070-0x0071]
[    0.212900] pnp 00:03: [irq 8]
[    0.212917] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.212922] pnp 00:04: [io  0x0061]
[    0.212941] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.212947] pnp 00:05: [io  0x00f0-0x00ff]
[    0.212954] pnp 00:05: [irq 13]
[    0.212971] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.213764] pnp 00:06: [io  0x03f8-0x03ff]
[    0.213767] pnp 00:06: [irq 4]
[    0.213769] pnp 00:06: [dma 0 disabled]
[    0.213837] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.214541] pnp 00:07: [io  0x0378-0x037f]
[    0.214544] pnp 00:07: [irq 7]
[    0.214546] pnp 00:07: [dma 0 disabled]
[    0.214732] pnp 00:07: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.214914] pnp 00:08: [mem 0xfed00000-0xfed003ff]
[    0.214934] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.214989] pnp 00:09: [io  0x0060]
[    0.214990] pnp 00:09: [io  0x0064]
[    0.214992] pnp 00:09: [mem 0xfec00000-0xfec00fff]
[    0.214994] pnp 00:09: [mem 0xfee00000-0xfee00fff]
[    0.215024] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.215026] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.215029] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.215130] pnp 00:0a: [io  0x0010-0x001f]
[    0.215132] pnp 00:0a: [io  0x0022-0x003f]
[    0.215133] pnp 00:0a: [io  0x0062-0x0063]
[    0.215135] pnp 00:0a: [io  0x0065-0x006f]
[    0.215136] pnp 00:0a: [io  0x0072-0x007f]
[    0.215138] pnp 00:0a: [io  0x0080]
[    0.215139] pnp 00:0a: [io  0x0084-0x0086]
[    0.215141] pnp 00:0a: [io  0x0088]
[    0.215142] pnp 00:0a: [io  0x008c-0x008e]
[    0.215144] pnp 00:0a: [io  0x0090-0x009f]
[    0.215145] pnp 00:0a: [io  0x00a2-0x00bf]
[    0.215147] pnp 00:0a: [io  0x00b1]
[    0.215148] pnp 00:0a: [io  0x00e0-0x00ef]
[    0.215150] pnp 00:0a: [io  0x04d0-0x04d1]
[    0.215152] pnp 00:0a: [io  0x040b]
[    0.215153] pnp 00:0a: [io  0x04d6]
[    0.215155] pnp 00:0a: [io  0x0c00-0x0c01]
[    0.215156] pnp 00:0a: [io  0x0c14]
[    0.215158] pnp 00:0a: [io  0x0c50-0x0c51]
[    0.215159] pnp 00:0a: [io  0x0c52]
[    0.215161] pnp 00:0a: [io  0x0c6c]
[    0.215162] pnp 00:0a: [io  0x0c6f]
[    0.215164] pnp 00:0a: [io  0x0cd0-0x0cd1]
[    0.215165] pnp 00:0a: [io  0x0cd2-0x0cd3]
[    0.215167] pnp 00:0a: [io  0x0cd4-0x0cd5]
[    0.215168] pnp 00:0a: [io  0x0cd6-0x0cd7]
[    0.215170] pnp 00:0a: [io  0x0cd8-0x0cdf]
[    0.215172] pnp 00:0a: [io  0x0800-0x089f]
[    0.215173] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
[    0.215176] pnp 00:0a: [io  0x0b00-0x0b0f]
[    0.215178] pnp 00:0a: [io  0x0b20-0x0b3f]
[    0.215179] pnp 00:0a: [io  0x0900-0x090f]
[    0.215181] pnp 00:0a: [io  0x0910-0x091f]
[    0.215183] pnp 00:0a: [io  0xfe00-0xfefe]
[    0.215184] pnp 00:0a: [io  0x0060]
[    0.215185] pnp 00:0a: [io  0x0064]
[    0.215187] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
[    0.215189] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
[    0.215248] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.215250] system 00:0a: [io  0x040b] has been reserved
[    0.215252] system 00:0a: [io  0x04d6] has been reserved
[    0.215254] system 00:0a: [io  0x0c00-0x0c01] has been reserved
[    0.215256] system 00:0a: [io  0x0c14] has been reserved
[    0.215258] system 00:0a: [io  0x0c50-0x0c51] has been reserved
[    0.215260] system 00:0a: [io  0x0c52] has been reserved
[    0.215262] system 00:0a: [io  0x0c6c] has been reserved
[    0.215263] system 00:0a: [io  0x0c6f] has been reserved
[    0.215265] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
[    0.215267] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
[    0.215269] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
[    0.215271] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
[    0.215273] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
[    0.215275] system 00:0a: [io  0x0800-0x089f] has been reserved
[    0.215277] system 00:0a: [io  0x0b00-0x0b0f] has been reserved
[    0.215279] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
[    0.215281] system 00:0a: [io  0x0900-0x090f] has been reserved
[    0.215283] system 00:0a: [io  0x0910-0x091f] has been reserved
[    0.215286] system 00:0a: [io  0xfe00-0xfefe] has been reserved
[    0.215288] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.215290] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.215292] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.215414] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
[    0.215415] pnp 00:0b: [io  0x0e00-0x0e0f]
[    0.215417] pnp 00:0b: [io  0x0e80-0x0e8f]
[    0.215419] pnp 00:0b: [io  0x0f40-0x0f4f]
[    0.215420] pnp 00:0b: [io  0x0a30-0x0a3f]
[    0.215451] system 00:0b: [io  0x0e00-0x0e0f] has been reserved
[    0.215453] system 00:0b: [io  0x0e80-0x0e8f] has been reserved
[    0.215455] system 00:0b: [io  0x0f40-0x0f4f] has been reserved
[    0.215457] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
[    0.215459] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.215481] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    0.215510] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.215512] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.215703] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.215705] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    0.215706] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    0.215708] pnp 00:0d: [mem 0x00100000-0x7fffffff]
[    0.215710] pnp 00:0d: [mem 0xfec00000-0xffffffff]
[    0.215744] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.215746] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.215748] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.215750] system 00:0d: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.215753] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.215755] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.215835] pnp: PnP ACPI: found 14 devices
[    0.215836] ACPI: ACPI bus type pnp unregistered
[    0.215838] PnPBIOS: Disabled by ACPI PNP
[    0.251323] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.251326] pci 0000:00:02.0:   bridge window [io  0xc000-0xcfff]
[    0.251329] pci 0000:00:02.0:   bridge window [mem 0xfcf00000-0xfdffffff]
[    0.251332] pci 0000:00:02.0:   bridge window [mem 0xd6000000-0xdfffffff 64bit pref]
[    0.251335] pci 0000:00:07.0: PCI bridge to [bus 02-02]
[    0.251337] pci 0000:00:07.0:   bridge window [io  0xd000-0xdfff]
[    0.251340] pci 0000:00:07.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.251342] pci 0000:00:07.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.251346] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.251348] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
[    0.251378] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.251380] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.251382] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.251383] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.251385] pci_bus 0000:00: resource 8 [mem 0x80000000-0xdfffffff]
[    0.251387] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.251389] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.251391] pci_bus 0000:01: resource 1 [mem 0xfcf00000-0xfdffffff]
[    0.251393] pci_bus 0000:01: resource 2 [mem 0xd6000000-0xdfffffff 64bit pref]
[    0.251395] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.251397] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.251399] pci_bus 0000:02: resource 2 [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.251401] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.251403] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.251404] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.251406] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.251408] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.251410] pci_bus 0000:03: resource 8 [mem 0x80000000-0xdfffffff]
[    0.251412] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.251438] NET: Registered protocol family 2
[    0.251482] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.251589] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.252034] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.252262] TCP: Hash tables configured (established 131072 bind 65536)
[    0.252263] TCP: reno registered
[    0.252266] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.252273] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.252340] NET: Registered protocol family 1
[    1.277942] pci 0000:01:00.0: Boot video device
[    1.277958] PCI: CLS 64 bytes, default 64
[    1.278123] LVT offset 1 assigned for vector 0x400
[    1.278129] IBS: LVT offset 1 assigned
[    1.278145] perf: AMD IBS detected (0x0000001f)
[    1.278254] audit: initializing netlink socket (disabled)
[    1.278262] type=2000 audit(1387149256.172:1): initialized
[    1.295938] Trying to unpack rootfs image as initramfs...
[    1.318337] highmem bounce pool size: 64 pages
[    1.318350] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.329837] VFS: Disk quotas dquot_6.5.2
[    1.329883] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.330295] fuse init (API version 7.19)
[    1.330348] msgmni has been set to 1690
[    1.342087] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.342124] io scheduler noop registered
[    1.342125] io scheduler deadline registered (default)
[    1.342131] io scheduler cfq registered
[    1.342237] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.342288] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
[    1.342331] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.342343] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.342435] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.342439] ACPI: Power Button [PWRB]
[    1.342470] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.342472] ACPI: Power Button [PWRF]
[    1.346171] thermal LNXTHERM:00: registered as thermal_zone0
[    1.346173] ACPI: Thermal Zone [THRM] (32 C)
[    1.346191] GHES: HEST is not enabled!
[    1.346252] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.366657] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.369744] isapnp: Scanning for PnP cards...
[    1.458826] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.481978] Linux agpgart interface v0.103
[    1.483043] brd: module loaded
[    1.483509] loop: module loaded
[    1.483643] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.483830] Fixed MDIO Bus: probed
[    1.483861] tun: Universal TUN/TAP device driver, 1.6
[    1.483862] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.483886] PPP generic driver version 2.4.2
[    1.483910] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.483935] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.483940] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.483947] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.483966] ehci_hcd 0000:00:12.2: debug port 1
[    1.483986] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfeaff800
[    1.527981] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.528014] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.528016] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.528017] usb usb1: Product: EHCI Host Controller
[    1.528019] usb usb1: Manufacturer: Linux 3.5.0-43-generic ehci_hcd
[    1.528021] usb usb1: SerialNumber: 0000:00:12.2
[    1.605555] hub 1-0:1.0: USB hub found
[    1.605561] hub 1-0:1.0: 6 ports detected
[    1.605648] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.605653] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.605660] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.605680] ehci_hcd 0000:00:13.2: debug port 1
[    1.605703] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfeaff400
[    1.617319] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.617341] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.617344] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.617346] usb usb2: Product: EHCI Host Controller
[    1.617347] usb usb2: Manufacturer: Linux 3.5.0-43-generic ehci_hcd
[    1.617349] usb usb2: SerialNumber: 0000:00:13.2
[    1.617437] hub 2-0:1.0: USB hub found
[    1.617441] hub 2-0:1.0: 6 ports detected
[    1.617510] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.617562] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.617567] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.617591] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfeafe000
[    1.681167] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.681171] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.681173] usb usb3: Product: OHCI Host Controller
[    1.681175] usb usb3: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
[    1.681176] usb usb3: SerialNumber: 0000:00:12.0
[    1.681271] hub 3-0:1.0: USB hub found
[    1.681280] hub 3-0:1.0: 3 ports detected
[    1.681346] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.681350] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.681366] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfeafd000
[    1.844963] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.844967] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.844969] usb usb4: Product: OHCI Host Controller
[    1.844971] usb usb4: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
[    1.844973] usb usb4: SerialNumber: 0000:00:12.1
[    1.845064] hub 4-0:1.0: USB hub found
[    1.845074] hub 4-0:1.0: 3 ports detected
[    1.845141] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.845146] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.845173] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfeafc000
[    1.908921] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.908925] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.908927] usb usb5: Product: OHCI Host Controller
[    1.908929] usb usb5: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
[    1.908930] usb usb5: SerialNumber: 0000:00:13.0
[    1.909018] hub 5-0:1.0: USB hub found
[    1.909028] hub 5-0:1.0: 3 ports detected
[    1.909093] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.909098] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.909114] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfeafb000
[    1.919228] Freeing initrd memory: 15192k freed
[    1.968386] isapnp: No Plug & Play device found
[    1.972415] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.972417] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.972419] usb usb6: Product: OHCI Host Controller
[    1.972421] usb usb6: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
[    1.972423] usb usb6: SerialNumber: 0000:00:13.1
[    1.972522] hub 6-0:1.0: USB hub found
[    1.972531] hub 6-0:1.0: 3 ports detected
[    1.972607] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.972611] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.972631] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfeafa000
[    2.032518] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    2.032522] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.032524] usb usb7: Product: OHCI Host Controller
[    2.032526] usb usb7: Manufacturer: Linux 3.5.0-43-generic ohci_hcd
[    2.032527] usb usb7: SerialNumber: 0000:00:14.5
[    2.032616] hub 7-0:1.0: USB hub found
[    2.032626] hub 7-0:1.0: 2 ports detected
[    2.032672] uhci_hcd: USB Universal Host Controller Interface driver
[    2.032729] usbcore: registered new interface driver libusual
[    2.032760] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.033198] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.033202] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.033268] mousedev: PS/2 mouse device common for all mice
[    2.033342] rtc_cmos 00:03: RTC can wake from S4
[    2.033434] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.033457] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.033495] device-mapper: uevent: version 1.0.3
[    2.033535] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    2.033547] EISA: Probing bus 0 at eisa.0
[    2.033548] EISA: Cannot allocate resource for mainboard
[    2.033550] Cannot allocate resource for EISA slot 1
[    2.033551] Cannot allocate resource for EISA slot 2
[    2.033552] Cannot allocate resource for EISA slot 3
[    2.033553] Cannot allocate resource for EISA slot 4
[    2.033554] Cannot allocate resource for EISA slot 5
[    2.033555] Cannot allocate resource for EISA slot 6
[    2.033556] Cannot allocate resource for EISA slot 7
[    2.033557] Cannot allocate resource for EISA slot 8
[    2.033558] EISA: Detected 0 cards.
[    2.033567] cpuidle: using governor ladder
[    2.033568] cpuidle: using governor menu
[    2.033570] EFI Variables Facility v0.08 2004-May-17
[    2.033711] ashmem: initialized
[    2.033791] TCP: cubic registered
[    2.033856] NET: Registered protocol family 10
[    2.033985] NET: Registered protocol family 17
[    2.033991] Key type dns_resolver registered
[    2.034026] Using IPI No-Shortcut mode
[    2.034071] PM: Hibernation image not present or could not be loaded.
[    2.034079] registered taskstats version 1
[    2.035799] Key type trusted registered
[    2.037209] Key type encrypted registered
[    2.038824]   Magic number: 9:772:251
[    2.038909] rtc_cmos 00:03: setting system clock to 2013-12-15 23:14:17 UTC (1387149257)
[    2.038934] powernow-k8: Found 1 AMD Sempron(tm) 145 Processor (1 cpu cores) (version 2.20.00)
[    2.038960] powernow-k8:    0 : pstate 0 (2800 MHz)
[    2.038961] powernow-k8:    1 : pstate 1 (2000 MHz)
[    2.038962] powernow-k8:    2 : pstate 2 (1600 MHz)
[    2.038963] powernow-k8:    3 : pstate 3 (800 MHz)
[    2.039016] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.039017] EDD information not available.
[    2.039111] Freeing unused kernel memory: 764k freed
[    2.039340] Write protecting the kernel text: 6060k
[    2.039352] Write protecting the kernel read-only data: 2484k
[    2.039353] NX-protecting the kernel data: 4180k
[    2.050953] udevd[84]: starting version 175
[    2.107929] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.108005] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    2.108139] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xf8418000, 00:30:67:8c:c9:b2, XID 081000c0 IRQ 42
[    2.108141] r8169 0000:02:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.111251] ahci 0000:00:11.0: version 3.0
[    2.111371] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    2.111374] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    2.125557] scsi0 : ahci
[    2.128396] scsi1 : ahci
[    2.130127] scsi2 : ahci
[    2.131794] scsi3 : ahci
[    2.131885] ata1: SATA max UDMA/133 abar m1024@0xfeaffc00 port 0xfeaffd00 irq 22
[    2.131888] ata2: SATA max UDMA/133 abar m1024@0xfeaffc00 port 0xfeaffd80 irq 22
[    2.131891] ata3: SATA max UDMA/133 abar m1024@0xfeaffc00 port 0xfeaffe00 irq 22
[    2.131894] ata4: SATA max UDMA/133 abar m1024@0xfeaffc00 port 0xfeaffe80 irq 22
[    2.152321] scsi4 : pata_atiixp
[    2.155321] scsi5 : pata_atiixp
[    2.155827] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    2.155829] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    2.291984] Refined TSC clocksource calibration: 2800.158 MHz.
[    2.291990] Switching to clocksource tsc
[    2.303960] usb 3-3: new low-speed USB device number 2 using ohci_hcd
[    2.337932] ata6.00: ATA-7: Maxtor 6L200P0, BAH41G10, max UDMA/133
[    2.337936] ata6.00: 398297088 sectors, multi 16: LBA48 
[    2.338354] ata6.01: ATA-5: QUANTUM FIREBALLlct20 10, APL.0900, max UDMA/100
[    2.338358] ata6.01: 20044080 sectors, multi 8: LBA 
[    2.353859] ata6.00: configured for UDMA/100
[    2.368595] ata6.01: configured for UDMA/100
[    2.447697] ata2: SATA link down (SStatus 0 SControl 300)
[    2.451690] ata3: SATA link down (SStatus 0 SControl 300)
[    2.451726] ata4: SATA link down (SStatus 0 SControl 300)
[    2.472639] usb 3-3: New USB device found, idVendor=046d, idProduct=c512
[    2.472643] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.472645] usb 3-3: Product: USB Receiver
[    2.472647] usb 3-3: Manufacturer: Logitech
[    2.590650] usbcore: registered new interface driver usbhid
[    2.590653] usbhid: USB HID core driver
[    2.619368] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.621845] ata1.00: ATAPI: ASUS    DRW-24B3LT, 1.00, max UDMA/100
[    2.622684] ata1.00: configured for UDMA/100
[    2.624641] scsi 0:0:0:0: CD-ROM            ASUS     DRW-24B3LT       1.00 PQ: 0 ANSI: 5
[    2.628023] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.628027] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.628125] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.628176] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.628283] scsi 5:0:0:0: Direct-Access     ATA      Maxtor 6L200P0   BAH4 PQ: 0 ANSI: 5
[    2.628369] sd 5:0:0:0: [sda] 398297088 512-byte logical blocks: (203 GB/189 GiB)
[    2.628402] sd 5:0:0:0: [sda] Write Protect is off
[    2.628405] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.628416] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.628584] sd 5:0:0:0: Attached scsi generic sg1 type 0
[    2.667821]  sda: sda1 sda2 < sda5 >
[    2.668034] sd 5:0:0:0: [sda] Attached SCSI disk
[    2.668087] scsi 5:0:1:0: Direct-Access     ATA      QUANTUM FIREBALL APL. PQ: 0 ANSI: 5
[    2.668178] sd 5:0:1:0: Attached scsi generic sg2 type 0
[    2.668215] sd 5:0:1:0: [sdb] 20044080 512-byte logical blocks: (10.2 GB/9.55 GiB)
[    2.668239] sd 5:0:1:0: [sdb] Write Protect is off
[    2.668241] sd 5:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.668252] sd 5:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.702020]  sdb: sdb1 sdb2 < sdb5 >
[    2.702233] sd 5:0:1:0: [sdb] Attached SCSI disk
[    2.713440] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input2
[    2.713539] logitech 0003:046D:C512.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:12.0-3/input0
[    2.714182] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1/input/input3
[    2.714332] logitech 0003:046D:C512.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:12.0-3/input1
[    5.387448] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    5.387452] EXT4-fs (sda1): write access will be enabled during recovery
[    6.383926] EXT4-fs (sda1): recovery complete
[    6.396480] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   16.438068] Adding 6141948k swap on /dev/sda5.  Priority:-1 extents:1 across:6141948k 
[   16.445565] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.471818] udevd[332]: starting version 175
[   16.517474] lp: driver loaded but no devices found
[   16.654027] wmi: Mapper loaded
[   16.720974] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.724074] type=1400 audit(1387149272.208:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=522 comm="apparmor_parser"
[   16.724456] type=1400 audit(1387149272.208:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=522 comm="apparmor_parser"
[   16.724671] type=1400 audit(1387149272.212:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=522 comm="apparmor_parser"
[   16.823074] parport_pc 00:07: reported by Plug and Play ACPI
[   16.823131] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   16.837032] ACPI Warning: 0x00000b00-0x00000b07 SystemIO conflicts with Region \SOR1 1 (20120320/utaddress-251)
[   16.837039] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.861088] sp5100_tco: SP5100 TCO WatchDog Timer Driver v0.01
[   16.862164] sp5100_tco: mmio address 0xfec000f0 already in use
[   16.862636] Bluetooth: Core ver 2.16
[   16.862648] NET: Registered protocol family 31
[   16.862649] Bluetooth: HCI device and connection manager initialized
[   16.862651] Bluetooth: HCI socket layer initialized
[   16.862652] Bluetooth: L2CAP socket layer initialized
[   16.862655] Bluetooth: SCO socket layer initialized
[   16.869978] nvidia: module license 'NVIDIA' taints kernel.
[   16.869982] Disabling lock debugging due to kernel taint
[   16.875276] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.875279] Bluetooth: BNEP filters: protocol multicast
[   16.891715] ppdev: user-space parallel port driver
[   16.967926] Bluetooth: RFCOMM TTY layer initialized
[   16.967932] Bluetooth: RFCOMM socket layer initialized
[   16.967933] Bluetooth: RFCOMM ver 1.11
[   16.999263] lp0: using parport0 (interrupt-driven).
[   17.099204] type=1400 audit(1387149272.584:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=679 comm="apparmor_parser"
[   17.102161] type=1400 audit(1387149272.588:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=679 comm="apparmor_parser"
[   17.114567] microcode: CPU0: patch_level=0x010000c8
[   17.228656] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   17.261529] init: failsafe main process (702) killed by TERM signal
[   17.304996] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.88  Wed Mar 27 14:31:12 PDT 2013
[   17.457093] type=1400 audit(1387149272.944:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=811 comm="apparmor_parser"
[   17.457433] type=1400 audit(1387149272.944:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=811 comm="apparmor_parser"
[   17.461715] type=1400 audit(1387149272.948:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=813 comm="apparmor_parser"
[   17.469672] type=1400 audit(1387149272.956:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=813 comm="apparmor_parser"
[   17.469909] type=1400 audit(1387149272.956:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=813 comm="apparmor_parser"
[   17.679175] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
[   17.716402] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[   17.716605] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   17.734195] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   17.755979] input: HDA ATI SB Line Out as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   17.772282] init: alsa-restore main process (880) terminated with status 19
[   17.784972] hda_intel: Disabling MSI
[   17.784983] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
[   17.812121] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   17.870025] r8169 0000:02:00.0: eth0: link down
[   17.874063] r8169 0000:02:00.0: eth0: link down
[   17.874276] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.874610] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.884771] kvm: Nested Virtualization enabled
[   17.884773] kvm: Nested Paging enabled

```

---

### Post by ian-weisser on 2013-12-16
Looks like one answer is in the logs. You seem to have NVIDIA hardware.

> **nwordz said:**
> ```

[    21.269] (EE) Failed to load module "nv" (module does not exist, 0)
..
[    21.270] (EE) Failed to load module "nv" (module does not exist, 0)
..
[    21.274] (EE) open /dev/dri/card0: No such file or directory
[    21.274] (EE) open /dev/dri/card0: No such file or directory
..
[    21.274] (EE) open /dev/fb0: No such file or directory
..
[    21.280] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[    21.280] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[    21.280] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[    21.280] (EE) NVIDIA(0):  *** Aborting ***
[    21.280] (EE) NVIDIA(0): Failing initialization of X screen 0
..
[    21.280] (EE) Screen(s) found, but none have a usable configuration.
[    21.280] 
Fatal server error:
[    21.280] no screens found
[    21.280] (EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    21.280] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    21.280] (EE) 
[    21.281] Server terminated with error (1). Closing log file.

```

1) Search the forum here for NVIDIA. Lots of posts from people with similar problems...and the solutions.

2) If you cannot find one that matches your situation, then please change the title of your thread to something more descriptive of the problem. That wil attract one of the gurus on this subject. I'm not a graphics card expert, and have never had that kind of problem, so I'll bow out and defer to them.

3) Try booting into an older kernel at the GRUB boot screen. You know your graphics works with an older kernel.

---

### Post by nwordz on 2013-12-17
Ok thanks Ian, ill check out those leads.
Only thing is about #3, I cant boot in to an old version of kernel, or at least don't know how or if I can. If that HDD is selected, it goes straight to that screen, no options or ways to stop or select a different boot as far as i know. Maybe you can enlighten me, is there a way to boot to an old version of kernel by pressing a sequence of keys?
Thanks for the help, I really appreciate it.
Zack

---

### Post by ian-weisser on 2013-12-17
If you cannot see the GRUB screen at boot, try the solution at [http://askubuntu.com/questions/87409/i-cant-get-grub-menu-to-show-up-during-boot](http://askubuntu.com/questions/87409/i-cant-get-grub-menu-to-show-up-during-boot)

---

