---
title: "Update of 12.04 broken X"
date: 2012-11-02
forum: General Help
---

### Post by samuelpenn on 2012-11-02
Currently running Kubuntu 12.04. Events as follows:

1) Run update to get security fixes and package updates.
2) Notice that Chrome is broken, can no longer load Javascript heavy sites (e.g., GMail).
3) Restart Chrome doesn't help. Chromium works fine.
4) Reboot computer.
5) KDE bombs out during startup, back to console.

And that's the state I'm in. It seems that X is bombing out, possibly due to an nvidia driver problem.

I've include the content of Xorg.failsafe.log below:

Any ideas what to try next?

Thanks.

```

[    27.580] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    27.580] X Protocol Version 11, Revision 0
[    27.580] Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
[    27.580] Current Operating System: Linux strange 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64
[    27.580] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-31-generic root=UUID=e4a0845f-0447-4efd-bf89-c656d40f968d ro quiet splash vt.handoff=7
[    27.580] Build Date: 29 August 2012  12:12:33AM
[    27.580] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[    27.580] Current version of pixman: 0.24.4
[    27.580] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    27.580] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    27.580] (++) Log file: "/var/log/Xorg.failsafe.log", Time: Fri Nov  2 18:24:31 2012
[    27.580] (++) Using config file: "/etc/X11/xorg.conf.failsafe"
[    27.580] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.581] (==) No Layout section.  Using the first Screen section.
[    27.581] (**) |-->Screen "Default Screen" (0)
[    27.581] (**) |   |-->Monitor "Configured Monitor"
[    27.581] (**) |   |-->Device "Configured Video Device"
[    27.581] (==) Automatically adding devices
[    27.581] (==) Automatically enabling devices
[    27.581] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    27.581] 	Entry deleted from font path.
[    27.581] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    27.581] 	Entry deleted from font path.
[    27.581] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    27.581] 	Entry deleted from font path.
[    27.581] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    27.581] 	Entry deleted from font path.
[    27.581] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    27.581] 	Entry deleted from font path.
[    27.581] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    27.581] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    27.581] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    27.581] (II) Loader magic: 0x7fea71a76b00
[    27.581] (II) Module ABI versions:
[    27.581] 	X.Org ANSI C Emulation: 0.4
[    27.581] 	X.Org Video Driver: 11.0
[    27.581] 	X.Org XInput driver : 16.0
[    27.581] 	X.Org Server Extension : 6.0
[    27.581] (--) PCI:*(0:1:0:0) 10de:0de1:10de:0828 rev 161, Mem @ 0xfd000000/16777216, 0xf0000000/134217728, 0xf8000000/33554432, I/O @ 0x0000d800/128, BIOS @ 0x????????/524288
[    27.582] (II) Open ACPI successful (/var/run/acpid.socket)
[    27.582] (II) LoadModule: "extmod"
[    27.582] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    27.582] (II) Module extmod: vendor="X.Org Foundation"
[    27.582] 	compiled for 1.11.3, module version = 1.0.0
[    27.582] 	Module class: X.Org Server Extension
[    27.582] 	ABI class: X.Org Server Extension, version 6.0
[    27.582] (II) Loading extension MIT-SCREEN-SAVER
[    27.582] (II) Loading extension XFree86-VidModeExtension
[    27.582] (II) Loading extension XFree86-DGA
[    27.582] (II) Loading extension DPMS
[    27.582] (II) Loading extension XVideo
[    27.582] (II) Loading extension XVideo-MotionCompensation
[    27.582] (II) Loading extension X-Resource
[    27.582] (II) LoadModule: "dbe"
[    27.582] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    27.582] (II) Module dbe: vendor="X.Org Foundation"
[    27.582] 	compiled for 1.11.3, module version = 1.0.0
[    27.582] 	Module class: X.Org Server Extension
[    27.582] 	ABI class: X.Org Server Extension, version 6.0
[    27.582] (II) Loading extension DOUBLE-BUFFER
[    27.582] (II) LoadModule: "glx"
[    27.582] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    27.594] (II) Module glx: vendor="NVIDIA Corporation"
[    27.594] 	compiled for 4.0.2, module version = 1.0.0
[    27.594] 	Module class: X.Org Server Extension
[    27.594] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[    27.594] (II) Loading extension GLX
[    27.594] (II) LoadModule: "record"
[    27.594] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    27.594] (II) Module record: vendor="X.Org Foundation"
[    27.594] 	compiled for 1.11.3, module version = 1.13.0
[    27.594] 	Module class: X.Org Server Extension
[    27.594] 	ABI class: X.Org Server Extension, version 6.0
[    27.594] (II) Loading extension RECORD
[    27.594] (II) LoadModule: "dri"
[    27.594] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    27.594] (II) Module dri: vendor="X.Org Foundation"
[    27.594] 	compiled for 1.11.3, module version = 1.0.0
[    27.594] 	ABI class: X.Org Server Extension, version 6.0
[    27.594] (II) Loading extension XFree86-DRI
[    27.594] (II) LoadModule: "dri2"
[    27.595] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    27.595] (II) Module dri2: vendor="X.Org Foundation"
[    27.595] 	compiled for 1.11.3, module version = 1.2.0
[    27.595] 	ABI class: X.Org Server Extension, version 6.0
[    27.595] (II) Loading extension DRI2
[    27.595] (II) LoadModule: "vesa"
[    27.595] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    27.595] (II) Module vesa: vendor="X.Org Foundation"
[    27.595] 	compiled for 1.11.3, module version = 2.3.0
[    27.595] 	Module class: X.Org Video Driver
[    27.595] 	ABI class: X.Org Video Driver, version 11.0
[    27.595] (II) VESA: driver for VESA chipsets: vesa
[    27.595] (--) using VT number 8

[    27.596] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    27.596] vesa: Ignoring device with a bound kernel driver
[    27.596] (WW) Falling back to old probe method for vesa
[    27.596] (II) UnloadModule: "vesa"
[    27.596] (II) Unloading vesa
[    27.596] (EE) Screen(s) found, but none have a usable configuration.
[    27.596] 
Fatal server error:
[    27.596] no screens found
[    27.596] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    27.596] Please also check the log file at "/var/log/Xorg.failsafe.log" for additional information.
[    27.596] 
[    27.598]  ddxSigGiveUp: Closing log
[    27.598] Server terminated with error (1). Closing log file.

```

