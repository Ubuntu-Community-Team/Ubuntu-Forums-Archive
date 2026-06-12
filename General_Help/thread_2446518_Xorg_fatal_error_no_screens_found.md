---
title: "Xorg fatal error: no screens found"
date: 2020-07-01
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2020-07-01
seems like Xorg can't find my display port monitors sometimes?
when wakeing from sleep mode sometimes the system crashes, numlock is unresponsice but REISUB works
I have a 8GB RX 580 for a video card
```
~$ cat /var/log/Xorg.1.log
[  4455.830] 
X.Org X Server 1.19.6
Release Date: 2017-12-20
[  4455.830] X Protocol Version 11, Revision 0
[  4455.830] Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
[  4455.830] Current Operating System: Linux Z97Killer 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64
[   4455.830] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-4.15.0-20-generic  root=UUID=43fff14c-8de1-4f07-b37e-333ff7d96675 ro quiet splash
[  4455.830] Build Date: 13 April 2018  08:07:36PM
[  4455.830] xorg-server 2:1.19.6-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[  4455.830] Current version of pixman: 0.34.0
[  4455.830]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  4455.830] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  4455.830] (==) Log file: "/var/log/Xorg.1.log", Time: Tue May  1 13:10:48 2018
[  4455.830] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  4455.830] (==) No Layout section.  Using the first Screen section.
[  4455.830] (==) No screen section available. Using defaults.
[  4455.830] (**) |-->Screen "Default Screen Section" (0)
[  4455.830] (**) |   |-->Monitor "<default monitor>"
[  4455.831] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  4455.831] (==) Automatically adding devices
[  4455.831] (==) Automatically enabling devices
[  4455.831] (==) Automatically adding GPU devices
[  4455.831] (==) Automatically binding GPU devices
[  4455.831] (==) Max clients allowed: 256, resource mask: 0x1fffff
[  4455.831] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  4455.831]     Entry deleted from font path.
[  4455.831] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  4455.831]     Entry deleted from font path.
[  4455.831] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  4455.831]     Entry deleted from font path.
[  4455.831] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  4455.831]     Entry deleted from font path.
[  4455.831] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  4455.831]     Entry deleted from font path.
[  4455.831] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  4455.831] (==) ModulePath set to "/usr/lib/xorg/modules"
[  4455.831] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  4455.831] (II) Loader magic: 0x55f6810de020
[  4455.831] (II) Module ABI versions:
[  4455.831]     X.Org ANSI C Emulation: 0.4
[  4455.831]     X.Org Video Driver: 23.0
[  4455.831]     X.Org XInput driver : 24.1
[  4455.831]     X.Org Server Extension : 10.0
[  4455.831] (++) using VT number 8

[   4455.831] (II) systemd-logind: logind integration requires -keeptty and  -keeptty was not provided, disabling logind integration
[  4455.831] (II) xfree86: Adding drm device (/dev/dri/card0)
[  4455.831] (EE) /dev/dri/card0: failed to set DRM interface version 1.4: Permission denied
[   4455.833] (--) PCI:*(0:1:0:0) 10de:11c2:10de:104c rev 161, Mem @  0xee000000/16777216, 0xe0000000/134217728, 0xe8000000/33554432, I/O @  0x0000e000/128, BIOS @ 0x????????/131072
[  4455.833] (II) LoadModule: "glx"
[  4455.833] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  4455.833] (II) Module glx: vendor="X.Org Foundation"
[  4455.833]     compiled for 1.19.6, module version = 1.0.0
[  4455.833]     ABI class: X.Org Server Extension, version 10.0
[  4455.833] (==) Matched nouveau as autoconfigured driver 0
[  4455.833] (==) Matched modesetting as autoconfigured driver 1
[  4455.833] (==) Matched fbdev as autoconfigured driver 2
[  4455.833] (==) Matched vesa as autoconfigured driver 3
[  4455.833] (==) Assigned the driver to the xf86ConfigLayout
[  4455.833] (II) LoadModule: "nouveau"
[  4455.833] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  4455.833] (II) Module nouveau: vendor="X.Org Foundation"
[  4455.833]     compiled for 1.19.3, module version = 1.0.15
[  4455.833]     Module class: X.Org Video Driver
[  4455.833]     ABI class: X.Org Video Driver, version 23.0
[  4455.833] (II) LoadModule: "modesetting"
[  4455.833] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  4455.834] (II) Module modesetting: vendor="X.Org Foundation"
[  4455.834]     compiled for 1.19.6, module version = 1.19.6
[  4455.834]     Module class: X.Org Video Driver
[  4455.834]     ABI class: X.Org Video Driver, version 23.0
[  4455.834] (II) LoadModule: "fbdev"
[  4455.834] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  4455.834] (II) Module fbdev: vendor="X.Org Foundation"
[  4455.834]     compiled for 1.19.3, module version = 0.4.4
[  4455.834]     Module class: X.Org Video Driver
[  4455.834]     ABI class: X.Org Video Driver, version 23.0
[  4455.834] (II) LoadModule: "vesa"
[  4455.834] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  4455.834] (II) Module vesa: vendor="X.Org Foundation"
[  4455.834]     compiled for 1.19.3, module version = 2.3.4
[  4455.834]     Module class: X.Org Video Driver
[  4455.834]     ABI class: X.Org Video Driver, version 23.0
[  4455.834] (II) NOUVEAU driver Date:   Fri Apr 21 14:41:17 2017 -0400
[  4455.834] (II) NOUVEAU driver for NVIDIA chipset families :
[  4455.834]     RIVA TNT        (NV04)
[  4455.834]     RIVA TNT2       (NV05)
[  4455.834]     GeForce 256     (NV10)
[  4455.834]     GeForce 2       (NV11, NV15)
[  4455.834]     GeForce 4MX     (NV17, NV18)
[  4455.834]     GeForce 3       (NV20)
[  4455.834]     GeForce 4Ti     (NV25, NV28)
[  4455.834]     GeForce FX      (NV3x)
[  4455.834]     GeForce 6       (NV4x)
[  4455.834]     GeForce 7       (G7x)
[  4455.834]     GeForce 8       (G8x)
[  4455.834]     GeForce GTX 200 (NVA0)
[  4455.834]     GeForce GTX 400 (NVC0)
[  4455.834] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  4455.834] (II) FBDEV: driver for framebuffer: fbdev
[  4455.834] (II) VESA: driver for VESA chipsets: vesa
[  4455.954] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -19
[  4455.954] (WW) Falling back to old probe method for modesetting
[  4455.954] (II) Loading sub module "fbdevhw"
[  4455.954] (II) LoadModule: "fbdevhw"
[  4455.954] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  4455.954] (II) Module fbdevhw: vendor="X.Org Foundation"
[  4455.954]     compiled for 1.19.6, module version = 0.0.2
[  4455.954]     ABI class: X.Org Video Driver, version 23.0
[  4455.954] (EE) open /dev/fb0: No such file or directory
[  4455.954] (WW) Falling back to old probe method for fbdev
[  4455.954] (II) Loading sub module "fbdevhw"
[  4455.954] (II) LoadModule: "fbdevhw"
[  4455.954] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  4455.954] (II) Module fbdevhw: vendor="X.Org Foundation"
[  4455.954]     compiled for 1.19.6, module version = 0.0.2
[  4455.954]     ABI class: X.Org Video Driver, version 23.0
[  4455.954] (EE) open /dev/fb0: No such file or directory
[  4455.955] vesa: Ignoring device with a bound kernel driver
[  4455.955] (WW) Falling back to old probe method for vesa
[  4455.955] (EE) Screen 0 deleted because of no matching config section.
[  4455.955] (II) UnloadModule: "modesetting"
[  4455.955] (EE) Screen 0 deleted because of no matching config section.
[  4455.955] (II) UnloadModule: "fbdev"
[  4455.955] (II) UnloadSubModule: "fbdevhw"
[  4455.955] (EE) Screen 0 deleted because of no matching config section.
[  4455.955] (II) UnloadModule: "vesa"
[  4455.955] (EE) Device(s) detected, but none match those in the config file.
[  4455.955] (==) Matched nouveau as autoconfigured driver 0
[  4455.955] (==) Matched modesetting as autoconfigured driver 1
[  4455.955] (==) Matched fbdev as autoconfigured driver 2
[  4455.955] (==) Matched vesa as autoconfigured driver 3
[  4455.955] (==) Assigned the driver to the xf86ConfigLayout
[  4455.955] (II) LoadModule: "nouveau"
[  4455.955] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  4455.955] (II) Module nouveau: vendor="X.Org Foundation"
[  4455.955]     compiled for 1.19.3, module version = 1.0.15
[  4455.955]     Module class: X.Org Video Driver
[  4455.955]     ABI class: X.Org Video Driver, version 23.0
[  4455.955] (II) UnloadModule: "nouveau"
[  4455.955] (II) Unloading nouveau
[  4455.955] (II) Failed to load module "nouveau" (already loaded, 22006)
[  4455.955] (II) LoadModule: "modesetting"
[  4455.955] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  4455.955] (II) Module modesetting: vendor="X.Org Foundation"
[  4455.955]     compiled for 1.19.6, module version = 1.19.6
[  4455.955]     Module class: X.Org Video Driver
[  4455.955]     ABI class: X.Org Video Driver, version 23.0
[  4455.955] (II) UnloadModule: "modesetting"
[  4455.955] (II) Unloading modesetting
[  4455.955] (II) Failed to load module "modesetting" (already loaded, 22006)
[  4455.955] (II) LoadModule: "fbdev"
[  4455.956] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  4455.956] (II) Module fbdev: vendor="X.Org Foundation"
[  4455.956]     compiled for 1.19.3, module version = 0.4.4
[  4455.956]     Module class: X.Org Video Driver
[  4455.956]     ABI class: X.Org Video Driver, version 23.0
[  4455.956] (II) UnloadModule: "fbdev"
[  4455.956] (II) Unloading fbdev
[  4455.956] (II) Failed to load module "fbdev" (already loaded, 22006)
[  4455.956] (II) LoadModule: "vesa"
[  4455.956] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  4455.956] (II) Module vesa: vendor="X.Org Foundation"
[  4455.956]     compiled for 1.19.3, module version = 2.3.4
[  4455.956]     Module class: X.Org Video Driver
[  4455.956]     ABI class: X.Org Video Driver, version 23.0
[  4455.956] (II) UnloadModule: "vesa"
[  4455.956] (II) Unloading vesa
[  4455.956] (II) Failed to load module "vesa" (already loaded, 22006)
[  4455.956] (II) NOUVEAU driver Date:   Fri Apr 21 14:41:17 2017 -0400
[  4455.956] (II) NOUVEAU driver for NVIDIA chipset families :
[  4455.956]     RIVA TNT        (NV04)
[  4455.956]     RIVA TNT2       (NV05)
[  4455.956]     GeForce 256     (NV10)
[  4455.956]     GeForce 2       (NV11, NV15)
[  4455.956]     GeForce 4MX     (NV17, NV18)
[  4455.956]     GeForce 3       (NV20)
[  4455.956]     GeForce 4Ti     (NV25, NV28)
[  4455.956]     GeForce FX      (NV3x)
[  4455.956]     GeForce 6       (NV4x)
[  4455.956]     GeForce 7       (G7x)
[  4455.957]     GeForce 8       (G8x)
[  4455.957]     GeForce GTX 200 (NVA0)
[  4455.957]     GeForce GTX 400 (NVC0)
[  4455.957] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  4455.957] (II) FBDEV: driver for framebuffer: fbdev
[  4455.957] (II) VESA: driver for VESA chipsets: vesa
[  4455.957] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[  4455.957] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[  4456.078] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -19
[  4456.078] (WW) Falling back to old probe method for modesetting
[  4456.078] (II) Loading sub module "fbdevhw"
[  4456.078] (II) LoadModule: "fbdevhw"
[  4456.078] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  4456.078] (II) Module fbdevhw: vendor="X.Org Foundation"
[  4456.078]     compiled for 1.19.6, module version = 0.0.2
[  4456.078]     ABI class: X.Org Video Driver, version 23.0
[  4456.078] (EE) open /dev/fb0: No such file or directory
[  4456.078] (WW) Falling back to old probe method for fbdev
[  4456.078] (II) Loading sub module "fbdevhw"
[  4456.078] (II) LoadModule: "fbdevhw"
[  4456.078] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  4456.078] (II) Module fbdevhw: vendor="X.Org Foundation"
[  4456.078]     compiled for 1.19.6, module version = 0.0.2
[  4456.079]     ABI class: X.Org Video Driver, version 23.0
[  4456.079] (EE) open /dev/fb0: No such file or directory
[  4456.079] vesa: Ignoring device with a bound kernel driver
[  4456.079] (WW) Falling back to old probe method for vesa
[  4456.079] (EE) Screen 0 deleted because of no matching config section.
[  4456.079] (II) UnloadModule: "modesetting"
[  4456.079] (EE) Screen 0 deleted because of no matching config section.
[  4456.079] (II) UnloadModule: "fbdev"
[  4456.079] (II) UnloadSubModule: "fbdevhw"
[  4456.079] (II) UnloadSubModule: "fbdevhw"
[  4456.079] (II) UnloadSubModule: "fbdevhw"
[  4456.079] (EE) Screen 0 deleted because of no matching config section.
[  4456.079] (II) UnloadModule: "vesa"
[  4456.079] (EE) Device(s) detected, but none match those in the config file.
[  4456.079] (EE) 
Fatal server error:
[  4456.079] (EE) no screens found(EE) 
[  4456.079] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[  4456.079] (EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[  4456.079] (EE) 
[  4456.080] (EE) Server terminated with error (1). Closing log file.
```

