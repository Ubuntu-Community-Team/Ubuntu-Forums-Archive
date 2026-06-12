---
title: "Bumblebee Screwed Up Unity. Can't Even do a Reinstall to Get it Back"
date: 2013-08-06
forum: General Help
---

### Post by jart16 on 2013-08-06
I have a MacBook Pro 6,2 with both Intel integrated graphics and Nvidia 330M. I was trying to get my external monitor to work in order to extend my display, but the proprietary drivers just gave me a black screen. I then looked into solutions for hybrid graphics. Not knowing if it was right for my computer, I took the risk and installed Bumblebee. It messed up everything, even after I did a purge. Now I just get text-only mode, where it asks for my login/password and then just goes into shell mode. Typing startx at the prompt produces an error, as well as typing "unity"

Here is my Xorg.0.log:
```
[    12.674] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    12.674] X Protocol Version 11, Revision 0
[    12.674] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    12.674] Current Operating System: Linux Jart-MacBookPro 3.8.0-27-generic #40-Ubuntu SMP Tue Jul 9 00:17:05 UTC 2013 x86_64
[    12.674] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-27-generic root=UUID=7854a770-a291-47ca-ba3d-10a1d6ac2d8f ro nomodeset
[    12.674] Build Date: 17 April 2013  10:43:13PM
[    12.674] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    12.674] Current version of pixman: 0.28.2
[    12.674] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    12.674] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.674] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug  6 10:49:45 2013
[    12.727] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.727] (==) No Layout section.  Using the first Screen section.
[    12.727] (==) No screen section available. Using defaults.
[    12.727] (**) |-->Screen "Default Screen Section" (0)
[    12.727] (**) |   |-->Monitor "<default monitor>"
[    12.727] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    12.727] (==) Automatically adding devices
[    12.727] (==) Automatically enabling devices
[    12.727] (==) Automatically adding GPU devices
[    12.761] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.761] 	Entry deleted from font path.
[    12.761] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    12.761] 	Entry deleted from font path.
[    12.761] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    12.761] 	Entry deleted from font path.
[    12.766] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    12.766] 	Entry deleted from font path.
[    12.766] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    12.766] 	Entry deleted from font path.
[    12.766] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    12.766] 	Entry deleted from font path.
[    12.766] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    12.766] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.766] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.766] (II) Loader magic: 0x7fd718678d20
[    12.766] (II) Module ABI versions:
[    12.766] 	X.Org ANSI C Emulation: 0.4
[    12.766] 	X.Org Video Driver: 13.1
[    12.766] 	X.Org XInput driver : 18.0
[    12.766] 	X.Org Server Extension : 7.0
[    12.766] (II) config/udev: Adding drm device (/dev/dri/card0)
[    12.768] (--) PCI: (0:0:2:0) 8086:0046:0000:0000 rev 18, Mem @ 0xc1400000/4194304, 0xb0000000/268435456, I/O @ 0x00003130/8
[    12.768] (--) PCI:*(0:1:0:0) 10de:0a29:106b:00c7 rev 162, Mem @ 0xc0000000/16777216, 0x90000000/268435456, 0xa0000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288
[    12.768] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.768] Initializing built-in extension Generic Event Extension
[    12.768] Initializing built-in extension SHAPE
[    12.768] Initializing built-in extension MIT-SHM
[    12.768] Initializing built-in extension XInputExtension
[    12.768] Initializing built-in extension XTEST
[    12.768] Initializing built-in extension BIG-REQUESTS
[    12.768] Initializing built-in extension SYNC
[    12.768] Initializing built-in extension XKEYBOARD
[    12.768] Initializing built-in extension XC-MISC
[    12.768] Initializing built-in extension SECURITY
[    12.768] Initializing built-in extension XINERAMA
[    12.768] Initializing built-in extension XFIXES
[    12.768] Initializing built-in extension RENDER
[    12.768] Initializing built-in extension RANDR
[    12.768] Initializing built-in extension COMPOSITE
[    12.768] Initializing built-in extension DAMAGE
[    12.768] Initializing built-in extension MIT-SCREEN-SAVER
[    12.768] Initializing built-in extension DOUBLE-BUFFER
[    12.768] Initializing built-in extension RECORD
[    12.768] Initializing built-in extension DPMS
[    12.768] Initializing built-in extension X-Resource
[    12.768] Initializing built-in extension XVideo
[    12.768] Initializing built-in extension XVideo-MotionCompensation
[    12.768] Initializing built-in extension SELinux
[    12.768] Initializing built-in extension XFree86-VidModeExtension
[    12.768] Initializing built-in extension XFree86-DGA
[    12.768] Initializing built-in extension XFree86-DRI
[    12.768] Initializing built-in extension DRI2
[    12.768] (II) LoadModule: "glx"
[    12.851] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    12.851] (II) Module glx: vendor="X.Org Foundation"
[    12.851] 	compiled for 1.13.3, module version = 1.0.0
[    12.851] 	ABI class: X.Org Server Extension, version 7.0
[    12.851] (==) AIGLX enabled
[    12.851] Loading extension GLX
[    12.851] (==) Matched intel as autoconfigured driver 0
[    12.851] (==) Matched nvidia as autoconfigured driver 1
[    12.851] (==) Matched nouveau as autoconfigured driver 2
[    12.851] (==) Matched vesa as autoconfigured driver 3
[    12.851] (==) Matched modesetting as autoconfigured driver 4
[    12.851] (==) Matched fbdev as autoconfigured driver 5
[    12.851] (==) Assigned the driver to the xf86ConfigLayout
[    12.851] (II) LoadModule: "intel"
[    12.851] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    12.862] (II) Module intel: vendor="X.Org Foundation"
[    12.862] 	compiled for 1.13.3, module version = 2.21.6
[    12.862] 	Module class: X.Org Video Driver
[    12.862] 	ABI class: X.Org Video Driver, version 13.1
[    12.862] (II) LoadModule: "nvidia"
[    12.864] (WW) Warning, couldn't open module nvidia
[    12.864] (II) UnloadModule: "nvidia"
[    12.864] (II) Unloading nvidia
[    12.864] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    12.864] (II) LoadModule: "nouveau"
[    12.864] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    12.875] (II) Module nouveau: vendor="X.Org Foundation"
[    12.875] 	compiled for 1.13.3, module version = 1.0.7
[    12.875] 	Module class: X.Org Video Driver
[    12.875] 	ABI class: X.Org Video Driver, version 13.1
[    12.875] (II) LoadModule: "vesa"
[    12.875] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.875] (II) Module vesa: vendor="X.Org Foundation"
[    12.875] 	compiled for 1.12.99.902, module version = 2.3.2
[    12.875] 	Module class: X.Org Video Driver
[    12.875] 	ABI class: X.Org Video Driver, version 13.0
[    12.875] (II) LoadModule: "modesetting"
[    12.876] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    12.876] (II) Module modesetting: vendor="X.Org Foundation"
[    12.876] 	compiled for 1.13.3, module version = 0.7.0
[    12.876] 	Module class: X.Org Video Driver
[    12.876] 	ABI class: X.Org Video Driver, version 13.1
[    12.876] (II) LoadModule: "fbdev"
[    12.876] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.876] (II) Module fbdev: vendor="X.Org Foundation"
[    12.876] 	compiled for 1.12.99.902, module version = 0.4.3
[    12.876] 	Module class: X.Org Video Driver
[    12.876] 	ABI class: X.Org Video Driver, version 13.0
[    12.876] (==) Matched intel as autoconfigured driver 0
[    12.876] (==) Matched nvidia as autoconfigured driver 1
[    12.876] (==) Matched nouveau as autoconfigured driver 2
[    12.876] (==) Matched vesa as autoconfigured driver 3
[    12.876] (==) Matched modesetting as autoconfigured driver 4
[    12.876] (==) Matched fbdev as autoconfigured driver 5
[    12.876] (==) Assigned the driver to the xf86ConfigLayout
[    12.876] (II) LoadModule: "intel"
[    12.876] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    12.876] (II) Module intel: vendor="X.Org Foundation"
[    12.876] 	compiled for 1.13.3, module version = 2.21.6
[    12.876] 	Module class: X.Org Video Driver
[    12.876] 	ABI class: X.Org Video Driver, version 13.1
[    12.876] (II) UnloadModule: "intel"
[    12.876] (II) Unloading intel
[    12.876] (II) Failed to load module "intel" (already loaded, 32727)
[    12.876] (II) LoadModule: "nvidia"
[    12.876] (WW) Warning, couldn't open module nvidia
[    12.876] (II) UnloadModule: "nvidia"
[    12.876] (II) Unloading nvidia
[    12.876] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    12.876] (II) LoadModule: "nouveau"
[    12.876] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    12.876] (II) Module nouveau: vendor="X.Org Foundation"
[    12.876] 	compiled for 1.13.3, module version = 1.0.7
[    12.876] 	Module class: X.Org Video Driver
[    12.876] 	ABI class: X.Org Video Driver, version 13.1
[    12.876] (II) UnloadModule: "nouveau"
[    12.876] (II) Unloading nouveau
[    12.876] (II) Failed to load module "nouveau" (already loaded, 0)
[    12.876] (II) LoadModule: "vesa"
[    12.877] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.877] (II) Module vesa: vendor="X.Org Foundation"
[    12.877] 	compiled for 1.12.99.902, module version = 2.3.2
[    12.877] 	Module class: X.Org Video Driver
[    12.877] 	ABI class: X.Org Video Driver, version 13.0
[    12.877] (II) UnloadModule: "vesa"
[    12.877] (II) Unloading vesa
[    12.877] (II) Failed to load module "vesa" (already loaded, 0)
[    12.877] (II) LoadModule: "modesetting"
[    12.877] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    12.877] (II) Module modesetting: vendor="X.Org Foundation"
[    12.877] 	compiled for 1.13.3, module version = 0.7.0
[    12.877] 	Module class: X.Org Video Driver
[    12.877] 	ABI class: X.Org Video Driver, version 13.1
[    12.877] (II) UnloadModule: "modesetting"
[    12.877] (II) Unloading modesetting
[    12.877] (II) Failed to load module "modesetting" (already loaded, 0)
[    12.877] (II) LoadModule: "fbdev"
[    12.877] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.877] (II) Module fbdev: vendor="X.Org Foundation"
[    12.877] 	compiled for 1.12.99.902, module version = 0.4.3
[    12.877] 	Module class: X.Org Video Driver
[    12.877] 	ABI class: X.Org Video Driver, version 13.0
[    12.877] (II) UnloadModule: "fbdev"
[    12.877] (II) Unloading fbdev
[    12.877] (II) Failed to load module "fbdev" (already loaded, 0)
[    12.877] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
	Ivybridge Server (GT2), HD Graphics, HD Graphics 4600,
	Haswell Desktop (GT3), HD Graphics, HD Graphics 4600,
	Haswell Mobile (GT3), HD Graphics, HD Graphics P4600/P4700,
	Haswell Server (GT3), Haswell (GT1), Haswell (GT2), Haswell (GT3),
	HD Graphics, Haswell (GT2), Haswell (GT3), Haswell SDV Desktop (GT1),
	Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT3),
	Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
	Haswell SDV Mobile (GT3), Haswell SDV Server (GT1),
	Haswell SDV Server (GT2), Haswell SDV Server (GT3),
	Haswell SDV (GT1), Haswell SDV (GT2), Haswell SDV (GT3),
	Haswell SDV (GT1), Haswell SDV (GT2), Haswell SDV (GT3),
	Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
	Iris(TM) Graphics 5100, HD Graphics, HD Graphics 4400,
	HD Graphics 5000, Haswell ULT Server (GT1), Haswell ULT Server (GT2),
	Iris(TM) Graphics 5100, Haswell ULT (GT1), Haswell ULT (GT2),
	Iris(TM) Graphics 5100, HD Graphics, HD Graphics 4200,
	Iris(TM) Graphics 5100, Haswell CRW Desktop (GT1), HD Graphics 4600,
	Iris(TM) Pro Graphics 5200, Haswell CRW Mobile (GT1),
	HD Graphics 4600, Iris(TM) Pro Graphics 5200,
	Haswell CRW Server (GT1), Haswell CRW Server (GT2),
	Iris(TM) Pro Graphics 5200, Haswell CRW (GT1), Haswell CRW (GT2),
	Iris(TM) Pro Graphics 5200, Haswell CRW (GT1), Haswell CRW (GT2),
	Iris(TM) Pro Graphics 5200, ValleyView PO board
[    12.877] (II) NOUVEAU driver Date:   Wed Mar 27 09:50:03 2013 +0100
[    12.877] (II) NOUVEAU driver for NVIDIA chipset families :
[    12.877] 	RIVA TNT        (NV04)
[    12.877] 	RIVA TNT2       (NV05)
[    12.877] 	GeForce 256     (NV10)
[    12.877] 	GeForce 2       (NV11, NV15)
[    12.877] 	GeForce 4MX     (NV17, NV18)
[    12.877] 	GeForce 3       (NV20)
[    12.877] 	GeForce 4Ti     (NV25, NV28)
[    12.877] 	GeForce FX      (NV3x)
[    12.877] 	GeForce 6       (NV4x)
[    12.878] 	GeForce 7       (G7x)
[    12.878] 	GeForce 8       (G8x)
[    12.878] 	GeForce GTX 200 (NVA0)
[    12.878] 	GeForce GTX 400 (NVC0)
[    12.878] (II) VESA: driver for VESA chipsets: vesa
[    12.878] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    12.878] (II) FBDEV: driver for framebuffer: fbdev
[    12.878] (++) using VT number 7

[    12.880] (EE) [drm] KMS not enabled
[    12.881] (EE) [drm] KMS not enabled
[    12.881] (II) modesetting(G0): using drv /dev/dri/card0
[    12.881] (WW) Falling back to old probe method for modesetting
[    12.881] (WW) Falling back to old probe method for fbdev
[    12.881] (II) Loading sub module "fbdevhw"
[    12.881] (II) LoadModule: "fbdevhw"
[    12.881] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    12.881] (II) Module fbdevhw: vendor="X.Org Foundation"
[    12.881] 	compiled for 1.13.3, module version = 0.0.2
[    12.881] 	ABI class: X.Org Video Driver, version 13.1
[    12.881] (II) Loading sub module "vbe"
[    12.881] (II) LoadModule: "vbe"
[    12.881] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    12.881] (II) Module vbe: vendor="X.Org Foundation"
[    12.881] 	compiled for 1.13.3, module version = 1.1.0
[    12.881] 	ABI class: X.Org Video Driver, version 13.1
[    12.881] (II) Loading sub module "int10"
[    12.881] (II) LoadModule: "int10"
[    12.881] (II) Loading /usr/lib/xorg/modules/libint10.so
[    12.881] (II) Module int10: vendor="X.Org Foundation"
[    12.881] 	compiled for 1.13.3, module version = 1.0.0
[    12.881] 	ABI class: X.Org Video Driver, version 13.1
[    12.881] (II) VESA(0): initializing int10
[    12.882] (EE) VESA(0): V_BIOS address 0xd00 out of range
[    12.882] (II) UnloadModule: "vesa"
[    12.882] (II) UnloadSubModule: "int10"
[    12.882] (II) Unloading int10
[    12.882] (II) UnloadSubModule: "vbe"
[    12.882] (II) Unloading vbe
[    12.882] (EE) modesetting(G0): Specified fbbpp (728721696) is not a permitted value
[    12.882] (II) UnloadModule: "modesetting"
[    12.882] (EE) Screen(s) found, but none have a usable configuration.
[    12.882] 
Fatal server error:
[    12.882] no screens found
[    12.882] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    12.882] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    12.882] (EE) 
[    12.885] Server terminated with error (1). Closing log file.
```

The live CD works fine. This used to work fine before I installed Bumblebee. I even tried doing a fresh install, and it still gave me these results. So far I have tried:

 - Forcing nouveau drivers by creating a folder and following directions at the end of [this.]("http://nouveau.freedesktop.org/wiki/InstallNouveau/")
 - Using an older kernel from GRUB

---

