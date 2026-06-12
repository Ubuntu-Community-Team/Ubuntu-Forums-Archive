---
title: "Beryl Crash"
date: 2007-01-19
forum: General Help
---

### Post by JamieC on 2007-01-19
Hey there, I need some help with Beryl. It will crash randomly (a complete hard lock-up, I am unable to move the mouse or restart X server) and I have no idea why. Below is the output when running beryl-manager and I'll attach my Xorg configuration file and log if it'll help.

jamie@Ubuntu:~$ *beryl-manager*:
> 
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: No GLXFBConfig for default depth, falling back on visinfo.
Reloading options
Initiating splash


Thanks in advance, Jamie.

---

### Post by JamieC on 2007-01-19
Hm, when I run it as root I get the following output in terminal:
> 
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: No GLXFBConfig for default depth, falling back on visinfo.
Reloading options
[b]beryl: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
beryl: Plugin 'dbus':initDisplay failed
beryl: Couldn't activate plugin 'dbus'
Couldn't initialise dbus. This should not happen![/b]
Initiating splash


---

### Post by CroEragon on 2007-01-19
Are you sure it's connected to Beryl? Cause my computer freezes in same way (cannot move mouse or restart x server) with or without Beryl. And after 3 moths trying to repair it im still unable to resolve problem. Does it unfreeze after 5-15 minutes after freezing? If so does it do all operations you did while being frozen (eg. if you type something and then get frozen, after it unfreeze is text typet while being frozen there)?

---

### Post by JamieC on 2007-01-19
It has to be, Ubuntu runs completely fine until Beryl is loaded. AIXGL is completely fine since Ubuntu does not freeze even after long periods of time.

It's a complete hard lock-up. It will never unfreeze and a reset is the only thing I can do to get Ubuntu running again (which can't be too good for mounted devices).

---

