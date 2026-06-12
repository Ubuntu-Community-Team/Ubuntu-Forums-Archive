---
title: "lightdm not starting on bootup put in tty1 automatically"
date: 2013-10-21
forum: General Help
---

### Post by cmptrwhz on 2013-10-21
I have kubuntu 13.04, my system just went thru the upgrade to saucy. now when I boot my computer lightdm doesn't start up. I am presented in tty1 on bootup. I have tried to
```
start lightdm
```
but i get the message
```
start: job failed to start
```
Here is my lightdm logs:
**lightdm.log**
```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.8.2, UID=0 PID=1449
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Registered seat module surfaceflinger
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Seat: Starting
[+0.00s] DEBUG: Seat: Creating greeter session
[+0.00s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+0.00s] DEBUG: Seat: Creating display server of type x
[+0.00s] DEBUG: Seat: Starting local X display
[+0.01s] DEBUG: Using VT 7
[+0.01s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.01s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.01s] DEBUG: DisplayServer x-0: Launching X Server
[+0.01s] DEBUG: Launching process 1455: /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.01s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.11s] DEBUG: Process 1455 terminated with signal 6
[+0.11s] DEBUG: DisplayServer x-0: X server stopped
[+0.11s] DEBUG: Releasing VT 7
[+0.11s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+0.11s] DEBUG: Seat: Display server stopped
[+0.11s] DEBUG: Seat: Stopping; greeter display server failed to start
[+0.11s] DEBUG: Seat: Stopping
[+0.11s] DEBUG: Seat: Stopping session
[+0.11s] DEBUG: Seat: Session stopped
[+0.11s] DEBUG: Seat: Stopped
[+0.11s] DEBUG: Required seat has stopped
[+0.11s] DEBUG: Stopping display manager
[+0.11s] DEBUG: Display manager stopped
[+0.11s] DEBUG: Stopping daemon
[+0.11s] DEBUG: Seat: Stopping session
[+0.11s] DEBUG: Releasing VT 7
[+0.11s] DEBUG: Exiting with return value 1

```
**x-0-greeter.log**
```
/usr/sbin/lightdm-kde-greeter: error while loading shared libraries: libpulsecommon-4.0.so: cannot open shared object file: No such file or directory
```

I have tried to re-install libpulse0 and that didn't do anything to fix the issue. Please assist me in getting my computer back to working. thank you.

---

### Post by enterdavertex on 2013-10-21
Try  [U][I][B]sudo apt-get install lightdm-kde-greeter
[/B][/I][/U]
Delete/Install LightDM. Look into your main config file to see if there is anything strange. 

