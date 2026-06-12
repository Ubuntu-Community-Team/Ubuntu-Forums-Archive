---
title: "Black/Blank Screen when Waking from Suspend"
date: 2014-07-14
forum: General Help
---

### Post by P_THE_AWESOME on 2014-07-14
Basically, my computer suspends correctly. However, when it wakes up, I get a blank screen on both my TV and laptop screen (the TV one should be on). No cursor or anything. **I know that it wakes up correctly because I can VNC (through x11vnc and UltraVNC) into the system. **Through the VNC, t shows everything just as I left it. I can interact with it from UltraVNC perfectly fine. I should note that this is acting as a home theater PC, so please don't suggest anything that will require me to walk over the the keyboard after waking up from standby. Some suggestions I saw from Google included auto-locking the desktop before suspending, but that would require me to type in my password, so that's not a solution. This is the first time I have loaded anything other than Windows XP on this machine.

So far, I have tried [Fix Ubuntu (or Linux) Suspend/Hibernate Not Working Bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug") to no avail. 
I would be happy to provide any logs or specs, etc. I am unsure exactly which logs to show for this porblem. Any help is greatly appreciated.


Lubuntu 14.04 LTS i386
Dell Latitude D610 Notebook (Monitor Off)
External 1360x768 HDMI TV
Intel(R) Graphics Installer 1.0.5 for Linux (for 14.04)

---

### Post by bapoumba on 2014-07-14
Just to point out that this guide is for 10.10. Although it could work on later releases, chances are it wont.

---

### Post by P_THE_AWESOME on 2014-07-14
> **bapoumba said:**
> Just to point out that this guide is for 10.10.  Although it could work on later releases, chances are it wont.
I know it's old, but a lot of posts and blogs linked there. Is there a newer solution (yet)?

Which log files are related to suspending/waking up?

---

### Post by P_THE_AWESOME on 2014-07-14
Well, I found [UnderstandingSuspend]("https://wiki.ubuntu.com/UnderstandingSuspend") and [DebuggingKernelSuspend]("https://wiki.ubuntu.com/DebuggingKernelSuspend") on the Ubuntu Wiki. It outlined some ways for finding problems. Again, I will say that the X desktop seems alright since I can VNC to it right where I left off, so it must be a display problem.

The first test suggested on the UnderstandingSuspend page was too outdated (running [FONT=courier new]/etc/acpi/sleep.sh --force[/FONT]). It turns out, that page was last edited in 2011 and [FONT=courier new]/etc/acpi[/FONT] doesn't exist in my 14.04 Lubuntu install. The DebuggingKernelSuspend page was last edited this year though.


After suspending (with the menu that pops up when clicking the icon in the bottom right) and waking up. Received through Putty SSH:

[FONT=courier new]cat /proc/acpi/wakeup > wakeup[/FONT]
[FONT=courier new]nano ~/wakeup[/FONT]:
 ```
Device  S-state   Status   Sysfs node
LID       S3    *enabled
PBTN      S4    *enabled
PCI0      S5    *disabled  no-bus:pci0000:00
USB0      S0    *enabled   pci:0000:00:1d.0
USB1      S0    *enabled   pci:0000:00:1d.1
USB2      S0    *enabled   pci:0000:00:1d.2
USB4      S0    *enabled   pci:0000:00:1d.3
USB3      S0    *enabled   pci:0000:00:1d.7
MODM      S3    *disabled  pci:0000:00:1e.3
PCIE      S4    *disabled  pci:0000:00:1e.0
NIC       S5    *enabled   pci:0000:02:00.0

```

 [HR][/HR][FONT=courier new]
nano /var/log/Xorg.0.log[/FONT]:
```
[    26.606]
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    26.606] X Protocol Version 11, Revision 0
[    26.606] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    26.606] Current Operating System: Linux media-D610 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:43:42 UTC 2014 i686
[    26.606] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-30-generic root=/dev/mapper/lubuntu--vg-root ro quiet splash vt.handoff=7
[    26.606] Build Date: 16 April 2014  01:40:08PM
[    26.606] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support)
[    26.606] Current version of pixman: 0.30.2
[    26.606]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    26.606] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.606] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 14 20:45:08 2014
[    26.627] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.628] (==) No Layout section.  Using the first Screen section.
[    26.628] (==) No screen section available. Using defaults.
[    26.628] (**) |-->Screen "Default Screen Section" (0)
[    26.628] (**) |   |-->Monitor "<default monitor>"
[    26.628] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    26.628] (==) Automatically adding devices
[    26.628] (==) Automatically enabling devices
[    26.628] (==) Automatically adding GPU devices
[    26.628] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.628]    Entry deleted from font path.
[    26.628] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    26.628]    Entry deleted from font path.
[    26.628] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.628]    Entry deleted from font path.
[    26.628] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    26.628]    Entry deleted from font path.
[    26.628] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    26.628]    Entry deleted from font path.
[    26.628] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.628]    Entry deleted from font path.
[    26.628] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        built-ins
[    26.628] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.628] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.628] (II) Loader magic: 0xb77f46c0
[    26.628] (II) Module ABI versions:
[    26.628]    X.Org ANSI C Emulation: 0.4
[    26.628]    X.Org Video Driver: 15.0
[    26.628]    X.Org XInput driver : 20.0
[    26.628]    X.Org Server Extension : 8.0
[    26.629] (II) xfree86: Adding drm device (/dev/dri/card0)
[    26.630] (--) PCI:*(0:0:2:0) 8086:2592:1028:0182 rev 3, Mem @ 0xdff00000/524288, 0xc0000000/268435456, 0xdfec0000/262144, I/O @ 0x0000ec38/8
[    26.630] (--) PCI: (0:0:2:1) 8086:2792:1028:0182 rev 3, Mem @ 0xdff80000/524288
[    26.630] Initializing built-in extension Generic Event Extension
[    26.630] Initializing built-in extension SHAPE
[    26.630] Initializing built-in extension MIT-SHM
[    26.630] Initializing built-in extension XInputExtension
[    26.630] Initializing built-in extension XTEST
[    26.630] Initializing built-in extension BIG-REQUESTS
[    26.630] Initializing built-in extension SYNC
[    26.630] Initializing built-in extension XKEYBOARD
[    26.630] Initializing built-in extension XC-MISC
[    26.630] Initializing built-in extension SECURITY
[    26.630] Initializing built-in extension XINERAMA
[    26.630] Initializing built-in extension XFIXES
[    26.630] Initializing built-in extension RENDER
[    26.630] Initializing built-in extension RANDR
[    26.630] Initializing built-in extension COMPOSITE
[    26.630] Initializing built-in extension DAMAGE
[    26.630] Initializing built-in extension MIT-SCREEN-SAVER
[    26.630] Initializing built-in extension DOUBLE-BUFFER
[    26.630] Initializing built-in extension RECORD
[    26.630] Initializing built-in extension DPMS
[    26.630] Initializing built-in extension Present
[    26.630] Initializing built-in extension DRI3
[    26.630] Initializing built-in extension X-Resource
[    26.630] Initializing built-in extension XVideo
[    26.630] Initializing built-in extension XVideo-MotionCompensation
[    26.631] Initializing built-in extension SELinux
[    26.631] Initializing built-in extension XFree86-VidModeExtension
[    26.631] Initializing built-in extension XFree86-DGA
[    26.631] Initializing built-in extension XFree86-DRI
[    26.631] Initializing built-in extension DRI2
[    26.631] (II) LoadModule: "glx"
[    26.656] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    26.758] (II) Module glx: vendor="X.Org Foundation"
[    26.759]    compiled for 1.15.1, module version = 1.0.0
[    26.759]    ABI class: X.Org Server Extension, version 8.0
[    26.759] (==) AIGLX enabled
[    26.759] Loading extension GLX
[    26.759] (==) Matched intel as autoconfigured driver 0
[    26.759] (==) Matched intel as autoconfigured driver 1
[    26.759] (==) Matched modesetting as autoconfigured driver 2
[    26.759] (==) Matched fbdev as autoconfigured driver 3
[    26.759] (==) Matched vesa as autoconfigured driver 4
[    26.759] (==) Assigned the driver to the xf86ConfigLayout
[    26.759] (II) LoadModule: "intel"
[    26.759] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    26.796] (II) Module intel: vendor="X.Org Foundation"
[    26.796]    compiled for 1.15.0, module version = 2.99.910
[    26.796]    Module class: X.Org Video Driver
[    26.796]    ABI class: X.Org Video Driver, version 15.0
[    26.796] (II) LoadModule: "modesetting"
[    26.797] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    26.797] (II) Module modesetting: vendor="X.Org Foundation"
[    26.797]    compiled for 1.15.0, module version = 0.8.1
[    26.797]    Module class: X.Org Video Driver
[    26.797]    ABI class: X.Org Video Driver, version 15.0
[    26.797] (II) LoadModule: "fbdev"
[    26.797] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.798] (II) Module fbdev: vendor="X.Org Foundation"
[    26.798]    compiled for 1.15.0, module version = 0.4.4
[    26.798]    Module class: X.Org Video Driver
[    26.798]    ABI class: X.Org Video Driver, version 15.0
[    26.798] (II) LoadModule: "vesa"
[    26.798] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.798] (II) Module vesa: vendor="X.Org Foundation"
[    26.798]    compiled for 1.15.0, module version = 2.3.3
[    26.798]    Module class: X.Org Video Driver
[    26.798]    ABI class: X.Org Video Driver, version 15.0
[    26.798] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    26.799] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[    26.799] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[    26.799] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[    26.799] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    26.799] (II) FBDEV: driver for framebuffer: fbdev
[    26.799] (II) VESA: driver for VESA chipsets: vesa
[    26.799] (++) using VT number 7
[    26.799] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1 (Timo Aaltonen <tjaalton@ubuntu.com>)
[    26.799] (WW) Falling back to old probe method for modesetting
[    26.799] (WW) Falling back to old probe method for fbdev
[    26.799] (II) Loading sub module "fbdevhw"
[    26.799] (II) LoadModule: "fbdevhw"
[    26.799] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.800] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.800]    compiled for 1.15.1, module version = 0.0.2
[    26.800]    ABI class: X.Org Video Driver, version 15.0
[    26.800] (WW) Falling back to old probe method for vesa
[    26.800] (--) intel(0): Integrated Graphics Chipset: Intel(R) 915GM
[    26.800] (--) intel(0): CPU: x86, sse2
[    26.800] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    26.800] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    26.800] (==) intel(0): RGB weight 888
[    26.800] (==) intel(0): Default visual is TrueColor
[    26.801] (**) intel(0): Framebuffer tiled
[    26.801] (**) intel(0): Pixmaps tiled
[    26.801] (**) intel(0): "Tear free" disabled
[    26.801] (**) intel(0): Forcing per-crtc-pixmaps? no
[    26.801] (II) intel(0): Output LVDS1 has no monitor section
[    26.801] (--) intel(0): found backlight control interface dell_backlight (type 'platform')
[    26.801] (II) intel(0): Output VGA1 has no monitor section
[    26.801] (II) intel(0): Output DVI1 has no monitor section
[    26.801] (II) intel(0): Output TV1 has no monitor section
[    26.801] (II) intel(0): Output VIRTUAL1 has no monitor section
[    26.801] (--) intel(0): Output LVDS1 using initial mode 1400x1050 on pipe 1
[    26.801] (--) intel(0): Output DVI1 using initial mode 1920x1080 on pipe 0
[    26.802] (==) intel(0): DPI set to (96, 96)
[    26.802] (II) Loading sub module "dri2"
[    26.802] (II) LoadModule: "dri2"
[    26.802] (II) Module "dri2" already built-in
[    26.802] (II) UnloadModule: "modesetting"
[    26.802] (II) Unloading modesetting
[    26.802] (II) UnloadModule: "fbdev"
[    26.802] (II) Unloading fbdev
[    26.802] (II) UnloadSubModule: "fbdevhw"
[    26.802] (II) Unloading fbdevhw
[    26.802] (II) UnloadModule: "vesa"
[    26.802] (II) Unloading vesa
[    26.802] (==) Depth 24 pixmap format is 32 bpp
[    26.802] (II) intel(0): SNA initialized with Alviso (gen3) backend
[    26.802] (==) intel(0): Backing store enabled
[    26.802] (==) intel(0): Silken mouse enabled
[    26.802] (II) intel(0): HW Cursor enabled
[    26.802] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    26.802] (==) intel(0): DPMS enabled
[    26.802] (II) intel(0): [DRI2] Setup complete
[    26.802] (II) intel(0): [DRI2]   DRI driver: i915
[    26.802] (II) intel(0): [DRI2]   VDPAU driver: i915
[    26.802] (II) intel(0): direct rendering: DRI2 Enabled
[    26.802] (==) intel(0): hotplug detection: "enabled"
[    26.802] (--) RandR disabled
[    26.813] (II) SELinux: Disabled on system
[    26.819] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    26.819] (II) AIGLX: enabled GLX_ARB_create_context
[    26.819] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    26.819] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    26.819] (II) AIGLX: enabled GLX_INTEL_swap_event
[    26.819] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    26.819] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    26.819] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    26.819] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    26.819] (II) AIGLX: Loaded and initialized i915
[    26.819] (II) GLX: Initialized DRI2 GL provider for screen 0
[    26.841] (II) intel(0): switch to mode 1920x1080@60.0 on DVI1 using pipe 0, position (0, 0), rotation normal, reflection none
[    26.864] (II) intel(0): switch to mode 1400x1050@60.0 on LVDS1 using pipe 1, position (0, 0), rotation normal, reflection none
[    26.890] (II) intel(0): Setting screen physical size to 507 x 285
[    26.901] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.905] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    26.905] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.905] (II) LoadModule: "evdev"
[    26.906] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.929] (II) Module evdev: vendor="X.Org Foundation"
[    26.929]    compiled for 1.15.0, module version = 2.8.2
[    26.929]    Module class: X.Org XInput Driver
[    26.929]    ABI class: X.Org XInput driver, version 20.0
[    26.929] (II) Using input driver 'evdev' for 'Video Bus'
[    26.929] (**) Video Bus: always reports core events
[    26.929] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    26.929] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    26.930] (--) evdev: Video Bus: Found keys
[    26.930] (II) evdev: Video Bus: Configuring as keyboard
[    26.930] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input7/event6"
[    26.930] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[    26.930] (**) Option "xkb_rules" "evdev"
[    26.930] (**) Option "xkb_model" "pc105"
[    26.930] (**) Option "xkb_layout" "us"
[    26.930] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.930] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.930] (II) Using input driver 'evdev' for 'Power Button'
[    26.930] (**) Power Button: always reports core events
[    26.930] (**) evdev: Power Button: Device: "/dev/input/event1"
[    26.930] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.930] (--) evdev: Power Button: Found keys
[    26.930] (II) evdev: Power Button: Configuring as keyboard
[    26.930] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    26.930] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    26.930] (**) Option "xkb_rules" "evdev"
[    26.931] (**) Option "xkb_model" "pc105"
[    26.931] (**) Option "xkb_layout" "us"
[    26.931] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    26.931] (II) No input driver specified, ignoring this device.
[    26.931] (II) This device may have been added with another device file.
[    26.932] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    26.932] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    26.932] (II) Using input driver 'evdev' for 'Sleep Button'
[    26.932] (**) Sleep Button: always reports core events
[    26.932] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    26.932] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    26.932] (--) evdev: Sleep Button: Found keys
[    26.932] (II) evdev: Sleep Button: Configuring as keyboard
[    26.932] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    26.932] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    26.932] (**) Option "xkb_rules" "evdev"
[    26.932] (**) Option "xkb_model" "pc105"
[    26.932] (**) Option "xkb_layout" "us"
[    26.932] (II) config/udev: Adding drm device (/dev/dri/card0)
[    26.932] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    26.933] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    26.933] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    26.933] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    26.933] (**) AT Translated Set 2 keyboard: always reports core events
[    26.933] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    26.933] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    26.933] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    26.933] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    26.933] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    26.933] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    26.933] (**) Option "xkb_rules" "evdev"
[    26.933] (**) Option "xkb_model" "pc105"
[    26.933] (**) Option "xkb_layout" "us"
[    26.933] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event5)
[    26.933] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
[    26.933] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
[    26.934] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "Default clickpad buttons"
[    26.934] (II) LoadModule: "synaptics"
[    26.934] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    26.934] (II) Module synaptics: vendor="X.Org Foundation"
[    26.934]    compiled for 1.15.0, module version = 1.7.4
[    26.934]    Module class: X.Org XInput Driver
[    26.934]    ABI class: X.Org XInput driver, version 20.0
[    26.934] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[    26.934] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    26.934] (**) Option "Device" "/dev/input/event5"
[    26.934] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 1023 (res 0)
[    26.934] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 767 (res 0)
[    26.934] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[    26.934] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: device does not report finger width.
[    26.934] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle
[    26.934] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: Vendor 0x2 Product 0x8
[    26.934] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: invalid finger width range.  defaulting to 0 - 15
[    26.934] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    26.934] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    26.934] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    26.934] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD, id 10)
[    26.934] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    26.934] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MaxSpeed is now 1.75
[    26.934] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) AccelFactor is now 0.156
[    26.935] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[    26.935] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 1
[    26.935] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[    26.935] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[    26.935] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    26.935] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse1)
[    26.935] (**) AlpsPS/2 ALPS DualPoint TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    26.935] (II) config/udev: Adding input device DualPoint Stick (/dev/input/event4)
[    26.935] (**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
[    26.935] (**) DualPoint Stick: Applying InputClass "trackpoint catchall"
[    26.935] (II) Using input driver 'evdev' for 'DualPoint Stick'
[    26.935] (**) DualPoint Stick: always reports core events
[    26.935] (**) evdev: DualPoint Stick: Device: "/dev/input/event4"
[    26.935] (--) evdev: DualPoint Stick: Vendor 0x2 Product 0x8
[    26.935] (--) evdev: DualPoint Stick: Found 3 mouse buttons
[    26.935] (--) evdev: DualPoint Stick: Found relative axes
[    26.935] (--) evdev: DualPoint Stick: Found x and y relative axes
[    26.935] (II) evdev: DualPoint Stick: Configuring as mouse
[    26.935] (**) Option "Emulate3Buttons" "true"
[    26.935] (**) Option "EmulateWheel" "true"
[    26.936] (**) Option "EmulateWheelButton" "2"
[    26.935] (**) Option "EmulateWheel" "true"
[    26.936] (**) Option "EmulateWheelButton" "2"
[    26.936] (**) Option "YAxisMapping" "4 5"
[    26.936] (**) evdev: DualPoint Stick: YAxisMapping: buttons 4 and 5
[    26.936] (**) Option "XAxisMapping" "6 7"
[    26.936] (**) evdev: DualPoint Stick: XAxisMapping: buttons 6 and 7
[    26.936] (**) evdev: DualPoint Stick: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.936] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event4"
[    26.936] (II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE, id 11)
[    26.936] (II) evdev: DualPoint Stick: initialized for relative axes.
[    26.936] (**) DualPoint Stick: (accel) keeping acceleration scheme 1
[    26.936] (**) DualPoint Stick: (accel) acceleration profile 0
[    26.936] (**) DualPoint Stick: (accel) acceleration factor: 2.000
[    26.936] (**) DualPoint Stick: (accel) acceleration threshold: 4
[    26.936] (II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse0)
[    26.936] (II) No input driver specified, ignoring this device.
[    26.936] (II) This device may have been added with another device file.
[    30.977] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    35.944] (II) intel(0): EDID vendor "SEC", prod id 13392
[    35.944] (II) intel(0): Printing DDC gathered Modelines:
[    35.944] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1055 1066 -hsync -vsync (64.0 kHz eP)
[    35.944] (II) intel(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1055 1066 -hsync -vsync (53.3 kHz e)
[    37.258] (II) intel(0): resizing framebuffer to 1360x765
[    37.401] (II) intel(0): switch to mode 1360x765@59.8 on DVI1 using pipe 0, position (0, 0), rotation normal, reflection none
[   189.242] (II) AIGLX: Suspending AIGLX clients for VT switch

```
**Major things I saw:**

```
[    26.627] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.628] (==) No Layout section.  Using the first Screen section.
[    26.628] (==) No screen section available. Using defaults.
[    26.628] (**) |-->Screen "Default Screen Section" (0)
[    26.628] (**) |   |-->Monitor "<default monitor>"
[    26.628] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
```In fact, no [FONT=courier new]/usr/share/X11/xorg.conf.d[/FONT] exists, so I'm not suprised that it's using the default. It switches to the correct resolution at the end of the log, so I'm not concerned.

```
[    26.801] (II) intel(0): Output LVDS1 has no monitor section
[    26.801] (--) intel(0): found backlight control interface dell_backlight (type 'platform')
[    26.801] (II) intel(0): Output VGA1 has no monitor section
[    26.801] (II) intel(0): Output DVI1 has no monitor section
[    26.801] (II) intel(0): Output TV1 has no monitor section
[    26.801] (II) intel(0): Output VIRTUAL1 has no monitor section
[    26.801] (--) intel(0): Output LVDS1 using initial mode 1400x1050 on pipe 1
[    26.801] (--) intel(0): Output DVI1 using initial mode 1920x1080 on pipe 0
[    26.802] (==) intel(0): DPI set to (96, 96)
```LVDS1 is the laptop screen and DVI1 is the TV. The others aren't plugged in. It then gets ready to set the two real ones to their default resolutions.


```
[    26.841] (II) intel(0): switch to mode 1920x1080@60.0 on DVI1 using pipe 0, position (0, 0), rotation normal, reflection none
[    26.864] (II) intel(0): switch to mode 1400x1050@60.0 on LVDS1 using pipe 1, position (0, 0), rotation normal, reflection none
[    26.890] (II) intel(0): Setting screen physical size to 507 x 285
```It sets the two monitors to their default resolutions. This isn't the native resolution for my TV, and sincs it's in monitor mode it just crops a window of it instead of scaling it down to 1360x768 like it does for my BD player. I think my TV responded to this change (a 1080p message on screen). Also, my TV shifts the picture over 3 pixels to the right, so I have a script that runs at login that adds a [FONT=courier new]1360x765_60.00[/FONT] to [FONT=courier new]xrandr[/FONT] then turns off the laptop monitor.


```
[    35.944] (II) intel(0): EDID vendor "SEC", prod id 13392
[    35.944] (II) intel(0): Printing DDC gathered Modelines:
[    35.944] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1055 1066 -hsync -vsync (64.0 kHz eP)
[    35.944] (II) intel(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1055 1066 -hsync -vsync (53.3 kHz e)
[    37.258] (II) intel(0): resizing framebuffer to 1360x765
[    37.401] (II) intel(0): switch to mode 1360x765@59.8 on DVI1 using pipe 0, position (0, 0), rotation normal, reflection none
[   189.242] (II) AIGLX: Suspending AIGLX clients for VT switch
```This appears much, much later into the log (after the touchpad & etc. has been enabled). My TV does not respond to this resolution change. This is the last thing in the log.
[HR][/HR]
[FONT=courier new]nano /var/log/pm-suspend.log:[/FONT]
```
Mon Jul 14 20:47:52 CDT 2014: performing suspend
Mon Jul 14 20:49:10 CDT 2014: Awake.
Mon Jul 14 20:49:10 CDT 2014: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level      = off
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

Mon Jul 14 20:49:10 CDT 2014: Finished.

```



[COLOR=#ff0000]***None of the logs here explain the problem clearly to me!***[/COLOR] Any help is appreceiated.

---

### Post by P_THE_AWESOME on 2014-07-15
Could it be related to my graphics drivers? I am using the [Intel Graphics Installer 1.0.5 for Linux 14.04 32-bit]("https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.5-linux"). I have an Intel Integrated Graphics Chipset 915GM. I definitely have the right driver since I can successfully run [FONT=courier new]glamrk2-es2[/FONT].

If I have to remove it, I'm not sure how to remove the actual drivers since it just adds apt repositories and is unlisted in Additional Hardware. I also regurely use XBMC to playback HD video, so it will probably hit performance pretty hard.

---

### Post by bapoumba on 2014-07-16
To note, I also have intel graphics and do not use any additional driver :
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```
```
lshw -c video
WARNING: you should run this program as super-user.
  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:d0100000-d017ffff ioport:1800(size=8) memory:b0000000-bfffffff memory:d0200000-d023ffff
```

```
modinfo i915
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/gpu/drm/i915/i915.ko
license:        GPL and additional rights
description:    Intel Graphics
author:         Tungsten Graphics, Inc.
license:        GPL and additional rights
srcversion:     FAEA6E75CFCF86C7E4D0A4B
<snipped aliases>
depends:        drm_kms_helper,drm,video,i2c-algo-bit
intree:         Y
vermagic:       3.13.0-30-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        6C:4C:CC:D2:3E:C5:78:FE:E9:B9:E0:C7:E2:67:0C:91:F2:E0:A0:AC
sig_hashalgo:   sha512
parm:           invert_brightness:Invert backlight brightness (-1 force normal, 0 machine defaults, 1 force inversion), please report PCI device ID, subsystem vendor and subsystem device ID to dri-devel@lists.freedesktop.org, if your machine needs it. It will then be included in an upcoming module version. (int)
parm:           modeset:Use kernel modesetting [KMS] (0=DRM_I915_KMS from .config, 1=on, -1=force vga console preference [default]) (int)
parm:           fbpercrtc:int
parm:           panel_ignore_lid:Override lid status (0=autodetect, 1=autodetect disabled [default], -1=force lid closed, -2=force lid open) (int)
parm:           powersave:Enable powersavings, fbc, downclocking, etc. (default: true) (int)
parm:           semaphores:Use semaphores for inter-ring sync (default: -1 (use per-chip defaults)) (int)
parm:           i915_enable_rc6:Enable power-saving render C-state 6. Different stages can be selected via bitmask values (0 = disable; 1 = enable rc6; 2 = enable deep rc6; 4 = enable deepest rc6). For example, 3 would enable rc6 and deep rc6, and 7 would enable everything. default: -1 (use per-chip default) (int)
parm:           i915_enable_fbc:Enable frame buffer compression for power savings (default: -1 (use per-chip default)) (int)
parm:           lvds_downclock:Use panel (LVDS/eDP) downclocking for power savings (default: false) (int)
parm:           lvds_channel_mode:Specify LVDS channel mode (0=probe BIOS [default], 1=single-channel, 2=dual-channel) (int)
parm:           lvds_use_ssc:Use Spread Spectrum Clock with panels [LVDS/eDP] (default: auto from VBT) (int)
parm:           vbt_sdvo_panel_type:Override/Ignore selection of SDVO panel mode in the VBT (-2=ignore, -1=auto [default], index in VBT BIOS table) (int)
parm:           reset:Attempt GPU resets (default: true) (bool)
parm:           enable_hangcheck:Periodically check GPU activity for detecting hangs. WARNING: Disabling this can cause system wide hangs. (default: true) (bool)
parm:           i915_enable_ppgtt:Enable PPGTT (default: true) (int)
parm:           enable_psr:Enable PSR (default: false) (int)
parm:           preliminary_hw_support:Enable preliminary hardware support. (int)
parm:           disable_power_well:Disable the power well when possible (default: true) (int)
parm:           enable_ips:Enable IPS (default: true) (int)
parm:           fastboot:Try to skip unnecessary mode sets at boot time (default: false) (bool)
parm:           enable_pc8:Enable support for low power package C states (PC8+) (default: true) (int)
parm:           pc8_timeout:Number of msecs of idleness required to enter PC8+ (default: 5000) (int)
parm:           prefault_disable:Disable page prefaulting for pread/pwrite/reloc (default:false). For developers only. (bool)

```

---

