---
title: "Issue with KMS / Xorg with Intel GM965 chipset"
date: 2017-01-08
forum: General Help
---

### Post by talensis on 2017-01-08
I am using Ubuntu MATE 16.10 x64 on an HP Compaq 6720s laptop with an Intel GM965 graphics chipset. I have an issue with Xorg, or rather with KMS. The main problem is that the system seems to work with software rendering and also Xorg makes the system hang randomly on start.


When I boot up the system, after the kernel loads, the screen goes black for a couple of seconds, then I see a lot of errors, but the system boots in regardless. When I run an "Xorg -configure", the configuration fails.


For troubleshooting, I have read a lot of forum articles and tried several things, but nothing helped so far.

[LIST]
[*]The system is fully updated.
[*]I have installed the latest Intel drivers with Intel Graphics Update Tool v2.0.3
[*]Tried the xorg-edgers PPA. No change, so I purged it and reverted back to vanilla.
[*]I am using kernel version 4.8.0-32 currently, but I have also tried the following: 4.9.1 (latest mainline kernel), 3.19.8 (latest from the 3.x branch). I haven't compiled a custom kernel though.
[/LIST]

Please see logs below.

LSCPI output:
```

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Mobile GM965/GL960 Integrated Graphics Controller (primary)
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at e4400000 (64-bit, non-prefetchable) [size=1M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=8]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 3
    Kernel driver in use: i915
    Kernel modules: i915, intelfb

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
    Subsystem: Hewlett-Packard Company Mobile GM965/GL960 Integrated Graphics Controller (secondary)
    Flags: bus master, fast devsel, latency 0
    Memory at e4500000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [d0] Power Management version 3

```


