---
title: "Two monitors connected, only one active when desktop loads."
date: 2013-11-08
forum: General Help
---

### Post by Beatsleigher on 2013-11-08
Hey there,
I'm having a slightly (very) annoying problem. Maybe some of you are like me as well, I can't live without at least two displays. It's just so cramped with only one.

Anyways, yesterday I got my PC working again (It's an old HP Compaq D530 SFF, Intel Pentium IV @ 2.8GHz - MPGA478, 2.5GB DDR RAM, nVidia GeForce 6200 GPU - 512MB RAM, S-ATA 320GB HDD, 80GB P-ATA (IDE) HDD) and wanted to install Kubuntu 13.10. The install was partially fine, but I had some display bugs, with some messages not showing correctly (or at all), but the install went fine and the computer booted. I logged on to my desktop and all I had was a background and an open window with no content (It was transparent). I didn't have the taskbar (Or what ever it's called in Kubuntu (XFCE, I think)) at the top and the dock at the bottom didn't show. So I downloaded Kubuntu 12.04 via my Win8 laptop and installed that, I completely gutted the HDD on which Kubuntu was installed. The install went fine, and I have a picture and can use the OS.
Except, I have two connected monitors. One via VGA (main monitor, which is getting a picture now) and one via DVI-D to HDMI (which isn't getting any picture at all).
When I boot the computer and when Kubuntu boots, I get a picture on both monitors. But as soon as Kubuntu has booted, the secondary monitor turns black, but is still recieving a signal (I think!).
I've checked all the system settings and the nVidia X Server configuration program, but it only detects my main monitor. 
Now, I'm a developer and I've just gotten so used to having two monitors side-by-side, that I'm not just going to live with only having one, after all, as I had Windows 7 on this thing, both monitors worked perfectly fine, but Windows is just too resource heavy to get a smooth system, and I need a Linux machine anyway to port my programs to it (I develop in Java, now).

Is this a known bug? If so, how can I get my monitor to work?

Thanks in advance for your help.

---

### Post by TheFu on 2013-11-08
If you have the proprietary nvidia drivers, [http://blog.jdpfu.com/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver](http://blog.jdpfu.com/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver) should help.
If the tools only see 1 monitor, that needs to be resolved before doing anything else.

I'd check the /var/log/Xorg.0.log file for messages.

---

### Post by Beatsleigher on 2013-11-08
> **TheFu said:**
> If you have the proprietary nvidia drivers, [http://blog.jdpfu.com/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver](http://blog.jdpfu.com/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver) should help.
If the tools only see 1 monitor, that needs to be resolved before doing anything else.

I'd check the /var/log/Xorg.0.log file for messages.

Thanks for the reply. I've tried several drivers, from the 'Select new drivers' menu. Nothing worked, it'll boot and shut down with both monitors on and with picture, but the desktop env. only uses one.

Here is the log you told me to check. I couldn't find anything suspicious.

```
[    14.695] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    14.695] X Protocol Version 11, Revision 0
[    14.695] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    14.695] Current Operating System: Linux beatsleigher-HP-d530-SFF-DF492S 3.2.0-52-generic #78-Ubuntu SMP Fri Jul 26 16:23:24 UTC 2013 i686
[    14.695] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-52-generic root=UUID=849b32cd-5129-45a6-82a8-917d750076f1 ro quiet splash vt.handoff=7
[    14.696] Build Date: 16 October 2013  04:45:22PM
[    14.696] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
[    14.696] Current version of pixman: 0.24.4
[    14.696]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    14.696] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.696] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov  8 16:57:44 2013
[    14.701] (==) Using config file: "/etc/X11/xorg.conf"
[    14.701] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.702] (==) No Layout section.  Using the first Screen section.
[    14.702] (==) No screen section available. Using defaults.
[    14.702] (**) |-->Screen "Default Screen Section" (0)
[    14.702] (**) |   |-->Monitor "<default monitor>"
[    14.702] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    14.702] (**) |   |-->Device "Default Device"
[    14.702] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    14.702] (==) Automatically adding devices
[    14.702] (==) Automatically enabling devices
[    14.702] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.702]     Entry deleted from font path.
[    14.702] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.702]     Entry deleted from font path.
[    14.702] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.702]     Entry deleted from font path.
[    14.702] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.703]     Entry deleted from font path.
[    14.703] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.703]     Entry deleted from font path.
[    14.703] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    14.703]     Entry deleted from font path.
[    14.703] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    14.703] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.703] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.703] (II) Loader magic: 0xdb65a0
[    14.703] (II) Module ABI versions:
[    14.703]     X.Org ANSI C Emulation: 0.4
[    14.703]     X.Org Video Driver: 11.0
[    14.703]     X.Org XInput driver : 16.0
[    14.703]     X.Org Server Extension : 6.0
[    14.704] (--) PCI:*(0:1:0:0) 10de:0221:1682:226a rev 161, Mem @ 0xf1000000/16777216, 0xe0000000/268435456, 0xf2000000/16777216, BIOS @ 0x????????/131072
[    14.707] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.708] (II) LoadModule: "extmod"
[    14.709] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.709] (II) Module extmod: vendor="X.Org Foundation"
[    14.709]     compiled for 1.11.3, module version = 1.0.0
[    14.709]     Module class: X.Org Server Extension
[    14.709]     ABI class: X.Org Server Extension, version 6.0
[    14.709] (II) Loading extension MIT-SCREEN-SAVER
[    14.709] (II) Loading extension XFree86-VidModeExtension
[    14.709] (II) Loading extension XFree86-DGA
[    14.709] (II) Loading extension DPMS
[    14.709] (II) Loading extension XVideo
[    14.709] (II) Loading extension XVideo-MotionCompensation
[    14.709] (II) Loading extension X-Resource
[    14.709] (II) LoadModule: "dbe"
[    14.710] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.710] (II) Module dbe: vendor="X.Org Foundation"
[    14.710]     compiled for 1.11.3, module version = 1.0.0
[    14.710]     Module class: X.Org Server Extension
[    14.710]     ABI class: X.Org Server Extension, version 6.0
[    14.710] (II) Loading extension DOUBLE-BUFFER
[    14.710] (II) LoadModule: "glx"
[    14.710] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    15.133] (II) Module glx: vendor="NVIDIA Corporation"
[    15.133]     compiled for 4.0.2, module version = 1.0.0
[    15.133]     Module class: X.Org Server Extension
[    15.133] (II) NVIDIA GLX Module  173.14.37  Wed Mar  6 17:14:50 PST 2013
[    15.133] (II) Loading extension GLX
[    15.133] (II) LoadModule: "record"
[    15.134] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.134] (II) Module record: vendor="X.Org Foundation"
[    15.134]     compiled for 1.11.3, module version = 1.13.0
[    15.134]     Module class: X.Org Server Extension
[    15.134]     ABI class: X.Org Server Extension, version 6.0
[    15.134] (II) Loading extension RECORD
[    15.134] (II) LoadModule: "dri"
[    15.134] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.135] (II) Module dri: vendor="X.Org Foundation"
[    15.135]     compiled for 1.11.3, module version = 1.0.0
[    15.135]     ABI class: X.Org Server Extension, version 6.0
[    15.135] (II) Loading extension XFree86-DRI
[    15.135] (II) LoadModule: "dri2"
[    15.135] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.135] (II) Module dri2: vendor="X.Org Foundation"
[    15.135]     compiled for 1.11.3, module version = 1.2.0
[    15.135]     ABI class: X.Org Server Extension, version 6.0
[    15.135] (II) Loading extension DRI2
[    15.135] (==) Matched nvidia as autoconfigured driver 0
[    15.135] (==) Matched nouveau as autoconfigured driver 1
[    15.135] (==) Matched nv as autoconfigured driver 2
[    15.135] (==) Matched vesa as autoconfigured driver 3
[    15.135] (==) Matched fbdev as autoconfigured driver 4
[    15.135] (==) Assigned the driver to the xf86ConfigLayout
[    15.135] (II) LoadModule: "nvidia"
[    15.135] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    15.155] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.155]     compiled for 4.0.2, module version = 1.0.0
[    15.155]     Module class: X.Org Video Driver
[    15.155] (II) LoadModule: "nouveau"
[    15.156] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    15.156] (II) Module nouveau: vendor="X.Org Foundation"
[    15.156]     compiled for 1.11.3, module version = 0.0.16
[    15.156]     Module class: X.Org Video Driver
[    15.156]     ABI class: X.Org Video Driver, version 11.0
[    15.156] (II) LoadModule: "nv"
[    15.169] (WW) Warning, couldn't open module nv
[    15.169] (II) UnloadModule: "nv"
[    15.169] (II) Unloading nv
[    15.169] (EE) Failed to load module "nv" (module does not exist, 0)
[    15.169] (II) LoadModule: "vesa"
[    15.169] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.170] (II) Module vesa: vendor="X.Org Foundation"
[    15.170]     compiled for 1.11.3, module version = 2.3.0
[    15.170]     Module class: X.Org Video Driver
[    15.170]     ABI class: X.Org Video Driver, version 11.0
[    15.170] (II) LoadModule: "fbdev"
[    15.170] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.170] (II) Module fbdev: vendor="X.Org Foundation"
[    15.170]     compiled for 1.11.3, module version = 0.4.2
[    15.170]     ABI class: X.Org Video Driver, version 11.0
[    15.170] (==) Matched nvidia as autoconfigured driver 0
[    15.170] (==) Matched nouveau as autoconfigured driver 1
[    15.170] (==) Matched nv as autoconfigured driver 2
[    15.170] (==) Matched vesa as autoconfigured driver 3
[    15.170] (==) Matched fbdev as autoconfigured driver 4
[    15.170] (==) Assigned the driver to the xf86ConfigLayout
[    15.171] (II) LoadModule: "nvidia"
[    15.171] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    15.171] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.171]     compiled for 4.0.2, module version = 1.0.0
[    15.171]     Module class: X.Org Video Driver
[    15.171] (II) UnloadModule: "nvidia"
[    15.171] (II) Unloading nvidia
[    15.171] (II) Failed to load module "nvidia" (already loaded, 14142491)
[    15.171] (II) LoadModule: "nouveau"
[    15.171] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    15.171] (II) Module nouveau: vendor="X.Org Foundation"
[    15.171]     compiled for 1.11.3, module version = 0.0.16
[    15.171]     Module class: X.Org Video Driver
[    15.171]     ABI class: X.Org Video Driver, version 11.0
[    15.171] (II) UnloadModule: "nouveau"
[    15.171] (II) Unloading nouveau
[    15.171] (II) Failed to load module "nouveau" (already loaded, 14142491)
[    15.171] (II) LoadModule: "nv"
[    15.172] (WW) Warning, couldn't open module nv
[    15.172] (II) UnloadModule: "nv"
[    15.172] (II) Unloading nv
[    15.172] (EE) Failed to load module "nv" (module does not exist, 0)
[    15.172] (II) LoadModule: "vesa"
[    15.173] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.173] (II) Module vesa: vendor="X.Org Foundation"
[    15.173]     compiled for 1.11.3, module version = 2.3.0
[    15.173]     Module class: X.Org Video Driver
[    15.173]     ABI class: X.Org Video Driver, version 11.0
[    15.173] (II) UnloadModule: "vesa"
[    15.173] (II) Unloading vesa
[    15.173] (II) Failed to load module "vesa" (already loaded, 0)
[    15.173] (II) LoadModule: "fbdev"
[    15.173] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.173] (II) Module fbdev: vendor="X.Org Foundation"
[    15.173]     compiled for 1.11.3, module version = 0.4.2
[    15.173]     ABI class: X.Org Video Driver, version 11.0
[    15.173] (II) UnloadModule: "fbdev"
[    15.173] (II) Unloading fbdev
[    15.173] (II) Failed to load module "fbdev" (already loaded, 0)
[    15.190] (II) NVIDIA dlloader X Driver  173.14.37  Wed Mar  6 17:02:37 PST 2013
[    15.190] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    15.190] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[    15.190] (II) NOUVEAU driver for NVIDIA chipset families :
[    15.190]     RIVA TNT        (NV04)
[    15.191]     RIVA TNT2       (NV05)
[    15.191]     GeForce 256     (NV10)
[    15.191]     GeForce 2       (NV11, NV15)
[    15.191]     GeForce 4MX     (NV17, NV18)
[    15.191]     GeForce 3       (NV20)
[    15.191]     GeForce 4Ti     (NV25, NV28)
[    15.191]     GeForce FX      (NV3x)
[    15.191]     GeForce 6       (NV4x)
[    15.191]     GeForce 7       (G7x)
[    15.191]     GeForce 8       (G8x)
[    15.191]     GeForce GTX 200 (NVA0)
[    15.191]     GeForce GTX 400 (NVC0)
[    15.191] (II) VESA: driver for VESA chipsets: vesa
[    15.191] (II) FBDEV: driver for framebuffer: fbdev
[    15.191] (++) using VT number 7

[    15.191] (II) Loading sub module "fb"
[    15.191] (II) LoadModule: "fb"
[    15.192] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.192] (II) Module fb: vendor="X.Org Foundation"
[    15.192]     compiled for 1.11.3, module version = 1.0.0
[    15.192]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.192] (II) Loading sub module "wfb"
[    15.192] (II) LoadModule: "wfb"
[    15.192] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    15.193] (II) Module wfb: vendor="X.Org Foundation"
[    15.193]     compiled for 1.11.3, module version = 1.0.0
[    15.193]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.193] (II) Loading sub module "ramdac"
[    15.193] (II) LoadModule: "ramdac"
[    15.193] (II) Module "ramdac" already built-in
[    15.193] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    15.193] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    15.193] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.193] (WW) Falling back to old probe method for vesa
[    15.193] (WW) Falling back to old probe method for fbdev
[    15.193] (II) Loading sub module "fbdevhw"
[    15.193] (II) LoadModule: "fbdevhw"
[    15.193] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.194] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.194]     compiled for 1.11.3, module version = 0.0.2
[    15.194]     ABI class: X.Org Video Driver, version 11.0
[    15.194] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    15.194] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    15.194] (==) NVIDIA(0): RGB weight 888
[    15.194] (==) NVIDIA(0): Default visual is TrueColor
[    15.194] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    15.194] (**) NVIDIA(0): Option "NoLogo" "True"
[    15.194] (**) NVIDIA(0): Enabling RENDER acceleration
[    15.194] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    15.194] (II) NVIDIA(0):     enabled.
[    16.764] (II) NVIDIA(0): NVIDIA GPU GeForce 6200 (NV44) at PCI:1:0:0 (GPU-0)
[    16.765] (--) NVIDIA(0): Memory: 524288 kBytes
[    16.765] (--) NVIDIA(0): VideoBIOS: 05.44.a2.10.87
[    16.765] (II) NVIDIA(0): Detected AGP rate: 8X
[    16.765] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    16.765] (--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
[    16.765] (--) NVIDIA(0):     HKC LCD MONITOR (CRT-0)
[    16.765] (--) NVIDIA(0):     Vestel 19W_LCD_TV (DFP-0)
[    16.765] (--) NVIDIA(0): HKC LCD MONITOR (CRT-0): 400.0 MHz maximum pixel clock
[    16.765] (--) NVIDIA(0): Vestel 19W_LCD_TV (DFP-0): 155.0 MHz maximum pixel clock
[    16.765] (--) NVIDIA(0): Vestel 19W_LCD_TV (DFP-0): Internal Single Link TMDS
[    16.765] (WW) NVIDIA(0): The EDID for HKC LCD MONITOR (CRT-0) contradicts itself: mode
[    16.765] (WW) NVIDIA(0):     "800x600" is specified in the EDID; however, the EDID's
[    16.765] (WW) NVIDIA(0):     valid VertRefresh range (60.000-75.000 Hz) would exclude
[    16.765] (WW) NVIDIA(0):     this mode's VertRefresh (56.2 Hz); ignoring VertRefresh
[    16.765] (WW) NVIDIA(0):     check for mode "800x600".
[    16.766] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    16.766] (==) NVIDIA(0): 
[    16.766] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    16.766] (==) NVIDIA(0):     will be used as the requested mode.
[    16.766] (==) NVIDIA(0): 
[    16.766] (II) NVIDIA(0): Validated modes:
[    16.766] (II) NVIDIA(0):     "nvidia-auto-select"
[    16.766] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[    16.767] (--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
[    16.767] (--) NVIDIA(0):     option
[    16.767] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    16.767] (II) UnloadModule: "nouveau"
[    16.767] (II) Unloading nouveau
[    16.767] (II) UnloadModule: "vesa"
[    16.767] (II) Unloading vesa
[    16.767] (II) UnloadModule: "fbdev"
[    16.767] (II) Unloading fbdev
[    16.767] (II) UnloadModule: "fbdevhw"
[    16.767] (II) Unloading fbdevhw
[    16.767] (--) Depth 24 pixmap format is 32 bpp
[    16.769] (II) NVIDIA(0): Initialized AGP GART.
[    16.774] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    16.874] (II) Loading extension NV-GLX
[    16.978] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    16.984] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    16.984] (==) NVIDIA(0): Backing store disabled
[    16.984] (==) NVIDIA(0): Silken mouse enabled
[    16.985] (==) NVIDIA(0): DPMS enabled
[    16.985] (II) Loading extension NV-CONTROL
[    16.985] (==) RandR enabled
[    16.985] (II) Initializing built-in extension Generic Event Extension
[    16.985] (II) Initializing built-in extension SHAPE
[    16.985] (II) Initializing built-in extension MIT-SHM
[    16.985] (II) Initializing built-in extension XInputExtension
[    16.985] (II) Initializing built-in extension XTEST
[    16.985] (II) Initializing built-in extension BIG-REQUESTS
[    16.985] (II) Initializing built-in extension SYNC
[    16.985] (II) Initializing built-in extension XKEYBOARD
[    16.985] (II) Initializing built-in extension XC-MISC
[    16.985] (II) Initializing built-in extension SECURITY
[    16.986] (II) Initializing built-in extension XINERAMA
[    16.986] (II) Initializing built-in extension XFIXES
[    16.986] (II) Initializing built-in extension RENDER
[    16.986] (II) Initializing built-in extension RANDR
[    16.986] (II) Initializing built-in extension COMPOSITE
[    16.986] (II) Initializing built-in extension DAMAGE
[    16.991] (II) Initializing extension GLX
[    17.024] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.030] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    17.030] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.030] (II) LoadModule: "evdev"
[    17.031] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.031] (II) Module evdev: vendor="X.Org Foundation"
[    17.031]     compiled for 1.11.3, module version = 2.7.0
[    17.031]     Module class: X.Org XInput Driver
[    17.031]     ABI class: X.Org XInput driver, version 16.0
[    17.031] (II) Using input driver 'evdev' for 'Power Button'
[    17.031] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.031] (**) Power Button: always reports core events
[    17.031] (**) evdev: Power Button: Device: "/dev/input/event1"
[    17.032] (--) evdev: Power Button: Vendor 0 Product 0x1
[    17.032] (--) evdev: Power Button: Found keys
[    17.032] (II) evdev: Power Button: Configuring as keyboard
[    17.032] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    17.032] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    17.032] (**) Option "xkb_rules" "evdev"
[    17.032] (**) Option "xkb_model" "pc105"
[    17.032] (**) Option "xkb_layout" "gb"
[    17.032] (**) Option "xkb_variant" "extd"
[    17.036] (II) XKB: reuse xkmfile /var/lib/xkb/server-75ECC1FC73DAECCA7C11B68297E66B9B8E3B1F31.xkm
[    17.038] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    17.038] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.038] (II) Using input driver 'evdev' for 'Power Button'
[    17.038] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.038] (**) Power Button: always reports core events
[    17.038] (**) evdev: Power Button: Device: "/dev/input/event0"
[    17.038] (--) evdev: Power Button: Vendor 0 Product 0x1
[    17.038] (--) evdev: Power Button: Found keys
[    17.038] (II) evdev: Power Button: Configuring as keyboard
[    17.038] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    17.038] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    17.038] (**) Option "xkb_rules" "evdev"
[    17.038] (**) Option "xkb_model" "pc105"
[    17.038] (**) Option "xkb_layout" "gb"
[    17.038] (**) Option "xkb_variant" "extd"
[    17.040] (II) config/udev: Adding input device HID 04d9:1400 (/dev/input/event2)
[    17.040] (**) HID 04d9:1400: Applying InputClass "evdev keyboard catchall"
[    17.040] (II) Using input driver 'evdev' for 'HID 04d9:1400'
[    17.040] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.040] (**) HID 04d9:1400: always reports core events
[    17.040] (**) evdev: HID 04d9:1400: Device: "/dev/input/event2"
[    17.040] (--) evdev: HID 04d9:1400: Vendor 0x4d9 Product 0x1400
[    17.040] (--) evdev: HID 04d9:1400: Found keys
[    17.040] (II) evdev: HID 04d9:1400: Configuring as keyboard
[    17.040] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input2/event2"
[    17.040] (II) XINPUT: Adding extended input device "HID 04d9:1400" (type: KEYBOARD, id 8)
[    17.040] (**) Option "xkb_rules" "evdev"
[    17.040] (**) Option "xkb_model" "pc105"
[    17.040] (**) Option "xkb_layout" "gb"
[    17.040] (**) Option "xkb_variant" "extd"
[    17.041] (II) config/udev: Adding input device HID 04d9:1400 (/dev/input/event3)
[    17.041] (**) HID 04d9:1400: Applying InputClass "evdev pointer catchall"
[    17.041] (**) HID 04d9:1400: Applying InputClass "evdev keyboard catchall"
[    17.041] (II) Using input driver 'evdev' for 'HID 04d9:1400'
[    17.042] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.042] (**) HID 04d9:1400: always reports core events
[    17.042] (**) evdev: HID 04d9:1400: Device: "/dev/input/event3"
[    17.042] (--) evdev: HID 04d9:1400: Vendor 0x4d9 Product 0x1400
[    17.042] (--) evdev: HID 04d9:1400: Found 9 mouse buttons
[    17.042] (--) evdev: HID 04d9:1400: Found scroll wheel(s)
[    17.042] (--) evdev: HID 04d9:1400: Found relative axes
[    17.042] (--) evdev: HID 04d9:1400: Found x and y relative axes
[    17.042] (--) evdev: HID 04d9:1400: Found keys
[    17.042] (II) evdev: HID 04d9:1400: Configuring as mouse
[    17.042] (II) evdev: HID 04d9:1400: Configuring as keyboard
[    17.042] (II) evdev: HID 04d9:1400: Adding scrollwheel support
[    17.042] (**) evdev: HID 04d9:1400: YAxisMapping: buttons 4 and 5
[    17.042] (**) evdev: HID 04d9:1400: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.042] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input3/event3"
[    17.042] (II) XINPUT: Adding extended input device "HID 04d9:1400" (type: KEYBOARD, id 9)
[    17.042] (**) Option "xkb_rules" "evdev"
[    17.042] (**) Option "xkb_model" "pc105"
[    17.042] (**) Option "xkb_layout" "gb"
[    17.042] (**) Option "xkb_variant" "extd"
[    17.043] (II) evdev: HID 04d9:1400: initialized for relative axes.
[    17.043] (**) HID 04d9:1400: (accel) keeping acceleration scheme 1
[    17.043] (**) HID 04d9:1400: (accel) acceleration profile 0
[    17.043] (**) HID 04d9:1400: (accel) acceleration factor: 2.000
[    17.043] (**) HID 04d9:1400: (accel) acceleration threshold: 4
[    17.043] (II) config/udev: Adding input device HID 04d9:1400 (/dev/input/mouse0)
[    17.044] (II) No input driver specified, ignoring this device.
[    17.044] (II) This device may have been added with another device file.
[    17.044] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event4)
[    17.044] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    17.044] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    17.044] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.044] (**) Logitech USB Optical Mouse: always reports core events
[    17.044] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event4"
[    17.044] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05b
[    17.044] (--) evdev: Logitech USB Optical Mouse: Found 12 mouse buttons
[    17.045] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[    17.045] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[    17.045] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[    17.045] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[    17.045] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[    17.045] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    17.045] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.045] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4/event4"
[    17.045] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 10)
[    17.045] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[    17.045] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    17.045] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    17.045] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    17.045] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    17.046] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse1)
[    17.046] (II) No input driver specified, ignoring this device.
[    17.046] (II) This device may have been added with another device file.


```

Any other ideas?

---

