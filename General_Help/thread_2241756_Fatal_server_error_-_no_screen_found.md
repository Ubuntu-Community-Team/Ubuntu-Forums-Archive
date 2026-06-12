---
title: "Fatal server error - no screen found"
date: 2014-08-28
forum: General Help
---

### Post by 2CV67 on 2014-08-28
Hi!
I am just setting up Ubuntu 14.04.1 on a new Acer Aspire TC-100-007 desktop.

Yesterday, things were going OK & I had Thunderbird, Firefox, Picasa in wine, LibreOffice etc running well.
The most recent changes I made were to reset the Grub timeout to 3 seconds & to install "Drawers" in the Launcher - I don't think those items are significant.

This morning - disaster!
When I login to my account, I just have the wallpaper, nothing else...
I have the mouse pointer & can right-click to change that wallpaper, but not much else.
I managed to shut down with REISUB & booted to Windows 8.1 OK.

I tried Ubuntu recovery mode with no success except finding a message about "Fatal server error - no screen found" & a suggestion to check /var/log/Xorg.failsafe.log.

I rebooted to Ubuntu & tried logging in to other accounts, which all work OK!

I found the Xorg.failsafe.log file which I attach below, but which doesn't tell me much.

I did try my own login again after the success with the others, but it was NG - just wallpaper.
I could get to a terminal with Ctr/Alt/F1.

I would appreciate any suggestions to troubleshoot & fix this problem!

Thanks!