From system logs from boot (with kernel 4.9.1, but it's the same with all 4.x kernel versions):
```

[   12.252049] [drm:drm_atomic_helper_commit_cleanup_done [drm_kms_helper]] *ERROR* [CRTC:26:pipe A] flip_done timed out
[   12.356060] ------------[ cut here ]------------
[   12.356096] WARNING: CPU: 1 PID: 185 at /home/kernel/COD/linux/drivers/gpu/drm/drm_irq.c:1252 drm_wait_one_vblank+0x1aa/0x1b0 [drm]
[   12.356105] vblank wait timed out on crtc 0
[   12.356109] Modules linked in: uas usb_storage i915 i2c_algo_bit psmouse drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops pata_acpi ahci drm libahci e1000e ptp pps_core wmi fjes video
[   12.356143] CPU: 1 PID: 185 Comm: kworker/u4:5 Not tainted 4.9.1-040901-generic #201701060531
[   12.356151] Hardware name: Hewlett-Packard HP Compaq 6720s/30D8, BIOS 68MDU Ver. F.0B 06/20/2008
[   12.356162] Workqueue: events_unbound async_run_entry_fn
[   12.356168]  ffffa9214098f9d0 ffffffffa6618042 ffffa9214098fa20 0000000000000000
[   12.356178]  ffffa9214098fa10 ffffffffa6283dab 000004e4722b7800 ffff9c5872070000
[   12.356188]  0000000000000000 0000000000000000 0000000001000001 ffff9c58725d6008
[   12.356198] Call Trace:
[   12.356207]  [<ffffffffa6618042>] dump_stack+0x63/0x81
[   12.356214]  [<ffffffffa6283dab>] __warn+0xcb/0xf0
[   12.356220]  [<ffffffffa6283e2f>] warn_slowpath_fmt+0x5f/0x80
[   12.356233]  [<ffffffffa62c8c26>] ? finish_wait+0x56/0x70
[   12.356249]  [<ffffffffc0186a3a>] drm_wait_one_vblank+0x1aa/0x1b0 [drm]
[   12.356255]  [<ffffffffa62c8f90>] ? wake_atomic_t_function+0x60/0x60
[   12.356319]  [<ffffffffc030fceb>] intel_get_load_detect_pipe+0x5fb/0x610 [i915]
[   12.356359]  [<ffffffffc034b305>] intel_tv_detect+0x155/0x550 [i915]
[   12.356370]  [<ffffffffc022515f>] drm_helper_probe_single_connector_modes+0x3ff/0x4f0 [drm_kms_helper]
[   12.356383]  [<ffffffffc0233ace>] drm_fb_helper_initial_config+0xae/0x430 [drm_kms_helper]
[   12.356423]  [<ffffffffc0324f68>] intel_fbdev_initial_config+0x18/0x30 [i915]
[   12.356429]  [<ffffffffa62a8607>] async_run_entry_fn+0x37/0x150
[   12.356435]  [<ffffffffa629ecdc>] process_one_work+0x1fc/0x4b0
[   12.356440]  [<ffffffffa629efdb>] worker_thread+0x4b/0x500
[   12.356445]  [<ffffffffa629ef90>] ? process_one_work+0x4b0/0x4b0
[   12.356451]  [<ffffffffa629ef90>] ? process_one_work+0x4b0/0x4b0
[   12.356456]  [<ffffffffa62a5339>] kthread+0xd9/0xf0
[   12.356462]  [<ffffffffa62a5260>] ? kthread_park+0x60/0x60
[   12.356468]  [<ffffffffa6a8dab5>] ret_from_fork+0x25/0x30
[   12.356473] ---[ end trace 46baaebcf4435a78 ]---
[   12.541252] ------------[ cut here ]------------
[   12.541272] WARNING: CPU: 0 PID: 185 at /home/kernel/COD/linux/drivers/gpu/drm/drm_irq.c:1252 drm_wait_one_vblank+0x1aa/0x1b0 [drm]
[   12.541281] vblank wait timed out on crtc 0
[   12.541286] Modules linked in: uas usb_storage i915 i2c_algo_bit psmouse drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops pata_acpi ahci drm libahci e1000e ptp pps_core wmi fjes video
[   12.541318] CPU: 0 PID: 185 Comm: kworker/u4:5 Tainted: G        W       4.9.1-040901-generic #201701060531
[   12.541326] Hardware name: Hewlett-Packard HP Compaq 6720s/30D8, BIOS 68MDU Ver. F.0B 06/20/2008
[   12.541334] Workqueue: events_unbound async_run_entry_fn
[   12.541340]  ffffa9214098f890 ffffffffa6618042 ffffa9214098f8e0 0000000000000000
[   12.541349]  ffffa9214098f8d0 ffffffffa6283dab 000004e400010bce ffff9c5872070000
[   12.541358]  0000000000000000 0000000000000000 0000000002000001 ffff9c58725d6008
[   12.541366] Call Trace:
[   12.541372]  [<ffffffffa6618042>] dump_stack+0x63/0x81
[   12.541378]  [<ffffffffa6283dab>] __warn+0xcb/0xf0
[   12.541384]  [<ffffffffa6283e2f>] warn_slowpath_fmt+0x5f/0x80
[   12.541390]  [<ffffffffa62c8c26>] ? finish_wait+0x56/0x70
[   12.541405]  [<ffffffffc0186a3a>] drm_wait_one_vblank+0x1aa/0x1b0 [drm]
[   12.541411]  [<ffffffffa62c8f90>] ? wake_atomic_t_function+0x60/0x60
[   12.541450]  [<ffffffffc0308f8e>] intel_pre_plane_update+0x12e/0x140 [i915]
[   12.541489]  [<ffffffffc0309600>] intel_atomic_commit_tail+0x150/0x1010 [i915]
[   12.541530]  [<ffffffffc030a807>] intel_atomic_commit+0x347/0x490 [i915]
[   12.541549]  [<ffffffffc0199a4a>] ? drm_atomic_check_only+0x30a/0x590 [drm]
[   12.541554]  [<ffffffffa62c8c26>] ? finish_wait+0x56/0x70
[   12.541572]  [<ffffffffc0199d19>] drm_atomic_commit+0x49/0x50 [drm]
[   12.541610]  [<ffffffffc030fd50>] intel_release_load_detect_pipe+0x50/0x90 [i915]
[   12.541650]  [<ffffffffc034b539>] intel_tv_detect+0x389/0x550 [i915]
[   12.541661]  [<ffffffffc022515f>] drm_helper_probe_single_connector_modes+0x3ff/0x4f0 [drm_kms_helper]
[   12.541674]  [<ffffffffc0233ace>] drm_fb_helper_initial_config+0xae/0x430 [drm_kms_helper]
[   12.541714]  [<ffffffffc0324f68>] intel_fbdev_initial_config+0x18/0x30 [i915]
[   12.541720]  [<ffffffffa62a8607>] async_run_entry_fn+0x37/0x150
[   12.541725]  [<ffffffffa629ecdc>] process_one_work+0x1fc/0x4b0
[   12.541731]  [<ffffffffa629efdb>] worker_thread+0x4b/0x500
[   12.541736]  [<ffffffffa629ef90>] ? process_one_work+0x4b0/0x4b0
[   12.541741]  [<ffffffffa629ef90>] ? process_one_work+0x4b0/0x4b0
[   12.541747]  [<ffffffffa62a5339>] kthread+0xd9/0xf0
[   12.541752]  [<ffffffffa62a5260>] ? kthread_park+0x60/0x60
[   12.541758]  [<ffffffffa6a8dab5>] ret_from_fork+0x25/0x30
[   12.541763] ---[ end trace 46baaebcf4435a79 ]---
[   12.597679] fbcon: inteldrmfb (fb0) is primary device
[   13.301956] Console: switching to colour frame buffer device 160x50
[   13.321369] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device

```


Xorg.0.log:
```

[ 470.564] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[ 470.564] X Protocol Version 11, Revision 0
[ 470.565] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[ 470.565] Current Operating System: Linux TaleLaptopLinux 4.8.0-32-generic #34-Ubuntu SMP Tue Dec 13 14:30:43 UTC 2016 x86_64
[ 470.565] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.8.0-32-generic root=UUID=89e4ba68-d25a-4cc0-a87b-98b2f3974504 ro
[ 470.566] Build Date: 02 November 2016 10:06:55PM
[ 470.567] xorg-server 2:1.18.4-1ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 
[ 470.567] Current version of pixman: 0.33.6
[ 470.569]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[ 470.569] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 470.573] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 27 20:40:04 2016
[ 470.573] (II) Loader magic: 0x56218a60e020
[ 470.573] (II) Module ABI versions:
[ 470.573]     X.Org ANSI C Emulation: 0.4
[ 470.573]     X.Org Video Driver: 20.0
[ 470.573]     X.Org XInput driver : 22.1
[ 470.573]     X.Org Server Extension : 9.0
[ 470.573] (--) using VT number 2
[ 470.573] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[ 470.574] (II) xfree86: Adding drm device (/dev/dri/card0)
[ 470.582] (--) PCI:*(0:0:2:0) 8086:2a02:103c:30d8 rev 12, Mem @ 0xe4400000/1048576, 0xd0000000/268435456, I/O @ 0x00004000/8, BIOS @ 0x????????/131072
[ 470.582] (--) PCI: (0:0:2:1) 8086:2a03:103c:30d8 rev 12, Mem @ 0xe4500000/1048576
[ 470.583] List of video drivers:
[ 470.584]     amdgpu
[ 470.585]     ati
[ 470.586]     intel
[ 470.588]     qxl
[ 470.589]     radeon
[ 470.590]     vmware
[ 470.591]     modesetting
[ 470.592]     vesa
[ 470.593]     fbdev
[ 470.594]     nouveau
[ 470.594] (II) LoadModule: "amdgpu"
[ 470.594] (II) Loading /usr/lib/xorg/modules/drivers/amdgpu_drv.so
[ 470.595] (II) Module amdgpu: vendor="X.Org Foundation"
[ 470.595]     compiled for 1.18.4, module version = 1.1.2
[ 470.595]     Module class: X.Org Video Driver
[ 470.595]     ABI class: X.Org Video Driver, version 20.0
[ 470.595] (II) LoadModule: "ati"
[ 470.595] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[ 470.595] (II) Module ati: vendor="X.Org Foundation"
[ 470.595]     compiled for 1.18.4, module version = 7.7.1
[ 470.595]     Module class: X.Org Video Driver
[ 470.595]     ABI class: X.Org Video Driver, version 20.0
[ 470.595] (II) LoadModule: "intel"
[ 470.595] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[ 470.595] (II) Module intel: vendor="X.Org Foundation"
[ 470.595]     compiled for 1.18.3, module version = 2.99.917
[ 470.595]     Module class: X.Org Video Driver
[ 470.595]     ABI class: X.Org Video Driver, version 20.0
[ 470.595] (II) LoadModule: "qxl"
[ 470.596] (II) Loading /usr/lib/xorg/modules/drivers/qxl_drv.so
[ 470.596] (II) Module qxl: vendor="X.Org Foundation"
[ 470.596]     compiled for 1.18.1, module version = 0.1.4
[ 470.596]     Module class: X.Org Video Driver
[ 470.596]     ABI class: X.Org Video Driver, version 20.0
[ 470.596] (II) LoadModule: "radeon"
[ 470.596] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[ 470.597] (II) Module radeon: vendor="X.Org Foundation"
[ 470.597]     compiled for 1.18.4, module version = 7.7.1
[ 470.597]     Module class: X.Org Video Driver
[ 470.597]     ABI class: X.Org Video Driver, version 20.0
[ 470.597] (II) LoadModule: "vmware"
[ 470.597] (II) Loading /usr/lib/xorg/modules/drivers/vmware_drv.so
[ 470.613] (II) Module vmware: vendor="X.Org Foundation"
[ 470.613]     compiled for 1.18.1, module version = 13.1.0
[ 470.613]     Module class: X.Org Video Driver
[ 470.613]     ABI class: X.Org Video Driver, version 20.0
[ 470.613] (II) LoadModule: "modesetting"
[ 470.613] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[ 470.613] (II) Module modesetting: vendor="X.Org Foundation"
[ 470.613]     compiled for 1.18.4, module version = 1.18.4
[ 470.613]     Module class: X.Org Video Driver
[ 470.613]     ABI class: X.Org Video Driver, version 20.0
[ 470.613] (II) LoadModule: "vesa"
[ 470.613] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 470.613] (II) Module vesa: vendor="X.Org Foundation"
[ 470.613]     compiled for 1.18.1, module version = 2.3.4
[ 470.613]     Module class: X.Org Video Driver
[ 470.613]     ABI class: X.Org Video Driver, version 20.0
[ 470.613] (II) LoadModule: "fbdev"
[ 470.614] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 470.614] (II) Module fbdev: vendor="X.Org Foundation"
[ 470.614]     compiled for 1.18.1, module version = 0.4.4
[ 470.614]     Module class: X.Org Video Driver
[ 470.614]     ABI class: X.Org Video Driver, version 20.0
[ 470.614] (II) LoadModule: "nouveau"
[ 470.614] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[ 470.614] (II) Module nouveau: vendor="X.Org Foundation"
[ 470.614]     compiled for 1.18.3, module version = 1.0.12
[ 470.614]     Module class: X.Org Video Driver
[ 470.614]     ABI class: X.Org Video Driver, version 20.0
[ 470.614] (II) intel(G0): Using Kernel Mode Setting driver: i915, version 1.6.0 20160711
[ 470.614] (II) intel(G0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20160706-1ubuntu1 (Timo Aaltonen <tjaalton@debian.org>)
[ 470.614] (II) intel(G0): SNA compiled for use with valgrind
[ 470.614] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[ 470.615] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[ 470.615] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[ 470.615] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[ 470.615] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[ 470.615] (WW) Falling back to old probe method for vesa
[ 470.615] (WW) Falling back to old probe method for fbdev
[ 470.647] (++) Using config file: "/home/talensis/xorg.conf.new"
[ 470.649] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 470.650] (==) ServerLayout "X.org Configured"
[ 470.651] (**) |-->Screen "Screen0" (0)
[ 470.651] (**) | |-->Monitor "Monitor0"
[ 470.651] (**) | |-->Device "Card0"
[ 470.651] (**) |-->Input Device "Mouse0"
[ 470.651] (**) |-->Input Device "Keyboard0"
[ 470.651] (==) Automatically adding devices
[ 470.651] (==) Automatically enabling devices
[ 470.651] (==) Automatically adding GPU devices
[ 470.651] (==) Max clients allowed: 256, resource mask: 0x1fffff
[ 470.651] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 470.651]     Entry deleted from font path.
[ 470.651] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 470.651]     Entry deleted from font path.
[ 470.651] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 470.651]     Entry deleted from font path.
[ 470.652] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 470.652]     Entry deleted from font path.
[ 470.652] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 470.652]     Entry deleted from font path.
[ 470.652] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 470.652]     Entry deleted from font path.
[ 470.652] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 470.652]     Entry deleted from font path.
[ 470.652] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 470.652]     Entry deleted from font path.
[ 470.652] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 470.652]     Entry deleted from font path.
[ 470.652] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 470.652]     Entry deleted from font path.
[ 470.652] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[ 470.652] (**) ModulePath set to "/usr/lib/xorg/modules"
[ 470.652] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[ 470.652] (WW) Disabling Mouse0
[ 470.652] (WW) Disabling Keyboard0
[ 470.652] (WW) Falling back to old probe method for modesetting
[ 470.652] (EE) 
[ 470.654] (EE) Backtrace:
[ 470.655] (EE) 0: /usr/lib/xorg/Xorg (xorg_backtrace+0x4a) [0x56218a3819fa]
[ 470.657] (EE) 1: /usr/lib/xorg/Xorg (0x56218a1c8000+0x1bdd69) [0x56218a385d69]
[ 470.658] (EE) 2: /lib/x86_64-linux-gnu/libc.so.6 (0x7f45d13aa000+0x35860) [0x7f45d13df860]
[ 470.659] (EE) 
[ 470.661] (EE) Segmentation fault at address 0x0
[ 470.662] (EE) 
Fatal server error:
[ 470.665] (EE) Caught signal 11 (Segmentation fault). Server aborting
[ 470.666] (EE) 
[ 470.667] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
for help. 
[ 470.673] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 470.675] (EE)

```

Can you please help, what should I do next? Would compiling a custom kernel with modifications in the Intel i915 driver help? If yes, which settings should I change in the kernel configuration?

Thanks in advance!

---

### Post by mörgæs on 2017-01-09
Before compiling I would do a simple test: Trying UXA in stead of SNA graphics. 

If you follow the link in my signature there is an xorg.conf you can try.

---

### Post by talensis on 2017-01-09
Thanks, mörgæs. It did seem to improve the situation, but I am still not out of the woods, yet.

I receive a new error message: "Number of created screens does not match number of detected devices. Configuration failed."

Xorg.0.log:

```

[    71.901] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    71.901] X Protocol Version 11, Revision 0
[    71.901] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[    71.901] Current Operating System: Linux TaleLaptopLinux 4.9.1-040901-generic #201701060531 SMP Fri Jan 6 10:33:15 UTC 2017 x86_64
[    71.901] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.9.1-040901-generic root=UUID=89e4ba68-d25a-4cc0-a87b-98b2f3974504 ro
[    71.902] Build Date: 02 November 2016  10:06:55PM
[    71.902] xorg-server 2:1.18.4-1ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 
[    71.902] Current version of pixman: 0.33.6
[    71.902]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    71.902] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    71.902] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 10 04:03:51 2017
[    71.903] (II) Loader magic: 0x5572b92d4020
[    71.903] (II) Module ABI versions:
[    71.903]     X.Org ANSI C Emulation: 0.4
[    71.903]     X.Org Video Driver: 20.0
[    71.903]     X.Org XInput driver : 22.1
[    71.903]     X.Org Server Extension : 9.0
[    71.904] (--) using VT number 2


[    71.904] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    71.904] (II) xfree86: Adding drm device (/dev/dri/card0)
[    71.919] (--) PCI:*(0:0:2:0) 8086:2a02:103c:30d8 rev 12, Mem @ 0xe4400000/1048576, 0xd0000000/268435456, I/O @ 0x00004000/8, BIOS @ 0x????????/131072
[    71.919] (--) PCI: (0:0:2:1) 8086:2a03:103c:30d8 rev 12, Mem @ 0xe4500000/1048576
[    71.919] List of video drivers:
[    71.919]     amdgpu
[    71.920]     ati
[    71.920]     intel
[    71.920]     qxl
[    71.920]     radeon
[    71.920]     vmware
[    71.920]     modesetting
[    71.920]     vesa
[    71.920]     fbdev
[    71.920]     nouveau
[    71.920] (II) LoadModule: "amdgpu"
[    71.921] (II) Loading /usr/lib/xorg/modules/drivers/amdgpu_drv.so
[    71.984] (II) Module amdgpu: vendor="X.Org Foundation"
[    71.984]     compiled for 1.18.4, module version = 1.1.2
[    71.984]     Module class: X.Org Video Driver
[    71.984]     ABI class: X.Org Video Driver, version 20.0
[    71.985] (II) LoadModule: "ati"
[    71.985] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    71.996] (II) Module ati: vendor="X.Org Foundation"
[    71.996]     compiled for 1.18.4, module version = 7.7.1
[    71.996]     Module class: X.Org Video Driver
[    71.996]     ABI class: X.Org Video Driver, version 20.0
[    71.996] (II) LoadModule: "intel"
[    71.996] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    72.040] (II) Module intel: vendor="X.Org Foundation"
[    72.040]     compiled for 1.18.3, module version = 2.99.917
[    72.040]     Module class: X.Org Video Driver
[    72.040]     ABI class: X.Org Video Driver, version 20.0
[    72.040] (II) LoadModule: "qxl"
[    72.040] (II) Loading /usr/lib/xorg/modules/drivers/qxl_drv.so
[    72.065] (II) Module qxl: vendor="X.Org Foundation"
[    72.065]     compiled for 1.18.1, module version = 0.1.4
[    72.065]     Module class: X.Org Video Driver
[    72.065]     ABI class: X.Org Video Driver, version 20.0
[    72.065] (II) LoadModule: "radeon"
[    72.065] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    72.112] (II) Module radeon: vendor="X.Org Foundation"
[    72.112]     compiled for 1.18.4, module version = 7.7.1
[    72.112]     Module class: X.Org Video Driver
[    72.112]     ABI class: X.Org Video Driver, version 20.0
[    72.112] (II) LoadModule: "vmware"
[    72.113] (II) Loading /usr/lib/xorg/modules/drivers/vmware_drv.so
[    73.344] (II) Module vmware: vendor="X.Org Foundation"
[    73.344]     compiled for 1.18.1, module version = 13.1.0
[    73.344]     Module class: X.Org Video Driver
[    73.344]     ABI class: X.Org Video Driver, version 20.0
[    73.344] (II) LoadModule: "modesetting"
[    73.345] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    73.363] (II) Module modesetting: vendor="X.Org Foundation"
[    73.363]     compiled for 1.18.4, module version = 1.18.4
[    73.363]     Module class: X.Org Video Driver
[    73.363]     ABI class: X.Org Video Driver, version 20.0
[    73.363] (II) LoadModule: "vesa"
[    73.363] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    73.713] (II) Module vesa: vendor="X.Org Foundation"
[    73.713]     compiled for 1.18.1, module version = 2.3.4
[    73.713]     Module class: X.Org Video Driver
[    73.713]     ABI class: X.Org Video Driver, version 20.0
[    73.713] (II) LoadModule: "fbdev"
[    73.713] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    73.720] (II) Module fbdev: vendor="X.Org Foundation"
[    73.720]     compiled for 1.18.1, module version = 0.4.4
[    73.720]     Module class: X.Org Video Driver
[    73.720]     ABI class: X.Org Video Driver, version 20.0
[    73.720] (II) LoadModule: "nouveau"
[    73.720] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    73.738] (II) Module nouveau: vendor="X.Org Foundation"
[    73.738]     compiled for 1.18.3, module version = 1.0.12
[    73.738]     Module class: X.Org Video Driver
[    73.738]     ABI class: X.Org Video Driver, version 20.0
[    73.750] (II) intel(G0): Using Kernel Mode Setting driver: i915, version 1.6.0 20160919
[    73.750] (II) intel(G0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20160706-1ubuntu1 (Timo Aaltonen <tjaalton@debian.org>)
[    73.750] (II) intel(G0): SNA compiled for use with valgrind
[    73.757] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    73.757] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    73.757] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    73.757] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    73.757] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    73.757] (WW) Falling back to old probe method for vesa
[    73.757] (WW) Falling back to old probe method for fbdev
[    73.814] (++) Using config file: "/home/talensis/xorg.conf.new"
[    73.814] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    73.872] (==) ServerLayout "X.org Configured"
[    73.872] (**) |-->Screen "Screen0" (0)
[    73.872] (**) |   |-->Monitor "Monitor0"
[    73.873] (**) |   |-->Device "Card0"
[    73.873] (**) |   |-->GPUDevice "Card0"
[    73.873] (**) |-->Input Device "Mouse0"
[    73.873] (**) |-->Input Device "Keyboard0"
[    73.873] (==) Automatically adding devices
[    73.873] (==) Automatically enabling devices
[    73.873] (==) Automatically adding GPU devices
[    73.883] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    73.883] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    73.883]     Entry deleted from font path.
[    73.883] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    73.883]     Entry deleted from font path.
[    73.883] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    73.883]     Entry deleted from font path.
[    73.883] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    73.883]     Entry deleted from font path.
[    73.883] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    73.883]     Entry deleted from font path.
[    73.883] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    73.883]     Entry deleted from font path.
[    73.883] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    73.883]     Entry deleted from font path.
[    73.883] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    73.883]     Entry deleted from font path.
[    73.883] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    73.883]     Entry deleted from font path.
[    73.883] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    73.883]     Entry deleted from font path.
[    73.883] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    73.883] (**) ModulePath set to "/usr/lib/xorg/modules"
[    73.883] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    73.883] (WW) Disabling Mouse0
[    73.883] (WW) Disabling Keyboard0
[    73.884] (WW) Falling back to old probe method for modesetting
[    73.887] Number of created screens does not match number of detected devices.
  Configuration failed.

```

I did find several forum threads on this topic, but none of them seemed to apply for me. I have removed ~/.Xauthority, but the only thing it did that I couldn't run Xorg anymore. I have restored it since then.

Anyway, I have created a .conf file into /usr/share/X11/xorg.conf.d/

```

Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "uxa"
EndSection


Section "Monitor"
    Identifier "foo"
EndSection


Section "Screen"
    Identifier "Default Screen"
    Device "Mobile GM965/Gl960 Integrated Graphics Controller (primary)"
    Monitor "foo"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1280x800" "1024x768" "800x600"
    EndSubSection
EndSection

```


Tried adding several Screens and Monitors, but it ignored the configuration. However, I found the below in ~/xorg.conf.new
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

```

I have added a Screen1, but it didn't help either.

**Any ideas?**

On another note: I ran the live version of both Ubuntu 16.04 LTS and 14.04 LTS from a flashdrive and none of them produced the KMS kernel warnings, though I didn't install any of them. They may use different kernel parameters at boot than the installed versions.

 When I stopped Xorg in 16.04, and tried the "sudo Xorg -configure" command, I received the same crash before adding the UXA acceleration to the currently used version. With 14.04, I only received the same "Number of created screens does not match number of detected devices." error. I saved the demsg and Xorg.0.log outputs, if it helps.

---

### Post by mörgæs on 2017-01-11
> **talensis said:**
> I ran the live version of both Ubuntu 16.04 LTS and 14.04 LTS from a flashdrive and none of them produced the KMS kernel warnings, though I didn't install any of them. They may use different kernel parameters at boot than the installed versions.

If you have the space you could try installing the 16.04.1 release in a new partition.

---

### Post by talensis on 2017-01-11
I was thinking the same, so eventually I scrapped my 16.10 installation and installed 16.04 LTS instead. Weirdly, the kernel error messages are gone now. So far, there seem to be no issues with Xorg. I do see some tearing when I watch something on YouTube with quick camera movements, but it's nothing serious.

Thanks [COLOR=#000000]mörgæs for your help. I am going to test different things on the system for a couple of days and see if there are any crashes.[/COLOR]

---

### Post by mörgæs on 2017-01-11
Good, please mark the thread solved. It will help others in a similar situation.

---

### Post by talensis on 2017-01-11
Done. Thanks again, I appreciate your help it.

---

### Post by mobrien118 on 2017-03-11
> **talensis said:**
> I was thinking the same, so eventually I scrapped my 16.10 installation and installed 16.04 LTS instead. Weirdly, the kernel error messages are gone now. So far, there seem to be no issues with Xorg. I do see some tearing when I watch something on YouTube with quick camera movements, but it's nothing serious.

Thanks [COLOR=#000000]mörgæs for your help. I am going to test different things on the system for a couple of days and see if there are any crashes.[/COLOR]

Any chance you could be more specific on what combination of steps resolved the issue?

I'm on stock 16.04.2 and having the same issue. I just upgraded the kernel to 4.9.0 (based on recommendation from another thread) and still having issues.

I was on 16.10 and was having the issues so reverted to 16.04.2 in hopes it would help, but no joy.

I don't know if you were having all of the same symptoms... I occasionally have the whole system lock up, or have the wifi stop working randomly - Also, I'm having trouble running apps on an android emulator and certain other apps that seem to be GPU heavy.

Very frustrating issue...

Thanks!

--mobrien118

---

### Post by mörgæs on 2017-03-12
> **mobrien118 said:**
> 
I'm on stock 16.04.2 and having the same issue
but do you also have the same hardware? 

If you do then you are welcome to post here. If not then it's better to open a new thread.

Please begin with the **lspci** command as seen in original post.

---

### Post by nikolaj-l on 2017-07-11
GRUB_CMDLINE_LINUX_DEFAULT="video=SVIDEO-1:d" on /etc/default/grub
grub-mkconfig -o /boot/grub/grub.cfg

See: [https://bbs.archlinux.org/viewtopic.php?id=218581&p=3](https://bbs.archlinux.org/viewtopic.php?id=218581&p=3)

---

### Post by p3k on 2017-11-03
> **nikolaj-l said:**
> GRUB_CMDLINE_LINUX_DEFAULT="video=SVIDEO-1:d" on /etc/default/grub
grub-mkconfig -o /boot/grub/grub.cfg

See: [https://bbs.archlinux.org/viewtopic.php?id=218581&p=3](https://bbs.archlinux.org/viewtopic.php?id=218581&p=3)

I am having similar problems with the chipset but I am booting with rEFInd (i.e. no grub) – how would I add the video kernel parameter in this case?

---

### Post by p3k on 2018-01-14
(Deleted)

---

### Post by p3k on 2018-01-14
Found the solution myself, see here: [https://elementaryos.stackexchange.com/questions/13844/long-boot-and-resume-times-on-2008-macbook/14420#14420](https://elementaryos.stackexchange.com/questions/13844/long-boot-and-resume-times-on-2008-macbook/14420#14420)

---

