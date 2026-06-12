---
title: "Machine and screen freezes 16.04.3"
date: 2017-09-04
forum: General Help
---

### Post by Robbyx on 2017-09-04
Is there a solution to the irregular system freezes I experience? I am using the Asrock FM2A88X Extreme 6+ MB. I have 14.6gb ram. Home has 20gb free, root 15gb free. I run 2 screens off the System board. I have a ram HD and an external HD.

Processor: AMD A10-7800 Radeon R7, 12 Compute Cores 4C+8G × 4 
Graphics: Gallium 0.4 on AMD KAVERI (DRM 2.49.0 / 4.10.0-33-generic, LLVM 4.0.0)

The machine freezes, nothing will work including the keyboard and mouse and after waiting some minutes say 10m it comes back on again only to repeat later.

I have checked the memory to no avail.

Is there a log that should help find the cause? 

I moved to Ubuntu because I had this type of unreliability with Windows. I never had it till 14.04 with  Ubuntu and 16.04  is worse.

Would it help if I bought a video card? I watch streaming videos, email, and browsing, but do not do games on the machine. If a video card would solve the problem, what spec should I go for?

Robin

---

### Post by Bucky Ball on 2017-09-04
Which driver are you currently using for graphics? Please run this and post the output between code tags.

```
sudo lshw -C video
```

Remember:

> The legacy binary driver fglrx does not work on Ubuntu 16.04LTS.

From [this page]("https://www.linkedin.com/pulse/using-newer-amdgpu-driver-ubuntu-1604lts-dennis-mungai").

Having said that, the fact that the machine is dying then resurrecting itself and behaving normally (until the next crash at least) ten minutes later doesn't immediately scream 'graphics!'. If it was graphics, the machine would freeze and that's that one would think. Or you wouldn't be able to boot to a desktop at all. Maybe the experts can shed some light. ;)

---

### Post by BenginM on 2017-09-05
Hiya Robin , so this is the system Motherboard & CPU + built in AMD APU, isn't ?

