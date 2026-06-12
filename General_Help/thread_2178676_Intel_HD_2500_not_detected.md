---
title: "Intel HD 2500 not detected"
date: 2013-10-04
forum: General Help
---

### Post by han2 on 2013-10-04
Hello,

I have an Intel HD 2500 (i5-3570 Ivy Bridge) that is not being detected. I can only set the screen resolution to 1024x768 and I have no hardware acceleration. Neither Ubuntu 13.04 nor Xubuntu 13.04 detect it. I've tried installing Intel Graphics Drivers, but it makes no difference.

Someone knows how can I solve this?

Regards.

---

### Post by oldfred on 2013-10-04
Post this just to see what it does say.
 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root

You can try several alternative settings instead of nomodeset.


  i915.i915_enable_rc6=1
      
 acpi_osi=linux pci=noacpi

 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

---

### Post by han2 on 2013-10-05
Thanks for your response, oldfred.


This is the info I get:


```
sudo lshw -c display


description: VGA compatible controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)


lspci | grep VGA


00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)


xwininfo -root


xwininfo: Window id: 0x9f (the root window) (has no name)




  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1024
  Height: 768
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1024x768+0+0
```


As I have an old monitor I'm using the VGA output, not the DVI one (I don't know if this may be related to the problem).

I've tried adding the following lines to the end of the "linux /boot" line in Grub boot menu, without noticing any difference:

```
nomodeset

i915.i915_enable_rc6=1

acpi_osi=linux

acpi_osi=linux pci=noacpi

video=1440x900-24@60

video=VGA-1:1440x900-24@60
```

The motherboard I'm using is a Gigabyte GA-Z77-DS3H, just in case this information is relevant.

Regards.

---

### Post by oldfred on 2013-10-05
With whatever it is running with it says this:
-geometry 1024x768+0+0

Your old monitor with VGA may not support the higher resolution?

Does a setting like this work. Do you have info on monitor?
video=VGA-1:1024x768-24@60

---

### Post by Yellow Pasque on 2013-10-05
Can you post the /var/log/Xorg.0.log ?

---

### Post by han2 on 2013-10-05
> **oldfred said:**
> With whatever it is running with it says this:
-geometry 1024x768+0+0

Your old monitor with VGA may not support the higher resolution?

Does a setting like this work. Do you have info on monitor?
video=VGA-1:1024x768-24@60

My monitor supports 1440x900, I've been working with that resolution for years.

I've tried that setting but it makes no difference. Now thinking, may the problem be the monitor? Maybe Ubuntu is not recognizing my monitor, and it's assuming that its maximum supported resolution is 1024x768.

> **Temüjin said:**
> Can you post the /var/log/Xorg.0.log ?

Of course.

