---
title: "GLX error in Kubuntu 14.04"
date: 2014-08-11
forum: General Help
---

### Post by Hapsburg on 2014-08-11
Hi there, I have Kubuntu 14.04 installed on my laptop computer, which has the built-in optimus technology (Two video cards : nVidia GeForce GT 640m, Intel 3rd Gen Core processor Graphics Controller). I have the proper graphic card driver packages installed alreay (nvidia-340, nvidia-340-uvm, nvidia-libopencl1-340, nvidia-opencl-icd-340). But there seems to be a problem on running GLX programs, all the 3D desktop effect in Kwin system doesn't work, and the Google Earth cannot be launched. The following are the error message I got by running the command "glxinfo" which is very similar with the message I got when I tried to run Google Earth:

```

name of display: :0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".

```

I have searched over some old posts on the error message, but still cannot draw any conclusion about the cause of the problem. I hope someone here can help me out from this, I've been stuck on this for days without any advance. I'm giving some more related information here to clarify the problem :

Command : lspci -vv
```

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 055f
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 43
    Region 0: Memory at f1000000 (64-bit, non-prefetchable) [size=4M]
    Region 2: Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 640M] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Dell GeForce GT 640M
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at d0000000 (64-bit, prefetchable) [size=32M]
    Region 5: I/O ports at 3000 [size=128]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: nvidia

```

Command : lsmod
```

Module                       Size           Used by
uvcvideo                     80885         0 
videobuf2_vmalloc      13216         1 uvcvideo
videobuf2_memops     13362         1 videobuf2_vmalloc
videobuf2_core            40664         1 uvcvideo
videodev                     134688       2 uvcvideo,videobuf2_core
nvidia                         10527448   0 
i915                            783805       2 
i2c_algo_bit                 13413        1 i915
drm_kms_helper         53081        1 i915
drm                            303102       4 i915,drm_kms_helper,nvidia
ahci                            25819         5 
alx                              32452         0 
libahci                        32560         1 ahci
mdio                           13807         1 alx
video                           19476        1 i915

```