[http://www.asrock.com/mb/AMD/FM2A88X%20Extreme6+/?cat=Specifications](http://www.asrock.com/mb/AMD/FM2A88X%20Extreme6+/?cat=Specifications)
[http://products.amd.com/en-gb/search/APU/AMD-A-Series-Processors/AMD-A10-Series-APU-for-Desktops/A10-7800-with-Radeon%E2%84%A2-R7-Series/9](http://products.amd.com/en-gb/search/APU/AMD-A-Series-Processors/AMD-A10-Series-APU-for-Desktops/A10-7800-with-Radeon%E2%84%A2-R7-Series/9)

With the two monitors attached  , how are these connected to the mobo , and how you set/configure them .. if you detached one or the other does the screen/system still freeze?

And which drive is in use for the AMD APU graphic ..? the command by Bucky Ball , should tell us..

is the system connected to Ethernet cable and are there other input devices attached to the mobo besides a mouse, keyboard and the two monitors while this behavior occur ?!

I don't believe a second GPU is the answer to this issue , how powerful & healthy is the power supply , and are the fans running probably?

for the software logs, look in syslog & kern.log, and Xorg.0.log.. logs in /var/log/ for something that is crashing , the kernel, a driver..

Does this occur under a previous kernel or the latest mainline kernel ! test it..

you may wish to #read :
[URL="https://wiki.ubuntu.com/X/Troubleshooting/Freeze"]https://wiki.ubuntu.com/X/Troubleshooting/Freeze

[/URL]

---

### Post by Robbyx on 2017-09-06
[QUOTE=BenginM;13683383]Hiya Robin , so this is the system Motherboard & CPU + built in AMD APU, isn't ?

[http://www.asrock.com/mb/AMD/FM2A88X%20Extreme6+/?cat=Specifications](http://www.asrock.com/mb/AMD/FM2A88X%20Extreme6+/?cat=Specifications)
[http://products.amd.com/en-gb/search/APU/AMD-A-Series-Processors/AMD-A10-Series-APU-for-Desktops/A10-7800-with-Radeon%E2%84%A2-R7-Series/9](http://products.amd.com/en-gb/search/APU/AMD-A-Series-Processors/AMD-A10-Series-APU-for-Desktops/A10-7800-with-Radeon%E2%84%A2-R7-Series/9)

With the two monitors attached  , how are these connected to the mobo , and how you set/configure them .. if you detached one or the other does the screen/system still freeze?

**Yes**

And which drive is in use for the AMD APU graphic ..? the command by Bucky Ball , should tell us..

is the system connected to Ethernet cable and are there other input devices attached to the mobo besides a mouse, keyboard and the two monitors while this behavior occur ?!
**Various USB devices, printer, sometimes mobile phone, Continuous power supply unit, external HD**

I don't believe a second GPU is the answer to this issue , how powerful & healthy is the power supply , and are the fans running probably?
**It is a new PSU. **

for the software logs, look in syslog & kern.log, and Xorg.0.log.. logs in /var/log/ for something that is crashing , the kernel, a driver..

```
dmesg | grep error
[    3.847858] kfd kfd: error getting iommu info. is the iommu enabled?
[    3.847981] kfd kfd: device (1002:130f) NOT added due to errors
[    4.301526] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    5.785851] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: errors=remount-ro
[    5.844297] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: errors=remount-ro
[    5.854776] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: errors=remount-ro
robins@robins-desktop:~$ 

```

Does this occur under a previous kernel or the latest mainline kernel ! test it..

**It occured in 14.04, so I upgraded to 16.04LTS.**

//QUOTE]
Here are samples from the syslog

```
Sep  4 02:24:48 robins-desktop slimjet.desktop[14615]: [1:16:0904/022448.112486:ERROR:render_media_log.cc(30)] MediaEvent: MEDIA_ERROR_LOG_ENTRY {"error":" Large timestamp gap detected; may cause AV sync to drift. time:46834625us expected:23440544us delta:23394081us"}

Sep  4 02:27:32 robins-desktop slimjet.desktop[14615]: [00007f86dc0177c8] postproc filter error: Unsupported input chroma (VDV0)
Sep  4 02:27:32 robins-desktop slimjet.desktop[14615]: [00007f870404f9d8] core video output error: Failed to create video filter2 'postproc'
Sep  4 02:27:32 robins-desktop slimjet.desktop[14615]: [00007f870404f9d8] core video output error: Failed to add filter 'postproc'
Sep  4 02:28:11 robins-desktop slimjet.desktop[14615]: [00007f871cc01948] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 10, expected 1) for PID 0
Sep  4 02:28:11 robins-desktop slimjet.desktop[14615]: [00007f871cc01948] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 10, expect

Sep  4 02:39:59 robins-desktop NetworkManager[1237]: <warn>  [1504489199.3898] error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: Authorization check failed: Message recipient disconnected from message bus without replying

Authorization check failed: Message recipient disconnected from message bus without replying
Sep  4 14:19:53 robins-desktop kernel: [    3.847651] kfd kfd: error getting iommu info. is the iommu enabled?
Sep  4 14:19:53 robins-desktop kernel: [    3.847776] kfd kfd: device (1002:130f) NOT added due to errors
Sep  4 14:19:53 robins-desktop kernel: [    4.644243] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
Sep  4 14:19:53 robins-desktop kernel: [    6.431674] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: errors=remount-ro
Sep  4 14:19:53 robins-desktop kernel: [    6.464544] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: errors=remount-ro
Sep  4 14:19:53 robins-desktop kernel: [    6.473892] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: errors=remount-ro
Sep  4 14:19:53 robins-desktop gpu-manager[1151]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Sep  4 14:19:58 robins-desktop /hpfax: [3599]: error: Failed to create /var/spool/cups/tmp/.hplip
Sep  4 14:19:59 robins-desktop /usr/lib/gdm3/gdm-x-session[3703]: #011(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

Sep  4 14:20:19 robins-desktop /usr/lib/gdm3/gdm-x-session[6233]: dbus-update-activation-environment: warning: error sending to systemd: org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
Sep  4 14:20:23 robins-desktop gnome-session[6249]: Gjs-Message: JS LOG: Extension "OverviewAllWindows@amiller27" had error: Error: Schema org.gnome.shell.extensions.overview-all-windows could not be found for extension OverviewAllWindows@amiller27. Please check your installation.
Sep  4 14:21:05 robins-desktop slimjet.desktop[10347]: [10347:10423:0904/142105.103362:ERROR:connection_factory_impl.cc(386)] Failed to connect to MCS endpoint with error -127
Sep  4 14:21:05 robins-desktop slimjet.desktop[10347]: [10724:10724:0904/142105.876956:ERROR:gpu_child_thread.cc(174)] Exiting GPU process due to errors during initialization

Sep  4 15:53:17 robins-desktop org.gtk.vfs.Daemon[6246]: ** (process:6680): WARNING **: send_done_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/2 (g-dbus-error-quark, 19)
Sep  5 03:22:54 robins-desktop kernel: [    3.839308] kfd kfd: error getting iommu info. is the iommu enabled?
Sep  5 03:22:54 robins-desktop kernel: [    3.839433] kfd kfd: device (1002:130f) NOT added due to errors
Sep  5 03:22:54 robins-desktop kernel: [    4.299344] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
Sep  5 03:22:54 robins-desktop kernel: [    5.854863] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: errors=remount-ro
Sep  5 03:22:54 robins-desktop kernel: [    5.859663] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: errors=remount-ro
Sep  5 03:22:54 robins-desktop kernel: [    5.862699] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: errors=remount-ro
Sep  5 03:22:54 robins-desktop gpu-manager[1213]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Sep  5 03:22:59 robins-desktop /hpfax: [3632]: error: Failed to create /var/spool/cups/tmp/.hplip
Sep  5 03:23:00 robins-desktop /usr/lib/gdm3/gdm-x-session[3689]: #011(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

Sep  5 03:49:02 robins-desktop org.a11y.atspi.Registry[3720]: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
Sep  5 03:49:02 robins-desktop NetworkManager[1169]: <warn>  [1504579742.9817] error requesting auth for org.freedesktop.NetworkManager.enable-disable-network: Authorization check failed: The name :1.9 was not provided by any .service files
Sep  5 03:49:02 robins-desktop NetworkManager[1169]: <warn>  [1504579742.9817] error requesting auth for org.freedesktop.NetworkManager.sleep-wake: Authorization check failed: The name :1.9 was not provided by any .service files

Sep  5 13:05:06 robins-desktop kernel: [ 5447.238557] blk_update_request: I/O error, dev sdb, sector 0
Sep  5 13:05:07 robins-desktop kernel: [ 5448.580066] EXT4-fs error (device sdb3): ext4_wait_block_bitmap:503: comm kworker/u8:1: Cannot read block bitmap - block_group = 0, block_bitmap = 1025
Sep  5 13:05:07 robins-desktop kernel: [ 5448.580160] EXT4-fs error (device sdb3): ext4_wait_block_bitmap:503: comm kworker/u8:1: Cannot read block bitmap - block_group = 1, block_bitmap = 1026

Sep  5 13:09:23 robins-desktop kernel: [ 5704.640807] buffer_io_error: 8 callbacks suppressed
Sep  5 13:09:23 robins-desktop kernel: [ 5704.640809] Buffer I/O error on device sdc3, logical block 34592
Sep  5 13:09:23 robins-desktop kernel: [ 5704.640816] Buffer I/O error on device sdc3, logical block 34593
Sep  5 13:09:23 robins-desktop kernel: [ 5704.640819] Buffer I/O error on device sdc3, logical block 34594
Sep  5 13:09:23 robins-desktop kernel: [ 5704.640830] Buffer I/O error on device sdc3, logical block 34595
Sep  5 13:09:23 robins-desktop kernel: [ 5704.640832] Buffer I/O error on device sdc3, logical block 34596
Sep  5 13:09:23 robins-desktop kernel: [ 5704.640841] Buffer I/O error on device sdc3, logical block 34597
Sep  5 13:09:23 robins-desktop kernel: [ 5704.640843] Buffer I/O error on device sdc3, logical block 34598
Sep  5 13:09:23 robins-desktop kernel: [ 5704.640848] Buffer I/O error on device sdc3, logical block 34599
Sep  5 13:09:23 robins-desktop kernel: [ 5704.640851] Buffer I/O error on device sdc3, logical block 34600
Sep  5 13:09:23 robins-desktop kernel: [ 5704.640855] Buffer I/O error on device sdc3, logical block 34601
Sep  5 13:09:23 robins-desktop kernel: [ 5704.641135] JBD2: Detected IO errors while flushing file data on sdc3-8

Sep  6 08:41:11 robins-desktop gnome-session[5784]: Gjs-Message: JS LOG: Received error from DBus search provider org.gnome.Photos.desktop: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name :1.135 was not provided by any .service files
Sep  6 08:47:28 robins-desktop gnome-session[5784]: Gjs-Message: JS LOG: Received error from DBus search provider org.gnome.Photos.desktop: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Sep  6 09:56:08 robins-desktop gnome-session[5784]: Gjs-Message: JS LOG: Extension "OverviewAllWindows@amiller27" had error: Error: Schema org.gnome.shell.extensions.overview-all-windows could not be found for extension OverviewAllWindows@amiller27. Please check your installation.
Sep  6 10:37:24 robins-desktop gnome-session[5784]: Gjs-Message: JS LOG: Received error from DBus search provider org.gnome.Photos.desktop: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface 'org.gnome.Shell.SearchProvider2' on object at path /org/gnome/Photos/SearchProvider
Sep  6 14:08:43 robins-desktop slimjet.desktop[14219]: [14219:14295:0906/140843.997455:ERROR:connection_factory_impl.cc(386)] Failed to connect to MCS endpoint with error -130
Sep  6 17:13:37 robins-desktop kernel: [31862.547065] gedit[2997]: segfault at 588 ip 00007fea286bb2e2 sp 00007ffc75202cd0 error 4 in libgedit.so[7fea2865b000+ad000]

```

I would have liked to give you just the unique lines but Sort -u with -k would not allow me to exclude duplicate errors not on the same address. Is there a way to produce list of the faults, with each line only showing a different type of fault? I couldn't work how to get the parameters right.

Robin

---

### Post by Robbyx on 2017-09-09
Would you like me to send you anything else to solve this crash problem? There seems to be a lot of errors in the logs I have submitted. 

 I have gone back to the previous kernel and do find some improvement, but by no means 100%

---

### Post by Robbyx on 2017-09-09
I have just had a transient crash and the following is today's entries in syslog with "error", but this is from 3am.  The crash took place at 21h and there is no entry in the log at that time which has error in its report but I hope it gives sufficient information for you to help me erradicate the freezes:

```
Sep  8 23:46:47 robins-desktop pcmanfm.desktop[31372]: pcmanfm: Fatal IO error 4 (Interrupted system call) on X server :1.
Sep  8 23:46:47 robins-desktop pcmanfm.desktop[31372]: kdeinit4: kded4 [kdeinit]: Fatal IO error 4 (Interrupted system call) on X server :1.0.
Sep  8 23:46:47 robins-desktop pcmanfm.desktop[31372]: kdeinit4: Fatal IO error: client killed
Sep  9 01:26:19 robins-desktop kernel: [    3.838872] kfd kfd: error getting iommu info. is the iommu enabled?
Sep  9 01:26:19 robins-desktop kernel: [    3.838997] kfd kfd: device (1002:130f) NOT added due to errors
Sep  9 01:26:19 robins-desktop kernel: [    4.490617] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
Sep  9 01:26:19 robins-desktop kernel: [    5.921315] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: errors=remount-ro
Sep  9 01:26:19 robins-desktop kernel: [    5.928477] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: errors=remount-ro
Sep  9 01:26:19 robins-desktop kernel: [    5.951694] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: errors=remount-ro
Sep  9 01:26:19 robins-desktop snap-repair[1213]: error: cannot use snap-repair on a classic system
Sep  9 01:26:19 robins-desktop gpu-manager[1278]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Sep  9 01:26:24 robins-desktop /hpfax: [3724]: error: Failed to create /var/spool/cups/tmp/.hplip
Sep  9 01:26:25 robins-desktop /usr/lib/gdm3/gdm-x-session[3794]: #011(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
Sep  9 01:27:08 robins-desktop /usr/lib/gdm3/gdm-x-session[7255]: #011(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
Sep  9 01:27:09 robins-desktop /usr/lib/gdm3/gdm-x-session[7255]: dbus-update-activation-environment: warning: error sending to systemd: org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
Sep  9 01:27:15 robins-desktop gnome-session[7571]: Gjs-Message: JS LOG: Extension "OverviewAllWindows@amiller27" had error: Error: Schema org.gnome.shell.extensions.overview-all-windows could not be found for extension OverviewAllWindows@amiller27. Please check your installation.
Sep  9 01:30:32 robins-desktop thunderbird.desktop[13728]: [21137:21214:0909/013032.337061:ERROR:connection_factory_impl.cc(386)] Failed to connect to MCS endpoint with error -127
Sep  9 01:30:33 robins-desktop thunderbird.desktop[13728]: [22782:22782:0909/013033.456093:ERROR:gpu_child_thread.cc(174)] Exiting GPU process due to errors during initialization
Sep  9 01:30:33 robins-desktop thunderbird.desktop[13728]: [22797:22797:0909/013033.575522:ERROR:gpu_child_thread.cc(174)] Exiting GPU process due to errors during initialization
Sep  9 01:30:33 robins-desktop thunderbird.desktop[13728]: [22804:22804:0909/013033.721468:ERROR:gpu_child_thread.cc(174)] Exiting GPU process due to errors during initialization
Sep  9 01:58:24 robins-desktop snap-repair[16990]: error: cannot use snap-repair on a classic system
Sep  9 02:05:37 robins-desktop pcmanfm.desktop[17390]: error: Broken zip file structure
Sep  9 02:08:13 robins-desktop pcmanfm.desktop[17390]: [00007f5d18017828] postproc filter error: Unsupported input chroma (VDV0)
Sep  9 02:08:13 robins-desktop pcmanfm.desktop[17390]: [00007f5d4007a4b8] core video output error: Failed to create video filter2 'postproc'
Sep  9 02:08:13 robins-desktop pcmanfm.desktop[17390]: [00007f5d4007a4b8] core video output error: Failed to add filter 'postproc'
Sep  9 02:13:34 robins-desktop pcmanfm.desktop[17390]: [00007f5d180291b8] postproc filter error: Unsupported input chroma (VDV0)
Sep  9 02:13:34 robins-desktop pcmanfm.desktop[17390]: [00007f5d4007a4b8] core video output error: Failed to create video filter2 'postproc'
Sep  9 02:13:34 robins-desktop pcmanfm.desktop[17390]: [00007f5d4007a4b8] core video output error: Failed to add filter 'postproc'
Sep  9 02:46:38 robins-desktop pcmanfm.desktop[17390]: [00007fc198017798] postproc filter error: Unsupported input chroma (VDV0)
Sep  9 02:46:38 robins-desktop pcmanfm.desktop[17390]: [00007fc1b807a598] core video output error: Failed to create video filter2 'postproc'
Sep  9 02:46:38 robins-desktop pcmanfm.desktop[17390]: [00007fc1b807a598] core video output error: Failed to add filter 'postproc'
Sep  9 02:50:04 robins-desktop pcmanfm.desktop[17390]: [00007fc198011398] postproc filter error: Unsupported input chroma (VDV0)
Sep  9 02:50:04 robins-desktop pcmanfm.desktop[17390]: [00007fc1b807a598] core video output error: Failed to create video filter2 'postproc'
Sep  9 02:50:04 robins-desktop pcmanfm.desktop[17390]: [00007fc1b807a598] core video output error: Failed to add filter 'postproc'
Sep  9 02:52:11 robins-desktop pcmanfm.desktop[17390]: [00007fa758017358] postproc filter error: Unsupported input chroma (VDV0)
Sep  9 02:52:11 robins-desktop pcmanfm.desktop[17390]: [00007fa780067058] core video output error: Failed to create video filter2 'postproc'
Sep  9 02:52:11 robins-desktop pcmanfm.desktop[17390]: [00007fa780067058] core video output error: Failed to add filter 'postproc'
Sep  9 02:53:38 robins-desktop pcmanfm.desktop[17390]: [00007fa758010978] postproc filter error: Unsupported input chroma (VDV0)
Sep  9 02:53:38 robins-desktop pcmanfm.desktop[17390]: [00007fa780067058] core video output error: Failed to create video filter2 'postproc'
Sep  9 02:53:38 robins-desktop pcmanfm.desktop[17390]: [00007fa780067058] core video output error: Failed to add filter 'postproc'
Sep  9 02:55:58 robins-desktop flareget.desktop[16787]: [00007f1bf4017fd8] postproc filter error: Unsupported input chroma (VDV0)
Sep  9 02:55:58 robins-desktop flareget.desktop[16787]: [00007f1c10120668] core video output error: Failed to create video filter2 'postproc'
Sep  9 02:55:58 robins-desktop flareget.desktop[16787]: [00007f1c10120668] core video output error: Failed to add filter 'postproc'
Sep  9 02:57:03 robins-desktop flareget.desktop[16787]: [00007f1bf401ba18] postproc filter error: Unsupported input chroma (VDV0)
Sep  9 02:57:03 robins-desktop flareget.desktop[16787]: [00007f1c10120668] core video output error: Failed to create video filter2 'postproc'
Sep  9 02:57:03 robins-desktop flareget.desktop[16787]: [00007f1c10120668] core video output error: Failed to add filter 'postproc'
Sep  9 03:16:55 robins-desktop thunderbird.desktop[13728]: [1:17:0909/031655.513136:ERROR:render_media_log.cc(30)] MediaEvent: MEDIA_ERROR_LOG_ENTRY {"error":" Large timestamp gap detected; may cause AV sync to drift. time:321015873us expected:321085532us delta:-69659us"}
Sep  9 03:16:55 robins-desktop thunderbird.desktop[13728]: [1:17:0909/031655.513794:ERROR:render_media_log.cc(30)] MediaEvent: MEDIA_ERROR_LOG_ENTRY {"error":" Large timestamp gap detected; may cause AV sync to drift. time:321039092us expected:321131971us delta:-92879us"}
Sep  9 03:16:55 robins-desktop thunderbird.desktop[13728]: [1:17:0909/031655.514231:ERROR:render_media_log.cc(30)] MediaEvent: MEDIA_ERROR_LOG_ENTRY {"error":" Large timestamp gap detected; may cause AV sync to drift. time:321062312us expected:321178411us delta:-116099us"}
Sep  9 03:42:39 robins-desktop pcmanfm.desktop[17390]: error: Broken zip file structure
Sep  9 03:42:57 robins-desktop pcmanfm.desktop[17390]: error: Broken zip file structure
Sep  9 03:43:34 robins-desktop pcmanfm.desktop[17390]: error: Broken zip file structure
Sep  9 03:44:06 robins-desktop pcmanfm.desktop[17390]: [00007f5758017778] postproc filter error: Unsupported input chroma (VDV0)
Sep  9 03:44:06 robins-desktop pcmanfm.desktop[17390]: [00007f577c00f858] core video output error: Failed to create video filter2 'postproc'
Sep  9 03:44:06 robins-desktop pcmanfm.desktop[17390]: [00007f577c00f858] core video output error: Failed to add filter 'postproc'
Sep  9 03:44:30 robins-desktop pcmanfm.desktop[17390]: [00007f575800f928] postproc filter error: Unsupported input chroma (VDV0)
Sep  9 03:44:30 robins-desktop pcmanfm.desktop[17390]: [00007f577c00f858] core video output error: Failed to create video filter2 'postproc'
Sep  9 03:44:30 robins-desktop pcmanfm.desktop[17390]: [00007f577c00f858] core video output error: Failed to add filter 'postproc'
Sep  9 03:56:04 robins-desktop pcmanfm.desktop[17390]: [00007f9c14017798] postproc filter error: Unsupported input chroma (VDV0)
Sep  9 03:56:04 robins-desktop pcmanfm.desktop[17390]: [00007f9c4004f9d8] core video output error: Failed to create video filter2 'postproc'
Sep  9 03:56:04 robins-desktop pcmanfm.desktop[17390]: [00007f9c4004f9d8] core video output error: Failed to add filter 'postproc'
Sep  9 03:56:41 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 4) for PID 0
Sep  9 03:56:41 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 4) for PID 4096
Sep  9 03:56:41 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 11) for PID 17
Sep  9 03:56:50 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 15) for PID 0
Sep  9 03:56:50 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 15) for PID 4096
Sep  9 03:56:50 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 2, expected 13) for PID 17
Sep  9 03:57:04 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS duplicate (received 15, expected 0) for PID 0
Sep  9 03:57:04 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS duplicate (received 15, expected 0) for PID 4096
Sep  9 03:57:04 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 4, expected 1) for PID 17
Sep  9 03:57:08 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 12, expected 5) for PID 0
Sep  9 03:57:08 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 12, expected 5) for PID 4096
Sep  9 03:57:08 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 11) for PID 17
Sep  9 03:57:34 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 9) for PID 0
Sep  9 03:57:34 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 9) for PID 4096
Sep  9 03:57:34 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 0, expected 15) for PID 17
Sep  9 03:57:37 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 6, expected 5) for PID 17
Sep  9 03:57:37 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 10) for PID 0
Sep  9 03:57:37 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 10) for PID 4096
Sep  9 03:57:42 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 11, expected 3) for PID 0
Sep  9 03:57:42 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 11, expected 3) for PID 4096
Sep  9 03:57:42 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 12, expected 14) for PID 17
Sep  9 03:57:43 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 15) for PID 0
Sep  9 03:57:43 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 15) for PID 4096
Sep  9 03:57:44 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 3, expected 13) for PID 17
Sep  9 03:57:44 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 9) for PID 0
Sep  9 03:57:44 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 9) for PID 4096
Sep  9 03:57:44 robins-desktop pcmanfm.desktop[17390]: [h264 @ 0x7f9c54cd8540] decode_slice_header error
Sep  9 03:57:48 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS duplicate (received 9, expected 10) for PID 17
Sep  9 03:57:48 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 3) for PID 0
Sep  9 03:57:48 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 3) for PID 4096
Sep  9 03:57:50 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS duplicate (received 12, expected 13) for PID 17
Sep  9 03:57:50 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 3) for PID 0
Sep  9 03:57:50 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 3) for PID 4096
Sep  9 03:57:51 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 6) for PID 0
Sep  9 03:57:51 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 6) for PID 4096
Sep  9 03:57:52 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 2, expected 11) for PID 0
Sep  9 03:57:52 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 2, expected 11) for PID 4096
Sep  9 03:58:02 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 0) for PID 0
Sep  9 03:58:02 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 0) for PID 4096
Sep  9 03:58:02 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 15) for PID 17
Sep  9 03:58:04 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 3) for PID 0
Sep  9 03:58:04 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 3) for PID 4096
Sep  9 03:58:05 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 8, expected 14) for PID 0
Sep  9 03:58:05 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 8, expected 14) for PID 4096
Sep  9 03:58:06 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS duplicate (received 12, expected 13) for PID 0
Sep  9 03:58:06 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS duplicate (received 12, expected 13) for PID 4096
Sep  9 03:58:06 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 11, expected 2) for PID 17
Sep  9 03:58:07 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 12, expected 14) for PID 0
Sep  9 03:58:07 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 12, expected 14) for PID 4096
Sep  9 03:58:07 robins-desktop pcmanfm.desktop[17390]: [h264 @ 0x7f9c54cd8540] decode_slice_header error
Sep  9 03:58:07 robins-desktop pcmanfm.desktop[17390]: [00007f9c54c01958] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 8, expected 12) for PID 17
Sep  9 03:58:21 robins-desktop pcmanfm.desktop[17390]: [00007f9c140d3d48] postproc filter error: Unsupported input chroma (VDV0)
Sep  9 03:58:21 robins-desktop pcmanfm.desktop[17390]: [00007f9c4004f9d8] core video output error: Failed to create video filter2 'postproc'
Sep  9 03:58:21 robins-desktop pcmanfm.desktop[17390]: [00007f9c4004f9d8] core video output error: Failed to add filter 'postproc'
Sep  9 03:58:27 robins-desktop pcmanfm.desktop[17390]: [00007f9c4007d8d8] postproc filter error: Unsupported input chroma (VDV0)
Sep  9 03:58:27 robins-desktop pcmanfm.desktop[17390]: [00007f9c24089518] core video output error: Failed to create video filter2 'postproc'
Sep  9 03:58:27 robins-desktop pcmanfm.desktop[17390]: [00007f9c24089518] core video output error: Failed to add filter 'postproc'
Sep  9 03:58:27 robins-desktop pcmanfm.desktop[17390]: [00007f9c24064d48] freetype spu text error: Breaking unbreakable line
Sep  9 03:58:27 robins-desktop pcmanfm.desktop[17390]: [00007f9c24064d48] freetype spu text error: Breaking unbreakable line
Sep  9 03:59:04 robins-desktop pcmanfm.desktop[17390]: [00007f9c4007df08] postproc filter error: Unsupported input chroma (VDV0)
Sep  9 03:59:04 robins-desktop pcmanfm.desktop[17390]: [00007f9c24089518] core video output error: Failed to create video filter2 'postproc'
Sep  9 03:59:04 robins-desktop pcmanfm.desktop[17390]: [00007f9c24089518] core video output error: Failed to add filter 'postproc'
Sep  9 03:59:04 robins-desktop pcmanfm.desktop[17390]: [00007f9c4007df08] postproc filter error: Unsupported input chroma (VDV0)
Sep  9 03:59:04 robins-desktop pcmanfm.desktop[17390]: [00007f9c24089518] core video output error: Failed to create video filter2 'postproc'
Sep  9 03:59:04 robins-desktop pcmanfm.desktop[17390]: [00007f9c24089518] core video output error: Failed to add filter 'postproc'
Sep  9 03:59:04 robins-desktop pcmanfm.desktop[17390]: [00007f9c1400f858] freetype spu text error: Breaking unbreakable line
Sep  9 03:59:19 robins-desktop pcmanfm.desktop[17390]: [00007f9c4001c068] postproc filter error: Unsupported input chroma (VDV0)
Sep  9 03:59:19 robins-desktop pcmanfm.desktop[17390]: [00007f9c24089518] core video output error: Failed to create video filter2 'postproc'
Sep  9 03:59:19 robins-desktop pcmanfm.desktop[17390]: [00007f9c24089518] core video output error: Failed to add filter 'postproc'
Sep  9 03:59:33 robins-desktop /usr/lib/gdm3/gdm-x-session[7255]: (EE) Bus error at address 0x7f76927ca000
Sep  9 03:59:33 robins-desktop /usr/lib/gdm3/gdm-x-session[7255]: Fatal server error:
Sep  9 03:59:33 robins-desktop /usr/lib/gdm3/gdm-x-session[7255]: (EE) Caught signal 7 (Bus error). Server aborting
Sep  9 03:59:33 robins-desktop /usr/lib/gdm3/gdm-x-session[7255]: (EE) Server terminated with error (1). Closing log file.
Sep  9 03:59:44 robins-desktop thunderbird.desktop[13728]: [21137:21137:0909/035944.889416:ERROR:chrome_browser_main_extra_parts_x11.cc(62)] X IO error received (X server probably went away)
Sep  9 03:59:44 robins-desktop gnome-session[7571]: (update-notifier:12400): Gdk-WARNING **: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Sep  9 03:59:44 robins-desktop pcmanfm.desktop[17390]: (file-roller:22657): Gdk-WARNING **: file-roller: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
Sep  9 03:59:44 robins-desktop flareget.desktop[16787]: flareget: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Sep  9 03:59:44 robins-desktop pcmanfm.desktop[17390]: pcmanfm: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Sep  9 03:59:44 robins-desktop gnome-session[7571]: (gnome-software:7753): Gdk-WARNING **: gnome-software: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Sep  9 03:59:44 robins-desktop org.a11y.atspi.Registry[7511]: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1"
Sep  9 03:59:44 robins-desktop gnome-session[7571]: (easystroke:7767): Gdk-WARNING **: easystroke: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Sep  9 03:59:44 robins-desktop gnome-session[7571]: (evolution-alarm-notify:7747): Gdk-WARNING **: evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Sep  9 03:59:44 robins-desktop gnome-session[7571]: xcb_connection_has_error() returned true
Sep  9 03:59:44 robins-desktop kernel: [ 9213.590424] vlc[22621]: segfault at 18 ip 00007f9c96ab9730 sp 00007f9c8c180d98 error 4 in libxcb.so.1.1.0[7f9c96aab000+21000]
Sep  9 03:59:44 robins-desktop pulseaudio[22721]: [pulseaudio] client-conf-x11.c: xcb_connection_has_error() returned true
Sep  9 03:59:45 robins-desktop gnome-session[7571]: (nautilus:7752): Gdk-WARNING **: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Sep  9 03:59:48 robins-desktop gnome-session[7571]: (gnome-shell:7642): Gdk-WARNING **: gnome-shell: Fatal IO error 25 (Inappropriate ioctl for device) on X server :1.

```

The kern log is showing repeatedly the following. The blank address is usually (16)
```
Sep  9 21:18:28 robins-desktop kernel: [29883.548574] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
Sep  9 21:18:28 robins-desktop kernel: [29883.548580] sd 6:0:0:0: [sdb] tag#0 Sense Key : Hardware Error [current] [descriptor] 
Sep  9 21:18:28 robins-desktop kernel: [29883.548583] sd 6:0:0:0: [sdb] tag#0 Add. Sense: No additional sense information
Sep  9 21:18:28 robins-desktop kernel: [29883.548588] sd 6:0:0:0: [sdb] tag#0 CDB: ATA command pass through(12)/Blank a1 06 20 da 00 00 4f c2 00 b0 00 00

```

The Xorg.0.log has these last 4 entries which I assume is from 3 am

```
Sep  9 21:18:28 robins-desktop kernel: [29883.548574] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
Sep  9 21:18:28 robins-desktop kernel: [29883.548580] sd 6:0:0:0: [sdb] tag#0 Sense Key : Hardware Error [current] [descriptor] 
Sep  9 21:18:28 robins-desktop kernel: [29883.548583] sd 6:0:0:0: [sdb] tag#0 Add. Sense: No additional sense information
Sep  9 21:18:28 robins-desktop kernel: [29883.548588] sd 6:0:0:0: [sdb] tag#0 CDB: ATA command pass through(12)/Blank a1 06 20 da 00 00 4f c2 00 b0 00 00
```

---

### Post by Lambertus on 2017-09-09
Robin.

Interested in any resolutions you get to this problem. I have had the same situation with similar log reports for a GTX board with Intel q9300 4 core chip and 6GB ram, running Ubuntu 14.04, and a radeon graphics card for two screens. Random freezing of everything, requiring power-off to restart. The longer it was left off between boots, the longer it would run. Eventually it started randomly going to the login screen and rebooting. Seemed to mostly provide errors about graphic elements, so thought it was the graphics card or driver.  Replaced that motherboard and chip; all other hardware the same. System stable under 17.04 (though with other quirks).

---

### Post by dragonfly41 on 2017-09-10
@Robbyx and @Lambertus

From time to time I experience freezes on my old system (Ubuntu 16.04 64 bits).
It is annoying not to be able to analyse log files - troubleshooting is so hit and miss
and my approach is to analyse logs for clues and then search around in google to find others with similar symptoms.

But what search patterns to use when searching?

I start by suggesting that you learn how to conduct _Google advanced searches_ which help to get to the root of your issue.

Take for example the information @Robbyx posted in post#1.

From this I extracted the patterns (clues)

Asrock FM2A88X Extreme
freeze

Next I constructed an advanced search pattern for Google search.

“Asrock FM2A88X Extreme” NEAR freeze

For an exact match put the pattern in quotes such as ..

“Asrock FM2A88X Extreme”


and in the case of @Lambertus try

"Intel q9300" NEAR freeze

I did note the common denominator that you both use dual monitors but I did not extend the example search pattern to include screen OR monitor.

...

Here is one thread which is found from the Asrock search ...

[http://forum.asrock.com/forum_posts.asp?TID=2805&title=fm2a88x-extreme4-freeze-only-with-a10-7890k](http://forum.asrock.com/forum_posts.asp?TID=2805&title=fm2a88x-extreme4-freeze-only-with-a10-7890k)

And this suggests one possible solution ...

> The problem is in the C6 State. After disabling it and testing for some days, the freeze are gone.

More on Advanced Search

[https://www.google.com/advanced_search](https://www.google.com/advanced_search)


and here ...

[https://moz.com/blog/mastering-google-search-operators-in-67-ste](https://moz.com/blog/mastering-google-search-operators-in-67-ste)

[https://moz.com/learn/seo/search-operators](https://moz.com/learn/seo/search-operators)


For example, read ... 

11. Find terms near each other

12. Find near exact-match phrases

21. Find a set of keywords in the text


===========================================


Now some tips on analysing logfiles to extract the clues/patterns to use in google search operators.

To take advantage of text analysis tools start by installing TextSTAT.

This allows a corpus (e.g. log files) to be analysed to extract clues from log files to be used in google advanced searching.

For example import into new corpus files such as /var/log/syslog.

[http://neon.niederlandistik.fu-berlin.de/en/textstat/](http://neon.niederlandistik.fu-berlin.de/en/textstat/)

You might wish to download latest ... TextSTAT-3-beta

[http://neon.niederlandistik.fu-berlin.de/static/textstat/TextSTAT-3-beta.zip](http://neon.niederlandistik.fu-berlin.de/static/textstat/TextSTAT-3-beta.zip)

but note that “latest” is September 02, 2015.

Unpack into $HOME/TextSTAT/

Also create new folder $HOME/TextSTAT-corpora/
This will hold corpus/corpora (such as your log files).

Launch terminal in $HOME/TextSTAT/

In that directory run python3 TextSTAT.py

From open window > Corpus > New Corpus

Name it to for example Ubuntu-logs.

Now you can add to corpus local files such as log files;  or if you wish url's.

You can add /var/log/syslog (and other log files).   Then look at Word frequency and Concordance.

Use the patterns to conduct google advanced search to try to track down other threads on the web.

[I]There is one issue to consider when using TextSTAT.   The space separator is used to break up the text corpus into individual words and this results in a large number of integers listed from the date pattern in syslog.   I am exploring how to change rsyslog output to use a different contiguous date pattern which does not use space separators.

[/I]There is the other consideration that some freezes occur *before* an entry is placed in log files so again I'm exploring from here ..

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

how to possibly use  logger to *inject* troubleshooting information into log files at regular intervals.
That is "I'm alive" messages.

For example a cron file might dump diagnostic information at regular intervals to be inspected in log file when next freeze occurs.

But these are just rough ideas under development.

============================================

There is other advice here for parsing log files ...

[https://www.loggly.com/ultimate-guide/analyzing-linux-logs/](https://www.loggly.com/ultimate-guide/analyzing-linux-logs/)

---

### Post by Lambertus on 2017-09-10
Dragonfly41.

Thank you very much for your helpful information on both searching more effectively, and interpreting log files. My searches must have been inadequate since they did not yield anything for the problem. After a few months, I needed a resolution (a reliable computer), and got a replacement motherboard (used). It solved that problem, and introduced others, though not as severe.

RE: two screens
The hardware-software combination with the two screens worked well together for 3 years before the problem arose.

---

### Post by wildmanne39 on 2017-09-10
> **Lambertus said:**
> Dragonfly41.

Thank you very much for your helpful information on both searching more effectively, and interpreting log files. My searches must have been inadequate since they did not yield anything for the problem. After a few months, I needed a resolution (a reliable computer), and got a replacement motherboard (used). It solved that problem, and introduced others, though not as severe.

RE: two screens
The hardware-software combination with the two screens worked well together for 3 years before the problem arose.

If you need more help please start your own thread it is better for you and the OP of this one.

Thanks

---

