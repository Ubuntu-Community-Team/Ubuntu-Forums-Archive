---
title: "Delay or freeze on logon screen"
date: 2015-11-03
forum: General Help
---

### Post by jose85 on 2015-11-03
Running Ubuntu 14.04

When I start up the computer, I get to the login screen and 2 things happen:

1.  The keyboard and mouse are not active.  While I can see that I can login, I cannot move the mouse, or type anything.  After maybe 30+ seconds, I'm able to use the mouse and keyboard.
2.  The login screen sometimes does not cover the entire monitor.  Almost as if it thinks my monitor is smaller.

Any idea how to go about fixing these?

---

### Post by jose85 on 2015-11-10
anyone?

---

### Post by houlouk on 2015-11-10
Hello,

Can you show us your file Xorg.0.log please ?

---

### Post by jose85 on 2015-11-14
I found the file you mentioned above, and there is also a ".old" version of it.  Here are the contents of the file you are referrring to:

[    13.142] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[    13.142] X Protocol Version 11, Revision 0
[    13.142] Build Operating System: Linux 3.2.0-77-generic x86_64 Ubuntu
[    13.142] Current Operating System: Linux ubu-desktop 3.19.0-33-generic #38~14.04.1-Ubuntu SMP Fri Nov 6 18:17:28 UTC 2015 x86_64
[    13.142] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-33-generic root=UUID=e9a2542f-cdd5-4014-b1d6-7f9021675256 ro quiet splash vt.handoff=7
[    13.142] Build Date: 13 May 2015  04:35:05AM
[    13.142] xorg-server 2:1.17.1-0ubuntu3~trusty1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    13.142] Current version of pixman: 0.30.2
[    13.142] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    13.142] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.142] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 14 09:36:59 2015
[    13.157] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.157] (==) No Layout section.  Using the first Screen section.
[    13.157] (==) No screen section available. Using defaults.
[    13.157] (**) |-->Screen "Default Screen Section" (0)
[    13.157] (**) |   |-->Monitor "<default monitor>"
[    13.157] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    13.157] (==) Automatically adding devices
[    13.157] (==) Automatically enabling devices
[    13.157] (==) Automatically adding GPU devices
[    13.157] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.157] 	Entry deleted from font path.
[    13.157] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    13.157] 	Entry deleted from font path.
[    13.157] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    13.157] 	Entry deleted from font path.
[    13.157] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    13.157] 	Entry deleted from font path.
[    13.157] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    13.157] 	Entry deleted from font path.
[    13.157] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    13.157] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.157] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    13.157] (II) Loader magic: 0x7f9350d64c60
[    13.157] (II) Module ABI versions:
[    13.157] 	X.Org ANSI C Emulation: 0.4
[    13.157] 	X.Org Video Driver: 19.0
[    13.157] 	X.Org XInput driver : 21.0
[    13.157] 	X.Org Server Extension : 9.0
[    13.158] (II) xfree86: Adding drm device (/dev/dri/card0)
[    13.158] (--) PCI:*(0:0:2:0) 8086:0412:1849:0412 rev 6, Mem @ 0xf0000000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[    13.158] (II) LoadModule: "glx"
[    13.159] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    13.348] (II) Module glx: vendor="X.Org Foundation"
[    13.348] 	compiled for 1.17.1, module version = 1.0.0
[    13.348] 	ABI class: X.Org Server Extension, version 9.0
[    13.348] (==) AIGLX enabled
[    13.348] (==) Matched intel as autoconfigured driver 0
[    13.348] (==) Matched intel as autoconfigured driver 1
[    13.348] (==) Matched modesetting as autoconfigured driver 2
[    13.348] (==) Matched fbdev as autoconfigured driver 3
[    13.348] (==) Matched vesa as autoconfigured driver 4
[    13.348] (==) Assigned the driver to the xf86ConfigLayout
[    13.348] (II) LoadModule: "intel"
[    13.349] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    13.368] (II) Module intel: vendor="X.Org Foundation"
[    13.368] 	compiled for 1.17.1, module version = 2.99.917
[    13.368] 	Module class: X.Org Video Driver
[    13.368] 	ABI class: X.Org Video Driver, version 19.0
[    13.368] (II) LoadModule: "modesetting"
[    13.368] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    13.368] (II) Module modesetting: vendor="X.Org Foundation"
[    13.368] 	compiled for 1.17.1, module version = 1.17.1
[    13.368] 	Module class: X.Org Video Driver
[    13.368] 	ABI class: X.Org Video Driver, version 19.0
[    13.368] (II) LoadModule: "fbdev"
[    13.368] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.368] (II) Module fbdev: vendor="X.Org Foundation"
[    13.368] 	compiled for 1.17.1, module version = 0.4.4
[    13.368] 	Module class: X.Org Video Driver
[    13.368] 	ABI class: X.Org Video Driver, version 19.0
[    13.368] (II) LoadModule: "vesa"
[    13.368] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    13.368] (II) Module vesa: vendor="X.Org Foundation"
[    13.368] 	compiled for 1.17.1, module version = 2.3.3
[    13.368] 	Module class: X.Org Video Driver
[    13.368] 	ABI class: X.Org Video Driver, version 19.0
[    13.368] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    13.368] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    13.368] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    13.368] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    13.369] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    13.369] (II) FBDEV: driver for framebuffer: fbdev
[    13.369] (II) VESA: driver for VESA chipsets: vesa
[    13.369] (++) using VT number 7