```
[     8.951] X.Org X Server 1.13.3
Release Date: 2013-03-07
[     8.951] X Protocol Version 11, Revision 0
[     8.951] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[     8.951] Current Operating System: Linux han 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 20:03:44 UTC 2013 x86_64
[     8.951] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=12b9f976-cc28-440c-a474-0b09771a6570 ro quiet splash vt.handoff=7
[     8.951] Build Date: 17 April 2013  10:43:13PM
[     8.951] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[     8.951] Current version of pixman: 0.28.2
[     8.951]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     8.951] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     8.951] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct  5 19:24:44 2013
[     8.964] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     8.964] (==) No Layout section.  Using the first Screen section.
[     8.964] (==) No screen section available. Using defaults.
[     8.964] (**) |-->Screen "Default Screen Section" (0)
[     8.964] (**) |   |-->Monitor "<default monitor>"
[     8.964] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     8.964] (==) Automatically adding devices
[     8.964] (==) Automatically enabling devices
[     8.964] (==) Automatically adding GPU devices
[     8.964] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     8.964]     Entry deleted from font path.
[     8.964] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     8.964]     Entry deleted from font path.
[     8.964] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     8.964]     Entry deleted from font path.
[     8.964] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     8.964]     Entry deleted from font path.
[     8.964] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     8.964]     Entry deleted from font path.
[     8.964] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     8.964]     Entry deleted from font path.
[     8.964] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     8.964] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     8.964] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     8.964] (II) Loader magic: 0x7f0fa91bbd20
[     8.964] (II) Module ABI versions:
[     8.964]     X.Org ANSI C Emulation: 0.4
[     8.964]     X.Org Video Driver: 13.1
[     8.964]     X.Org XInput driver : 18.0
[     8.964]     X.Org Server Extension : 7.0
[     8.964] (II) config/udev: Adding drm device (/dev/dri/card0)
[     8.965] (--) PCI:*(0:0:2:0) 8086:0152:1458:d000 rev 9, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[     8.965] (II) Open ACPI successful (/var/run/acpid.socket)
[     8.965] Initializing built-in extension Generic Event Extension
[     8.965] Initializing built-in extension SHAPE
[     8.965] Initializing built-in extension MIT-SHM
[     8.965] Initializing built-in extension XInputExtension
[     8.965] Initializing built-in extension XTEST
[     8.965] Initializing built-in extension BIG-REQUESTS
[     8.965] Initializing built-in extension SYNC
[     8.965] Initializing built-in extension XKEYBOARD
[     8.965] Initializing built-in extension XC-MISC
[     8.965] Initializing built-in extension SECURITY
[     8.965] Initializing built-in extension XINERAMA
[     8.965] Initializing built-in extension XFIXES
[     8.965] Initializing built-in extension RENDER
[     8.965] Initializing built-in extension RANDR
[     8.965] Initializing built-in extension COMPOSITE
[     8.965] Initializing built-in extension DAMAGE
[     8.965] Initializing built-in extension MIT-SCREEN-SAVER
[     8.965] Initializing built-in extension DOUBLE-BUFFER
[     8.965] Initializing built-in extension RECORD
[     8.965] Initializing built-in extension DPMS
[     8.965] Initializing built-in extension X-Resource
[     8.965] Initializing built-in extension XVideo
[     8.965] Initializing built-in extension XVideo-MotionCompensation
[     8.965] Initializing built-in extension SELinux
[     8.965] Initializing built-in extension XFree86-VidModeExtension
[     8.965] Initializing built-in extension XFree86-DGA
[     8.965] Initializing built-in extension XFree86-DRI
[     8.965] Initializing built-in extension DRI2
[     8.965] (II) LoadModule: "glx"
[     8.990] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     8.990] (II) Module glx: vendor="X.Org Foundation"
[     8.990]     compiled for 1.13.3, module version = 1.0.0
[     8.990]     ABI class: X.Org Server Extension, version 7.0
[     8.990] (==) AIGLX enabled
[     8.990] Loading extension GLX
[     8.990] (==) Matched intel as autoconfigured driver 0
[     8.990] (==) Matched intel as autoconfigured driver 1
[     8.990] (==) Matched vesa as autoconfigured driver 2
[     8.990] (==) Matched modesetting as autoconfigured driver 3
[     8.990] (==) Matched fbdev as autoconfigured driver 4
[     8.990] (==) Assigned the driver to the xf86ConfigLayout
[     8.990] (II) LoadModule: "intel"
[     8.990] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     9.015] (II) Module intel: vendor="X.Org Foundation"
[     9.015]     compiled for 1.13.3, module version = 2.21.9
[     9.015]     Module class: X.Org Video Driver
[     9.015]     ABI class: X.Org Video Driver, version 13.1
[     9.015] (II) LoadModule: "vesa"
[     9.015] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     9.015] (II) Module vesa: vendor="X.Org Foundation"
[     9.015]     compiled for 1.12.99.902, module version = 2.3.2
[     9.015]     Module class: X.Org Video Driver
[     9.015]     ABI class: X.Org Video Driver, version 13.0
[     9.015] (II) LoadModule: "modesetting"
[     9.015] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     9.015] (II) Module modesetting: vendor="X.Org Foundation"
[     9.015]     compiled for 1.13.3, module version = 0.7.0
[     9.015]     Module class: X.Org Video Driver
[     9.015]     ABI class: X.Org Video Driver, version 13.1
[     9.015] (II) LoadModule: "fbdev"
[     9.015] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     9.015] (II) Module fbdev: vendor="X.Org Foundation"
[     9.015]     compiled for 1.12.99.902, module version = 0.4.3
[     9.016]     Module class: X.Org Video Driver
[     9.016]     ABI class: X.Org Video Driver, version 13.0
[     9.016] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
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
[     9.016] (II) VESA: driver for VESA chipsets: vesa
[     9.016] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     9.016] (II) FBDEV: driver for framebuffer: fbdev
[     9.016] (++) using VT number 7


[     9.016] (WW) Falling back to old probe method for vesa
[     9.016] (WW) Falling back to old probe method for modesetting
[     9.016] (WW) Falling back to old probe method for fbdev
[     9.016] (II) Loading sub module "fbdevhw"
[     9.016] (II) LoadModule: "fbdevhw"
[     9.042] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     9.042] (II) Module fbdevhw: vendor="X.Org Foundation"
[     9.042]     compiled for 1.13.3, module version = 0.0.2
[     9.042]     ABI class: X.Org Video Driver, version 13.1
[     9.042] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     9.042] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     9.042] (==) intel(0): RGB weight 888
[     9.042] (==) intel(0): Default visual is TrueColor
[     9.042] (--) intel(0): Integrated Graphics Chipset: Intel(R) Ivybridge Desktop (GT1)
[     9.042] (**) intel(0): Relaxed fencing enabled
[     9.042] (**) intel(0): Wait on SwapBuffers? enabled
[     9.042] (**) intel(0): Triple buffering? enabled
[     9.042] (**) intel(0): Framebuffer tiled
[     9.042] (**) intel(0): Pixmaps tiled
[     9.042] (**) intel(0): 3D buffers tiled
[     9.042] (**) intel(0): SwapBuffers wait enabled
[     9.042] (==) intel(0): video overlay key set to 0x101fe
[     9.043] (II) intel(0): Output VGA1 has no monitor section
[     9.043] (II) intel(0): Output HDMI1 has no monitor section
[     9.043] (II) intel(0): Output DP1 has no monitor section
[     9.044] (II) intel(0): Output HDMI2 has no monitor section
[     9.044] (II) intel(0): Output DP2 has no monitor section
[     9.044] (II) intel(0): EDID for output VGA1
[     9.044] (II) intel(0): Printing probed modes for output VGA1
[     9.044] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     9.044] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     9.044] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     9.044] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[     9.044] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz e)
[     9.045] (II) intel(0): EDID for output HDMI1
[     9.045] (II) intel(0): EDID for output DP1
[     9.045] (II) intel(0): EDID for output HDMI2
[     9.045] (II) intel(0): EDID for output DP2
[     9.045] (II) intel(0): Output VGA1 connected
[     9.045] (II) intel(0): Output HDMI1 disconnected
[     9.045] (II) intel(0): Output DP1 disconnected
[     9.045] (II) intel(0): Output HDMI2 disconnected
[     9.045] (II) intel(0): Output DP2 disconnected
[     9.045] (II) intel(0): Using exact sizes for initial modes
[     9.045] (II) intel(0): Output VGA1 using initial mode 1024x768
[     9.045] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     9.045] (II) intel(0): Kernel page flipping support detected, enabling
[     9.045] (==) intel(0): DPI set to (96, 96)
[     9.045] (II) Loading sub module "fb"
[     9.045] (II) LoadModule: "fb"
[     9.045] (II) Loading /usr/lib/xorg/modules/libfb.so
[     9.045] (II) Module fb: vendor="X.Org Foundation"
[     9.045]     compiled for 1.13.3, module version = 1.0.0
[     9.045]     ABI class: X.Org ANSI C Emulation, version 0.4
[     9.045] (II) Loading sub module "dri2"
[     9.045] (II) LoadModule: "dri2"
[     9.045] (II) Module "dri2" already built-in
[     9.045] (II) UnloadModule: "vesa"
[     9.045] (II) Unloading vesa
[     9.045] (II) UnloadModule: "modesetting"
[     9.045] (II) Unloading modesetting
[     9.045] (II) UnloadModule: "fbdev"
[     9.045] (II) Unloading fbdev
[     9.045] (II) UnloadSubModule: "fbdevhw"
[     9.045] (II) Unloading fbdevhw
[     9.045] (==) Depth 24 pixmap format is 32 bpp
[     9.045] (II) intel(0): [DRI2] Setup complete
[     9.045] (II) intel(0): [DRI2]   DRI driver: i965
[     9.045] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[     9.046] (II) UXA(0): Driver registered support for the following operations:
[     9.046] (II)         solid
[     9.046] (II)         copy
[     9.046] (II)         composite (RENDER acceleration)
[     9.046] (II)         put_image
[     9.046] (II)         get_image
[     9.046] (==) intel(0): Backing store disabled
[     9.046] (==) intel(0): Silken mouse enabled
[     9.046] (II) intel(0): Initializing HW Cursor
[     9.046] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     9.046] (==) intel(0): DPMS enabled
[     9.046] (==) intel(0): Intel XvMC decoder enabled
[     9.046] (II) intel(0): Set up textured video
[     9.046] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[     9.046] (II) intel(0): direct rendering: DRI2 Enabled
[     9.046] (==) intel(0): hotplug detection: "enabled"
[     9.056] (--) RandR disabled
[     9.058] (II) SELinux: Disabled on system
[     9.323] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     9.323] (II) AIGLX: enabled GLX_INTEL_swap_event
[     9.323] (II) AIGLX: enabled GLX_ARB_create_context
[     9.323] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     9.323] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[     9.323] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     9.323] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     9.323] (II) AIGLX: Loaded and initialized i965
[     9.323] (II) GLX: Initialized DRI2 GL provider for screen 0
[     9.323] (II) intel(0): Setting screen physical size to 270 x 203
[     9.327] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     9.328] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     9.328] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     9.328] (II) LoadModule: "evdev"
[     9.328] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     9.369] (II) Module evdev: vendor="X.Org Foundation"
[     9.369]     compiled for 1.13.3, module version = 2.7.3
[     9.369]     Module class: X.Org XInput Driver
[     9.369]     ABI class: X.Org XInput driver, version 18.0
[     9.369] (II) Using input driver 'evdev' for 'Power Button'
[     9.369] (**) Power Button: always reports core events
[     9.369] (**) evdev: Power Button: Device: "/dev/input/event1"
[     9.369] (--) evdev: Power Button: Vendor 0 Product 0x1
[     9.369] (--) evdev: Power Button: Found keys
[     9.369] (II) evdev: Power Button: Configuring as keyboard
[     9.370] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     9.370] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     9.370] (**) Option "xkb_rules" "evdev"
[     9.370] (**) Option "xkb_model" "pc105"
[     9.370] (**) Option "xkb_layout" "es"
[     9.371] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[     9.371] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[     9.371] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     9.371] (II) Using input driver 'evdev' for 'Video Bus'
[     9.371] (**) Video Bus: always reports core events
[     9.371] (**) evdev: Video Bus: Device: "/dev/input/event5"
[     9.371] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     9.371] (--) evdev: Video Bus: Found keys
[     9.371] (II) evdev: Video Bus: Configuring as keyboard
[     9.371] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[     9.371] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     9.371] (**) Option "xkb_rules" "evdev"
[     9.371] (**) Option "xkb_model" "pc105"
[     9.371] (**) Option "xkb_layout" "es"
[     9.371] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     9.371] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     9.371] (II) Using input driver 'evdev' for 'Power Button'
[     9.371] (**) Power Button: always reports core events
[     9.371] (**) evdev: Power Button: Device: "/dev/input/event0"
[     9.371] (--) evdev: Power Button: Vendor 0 Product 0x1
[     9.371] (--) evdev: Power Button: Found keys
[     9.371] (II) evdev: Power Button: Configuring as keyboard
[     9.371] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     9.371] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     9.371] (**) Option "xkb_rules" "evdev"
[     9.371] (**) Option "xkb_model" "pc105"
[     9.371] (**) Option "xkb_layout" "es"
[     9.371] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[     9.371] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     9.372] (II) config/udev: Adding input device Logitech USB Laser Mouse (/dev/input/event2)
[     9.372] (**) Logitech USB Laser Mouse: Applying InputClass "evdev pointer catchall"
[     9.372] (II) Using input driver 'evdev' for 'Logitech USB Laser Mouse'
[     9.372] (**) Logitech USB Laser Mouse: always reports core events
[     9.372] (**) evdev: Logitech USB Laser Mouse: Device: "/dev/input/event2"
[     9.372] (--) evdev: Logitech USB Laser Mouse: Vendor 0x46d Product 0xc069
[     9.372] (--) evdev: Logitech USB Laser Mouse: Found 12 mouse buttons
[     9.372] (--) evdev: Logitech USB Laser Mouse: Found scroll wheel(s)
[     9.372] (--) evdev: Logitech USB Laser Mouse: Found relative axes
[     9.372] (--) evdev: Logitech USB Laser Mouse: Found x and y relative axes
[     9.372] (II) evdev: Logitech USB Laser Mouse: Configuring as mouse
[     9.372] (II) evdev: Logitech USB Laser Mouse: Adding scrollwheel support
[     9.372] (**) evdev: Logitech USB Laser Mouse: YAxisMapping: buttons 4 and 5
[     9.372] (**) evdev: Logitech USB Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     9.372] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input2/event2"
[     9.372] (II) XINPUT: Adding extended input device "Logitech USB Laser Mouse" (type: MOUSE, id 9)
[     9.372] (II) evdev: Logitech USB Laser Mouse: initialized for relative axes.
[     9.372] (**) Logitech USB Laser Mouse: (accel) keeping acceleration scheme 1
[     9.372] (**) Logitech USB Laser Mouse: (accel) acceleration profile 0
[     9.372] (**) Logitech USB Laser Mouse: (accel) acceleration factor: 2.000
[     9.372] (**) Logitech USB Laser Mouse: (accel) acceleration threshold: 4
[     9.372] (II) config/udev: Adding input device Logitech USB Laser Mouse (/dev/input/mouse0)
[     9.372] (II) No input driver specified, ignoring this device.
[     9.372] (II) This device may have been added with another device file.
[     9.372] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event3)
[     9.372] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[     9.372] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[     9.372] (**) Logitech USB Keyboard: always reports core events
[     9.372] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event3"
[     9.372] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[     9.372] (--) evdev: Logitech USB Keyboard: Found keys
[     9.372] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[     9.372] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input3/event3"
[     9.372] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 10)
[     9.372] (**) Option "xkb_rules" "evdev"
[     9.372] (**) Option "xkb_model" "pc105"
[     9.372] (**) Option "xkb_layout" "es"
[     9.373] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event4)
[     9.373] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[     9.373] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[     9.373] (**) Logitech USB Keyboard: always reports core events
[     9.373] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event4"
[     9.373] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[     9.373] (--) evdev: Logitech USB Keyboard: Found absolute axes
[     9.373] (II) evdev: Logitech USB Keyboard: Forcing absolute x/y axes to exist.
[     9.373] (--) evdev: Logitech USB Keyboard: Found keys
[     9.373] (II) evdev: Logitech USB Keyboard: Forcing relative x/y axes to exist.
[     9.373] (II) evdev: Logitech USB Keyboard: Configuring as mouse
[     9.373] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[     9.373] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.1/input/input4/event4"
[     9.373] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 11)
[     9.373] (**) Option "xkb_rules" "evdev"
[     9.373] (**) Option "xkb_model" "pc105"
[     9.373] (**) Option "xkb_layout" "es"
[     9.373] (II) evdev: Logitech USB Keyboard: initialized for absolute axes.
[     9.373] (**) Logitech USB Keyboard: (accel) keeping acceleration scheme 1
[     9.373] (**) Logitech USB Keyboard: (accel) acceleration profile 0
[     9.373] (**) Logitech USB Keyboard: (accel) acceleration factor: 2.000
[     9.373] (**) Logitech USB Keyboard: (accel) acceleration threshold: 4
[     9.373] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event10)
[     9.373] (II) No input driver specified, ignoring this device.
[     9.373] (II) This device may have been added with another device file.
[     9.373] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event11)
[     9.373] (II) No input driver specified, ignoring this device.
[     9.373] (II) This device may have been added with another device file.
[     9.373] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event6)
[     9.373] (II) No input driver specified, ignoring this device.
[     9.373] (II) This device may have been added with another device file.
[     9.373] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event7)
[     9.373] (II) No input driver specified, ignoring this device.
[     9.373] (II) This device may have been added with another device file.
[     9.373] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event8)
[     9.373] (II) No input driver specified, ignoring this device.
[     9.373] (II) This device may have been added with another device file.
[     9.374] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event9)
[     9.374] (II) No input driver specified, ignoring this device.
[     9.374] (II) This device may have been added with another device file.
```