Take a look here if you still need info [http://doc.ubuntu-fr.org/lightdm](http://doc.ubuntu-fr.org/lightdm)

---

### Post by cmptrwhz on 2013-10-21
thank you for your advice I will try that now. and let you know.

---

### Post by enterdavertex on 2013-10-21
> **cmptrwhz said:**
> thank you for your advice I will try that now. and let you know.
No problem at all, let the forum knows if it helped you out though.

---

### Post by cmptrwhz on 2013-10-21
sorry that still didn't work, I found in the Xorg.log that the screens are found but not usable? How do I fix my screens?

**Xorg.log**
```
[    11.063] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[    11.063] X Protocol Version 11, Revision 0
[    11.063] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    11.063] Current Operating System: Linux davevirtual 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 i686
[    11.063] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=be4697eb-0596-4669-9b7b-c428861042a9 ro quiet splash vt.handoff=7
[    11.063] Build Date: 15 October 2013  09:23:29AM
[    11.063] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    11.063] Current version of pixman: 0.30.2
[    11.063] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    11.063] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.063] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 21 11:28:57 2013
[    11.067] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.067] (==) No Layout section.  Using the first Screen section.
[    11.067] (==) No screen section available. Using defaults.
[    11.067] (**) |-->Screen "Default Screen Section" (0)
[    11.067] (**) |   |-->Monitor "<default monitor>"
[    11.068] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    11.068] (==) Automatically adding devices
[    11.068] (==) Automatically enabling devices
[    11.068] (==) Automatically adding GPU devices
[    11.107] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.107] 	Entry deleted from font path.
[    11.199] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
[    11.199] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.199] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    11.199] (II) Loader magic: 0xb77186a0
[    11.199] (II) Module ABI versions:
[    11.199] 	X.Org ANSI C Emulation: 0.4
[    11.199] 	X.Org Video Driver: 14.1
[    11.199] 	X.Org XInput driver : 19.1
[    11.199] 	X.Org Server Extension : 7.0
[    11.200] (II) xfree86: Adding drm device (/dev/dri/card0)
[    11.207] (--) PCI:*(0:0:2:0) 80ee:beef:0000:0000 rev 0, Mem @ 0xe0000000/134217728
[    11.207] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.207] Initializing built-in extension Generic Event Extension
[    11.207] Initializing built-in extension SHAPE
[    11.207] Initializing built-in extension MIT-SHM
[    11.207] Initializing built-in extension XInputExtension
[    11.207] Initializing built-in extension XTEST
[    11.207] Initializing built-in extension BIG-REQUESTS
[    11.207] Initializing built-in extension SYNC
[    11.207] Initializing built-in extension XKEYBOARD
[    11.207] Initializing built-in extension XC-MISC
[    11.207] Initializing built-in extension SECURITY
[    11.207] Initializing built-in extension XINERAMA
[    11.207] Initializing built-in extension XFIXES
[    11.207] Initializing built-in extension RENDER
[    11.207] Initializing built-in extension RANDR
[    11.207] Initializing built-in extension COMPOSITE
[    11.207] Initializing built-in extension DAMAGE
[    11.207] Initializing built-in extension MIT-SCREEN-SAVER
[    11.207] Initializing built-in extension DOUBLE-BUFFER
[    11.207] Initializing built-in extension RECORD
[    11.207] Initializing built-in extension DPMS
[    11.207] Initializing built-in extension X-Resource
[    11.207] Initializing built-in extension XVideo
[    11.207] Initializing built-in extension XVideo-MotionCompensation
[    11.207] Initializing built-in extension SELinux
[    11.207] Initializing built-in extension XFree86-VidModeExtension
[    11.207] Initializing built-in extension XFree86-DGA
[    11.207] Initializing built-in extension XFree86-DRI
[    11.207] Initializing built-in extension DRI2
[    11.207] (II) "glx" will be loaded by default.
[    11.207] (WW) "xmir" is not to be loaded by default. Skipping.
[    11.207] (II) LoadModule: "dri2"
[    11.207] (II) Module "dri2" already built-in
[    11.207] (II) LoadModule: "glamoregl"
[    11.258] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    11.610] (II) Module glamoregl: vendor="X.Org Foundation"
[    11.610] 	compiled for 1.14.2.901, module version = 0.5.1
[    11.610] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    11.610] (II) LoadModule: "glx"
[    11.654] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    11.654] (II) Module glx: vendor="X.Org Foundation"
[    11.654] 	compiled for 1.14.3, module version = 1.0.0
[    11.654] 	ABI class: X.Org Server Extension, version 7.0
[    11.654] (==) AIGLX enabled
[    11.654] Loading extension GLX
[    11.654] (==) Matched vboxvideo as autoconfigured driver 0
[    11.654] (==) Matched vboxvideo as autoconfigured driver 1
[    11.654] (==) Matched vesa as autoconfigured driver 2
[    11.654] (==) Matched modesetting as autoconfigured driver 3
[    11.654] (==) Matched fbdev as autoconfigured driver 4
[    11.654] (==) Assigned the driver to the xf86ConfigLayout
[    11.654] (II) LoadModule: "vboxvideo"
[    11.654] (II) Loading /usr/lib/xorg/modules/drivers/vboxvideo_drv.so
[    11.682] (II) Module vboxvideo: vendor="Oracle Corporation"
[    11.682] 	compiled for 10.13.0, module version = 1.0.1
[    11.682] 	Module class: X.Org Video Driver
[    11.682] 	ABI class: X.Org Video Driver, version 13.0
[    11.682] (EE) module ABI major version (13) doesn't match the server's version (14)
[    11.682] (II) UnloadModule: "vboxvideo"
[    11.682] (II) Unloading vboxvideo
[    11.682] (EE) Failed to load module "vboxvideo" (module requirement mismatch, 0)
[    11.682] (II) LoadModule: "vesa"
[    11.683] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.683] (II) Module vesa: vendor="X.Org Foundation"
[    11.683] 	compiled for 1.14.1, module version = 2.3.2
[    11.683] 	Module class: X.Org Video Driver
[    11.683] 	ABI class: X.Org Video Driver, version 14.1
[    11.683] (II) LoadModule: "modesetting"
[    11.683] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    11.683] (II) Module modesetting: vendor="X.Org Foundation"
[    11.683] 	compiled for 1.14.1, module version = 0.8.0
[    11.683] 	Module class: X.Org Video Driver
[    11.683] 	ABI class: X.Org Video Driver, version 14.1
[    11.683] (II) LoadModule: "fbdev"
[    11.684] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.684] (II) Module fbdev: vendor="X.Org Foundation"
[    11.684] 	compiled for 1.14.1, module version = 0.4.3
[    11.684] 	Module class: X.Org Video Driver
[    11.684] 	ABI class: X.Org Video Driver, version 14.1
[    11.684] (==) Matched vboxvideo as autoconfigured driver 0
[    11.684] (==) Matched vboxvideo as autoconfigured driver 1
[    11.684] (==) Matched vesa as autoconfigured driver 2
[    11.684] (==) Matched modesetting as autoconfigured driver 3
[    11.684] (==) Matched fbdev as autoconfigured driver 4
[    11.684] (==) Assigned the driver to the xf86ConfigLayout
[    11.684] (II) LoadModule: "vboxvideo"
[    11.684] (II) Loading /usr/lib/xorg/modules/drivers/vboxvideo_drv.so
[    11.684] (II) Module vboxvideo: vendor="Oracle Corporation"
[    11.684] 	compiled for 10.13.0, module version = 1.0.1
[    11.684] 	Module class: X.Org Video Driver
[    11.684] 	ABI class: X.Org Video Driver, version 13.0
[    11.684] (EE) module ABI major version (13) doesn't match the server's version (14)
[    11.684] (II) UnloadModule: "vboxvideo"
[    11.685] (II) Unloading vboxvideo
[    11.685] (EE) Failed to load module "vboxvideo" (module requirement mismatch, 0)
[    11.685] (II) LoadModule: "vesa"
[    11.685] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.685] (II) Module vesa: vendor="X.Org Foundation"
[    11.685] 	compiled for 1.14.1, module version = 2.3.2
[    11.685] 	Module class: X.Org Video Driver
[    11.685] 	ABI class: X.Org Video Driver, version 14.1
[    11.685] (II) UnloadModule: "vesa"
[    11.685] (II) Unloading vesa
[    11.685] (II) Failed to load module "vesa" (already loaded, 0)
[    11.685] (II) LoadModule: "modesetting"
[    11.685] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    11.685] (II) Module modesetting: vendor="X.Org Foundation"
[    11.685] 	compiled for 1.14.1, module version = 0.8.0
[    11.685] 	Module class: X.Org Video Driver
[    11.685] 	ABI class: X.Org Video Driver, version 14.1
[    11.685] (II) UnloadModule: "modesetting"
[    11.685] (II) Unloading modesetting
[    11.685] (II) Failed to load module "modesetting" (already loaded, 0)
[    11.685] (II) LoadModule: "fbdev"
[    11.685] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.685] (II) Module fbdev: vendor="X.Org Foundation"
[    11.685] 	compiled for 1.14.1, module version = 0.4.3
[    11.685] 	Module class: X.Org Video Driver
[    11.685] 	ABI class: X.Org Video Driver, version 14.1
[    11.685] (II) UnloadModule: "fbdev"
[    11.686] (II) Unloading fbdev
[    11.686] (II) Failed to load module "fbdev" (already loaded, 0)
[    11.686] (II) VESA: driver for VESA chipsets: vesa
[    11.686] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    11.686] (II) FBDEV: driver for framebuffer: fbdev
[    11.686] (++) using VT number 7

[    11.686] (WW) Falling back to old probe method for modesetting
[    11.686] (WW) Falling back to old probe method for fbdev
[    11.686] (II) Loading sub module "fbdevhw"
[    11.686] (II) LoadModule: "fbdevhw"
[    11.686] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    11.686] (II) Module fbdevhw: vendor="X.Org Foundation"
[    11.686] 	compiled for 1.14.3, module version = 0.0.2
[    11.686] 	ABI class: X.Org Video Driver, version 14.1
[    11.686] (II) Loading sub module "vbe"
[    11.686] (II) LoadModule: "vbe"
[    11.686] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    11.686] (II) Module vbe: vendor="X.Org Foundation"
[    11.686] 	compiled for 1.14.3, module version = 1.1.0
[    11.686] 	ABI class: X.Org Video Driver, version 14.1
[    11.686] (II) Loading sub module "int10"
[    11.687] (II) LoadModule: "int10"
[    11.687] (II) Loading /usr/lib/xorg/modules/libint10.so
[    11.687] (II) Module int10: vendor="X.Org Foundation"
[    11.687] 	compiled for 1.14.3, module version = 1.0.0
[    11.687] 	ABI class: X.Org Video Driver, version 14.1
[    11.687] (II) VESA(0): initializing int10
[    11.687] (EE) VESA(0): Cannot read V_BIOS (3) Input/output error
[    11.687] (II) UnloadModule: "vesa"
[    11.687] (II) UnloadSubModule: "int10"
[    11.687] (II) Unloading int10
[    11.687] (II) UnloadSubModule: "vbe"
[    11.687] (II) Unloading vbe
[COLOR="#FF0000"]**_[    11.687] (EE) Screen(s) found, but none have a usable configuration._**[/COLOR]
[    11.687] (EE) 
Fatal server error:
[    11.687] (EE) no screens found(EE) 
[    11.687] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    11.687] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    11.687] (EE) 
[    11.690] (EE) Server terminated with error (1). Closing log file.
```

---

### Post by cmptrwhz on 2013-10-21
I removed xserver-xorg and reinstalled it and then did a dpkg-reconfigure on it. but no questions were asked when i did the reconfigure.

---

### Post by cmptrwhz on 2013-10-21
I just purged and removed KDE, Lightdm, and Lightdm-kde-greeter. then reinstalled them. still nothing. please provide me with some ideas or what logs I should provide.

---

### Post by cmptrwhz on 2013-10-21
this is the weirdest thing ever but after I installed the virtualbox guest additions it started working again.

---

