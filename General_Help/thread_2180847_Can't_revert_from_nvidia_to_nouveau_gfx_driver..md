---
title: "Can't revert from nvidia to nouveau gfx driver."
date: 2013-10-14
forum: General Help
---

### Post by stinkeye on 2013-10-14
Raring 64bit..... Nvidia GeForce GTX 550 Ti
I used to be able to do this simply by selecting nouveau in additional drivers and restarting.
I do not have an  **/etc/X11/xorg.conf** file.
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **cat /etc/X11/xorg.conf**
cat: /etc/X11/xorg.conf: No such file or directory
```

...and I don't believe the nouveau driver is blacklisted from this command which returns no results...
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] cat /etc/modprobe.d/* | egrep 'blacklist nouveau'
```

The [**_[COLOR="#B22222"]nouveau wiki[/COLOR]_**]("http://nouveau.freedesktop.org/wiki/UbuntuPackages/") says to create this minimal **/etc/X11/xorg.conf** file if you encounter any problems.
```
Section "Device"
Identifier "n"
Driver "nouveau"
EndSection
```


I tried this but still loads the Mesa driver...
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **/usr/lib/nux/unity_support_test -p**
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.2, 128 bits)
OpenGL version string:  2.1 Mesa 9.1.4
```


Start of **xorg.0.log** with nouveau drivers enabled but loads mesa...
```
[    24.610] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    24.610] X Protocol Version 11, Revision 0
[    24.610] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    24.610] Current Operating System: Linux Raring 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 20:03:44 UTC 2013 x86_64
[    24.610] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=b3f8e203-03ff-4df2-a45f-0af8be25735b ro quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap vt.handoff=7
[    24.610] Build Date: 17 April 2013  10:43:13PM
[    24.610] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    24.610] Current version of pixman: 0.28.2
[    24.610] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    24.610] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.610] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 15 10:35:23 2013
[    24.640] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.640] (==) No Layout section.  Using the first Screen section.
[    24.640] (==) No screen section available. Using defaults.
[    24.640] (**) |-->Screen "Default Screen Section" (0)
[    24.640] (**) |   |-->Monitor "<default monitor>"
[    24.641] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    24.641] (==) Automatically adding devices
[    24.641] (==) Automatically enabling devices
[    24.641] (==) Automatically adding GPU devices
[    24.641] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.641] 	Entry deleted from font path.
[    24.641] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.641] 	Entry deleted from font path.
[    24.641] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.641] 	Entry deleted from font path.
[    24.641] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.641] 	Entry deleted from font path.
[    24.641] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.641] 	Entry deleted from font path.
[    24.641] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    24.641] 	Entry deleted from font path.
[    24.641] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    24.641] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.641] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.641] (II) Loader magic: 0x7f949f96fd20
[    24.641] (II) Module ABI versions:
[    24.641] 	X.Org ANSI C Emulation: 0.4
[    24.641] 	X.Org Video Driver: 13.1
[    24.641] 	X.Org XInput driver : 18.0
[    24.641] 	X.Org Server Extension : 7.0
[    24.642] (--) PCI:*(0:1:0:0) 10de:1244:1458:351a rev 161, Mem @ 0xf8000000/33554432, 0xc8000000/134217728, 0xd4000000/67108864, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
[    24.642] (II) Open ACPI successful (/var/run/acpid.socket)
[    24.642] Initializing built-in extension Generic Event Extension
[    24.642] Initializing built-in extension SHAPE
[    24.642] Initializing built-in extension MIT-SHM
[    24.642] Initializing built-in extension XInputExtension
[    24.642] Initializing built-in extension XTEST
[    24.642] Initializing built-in extension BIG-REQUESTS
[    24.642] Initializing built-in extension SYNC
[    24.642] Initializing built-in extension XKEYBOARD
[    24.642] Initializing built-in extension XC-MISC
[    24.642] Initializing built-in extension SECURITY
[    24.642] Initializing built-in extension XINERAMA
[    24.642] Initializing built-in extension XFIXES
[    24.642] Initializing built-in extension RENDER
[    24.642] Initializing built-in extension RANDR
[    24.642] Initializing built-in extension COMPOSITE
[    24.642] Initializing built-in extension DAMAGE
[    24.642] Initializing built-in extension MIT-SCREEN-SAVER
[    24.642] Initializing built-in extension DOUBLE-BUFFER
[    24.642] Initializing built-in extension RECORD
[    24.642] Initializing built-in extension DPMS
[    24.642] Initializing built-in extension X-Resource
[    24.642] Initializing built-in extension XVideo
[    24.642] Initializing built-in extension XVideo-MotionCompensation
[    24.642] Initializing built-in extension SELinux
[    24.642] Initializing built-in extension XFree86-VidModeExtension
[    24.642] Initializing built-in extension XFree86-DGA
[    24.642] Initializing built-in extension XFree86-DRI
[    24.642] Initializing built-in extension DRI2
[    24.642] (II) LoadModule: "glx"
[    24.657] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    24.657] (II) Module glx: vendor="X.Org Foundation"
[    24.657] 	compiled for 1.13.3, module version = 1.0.0
[    24.657] 	ABI class: X.Org Server Extension, version 7.0
[    24.657] (==) AIGLX enabled
[    24.657] Loading extension GLX
[    24.657] (==) Matched nvidia as autoconfigured driver 0
[    24.657] (==) Matched nouveau as autoconfigured driver 1
[    24.657] (==) Matched vesa as autoconfigured driver 2
[    24.657] (==) Matched modesetting as autoconfigured driver 3
[    24.657] (==) Matched fbdev as autoconfigured driver 4
[    24.657] (==) Assigned the driver to the xf86ConfigLayout
[    24.657] (II) LoadModule: "nvidia"
[    24.658] (WW) Warning, couldn't open module nvidia
[    24.658] (II) UnloadModule: "nvidia"
[    24.658] (II) Unloading nvidia
[    24.658] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    24.658] (II) LoadModule: "nouveau"
[    24.658] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    24.665] (II) Module nouveau: vendor="X.Org Foundation"
[    24.665] 	compiled for 1.13.3, module version = 1.0.7
[    24.665] 	Module class: X.Org Video Driver
[    24.665] 	ABI class: X.Org Video Driver, version 13.1
[    24.665] (II) LoadModule: "vesa"
[    24.665] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.665] (II) Module vesa: vendor="X.Org Foundation"
[    24.665] 	compiled for 1.12.99.902, module version = 2.3.2
[    24.665] 	Module class: X.Org Video Driver
[    24.665] 	ABI class: X.Org Video Driver, version 13.0
[    24.665] (II) LoadModule: "modesetting"
[    24.665] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    24.665] (II) Module modesetting: vendor="X.Org Foundation"
[    24.665] 	compiled for 1.13.3, module version = 0.7.0
[    24.665] 	Module class: X.Org Video Driver
[    24.665] 	ABI class: X.Org Video Driver, version 13.1
[    24.665] (II) LoadModule: "fbdev"
[    24.665] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.665] (II) Module fbdev: vendor="X.Org Foundation"
[    24.665] 	compiled for 1.12.99.902, module version = 0.4.3
[    24.665] 	Module class: X.Org Video Driver
[    24.665] 	ABI class: X.Org Video Driver, version 13.0
[    24.665] (==) Matched nvidia as autoconfigured driver 0
[    24.665] (==) Matched nouveau as autoconfigured driver 1
[    24.665] (==) Matched vesa as autoconfigured driver 2
[    24.665] (==) Matched modesetting as autoconfigured driver 3
[    24.665] (==) Matched fbdev as autoconfigured driver 4
[    24.665] (==) Assigned the driver to the xf86ConfigLayout
[    24.665] (II) LoadModule: "nvidia"
[    24.666] (WW) Warning, couldn't open module nvidia
[    24.666] (II) UnloadModule: "nvidia"
[    24.666] (II) Unloading nvidia
[    24.666] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    24.666] (II) LoadModule: "nouveau"
[    24.666] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    24.666] (II) Module nouveau: vendor="X.Org Foundation"
[    24.666] 	compiled for 1.13.3, module version = 1.0.7
[    24.666] 	Module class: X.Org Video Driver
[    24.666] 	ABI class: X.Org Video Driver, version 13.1
[    24.666] (II) UnloadModule: "nouveau"
[    24.666] (II) Unloading nouveau
[    24.666] (II) Failed to load module "nouveau" (already loaded, 0)
[    24.666] (II) LoadModule: "vesa"
[    24.666] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.666] (II) Module vesa: vendor="X.Org Foundation"
[    24.666] 	compiled for 1.12.99.902, module version = 2.3.2
[    24.666] 	Module class: X.Org Video Driver
[    24.666] 	ABI class: X.Org Video Driver, version 13.0
[    24.666] (II) UnloadModule: "vesa"
[    24.666] (II) Unloading vesa
[    24.666] (II) Failed to load module "vesa" (already loaded, 0)
[    24.666] (II) LoadModule: "modesetting"
[    24.666] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    24.666] (II) Module modesetting: vendor="X.Org Foundation"
[    24.666] 	compiled for 1.13.3, module version = 0.7.0
[    24.666] 	Module class: X.Org Video Driver
[    24.666] 	ABI class: X.Org Video Driver, version 13.1
[    24.666] (II) UnloadModule: "modesetting"
[    24.666] (II) Unloading modesetting
[    24.666] (II) Failed to load module "modesetting" (already loaded, 0)
[    24.666] (II) LoadModule: "fbdev"
[    24.666] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.666] (II) Module fbdev: vendor="X.Org Foundation"
[    24.666] 	compiled for 1.12.99.902, module version = 0.4.3
[    24.666] 	Module class: X.Org Video Driver
[    24.666] 	ABI class: X.Org Video Driver, version 13.0
[    24.666] (II) UnloadModule: "fbdev"
[    24.666] (II) Unloading fbdev
[    24.666] (II) Failed to load module "fbdev" (already loaded, 0)
[    24.666] (II) NOUVEAU driver Date:   Wed Mar 27 09:50:03 2013 +0100
[    24.666] (II) NOUVEAU driver for NVIDIA chipset families :
[    24.666] 	RIVA TNT        (NV04)
[    24.666] 	RIVA TNT2       (NV05)
[    24.666] 	GeForce 256     (NV10)
[    24.666] 	GeForce 2       (NV11, NV15)
[    24.666] 	GeForce 4MX     (NV17, NV18)
[    24.666] 	GeForce 3       (NV20)
[    24.666] 	GeForce 4Ti     (NV25, NV28)
[    24.666] 	GeForce FX      (NV3x)
[    24.666] 	GeForce 6       (NV4x)
[    24.666] 	GeForce 7       (G7x)
[    24.666] 	GeForce 8       (G8x)
[    24.666] 	GeForce GTX 200 (NVA0)
[    24.666] 	GeForce GTX 400 (NVC0)
[    24.666] (II) VESA: driver for VESA chipsets: vesa
[    24.666] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    24.666] (II) FBDEV: driver for framebuffer: fbdev
[    24.666] (++) using VT number 7