---

### Post by Yellow Pasque on 2020-07-02
```
[   4455.830] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-4.15.0-20-generic  root=UUID=43fff14c-8de1-4f07-b37e-333ff7d96675 ro quiet splash
[  4455.830] Build Date: 13 April 2018  08:07:36PM
```

You are booting into an ancient kernel version. I'm not sure how you managed to do that, unless this output is from a LiveUSB. 4.15.0-**109** is the lastest version in the 4.15.x series.

You should use Synaptic to search for "linux-" packages, sort them by installed version, and get rid of all but the latest two.

---

### Post by Yellow Pasque on 2020-07-02
> /var/log/Xorg.1.log

Are you sure you gave us the right log? Does Xorg.0.log look different?

---

### Post by pqwoerituytrueiwoq on 2020-07-03
i assumed Xorg.1.log was last boot, clearly that appears to be from May 2018
now the log file i needed to check has been purged...

When i woke it this morning it acted like it was not in sleep mode and just booted there was no power outage or crash report and i turned it on via WOL
This is from syslog today: [https://paste.ubuntu.com/p/VBVw9nWwRf/](https://paste.ubuntu.com/p/VBVw9nWwRf/)

---

### Post by Yellow Pasque on 2020-07-03
You may want to try running without openrazer daemon and see if that helps: [https://ubuntuforums.org/showthread.php?t=2445875](https://ubuntuforums.org/showthread.php?t=2445875)

---

### Post by pqwoerituytrueiwoq on 2020-07-03
The crash in sleep mode happened again with  openrazer daemon not running
edit: now i got the other type of crash, lets try purging openrazor, luckily the mouse seems to store it's own config
I've been through every log file, the problem is not being recorded during the wake process

---

### Post by pqwoerituytrueiwoq on 2020-07-12
I think figured it out if you force the ram speed on RX 580 to it's lowest power state (300Mhz @ 0.75V) it has a high chance of crashing when waking from sleep mode, forcing the core and mem clocks to the lowest speeds greatly cuts power and thermals and it is plenty fast for video playback/web browsing

---