### Post by Peti29 on 2007-01-19
Have you considered this?: [http://ubuntuforums.org/showthread.php?t=341036](http://ubuntuforums.org/showthread.php?t=341036)

---

### Post by CroEragon on 2007-01-19
> **Peti29 said:**
> Have you considered this?: [http://ubuntuforums.org/showthread.php?t=341036](http://ubuntuforums.org/showthread.php?t=341036)
I think it is not connected. I assume you he can use Beryl properly before it freeze so it shouldnt be connected.
BTW i Had same problem wit new updates, i downgraded, and now beryl works, but it still freeze.

---

### Post by JamieC on 2007-01-19
Yes, I do know of the issue and have considered it. Thanks anyway. Beryl has always been troublesome with my setup.

I was hoping someone would be able to shed some light on the situation using the provided logs and configuration to determine the source of the error.

---

### Post by CroEragon on 2007-01-19
Im certainly not able to help you "translate" log. Just note that Beryl is still beta and with such complex software it is normal to have crashes and problems, if there is no crashes or problems it would be final version.

---

### Post by JamieC on 2007-01-21
Even with the new version I am experiencing hard crashes. Anybody have any suggestions?

I tried to pull everything remotely nVidia related from my logs, here's the result:-

jamie@Ubuntu:~$ *cd /var/log && for i in `ls`; do echo $i && (cat $i | grep NVIDIA && cat $i | grep nVidia && cat $i | grep nvidia); done*:
> 
acpid
acpid.1.gz
acpid.2.gz
apport.log
apport.log.1
apport.log.2.gz
apport.log.3.gz
apport.log.4.gz
apport.log.5.gz
apport.log.6.gz
aptitude
auth.log
auth.log.0
auth.log.1.gz
boot
btmp
clamav
cat: clamav: Is a directory
cups
cat: cups: Is a directory
daemon.log
daemon.log.0
daemon.log.1.gz
debug
debug.0
debug.1.gz
dist-upgrade
cat: dist-upgrade: Is a directory
dmesg
[17179595.480000] nvidia: module license 'NVIDIA' taints kernel.
[17179595.976000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
dmesg.0
[17179596.264000] nvidia: module license 'NVIDIA' taints kernel.
[17179596.268000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
dmesg.1.gz
dmesg.2.gz
dmesg.3.gz
dmesg.4.gz
dpkg.log
faillog
fontconfig.log
fsck
cat: fsck: Is a directory
gdm
cat: gdm: Is a directory
installer
cat: installer: Is a directory
kern.log
Jan 20 12:32:58 Ubuntu kernel: [17179599.812000] nvidia: module license 'NVIDIA' taints kernel.
Jan 20 12:32:58 Ubuntu kernel: [17179600.220000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 20 19:05:57 Ubuntu kernel: [17179598.080000] nvidia: module license 'NVIDIA' taints kernel.
Jan 20 19:05:57 Ubuntu kernel: [17179598.112000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 21 06:15:36 Ubuntu kernel: [17179593.712000] nvidia: module license 'NVIDIA' taints kernel.
Jan 21 06:15:36 Ubuntu kernel: [17179593.716000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 21 06:19:10 Ubuntu kernel: [17179595.828000] nvidia: module license 'NVIDIA' taints kernel.
Jan 21 06:19:10 Ubuntu kernel: [17179596.284000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 21 11:05:08 Ubuntu kernel: [17179596.984000] nvidia: module license 'NVIDIA' taints kernel.
Jan 21 11:05:08 Ubuntu kernel: [17179596.988000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 21 11:14:40 Ubuntu kernel: [17179596.264000] nvidia: module license 'NVIDIA' taints kernel.
Jan 21 11:14:40 Ubuntu kernel: [17179596.268000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 21 11:19:30 Ubuntu kernel: [17179595.480000] nvidia: module license 'NVIDIA' taints kernel.
Jan 21 11:19:30 Ubuntu kernel: [17179595.976000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
kern.log.0
Jan 19 11:12:43 Ubuntu kernel: [17179599.164000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 11:12:43 Ubuntu kernel: [17179599.672000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 19 11:20:24 Ubuntu kernel: [17179597.424000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 11:20:24 Ubuntu kernel: [17179597.880000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 19 11:26:18 Ubuntu kernel: [17179595.320000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 11:26:18 Ubuntu kernel: [17179595.772000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 19 11:27:57 Ubuntu kernel: [17179594.492000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 11:27:57 Ubuntu kernel: [17179594.804000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 19 15:03:23 Ubuntu kernel: [17179593.976000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 15:03:23 Ubuntu kernel: [17179593.980000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 19 15:15:32 Ubuntu kernel: [17179595.896000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 15:15:32 Ubuntu kernel: [17179595.900000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 19 17:35:21 Ubuntu kernel: [17179598.772000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 17:35:21 Ubuntu kernel: [17179598.776000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 19 18:37:51 Ubuntu kernel: [17179598.456000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 18:37:51 Ubuntu kernel: [17179598.984000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 19 18:41:24 Ubuntu kernel: [17179594.456000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 18:41:24 Ubuntu kernel: [17179594.460000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 20 11:55:55 Ubuntu kernel: [17179595.084000] nvidia: module license 'NVIDIA' taints kernel.
Jan 20 11:55:55 Ubuntu kernel: [17179595.088000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
kern.log.1.gz
kern.log.2.gz
kern.log.3.gz
lastlog
lpr.log
mail.err
mail.info
mail.info.0
mail.log
mail.log.0
mail.warn
messages
Jan 20 12:32:58 Ubuntu kernel: [17179599.812000] nvidia: module license 'NVIDIA' taints kernel.
Jan 20 12:32:58 Ubuntu kernel: [17179600.220000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 20 19:05:57 Ubuntu kernel: [17179598.080000] nvidia: module license 'NVIDIA' taints kernel.
Jan 20 19:05:57 Ubuntu kernel: [17179598.112000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 21 06:15:36 Ubuntu kernel: [17179593.712000] nvidia: module license 'NVIDIA' taints kernel.
Jan 21 06:15:36 Ubuntu kernel: [17179593.716000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 21 06:19:10 Ubuntu kernel: [17179595.828000] nvidia: module license 'NVIDIA' taints kernel.
Jan 21 06:19:10 Ubuntu kernel: [17179596.284000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 21 11:05:08 Ubuntu kernel: [17179596.984000] nvidia: module license 'NVIDIA' taints kernel.
Jan 21 11:05:08 Ubuntu kernel: [17179596.988000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 21 11:14:40 Ubuntu kernel: [17179596.264000] nvidia: module license 'NVIDIA' taints kernel.
Jan 21 11:14:40 Ubuntu kernel: [17179596.268000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 21 11:19:30 Ubuntu kernel: [17179595.480000] nvidia: module license 'NVIDIA' taints kernel.
Jan 21 11:19:30 Ubuntu kernel: [17179595.976000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
messages.0
Jan 19 11:12:43 Ubuntu kernel: [17179599.164000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 11:12:43 Ubuntu kernel: [17179599.672000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 19 11:20:24 Ubuntu kernel: [17179597.424000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 11:20:24 Ubuntu kernel: [17179597.880000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 19 11:26:18 Ubuntu kernel: [17179595.320000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 11:26:18 Ubuntu kernel: [17179595.772000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 19 11:27:57 Ubuntu kernel: [17179594.492000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 11:27:57 Ubuntu kernel: [17179594.804000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 19 15:03:23 Ubuntu kernel: [17179593.976000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 15:03:23 Ubuntu kernel: [17179593.980000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 19 15:15:32 Ubuntu kernel: [17179595.896000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 15:15:32 Ubuntu kernel: [17179595.900000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 19 17:35:21 Ubuntu kernel: [17179598.772000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 17:35:21 Ubuntu kernel: [17179598.776000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 19 18:37:51 Ubuntu kernel: [17179598.456000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 18:37:51 Ubuntu kernel: [17179598.984000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 19 18:41:24 Ubuntu kernel: [17179594.456000] nvidia: module license 'NVIDIA' taints kernel.
Jan 19 18:41:24 Ubuntu kernel: [17179594.460000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 20 11:55:55 Ubuntu kernel: [17179595.084000] nvidia: module license 'NVIDIA' taints kernel.
Jan 20 11:55:55 Ubuntu kernel: [17179595.088000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
messages.1.gz
messages.2.gz
messages.3.gz
news
cat: news: Is a directory
pycentral.log
scrollkeeper.log
scrollkeeper.log.1
scrollkeeper.log.2
syslog
Jan 21 11:14:40 Ubuntu kernel: [17179596.264000] nvidia: module license 'NVIDIA' taints kernel.
Jan 21 11:14:40 Ubuntu kernel: [17179596.268000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 21 11:19:30 Ubuntu kernel: [17179595.480000] nvidia: module license 'NVIDIA' taints kernel.
Jan 21 11:19:30 Ubuntu kernel: [17179595.976000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
syslog.0
Jan 20 12:32:58 Ubuntu kernel: [17179599.812000] nvidia: module license 'NVIDIA' taints kernel.
Jan 20 12:32:58 Ubuntu kernel: [17179600.220000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 20 19:05:57 Ubuntu kernel: [17179598.080000] nvidia: module license 'NVIDIA' taints kernel.
Jan 20 19:05:57 Ubuntu kernel: [17179598.112000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 21 06:15:36 Ubuntu kernel: [17179593.712000] nvidia: module license 'NVIDIA' taints kernel.
Jan 21 06:15:36 Ubuntu kernel: [17179593.716000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 21 06:19:10 Ubuntu kernel: [17179595.828000] nvidia: module license 'NVIDIA' taints kernel.
Jan 21 06:19:10 Ubuntu kernel: [17179596.284000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 21 11:05:08 Ubuntu kernel: [17179596.984000] nvidia: module license 'NVIDIA' taints kernel.
Jan 21 11:05:08 Ubuntu kernel: [17179596.988000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
syslog.1.gz
syslog.2.gz
syslog.3.gz
syslog.4.gz
syslog.5.gz
syslog.6.gz
udev
unattended-upgrades
cat: unattended-upgrades: Is a directory
user.log
user.log.0
user.log.1.gz
uucp.log
wtmp
wvdialconf.log
Xorg.0.log
(**) |   |-->Device "NVIDIA Corporation NV40 [GeForce 6200?]"
(II) Module glx: vendor="NVIDIA Corporation"
(II) Module nvidia: vendor="NVIDIA Corporation"
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:58:46 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(--) Chipset NVIDIA GPU found
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 LE at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.02.45.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 LE at PCI:1:0:0:
(--) NVIDIA(0):     Proview (CRT-0)
(--) NVIDIA(0): Proview (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config option
(II) NVIDIA(0): Setting mode "1280x1024"
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(WW) NVIDIA(0): Option "XAANoOffscreenPixmaps" is not used
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(--) PCI:*(1:0:0) nVidia Corporation GeForce 6200 LE rev 161, Mem @ 0xfa000000/24, 0xd0000000/28, 0xfb000000/24
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
Xorg.0.log.old
(**) |   |-->Device "NVIDIA Corporation NV40 [GeForce 6200?]"
(II) Module glx: vendor="NVIDIA Corporation"
(II) Module nvidia: vendor="NVIDIA Corporation"
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:58:46 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(--) Chipset NVIDIA GPU found
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 LE at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.02.45.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 LE at PCI:1:0:0:
(--) NVIDIA(0):     Proview (CRT-0)
(--) NVIDIA(0): Proview (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config option
(II) NVIDIA(0): Setting mode "1280x1024"
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(WW) NVIDIA(0): Option "XAANoOffscreenPixmaps" is not used
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(--) PCI:*(1:0:0) nVidia Corporation GeForce 6200 LE rev 161, Mem @ 0xfa000000/24, 0xd0000000/28, 0xfb000000/24
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"


---