[    24.666] (EE) [drm] KMS not enabled
[    24.666] (EE) [drm] KMS not enabled
[    24.666] (WW) Falling back to old probe method for modesetting
[    24.666] (EE) open /dev/dri/card0: No such file or directory
[    24.666] (EE) open /dev/dri/card0: No such file or directory
[    24.666] (WW) Falling back to old probe method for fbdev
[    24.666] (II) Loading sub module "fbdevhw"
[    24.666] (II) LoadModule: "fbdevhw"
[    24.667] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.667] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.667] 	compiled for 1.13.3, module version = 0.0.2
[    24.667] 	ABI class: X.Org Video Driver, version 13.1
[    24.667] (II) Loading sub module "vbe"
[    24.667] (II) LoadModule: "vbe"
[    24.667] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    24.667] (II) Module vbe: vendor="X.Org Foundation"
[    24.667] 	compiled for 1.13.3, module version = 1.1.0
[    24.667] 	ABI class: X.Org Video Driver, version 13.1
[    24.667] (II) Loading sub module "int10"
[    24.667] (II) LoadModule: "int10"
[    24.667] (II) Loading /usr/lib/xorg/modules/libint10.so
[    24.667] (II) Module int10: vendor="X.Org Foundation"
[    24.667] 	compiled for 1.13.3, module version = 1.0.0
[    24.667] 	ABI class: X.Org Video Driver, version 13.1
[    24.667] (II) VESA(0): initializing int10
[    24.669] (II) VESA(0): Bad V_BIOS checksum
[    24.669] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    24.720] (II) VESA(0): VESA BIOS detected
[    24.720] (II) VESA(0): VESA VBE Version 3.0
[    24.720] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    24.720] (II) VESA(0): VESA VBE OEM: NVIDIA
[    24.720] (II) VESA(0): VESA VBE OEM Software Rev: 112.38
[    24.720] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    24.720] (II) VESA(0): VESA VBE OEM Product: GF106B Board - 10500000
[    24.720] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    24.815] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    24.815] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    24.815] (==) VESA(0): RGB weight 888
[    24.815] (==) VESA(0): Default visual is TrueColor
[    24.815] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    24.815] (II) Loading sub module "ddc"
[    24.815] (II) LoadModule: "ddc"
[    24.815] (II) Module "ddc" already built-in
[    24.816] (II) VESA(0): VESA VBE DDC supported
[    24.816] (II) VESA(0): VESA VBE DDC Level 2
[    24.816] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    24.852] (II) VESA(0): VESA VBE DDC read successfully
[    24.852] (II) VESA(0): Manufacturer: SAM  Model: 37c  Serial#: 1095840306
[    24.852] (II) VESA(0): Year: 2008  Week: 8
[    24.852] (II) VESA(0): EDID Version: 1.3
[    24.852] (II) VESA(0): Digital Display Input
[    24.852] (II) VESA(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    24.852] (II) VESA(0): Gamma: 2.20
[    24.852] (II) VESA(0): DPMS capabilities: Off
```


Start of **xorg.0.log** with nvidia drivers enabled and loads correctly...
```
[    23.231] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    23.231] X Protocol Version 11, Revision 0
[    23.231] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    23.231] Current Operating System: Linux Raring 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 20:03:44 UTC 2013 x86_64
[    23.231] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=b3f8e203-03ff-4df2-a45f-0af8be25735b ro quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
[    23.231] Build Date: 17 April 2013  10:43:13PM
[    23.231] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    23.231] Current version of pixman: 0.28.2
[    23.231] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    23.231] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.231] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 15 12:03:08 2013
[    23.296] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.296] (==) No Layout section.  Using the first Screen section.
[    23.296] (==) No screen section available. Using defaults.
[    23.296] (**) |-->Screen "Default Screen Section" (0)
[    23.296] (**) |   |-->Monitor "<default monitor>"
[    23.296] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    23.296] (==) Automatically adding devices
[    23.296] (==) Automatically enabling devices
[    23.296] (==) Automatically adding GPU devices
[    23.296] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.296] 	Entry deleted from font path.
[    23.296] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    23.296] 	Entry deleted from font path.
[    23.296] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    23.296] 	Entry deleted from font path.
[    23.296] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    23.296] 	Entry deleted from font path.
[    23.296] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    23.296] 	Entry deleted from font path.
[    23.296] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    23.296] 	Entry deleted from font path.
[    23.296] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    23.296] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.296] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.296] (II) Loader magic: 0x7fabc75c0d20
[    23.296] (II) Module ABI versions:
[    23.296] 	X.Org ANSI C Emulation: 0.4
[    23.296] 	X.Org Video Driver: 13.1
[    23.296] 	X.Org XInput driver : 18.0
[    23.296] 	X.Org Server Extension : 7.0
[    23.297] (--) PCI:*(0:1:0:0) 10de:1244:1458:351a rev 161, Mem @ 0xf8000000/33554432, 0xc8000000/134217728, 0xd4000000/67108864, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
[    23.297] (II) Open ACPI successful (/var/run/acpid.socket)
[    23.297] Initializing built-in extension Generic Event Extension
[    23.297] Initializing built-in extension SHAPE
[    23.297] Initializing built-in extension MIT-SHM
[    23.297] Initializing built-in extension XInputExtension
[    23.297] Initializing built-in extension XTEST
[    23.297] Initializing built-in extension BIG-REQUESTS
[    23.297] Initializing built-in extension SYNC
[    23.297] Initializing built-in extension XKEYBOARD
[    23.297] Initializing built-in extension XC-MISC
[    23.297] Initializing built-in extension SECURITY
[    23.297] Initializing built-in extension XINERAMA
[    23.297] Initializing built-in extension XFIXES
[    23.297] Initializing built-in extension RENDER
[    23.297] Initializing built-in extension RANDR
[    23.297] Initializing built-in extension COMPOSITE
[    23.297] Initializing built-in extension DAMAGE
[    23.297] Initializing built-in extension MIT-SCREEN-SAVER
[    23.297] Initializing built-in extension DOUBLE-BUFFER
[    23.297] Initializing built-in extension RECORD
[    23.297] Initializing built-in extension DPMS
[    23.297] Initializing built-in extension X-Resource
[    23.297] Initializing built-in extension XVideo
[    23.297] Initializing built-in extension XVideo-MotionCompensation
[    23.297] Initializing built-in extension SELinux
[    23.297] Initializing built-in extension XFree86-VidModeExtension
[    23.297] Initializing built-in extension XFree86-DGA
[    23.297] Initializing built-in extension XFree86-DRI
[    23.297] Initializing built-in extension DRI2
[    23.297] (II) LoadModule: "glx"
[    23.297] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    24.338] (II) Module glx: vendor="NVIDIA Corporation"
[    24.338] 	compiled for 4.0.2, module version = 1.0.0
[    24.338] 	Module class: X.Org Server Extension
[    24.338] (II) NVIDIA GLX Module  313.30  Wed Mar 27 15:51:21 PDT 2013
[    24.347] Loading extension GLX
[    24.348] (==) Matched nvidia as autoconfigured driver 0
[    24.348] (==) Matched nouveau as autoconfigured driver 1
[    24.348] (==) Matched vesa as autoconfigured driver 2
[    24.348] (==) Matched modesetting as autoconfigured driver 3
[    24.348] (==) Matched fbdev as autoconfigured driver 4
[    24.348] (==) Assigned the driver to the xf86ConfigLayout
[    24.348] (II) LoadModule: "nvidia"
[    24.348] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    24.453] (II) Module nvidia: vendor="NVIDIA Corporation"
[    24.453] 	compiled for 4.0.2, module version = 1.0.0
[    24.453] 	Module class: X.Org Video Driver
[    24.464] (II) LoadModule: "nouveau"
[    24.464] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    24.489] (II) Module nouveau: vendor="X.Org Foundation"
[    24.489] 	compiled for 1.13.3, module version = 1.0.7
[    24.489] 	Module class: X.Org Video Driver
[    24.489] 	ABI class: X.Org Video Driver, version 13.1
[    24.489] (II) LoadModule: "vesa"
[    24.490] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.490] (II) Module vesa: vendor="X.Org Foundation"
[    24.490] 	compiled for 1.12.99.902, module version = 2.3.2
[    24.490] 	Module class: X.Org Video Driver
[    24.490] 	ABI class: X.Org Video Driver, version 13.0
[    24.490] (II) LoadModule: "modesetting"
[    24.490] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    24.490] (II) Module modesetting: vendor="X.Org Foundation"
[    24.490] 	compiled for 1.13.3, module version = 0.7.0
[    24.490] 	Module class: X.Org Video Driver
[    24.490] 	ABI class: X.Org Video Driver, version 13.1
[    24.490] (II) LoadModule: "fbdev"
[    24.490] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.490] (II) Module fbdev: vendor="X.Org Foundation"
[    24.490] 	compiled for 1.12.99.902, module version = 0.4.3
[    24.490] 	Module class: X.Org Video Driver
[    24.490] 	ABI class: X.Org Video Driver, version 13.0
[    24.490] (II) NVIDIA dlloader X Driver  313.30  Wed Mar 27 15:33:21 PDT 2013
[    24.490] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    24.491] (II) NOUVEAU driver Date:   Wed Mar 27 09:50:03 2013 +0100
[    24.491] (II) NOUVEAU driver for NVIDIA chipset families :
[    24.491] 	RIVA TNT        (NV04)
[    24.491] 	RIVA TNT2       (NV05)
[    24.491] 	GeForce 256     (NV10)
[    24.491] 	GeForce 2       (NV11, NV15)
[    24.491] 	GeForce 4MX     (NV17, NV18)
[    24.491] 	GeForce 3       (NV20)
[    24.491] 	GeForce 4Ti     (NV25, NV28)
[    24.491] 	GeForce FX      (NV3x)
[    24.491] 	GeForce 6       (NV4x)
[    24.491] 	GeForce 7       (G7x)
[    24.491] 	GeForce 8       (G8x)
[    24.491] 	GeForce GTX 200 (NVA0)
[    24.491] 	GeForce GTX 400 (NVC0)
[    24.491] (II) VESA: driver for VESA chipsets: vesa
[    24.491] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    24.491] (II) FBDEV: driver for framebuffer: fbdev
[    24.491] (++) using VT number 7