Xorg log:```

[   119.616] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[   119.620] X Protocol Version 11, Revision 0
[   119.621] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[   119.623] Current Operating System: Linux Aspire-TC 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64
[   119.623] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-34-generic.efi.signed root=UUID=b92778eb-50df-4b24-b6c1-4c177cf89507 ro recovery nomodeset
[   119.628] Build Date: 16 April 2014  01:36:29PM
[   119.629] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[   119.631] Current version of pixman: 0.30.2
[   119.634] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   119.634] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   119.640] (++) Log file: "/var/log/Xorg.failsafe.log", Time: Thu Aug 28 10:19:00 2014
[   119.642] (++) Using config file: "/etc/X11/xorg.conf.failsafe"
[   119.644] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   119.645] (==) No Layout section.  Using the first Screen section.
[   119.645] (**) |-->Screen "Default Screen" (0)
[   119.645] (**) |   |-->Monitor "Configured Monitor"
[   119.645] (**) |   |-->Device "Configured Video Device"
[   119.645] (==) Automatically adding devices
[   119.645] (==) Automatically enabling devices
[   119.645] (==) Automatically adding GPU devices
[   119.646] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   119.646] 	Entry deleted from font path.
[   119.646] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   119.646] 	Entry deleted from font path.
[   119.646] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   119.646] 	Entry deleted from font path.
[   119.646] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   119.646] 	Entry deleted from font path.
[   119.646] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   119.646] 	Entry deleted from font path.
[   119.646] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   119.646] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   119.646] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   119.646] (II) Loader magic: 0x7f12c3c0fd60
[   119.646] (II) Module ABI versions:
[   119.646] 	X.Org ANSI C Emulation: 0.4
[   119.646] 	X.Org Video Driver: 15.0
[   119.646] 	X.Org XInput driver : 20.0
[   119.646] 	X.Org Server Extension : 8.0
[   119.646] (II) xfree86: Adding drm device (/dev/dri/card0)
[   119.649] (--) PCI:*(0:0:1:0) 1002:9832:1025:0800 rev 0, Mem @ 0xc0000000/268435456, 0xd0000000/8388608, 0xfeb00000/262144, I/O @ 0x0000f000/256, BIOS @ 0x????????/131072
[   119.650] Initializing built-in extension Generic Event Extension
[   119.652] Initializing built-in extension SHAPE
[   119.654] Initializing built-in extension MIT-SHM
[   119.656] Initializing built-in extension XInputExtension
[   119.657] Initializing built-in extension XTEST
[   119.659] Initializing built-in extension BIG-REQUESTS
[   119.661] Initializing built-in extension SYNC
[   119.662] Initializing built-in extension XKEYBOARD
[   119.664] Initializing built-in extension XC-MISC
[   119.666] Initializing built-in extension SECURITY
[   119.668] Initializing built-in extension XINERAMA
[   119.669] Initializing built-in extension XFIXES
[   119.671] Initializing built-in extension RENDER
[   119.672] Initializing built-in extension RANDR
[   119.674] Initializing built-in extension COMPOSITE
[   119.675] Initializing built-in extension DAMAGE
[   119.676] Initializing built-in extension MIT-SCREEN-SAVER
[   119.678] Initializing built-in extension DOUBLE-BUFFER
[   119.679] Initializing built-in extension RECORD
[   119.680] Initializing built-in extension DPMS
[   119.682] Initializing built-in extension Present
[   119.683] Initializing built-in extension DRI3
[   119.684] Initializing built-in extension X-Resource
[   119.685] Initializing built-in extension XVideo
[   119.686] Initializing built-in extension XVideo-MotionCompensation
[   119.687] Initializing built-in extension SELinux
[   119.688] Initializing built-in extension XFree86-VidModeExtension
[   119.689] Initializing built-in extension XFree86-DGA
[   119.690] Initializing built-in extension XFree86-DRI
[   119.691] Initializing built-in extension DRI2
[   119.691] (II) LoadModule: "glx"
[   119.692] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   119.694] (II) Module glx: vendor="X.Org Foundation"
[   119.694] 	compiled for 1.15.1, module version = 1.0.0
[   119.694] 	ABI class: X.Org Server Extension, version 8.0
[   119.694] (==) AIGLX enabled
[   119.695] Loading extension GLX
[   119.695] (II) LoadModule: "vesa"
[   119.695] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   119.695] (II) Module vesa: vendor="X.Org Foundation"
[   119.695] 	compiled for 1.15.0, module version = 2.3.3
[   119.695] 	Module class: X.Org Video Driver
[   119.696] 	ABI class: X.Org Video Driver, version 15.0
[   119.696] (II) VESA: driver for VESA chipsets: vesa
[   119.696] (--) using VT number 2

[   119.699] (II) Loading sub module "vbe"
[   119.699] (II) LoadModule: "vbe"
[   119.700] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   119.700] (II) Module vbe: vendor="X.Org Foundation"
[   119.700] 	compiled for 1.15.1, module version = 1.1.0
[   119.700] 	ABI class: X.Org Video Driver, version 15.0
[   119.700] (II) Loading sub module "int10"
[   119.700] (II) LoadModule: "int10"
[   119.701] (II) Loading /usr/lib/xorg/modules/libint10.so
[   119.701] (II) Module int10: vendor="X.Org Foundation"
[   119.701] 	compiled for 1.15.1, module version = 1.0.0
[   119.701] 	ABI class: X.Org Video Driver, version 15.0
[   119.701] (II) VESA(0): initializing int10
[   119.701] (EE) VESA(0): V_BIOS address 0xd00 out of range
[   119.702] (II) UnloadModule: "vesa"
[   119.702] (II) UnloadSubModule: "int10"
[   119.702] (II) Unloading int10
[   119.702] (II) UnloadSubModule: "vbe"
[   119.702] (II) Unloading vbe
[   119.702] (EE) Screen(s) found, but none have a usable configuration.
[   119.702] (EE) 
Fatal server error:
[   119.702] (EE) no screens found(EE) 
[   119.702] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   119.702] (EE) Please also check the log file at "/var/log/Xorg.failsafe.log" for additional information.
[   119.702] (EE) 
[   119.709] (EE) Server terminated with error (1). Closing log file.
```

---

### Post by 2CV67 on 2014-08-28
Removing the file  *me/.config/dconf/user* fixed it, after lots of other attempts...

Don't ask me why, or how we got there in the first place.

---

