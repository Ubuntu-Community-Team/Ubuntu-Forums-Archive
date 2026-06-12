---
title: "Xubuntu/Voyager 12.04 32bit Locks up"
date: 2013-06-06
forum: General Help
---

### Post by UltimateCat on 2013-06-06
;)Hi:

I just installed Voyager 12.04 32bit on my Toshibia Satelite laptop. This distro is Xubuntu based; BTW--
[http://voyager.legtux.org/index.php/live-voyager-12-04-lts/](http://voyager.legtux.org/index.php/live-voyager-12-04-lts/)

Sometimes it boots up to Voyager right away and sometimes it has to be re-booted and I only get the "Toshibia" Screen and it stays black and have to do
a hard shut down and re-boot again. The laptop won't run on battery without the adapter plugged in.  In fact as soon as I disconnect the adapter the laptop shuts down.

I spent the last 2 days taking apart the laptop. I replaced the fan (the old one was very nasty) removed the heatsink cleaned it up and put a fresh layer of compound (thermal paste) on the processor.

When the OS is up and running the DE, Firefox or whatever application is open it just lock's up and the touchpad and mouse become un-responsive.
Sometimes the laptop runs about 15 min's before it locks up--


Here's the var/log: if that helps-

```
[FONT=Verdana][    14.453] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    14.453] X Protocol Version 11, Revision 0
[    14.453] Build Operating System: Linux 2.6.42-23-generic i686 Ubuntu
[    14.453] Current Operating System: Linux sifubill-Satellite-A205  3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 i686
[    14.453] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=08f504a7-4a4c-4440-96ff-b38fc3e851ca ro quiet splash vt.handoff=7
[    14.454] Build Date: 20 April 2012  05:12:21AM
[    14.454] xorg-server 2:1.11.4-0ubuntu10.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    14.454] Current version of pixman: 0.24.4
[    14.454]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    14.454] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.454] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun  6 19:49:49 2013
[    14.464] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.465] (==) No Layout section.  Using the first Screen section.
[    14.465] (==) No screen section available. Using defaults.
[    14.465] (**) |-->Screen "Default Screen Section" (0)
[    14.465] (**) |   |-->Monitor "<default monitor>"
[    14.465] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    14.465] (==) Automatically adding devices
[    14.465] (==) Automatically enabling devices
[    14.465] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.465]     Entry deleted from font path.
[    14.465] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.465]     Entry deleted from font path.
[    14.465] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.465]     Entry deleted from font path.
[    14.465] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.465]     Entry deleted from font path.
[    14.465] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.465]     Entry deleted from font path.
[    14.465] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    14.465]     Entry deleted from font path.
[    14.466] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    14.466] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.466] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.466] (II) Loader magic: 0x7a45a0
[    14.466] (II) Module ABI versions:
[    14.466]     X.Org ANSI C Emulation: 0.4
[    14.466]     X.Org Video Driver: 11.0
[    14.466]     X.Org XInput driver : 16.0
[    14.466]     X.Org Server Extension : 6.0
[    14.467] (--) PCI:*(0:0:2:0) 8086:2a02:1179:ff10 rev 3, Mem @ 0xf5000000/1048576, 0xd0000000/268435456, I/O @ 0x00001800/8
[    14.467] (--) PCI: (0:0:2:1) 8086:2a03:1179:ff10 rev 3, Mem @ 0xf5100000/1048576
[    14.467] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.467] (II) LoadModule: "extmod"
[    14.504] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.505] (II) Module extmod: vendor="X.Org Foundation"
[    14.505]     compiled for 1.11.3, module version = 1.0.0
[    14.505]     Module class: X.Org Server Extension
[    14.505]     ABI class: X.Org Server Extension, version 6.0
[    14.505] (II) Loading extension MIT-SCREEN-SAVER
[    14.505] (II) Loading extension XFree86-VidModeExtension
[    14.505] (II) Loading extension XFree86-DGA
[    14.505] (II) Loading extension DPMS
[    14.505] (II) Loading extension XVideo
[    14.505] (II) Loading extension XVideo-MotionCompensation
[    14.505] (II) Loading extension X-Resource
[    14.505] (II) LoadModule: "dbe"
[    14.505] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.505] (II) Module dbe: vendor="X.Org Foundation"
[    14.505]     compiled for 1.11.3, module version = 1.0.0
[    14.505]     Module class: X.Org Server Extension
[    14.505]     ABI class: X.Org Server Extension, version 6.0
[    14.505] (II) Loading extension DOUBLE-BUFFER
[    14.505] (II) LoadModule: "glx"
[    14.506] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.506] (II) Module glx: vendor="X.Org Foundation"
[    14.506]     compiled for 1.11.3, module version = 1.0.0
[    14.506]     ABI class: X.Org Server Extension, version 6.0
[    14.506] (==) AIGLX enabled
[    14.506] (II) Loading extension GLX
[    14.506] (II) LoadModule: "record"
[    14.507] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.507] (II) Module record: vendor="X.Org Foundation"
[    14.507]     compiled for 1.11.3, module version = 1.13.0
[    14.507]     Module class: X.Org Server Extension
[    14.507]     ABI class: X.Org Server Extension, version 6.0
[    14.507] (II) Loading extension RECORD
[    14.507] (II) LoadModule: "dri"
[    14.507] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.507] (II) Module dri: vendor="X.Org Foundation"
[    14.507]     compiled for 1.11.3, module version = 1.0.0
[    14.507]     ABI class: X.Org Server Extension, version 6.0
[    14.507] (II) Loading extension XFree86-DRI
[    14.508] (II) LoadModule: "dri2"
[    14.508] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.508] (II) Module dri2: vendor="X.Org Foundation"
[    14.508]     compiled for 1.11.3, module version = 1.2.0
[    14.508]     ABI class: X.Org Server Extension, version 6.0
[    14.508] (II) Loading extension DRI2
[    14.508] (==) Matched intel as autoconfigured driver 0
[    14.508] (==) Matched vesa as autoconfigured driver 1
[    14.508] (==) Matched fbdev as autoconfigured driver 2
[    14.508] (==) Assigned the driver to the xf86ConfigLayout
[    14.508] (II) LoadModule: "intel"
[    14.509] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    14.509] (II) Module intel: vendor="X.Org Foundation"
[    14.509]     compiled for 1.11.3, module version = 2.17.0
[    14.509]     Module class: X.Org Video Driver
[    14.509]     ABI class: X.Org Video Driver, version 11.0
[    14.509] (II) LoadModule: "vesa"
[    14.509] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.510] (II) Module vesa: vendor="X.Org Foundation"
[    14.510]     compiled for 1.11.3, module version = 2.3.0
[    14.510]     Module class: X.Org Video Driver
[    14.510]     ABI class: X.Org Video Driver, version 11.0
[    14.510] (II) LoadModule: "fbdev"
[    14.510] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.510] (II) Module fbdev: vendor="X.Org Foundation"
[    14.510]     compiled for 1.11.3, module version = 0.4.2
[    14.510]     ABI class: X.Org Video Driver, version 11.0
[    14.510] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    14.511] (II) VESA: driver for VESA chipsets: vesa
[    14.511] (II) FBDEV: driver for framebuffer: fbdev
[    14.511] (++) using VT number 7

[    14.513] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    14.514] (WW) Falling back to old probe method for vesa
[    14.514] (WW) Falling back to old probe method for fbdev
[    14.514] (II) Loading sub module "fbdevhw"
[    14.514] (II) LoadModule: "fbdevhw"
[    14.514] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.514] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.514]     compiled for 1.11.3, module version = 0.0.2
[    14.514]     ABI class: X.Org Video Driver, version 11.0
[    14.514] drmOpenDevice: node name is /dev/dri/card0
[    14.514] drmOpenDevice: open result is 9, (OK)
[    14.514] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    14.514] drmOpenDevice: node name is /dev/dri/card0
[    14.514] drmOpenDevice: open result is 9, (OK)
[    14.515] drmOpenByBusid: drmOpenMinor returns 9
[    14.515] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    14.515] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    14.515] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    14.515] (==) intel(0): RGB weight 888
[    14.515] (==) intel(0): Default visual is TrueColor
[    14.515] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    14.515] (--) intel(0): Chipset: "965GM"
[    14.515] (**) intel(0): Relaxed fencing enabled
[    14.515] (**) intel(0): Wait on SwapBuffers? enabled
[    14.515] (**) intel(0): Triple buffering? enabled
[    14.515] (**) intel(0): Framebuffer tiled
[    14.515] (**) intel(0): Pixmaps tiled
[    14.515] (**) intel(0): 3D buffers tiled
[    14.515] (**) intel(0): SwapBuffers wait enabled
[    14.515] (==) intel(0): video overlay key set to 0x101fe
[    14.515] (II) intel(0): Output LVDS1 has no monitor section
[    14.516] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    14.532] (II) intel(0): Output VGA1 has no monitor section
[    14.793] (II) intel(0): Output TV1 has no monitor section
[    14.793] (II) intel(0): EDID for output LVDS1
[    14.793] (II) intel(0): Manufacturer: SEC  Model: 3645  Serial#: 0
[    14.793] (II) intel(0): Year: 2005  Week: 0
[    14.793] (II) intel(0): EDID Version: 1.3
[    14.793] (II) intel(0): Digital Display Input
[    14.793] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    14.793] (II) intel(0): Gamma: 2.20
[    14.793] (II) intel(0): No DPMS capabilities specified
[    14.793] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    14.793] (II) intel(0): First detailed timing is preferred mode
[    14.793] (II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[    14.793] (II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    14.793] (II) intel(0): Manufacturer's mask: 0
[    14.793] (II) intel(0): Supported detailed timing:
[    14.793] (II) intel(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
[    14.793] (II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
[    14.793] (II) intel(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
[    14.793] (II) intel(0): Unknown vendor-specific block f
[    14.793] (II) intel(0):  SAMSUNG
[    14.793] (II) intel(0):  LTN154X3-L05
[    14.793] (II) intel(0): EDID (in hex):
[    14.793] (II) intel(0):     00ffffffffffff004ca3453600000000
[    14.793] (II) intel(0):     000f0103802115780a87f594574f8c27
[    14.793] (II) intel(0):     27505400000001010101010101010101
[    14.793] (II) intel(0):     010101010101ee1a0080502010301030
[    14.793] (II) intel(0):     13004bcf100000190000000f00000000
[    14.794] (II) intel(0):     00000000002387026400000000fe0053
[    14.794] (II) intel(0):     414d53554e470a2020202020000000fe
[    14.794] (II) intel(0):     004c544e31353458332d4c30350a0061
[    14.794] (II) intel(0): EDID vendor "SEC", prod id 13893
[    14.794] (II) intel(0): Printing DDC gathered Modelines:
[    14.794] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
[    14.794] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    14.794] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    14.794] (II) intel(0): Printing probed modes for output LVDS1
[    14.794] (II) intel(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
[    14.794] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.794] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.794] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    14.794] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.816] (II) intel(0): EDID for output VGA1
[    15.077] (II) intel(0): EDID for output TV1
[    15.077] (II) intel(0): Output LVDS1 connected
[    15.077] (II) intel(0): Output VGA1 disconnected
[    15.077] (II) intel(0): Output TV1 disconnected
[    15.077] (II) intel(0): Using exact sizes for initial modes
[    15.077] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    15.077] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    15.077] (II) intel(0): Kernel page flipping support detected, enabling
[    15.077] (**) intel(0): Display dimensions: (330, 210) mm
[    15.077] (**) intel(0): DPI set to (98, 96)
[    15.077] (II) Loading sub module "fb"
[    15.077] (II) LoadModule: "fb"
[    15.078] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.078] (II) Module fb: vendor="X.Org Foundation"
[    15.078]     compiled for 1.11.3, module version = 1.0.0
[    15.078]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.078] (II) Loading sub module "dri2"
[    15.078] (II) LoadModule: "dri2"
[    15.078] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.078] (II) Module dri2: vendor="X.Org Foundation"
[    15.078]     compiled for 1.11.3, module version = 1.2.0
[    15.078]     ABI class: X.Org Server Extension, version 6.0
[    15.078] (II) UnloadModule: "vesa"
[    15.078] (II) Unloading vesa
[    15.078] (II) UnloadModule: "fbdev"
[    15.078] (II) Unloading fbdev
[    15.078] (II) UnloadModule: "fbdevhw"
[    15.078] (II) Unloading fbdevhw
[    15.078] (==) Depth 24 pixmap format is 32 bpp
[    15.079] (II) intel(0): [DRI2] Setup complete
[    15.079] (II) intel(0): [DRI2]   DRI driver: i965
[    15.079] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[    15.095] (II) UXA(0): Driver registered support for the following operations:
[    15.095] (II)         solid
[    15.095] (II)         copy
[    15.095] (II)         composite (RENDER acceleration)
[    15.095] (II)         put_image
[    15.096] (II)         get_image
[    15.096] (==) intel(0): Backing store disabled
[    15.096] (==) intel(0): Silken mouse enabled
[    15.096] (II) intel(0): Initializing HW Cursor
[    15.120] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    15.122] (==) intel(0): DPMS enabled
[    15.122] (==) intel(0): Intel XvMC decoder enabled
[    15.122] (II) intel(0): Set up textured video
[    15.123] (II) intel(0): Set up overlay video
[    15.123] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    15.123] (II) intel(0): direct rendering: DRI2 Enabled
[    15.123] (==) intel(0): hotplug detection: "enabled"
[    15.123] (--) RandR disabled
[    15.123] (II) Initializing built-in extension Generic Event Extension
[    15.123] (II) Initializing built-in extension SHAPE
[    15.123] (II) Initializing built-in extension MIT-SHM
[    15.123] (II) Initializing built-in extension XInputExtension
[    15.123] (II) Initializing built-in extension XTEST
[    15.123] (II) Initializing built-in extension BIG-REQUESTS
[    15.123] (II) Initializing built-in extension SYNC
[    15.123] (II) Initializing built-in extension XKEYBOARD
[    15.123] (II) Initializing built-in extension XC-MISC
[    15.123] (II) Initializing built-in extension SECURITY
[    15.123] (II) Initializing built-in extension XINERAMA
[    15.123] (II) Initializing built-in extension XFIXES
[    15.123] (II) Initializing built-in extension RENDER
[    15.123] (II) Initializing built-in extension RANDR
[    15.123] (II) Initializing built-in extension COMPOSITE
[    15.123] (II) Initializing built-in extension DAMAGE
[    15.142] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    15.142] (II) AIGLX: enabled GLX_INTEL_swap_event
[    15.142] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    15.142] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    15.142] (II) AIGLX: Loaded and initialized i965
[    15.142] (II) GLX: Initialized DRI2 GL provider for screen 0
[    15.143] (II) intel(0): Setting screen physical size to 338 x 211
[    15.156] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.161] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    15.161] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.161] (II) LoadModule: "evdev"
[    15.161] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.162] (II) Module evdev: vendor="X.Org Foundation"
[    15.162]     compiled for 1.11.3, module version = 2.7.0
[    15.162]     Module class: X.Org XInput Driver
[    15.162]     ABI class: X.Org XInput driver, version 16.0
[    15.162] (II) Using input driver 'evdev' for 'Power Button'
[    15.162] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.162] (**) Power Button: always reports core events
[    15.162] (**) evdev: Power Button: Device: "/dev/input/event2"
[    15.162] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.162] (--) evdev: Power Button: Found keys
[    15.162] (II) evdev: Power Button: Configuring as keyboard
[    15.162] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    15.162] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    15.162] (**) Option "xkb_rules" "evdev"
[    15.162] (**) Option "xkb_model" "pc105"
[    15.162] (**) Option "xkb_layout" "us"
[    15.163] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    15.163] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    15.163] (II) Using input driver 'evdev' for 'Video Bus'
[    15.163] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.163] (**) Video Bus: always reports core events
[    15.163] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    15.164] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    15.164] (--) evdev: Video Bus: Found keys
[    15.164] (II) evdev: Video Bus: Configuring as keyboard
[    15.164] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6/event6"
[    15.164] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    15.164] (**) Option "xkb_rules" "evdev"
[    15.164] (**) Option "xkb_model" "pc105"
[    15.164] (**) Option "xkb_layout" "us"
[    15.165] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    15.165] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.165] (II) Using input driver 'evdev' for 'Power Button'
[    15.165] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.165] (**) Power Button: always reports core events
[    15.165] (**) evdev: Power Button: Device: "/dev/input/event1"
[    15.165] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.165] (--) evdev: Power Button: Found keys
[    15.165] (II) evdev: Power Button: Configuring as keyboard
[    15.165] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    15.165] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    15.165] (**) Option "xkb_rules" "evdev"
[    15.165] (**) Option "xkb_model" "pc105"
[    15.165] (**) Option "xkb_layout" "us"
[    15.166] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    15.166] (II) No input driver specified, ignoring this device.
[    15.166] (II) This device may have been added with another device file.
[    15.166] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event7)
[    15.166] (II) No input driver specified, ignoring this device.
[    15.166] (II) This device may have been added with another device file.
[    15.167] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event8)
[    15.167] (II) No input driver specified, ignoring this device.
[    15.167] (II) This device may have been added with another device file.
[    15.168] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:400a (/dev/input/event5)
[    15.168] (**) Logitech Unifying Device. Wireless PID:400a: Applying InputClass "evdev pointer catchall"
[    15.168] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:400a'
[    15.168] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.168] (**) Logitech Unifying Device. Wireless PID:400a: always reports core events
[    15.168] (**) evdev: Logitech Unifying Device. Wireless PID:400a: Device: "/dev/input/event5"
[    15.168] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Vendor 0x46d Product 0xc52b
[    15.168] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Found 20 mouse buttons
[    15.168] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Found scroll wheel(s)
[    15.168] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Found relative axes
[    15.168] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Found x and y relative axes
[    15.168] (II) evdev: Logitech Unifying Device. Wireless PID:400a: Configuring as mouse
[    15.168] (II) evdev: Logitech Unifying Device. Wireless PID:400a: Adding scrollwheel support
[    15.168] (**) evdev: Logitech Unifying Device. Wireless PID:400a: YAxisMapping: buttons 4 and 5
[    15.168] (**) evdev: Logitech Unifying Device. Wireless PID:400a:  EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.168] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.2/0003:046D:C52B.0003/input/input5/event5"
[    15.168] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:400a" (type: MOUSE, id 9)
[    15.168] (II) evdev: Logitech Unifying Device. Wireless PID:400a: initialized for relative axes.
[    15.168] (**) Logitech Unifying Device. Wireless PID:400a: (accel) keeping acceleration scheme 1
[    15.168] (**) Logitech Unifying Device. Wireless PID:400a: (accel) acceleration profile 0
[    15.168] (**) Logitech Unifying Device. Wireless PID:400a: (accel) acceleration factor: 2.000
[    15.168] (**) Logitech Unifying Device. Wireless PID:400a: (accel) acceleration threshold: 4
[    15.169] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:400a (/dev/input/mouse0)
[    15.169] (II) No input driver specified, ignoring this device.
[    15.169] (II) This device may have been added with another device file.
[    15.170] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    15.170] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    15.170] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    15.170] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.170] (**) AT Translated Set 2 keyboard: always reports core events
[    15.170] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    15.170] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    15.170] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    15.170] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    15.170] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    15.170] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    15.170] (**) Option "xkb_rules" "evdev"
[    15.170] (**) Option "xkb_model" "pc105"
[    15.170] (**) Option "xkb_layout" "us"
[    15.171] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[    15.171] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    15.171] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    15.171] (II) LoadModule: "synaptics"
[    15.171] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    15.171] (II) Module synaptics: vendor="X.Org Foundation"
[    15.171]     compiled for 1.11.3, module version = 1.5.99
[    15.171]     Module class: X.Org XInput Driver
[    15.172]     ABI class: X.Org XInput driver, version 16.0
[    15.172] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    15.172] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    15.172] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    15.172] (**) Option "Device" "/dev/input/event9"
[    15.176] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    15.176] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    15.176] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    15.176] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    15.176] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple scroll-buttons
[    15.176] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    15.176] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    15.176] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    15.181] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[    15.181] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    15.181] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    15.181] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    15.181] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    15.182] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    15.182] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    15.182] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    15.182] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    15.182] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    15.182] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    15.182] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    15.186] (II) config/udev: Adding input device Toshiba input device (/dev/input/event4)
[    15.186] (**) Toshiba input device: Applying InputClass "evdev keyboard catchall"
[    15.186] (II) Using input driver 'evdev' for 'Toshiba input device'
[    15.186] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.186] (**) Toshiba input device: always reports core events
[    15.186] (**) evdev: Toshiba input device: Device: "/dev/input/event4"
[    15.186] (--) evdev: Toshiba input device: Vendor 0 Product 0
[    15.186] (--) evdev: Toshiba input device: Found keys
[    15.186] (II) evdev: Toshiba input device: Configuring as keyboard
[    15.186] (**) Option "config_info" "udev:/sys/devices/virtual/input/input4/event4"
[    15.186] (II) XINPUT: Adding extended input device "Toshiba input device" (type: KEYBOARD, id 12)
[    15.186] (**) Option "xkb_rules" "evdev"
[    15.186] (**) Option "xkb_model" "pc105"
[    15.186] (**) Option "xkb_layout" "us"
[    24.135] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    24.328] (II) intel(0): EDID vendor "SEC", prod id 13893
[    24.328] (II) intel(0): Printing DDC gathered Modelines:
[    24.328] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
[    24.601] (II) intel(0): EDID vendor "SEC", prod id 13893
[    24.601] (II) intel(0): Printing DDC gathered Modelines:
[    24.601] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
[    25.575] (II) intel(0): EDID vendor "SEC", prod id 13893
[    25.575] (II) intel(0): Printing DDC gathered Modelines:
[    25.575] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)

[/FONT]
```

Looking at just this:
> 

[FONT=Verdana]14.465] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist. [    14.465]     Entry deleted from font path. [    14.465] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist. [    14.465]     Entry deleted from font path. [    14.465] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist. [    14.465]     Entry deleted from font path. [    14.465] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist. [    14.465]     Entry deleted from font path. [    14.465] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.[/FONT]

