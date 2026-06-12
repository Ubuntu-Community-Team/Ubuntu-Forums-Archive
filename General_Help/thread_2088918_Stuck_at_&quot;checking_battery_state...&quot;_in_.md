---
title: "Stuck at &quot;checking battery state...&quot; in ubuntu 12.04. Please help."
date: 2012-11-27
forum: General Help
---

### Post by agentfortyseven on 2012-11-27
Hey there,
I've been using Ubuntu 12.04 for quite sometime now. Recently I started having problems with my gnome-settings-daemon i.e whenever I tried to shut down my PC, I used to get a prompt saying gnome-settings-daemon is currently busy. So I uninstalled it out of frustration (which was not a smart thing to do). When I restarted, I could not login and I couldn't see the regular GUI window at the startup. Instead I got the following message:

[B]*Starting network connection manager wicd 
rather than invoking init scripts through /etc/init.d use the service ( 8 ) utility, e.g. service S50 cups start initctl: Unknown job: S50 cups 
since the scripts you are attempting to invoke has been converted to an upstart job, you may also use the start ( 8 ) utility, e.g. start S50 cups saned disabled; edit /etc/default/saned
*checking battery state...      [/B] 

I managed to reinstall gnome-settings-daemon using sudo apt-get install gnome-settings-daemon from the terminal at the startup but it didn't help. 
Can you guys please help me out?

Edit: I have windows XP 32 bit dual boot on my laptop.

---

### Post by agentfortyseven on 2012-11-29
bump...

---

### Post by Statia on 2012-11-29
Maybe try:

 sudo dpkg-reconfigure gnome-whatwasitagain?can'tseepostwhileanswering

---

### Post by agentfortyseven on 2012-11-29
> **Statia said:**
> Maybe try:

 sudo dpkg-reconfigure gnome-whatwasitagain?can'tseepostwhileanswering

you can see my post if you try to reply with quote.

---

### Post by dino99 on 2012-11-29
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

or 

sudo rm /etc/X11/xorg.conf

then reboot

---

### Post by agentfortyseven on 2012-11-29
> **dino99 said:**
> sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

or 

sudo rm /etc/X11/xorg.conf

then reboot

Thanks. I will give it a try and let you know in a few minutes.

---

### Post by agentfortyseven on 2012-11-29
when I ran this command 'sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup' from the terminal mode at login I got the following reply:
mv: cannot stat '/etc/X11/xorg.conf': no such file or directory.

I got  a similiar reply for the second command you gave me.

---

### Post by sdowney717 on 2012-11-29
IMO, this is a video driver issue.

What do you have for a video card?
You can download and install video driver and make other changes from a console window.

---

### Post by sdowney717 on 2012-11-29
> **agentfortyseven said:**
> when I ran this command 'sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup' from the terminal mode at login I got the following reply:
mv: cannot stat '/etc/X11/xorg.conf': no such file or directory.

I got  a similiar reply for the second command you gave me.

then the file does not exist.
You should not need an xorg.conf file for video card to work except for proprietary binary drivers.
This is automatically configured. EDID data comes from monitor and the os automatically sets up the driver at boot.

There is an error log you can view in /var/logs. a 'EE' entry tells the problem. Right now cant recall the name of that log. there is a lot of info and it lists step by step what is happening at boot.

---

### Post by sdowney717 on 2012-11-29
var/log/xorg.0.log

here is my log

