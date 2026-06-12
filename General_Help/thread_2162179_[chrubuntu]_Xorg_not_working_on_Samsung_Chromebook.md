---
title: "[chrubuntu] Xorg not working on Samsung Chromebook XE303C12"
date: 2013-07-13
forum: General Help
---

### Post by mofoburrell on 2013-07-13
I followed the instructions [here]("http://chromeos-cr48.blogspot.ca/2013/05/chrubuntu-one-script-to-rule-them-all_31.html") to install xubuntu-desktop 13.04 on my Chromebook Series 3. Everything seemed to install alright and I can log in from the console alright and everything. Xorg fails to start, though.

Has anyone had any problems getting Xorg running on a Series 3?

Here's the output of X -configure:


X.Org X Server 1.13.3
Release Date: 2013-03-07 
X Protocol Version 11, Revision 0 
Build Operating System: Linux 3.2.0-1426-omap4 armv7l Ubuntu 
Current Operating System: Linux chrubuntu 3.4.0 #1 SMP Fri Jun 14 15:09:54 PDT 2013 armv7l 
Kernel command line: cros_secure console= console=tty1 debug verbose root=/dev/mmcblk0p7 rootwait rw lsm.module_locking=0  
Build Date: 17 April 2013  10:48:48PM 
xorg-server 2:1.13.3-0ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))  
Current version of pixman: 0.28.2 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) 
	to make sure that you have the latest version. 
Markers: (--) probed, (**) from config file, (==) default setting, 
	(++) from command line, (!!) notice, (II) informational, 
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown. 
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 13 14:29:33 2013 
List of video drivers: 
	omap 
	modesetting 
	r128 
	radeon 
	mach64 
	nouveau 
	ati 
	fbdev 
	vesa 
No devices to configure.  Configuration failed. 
Server terminated with error (2). Closing log file.

---

### Post by mofoburrell on 2013-07-13
Here's /var/log/Xorg.0.log:

```


[     7.875]  X.Org X Server 1.13.3 Release Date: 2013-03-07 
[     7.875] X Protocol Version 11, Revision 0 
[     7.875] Build Operating System: Linux 3.2.0-1426-omap4 armv7l Ubuntu 
[     7.875] Current Operating System: Linux chrubuntu 3.4.0 #1 SMP Fri Jun 14 15:09:54 PDT 2013 armv7l 
[     7.875] Kernel command line: cros_secure console= console=tty1 debug verbose root=/dev/mmcblk0p7 rootwait rw lsm.module_locking=0  
[     7.875] Build Date: 17 April 2013  10:48:48PM 
[     7.875] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))  
[     7.875] Current version of pixman: 0.28.2 
[     7.875] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) 	to make sure that you have the latest version. 
[     7.875] Markers: (--) probed, (**) from config file, (==) default setting, 	(++) from command line, (!!) notice, (II) informational, 	(WW) warning, (EE) error, (NI) not implemented, (??) unknown. 
[     7.876] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 13 04:05:00 2013 
[     7.884] (==) Using system config directory "/usr/share/X11/xorg.conf.d" 
[     7.891] (==) No Layout section.  Using the first Screen section. 
[     7.891] (==) No screen section available. Using defaults. 
[     7.891] (**) |-->Screen "Default Screen Section" (0) 
[     7.891] (**) |   |-->Monitor "<default monitor>" 
[     7.891] (==) No monitor specified for screen "Default Screen Section". 	Using a default monitor configuration. 
[     7.891] (==) Automatically adding devices 
[     7.891] (==) Automatically enabling devices 
[     7.891] (==) Automatically adding GPU devices 
[     7.895] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist. 
[     7.895] 	Entry deleted from font path. 
[     7.895] (WW) The directory "[I]/usr/share/fonts/X11/100dpi/" does not exist. 
[     7.895] 	Entry deleted from font path. 
[     7.895] (WW) The directory "[I]/usr/share/fonts/X11/75dpi/" does not exist. 
[     7.895] 	Entry deleted from font path. 
[     7.898] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist. 
[     7.898] 	Entry deleted from font path. 
[     7.898] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist. 
[     7.898] 	Entry deleted from font path. 
[     7.898] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist. 
[     7.898] 	Entry deleted from font path. 
[     7.898] (==) FontPath set to: 
	/usr/share/fonts/X11/misc, 
	/usr/share/fonts/X11/Type1, 
	built-ins 
[     7.898] (==) ModulePath set to "/usr/lib/arm-linux-gnueabihf/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules" 
[     7.898] (II) The server relies on udev to provide the list of input devices. 
	If no devices become available, reconfigure udev or disable AutoAddDevices. 
[     7.898] (II) Loader magic: 0x76ff8ed8 
[     7.898] (II) Module ABI versions: 
[     7.898] 	X.Org ANSI C Emulation: 0.4 
[     7.898] 	X.Org Video Driver: 13.1 
[     7.898] 	X.Org XInput driver : 18.0 
[     7.898] 	X.Org Server Extension : 7.0 
[     7.899] (II) config/udev: Adding drm device (/dev/dri/card0) 
[     7.899] Initializing built-in extension Generic Event Extension 
[     7.899] Initializing built-in extension SHAPE 
[     7.899] Initializing built-in extension MIT-SHM 
[     7.899] Initializing built-in extension XInputExtension 
[     7.899] Initializing built-in extension XTEST 
[     7.899] Initializing built-in extension BIG-REQUESTS 
[     7.900] Initializing built-in extension SYNC 
[     7.900] Initializing built-in extension XKEYBOARD 
[     7.900] Initializing built-in extension XC-MISC 
[     7.900] Initializing built-in extension SECURITY 
[     7.900] Initializing built-in extension XINERAMA 
[     7.900] Initializing built-in extension XFIXES 
[     7.900] Initializing built-in extension RENDER 
[     7.900] Initializing built-in extension RANDR 
[     7.900] Initializing built-in extension COMPOSITE 
[     7.900] Initializing built-in extension DAMAGE 
[     7.900] Initializing built-in extension MIT-SCREEN-SAVER 
[     7.900] Initializing built-in extension DOUBLE-BUFFER 
[     7.900] Initializing built-in extension RECORD 
[     7.900] Initializing built-in extension DPMS 
[     7.900] Initializing built-in extension X-Resource 
[     7.900] Initializing built-in extension XVideo 
[     7.900] Initializing built-in extension XVideo-MotionCompensation 
[     7.900] Initializing built-in extension SELinux 
[     7.900] Initializing built-in extension XFree86-VidModeExtension 
[     7.900] Initializing built-in extension XFree86-DGA 
[     7.900] Initializing built-in extension XFree86-DRI 
[     7.900] Initializing built-in extension DRI2 
[     7.900] (II) LoadModule: "glx" 
[     7.905] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so 
[     7.910] (II) Module glx: vendor="X.Org Foundation" 
[     7.910] 	compiled for 1.13.3, module version = 1.0.0 
[     7.910] 	ABI class: X.Org Server Extension, version 7.0 
[     7.910] (==) AIGLX enabled 
[     7.910] Loading extension GLX 
[     7.911] (==) Matched modesetting as autoconfigured driver 0 
[     7.911] (==) Matched fbdev as autoconfigured driver 1 
[     7.911] (==) Assigned the driver to the xf86ConfigLayout 
[     7.911] (II) LoadModule: "modesetting" 
[     7.912] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so 
[     7.913] (II) Module modesetting: vendor="X.Org Foundation" 
[     7.913] 	compiled for 1.13.3, module version = 0.7.0 
[     7.913] 	Module class: X.Org Video Driver 
[     7.913] 	ABI class: X.Org Video Driver, version 13.1 
[     7.913] (II) LoadModule: "fbdev" 
[     7.914] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so

[     7.915] (II) Module fbdev: vendor="X.Org Foundation" 
[     7.915] 	compiled for 1.12.99.902, module version = 0.4.3 
[     7.915] 	Module class: X.Org Video Driver 
[     7.915] 	ABI class: X.Org Video Driver, version 13.0 
[     7.915] (II) modesetting: Driver for Modesetting Kernel Drivers: kms 
[     7.915] (II) FBDEV: driver for framebuffer: fbdev 
[     7.915] (++) using VT number 7 
[     7.916] (II) modesetting(0): using drv /dev/dri/card0 
[     7.916] (WW) Falling back to old probe method for fbdev 
[     7.916] (II) Loading sub module "fbdevhw" 
[     7.916] (II) LoadModule: "fbdevhw" 
[     7.916] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so 
[     7.917] (II) Module fbdevhw: vendor="X.Org Foundation" 
[     7.917] 	compiled for 1.13.3, module version = 0.0.2 
[     7.917] 	ABI class: X.Org Video Driver, version 13.1 
[     7.917] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support 
[     7.917] (II) modesetting(0): Creating default Display subsection in Screen section 
	"Default Screen Section" for depth/fbbpp 24/24 
[     7.917] (==) modesetting(0): Depth 24, (==) framebuffer bpp 24 
[     7.917] (==) modesetting(0): RGB weight 888 
[     7.917] (==) modesetting(0): Default visual is TrueColor 
[     7.917] (II) modesetting(0): ShadowFB: preferred NO, enabled NO 
[     7.917] (II) modesetting(0): Output eDP-0 has no monitor section 
[     7.918] (II) modesetting(0): Output HDMI-0 has no monitor section 
[     7.918] (II) modesetting(0): EDID for output eDP-0 
[     7.918] (II) modesetting(0): Printing probed modes for output eDP-0 
[     7.918] (II) modesetting(0): Modeline "1366x768"x59.9   70.50  1366 1406 1438 1478  768 780 786 796 (47.7 kHz eP) 
[     7.918] (II) modesetting(0): EDID for output HDMI-0 
[     7.918] (II) modesetting(0): Output eDP-0 connected 
[     7.918] (II) modesetting(0): Output HDMI-0 disconnected 
[     7.918] (II) modesetting(0): Using exact sizes for initial modes 
[     7.918] (II) modesetting(0): Output eDP-0 using initial mode 1366x768 
[     7.918] (II) modesetting(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated. 
[     7.918] (==) modesetting(0): DPI set to (96, 96) 
[     7.918] (II) Loading sub module "fb" 
[     7.918] (II) LoadModule: "fb" 
[     7.922] (II) Loading /usr/lib/xorg/modules/libfb.so 
[     7.924] (II) Module fb: vendor="X.Org Foundation" 
[     7.924] 	compiled for 1.13.3, module version = 1.0.0 
[     7.924] 	ABI class: X.Org ANSI C Emulation, version 0.4 
[     7.924] (II) UnloadModule: "fbdev" 
[     7.924] (II) Unloading fbdev 
[     7.924] (II) UnloadSubModule: "fbdevhw" 
[     7.924] (II) Unloading fbdevhw 
[     7.924] (==) Depth 24 pixmap format is 32 bpp 
[     7.924]  
Fatal server error: 
[     7.924] AddScreen/ScreenInit failed for driver 0 
[     7.924]  
[     7.925] (EE)  
Please consult the The X.Org Foundation support  
	 at [http://wiki.x.org](http://wiki.x.org) 
 for help.  
[     7.925] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information. 
[     7.925] (EE)  
[     7.933] Server terminated with error (1). Closing log file.[/I][/I] **
```

---

### Post by mofoburrell on 2013-07-13
Solved. I installed with the kpzxn script (curl -L -O [http://goo.gl/kpzxn](http://goo.gl/kpzxn)) instead of the s9ryd script and things work now.

---