Is that the issue?I'm confused :confused: -

 What do you think is the problem and how can I fix this?
Any ideas?

---

### Post by UltimateCat on 2013-06-08
Strangly so; taking out the battery and just plugging in the adapter allows for the OS to stay up as long as 50 min's to an hour before it locks up again.

I ran Memtest; the memory is ok.  The test said:
Pass complete: no errors


Could it be that the BIOS need re-set?

Is it a driver issue?

---

### Post by Buntu Bunny on 2013-06-08
Well, I don't have any answers UltimateCat, but here's a bump for you. From your torrent thread I was able to download Voyager and install it on my laptop. I love it! No problems so far, but I'm interested in this thread just in case.

---

### Post by UltimateCat on 2013-06-09
Glad you like Voyager Buntu Bunny!

I hope that another member or Moderator knows what I could try. I don't know how to diagnose these problems--

I did check on the kernel mod's and all of the kernel drivers are in use so it's not that-
I'm currently reading through the 'dmesg' log but I don't understand a lot of what I am reading-

I'm using Google and looking for answers --


Could it be that the processor is starting to wear out? 
Would that cause a lock up or freeze?

---

### Post by UltimateCat on 2013-06-15
I tried 2 new 1 GB's of DDR2 and it made no difference; Voyager still locked up-

I installed CPU Frequency Monitoring application to keep an eye on the CPU.
It's a good app to watch the CPU, underclock the system or overclock it but I wasn't able to really make a dx with it--

Now running the Toshiba Recovery Wizard completely wiping the HDD--
It's been running for the last 22 hours and is at 69%-

Anyone know if updating the BIOS could be causing the system to lock up and have boot issue's?

---

### Post by UltimateCat on 2013-07-02
I tried for 5 weeks to get this laptop to work.

I tried:
-Zorin OS 6, Linux Mint Debian, Puppy Linux and Crunchbang.

Zorin locked up before it completely loaded on the Live CD-
Same thing happened with LM Debian.
Crunchbang installed but the DE locks up before I can type the first 3 letters to the username.

Puppy runs but the wireless internet did not work even with the rtl8187 driver--

It consistently failed with booting the first 2 tries and presented a black screen. Upon the 3rd or 4th boot it loaded into Puppy or Voyager.

Think this laptop is done for. Just going to throw it away-

---