Regards.

---

### Post by Yellow Pasque on 2013-10-05
```
cvt 1440 900 60
```

Creat an xorg.conf
```
gksu gedit /etc/X11/xorg.conf
```
Copy this into the blank file (and copy the modeline from cvt where indicated).
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "VGA1"
        <paste Modeline from cvt here>
        Option          "PreferredMode" "1440x900_60.00"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor        "VGA1"
        Device         "Configured Video Device"
EndSection
```

---

### Post by Yellow Pasque on 2013-10-05
As for the 3D acceleration, the log looks okay. What does glxinfo say?
```
sudo apt-get install mesa-utils
glxinfo
```

---

### Post by han2 on 2013-10-06
It works! My monitor is a LG L192WS, and right now it's working with this xorg.conf:

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection


Section "Monitor"
        Identifier      "VGA1"
        Modeline        "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
        Option          "PreferredMode" "1440x900_60.00"
EndSection


Section "Screen"
        Identifier      "Default Screen"
        Monitor         "VGA1"
        Device          "Configured Video Device"
EndSection

```

So it was a problem related to the monitor, not the Intel HD 2500.

> **Temüjin said:**
> As for the 3D acceleration, the log looks okay. What does glxinfo say?
```
sudo apt-get install mesa-utils
glxinfo
```

I'm sorry, I think I made a gaffe. I assumed the acceleration was not working, but in fact it is.

Thanks, oldfred and Temüjin, for your help :)

Regards.

---