[    13.369] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20141121
[    13.369] (II) intel(0): SNA compiled: xserver-xorg-video-intel-lts-vivid 2:2.99.917-1~exp1ubuntu2.2~trusty1 (Timo Aaltonen <tjaalton@debian.org>)
[    13.369] (II) intel(0): SNA compiled for use with valgrind
[    13.369] (WW) Falling back to old probe method for modesetting
[    13.369] (WW) Falling back to old probe method for fbdev
[    13.369] (II) Loading sub module "fbdevhw"
[    13.369] (II) LoadModule: "fbdevhw"
[    13.369] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    13.369] (II) Module fbdevhw: vendor="X.Org Foundation"
[    13.369] 	compiled for 1.17.1, module version = 0.0.2
[    13.369] 	ABI class: X.Org Video Driver, version 19.0
[    13.369] (WW) Falling back to old probe method for vesa
[    13.369] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    13.369] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[    13.369] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    13.369] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    13.369] (==) intel(0): RGB weight 888
[    13.369] (==) intel(0): Default visual is TrueColor
[    13.369] (II) intel(0): Output VGA1 has no monitor section
[    13.369] (II) intel(0): Enabled output VGA1
[    13.369] (II) intel(0): Output HDMI1 has no monitor section
[    13.369] (II) intel(0): Enabled output HDMI1
[    13.369] (II) intel(0): Output DP1 has no monitor section
[    13.369] (II) intel(0): Enabled output DP1
[    13.369] (II) intel(0): Output HDMI2 has no monitor section
[    13.369] (II) intel(0): Enabled output HDMI2
[    13.369] (II) intel(0): Output HDMI3 has no monitor section
[    13.369] (II) intel(0): Enabled output HDMI3
[    13.369] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    13.369] (II) intel(0): Output VIRTUAL1 has no monitor section
[    13.369] (II) intel(0): Enabled output VIRTUAL1
[    13.369] (--) intel(0): Output HDMI1 using initial mode 1920x1080 on pipe 0
[    13.369] (--) intel(0): Output HDMI3 using initial mode 1280x800 on pipe 1
[    13.369] (==) intel(0): TearFree disabled
[    13.369] (==) intel(0): DPI set to (96, 96)
[    13.369] (II) Loading sub module "dri2"
[    13.369] (II) LoadModule: "dri2"
[    13.369] (II) Module "dri2" already built-in
[    13.369] (II) Loading sub module "present"
[    13.369] (II) LoadModule: "present"
[    13.369] (II) Module "present" already built-in
[    13.369] (II) UnloadModule: "modesetting"
[    13.369] (II) Unloading modesetting
[    13.369] (II) UnloadModule: "fbdev"
[    13.369] (II) Unloading fbdev
[    13.369] (II) UnloadSubModule: "fbdevhw"
[    13.369] (II) Unloading fbdevhw
[    13.369] (II) UnloadModule: "vesa"
[    13.369] (II) Unloading vesa
[    13.369] (==) Depth 24 pixmap format is 32 bpp
[    13.370] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[    13.370] (==) intel(0): Backing store enabled
[    13.370] (==) intel(0): Silken mouse enabled
[    13.370] (II) intel(0): HW Cursor enabled
[    13.370] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    13.370] (==) intel(0): DPMS enabled
[    13.370] (==) intel(0): display hotplug detection enabled
[    13.370] (II) intel(0): [DRI2] Setup complete
[    13.370] (II) intel(0): [DRI2]   DRI driver: i965
[    13.370] (II) intel(0): [DRI2]   VDPAU driver: i965
[    13.370] (II) intel(0): direct rendering: DRI2 enabled
[    13.370] (II) intel(0): hardware support for Present enabled
[    13.370] (--) RandR disabled
[    13.387] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    13.387] (II) AIGLX: enabled GLX_ARB_create_context
[    13.387] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    13.387] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    13.387] (II) AIGLX: enabled GLX_INTEL_swap_event
[    13.387] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    13.387] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    13.387] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    13.387] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    13.387] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    13.387] (II) AIGLX: Loaded and initialized i965
[    13.387] (II) GLX: Initialized DRI2 GL provider for screen 0
[    13.389] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using pipe 0, position (0, 0), rotation normal, reflection none
[    13.397] (II) intel(0): switch to mode 1280x800@60.0 on HDMI3 using pipe 1, position (0, 0), rotation normal, reflection none
[    13.412] (II) intel(0): Setting screen physical size to 508 x 285
[    13.416] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.417] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    13.417] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.417] (II) LoadModule: "evdev"
[    13.418] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.473] (II) Module evdev: vendor="X.Org Foundation"
[    13.473] 	compiled for 1.17.1, module version = 2.9.0
[    13.473] 	Module class: X.Org XInput Driver
[    13.473] 	ABI class: X.Org XInput driver, version 21.0
[    13.473] (II) Using input driver 'evdev' for 'Power Button'
[    13.473] (**) Power Button: always reports core events
[    13.473] (**) evdev: Power Button: Device: "/dev/input/event1"
[    13.473] (--) evdev: Power Button: Vendor 0 Product 0x1
[    13.473] (--) evdev: Power Button: Found keys
[    13.473] (II) evdev: Power Button: Configuring as keyboard
[    13.473] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    13.473] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    13.473] (**) Option "xkb_rules" "evdev"
[    13.473] (**) Option "xkb_model" "pc105"
[    13.473] (**) Option "xkb_layout" "us"
[    13.473] (II) config/udev: Adding input device Video Bus (/dev/input/event2)
[    13.473] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    13.473] (II) Using input driver 'evdev' for 'Video Bus'
[    13.473] (**) Video Bus: always reports core events
[    13.473] (**) evdev: Video Bus: Device: "/dev/input/event2"
[    13.473] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    13.473] (--) evdev: Video Bus: Found keys
[    13.473] (II) evdev: Video Bus: Configuring as keyboard
[    13.473] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event2"
[    13.473] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    13.473] (**) Option "xkb_rules" "evdev"
[    13.473] (**) Option "xkb_model" "pc105"
[    13.473] (**) Option "xkb_layout" "us"
[    13.473] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    13.473] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.473] (II) Using input driver 'evdev' for 'Power Button'
[    13.473] (**) Power Button: always reports core events
[    13.473] (**) evdev: Power Button: Device: "/dev/input/event0"
[    13.473] (--) evdev: Power Button: Vendor 0 Product 0x1
[    13.473] (--) evdev: Power Button: Found keys
[    13.473] (II) evdev: Power Button: Configuring as keyboard
[    13.473] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    13.473] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    13.473] (**) Option "xkb_rules" "evdev"
[    13.473] (**) Option "xkb_model" "pc105"
[    13.473] (**) Option "xkb_layout" "us"
[    13.474] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event8)
[    13.474] (II) No input driver specified, ignoring this device.
[    13.474] (II) This device may have been added with another device file.
[    13.474] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event9)
[    13.474] (II) No input driver specified, ignoring this device.
[    13.474] (II) This device may have been added with another device file.
[    13.474] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event10)
[    13.474] (II) No input driver specified, ignoring this device.
[    13.474] (II) This device may have been added with another device file.
[    13.474] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event7)
[    13.474] (II) No input driver specified, ignoring this device.
[    13.474] (II) This device may have been added with another device file.
[    13.474] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event3)
[    13.474] (II) No input driver specified, ignoring this device.
[    13.474] (II) This device may have been added with another device file.
[    13.474] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event4)
[    13.474] (II) No input driver specified, ignoring this device.
[    13.474] (II) This device may have been added with another device file.
[    13.474] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event5)
[    13.474] (II) No input driver specified, ignoring this device.
[    13.474] (II) This device may have been added with another device file.
[    13.474] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event6)
[    13.474] (II) No input driver specified, ignoring this device.
[    13.474] (II) This device may have been added with another device file.
[    42.754] (II) config/udev: Adding input device PixArt USB Optical Mouse (/dev/input/mouse0)
[    42.754] (II) No input driver specified, ignoring this device.
[    42.754] (II) This device may have been added with another device file.
[    42.754] (II) config/udev: Adding input device Dell Dell USB Entry Keyboard (/dev/input/event11)
[    42.754] (**) Dell Dell USB Entry Keyboard: Applying InputClass "evdev keyboard catchall"
[    42.754] (II) Using input driver 'evdev' for 'Dell Dell USB Entry Keyboard'
[    42.754] (**) Dell Dell USB Entry Keyboard: always reports core events
[    42.754] (**) evdev: Dell Dell USB Entry Keyboard: Device: "/dev/input/event11"
[    42.754] (--) evdev: Dell Dell USB Entry Keyboard: Vendor 0x413c Product 0x2107
[    42.754] (--) evdev: Dell Dell USB Entry Keyboard: Found keys
[    42.754] (II) evdev: Dell Dell USB Entry Keyboard: Configuring as keyboard
[    42.754] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13:1.0/0003:413C:2107.0001/input/input14/event11"
[    42.754] (II) XINPUT: Adding extended input device "Dell Dell USB Entry Keyboard" (type: KEYBOARD, id 9)
[    42.754] (**) Option "xkb_rules" "evdev"
[    42.754] (**) Option "xkb_model" "pc105"
[    42.754] (**) Option "xkb_layout" "us"
[    42.754] (II) config/udev: Adding input device PixArt USB Optical Mouse (/dev/input/event12)
[    42.755] (**) PixArt USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    42.755] (II) Using input driver 'evdev' for 'PixArt USB Optical Mouse'
[    42.755] (**) PixArt USB Optical Mouse: always reports core events
[    42.755] (**) evdev: PixArt USB Optical Mouse: Device: "/dev/input/event12"
[    42.808] (--) evdev: PixArt USB Optical Mouse: Vendor 0x93a Product 0x2510
[    42.808] (--) evdev: PixArt USB Optical Mouse: Found 12 mouse buttons
[    42.808] (--) evdev: PixArt USB Optical Mouse: Found scroll wheel(s)
[    42.808] (--) evdev: PixArt USB Optical Mouse: Found relative axes
[    42.808] (--) evdev: PixArt USB Optical Mouse: Found x and y relative axes
[    42.808] (II) evdev: PixArt USB Optical Mouse: Configuring as mouse
[    42.808] (II) evdev: PixArt USB Optical Mouse: Adding scrollwheel support
[    42.808] (**) evdev: PixArt USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    42.808] (**) evdev: PixArt USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    42.808] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-14/1-14:1.0/0003:093A:2510.0002/input/input15/event12"
[    42.808] (II) XINPUT: Adding extended input device "PixArt USB Optical Mouse" (type: MOUSE, id 10)
[    42.808] (II) evdev: PixArt USB Optical Mouse: initialized for relative axes.
[    42.808] (**) PixArt USB Optical Mouse: (accel) keeping acceleration scheme 1
[    42.808] (**) PixArt USB Optical Mouse: (accel) acceleration profile 0
[    42.808] (**) PixArt USB Optical Mouse: (accel) acceleration factor: 2.000
[    42.808] (**) PixArt USB Optical Mouse: (accel) acceleration threshold: 4
[    49.326] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    49.683] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    49.693] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    54.577] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[  2277.478] (II) intel(0): resizing framebuffer to 3200x1080
[  2277.506] (II) intel(0): switch to mode 1280x720@60.0 on HDMI3 using pipe 1, position (1920, 0), rotation normal, reflection none

---