[    24.492] (II) Loading sub module "wfb"
[    24.492] (II) LoadModule: "wfb"
[    24.492] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    24.522] (II) Module wfb: vendor="X.Org Foundation"
[    24.522] 	compiled for 1.13.3, module version = 1.0.0
[    24.522] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    24.522] (II) Loading sub module "ramdac"
[    24.522] (II) LoadModule: "ramdac"
[    24.522] (II) Module "ramdac" already built-in
[    24.536] (WW) Falling back to old probe method for vesa
[    24.536] (WW) Falling back to old probe method for modesetting
[    24.536] (EE) open /dev/dri/card0: No such file or directory
[    24.536] (WW) Falling back to old probe method for fbdev
[    24.536] (II) Loading sub module "fbdevhw"
[    24.536] (II) LoadModule: "fbdevhw"
[    24.536] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.536] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.536] 	compiled for 1.13.3, module version = 0.0.2
[    24.536] 	ABI class: X.Org Video Driver, version 13.1
[    24.536] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    24.536] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    24.537] (==) NVIDIA(0): RGB weight 888
[    24.537] (==) NVIDIA(0): Default visual is TrueColor
[    24.537] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    24.538] (**) NVIDIA(0): Enabling 2D acceleration
[    26.797] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[    26.797] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    26.798] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 550 Ti (GF116) at PCI:1:0:0 (GPU-0)
[    26.798] (--) NVIDIA(0): Memory: 1048576 kBytes
[    26.798] (--) NVIDIA(0): VideoBIOS: 70.26.18.00.02
```

I can switch back to nvidia no problem by reselecting in additional drivers and restarting.
Ideas???

---

### Post by stinkeye on 2013-10-15
Also tried this...
```
sudo apt-get remove --purge nvidia*
sudo apt-get remove --purge xserver-xorg-video-nouveau
sudo apt-get install nvidia-common
sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:__Need_to_fully_remove_-nvidia_and_reinstall_-nouveau_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:__Need_to_fully_remove_-nvidia_and_reinstall_-nouveau_from_scratch)

Still no nouveau.

---

### Post by Willynux on 2014-07-27
I just had a similar problem on 14.04 and couldn't login the graphical interface anymore once nvidia driver is installed. Solved it by removing completely all nvidia package (dpkg -l | grep nvidia => this shows you the nvidia packages installed)

 On the frozen login window, log into a terminal with Ctrl+Alt+F6, then log in with username and password and type:

> sudo apt-get purge nvidia*

Then restart:

> sudo shutdown -r now

You should be back to Nouveau (by default) and the graphical interface.

Hope that helps other people searching for nvidia related problems.

---

