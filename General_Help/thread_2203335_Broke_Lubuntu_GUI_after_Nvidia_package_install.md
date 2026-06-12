---
title: "Broke Lubuntu GUI after Nvidia package install"
date: 2014-02-02
forum: General Help
---

### Post by twaelbroeck on 2014-02-02
Hello all,

As the title states, my Lubuntu 13.10 install isn't working quite right currently. I installed everything just fine and was just getting comfortable with my setup. A few of the games I play were having graphics issues, so I was trying to fix that and in turn, broke everything. 

When I boot, after I choose Lubuntu, all I get is a flashing horizontal cursor in the top left of my screen. I can switch to terminal mode via Ctrl + Alt + F1 and work from there, but that's it. This began after I installed a package from the command line (I want to say it was nvidia-331 perhaps?). After rebooting, I uninstalled that package and rebooted again to be greeted with the same sad situation. I tried installing nvidia-current which hasn't changed anything. I also tried installing gnome-shell to see if it was a problem with the lubuntu desktop, but it did not change anything.

Any suggestions would be gladly welcome.

Specs:

Lenovo W510
Nvidia 880M 
i7 Q720
4GB RAM

---

### Post by Ubi_one_2014 on 2014-02-02
what happend when you run, as NORMAL user:
startx

from terminal?

---

### Post by twaelbroeck on 2014-02-02
After running startx as non-sudo, it gives this output file (/var/log/Xorg.0.log):