```
[  9172.855] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[  9172.855] X Protocol Version 11, Revision 0
[  9172.855] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[  9172.855] Current Operating System: Linux scott-P5QC 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686
[  9172.855] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-33-generic-pae root=UUID=4c1f632a-f05d-41e3-bc3e-ba9036e8e0b1 ro quiet splash vt.handoff=7
[  9172.855] Build Date: 29 August 2012  12:10:05AM
[  9172.855] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[  9172.855] Current version of pixman: 0.24.4
[  9172.855] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  9172.855] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  9172.855] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 24 10:37:56 2012
[  9172.855] (==) Using config file: "/etc/X11/xorg.conf"
[  9172.855] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  9172.856] (==) ServerLayout "Layout0"
[  9172.856] (**) |-->Screen "Screen0" (0)
[  9172.856] (**) |   |-->Monitor "Monitor0"
[  9172.856] (**) |   |-->Device "Device0"
[  9172.856] (**) |-->Input Device "Keyboard0"
[  9172.856] (**) |-->Input Device "Mouse0"
[  9172.856] (==) Automatically adding devices
[  9172.856] (==) Automatically enabling devices
[  9172.856] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  9172.856] 	Entry deleted from font path.
[  9172.856] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  9172.856] 	Entry deleted from font path.
[  9172.856] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  9172.856] 	Entry deleted from font path.
[  9172.856] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  9172.856] 	Entry deleted from font path.
[  9172.856] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  9172.856] 	Entry deleted from font path.
[  9172.856] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  9172.856] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  9172.856] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[  9172.856] (WW) Disabling Keyboard0
[  9172.856] (WW) Disabling Mouse0
[  9172.856] (II) Loader magic: 0xb77b45a0
[  9172.856] (II) Module ABI versions:
[  9172.856] 	X.Org ANSI C Emulation: 0.4
[  9172.856] 	X.Org Video Driver: 11.0
[  9172.856] 	X.Org XInput driver : 16.0
[  9172.856] 	X.Org Server Extension : 6.0
[  9172.857] (--) PCI:*(0:1:0:0) 10de:06e4:196e:05cc rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
[  9172.857] (--) PCI: (0:5:1:0) 4444:0016:9005:0092 rev 1, Mem @ 0xf4000000/67108864
[  9172.857] (II) Open ACPI successful (/var/run/acpid.socket)
[  9172.857] (II) LoadModule: "extmod"
[  9172.857] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  9172.857] (II) Module extmod: vendor="X.Org Foundation"
[  9172.857] 	compiled for 1.11.3, module version = 1.0.0
[  9172.857] 	Module class: X.Org Server Extension
[  9172.857] 	ABI class: X.Org Server Extension, version 6.0
[  9172.857] (II) Loading extension MIT-SCREEN-SAVER
[  9172.857] (II) Loading extension XFree86-VidModeExtension
[  9172.857] (II) Loading extension XFree86-DGA
[  9172.857] (II) Loading extension DPMS
[  9172.857] (II) Loading extension XVideo
[  9172.857] (II) Loading extension XVideo-MotionCompensation
[  9172.857] (II) Loading extension X-Resource
[  9172.857] (II) LoadModule: "dbe"
[  9172.858] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  9172.858] (II) Module dbe: vendor="X.Org Foundation"
[  9172.858] 	compiled for 1.11.3, module version = 1.0.0
[  9172.858] 	Module class: X.Org Server Extension
[  9172.858] 	ABI class: X.Org Server Extension, version 6.0
[  9172.858] (II) Loading extension DOUBLE-BUFFER
[  9172.858] (II) LoadModule: "glx"
[  9172.858] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[  9172.877] (II) Module glx: vendor="NVIDIA Corporation"
[  9172.877] 	compiled for 4.0.2, module version = 1.0.0
[  9172.877] 	Module class: X.Org Server Extension
[  9172.877] (II) NVIDIA GLX Module  304.64  Tue Oct 30 11:31:18 PDT 2012
[  9172.877] (II) Loading extension GLX
[  9172.877] (II) LoadModule: "record"
[  9172.877] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  9172.877] (II) Module record: vendor="X.Org Foundation"
[  9172.877] 	compiled for 1.11.3, module version = 1.13.0
[  9172.877] 	Module class: X.Org Server Extension
[  9172.877] 	ABI class: X.Org Server Extension, version 6.0
[  9172.877] (II) Loading extension RECORD
[  9172.877] (II) LoadModule: "dri"
[  9172.877] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  9172.877] (II) Module dri: vendor="X.Org Foundation"
[  9172.877] 	compiled for 1.11.3, module version = 1.0.0
[  9172.877] 	ABI class: X.Org Server Extension, version 6.0
[  9172.877] (II) Loading extension XFree86-DRI
[  9172.877] (II) LoadModule: "dri2"
[  9172.878] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  9172.878] (II) Module dri2: vendor="X.Org Foundation"
[  9172.878] 	compiled for 1.11.3, module version = 1.2.0
[  9172.878] 	ABI class: X.Org Server Extension, version 6.0
[  9172.878] (II) Loading extension DRI2
[  9172.878] (II) LoadModule: "nvidia"
[  9172.878] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  9172.878] (II) Module nvidia: vendor="NVIDIA Corporation"
[  9172.878] 	compiled for 4.0.2, module version = 1.0.0
[  9172.878] 	Module class: X.Org Video Driver
[  9172.878] (II) NVIDIA dlloader X Driver  304.64  Tue Oct 30 11:11:05 PDT 2012
[  9172.878] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  9172.878] (++) using VT number 7

[  9172.878] (II) Loading sub module "fb"
[  9172.878] (II) LoadModule: "fb"
[  9172.879] (II) Loading /usr/lib/xorg/modules/libfb.so
[  9172.879] (II) Module fb: vendor="X.Org Foundation"
[  9172.879] 	compiled for 1.11.3, module version = 1.0.0
[  9172.879] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  9172.879] (II) Loading sub module "wfb"
[  9172.879] (II) LoadModule: "wfb"
[  9172.879] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  9172.879] (II) Module wfb: vendor="X.Org Foundation"
[  9172.879] 	compiled for 1.11.3, module version = 1.0.0
[  9172.879] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  9172.879] (II) Loading sub module "ramdac"
[  9172.879] (II) LoadModule: "ramdac"
[  9172.879] (II) Module "ramdac" already built-in
[  9172.879] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  9172.879] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  9172.879] (II) Loading /usr/lib/xorg/modules/libfb.so
[  9172.879] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[  9172.879] (==) NVIDIA(0): RGB weight 888
[  9172.879] (==) NVIDIA(0): Default visual is TrueColor
[  9172.879] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  9172.879] (**) NVIDIA(0): Option "ExactModeTimingsDVI" "TRUE"
[  9172.879] (**) NVIDIA(0): Option "ModeValidation" "NoEdidModes"
[  9172.879] (**) NVIDIA(0): Enabling 2D acceleration
[  9173.240] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[  9173.240] (II) NVIDIA(GPU-0):     3D Vision stereo.
[  9173.241] (II) NVIDIA(0): NVIDIA GPU GeForce 8400 GS (G98) at PCI:1:0:0 (GPU-0)
[  9173.241] (--) NVIDIA(0): Memory: 524288 kBytes
[  9173.241] (--) NVIDIA(0): VideoBIOS: 62.98.29.00.51
[  9173.241] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  9173.241] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  9173.242] (--) NVIDIA(0): Valid display device(s) on GeForce 8400 GS at PCI:1:0:0
[  9173.242] (--) NVIDIA(0):     CRT-0
[  9173.242] (--) NVIDIA(0):     CRT-1
[  9173.242] (--) NVIDIA(0):     TV-0
[  9173.242] (--) NVIDIA(0):     Samsung SyncMaster (DFP-0) (connected)
[  9173.242] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[  9173.242] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[  9173.242] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[  9173.242] (--) NVIDIA(0): TV encoder: (null)
[  9173.242] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
[  9173.242] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
[  9173.242] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  9173.242] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[  9173.242] (**) NVIDIA(0):     has been enabled on all display devices.)
[  9173.242] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[  9173.242] (II) NVIDIA(0):     NoEdidModes
[  9173.252] (II) NVIDIA(0): Validated MetaModes:
[  9173.252] (II) NVIDIA(0):     "DFP-0:1680x1050"
[  9173.252] (II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
[  9173.288] (--) NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
[  9173.288] (--) NVIDIA(0):     option
[  9173.288] (--) Depth 24 pixmap format is 32 bpp
[  9173.288] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[  9173.292] (II) NVIDIA(0): Setting mode "DFP-0:1680x1050"
[  9173.326] (II) Loading extension NV-GLX
[  9173.357] (==) NVIDIA(0): Disabling shared memory pixmaps
[  9173.357] (==) NVIDIA(0): Backing store disabled
[  9173.357] (==) NVIDIA(0): Silken mouse enabled
[  9173.357] (**) NVIDIA(0): DPMS enabled
[  9173.357] (II) Loading extension NV-CONTROL
[  9173.357] (II) Loading extension XINERAMA
[  9173.357] (II) Loading sub module "dri2"
[  9173.357] (II) LoadModule: "dri2"
[  9173.358] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  9173.358] (II) Module dri2: vendor="X.Org Foundation"
[  9173.358] 	compiled for 1.11.3, module version = 1.2.0
[  9173.358] 	ABI class: X.Org Server Extension, version 6.0
[  9173.358] (II) NVIDIA(0): [DRI2] Setup complete
[  9173.358] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[  9173.358] (--) RandR disabled
[  9173.358] (II) Initializing built-in extension Generic Event Extension
[  9173.358] (II) Initializing built-in extension SHAPE
[  9173.358] (II) Initializing built-in extension MIT-SHM
[  9173.358] (II) Initializing built-in extension XInputExtension
[  9173.358] (II) Initializing built-in extension XTEST
[  9173.358] (II) Initializing built-in extension BIG-REQUESTS
[  9173.358] (II) Initializing built-in extension SYNC
[  9173.358] (II) Initializing built-in extension XKEYBOARD
[  9173.358] (II) Initializing built-in extension XC-MISC
[  9173.358] (II) Initializing built-in extension SECURITY
[  9173.358] (II) Initializing built-in extension XINERAMA
[  9173.358] (II) Initializing built-in extension XFIXES
[  9173.358] (II) Initializing built-in extension RENDER
[  9173.358] (II) Initializing built-in extension RANDR
[  9173.358] (II) Initializing built-in extension COMPOSITE
[  9173.358] (II) Initializing built-in extension DAMAGE
[  9173.360] (II) Initializing extension GLX
[  9173.374] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  9173.376] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  9173.377] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  9173.377] (II) LoadModule: "evdev"
[  9173.377] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  9173.377] (II) Module evdev: vendor="X.Org Foundation"
[  9173.377] 	compiled for 1.11.3, module version = 2.7.0
[  9173.377] 	Module class: X.Org XInput Driver
[  9173.377] 	ABI class: X.Org XInput driver, version 16.0
[  9173.377] (II) Using input driver 'evdev' for 'Power Button'
[  9173.377] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  9173.377] (**) Power Button: always reports core events
[  9173.377] (**) evdev: Power Button: Device: "/dev/input/event1"
[  9173.377] (--) evdev: Power Button: Vendor 0 Product 0x1
[  9173.377] (--) evdev: Power Button: Found keys
[  9173.377] (II) evdev: Power Button: Configuring as keyboard
[  9173.377] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[  9173.377] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  9173.377] (**) Option "xkb_rules" "evdev"
[  9173.377] (**) Option "xkb_model" "pc105"
[  9173.377] (**) Option "xkb_layout" "us"
[  9173.377] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  9173.377] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  9173.377] (II) Using input driver 'evdev' for 'Power Button'
[  9173.377] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  9173.377] (**) Power Button: always reports core events
[  9173.377] (**) evdev: Power Button: Device: "/dev/input/event0"
[  9173.378] (--) evdev: Power Button: Vendor 0 Product 0x1
[  9173.378] (--) evdev: Power Button: Found keys
[  9173.378] (II) evdev: Power Button: Configuring as keyboard
[  9173.378] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[  9173.378] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[  9173.378] (**) Option "xkb_rules" "evdev"
[  9173.378] (**) Option "xkb_model" "pc105"
[  9173.378] (**) Option "xkb_layout" "us"
[  9173.378] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
[  9173.378] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[  9173.378] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[  9173.378] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  9173.378] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[  9173.378] (**) evdev: Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
[  9173.378] (--) evdev: Logitech USB-PS/2 Optical Mouse: Vendor 0x46d Product 0xc00e
[  9173.378] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
[  9173.378] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[  9173.378] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found relative axes
[  9173.378] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[  9173.378] (II) evdev: Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[  9173.378] (II) evdev: Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[  9173.378] (**) evdev: Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[  9173.378] (**) evdev: Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  9173.378] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input4/event4"
[  9173.378] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE, id 8)
[  9173.378] (II) evdev: Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[  9173.378] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[  9173.378] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[  9173.378] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[  9173.378] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[  9173.378] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[  9173.378] (II) No input driver specified, ignoring this device.
[  9173.378] (II) This device may have been added with another device file.
[  9173.379] (II) config/udev: Adding input device sn9c20x (/dev/input/event3)
[  9173.379] (**) sn9c20x: Applying InputClass "evdev keyboard catchall"
[  9173.379] (II) Using input driver 'evdev' for 'sn9c20x'
[  9173.379] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  9173.379] (**) sn9c20x: always reports core events
[  9173.379] (**) evdev: sn9c20x: Device: "/dev/input/event3"
[  9173.379] (--) evdev: sn9c20x: Vendor 0x45e Product 0xf4
[  9173.379] (--) evdev: sn9c20x: Found keys
[  9173.379] (II) evdev: sn9c20x: Configuring as keyboard
[  9173.379] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4/input/input3/event3"
[  9173.379] (II) XINPUT: Adding extended input device "sn9c20x" (type: KEYBOARD, id 9)
[  9173.379] (**) Option "xkb_rules" "evdev"
[  9173.379] (**) Option "xkb_model" "pc105"
[  9173.379] (**) Option "xkb_layout" "us"
[  9173.379] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[  9173.379] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  9173.379] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  9173.379] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  9173.379] (**) AT Translated Set 2 keyboard: always reports core events
[  9173.379] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[  9173.379] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[  9173.379] (--) evdev: AT Translated Set 2 keyboard: Found keys
[  9173.379] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[  9173.379] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[  9173.379] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[  9173.379] (**) Option "xkb_rules" "evdev"
[  9173.379] (**) Option "xkb_model" "pc105"
[  9173.379] (**) Option "xkb_layout" "us"
[  9173.668] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[  9173.669] (II) NVIDIA(GPU-0):     3D Vision stereo.
[  9173.669] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  9173.669] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[  9173.669] (**) NVIDIA(0):     has been enabled on all display devices.)
[  9173.669] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[  9173.669] (II) NVIDIA(0):     NoEdidModes
[  9173.814] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[  9173.814] (II) NVIDIA(GPU-0):     3D Vision stereo.
[  9173.814] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  9173.814] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[  9173.814] (**) NVIDIA(0):     has been enabled on all display devices.)
[  9173.814] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[  9173.814] (II) NVIDIA(0):     NoEdidModes
[  9182.000] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[  9182.000] (II) NVIDIA(GPU-0):     3D Vision stereo.
[  9182.000] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  9182.000] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[  9182.000] (**) NVIDIA(0):     has been enabled on all display devices.)
[  9182.000] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[  9182.000] (II) NVIDIA(0):     NoEdidModes
[  9182.181] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[  9182.181] (II) NVIDIA(GPU-0):     3D Vision stereo.
[  9182.181] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  9182.181] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[  9182.181] (**) NVIDIA(0):     has been enabled on all display devices.)
[  9182.181] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[  9182.181] (II) NVIDIA(0):     NoEdidModes
[  9182.359] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[  9202.494] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[  9202.494] (II) NVIDIA(GPU-0):     3D Vision stereo.
[  9202.494] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  9202.494] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[  9202.494] (**) NVIDIA(0):     has been enabled on all display devices.)
[  9202.494] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[  9202.494] (II) NVIDIA(0):     NoEdidModes
[  9212.440] (II) NVIDIA(0): Setting mode "DVI-I-1:1920x1080"
[  9216.795] (WW) NVIDIA(0): Specified panning domain height of 576 is smaller than
[  9216.795] (WW) NVIDIA(0):     viewport height 768; adjusting
[  9245.142] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[ 13437.881] [mi] Increasing EQ size to 512 to prevent dropped events.
[ 19658.432] (II) NVIDIA(0): Setting mode "DFP-0:1680x1050"
[ 19661.805] (WW) NVIDIA(0): Specified panning domain height of 576 is smaller than
[ 19661.805] (WW) NVIDIA(0):     viewport height 768; adjusting
[ 30414.653] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[ 30414.653] (II) NVIDIA(GPU-0):     3D Vision stereo.
[ 30414.653] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 30414.653] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[ 30414.653] (**) NVIDIA(0):     has been enabled on all display devices.)
[ 30414.653] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[ 30414.653] (II) NVIDIA(0):     NoEdidModes
[ 36635.812] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[ 36635.812] (II) NVIDIA(GPU-0):     3D Vision stereo.
[ 36635.812] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 36635.812] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[ 36635.812] (**) NVIDIA(0):     has been enabled on all display devices.)
[ 36635.812] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[ 36635.812] (II) NVIDIA(0):     NoEdidModes
[ 59469.413] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[ 59469.413] (II) NVIDIA(GPU-0):     3D Vision stereo.
[ 59469.413] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 59469.413] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[ 59469.413] (**) NVIDIA(0):     has been enabled on all display devices.)
[ 59469.414] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[ 59469.414] (II) NVIDIA(0):     NoEdidModes
[100012.813] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[100012.821] (II) NVIDIA(GPU-0):     3D Vision stereo.
[100012.833] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[100012.833] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[100012.833] (**) NVIDIA(0):     has been enabled on all display devices.)
[100012.833] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[100012.833] (II) NVIDIA(0):     NoEdidModes
[125709.683] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[125709.693] (II) NVIDIA(GPU-0):     3D Vision stereo.
[125709.694] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[125709.694] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[125709.694] (**) NVIDIA(0):     has been enabled on all display devices.)
[125709.694] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[125709.694] (II) NVIDIA(0):     NoEdidModes
[139011.068] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[139011.076] (II) NVIDIA(GPU-0):     3D Vision stereo.
[139011.077] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[139011.077] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[139011.077] (**) NVIDIA(0):     has been enabled on all display devices.)
[139011.077] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[139011.077] (II) NVIDIA(0):     NoEdidModes
[146622.006] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[146622.006] (II) NVIDIA(GPU-0):     3D Vision stereo.
[146622.006] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[146622.006] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[146622.006] (**) NVIDIA(0):     has been enabled on all display devices.)
[146622.006] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[146622.006] (II) NVIDIA(0):     NoEdidModes
[181476.308] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[181476.316] (II) NVIDIA(GPU-0):     3D Vision stereo.
[181476.317] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[181476.317] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[181476.317] (**) NVIDIA(0):     has been enabled on all display devices.)
[181476.317] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[181476.317] (II) NVIDIA(0):     NoEdidModes
[217062.074] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[217062.131] (II) NVIDIA(GPU-0):     3D Vision stereo.
[217062.142] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[217062.142] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[217062.142] (**) NVIDIA(0):     has been enabled on all display devices.)
[217062.174] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[217062.174] (II) NVIDIA(0):     NoEdidModes
[227827.200] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[227827.208] (II) NVIDIA(GPU-0):     3D Vision stereo.
[227827.208] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[227827.208] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[227827.208] (**) NVIDIA(0):     has been enabled on all display devices.)
[227827.208] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[227827.208] (II) NVIDIA(0):     NoEdidModes
[267819.310] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[267819.318] (II) NVIDIA(GPU-0):     3D Vision stereo.
[267819.319] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[267819.319] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[267819.319] (**) NVIDIA(0):     has been enabled on all display devices.)
[267819.319] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[267819.319] (II) NVIDIA(0):     NoEdidModes
[296814.912] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[296814.920] (II) NVIDIA(GPU-0):     3D Vision stereo.
[296814.920] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[296814.920] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[296814.920] (**) NVIDIA(0):     has been enabled on all display devices.)
[296814.921] (II) NVIDIA(0): Mode Validation Overrides for Samsung SyncMaster (DFP-0):
[296814.921] (II) NVIDIA(0):     NoEdidModes
[303414.581] 
```