/var/log/Xorg.0.log
```

[    19.277] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    19.277] X Protocol Version 11, Revision 0
[    19.277] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    19.277] Current Operating System: Linux Hapsburg-LT 3.13.0-33-generic #58-Ubuntu SMP Tue Jul 29 16:45:05 UTC 2014 x86_64
[    19.277] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-33-generic root=UUID=aa3bcf90-6e11-4e16-87cf-e3bcb81161f5 ro quiet splash
[    19.277] Build Date: 16 April 2014  01:36:29PM
[    19.277] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    19.277] Current version of pixman: 0.30.2
[    19.277]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    19.277] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.277] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 12 10:44:03 2014
[    19.445] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.598] (==) No Layout section.  Using the first Screen section.
[    19.598] (==) No screen section available. Using defaults.
[    19.598] (**) |-->Screen "Default Screen Section" (0)
[    19.598] (**) |   |-->Monitor "<default monitor>"
[    19.598] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    19.598] (==) Automatically adding devices
[    19.598] (==) Automatically enabling devices
[    19.598] (==) Automatically adding GPU devices
[    19.784] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.784]     Entry deleted from font path.
[    19.784] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.784]     Entry deleted from font path.
[    19.784] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.784]     Entry deleted from font path.
[    19.799] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.799]     Entry deleted from font path.
[    19.799] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.799]     Entry deleted from font path.
[    19.799] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    19.799] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.799] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.799] (II) Loader magic: 0x7f371c7abd60
[    19.799] (II) Module ABI versions:
[    19.799]     X.Org ANSI C Emulation: 0.4
[    19.799]     X.Org Video Driver: 15.0
[    19.799]     X.Org XInput driver : 20.0
[    19.799]     X.Org Server Extension : 8.0
[    19.800] (II) xfree86: Adding drm device (/dev/dri/card1)
[    19.800] (II) xfree86: Adding drm device (/dev/dri/card0)
[    19.801] (--) PCI:*(0:0:2:0) 8086:0166:1028:055f rev 9, Mem @ 0xf1000000/4194304, 0xe0000000/268435456, I/O @ 0x00004000/64
[    19.801] (--) PCI: (0:1:0:0) 10de:0fd2:1028:055f rev 161, Mem @ 0xf0000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00003000/128
[    19.822] Initializing built-in extension Generic Event Extension
[    19.822] Initializing built-in extension SHAPE
[    19.822] Initializing built-in extension MIT-SHM
[    19.822] Initializing built-in extension XInputExtension
[    19.822] Initializing built-in extension XTEST
[    19.822] Initializing built-in extension BIG-REQUESTS
[    19.822] Initializing built-in extension SYNC
[    19.822] Initializing built-in extension XKEYBOARD
[    19.822] Initializing built-in extension XC-MISC
[    19.822] Initializing built-in extension SECURITY
[    19.822] Initializing built-in extension XINERAMA
[    19.822] Initializing built-in extension XFIXES
[    19.822] Initializing built-in extension RENDER
[    19.822] Initializing built-in extension RANDR
[    19.822] Initializing built-in extension COMPOSITE
[    19.822] Initializing built-in extension DAMAGE
[    19.822] Initializing built-in extension MIT-SCREEN-SAVER
[    19.822] Initializing built-in extension DOUBLE-BUFFER
[    19.822] Initializing built-in extension RECORD
[    19.822] Initializing built-in extension DPMS
[    19.822] Initializing built-in extension Present
[    19.822] Initializing built-in extension DRI3
[    19.822] Initializing built-in extension X-Resource
[    19.822] Initializing built-in extension XVideo
[    19.822] Initializing built-in extension XVideo-MotionCompensation
[    19.822] Initializing built-in extension SELinux
[    19.822] Initializing built-in extension XFree86-VidModeExtension
[    19.822] Initializing built-in extension XFree86-DGA
[    19.822] Initializing built-in extension XFree86-DRI
[    19.822] Initializing built-in extension DRI2
[    19.822] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    19.822] (II) "glx" will be loaded by default.
[    19.822] (WW) "xmir" is not to be loaded by default. Skipping.
[    19.822] (II) LoadModule: "glx"
[    19.865] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    22.174] (II) Module glx: vendor="NVIDIA Corporation"
[    22.174]     compiled for 4.0.2, module version = 1.0.0
[    22.174]     Module class: X.Org Server Extension
[    22.196] (II) NVIDIA GLX Module  340.24  Wed Jul  2 15:04:31 PDT 2014
[    22.219] Loading extension GLX
[    22.219] (==) Matched intel as autoconfigured driver 0
[    22.219] (==) Matched nvidia as autoconfigured driver 1
[    22.219] (==) Matched nouveau as autoconfigured driver 2
[    22.219] (==) Matched intel as autoconfigured driver 3
[    22.219] (==) Matched modesetting as autoconfigured driver 4
[    22.219] (==) Matched fbdev as autoconfigured driver 5
[    22.219] (==) Matched vesa as autoconfigured driver 6
[    22.219] (==) Assigned the driver to the xf86ConfigLayout
[    22.219] (II) LoadModule: "intel"
[    22.243] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    22.401] (II) Module intel: vendor="X.Org Foundation"
[    22.401]     compiled for 1.15.1, module version = 2.99.914
[    22.401]     Module class: X.Org Video Driver
[    22.401]     ABI class: X.Org Video Driver, version 15.0
[    22.401] (II) LoadModule: "nvidia"
[    22.401] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    22.541] (II) Module nvidia: vendor="NVIDIA Corporation"
[    22.541]     compiled for 4.0.2, module version = 1.0.0
[    22.541]     Module class: X.Org Video Driver
[    22.544] (II) LoadModule: "nouveau"
[    22.544] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    22.564] (II) Module nouveau: vendor="X.Org Foundation"
[    22.564]     compiled for 1.15.1, module version = 1.0.10
[    22.564]     Module class: X.Org Video Driver
[    22.564]     ABI class: X.Org Video Driver, version 15.0
[    22.564] (II) LoadModule: "modesetting"
[    22.564] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    22.573] (II) Module modesetting: vendor="X.Org Foundation"
[    22.573]     compiled for 1.15.0, module version = 0.8.1
[    22.573]     Module class: X.Org Video Driver
[    22.573]     ABI class: X.Org Video Driver, version 15.0
[    22.573] (II) LoadModule: "fbdev"
[    22.573] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.574] (II) Module fbdev: vendor="X.Org Foundation"
[    22.574]     compiled for 1.15.0, module version = 0.4.4
[    22.574]     Module class: X.Org Video Driver
[    22.574]     ABI class: X.Org Video Driver, version 15.0
[    22.574] (II) LoadModule: "vesa"
[    22.574] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.574] (II) Module vesa: vendor="X.Org Foundation"
[    22.574]     compiled for 1.15.0, module version = 2.3.3
[    22.574]     Module class: X.Org Video Driver
[    22.574]     ABI class: X.Org Video Driver, version 15.0
[    22.574] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    22.575] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    22.575] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    22.575] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    22.575] (II) NVIDIA dlloader X Driver  340.24  Wed Jul  2 14:42:23 PDT 2014
[    22.575] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    22.589] (II) NOUVEAU driver 
[    22.589] (II) NOUVEAU driver for NVIDIA chipset families :
[    22.589]     RIVA TNT        (NV04)
[    22.589]     RIVA TNT2       (NV05)
[    22.589]     GeForce 256     (NV10)
[    22.589]     GeForce 2       (NV11, NV15)
[    22.589]     GeForce 4MX     (NV17, NV18)
[    22.589]     GeForce 3       (NV20)
[    22.589]     GeForce 4Ti     (NV25, NV28)
[    22.589]     GeForce FX      (NV3x)
[    22.589]     GeForce 6       (NV4x)
[    22.589]     GeForce 7       (G7x)
[    22.589]     GeForce 8       (G8x)
[    22.589]     GeForce GTX 200 (NVA0)
[    22.589]     GeForce GTX 400 (NVC0)
[    22.589] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    22.589] (II) FBDEV: driver for framebuffer: fbdev
[    22.589] (II) VESA: driver for VESA chipsets: vesa
[    22.589] (++) using VT number 8

[    22.593] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[    22.593] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.914+git20140811.6554cf0a-0ubuntu0sarvatt~trusty (Robert Hooker <sarvatt@ubuntu.com>)
[    22.593] (II) intel(0): SNA compiled for use with valgrind
[    22.595] (EE) [drm] KMS not enabled
[    22.595] (WW) Falling back to old probe method for modesetting
[    22.595] (WW) Falling back to old probe method for fbdev
[    22.595] (II) Loading sub module "fbdevhw"
[    22.595] (II) LoadModule: "fbdevhw"
[    22.618] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.624] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.624]     compiled for 1.15.1, module version = 0.0.2
[    22.624]     ABI class: X.Org Video Driver, version 15.0
[    22.624] (WW) Falling back to old probe method for vesa
[    22.625] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4000
[    22.625] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[    22.625] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    22.625] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    22.625] (==) intel(0): RGB weight 888
[    22.625] (==) intel(0): Default visual is TrueColor
[    22.626] (II) intel(0): Output LVDS1 has no monitor section
[    22.626] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output LVDS1
[    22.626] (II) intel(0): Enabled output LVDS1
[    22.626] (II) intel(0): Output VGA1 has no monitor section
[    22.626] (II) intel(0): Enabled output VGA1
[    22.626] (II) intel(0): Output HDMI1 has no monitor section
[    22.626] (II) intel(0): Enabled output HDMI1
[    22.626] (II) intel(0): Output DP1 has no monitor section
[    22.626] (II) intel(0): Enabled output DP1
[    22.626] (--) intel(0): Using a maximum size of 64x64 for hardware cursors
[    22.626] (II) intel(0): Output VIRTUAL1 has no monitor section
[    22.626] (II) intel(0): Enabled output VIRTUAL1
[    22.626] (--) intel(0): Output LVDS1 using initial mode 1600x900 on pipe 0
[    22.626] (==) intel(0): TearFree disabled
[    22.626] (==) intel(0): DPI set to (96, 96)
[    22.626] (II) Loading sub module "dri3"
[    22.626] (II) LoadModule: "dri3"
[    22.627] (WW) Warning, couldn't open module dri3
[    22.627] (II) UnloadModule: "dri3"
[    22.627] (II) Unloading dri3
[    22.627] (EE) intel: Failed to load module "dri3" (module does not exist, 0)
[    22.627] (II) Loading sub module "dri2"
[    22.627] (II) LoadModule: "dri2"
[    22.627] (II) Module "dri2" already built-in
[    22.627] (II) Loading sub module "present"
[    22.627] (II) LoadModule: "present"
[    22.627] (WW) Warning, couldn't open module present
[    22.627] (II) UnloadModule: "present"
[    22.627] (II) Unloading present
[    22.627] (EE) intel: Failed to load module "present" (module does not exist, 0)
[    22.728] (II) UnloadModule: "nvidia"
[    22.728] (II) Unloading nvidia
[    22.728] (II) UnloadModule: "fbdev"
[    22.728] (II) Unloading fbdev
[    22.728] (II) UnloadSubModule: "fbdevhw"
[    22.728] (II) Unloading fbdevhw
[    22.728] (II) UnloadModule: "vesa"
[    22.728] (II) Unloading vesa
[    22.728] (==) Depth 24 pixmap format is 32 bpp
[    22.770] (II) intel(0): SNA initialized with Ivybridge (gen7, gt2) backend
[    22.770] (==) intel(0): Backing store enabled
[    22.770] (==) intel(0): Silken mouse enabled
[    22.771] (II) intel(0): HW Cursor enabled
[    22.771] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    22.772] (==) intel(0): DPMS enabled
[    22.772] (II) intel(0): [DRI2] Setup complete
[    22.772] (II) intel(0): [DRI2]   DRI driver: i965
[    22.772] (II) intel(0): [DRI2]   VDPAU driver: i965
[    22.772] (II) intel(0): direct rendering: DRI2 enabled
[    22.772] (==) intel(0): display hotplug detection enabled
[    22.772] (--) RandR disabled
[    22.776] (II) SELinux: Disabled on system
[    22.792] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    22.794] (II) intel(0): switch to mode 1600x900@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    22.812] (II) intel(0): Setting screen physical size to 423 x 238
[    22.929] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.951] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    22.951] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.951] (II) LoadModule: "evdev"
[    22.951] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.960] (II) Module evdev: vendor="X.Org Foundation"
[    22.960]     compiled for 1.15.0, module version = 2.8.2
[    22.960]     Module class: X.Org XInput Driver
[    22.960]     ABI class: X.Org XInput driver, version 20.0
[    22.961] (II) Using input driver 'evdev' for 'Power Button'
[    22.961] (**) Power Button: always reports core events
[    22.961] (**) evdev: Power Button: Device: "/dev/input/event3"
[    22.961] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.961] (--) evdev: Power Button: Found keys
[    22.961] (II) evdev: Power Button: Configuring as keyboard
[    22.961] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    22.961] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    22.961] (**) Option "xkb_rules" "evdev"
[    22.961] (**) Option "xkb_model" "pc105"
[    22.961] (**) Option "xkb_layout" "us"
[    22.961] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    22.961] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    22.961] (II) Using input driver 'evdev' for 'Video Bus'
[    22.961] (**) Video Bus: always reports core events
[    22.961] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    22.961] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    22.961] (--) evdev: Video Bus: Found keys
[    22.961] (II) evdev: Video Bus: Configuring as keyboard
[    22.961] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input10/event7"
[    22.961] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    22.961] (**) Option "xkb_rules" "evdev"
[    22.961] (**) Option "xkb_model" "pc105"
[    22.961] (**) Option "xkb_layout" "us"
[    22.962] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    22.962] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    22.962] (II) Using input driver 'evdev' for 'Video Bus'
[    22.962] (**) Video Bus: always reports core events
[    22.962] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    22.962] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    22.962] (--) evdev: Video Bus: Found keys
[    22.962] (II) evdev: Video Bus: Configuring as keyboard
[    22.962] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2f/LNXVIDEO:00/input/input9/event6"
[    22.962] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    22.962] (**) Option "xkb_rules" "evdev"
[    22.962] (**) Option "xkb_model" "pc105"
[    22.962] (**) Option "xkb_layout" "us"
[    22.962] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    22.962] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.962] (II) Using input driver 'evdev' for 'Power Button'
[    22.962] (**) Power Button: always reports core events
[    22.962] (**) evdev: Power Button: Device: "/dev/input/event0"
[    22.962] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.962] (--) evdev: Power Button: Found keys
[    22.962] (II) evdev: Power Button: Configuring as keyboard
[    22.962] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    22.962] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    22.962] (**) Option "xkb_rules" "evdev"
[    22.962] (**) Option "xkb_model" "pc105"
[    22.962] (**) Option "xkb_layout" "us"
[    22.963] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    22.963] (II) No input driver specified, ignoring this device.
[    22.963] (II) This device may have been added with another device file.
[    22.963] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    22.963] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    22.963] (II) Using input driver 'evdev' for 'Sleep Button'
[    22.963] (**) Sleep Button: always reports core events
[    22.963] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    22.963] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    22.963] (--) evdev: Sleep Button: Found keys
[    22.963] (II) evdev: Sleep Button: Configuring as keyboard
[    22.963] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    22.963] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    22.963] (**) Option "xkb_rules" "evdev"
[    22.963] (**) Option "xkb_model" "pc105"
[    22.963] (**) Option "xkb_layout" "us"
[    22.963] (II) config/udev: Adding drm device (/dev/dri/card1)
[    22.963] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[    22.963] (II) config/udev: Adding drm device (/dev/dri/card0)
[    22.963] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    22.963] (II) config/udev: Adding input device Logitech USB Laser Mouse (/dev/input/event5)
[    22.963] (**) Logitech USB Laser Mouse: Applying InputClass "evdev pointer catchall"
[    22.963] (II) Using input driver 'evdev' for 'Logitech USB Laser Mouse'
[    22.963] (**) Logitech USB Laser Mouse: always reports core events
[    22.963] (**) evdev: Logitech USB Laser Mouse: Device: "/dev/input/event5"
[    22.964] (--) evdev: Logitech USB Laser Mouse: Vendor 0x46d Product 0xc052
[    22.964] (--) evdev: Logitech USB Laser Mouse: Found 3 mouse buttons
[    22.964] (--) evdev: Logitech USB Laser Mouse: Found scroll wheel(s)
[    22.964] (--) evdev: Logitech USB Laser Mouse: Found relative axes
[    22.964] (--) evdev: Logitech USB Laser Mouse: Found x and y relative axes
[    22.964] (II) evdev: Logitech USB Laser Mouse: Configuring as mouse
[    22.964] (II) evdev: Logitech USB Laser Mouse: Adding scrollwheel support
[    22.964] (**) evdev: Logitech USB Laser Mouse: YAxisMapping: buttons 4 and 5
[    22.964] (**) evdev: Logitech USB Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.964] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input8/event5"
[    22.964] (II) XINPUT: Adding extended input device "Logitech USB Laser Mouse" (type: MOUSE, id 11)
[    22.964] (II) evdev: Logitech USB Laser Mouse: initialized for relative axes.
[    22.964] (**) Logitech USB Laser Mouse: (accel) keeping acceleration scheme 1
[    22.964] (**) Logitech USB Laser Mouse: (accel) acceleration profile 0
[    22.964] (**) Logitech USB Laser Mouse: (accel) acceleration factor: 2.000
[    22.964] (**) Logitech USB Laser Mouse: (accel) acceleration threshold: 4
[    22.964] (II) config/udev: Adding input device Logitech USB Laser Mouse (/dev/input/mouse0)
[    22.964] (II) No input driver specified, ignoring this device.
[    22.964] (II) This device may have been added with another device file.
[    22.964] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD (/dev/input/event11)
[    22.964] (**) Laptop_Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[    22.964] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD'
[    22.964] (**) Laptop_Integrated_Webcam_HD: always reports core events
[    22.964] (**) evdev: Laptop_Integrated_Webcam_HD: Device: "/dev/input/event11"
[    22.964] (--) evdev: Laptop_Integrated_Webcam_HD: Vendor 0xbda Product 0x58bf
[    22.964] (--) evdev: Laptop_Integrated_Webcam_HD: Found keys
[    22.964] (II) evdev: Laptop_Integrated_Webcam_HD: Configuring as keyboard
[    22.964] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input12/event11"
[    22.964] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD" (type: KEYBOARD, id 12)
[    22.964] (**) Option "xkb_rules" "evdev"
[    22.964] (**) Option "xkb_model" "pc105"
[    22.964] (**) Option "xkb_layout" "us"
[    22.965] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event14)
[    22.965] (II) No input driver specified, ignoring this device.
[    22.965] (II) This device may have been added with another device file.
[    22.965] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event13)
[    22.965] (II) No input driver specified, ignoring this device.
[    22.965] (II) This device may have been added with another device file.
[    22.965] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    22.965] (II) No input driver specified, ignoring this device.
[    22.965] (II) This device may have been added with another device file.
[    22.965] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    22.965] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    22.965] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    22.965] (**) AT Translated Set 2 keyboard: always reports core events
[    22.965] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    22.965] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    22.965] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    22.965] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    22.965] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    22.965] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    22.965] (**) Option "xkb_rules" "evdev"
[    22.965] (**) Option "xkb_model" "pc105"
[    22.965] (**) Option "xkb_layout" "us"
[    22.966] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event9)
[    22.966] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    22.966] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    22.966] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "Default clickpad buttons"
[    22.966] (II) LoadModule: "synaptics"
[    22.966] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    22.986] (II) Module synaptics: vendor="X.Org Foundation"
[    22.986]     compiled for 1.15.0, module version = 1.7.4
[    22.986]     Module class: X.Org XInput Driver
[    22.986]     ABI class: X.Org XInput driver, version 20.0
[    22.986] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    22.986] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    22.986] (**) Option "Device" "/dev/input/event9"
[    23.000] (II) synaptics: AlpsPS/2 ALPS GlidePoint: ignoring touch events for semi-multitouch device
[    23.000] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1216 (res 0)
[    23.000] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 640 (res 0)
[    23.000] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    23.000] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[    23.000] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle double triple
[    23.000] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[    23.000] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[    23.000] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    23.000] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    23.016] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event9"
[    23.016] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 14)
[    23.016] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    23.016] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MaxSpeed is now 1.75
[    23.016] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) AccelFactor is now 0.146
[    23.016] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    23.016] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    23.016] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    23.016] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    23.016] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    23.016] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
[    23.016] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[    23.017] (II) config/udev: Adding input device ALPS PS/2 Device (/dev/input/event8)
[    23.017] (**) ALPS PS/2 Device: Applying InputClass "evdev pointer catchall"
[    23.017] (II) Using input driver 'evdev' for 'ALPS PS/2 Device'
[    23.017] (**) ALPS PS/2 Device: always reports core events
[    23.017] (**) evdev: ALPS PS/2 Device: Device: "/dev/input/event8"
[    23.017] (--) evdev: ALPS PS/2 Device: Vendor 0x2 Product 0x8
[    23.017] (--) evdev: ALPS PS/2 Device: Found 3 mouse buttons
[    23.017] (--) evdev: ALPS PS/2 Device: Found relative axes
[    23.017] (--) evdev: ALPS PS/2 Device: Found x and y relative axes
[    23.017] (II) evdev: ALPS PS/2 Device: Configuring as mouse
[    23.017] (**) evdev: ALPS PS/2 Device: YAxisMapping: buttons 4 and 5
[    23.017] (**) evdev: ALPS PS/2 Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.017] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event8"
[    23.017] (II) XINPUT: Adding extended input device "ALPS PS/2 Device" (type: MOUSE, id 15)
[    23.017] (II) evdev: ALPS PS/2 Device: initialized for relative axes.
[    23.017] (**) ALPS PS/2 Device: (accel) keeping acceleration scheme 1
[    23.017] (**) ALPS PS/2 Device: (accel) acceleration profile 0
[    23.017] (**) ALPS PS/2 Device: (accel) acceleration factor: 2.000
[    23.017] (**) ALPS PS/2 Device: (accel) acceleration threshold: 4
[    23.017] (II) config/udev: Adding input device ALPS PS/2 Device (/dev/input/mouse1)
[    23.017] (II) No input driver specified, ignoring this device.
[    23.017] (II) This device may have been added with another device file.
[    23.018] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event10)
[    23.018] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    23.018] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    23.018] (**) Dell WMI hotkeys: always reports core events
[    23.018] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event10"
[    23.018] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    23.018] (--) evdev: Dell WMI hotkeys: Found keys
[    23.018] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    23.018] (**) Option "config_info" "udev:/sys/devices/virtual/input/input11/event10"
[    23.018] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 16)
[    23.018] (**) Option "xkb_rules" "evdev"
[    23.018] (**) Option "xkb_model" "pc105"
[    23.018] (**) Option "xkb_layout" "us"
[    47.373] (II) intel(0): EDID vendor "LGD", prod id 870
[    47.373] (II) intel(0): Printing DDC gathered Modelines:
[    47.373] (II) intel(0): Modeline "1600x900"x0.0  121.20  1600 1760 1856 2104  900 903 908 960 +hsync -vsync (57.6 kHz eP)
[    47.373] (II) intel(0): Modeline "1600x900"x0.0   80.80  1600 1760 1856 2104  900 903 908 960 +hsync -vsync (38.4 kHz e)

```

