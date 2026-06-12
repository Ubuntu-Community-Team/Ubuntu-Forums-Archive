---
title: "X won't start after Nvidia update on Precise 12.04"
date: 2013-10-12
forum: General Help
---

### Post by vanessax on 2013-10-12
I couldn't find any references to this but I'm hoping someone knows how to fix this and can reply to this today.

Last night there was a batch of software updates, one was for the (proprietery) NVidia drivers.

I went ahead and told software update to update the drivers and all.

Then I noticed that it actually removed some of the drivers, leaving some symlinks dangling in /usr/bin/ which point to /etc/alternatives/.

I then clicked on the Settings and Additional Drivers, then it said "no prioprietery drivers were installed" and it listed a couple of NVidia drivers, I clicked on the "recommended" one for 319.

After it (supposedly) installed that it said to restart and I did.

Then on booting up it hangs after running some init scripts, it varies slightly each time, but no X and no VT's (virtual terminals), it just hangs. I had to use my original install disk to boot and get online again.

Hopefully someone knows how to fix this?

Is there a way to get apt to remove all the NVidia package mess and reinstall X and then reinstall the NVidial latest drivers?

Here is the log file for /var/log/Xorg.0.log:
```

[    15.132] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    15.132] X Protocol Version 11, Revision 0
[    15.132] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    15.132] Current Operating System: Linux zareason-limbo 3.5.0-42-generic #65~precise1-Ubuntu SMP Wed Oct 2 20:57:18 UTC 2013 x86_64
[    15.132] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-42-generic root=UUID=cebfb244-a57f-45e1-a3e1-05ebd0c343b5 ro quiet splash
[    15.132] Build Date: 11 April 2013  11:49:23PM
[    15.132] xorg-server 2:1.13.0-0ubuntu6.1~precise3 (For technical support please see http://www.ubuntu.com/support) 
[    15.132] Current version of pixman: 0.24.4
[    15.132]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    15.132] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.132] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 12 13:37:46 2013
[    15.156] (==) Using config file: "/etc/X11/xorg.conf"
[    15.156] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.188] (==) No Layout section.  Using the first Screen section.
[    15.188] (**) |-->Screen "Default Screen" (0)
[    15.188] (**) |   |-->Monitor "Configured Monitor"
[    15.189] (**) |   |-->Device "Configured Video Device"
[    15.189] (==) Automatically adding devices
[    15.189] (==) Automatically enabling devices
[    15.189] (==) Automatically adding GPU devices
[    15.230] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.230]     Entry deleted from font path.
[    15.230] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.230]     Entry deleted from font path.
[    15.230] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.230]     Entry deleted from font path.
[    15.230] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.230]     Entry deleted from font path.
[    15.230] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.230]     Entry deleted from font path.
[    15.230] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    15.230]     Entry deleted from font path.
[    15.230] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    15.230] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.230] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.231] (II) Loader magic: 0x7ffe59418c20
[    15.231] (II) Module ABI versions:
[    15.231]     X.Org ANSI C Emulation: 0.4
[    15.231]     X.Org Video Driver: 13.0
[    15.231]     X.Org XInput driver : 18.0
[    15.231]     X.Org Server Extension : 7.0
[    15.232] (--) PCI:*(0:2:0:0) 10de:0641:1462:1572 rev 161, Mem @ 0xfa000000/16777216, 0xc0000000/536870912, 0xf8000000/33554432, I/O @ 0x0000ac00/128, BIOS @ 0x????????/524288
[    15.232] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.233] Initializing built-in extension Generic Event Extension
[    15.233] Initializing built-in extension SHAPE
[    15.233] Initializing built-in extension MIT-SHM
[    15.233] Initializing built-in extension XInputExtension
[    15.233] Initializing built-in extension XTEST
[    15.233] Initializing built-in extension BIG-REQUESTS
[    15.233] Initializing built-in extension SYNC
[    15.233] Initializing built-in extension XKEYBOARD
[    15.233] Initializing built-in extension XC-MISC
[    15.233] Initializing built-in extension SECURITY
[    15.233] Initializing built-in extension XINERAMA
[    15.233] Initializing built-in extension XFIXES
[    15.233] Initializing built-in extension RENDER
[    15.233] Initializing built-in extension RANDR
[    15.233] Initializing built-in extension COMPOSITE
[    15.233] Initializing built-in extension DAMAGE
[    15.233] Initializing built-in extension MIT-SCREEN-SAVER
[    15.233] Initializing built-in extension DOUBLE-BUFFER
[    15.233] Initializing built-in extension RECORD
[    15.233] Initializing built-in extension DPMS
[    15.233] Initializing built-in extension X-Resource
[    15.233] Initializing built-in extension XVideo
[    15.233] Initializing built-in extension XVideo-MotionCompensation
[    15.233] Initializing built-in extension XFree86-VidModeExtension
[    15.233] Initializing built-in extension XFree86-DGA
[    15.233] Initializing built-in extension XFree86-DRI
[    15.233] Initializing built-in extension DRI2
[    15.233] (II) LoadModule: "glx"
[    15.265] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    15.918] (II) Module glx: vendor="NVIDIA Corporation"
[    15.918]     compiled for 4.0.2, module version = 1.0.0
[    15.918]     Module class: X.Org Server Extension
[    15.918] (II) NVIDIA GLX Module  319.32  Wed Jun 19 14:55:38 PDT 2013
[    15.922] Loading extension GLX
[    15.922] (II) LoadModule: "vesa"
[    15.953] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.965] (II) Module vesa: vendor="X.Org Foundation"
[    15.965]     compiled for 1.13.0, module version = 2.3.2
[    15.965]     Module class: X.Org Video Driver
[    15.965]     ABI class: X.Org Video Driver, version 13.0
[    15.965] (II) VESA: driver for VESA chipsets: vesa
[    15.965] (++) using VT number 7

[    15.966] vesa: Ignoring device with a bound kernel driver
[    15.966] (WW) Falling back to old probe method for vesa
[    15.966] (EE) Screen 0 deleted because of no matching config section.
[    15.966] (II) UnloadModule: "vesa"
[    15.966] (EE) Device(s) detected, but none match those in the config file.
[    15.966] (==) Matched nvidia as autoconfigured driver 0
[    15.966] (==) Matched nouveau as autoconfigured driver 1
[    15.966] (==) Matched nv as autoconfigured driver 2
[    15.966] (==) Matched vesa as autoconfigured driver 3
[    15.966] (==) Matched modesetting as autoconfigured driver 4
[    15.966] (==) Matched fbdev as autoconfigured driver 5
[    15.966] (==) Assigned the driver to the xf86ConfigLayout
[    15.966] (II) LoadModule: "nvidia"
[    15.966] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    16.035] (II) Module nvidia: vendor="NVIDIA Corporation"
[    16.035]     compiled for 4.0.2, module version = 1.0.0
[    16.035]     Module class: X.Org Video Driver
[    16.049] (II) LoadModule: "nouveau"
[    16.049] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    16.070] (II) Module nouveau: vendor="X.Org Foundation"
[    16.070]     compiled for 1.13.0, module version = 1.0.2
[    16.070]     Module class: X.Org Video Driver
[    16.070]     ABI class: X.Org Video Driver, version 13.0
[    16.070] (II) LoadModule: "nv"
[    16.085] (WW) Warning, couldn't open module nv
[    16.085] (II) UnloadModule: "nv"
[    16.085] (II) Unloading nv
[    16.085] (EE) Failed to load module "nv" (module does not exist, 0)
[    16.085] (II) LoadModule: "vesa"
[    16.085] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.085] (II) Module vesa: vendor="X.Org Foundation"
[    16.085]     compiled for 1.13.0, module version = 2.3.2
[    16.086]     Module class: X.Org Video Driver
[    16.086]     ABI class: X.Org Video Driver, version 13.0
[    16.086] (II) UnloadModule: "vesa"
[    16.086] (II) Unloading vesa
[    16.086] (II) Failed to load module "vesa" (already loaded, 0)
[    16.086] (II) LoadModule: "modesetting"
[    16.086] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    16.099] (II) Module modesetting: vendor="X.Org Foundation"
[    16.099]     compiled for 1.13.0, module version = 0.5.0
[    16.099]     Module class: X.Org Video Driver
[    16.099]     ABI class: X.Org Video Driver, version 13.0
[    16.099] (II) LoadModule: "fbdev"
[    16.099] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.106] (II) Module fbdev: vendor="X.Org Foundation"
[    16.106]     compiled for 1.13.0, module version = 0.4.3
[    16.106]     Module class: X.Org Video Driver
[    16.106]     ABI class: X.Org Video Driver, version 13.0
[    16.106] (II) VESA: driver for VESA chipsets: vesa
[    16.106] (II) NVIDIA dlloader X Driver  319.32  Wed Jun 19 14:34:12 PDT 2013
[    16.106] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    16.106] (II) NOUVEAU driver Date:   Wed Sep 12 13:42:43 2012 +0200
[    16.106] (II) NOUVEAU driver for NVIDIA chipset families :
[    16.106]     RIVA TNT        (NV04)
[    16.106]     RIVA TNT2       (NV05)
[    16.106]     GeForce 256     (NV10)
[    16.106]     GeForce 2       (NV11, NV15)
[    16.106]     GeForce 4MX     (NV17, NV18)
[    16.106]     GeForce 3       (NV20)
[    16.106]     GeForce 4Ti     (NV25, NV28)
[    16.106]     GeForce FX      (NV3x)
[    16.106]     GeForce 6       (NV4x)
[    16.106]     GeForce 7       (G7x)
[    16.106]     GeForce 8       (G8x)
[    16.106]     GeForce GTX 200 (NVA0)
[    16.106]     GeForce GTX 400 (NVC0)
[    16.106] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    16.106] (II) FBDEV: driver for framebuffer: fbdev
[    16.106] (++) using VT number 7

[    16.106] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    16.106] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    16.106] vesa: Ignoring device with a bound kernel driver
[    16.106] (WW) Falling back to old probe method for vesa
[    16.107] (II) Loading sub module "fb"
[    16.107] (II) LoadModule: "fb"
[    16.107] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.126] (II) Module fb: vendor="X.Org Foundation"
[    16.126]     compiled for 1.13.0, module version = 1.0.0
[    16.126]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.126] (WW) Unresolved symbol: fbGetGCPrivateKey
[    16.126] (II) Loading sub module "wfb"
[    16.126] (II) LoadModule: "wfb"
[    16.126] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    16.128] (II) Module wfb: vendor="X.Org Foundation"
[    16.128]     compiled for 1.13.0, module version = 1.0.0
[    16.128]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.128] (II) Loading sub module "shadow"
[    16.128] (II) LoadModule: "shadow"
[    16.128] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    16.133] (II) Module shadow: vendor="X.Org Foundation"
[    16.133]     compiled for 1.13.0, module version = 1.1.0
[    16.133]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.133] (II) Loading sub module "ramdac"
[    16.133] (II) LoadModule: "ramdac"
[    16.133] (II) Module "ramdac" already built-in
[    16.135] (WW) Falling back to old probe method for modesetting
[    16.135] (EE) open /dev/dri/card0: No such file or directory
[    16.135] (WW) Falling back to old probe method for fbdev
[    16.135] (II) Loading sub module "fbdevhw"
[    16.135] (II) LoadModule: "fbdevhw"
[    16.135] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.136] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.136]     compiled for 1.13.0, module version = 0.0.2
[    16.136]     ABI class: X.Org Video Driver, version 13.0
[    16.136] (EE) open /dev/fb0: No such file or directory
[    16.136] (EE) Screen 0 deleted because of no matching config section.
[    16.136] (II) UnloadModule: "vesa"
[    16.136] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    16.136] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    16.136] (==) NVIDIA(0): RGB weight 888
[    16.136] (==) NVIDIA(0): Default visual is TrueColor
[    16.136] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    16.136] (**) NVIDIA(0): Enabling 2D acceleration
[    16.157] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[    16.157] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[    16.157] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[    16.157] (EE) NVIDIA(0):  *** Aborting ***
[    16.157] (EE) NVIDIA(0): Failing initialization of X screen 0
[    16.157] (II) UnloadModule: "nvidia"
[    16.157] (II) UnloadSubModule: "shadow"
[    16.157] (II) UnloadSubModule: "wfb"
[    16.157] (II) UnloadSubModule: "fb"
[    16.157] (EE) Screen(s) found, but none have a usable configuration.
[    16.157] 
Fatal server error:
[    16.157] no screens found
[    16.157] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    16.157] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    16.157] (EE) 
[    16.169] Server terminated with error (1). Closing log file.

```

---

### Post by richardeszes on 2013-10-13
Hi,

what is in your /etc/X11/xorg.conf file?

---

### Post by vanessax on 2013-10-13
I figured it out, and it took a while, this is what I did.

Managed to reboot in recovery mode and get dpkg to work, I wanted to remove all the NVidia stuff.

I used this command to find the nvidia packages and to remove them:

dpkg -l | grep -i nvidia

Half way though I realized the 319 nvidia packages were already downloaded but not installed. The new nvidia packages were in /var/cache/apt/archives/. For whatever reason, removing the old nvidia packages and installing the new one (nvidia-319_319.32-0ubuntu0.0.1_amd64.deb) got all the dangling symlinks fixed.

I then had nvidia-xconfig again and ran that, then if automatically wrote the new xorg.conf.

I then did a hard reboot and this time X started with the nvidia drivers. So the trick was the reboot in recovery mode (hold down the SHIFT) and drop to a root terminal/prompt, then use dpkg to remove/install the new drivers that were already downloaded.

---