---

### Post by agentfortyseven on 2012-11-29
> **sdowney717 said:**
> IMO, this is a video driver issue.

What do you have for a video card?
You can download and install video driver and make other changes from a console window.

I have NVIDIA Quadro NVS 160M.
You think this procedure won't work?

> sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
or 
sudo rm /etc/X11/xorg.conf
then rebootCan you please tell me how to download, install and make other changes from the console window.

---

### Post by sdowney717 on 2012-11-29
you can use wget command to download an nvidia driver from their website.
I have done it before.
the idea is download it, then install from the boot console window.

You just have to log in from the boot menu screen to a command prompt with networking enabled.

You need to find the details for getting this file using a google search. Or maybe someone else will know a better way to fix this.

to install you navigate to the directory and type 
./nameoffile.run 
ls shows the files in a directory. cd lets you move into the directory, etc...

You got an error running that command so you likely do not have the xorg file in etc folder.

---

### Post by sdowney717 on 2012-11-29
here is a site that talks about doing this.
there may be another way.

[http://superuser.com/questions/484991/nvidia-graphics-driver-in-ubuntu-12-04](http://superuser.com/questions/484991/nvidia-graphics-driver-in-ubuntu-12-04)

---

### Post by agentfortyseven on 2012-11-29
alright I will try to do that and let you know if it works.

---

### Post by dino99 on 2012-11-29
for a quadro card, you need either:
- the nvidia driver from the site
- or install "nouveau" which work also with the quadro cards

[http://askubuntu.com/questions/93809/nvidia-quadro-nvs-160m-in-the-dell-latitude-e6500](http://askubuntu.com/questions/93809/nvidia-quadro-nvs-160m-in-the-dell-latitude-e6500)

See /usr/share/doc/nvidia-current-updates/README.txt.gz for a complete list
of supported GPUs and PCIIDs

---

### Post by NikTh on 2012-11-29
Hi,
nouveau (open source driver for nvidia) is pre-installed. Have you tried it ? 

You can execute the commands below to make sure that no nvidia-proprietary driver left in your system and nouveau will be used. 

```
sudo apt-get purge nvidia-*
sudo rm /etc/X11/xorg.conf **#** if the file does not exist , then is OK 
sudo apt-get install nvidia-common ubuntu-desktop
sudo apt-get install --reinstall xserver-xorg-video-nouveau
sudo dpkg-reconfigure xserver-xorg 
```and at the end , give this command to reboot your pc
```
sudo reboot
```If everything work ok , then is not needed to install additional-proprietary nvidia driver.

Thanks

---

### Post by sdowney717 on 2012-11-29
> **NikTh said:**
> Hi,
If everything work ok , then is not needed to install additional-proprietary nvidia driver.

Thanks

I really cant imagine running that driver. 
How well does it do games and video?

---

### Post by dannyboy79 on 2012-11-29
i get that same checking battery state message on my headless server. it's because I uninstalled a desktop manager. I am guessing lightdm was uninstalled when you uninstalled that gnome thingy. try to reinstall lightdm.

also, what happens if at the checking battery state screen, you hit ctrl-alt-f1, login textually. then at the prompt enter this
sudo service start lightdm

---

### Post by sdowney717 on 2012-11-29
> **dannyboy79 said:**
> i get that same checking battery state message on my headless server. it's because I uninstalled a desktop manager. I am guessing lightdm was uninstalled when you uninstalled that gnome thingy. try to reinstall lightdm.

also, what happens if at the checking battery state screen, you hit ctrl-alt-f1, login textually. then at the prompt enter this
sudo service start lightdm

the xorg.0.log file should reveal the problem, if he looks at it.

you can from the root directory 

cat /var/log/Xorg.0.log |more

to see it. space bar and enter key will move it along.

---

### Post by agentfortyseven on 2012-11-30
I have to say I am overwhelmed by your help and support guys. So thanks a lot.

---

### Post by agentfortyseven on 2012-11-30
> **NikTh said:**
> Hi,
nouveau (open source driver for nvidia) is pre-installed. Have you tried it ? 

You can execute the commands below to make sure that no nvidia-proprietary driver left in your system and nouveau will be used. 

```
sudo apt-get purge nvidia-*
sudo rm /etc/X11/xorg.conf **#** if the file does not exist , then is OK 
sudo apt-get install nvidia-common ubuntu-desktop
sudo apt-get install --reinstall xserver-xorg-video-nouveau
sudo dpkg-reconfigure xserver-xorg 
```and at the end , give this command to reboot your pc
```
sudo reboot
```If everything work ok , then is not needed to install additional-proprietary nvidia driver.

Thanks

I tried this and I was finally able to login from the GUI.
But there is a small problem with this procedure. 
Whenever  I reboot or start my computer, after the purple screen with red dots I  see "a purple screen with a dark patch" for about 10-15 seconds followed  by a white screen for some 5 seconds and then I see the login window. 
Can someone please tell me what could be wrong?

---

### Post by agentfortyseven on 2012-11-30
> **dannyboy79 said:**
> i get that same checking battery state message on my headless server. it's because I uninstalled a desktop manager. I am guessing lightdm was uninstalled when you uninstalled that gnome thingy. try to reinstall lightdm.

also, what happens if at the checking battery state screen, you hit ctrl-alt-f1, login textually. then at the prompt enter this
sudo service start lightdm

Now that I can finally login, I can see that I have lightdm installed on my computer. 
Do I need to run the following command from the terminal?
> sudo service start lightdm 

---

### Post by NikTh on 2012-11-30
Hi ,
lightdm is already started . You don't need to start something manually. The  problem probably is with graphics driver , Nvidia additional drivers. 
Now that you have purged completely nvidia , you can try to install another version if you want.
You have 2 options. 
One is nvidia-experimental-304 and the other is nvidia-experimental-310 

First try 
```
sudo apt-get install nvidia-experimental-304 nvidia-settings-experimental-304
sudo nvidia-xconfig
``` 

Reboot to see if you can login without problems. 

The other "problem" with plymouth(during OS start, that with the dots ...etc) , I cannot handle it . Sometimes work good , sometimes not.

If the experimental-304 not working for you , try the 310, but first remove manually the 304.
```
sudo apt-get remove --purge nvidia-experimental-*
sudo rm /etc/X11/xorg.conf
```
and then try 310
```
sudo apt-get install nvidia-experimental-310 nvidia-settings-experimental-310
sudo nvidia-xconfig
```
and reboot again.

Thanks (hope you solve it soon)

---

### Post by agentfortyseven on 2012-11-30
> **NikTh said:**
> Hi ,
First try 
```
sudo apt-get install nvidia-experimental-304 nvidia-settings-experimental-304
sudo nvidia-xconfig
```Reboot to see if you can login without problems. 
 
Thanks a lot. Now I don’t see that ugly screen at login however now I see an NVIDIA splash screen at startup for a couple of seconds and I can still see that bright white screen I talked about in my earlier post.
Should I try nvidia-experimental-310? Will it fix my problem? Or is there any other way?

---

### Post by NikTh on 2012-11-30
> **agentfortyseven said:**
> now I see an **NVIDIA splash screen **at startup for a couple of seconds and I can still see that bright white screen I talked about in my earlier post. 
Yes ? is it beautiful ? never saw it :) 

> **agentfortyseven said:**
> Should I try nvidia-experimental-310? Will it fix my problem? Or is there any other way?

Well, nobody can tell you if will work better or worst. Experimental is experimental. 
If you want to give it a shot.. you know how to remove if not work. 

Thanks

---

### Post by agentfortyseven on 2012-12-02
> **NikTh said:**
> First try 
     Code:
     sudo apt-get install nvidia-experimental-304 nvidia-settings-experimental-304 
sudo nvidia-xconfig 
I actually forgot to run the second command and  restarted. Now when I ran the second command I don’t see the white  screen anymore but I do see the nvidia splash screen. And the boot time  has increased compared to what it used to be. I'm gonna mark this thread as solved anyway.


> **NikTh said:**
> Yes ? is it beautiful ? never saw it 
Nah its not beautiful at all but I can deal with it. I would however be glad if you or someone else could help me stop it from appearing at login.
And thanks a lot for your help NikTh and others too.

---

### Post by NikTh on 2012-12-02
> **agentfortyseven said:**
> 
Nah its not beautiful at all but I can deal with it. I would however be glad if you or someone else could help me stop it from appearing at login.

The only thing I can suggest is this command 
```
sudo update-alternatives --config default.plymouth
``` 
and if the results are more than one , choose the Ubuntu's plymouth screen. 

Then run 

```
sudo update-initramfs -u -k all
``` 

Thanks

---

### Post by dannyboy79 on 2012-12-03
you can add
```
Option "NoLogo" "True"
```
to your xorg.conf file I am just not exactly sure which section it suppose to be put in.

---

### Post by agentfortyseven on 2012-12-04
> **NikTh said:**
> The only thing I can suggest is this command 
```
sudo update-alternatives --config default.plymouth
```

When i ran the above command I got the following message:
[I]There is only one alternative in link group default.plymouth: /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth
Nothing to configure.[/I]

Its alright I'm happy with my computer right now.
I do however have one final question: 
Is nvidia experimental 304 driver more stable or experimental 310? Because I have experimental 304 driver and sometimes my computer freezes.

---

### Post by agentfortyseven on 2012-12-04
> **dannyboy79 said:**
> you can add
```
Option "NoLogo" "True"
```to your xorg.conf file I am just not exactly sure which section it suppose to be put in.

I don't have any xorg.conf file on my computer my friend. But thanks a lot for your help.

---

### Post by NikTh on 2012-12-04
> **agentfortyseven said:**
> 
[I]There is only one alternative in link group default.plymouth: /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth
Nothing to configure.[/I] 
So , is not the plymouth. 

> **agentfortyseven said:**
> I do however have one final question: 
Is nvidia experimental 304 driver more stable or experimental 310? Because I have experimental 304 driver and sometimes my computer freezes.
No , is not more stable , but the 310 is newer driver than 304. 
You can test it if you want , by running the commands below (one at time)
```
sudo apt-get remove --purge nvidia-*
sudo apt-get install nvidia-experimental-310 nvidia-settings-experimental-310
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
```and reboot your PC to see if its better.

> **agentfortyseven said:**
> I don't have any xorg.conf file on my computer my friend. But thanks a lot for your help.
Yes you have. If you ran the commands as I gave them , the command ```
sudo nvidia-xconfig
``` creates an xorg.conf file . The path is /etc/X11/xorg.conf
To open this file you can give in terminal
```
gksudo gedit /etc/X11/xorg.conf
```and add what @dannyboy79 suggested , by hand (manually). You will see other options as well. I think you should add the Options at ```
Section "Device"
    Option          "NoLogo"             "True" 
```
save the file and reboot your PC to see the changes.
Thanks

---

### Post by dannyboy79 on 2012-12-04
he shouldn't have to remove the xorg.conf if trying a different nvidia driver IMO. the driver still remains "nvidia" doesn't it?

By the way, NikTH, can you possibly provide some help over here I am having my own Xserver issues with an nvidia geforce 6200 card.
[http://ubuntuforums.org/showthread.php?t=2090231](http://ubuntuforums.org/showthread.php?t=2090231)

---

### Post by NikTh on 2012-12-04
> **dannyboy79 said:**
> he shouldn't have to remove the xorg.conf if trying a different nvidia driver IMO. the driver still remains "nvidia" doesn't it?

Yes , you have right to that. But is a matter of a .... habit of mine ? :)

---

### Post by agentfortyseven on 2012-12-06
> **NikTh said:**
> So , is not the plymouth. 


No , is not more stable , but the 310 is newer driver than 304. 
You can test it if you want , by running the commands below (one at time)
```
sudo apt-get remove --purge nvidia-*
sudo apt-get install nvidia-experimental-310 nvidia-settings-experimental-310
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
```and reboot your PC to see if its better.

Ok I've installed nvidia experimental 310. Hopefully it wont be as buggy as experimental 304.


> **NikTh said:**
> Yes you have. If you ran the commands as I gave them , the command ```
sudo nvidia-xconfig
``` creates an xorg.conf file . The path is /etc/X11/xorg.conf
To open this file you can give in terminal
```
gksudo gedit /etc/X11/xorg.conf
```and add what @dannyboy79 suggested , by hand (manually). You will see other options as well. I think you should add the Options at ```
Section "Device"
    Option          "NoLogo"             "True" 
```save the file and reboot your PC to see the changes.
Thanks

 I tried this and I dont see any nvidia logo at startup anymore. 
Thank you so much guys I really appreciate your help.

Edit: I would be really happy if you could help me out with my other issue with adobe flash plugin [http://ubuntuforums.org/showthread.php?t=2091771](http://ubuntuforums.org/showthread.php?t=2091771)

---

### Post by zainka on 2012-12-07
Hi

When I boot i get a glimpse of the Xubuntu (12.04) splashscreen before getting "Checking battery State" message. However, I am not able to enter shell or do anything. The box won't react to any keyboard commands at all including ctrl+alt+f1, alt+f5, ctrl+alt+del, and any other similar commands. only a restart will do and therefor I am not able to reinstall or change the nvidia settings etc.

I may boot into recoverymode and enter root shell, but then the file system is reported as beeing read only and I can't reinstall the nvidia driver. I have been looking into many threads similar to this one and tried many solutions but nothing helps. 

Main issue now is to enter shell from normall boot. Any help will do. Is there any boot command i can write in grub (e' option) that will make my box boot normally except it will omit graphic and use shell directly, asking for my login data?

Breg
Vidar

---

### Post by zainka on 2012-12-10
> **zainka said:**
> 
Main issue now is to enter shell from normall boot.

Solved this by using the grub 'e' option to change the boot command. Added word "text" just after "quiet splash" on second last line. 

Now working on solving the battery state issue

---