Command : dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-33-generic (buildd@tipua) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #58-Ubuntu SMP Tue Jul 29 16:45:05 UTC 2014 (Ubuntu 3.13.0-33.58-generic 3.13.11.4)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.13.0-33-generic root=UUID=aa3bcf90-6e11-4e16-87cf-e3bcb81161f5 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000a9094fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000a9095000-0x00000000a9296fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000a9297000-0x00000000b813dfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b813e000-0x00000000baeeefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000baeef000-0x00000000baf9efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000baf9f000-0x00000000baffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bafff000-0x00000000baffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb000000-0x00000000bf9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed08000-0x00000000fed08fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff980000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000023f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Dell Inc.          Inspiron 7420/08PPR2, BIOS A09 08/16/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x23f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FF800000 mask FFF800000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0BB000000 mask FFF000000 uncachable
[    0.000000]   5 base 100000000 mask F00000000 write-back
[    0.000000]   6 base 200000000 mask FC0000000 write-back
[    0.000000]   7 base 23F800000 mask FFF800000 uncachable
[    0.000000]   8 base 23F600000 mask FFFE00000 uncachable
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xbb000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f0100-0x000f010f] mapped at [ffff8800000f0100]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23f400000-0x23f5fffff]
[    0.000000]  [mem 0x23f400000-0x23f5fffff] page 2M
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23c000000-0x23f3fffff]
[    0.000000]  [mem 0x23c000000-0x23f3fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x23bffffff]
[    0.000000]  [mem 0x200000000-0x23bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x40003fff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x40003fff] page 4k
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x40005000-0xa9094fff]
[    0.000000]  [mem 0x40005000-0x401fffff] page 4k
[    0.000000]  [mem 0x40200000-0xa8ffffff] page 2M
[    0.000000]  [mem 0xa9000000-0xa9094fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xa9297000-0xb813dfff]
[    0.000000]  [mem 0xa9297000-0xa93fffff] page 4k
[    0.000000]  [mem 0xa9400000-0xb7ffffff] page 2M
[    0.000000]  [mem 0xb8000000-0xb813dfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbafff000-0xbaffffff]
[    0.000000]  [mem 0xbafff000-0xbaffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
[    0.000000] RAMDISK: [mem 0x34c3e000-0x36616fff]
[    0.000000] ACPI: RSDP 00000000000f0120 000024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000baffe170 0000A4 (v01 DELL    QA09    00000002 LOHR 00000002)
[    0.000000] ACPI: FACP 00000000bafe4000 00010C (v05 DELL    QA09    00000002 LOHR 00000002)
[    0.000000] ACPI: DSDT 00000000baff2000 009ECD (v02 DELL    IVB-CPT 00000000 INTL 20061109)
[    0.000000] ACPI: FACS 00000000baf7c000 000040
[    0.000000] ACPI: SLIC 00000000baffd000 000176 (v01 DELL    QA09    00000002 LOHR 00000001)
[    0.000000] ACPI: SSDT 00000000baffc000 000166 (v01 DELL   PtidDevc 00001000 INTL 20061109)
[    0.000000] ACPI: ASF! 00000000baff1000 0000A5 (v32 DELL    QA09    00000002 LOHR 00000002)
[    0.000000] ACPI: HPET 00000000bafee000 000038 (v01 DELL    QA09    00000002 LOHR 00000002)
[    0.000000] ACPI: APIC 00000000bafed000 000098 (v01 DELL    QA09    00000002 LOHR 00000002)
[    0.000000] ACPI: MCFG 00000000bafec000 00003C (v01 DELL    QA09    00000002 LOHR 00000002)
[    0.000000] ACPI: FPDT 00000000bafeb000 000064 (v01 DELL    QA09    00000002 LOHR 00000002)
[    0.000000] ACPI: SSDT 00000000bafea000 000860 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bafe9000 000A92 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: UEFI 00000000bafe8000 00003E (v01 DELL    QA09    00000002 LOHR 00000002)
[    0.000000] ACPI: UEFI 00000000bafe7000 000042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: POAT 00000000bafe6000 000055 (v03 DELL    QA09    00000002 LOHR 00000002)
[    0.000000] ACPI: SSDT 00000000bafe3000 000DAE (v01 NvORef NvOptTbl 00001000 INTL 20061109)
[    0.000000] ACPI: UEFI 00000000bafe2000 00027E (v01 DELL    QA09    00000002 LOHR 00000002)
[    0.000000] ACPI: DBG2 00000000bafe0000 000070 (v00 DELL    QA09    00000002 LOHR 00000002)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x23f5fffff]
[    0.000000]   NODE_DATA [mem 0x23f5f2000-0x23f5f6fff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880236c00000-ffff88023ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x23f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0xa9094fff]
[    0.000000]   node   0: [mem 0xa9297000-0xb813dfff]
[    0.000000]   node   0: [mem 0xbafff000-0xbaffffff]
[    0.000000]   node   0: [mem 0x100000000-0x23f5fffff]
[    0.000000] On node 0 totalpages: 2061016
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11701 pages used for memmap
[    0.000000]   DMA32 zone: 748860 pages, LIFO batch:31
[    0.000000]   Normal zone: 20440 pages used for memmap
[    0.000000]   Normal zone: 1308160 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40004000-0x40004fff]
[    0.000000] PM: Registered nosave memory: [mem 0xa9095000-0xa9296fff]
[    0.000000] PM: Registered nosave memory: [mem 0xb813e000-0xbaeeefff]
[    0.000000] PM: Registered nosave memory: [mem 0xbaeef000-0xbaf9efff]
[    0.000000] PM: Registered nosave memory: [mem 0xbaf9f000-0xbaffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb000000-0xbf9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfa00000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed07fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed08000-0xfed08fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed09000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff97ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff980000-0xffffffff]
[    0.000000] e820: [mem 0xbfa00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88023f200000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2028790
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-33-generic root=UUID=aa3bcf90-6e11-4e16-87cf-e3bcb81161f5 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8002876K/8244064K available (7363K kernel code, 1142K rwdata, 3400K rodata, 1336K init, 1440K bss, 241188K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2095.170 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4190.34 BogoMIPS (lpj=8380680)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000029] Security Framework initialized
[    0.000046] AppArmor: AppArmor initialized
[    0.000047] Yama: becoming mindful.
[    0.000694] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.003034] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004086] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.004098] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.004307] Initializing cgroup subsys memory
[    0.004313] Initializing cgroup subsys devices
[    0.004314] Initializing cgroup subsys freezer
[    0.004316] Initializing cgroup subsys blkio
[    0.004317] Initializing cgroup subsys perf_event
[    0.004320] Initializing cgroup subsys hugetlb
[    0.004343] CPU: Physical Processor ID: 0
[    0.004344] CPU: Processor Core ID: 0
[    0.004349] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.004349] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.004775] mce: CPU supports 9 MCE banks
[    0.004787] CPU0: Thermal monitoring handled by SMI
[    0.004796] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.004796] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.004796] tlb_flushall_shift: 2
[    0.004934] Freeing SMP alternatives memory: 32K (ffffffff81e6d000 - ffffffff81e75000)
[    0.006247] ACPI: Core revision 20131115
[    0.012030] ACPI: All ACPI Tables successfully acquired
[    0.012298] ftrace: allocating 28495 entries in 112 pages
[    0.028116] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067822] smpboot: CPU0: Intel(R) Core(TM) i7-3612QM CPU @ 2.10GHz (fam: 06, model: 3a, stepping: 09)
[    0.067830] TSC deadline timer enabled
[    0.067839] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.067846] ... version:                3
[    0.067847] ... bit width:              48
[    0.067848] ... generic registers:      4
[    0.067849] ... value mask:             0000ffffffffffff
[    0.067850] ... max period:             0000ffffffffffff
[    0.067851] ... fixed-purpose events:   3
[    0.067852] ... event mask:             000000070000000f
[    0.069654] x86: Booting SMP configuration:
[    0.081165] CPU1: Thermal monitoring handled by SMI
[    0.083308] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.094891] CPU2: Thermal monitoring handled by SMI
[    0.108529] CPU3: Thermal monitoring handled by SMI
[    0.122188] CPU4: Thermal monitoring handled by SMI
[    0.135826] CPU5: Thermal monitoring handled by SMI
[    0.149473] CPU6: Thermal monitoring handled by SMI
[    0.163212] CPU7: Thermal monitoring handled by SMI
[    0.069656] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.165366] x86: Booted up 1 node, 8 CPUs
[    0.165370] smpboot: Total of 8 processors activated (33522.72 BogoMIPS)
[    0.173462] devtmpfs: initialized
[    0.176324] EVM: security.selinux
[    0.176325] EVM: security.SMACK64
[    0.176326] EVM: security.ima
[    0.176327] EVM: security.capability
[    0.176373] PM: Registering ACPI NVS region [mem 0xbaeef000-0xbaf9efff] (720896 bytes)
[    0.177235] pinctrl core: initialized pinctrl subsystem
[    0.177298] regulator-dummy: no parameters
[    0.177330] RTC time:  2:43:44, date: 08/12/14
[    0.177365] NET: Registered protocol family 16
[    0.177463] cpuidle: using governor ladder
[    0.177465] cpuidle: using governor menu
[    0.177500] ACPI: bus type PCI registered
[    0.177502] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.177564] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.177566] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.184694] PCI: Using configuration type 1 for base access
[    0.184958] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.184959] mtrr: probably your BIOS does not setup all CPUs.
[    0.184960] mtrr: corrected configuration.
[    0.185686] bio: create slab <bio-0> at 0
[    0.185865] ACPI: Added _OSI(Module Device)
[    0.185867] ACPI: Added _OSI(Processor Device)
[    0.185868] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.185870] ACPI: Added _OSI(Processor Aggregator Device)
[    0.188652] ACPI: Executed 2 blocks of module-level executable AML code
[    0.197273] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.197738] ACPI: SSDT 00000000bae8e018 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.198102] ACPI: Dynamic OEM Table Load:
[    0.198104] ACPI: SSDT           (null) 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.201461] ACPI: SSDT 00000000bae8fa98 000303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.201848] ACPI: Dynamic OEM Table Load:
[    0.201849] ACPI: SSDT           (null) 000303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.205335] ACPI: SSDT 00000000bae8dd98 000119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.205688] ACPI: Dynamic OEM Table Load:
[    0.205690] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.211718] ACPI: Interpreter enabled
[    0.211725] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.211730] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.211745] ACPI: (supports S0 S3 S4 S5)
[    0.211746] ACPI: Using IOAPIC for interrupt routing
[    0.211771] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.211901] ACPI: No dock devices found.
[    0.217723] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.217729] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.217854] \_SB_.PCI0:_OSC invalid UUID
[    0.217856] _OSC request data:1 1f 0 
[    0.217860] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.218520] PCI host bridge to bus 0000:00
[    0.218523] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.218525] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.218527] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.218529] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.218531] pci_bus 0000:00: root bus resource [mem 0xbfa00000-0xfeafffff]
[    0.218539] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    0.218614] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.218647] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.218680] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.218713] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    0.218725] pci 0000:00:02.0: reg 0x10: [mem 0xf1000000-0xf13fffff 64bit]
[    0.218732] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.218737] pci 0000:00:02.0: reg 0x20: [io  0x4000-0x403f]
[    0.218829] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.218853] pci 0000:00:14.0: reg 0x10: [mem 0xf1600000-0xf160ffff 64bit]
[    0.218930] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.218963] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.218996] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.219018] pci 0000:00:16.0: reg 0x10: [mem 0xf1615000-0xf161500f 64bit]
[    0.219088] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.219161] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.219185] pci 0000:00:1a.0: reg 0x10: [mem 0xf161a000-0xf161a3ff]
[    0.219282] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.219332] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.219366] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.219383] pci 0000:00:1b.0: reg 0x10: [mem 0xf1610000-0xf1613fff 64bit]
[    0.219457] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.219524] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.219651] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.219698] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.219731] pci 0000:00:1c.4: [8086:1e18] type 01 class 0x060400
[    0.219815] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.219853] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.219890] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.219914] pci 0000:00:1d.0: reg 0x10: [mem 0xf1619000-0xf16193ff]
[    0.220011] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.220057] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.220090] pci 0000:00:1f.0: [8086:1e57] type 00 class 0x060100
[    0.220259] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.220280] pci 0000:00:1f.2: reg 0x10: [io  0x4098-0x409f]
[    0.220289] pci 0000:00:1f.2: reg 0x14: [io  0x40bc-0x40bf]
[    0.220298] pci 0000:00:1f.2: reg 0x18: [io  0x4090-0x4097]
[    0.220307] pci 0000:00:1f.2: reg 0x1c: [io  0x40b8-0x40bb]
[    0.220316] pci 0000:00:1f.2: reg 0x20: [io  0x4060-0x407f]
[    0.220325] pci 0000:00:1f.2: reg 0x24: [mem 0xf1618000-0xf16187ff]
[    0.220374] pci 0000:00:1f.2: PME# supported from D3hot
[    0.220431] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.220449] pci 0000:00:1f.3: reg 0x10: [mem 0xf1614000-0xf16140ff 64bit]
[    0.220472] pci 0000:00:1f.3: reg 0x20: [io  0xefa0-0xefbf]
[    0.220586] pci 0000:01:00.0: [10de:0fd2] type 00 class 0x030000
[    0.220594] pci 0000:01:00.0: reg 0x10: [mem 0xf0000000-0xf0ffffff]
[    0.220602] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.220610] pci 0000:01:00.0: reg 0x1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.220615] pci 0000:01:00.0: reg 0x24: [io  0x3000-0x307f]
[    0.220621] pci 0000:01:00.0: reg 0x30: [mem 0xfff80000-0xffffffff pref]
[    0.220660] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.225277] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.225296] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.225298] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf0ffffff]
[    0.225302] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.225455] pci 0000:02:00.0: [8086:0887] type 00 class 0x028000
[    0.225504] pci 0000:02:00.0: reg 0x10: [mem 0xf1500000-0xf1501fff 64bit]
[    0.225740] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.225788] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.233362] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.233369] pci 0000:00:1c.0:   bridge window [mem 0xf1500000-0xf15fffff]
[    0.233463] pci 0000:03:00.0: [1969:1091] type 00 class 0x020000
[    0.233493] pci 0000:03:00.0: reg 0x10: [mem 0xf1400000-0xf143ffff 64bit]
[    0.233509] pci 0000:03:00.0: reg 0x18: [io  0x2000-0x207f]
[    0.233644] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.233682] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.241321] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.241325] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    0.241330] pci 0000:00:1c.4:   bridge window [mem 0xf1400000-0xf14fffff]
[    0.241838] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.241893] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.241945] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.241996] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.242047] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.242098] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.242150] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.242201] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.242435] ACPI: Enabled 5 GPEs in block 00 to 3F
[    0.242442] ACPI: \_SB_.PCI0: notify handler is installed
[    0.242489] Found 1 acpi root devices
[    0.242586] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.242673] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.242677] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.242679] vgaarb: loaded
[    0.242680] vgaarb: bridge control possible 0000:01:00.0
[    0.242681] vgaarb: no bridge control possible 0000:00:02.0
[    0.242819] SCSI subsystem initialized
[    0.242856] libata version 3.00 loaded.
[    0.242874] ACPI: bus type USB registered
[    0.242888] usbcore: registered new interface driver usbfs
[    0.242895] usbcore: registered new interface driver hub
[    0.242914] usbcore: registered new device driver usb
[    0.243021] PCI: Using ACPI for IRQ routing
[    0.244685] PCI: pci_cache_line_size set to 64 bytes
[    0.244785] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.244786] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.244788] e820: reserve RAM buffer [mem 0xa9095000-0xabffffff]
[    0.244789] e820: reserve RAM buffer [mem 0xb813e000-0xbbffffff]
[    0.244791] e820: reserve RAM buffer [mem 0xbb000000-0xbbffffff]
[    0.244792] e820: reserve RAM buffer [mem 0x23f600000-0x23fffffff]
[    0.244864] NetLabel: Initializing
[    0.244865] NetLabel:  domain hash size = 128
[    0.244866] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.244878] NetLabel:  unlabeled traffic allowed by default
[    0.244929] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.244934] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.246975] Switched to clocksource hpet
[    0.251324] AppArmor: AppArmor Filesystem Enabled
[    0.251344] pnp: PnP ACPI init
[    0.251356] ACPI: bus type PNP registered
[    0.251387] pnp 00:00: [dma 4]
[    0.251405] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.251500] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.251526] pnp 00:02: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.251569] system 00:03: [io  0x0680-0x069f] has been reserved
[    0.251571] system 00:03: [io  0x1000-0x1003] has been reserved
[    0.251573] system 00:03: [io  0x1004-0x1013] has been reserved
[    0.251575] system 00:03: [io  0xffff] has been reserved
[    0.251577] system 00:03: [io  0x0400-0x0453] could not be reserved
[    0.251579] system 00:03: [io  0x0458-0x047f] has been reserved
[    0.251580] system 00:03: [io  0x0500-0x057f] has been reserved
[    0.251582] system 00:03: [io  0x164e-0x164f] has been reserved
[    0.251585] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.251606] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.251650] system 00:05: [io  0x0454-0x0457] has been reserved
[    0.251653] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.251691] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.251719] pnp 00:07: Plug and Play ACPI device, IDs DLL055f PNP0f13 (active)
[    0.251822] pnp 00:08: disabling [mem 0xfffff000-0xffffffff] because it overlaps 0000:01:00.0 BAR 6 [mem 0xfff80000-0xffffffff pref]
[    0.251840] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.251843] system 00:08: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.251844] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.251846] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.251848] system 00:08: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.251850] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.251852] system 00:08: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.251854] system 00:08: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.251856] system 00:08: [mem 0xff000000-0xffffffff] could not be reserved
[    0.251858] system 00:08: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.251860] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.252095] pnp: PnP ACPI: found 9 devices
[    0.252097] ACPI: bus type PNP unregistered
[    0.258346] pci 0000:01:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
[    0.258376] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x80000)
[    0.258378] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.258381] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.258384] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf0ffffff]
[    0.258387] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.258390] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.258398] pci 0000:00:1c.0:   bridge window [mem 0xf1500000-0xf15fffff]
[    0.258410] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.258413] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    0.258418] pci 0000:00:1c.4:   bridge window [mem 0xf1400000-0xf14fffff]
[    0.258428] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.258430] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.258432] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.258434] pci_bus 0000:00: resource 7 [mem 0xbfa00000-0xfeafffff]
[    0.258435] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.258437] pci_bus 0000:01: resource 1 [mem 0xf0000000-0xf0ffffff]
[    0.258439] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.258441] pci_bus 0000:02: resource 1 [mem 0xf1500000-0xf15fffff]
[    0.258443] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.258444] pci_bus 0000:03: resource 1 [mem 0xf1400000-0xf14fffff]
[    0.258471] NET: Registered protocol family 2
[    0.258630] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.258799] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.258929] TCP: Hash tables configured (established 65536 bind 65536)
[    0.258946] TCP: reno registered
[    0.258958] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.258998] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.259067] NET: Registered protocol family 1
[    0.259079] pci 0000:00:02.0: Boot video device
[    0.259530] pci 0000:03:00.0: set MSI_INTX_DISABLE_BUG flag
[    0.259535] PCI: CLS 64 bytes, default 64
[    0.259585] Trying to unpack rootfs image as initramfs...
[    0.719425] Freeing initrd memory: 26468K (ffff880034c3e000 - ffff880036617000)
[    0.719430] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.719432] software IO TLB [mem 0xb413e000-0xb813e000] (64MB) mapped at [ffff8800b413e000-ffff8800b813dfff]
[    0.719736] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x12
[    0.719743] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x12
[    0.719755] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x12
[    0.719763] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x12
[    0.719769] microcode: CPU4 sig=0x306a9, pf=0x10, revision=0x12
[    0.719777] microcode: CPU5 sig=0x306a9, pf=0x10, revision=0x12
[    0.719784] microcode: CPU6 sig=0x306a9, pf=0x10, revision=0x12
[    0.719792] microcode: CPU7 sig=0x306a9, pf=0x10, revision=0x12
[    0.719839] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.719840] Scanning for low memory corruption every 60 seconds
[    0.720096] Initialise system trusted keyring
[    0.720137] audit: initializing netlink socket (disabled)
[    0.720147] type=2000 audit(1407811424.700:1): initialized
[    0.749982] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.751068] zbud: loaded
[    0.751212] VFS: Disk quotas dquot_6.5.2
[    0.751250] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.751637] fuse init (API version 7.22)
[    0.751703] msgmni has been set to 15682
[    0.751752] Key type big_key registered
[    0.752211] Key type asymmetric registered
[    0.752213] Asymmetric key parser 'x509' registered
[    0.752239] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.752286] io scheduler noop registered
[    0.752287] io scheduler deadline registered (default)
[    0.752307] io scheduler cfq registered
[    0.752463] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.752726] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.752738] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.752774] intel_idle: MWAIT substates: 0x21120
[    0.752776] intel_idle: v0.4 model 0x3A
[    0.752777] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.752942] ipmi message handler version 39.2
[    0.959400] ACPI: AC Adapter [ADP0] (on-line)
[    0.959479] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.959484] ACPI: Power Button [PWRB]
[    0.959511] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.959513] ACPI: Sleep Button [SLPB]
[    0.959541] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.959966] ACPI: Lid Switch [LID0]
[    0.960000] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.960003] ACPI: Power Button [PWRF]
[    0.963577] thermal LNXTHERM:00: registered as thermal_zone0
[    0.963580] ACPI: Thermal Zone [TZ00] (60 C)
[    0.963809] thermal LNXTHERM:01: registered as thermal_zone1
[    0.963810] ACPI: Thermal Zone [TZ01] (60 C)
[    0.963830] GHES: HEST is not enabled!
[    0.963909] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.967486] Linux agpgart interface v0.103
[    0.969237] brd: module loaded
[    0.969950] loop: module loaded
[    0.970250] libphy: Fixed MDIO Bus: probed
[    0.970327] tun: Universal TUN/TAP device driver, 1.6
[    0.970329] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.970399] PPP generic driver version 2.4.2
[    0.970455] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.970458] ehci-pci: EHCI PCI platform driver
[    0.970592] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.970599] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.970613] ehci-pci 0000:00:1a.0: debug port 2
[    0.971065] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.971071] ACPI: Battery Slot [BAT0] (battery present)
[    0.974530] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.974546] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf161a000
[    0.983426] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.983474] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.983476] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.983478] usb usb1: Product: EHCI Host Controller
[    0.983479] usb usb1: Manufacturer: Linux 3.13.0-33-generic ehci_hcd
[    0.983481] usb usb1: SerialNumber: 0000:00:1a.0
[    0.983611] hub 1-0:1.0: USB hub found
[    0.983619] hub 1-0:1.0: 2 ports detected
[    0.983804] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.983808] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.983821] ehci-pci 0000:00:1d.0: debug port 2
[    0.987723] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.987736] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf1619000
[    0.999412] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.999458] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.999460] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.999461] usb usb2: Product: EHCI Host Controller
[    0.999463] usb usb2: Manufacturer: Linux 3.13.0-33-generic ehci_hcd
[    0.999465] usb usb2: SerialNumber: 0000:00:1d.0
[    0.999590] hub 2-0:1.0: USB hub found
[    0.999597] hub 2-0:1.0: 2 ports detected
[    0.999694] ehci-platform: EHCI generic platform driver
[    0.999701] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.999702] ohci-pci: OHCI PCI platform driver
[    0.999709] ohci-platform: OHCI generic platform driver
[    0.999714] uhci_hcd: USB Universal Host Controller Interface driver
[    0.999810] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.999815] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.999912] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.999933] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    1.000001] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.000003] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.000004] usb usb3: Product: xHCI Host Controller
[    1.000006] usb usb3: Manufacturer: Linux 3.13.0-33-generic xhci_hcd
[    1.000007] usb usb3: SerialNumber: 0000:00:14.0
[    1.000122] hub 3-0:1.0: USB hub found
[    1.000133] hub 3-0:1.0: 4 ports detected
[    1.000434] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.000437] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.000477] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.000479] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.000481] usb usb4: Product: xHCI Host Controller
[    1.000482] usb usb4: Manufacturer: Linux 3.13.0-33-generic xhci_hcd
[    1.000484] usb usb4: SerialNumber: 0000:00:14.0
[    1.000595] hub 4-0:1.0: USB hub found
[    1.000605] hub 4-0:1.0: 4 ports detected
[    1.007522] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.011618] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.011623] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.011855] mousedev: PS/2 mouse device common for all mice
[    1.012248] rtc_cmos 00:04: RTC can wake from S4
[    1.012369] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.012400] rtc_cmos 00:04: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.012458] device-mapper: uevent: version 1.0.3
[    1.012511] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.012517] ledtrig-cpu: registered to indicate activity on CPUs
[    1.012614] TCP: cubic registered
[    1.012686] NET: Registered protocol family 10
[    1.012845] NET: Registered protocol family 17
[    1.012854] Key type dns_resolver registered
[    1.013248] Loading compiled-in X.509 certificates
[    1.014200] Loaded X.509 cert 'Magrathea: Glacier signing key: 868cfa5c25f811a3fe9005dde26823838b90f688'
[    1.014210] registered taskstats version 1
[    1.017164] Key type trusted registered
[    1.019871] Key type encrypted registered
[    1.020657] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.022549] AppArmor: AppArmor sha1 policy hashing enabled
[    1.022552] IMA: No TPM chip found, activating TPM-bypass!
[    1.022902] regulator-dummy: disabling
[    1.023052]   Magic number: 10:805:712
[    1.023163] rtc_cmos 00:04: setting system clock to 2014-08-12 02:43:45 UTC (1407811425)
[    1.024322] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.024323] EDD information not available.
[    1.024354] PM: Hibernation image not present or could not be loaded.
[    1.025093] Freeing unused kernel memory: 1336K (ffffffff81d1f000 - ffffffff81e6d000)
[    1.025095] Write protecting the kernel read-only data: 12288k
[    1.026839] Freeing unused kernel memory: 816K (ffff880001734000 - ffff880001800000)
[    1.028274] Freeing unused kernel memory: 696K (ffff880001b52000 - ffff880001c00000)
[    1.039532] systemd-udevd[144]: starting version 204
[    1.260950] ahci 0000:00:1f.2: version 3.0
[    1.261049] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.261847] [drm] Initialized drm 1.1.0 20060810
[    1.270840] alx 0000:03:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [5c:f9:dd:48:b8:fe]
[    1.275612] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x9 impl SATA mode
[    1.275618] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.283947] scsi0 : ahci
[    1.284080] scsi1 : ahci
[    1.284174] scsi2 : ahci
[    1.284268] scsi3 : ahci
[    1.284384] scsi4 : ahci
[    1.284488] scsi5 : ahci
[    1.284514] ata1: SATA max UDMA/133 abar m2048@0xf1618000 port 0xf1618100 irq 42
[    1.284515] ata2: DUMMY
[    1.284516] ata3: DUMMY
[    1.284519] ata4: SATA max UDMA/133 abar m2048@0xf1618000 port 0xf1618280 irq 42
[    1.284520] ata5: DUMMY
[    1.284520] ata6: DUMMY
[    1.285376] [drm] Memory usable by graphics device = 2048M
[    1.295630] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.331727] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[    1.331737] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.331738] [drm] Driver supports precise vblank timestamp query.
[    1.331906] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=none
[    1.377793] fbcon: inteldrmfb (fb0) is primary device
[    1.427963] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.427964] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.428246] hub 1-1:1.0: USB hub found
[    1.428344] hub 1-1:1.0: 6 ports detected
[    1.539743] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.603764] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.607760] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.610051] ata1.00: ATA-8: ST1000LM024 HN-M101MBB, 2AR20003, max UDMA/133
[    1.610053] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.616349] ata1.00: configured for UDMA/133
[    1.616517] scsi 0:0:0:0: Direct-Access     ATA      ST1000LM024 HN-M 2AR2 PQ: 0 ANSI: 5
[    1.616684] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.616687] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.616825] sd 0:0:0:0: [sda] Write Protect is off
[    1.616827] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.616956] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.623831] ata4.00: ATAPI: MATSHITA DVD+/-RW UJ8D1, D.02, max UDMA/100
[    1.647870] ata4.00: configured for UDMA/100
[    1.649323] scsi 3:0:0:0: CD-ROM            MATSHITA DVD+-RW UJ8D1    D.02 PQ: 0 ANSI: 5
[    1.668103] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.668104] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.668266] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.668394] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.672136] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.672137] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.672386] hub 2-1:1.0: USB hub found
[    1.672524] hub 2-1:1.0: 8 ports detected
[    1.689525]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
[    1.690318] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.719836] tsc: Refined TSC clocksource calibration: 2095.233 MHz
[    1.840009] usb 3-3: new low-speed USB device number 2 using xhci_hcd
[    1.862094] usb 3-3: New USB device found, idVendor=046d, idProduct=c052
[    1.862097] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.862108] usb 3-3: Product: USB Laser Mouse
[    1.862109] usb 3-3: Manufacturer: Logitech
[    1.862244] usb 3-3: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.865199] hidraw: raw HID events driver (C) Jiri Kosina
[    1.870757] usbcore: registered new interface driver usbhid
[    1.870757] usbhid: USB HID core driver
[    1.871964] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input8
[    1.872068] hid-generic 0003:046D:C052.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:14.0-3/input0
[    1.932174] usb 1-1.3: new high-speed USB device number 3 using ehci-pci
[    2.024970] usb 1-1.3: New USB device found, idVendor=0bda, idProduct=0129
[    2.024973] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.024975] usb 1-1.3: Product: USB2.0-CRW
[    2.024977] usb 1-1.3: Manufacturer: Generic
[    2.024978] usb 1-1.3: SerialNumber: 20100201396000000
[    2.096264] usb 1-1.5: new high-speed USB device number 4 using ehci-pci
[    2.158813] Console: switching to colour frame buffer device 200x56
[    2.161365] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    2.161366] i915 0000:00:02.0: registered panic notifier
[    2.161518] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20131115/video-1246)
[    2.161522] ACPI: Video Device [PEGP] (multi-head: no  rom: yes  post: no)
[    2.161565] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2f/LNXVIDEO:00/input/input9
[    2.164677] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.164965] acpi device:32: registered as cooling_device8
[    2.165029] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input10
[    2.165145] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.253097] input: ALPS PS/2 Device as /devices/platform/i8042/serio1/input/input7
[    2.269197] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input6
[    2.269936] usb 1-1.5: New USB device found, idVendor=0bda, idProduct=58bf
[    2.269939] usb 1-1.5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    2.269942] usb 1-1.5: Product: Laptop_Integrated_Webcam_HD
[    2.269944] usb 1-1.5: Manufacturer: CKFB187F301030031450
[    2.269946] usb 1-1.5: SerialNumber: 0x0001
[    2.344245] usb 2-1.5: new full-speed USB device number 3 using ehci-pci
[    2.440667] usb 2-1.5: New USB device found, idVendor=8087, idProduct=07da
[    2.440674] usb 2-1.5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.624848] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    2.720636] Switched to clocksource tsc
[    2.829127] random: nonblocking pool is initialized
[    2.836783] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[    3.861734] Adding 3998716k swap on /dev/sda5.  Priority:-1 extents:1 across:3998716k FS
[    4.273626] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.598848] systemd-udevd[377]: starting version 204
[    5.282445] lp: driver loaded but no devices found
[    5.322087] ppdev: user-space parallel port driver
[    6.395710] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[    6.395716] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.395722] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    6.395724] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
[    6.395727] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.395727] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    6.395729] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
[    6.395731] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.395732] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    6.485220] wmi: Mapper loaded
[    6.521365] mei_me 0000:00:16.0: irq 44 for MSI/MSI-X
[    6.557408] Bluetooth: Core ver 2.17
[    6.557424] NET: Registered protocol family 31
[    6.557426] Bluetooth: HCI device and connection manager initialized
[    6.557433] Bluetooth: HCI socket layer initialized
[    6.557436] Bluetooth: L2CAP socket layer initialized
[    6.557440] Bluetooth: SCO socket layer initialized
[    6.734025] usbcore: registered new interface driver btusb
[    6.926352] cfg80211: Calling CRDA to update world regulatory domain
[    7.089971] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[    7.288351] nvidia: module license 'NVIDIA' taints kernel.
[    7.288354] Disabling lock debugging due to kernel taint
[    7.290854] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[    7.294227] nvidia 0000:01:00.0: enabling device (0006 -> 0007)
[    7.294285] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[    7.294507] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 1
[    7.294512] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  340.24  Wed Jul  2 14:24:20 PDT 2014
[    7.296581] input: Dell WMI hotkeys as /devices/virtual/input/input11
[    7.310234] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    7.372164] Linux video capture interface: v2.00
[    7.439196] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[    7.442442] scsi6 : SCSI emulation for RTS5139 USB card reader
[    7.442518] usbcore: registered new interface driver rts5139
[    7.442531] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[    7.443043] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    7.508344] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    7.892929] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_HD (0bda:58bf)
[    7.904426] input: Laptop_Integrated_Webcam_HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input12
[    7.904537] usbcore: registered new interface driver uvcvideo
[    7.904539] USB Video Class driver (1.1.1)
[    7.906537] Intel(R) Wireless WiFi driver for Linux, in-tree:
[    7.906540] Copyright(c) 2003-2013 Intel Corporation
[    7.906674] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    7.906776] iwlwifi 0000:02:00.0: irq 45 for MSI/MSI-X
[    7.955550] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[    8.019108] hda_codec: CX20590: BIOS auto-probing.
[    8.019546] autoconfig: line_outs=1 (0x1f/0x0/0x0/0x0/0x0) type:speaker
[    8.019547]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    8.019548]    hp_outs=1 (0x19/0x0/0x0/0x0/0x0)
[    8.019549]    mono: mono_out=0x0
[    8.019549]    inputs:
[    8.019551]      Internal Mic=0x23
[    8.019552]      Mic=0x1a
[    8.020400] hda_codec: Enable sync_write for stable communication
[    8.073413] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    8.155633] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    8.155703] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    8.155764] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    8.238150] intel_rapl: domain uncore energy ctr 176172:176172 not working, skip
[    8.305975] systemd-udevd[542]: failed to execute '/usr/sbin/alsactl' '/usr/sbin/alsactl -E HOME=/var/run/alsa restore 0': No such file or directory
[    8.361285] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    8.759083] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    8.818357] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    8.818361] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    8.818362] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    8.818365] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[    8.818461] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    8.998681] cfg80211: World regulatory domain updated:
[    8.998684] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.998686] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.998687] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.998688] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.998689] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.998690] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.009014] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    9.498969] type=1400 audit(1407811433.965:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=483 comm="apparmor_parser"
[    9.498976] type=1400 audit(1407811433.965:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=483 comm="apparmor_parser"
[    9.498979] type=1400 audit(1407811433.965:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=483 comm="apparmor_parser"
[    9.499156] type=1400 audit(1407811433.965:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=562 comm="apparmor_parser"
[    9.499165] type=1400 audit(1407811433.965:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=562 comm="apparmor_parser"
[    9.499169] type=1400 audit(1407811433.965:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=562 comm="apparmor_parser"
[    9.499176] type=1400 audit(1407811433.965:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=482 comm="apparmor_parser"
[    9.499182] type=1400 audit(1407811433.965:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=482 comm="apparmor_parser"
[    9.499187] type=1400 audit(1407811433.965:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=482 comm="apparmor_parser"
[    9.499355] type=1400 audit(1407811433.965:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=483 comm="apparmor_parser"
[   10.313171] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   10.587291] init: failsafe main process (679) killed by TERM signal
[   14.735845] init: plymouth-upstart-bridge main process ended, respawning
[   14.753524] Bluetooth: RFCOMM TTY layer initialized
[   14.753534] Bluetooth: RFCOMM socket layer initialized
[   14.753540] Bluetooth: RFCOMM ver 1.11
[   14.946900] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.946903] Bluetooth: BNEP filters: protocol multicast
[   14.946910] Bluetooth: BNEP socket layer initialized
[   15.015204] audit_printk_skb: 183 callbacks suppressed
[   15.015207] type=1400 audit(1407811439.481:73): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1064 comm="apparmor_parser"
[   15.015654] type=1400 audit(1407811439.481:74): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1063 comm="apparmor_parser"
[   15.015660] type=1400 audit(1407811439.481:75): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1063 comm="apparmor_parser"
[   15.016012] type=1400 audit(1407811439.481:76): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1063 comm="apparmor_parser"
[   16.650354] init: cups main process (1085) killed by HUP signal
[   16.650365] init: cups main process ended, respawning
[   18.092021] init: plymouth-stop pre-start process (1174) terminated with status 1
[   21.252441] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   21.260082] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[   21.511011] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   21.518663] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[   21.591901] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.592569] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.594268] alx 0000:03:00.0: irq 47 for MSI/MSI-X
[   21.594325] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.595172] alx 0000:03:00.0 eth0: NIC Up: 100 Mbps Full
[   21.595383] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   39.074462] NET: Registered protocol family 24
[   46.261877] type=1400 audit(1407811470.709:77): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1649 comm="apparmor_parser"
[   46.261884] type=1400 audit(1407811470.709:78): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1649 comm="apparmor_parser"
[   46.262235] type=1400 audit(1407811470.709:79): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1649 comm="apparmor_parser"

```

---