```
[    36.934] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[    36.934] X Protocol Version 11, Revision 0
[    36.934] Build Operating System: Linux 3.2.0-54-generic i686 Ubuntu
[    36.934] Current Operating System: Linux travis-ThinkPad-W510 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:25:07 UTC 2014 i686
[    36.934] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=8ed96024-9c7a-4467-8b50-c91e13077dc7 ro quiet splash
[    36.934] Build Date: 17 December 2013  10:03:52AM
[    36.935] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see http://www.ubuntu.com/support) 
[    36.935] Current version of pixman: 0.30.2
[    36.935]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    36.935] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    36.936] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb  2 23:20:41 2014
[    36.936] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    36.936] (==) No Layout section.  Using the first Screen section.
[    36.936] (==) No screen section available. Using defaults.
[    36.936] (**) |-->Screen "Default Screen Section" (0)
[    36.936] (**) |   |-->Monitor "<default monitor>"
[    36.937] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    36.937] (==) Automatically adding devices
[    36.937] (==) Automatically enabling devices
[    36.937] (==) Automatically adding GPU devices
[    36.937] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    36.937]     Entry deleted from font path.
[    36.937] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    36.937]     Entry deleted from font path.
[    36.937] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    36.937]     Entry deleted from font path.
[    36.937] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    36.937]     Entry deleted from font path.
[    36.937] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    36.937]     Entry deleted from font path.
[    36.937] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    36.937]     Entry deleted from font path.
[    36.937] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    built-ins
[    36.937] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    36.937] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    36.937] (II) Loader magic: 0xb77a06a0
[    36.937] (II) Module ABI versions:
[    36.937]     X.Org ANSI C Emulation: 0.4
[    36.937]     X.Org Video Driver: 14.1
[    36.937]     X.Org XInput driver : 19.1
[    36.937]     X.Org Server Extension : 7.0
[    36.939] (--) PCI:*(0:1:0:0) 10de:0a3c:17aa:2145 rev 162, Mem @ 0xcc000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288
[    36.939] (II) Open ACPI successful (/var/run/acpid.socket)
[    36.939] Initializing built-in extension Generic Event Extension
[    36.939] Initializing built-in extension SHAPE
[    36.939] Initializing built-in extension MIT-SHM
[    36.940] Initializing built-in extension XInputExtension
[    36.940] Initializing built-in extension XTEST
[    36.940] Initializing built-in extension BIG-REQUESTS
[    36.940] Initializing built-in extension SYNC
[    36.940] Initializing built-in extension XKEYBOARD
[    36.940] Initializing built-in extension XC-MISC
[    36.940] Initializing built-in extension SECURITY
[    36.940] Initializing built-in extension XINERAMA
[    36.941] Initializing built-in extension XFIXES
[    36.941] Initializing built-in extension RENDER
[    36.941] Initializing built-in extension RANDR
[    36.941] Initializing built-in extension COMPOSITE
[    36.941] Initializing built-in extension DAMAGE
[    36.941] Initializing built-in extension MIT-SCREEN-SAVER
[    36.941] Initializing built-in extension DOUBLE-BUFFER
[    36.941] Initializing built-in extension RECORD
[    36.942] Initializing built-in extension DPMS
[    36.942] Initializing built-in extension X-Resource
[    36.942] Initializing built-in extension XVideo
[    36.942] Initializing built-in extension XVideo-MotionCompensation
[    36.942] Initializing built-in extension SELinux
[    36.942] Initializing built-in extension XFree86-VidModeExtension
[    36.942] Initializing built-in extension XFree86-DGA
[    36.942] Initializing built-in extension XFree86-DRI
[    36.942] Initializing built-in extension DRI2
[    36.942] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    36.942] (II) "glx" will be loaded by default.
[    36.942] (WW) "xmir" is not to be loaded by default. Skipping.
[    36.943] (II) LoadModule: "glx"
[    36.943] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    36.960] (II) Module glx: vendor="NVIDIA Corporation"
[    36.960]     compiled for 4.0.2, module version = 1.0.0
[    36.960]     Module class: X.Org Server Extension
[    36.960] (II) NVIDIA GLX Module  304.117  Tue Nov 26 21:56:56 PST 2013
[    36.960] Loading extension GLX
[    36.960] (==) Matched nvidia as autoconfigured driver 0
[    36.960] (==) Matched nouveau as autoconfigured driver 1
[    36.960] (==) Matched vesa as autoconfigured driver 2
[    36.960] (==) Matched modesetting as autoconfigured driver 3
[    36.960] (==) Matched fbdev as autoconfigured driver 4
[    36.960] (==) Assigned the driver to the xf86ConfigLayout
[    36.960] (II) LoadModule: "nvidia"
[    36.960] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    36.961] (II) Module nvidia: vendor="NVIDIA Corporation"
[    36.961]     compiled for 4.0.2, module version = 1.0.0
[    36.961]     Module class: X.Org Video Driver
[    36.963] (II) LoadModule: "nouveau"
[    36.963] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    36.963] (II) Module nouveau: vendor="X.Org Foundation"
[    36.963]     compiled for 1.14.2, module version = 1.0.9
[    36.963]     Module class: X.Org Video Driver
[    36.963]     ABI class: X.Org Video Driver, version 14.1
[    36.963] (II) LoadModule: "vesa"
[    36.963] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    36.963] (II) Module vesa: vendor="X.Org Foundation"
[    36.963]     compiled for 1.14.1, module version = 2.3.2
[    36.963]     Module class: X.Org Video Driver
[    36.963]     ABI class: X.Org Video Driver, version 14.1
[    36.964] (II) LoadModule: "modesetting"
[    36.964] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    36.964] (II) Module modesetting: vendor="X.Org Foundation"
[    36.964]     compiled for 1.14.1, module version = 0.8.0
[    36.964]     Module class: X.Org Video Driver
[    36.964]     ABI class: X.Org Video Driver, version 14.1
[    36.964] (II) LoadModule: "fbdev"
[    36.964] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    36.964] (II) Module fbdev: vendor="X.Org Foundation"
[    36.964]     compiled for 1.14.1, module version = 0.4.3
[    36.964]     Module class: X.Org Video Driver
[    36.964]     ABI class: X.Org Video Driver, version 14.1
[    36.964] (II) NVIDIA dlloader X Driver  304.117  Tue Nov 26 21:38:08 PST 2013
[    36.964] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    36.964] (II) NOUVEAU driver 
[    36.964] (II) NOUVEAU driver for NVIDIA chipset families :
[    36.964]     RIVA TNT        (NV04)
[    36.964]     RIVA TNT2       (NV05)
[    36.964]     GeForce 256     (NV10)
[    36.964]     GeForce 2       (NV11, NV15)
[    36.964]     GeForce 4MX     (NV17, NV18)
[    36.964]     GeForce 3       (NV20)
[    36.964]     GeForce 4Ti     (NV25, NV28)
[    36.964]     GeForce FX      (NV3x)
[    36.964]     GeForce 6       (NV4x)
[    36.964]     GeForce 7       (G7x)
[    36.964]     GeForce 8       (G8x)
[    36.964]     GeForce GTX 200 (NVA0)
[    36.964]     GeForce GTX 400 (NVC0)
[    36.964] (II) VESA: driver for VESA chipsets: vesa
[    36.964] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    36.964] (II) FBDEV: driver for framebuffer: fbdev
[    36.964] (--) using VT number 7

[    36.969] (II) Loading sub module "fb"
[    36.969] (II) LoadModule: "fb"
[    36.970] (II) Loading /usr/lib/xorg/modules/libfb.so
[    36.970] (II) Module fb: vendor="X.Org Foundation"
[    36.970]     compiled for 1.14.5, module version = 1.0.0
[    36.970]     ABI class: X.Org ANSI C Emulation, version 0.4
[    36.970] (II) Loading sub module "wfb"
[    36.970] (II) LoadModule: "wfb"
[    36.970] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    36.970] (II) Module wfb: vendor="X.Org Foundation"
[    36.970]     compiled for 1.14.5, module version = 1.0.0
[    36.970]     ABI class: X.Org ANSI C Emulation, version 0.4
[    36.970] (II) Loading sub module "ramdac"
[    36.970] (II) LoadModule: "ramdac"
[    36.970] (II) Module "ramdac" already built-in
[    36.970] (WW) Falling back to old probe method for vesa
[    36.970] (WW) Falling back to old probe method for modesetting
[    36.970] (EE) open /dev/dri/card0: No such file or directory
[    36.970] (WW) Falling back to old probe method for fbdev
[    36.970] (II) Loading sub module "fbdevhw"
[    36.970] (II) LoadModule: "fbdevhw"
[    36.970] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    36.970] (II) Module fbdevhw: vendor="X.Org Foundation"
[    36.970]     compiled for 1.14.5, module version = 0.0.2
[    36.970]     ABI class: X.Org Video Driver, version 14.1
[    36.970] (EE) open /dev/fb0: No such file or directory
[    36.970] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    36.970] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    36.970] (==) NVIDIA(0): RGB weight 888
[    36.970] (==) NVIDIA(0): Default visual is TrueColor
[    36.970] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    36.971] (**) NVIDIA(0): Enabling 2D acceleration
[    36.974] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[    36.974] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[    36.974] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[    36.974] (EE) NVIDIA(0):  *** Aborting ***
[    36.974] (EE) NVIDIA(0): Failing initialization of X screen 0
[    36.974] (II) UnloadModule: "nvidia"
[    36.974] (II) UnloadSubModule: "wfb"
[    36.974] (II) UnloadSubModule: "fb"
[    36.974] (EE) Screen(s) found, but none have a usable configuration.
[    36.974] (EE) 
Fatal server error:
[    36.974] (EE) no screens found(EE) 
[    36.974] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    36.975] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    36.975] (EE) 
[    36.978] (EE) Server terminated with error (1). Closing log file.


```

---

### Post by twaelbroeck on 2014-02-03
Thanks to [NikTh]("http://askubuntu.com/users/95393/nikth") for forwarding me to [this page]("http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely/206289#206289") that helped me figure out a way to get (mostly) back up and running!

Short version was: 
```

dpkg -l | grep -i nvidia
sudo apt-get remove --purge nvidia-*
sudo apt-get install lubuntu-desktop
```

Thanks for your help, Ubi_one-2014 :)

---