---

### Post by hal8000 on 2012-11-02
I notice two things from your error log, its reporting kernel 3.2, Ubuntu 12.10 is kernel 3.5.17 and no useable screens for X.


A couple of things to try but only if you can boot and log in at the console, start by typing:

uname -a

This will show which kernel is in use, then try

sudo modprobe nvidia

The above command will try and load the nvidia module, if that fails,
try loading the vesa module

sudo modprobe vesa


then to start your display manager type:


startx

---

### Post by samuelpenn on 2012-11-02
I'm running 12.04, not 12.10

uname -a reports 3.2.0-31-generic

I get no error if I try to modprobe nvidia, but running startx hangs the machine. This has been a 'feature' since my troubles started. When it first boots, I get the KDE starting screen, then the NVidia splash screen, then it dumps me to the console.

If I then subsequently try to startx, or kdm, then the machine hangs.

Running modprobe vesa gives a 'module not found' error.

Thanks,
Sam.

---

### Post by samuelpenn on 2012-11-02
I'm actually running 12.04.1

If I try apt-get install xserver-xorg-video-vesa then it tells me that I already have the latest version installed.

I can do modprobe vesafb, which works. startx then hangs the machine.

If I try to apt-get anything, I get errors about broken libc6 dependencies:

You might want to run apt-get -f install to correct these:
The following packages have unmet dependencies.
  libc6 : Breaks: libc6:i386 (!= 2.15-Oubuntu10.3) but 2.15-Oubuntu10.2 is to be installed

---

