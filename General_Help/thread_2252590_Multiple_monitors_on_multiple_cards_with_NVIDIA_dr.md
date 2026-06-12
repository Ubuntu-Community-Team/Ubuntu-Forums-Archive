---
title: "Multiple monitors on multiple cards with NVIDIA driver"
date: 2014-11-13
forum: General Help
---

### Post by akaylor on 2014-11-13
I'm trying to get two monitors working with two seperate video cards (i.e. not TwinView).  On the base install of Ubuntu (14.04-1) with the xorg Nouvuea driver this works great.  My primary monitor runs off a NVIDIA GTX 660 Ti and the second screen runs off the integrated Intel HD 4600. Unfortunately it seems very unstable so I'm trying to switch to the mfg driver.  As soon as I use the Additional Drivers tool to select the NVIDIA driver (331 or 304) and reboot I lose the second screen.  Same results with the updated 340.58 driver.  I've spent a few days monkeying with an xorg.conf but no dice.

lspci
```
                 
[LIST=1]
[*]00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 Display controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation Device 8cb1
00:16.0 Communication controller: Intel Corporation Device 8cba
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection (2) I218-V
00:1a.0 USB controller: Intel Corporation Device 8cad
00:1b.0 Audio device: Intel Corporation Device 8ca0
00:1c.0 PCI bridge: Intel Corporation Device 8c90 (rev d0)
00:1c.3 PCI bridge: Intel Corporation Device 8c96 (rev d0)
00:1c.6 PCI bridge: Intel Corporation Device 8c9c (rev d0)
00:1d.0 USB controller: Intel Corporation Device 8ca6
00:1f.0 ISA bridge: Intel Corporation Device 8cc4

00:1f.3 SMBus: Intel Corporation Device 8ca2
01:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 660 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
03:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 02)
04:00.0 USB controller: ASMedia Technology Inc. Device 1142 
[/LIST]

         


```
xorg.conf
```
                 
[LIST=1]
[*]Section "Module"

  Load "extmod"
  Load "dbe"
  Load "type1"
  Load "freetype"
  Load "glx"
EndSection
 
Section "Device"
  Identifier "nvidia"
  Driver "nvidia"
#  BusID "01:00.0"
#  Screen 0
#  Option "UseDisplayDevice"    "DFP-0"
#  Option "DynamicTwinView"     "False"
#  Option      "AddARGBGLXVisuals"  "true"
#  Option      "UseEDIDDpi"         "false"
#  Option      "DPI"                "96 x 96"
#  Option      "Coolbits"           "1"
 
  Option "NoLogo" "True"
 
EndSection
 
Section "Device"
  Identifier "intel"
  Driver "intel"
#  BusID "00:02.0"
EndSection
 
Section "Monitor"
  Identifier   "Monitor0"
        
  Option  "dpms"  "on"
EndSection
 
Section "Monitor"
  Identifier   "Monitor1"
  Option  "dpms"  "on"
EndSection
 
Section "Screen"
  Identifier   "MainDisplay"
  Device       "nvidia"
  Monitor      "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Depth     24
    Modes     "1920x1080"
  EndSubsection
EndSection
 
Section "Screen"
  Identifier   "RightDisplay"
  Device       "intel"
  Monitor      "Monitor1"
  DefaultDepth 24
  SubSection "Display"
    Depth     24
    Modes     "1920x1080"
  EndSubsection
EndSection
 
Section "ServerLayout"
        Identifier "Layout0"
        Screen 0 "MainDisplay" 0 0
        Screen 1 "RightDisplay" RightOf "MainDisplay"
EndSection 
[/LIST]

         
```


Xorg.0.log

                 ```

[     3.067] 

X.Org X Server 1.15.1
Release Date: 2014-04-13

[     3.067] X Protocol Version 11, Revision 0
[     3.067] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[     3.067] Current Operating System: Linux monolith 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64
[     3.067] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-39-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash
[     3.067] Build Date: 30 July 2014  12:21:54AM
[     3.067] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[     3.067] Current version of pixman: 0.30.2
[     3.067]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[     3.067] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.067] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 12 22:30:13 2014
[     3.068] (==) Using config file: "/etc/X11/xorg.conf"
[     3.068] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     3.071] (==) ServerLayout "Layout0"
[     3.071] (**) |-->Screen "MainDisplay" (0)
[     3.071] (**) |   |-->Monitor "Monitor0"
[     3.071] (**) |   |-->Device "nvidia"
[     3.071] (**) |-->Screen "RightDisplay" (1)
[     3.071] (**) |   |-->Monitor "Monitor1"
[     3.071] (**) |   |-->Device "intel"
[     3.071] (==) Automatically adding devices
[     3.071] (==) Automatically enabling devices
[     3.071] (==) Automatically adding GPU devices
[     3.072] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.072]    Entry deleted from font path.
[     3.072] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     3.072]    Entry deleted from font path.
[     3.072] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     3.072]    Entry deleted from font path.
[     3.072] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     3.072]    Entry deleted from font path.
[     3.072] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     3.072]    Entry deleted from font path.
[     3.072] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[     3.072] (==) ModulePath set to  "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     3.072] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[     3.072] (II) Loader magic: 0x7fbca4630d40
[     3.072] (II) Module ABI versions:
[     3.072]    X.Org ANSI C Emulation: 0.4
[     3.072]    X.Org Video Driver: 15.0
[     3.072]    X.Org XInput driver : 20.0
[     3.072]    X.Org Server Extension : 8.0
[     3.072] (II) xfree86: Adding drm device (/dev/dri/card1)
[     3.072] (II) xfree86: Adding drm device (/dev/dri/card0)
[     3.073] (--) PCI: (0:0:2:0) 8086:0412:1849:0412 rev 6, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[     3.073] (--) PCI:*(0:1:0:0) 10de:1183:1043:841f  rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/134217728,  0xe8000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     3.074] Initializing built-in extension Generic Event Extension
[     3.074] Initializing built-in extension SHAPE
[     3.074] Initializing built-in extension MIT-SHM
[     3.074] Initializing built-in extension XInputExtension
[     3.074] Initializing built-in extension XTEST
[     3.074] Initializing built-in extension BIG-REQUESTS
[     3.074] Initializing built-in extension SYNC
[     3.074] Initializing built-in extension XKEYBOARD
[     3.074] Initializing built-in extension XC-MISC
[     3.074] Initializing built-in extension SECURITY
[     3.074] Initializing built-in extension XINERAMA
[     3.074] Initializing built-in extension XFIXES
[     3.074] Initializing built-in extension RENDER
[     3.074] Initializing built-in extension RANDR
[     3.074] Initializing built-in extension COMPOSITE
[     3.074] Initializing built-in extension DAMAGE
[     3.074] Initializing built-in extension MIT-SCREEN-SAVER
[     3.074] Initializing built-in extension DOUBLE-BUFFER
[     3.074] Initializing built-in extension RECORD
[     3.074] Initializing built-in extension DPMS
[     3.074] Initializing built-in extension Present
[     3.074] Initializing built-in extension DRI3
[     3.074] Initializing built-in extension X-Resource
[     3.074] Initializing built-in extension XVideo
[     3.074] Initializing built-in extension XVideo-MotionCompensation
[     3.074] Initializing built-in extension SELinux
[     3.074] Initializing built-in extension XFree86-VidModeExtension
[     3.074] Initializing built-in extension XFree86-DGA
[     3.074] Initializing built-in extension XFree86-DRI
[     3.074] Initializing built-in extension DRI2
[     3.074] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[     3.074] (WW) "xmir" is not to be loaded by default. Skipping.
[     3.074] (II) LoadModule: "extmod"
[     3.074] (II) Module "extmod" already built-in
[     3.074] (II) LoadModule: "dbe"
[     3.074] (II) Module "dbe" already built-in
[     3.074] (II) LoadModule: "glx"
[     3.074] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     3.173] (II) Module glx: vendor="NVIDIA Corporation"
[     3.173]    compiled for 4.0.2, module version = 1.0.0
[     3.173]    Module class: X.Org Server Extension
[     3.174] (II) NVIDIA GLX Module  340.58  Fri Oct 31 16:48:52 PDT 2014
[     3.174] Loading extension GLX
[     3.174] (II) LoadModule: "nvidia"
[     3.174] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     3.180] (II) Module nvidia: vendor="NVIDIA Corporation"
[     3.180]    compiled for 4.0.2, module version = 1.0.0
[     3.180]    Module class: X.Org Video Driver
[     3.181] (II) LoadModule: "intel"
[     3.181] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     3.184] (II) Module intel: vendor="X.Org Foundation"
[     3.184]    compiled for 1.15.1, module version = 2.99.916
[     3.184]    Module class: X.Org Video Driver
[     3.184]    ABI class: X.Org Video Driver, version 15.0
[     3.184] (II) NVIDIA dlloader X Driver  340.58  Fri Oct 31 16:27:22 PDT 2014
[     3.184] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     3.184] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[     3.184] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[     3.184] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[     3.184] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[     3.184] (++) using VT number 7
 
[     3.186] (II) Loading sub module "fb"
[     3.186] (II) LoadModule: "fb"
[     3.186] (II) Loading /usr/lib/xorg/modules/libfb.so
[     3.187] (II) Module fb: vendor="X.Org Foundation"
[     3.187]    compiled for 1.15.1, module version = 1.0.0
[     3.187]    ABI class: X.Org ANSI C Emulation, version 0.4
[     3.187] (WW) Unresolved symbol: fbGetGCPrivateKey
[     3.187] (II) Loading sub module "wfb"
[     3.187] (II) LoadModule: "wfb"
[     3.187] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     3.188] (II) Module wfb: vendor="X.Org Foundation"
[     3.188]    compiled for 1.15.1, module version = 1.0.0
[     3.188]    ABI class: X.Org ANSI C Emulation, version 0.4
[     3.188] (II) Loading sub module "ramdac"
[     3.188] (II) LoadModule: "ramdac"
[     3.188] (II) Module "ramdac" already built-in
[     3.190] (II) intel(G0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[     3.190] (II) intel(G0): SNA compiled:  xserver-xorg-video-intel  2:2.99.916+git20141112.f9f85b88-0ubuntu0sarvatt~trusty (Robert Hooker  <sarvatt@ubuntu.com>)
[     3.190] (II) intel(G0): SNA compiled for use with valgrind
[     3.191] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[     3.191] (==) NVIDIA(0): RGB weight 888
[     3.191] (==) NVIDIA(0): Default visual is TrueColor
[     3.191] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     3.191] (**) NVIDIA(0): Option "NoLogo" "True"
[     3.191] (**) NVIDIA(0): Enabling 2D acceleration
[     3.861] (II) NVIDIA(0): Display (BenQ XL2720Z (DFP-0)) supports NVIDIA 3D Vision
[     3.861] (II) NVIDIA(0):     stereo.
[     3.861] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102)
[     3.862] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 660 Ti (GK104) at PCI:1:0:0 (GPU-0)
[     3.862] (--) NVIDIA(0): Memory: 2097152 kBytes
[     3.862] (--) NVIDIA(0): VideoBIOS: 80.04.4b.00.2e
[     3.862] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     3.866] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 660 Ti at PCI:1:0:0
[     3.866] (--) NVIDIA(0):     CRT-0
[     3.866] (--) NVIDIA(0):     BenQ XL2720Z (DFP-0) (boot, connected)
[     3.866] (--) NVIDIA(0):     DFP-1
[     3.866] (--) NVIDIA(0):     DFP-2
[     3.866] (--) NVIDIA(0):     DFP-3
[     3.866] (--) NVIDIA(0):     DFP-4
[     3.866] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     3.866] (--) NVIDIA(0): BenQ XL2720Z (DFP-0): Internal TMDS
[     3.866] (--) NVIDIA(GPU-0): BenQ XL2720Z (DFP-0): 330.0 MHz maximum pixel clock
[     3.866] (--) NVIDIA(0): DFP-1: Internal TMDS
[     3.866] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     3.866] (--) NVIDIA(0): DFP-2: Internal TMDS
[     3.866] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
[     3.866] (--) NVIDIA(0): DFP-3: Internal TMDS
[     3.866] (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
[     3.866] (--) NVIDIA(0): DFP-4: Internal DisplayPort
[     3.866] (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
[     3.866] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     3.866] (**) NVIDIA(0):     device BenQ XL2720Z (DFP-0) (Using EDID frequencies has
[     3.866] (**) NVIDIA(0):     been enabled on all display devices.)
[     3.867] (II) NVIDIA(0): Validated MetaModes:
[     3.867] (II) NVIDIA(0):     "DFP-0:1920x1080"
[     3.867] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[     3.900] (--) NVIDIA(0): DPI set to (81, 80); computed from "UseEdidDpi" X config
[     3.900] (--) NVIDIA(0):     option
[     3.901] (--) intel(G0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[     3.901] (--) intel(G0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[     3.901] (**) intel(G0): Depth 24, (--) framebuffer bpp 32
[     3.901] (==) intel(G0): RGB weight 888
[     3.901] (==) intel(G0): Default visual is TrueColor
[     3.901] (II) intel(G0): Output VGA1 using monitor section Monitor0
[     3.901] (II) intel(G0): Enabled output VGA1
[     3.901] (II) intel(G0): Output HDMI1 has no monitor section
[     3.901] (II) intel(G0): Enabled output HDMI1
[     3.901] (II) intel(G0): Output DP1 has no monitor section
[     3.901] (II) intel(G0): Enabled output DP1
[     3.901] (II) intel(G0): Output HDMI2 has no monitor section
[     3.901] (II) intel(G0): Enabled output HDMI2
[     3.901] (II) intel(G0): Output HDMI3 has no monitor section
[     3.901] (II) intel(G0): Enabled output HDMI3
[     3.901] (--) intel(G0): Using a maximum size of 64x64 for hardware cursors
[     3.901] (II) intel(G0): Output VIRTUAL1 has no monitor section
[     3.901] (II) intel(G0): Enabled output VIRTUAL1
[     3.901] (==) intel(G0): TearFree disabled
[     3.901] (==) intel(G0): DPI set to (96, 96)
[     3.901] (II) Loading sub module "dri3"
[     3.901] (II) LoadModule: "dri3"
[     3.902] (WW) Warning, couldn't open module dri3
[     3.902] (II) UnloadModule: "dri3"
[     3.902] (II) Unloading dri3
[     3.902] (EE) intel: Failed to load module "dri3" (module does not exist, 0)
[     3.902] (II) Loading sub module "dri2"
[     3.902] (II) LoadModule: "dri2"
[     3.902] (II) Module "dri2" already built-in
[     3.902] (II) Loading sub module "present"
[     3.902] (II) LoadModule: "present"
[     3.902] (WW) Warning, couldn't open module present
[     3.902] (II) UnloadModule: "present"
[     3.902] (II) Unloading present
[     3.902] (EE) intel: Failed to load module "present" (module does not exist, 0)
[     3.902] (--) Depth 24 pixmap format is 32 bpp
[     3.904] (II) intel(G0): SNA initialized with Haswell (gen7.5, gt2) backend
[     3.904] (==) intel(G0): Backing store enabled
[     3.904] (==) intel(G0): Silken mouse enabled
[     3.905] (II) intel(G0): HW Cursor enabled
[     3.905] (II) intel(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     3.905] (**) intel(G0): DPMS enabled
[     3.905] (==) intel(G0): display hotplug detection enabled
[     3.905] (II) intel(G0): [DRI2] Setup complete
[     3.905] (II) intel(G0): [DRI2]   DRI driver: i965
[     3.905] (II) intel(G0): [DRI2]   VDPAU driver: i965
[     3.905] (II) intel(G0): direct rendering: DRI2 enabled
[     3.905] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[     3.905] (II) NVIDIA:     access.
[     3.911] (II) NVIDIA(0): Setting mode "DFP-0:1920x1080"
[     3.940] Loading extension NV-GLX
[     3.950] (==) NVIDIA(0): Disabling shared memory pixmaps
[     3.950] (==) NVIDIA(0): Backing store enabled
[     3.950] (==) NVIDIA(0): Silken mouse enabled
[     3.950] (**) NVIDIA(0): DPMS enabled
[     3.950] Loading extension NV-CONTROL
[     3.950] Loading extension XINERAMA
[     3.950] (II) Loading sub module "dri2"
[     3.950] (II) LoadModule: "dri2"
[     3.950] (II) Module "dri2" already built-in
[     3.950] (II) NVIDIA(0): [DRI2] Setup complete
[     3.950] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     3.951] (--) RandR disabled
[     3.953] (II) SELinux: Disabled on system
[     3.954] (II) Initializing extension GLX
[     4.004] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     4.006] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     4.006] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.006] (II) LoadModule: "evdev"
[     4.006] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     4.007] (II) Module evdev: vendor="X.Org Foundation"
[     4.007]    compiled for 1.15.0, module version = 2.8.2
[     4.007]    Module class: X.Org XInput Driver
[     4.007]    ABI class: X.Org XInput driver, version 20.0
[     4.007] (II) Using input driver 'evdev' for 'Power Button'
[     4.007] (**) Power Button: always reports core events
[     4.007] (**) evdev: Power Button: Device: "/dev/input/event2"
[     4.007] (--) evdev: Power Button: Vendor 0 Product 0x1
[     4.007] (--) evdev: Power Button: Found keys
[     4.007] (II) evdev: Power Button: Configuring as keyboard
[     4.007] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[     4.007] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     4.007] (**) Option "xkb_rules" "evdev"
[     4.007] (**) Option "xkb_model" "pc105"
[     4.007] (**) Option "xkb_layout" "us"
[     4.007] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[     4.007] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     4.007] (II) Using input driver 'evdev' for 'Video Bus'
[     4.007] (**) Video Bus: always reports core events
[     4.007] (**) evdev: Video Bus: Device: "/dev/input/event6"
[     4.007] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     4.007] (--) evdev: Video Bus: Found keys
[     4.007] (II) evdev: Video Bus: Configuring as keyboard
[     4.007] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9/event6"
[     4.007] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     4.007] (**) Option "xkb_rules" "evdev"
[     4.007] (**) Option "xkb_model" "pc105"
[     4.007] (**) Option "xkb_layout" "us"
[     4.007] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     4.007] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.007] (II) Using input driver 'evdev' for 'Power Button'
[     4.007] (**) Power Button: always reports core events
[     4.007] (**) evdev: Power Button: Device: "/dev/input/event0"
[     4.007] (--) evdev: Power Button: Vendor 0 Product 0x1
[     4.007] (--) evdev: Power Button: Found keys
[     4.007] (II) evdev: Power Button: Configuring as keyboard
[     4.007] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     4.007] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     4.007] (**) Option "xkb_rules" "evdev"
[     4.007] (**) Option "xkb_model" "pc105"
[     4.007] (**) Option "xkb_layout" "us"
[     4.007] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[     4.007] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[     4.007] (II) Using input driver 'evdev' for 'Sleep Button'
[     4.007] (**) Sleep Button: always reports core events
[     4.007] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[     4.007] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[     4.007] (--) evdev: Sleep Button: Found keys
[     4.007] (II) evdev: Sleep Button: Configuring as keyboard
[     4.007] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[     4.007] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[     4.007] (**) Option "xkb_rules" "evdev"
[     4.007] (**) Option "xkb_model" "pc105"
[     4.007] (**) Option "xkb_layout" "us"
[     4.008] (II) config/udev: Adding drm device  (/dev/dri/card1) card1  /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card1
[     4.008] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[     4.008] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event20)
[     4.008] (II) No input driver specified, ignoring this device.
[     4.008] (II) This device may have been added with another device file.
[     4.008] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event19)
[     4.008] (II) No input driver specified, ignoring this device.
[     4.008] (II) This device may have been added with another device file.
[     4.008] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event18)
[     4.008] (II) No input driver specified, ignoring this device.
[     4.008] (II) This device may have been added with another device file.
[     4.008] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event17)
[     4.008] (II) No input driver specified, ignoring this device.
[     4.008] (II) This device may have been added with another device file.
[     4.008] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[     4.008] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     4.008] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event16)
[     4.008] (II) No input driver specified, ignoring this device.
[     4.008] (II) This device may have been added with another device file.
[     4.008] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event15)
[     4.008] (II) No input driver specified, ignoring this device.
[     4.008] (II) This device may have been added with another device file.
[     4.008] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event14)
[     4.008] (II) No input driver specified, ignoring this device.
[     4.008] (II) This device may have been added with another device file.
[     4.008] (II) config/udev: Adding input device Lite-On Goldtouch USB Keyboard (/dev/input/event3)
[     4.008] (**) Lite-On Goldtouch USB Keyboard: Applying InputClass "evdev keyboard catchall"
[     4.008] (II) Using input driver 'evdev' for 'Lite-On Goldtouch USB Keyboard'
[     4.008] (**) Lite-On Goldtouch USB Keyboard: always reports core events
[     4.008] (**) evdev: Lite-On Goldtouch USB Keyboard: Device: "/dev/input/event3"
[     4.008] (--) evdev: Lite-On Goldtouch USB Keyboard: Vendor 0x4ca Product 0x5d
[     4.008] (--) evdev: Lite-On Goldtouch USB Keyboard: Found keys
[     4.008] (II) evdev: Lite-On Goldtouch USB Keyboard: Configuring as keyboard
[     4.008] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input6/event3"
[     4.008] (II) XINPUT: Adding extended input device "Lite-On Goldtouch USB Keyboard" (type: KEYBOARD, id 10)
[     4.008] (**) Option "xkb_rules" "evdev"
[     4.008] (**) Option "xkb_model" "pc105"
[     4.008] (**) Option "xkb_layout" "us"
[     4.009] (II) config/udev: Adding input device Lite-On Goldtouch USB Keyboard (/dev/input/event4)
[     4.009] (**) Lite-On Goldtouch USB Keyboard: Applying InputClass "evdev keyboard catchall"
[     4.009] (II) Using input driver 'evdev' for 'Lite-On Goldtouch USB Keyboard'
[     4.009] (**) Lite-On Goldtouch USB Keyboard: always reports core events
[     4.009] (**) evdev: Lite-On Goldtouch USB Keyboard: Device: "/dev/input/event4"
[     4.009] (--) evdev: Lite-On Goldtouch USB Keyboard: Vendor 0x4ca Product 0x5d
[     4.009] (--) evdev: Lite-On Goldtouch USB Keyboard: Found 1 mouse buttons
[     4.009] (--) evdev: Lite-On Goldtouch USB Keyboard: Found scroll wheel(s)
[     4.009] (--) evdev: Lite-On Goldtouch USB Keyboard: Found relative axes
[     4.009] (II) evdev: Lite-On Goldtouch USB Keyboard: Forcing relative x/y axes to exist.
[     4.009] (--) evdev: Lite-On Goldtouch USB Keyboard: Found absolute axes
[     4.009] (II) evdev: Lite-On Goldtouch USB Keyboard: Forcing absolute x/y axes to exist.
[     4.009] (--) evdev: Lite-On Goldtouch USB Keyboard: Found keys
[     4.009] (II) evdev: Lite-On Goldtouch USB Keyboard: Configuring as mouse
[     4.009] (II) evdev: Lite-On Goldtouch USB Keyboard: Configuring as keyboard
[     4.009] (II) evdev: Lite-On Goldtouch USB Keyboard: Adding scrollwheel support
[     4.009] (**) evdev: Lite-On Goldtouch USB Keyboard: YAxisMapping: buttons 4 and 5
[     4.009] (**) evdev: Lite-On Goldtouch USB  Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10,  EmulateWheelTimeout: 200
[     4.009] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.1/input/input7/event4"
[     4.009] (II) XINPUT: Adding extended input device "Lite-On Goldtouch USB Keyboard" (type: KEYBOARD, id 11)
[     4.009] (**) Option "xkb_rules" "evdev"
[     4.009] (**) Option "xkb_model" "pc105"
[     4.009] (**) Option "xkb_layout" "us"
[     4.009] (II) evdev: Lite-On Goldtouch USB Keyboard: initialized for relative axes.
[     4.009] (WW) evdev: Lite-On Goldtouch USB Keyboard: ignoring absolute axes.
[     4.009] (**) Lite-On Goldtouch USB Keyboard: (accel) keeping acceleration scheme 1
[     4.009] (**) Lite-On Goldtouch USB Keyboard: (accel) acceleration profile 0
[     4.009] (**) Lite-On Goldtouch USB Keyboard: (accel) acceleration factor: 2.000
[     4.009] (**) Lite-On Goldtouch USB Keyboard: (accel) acceleration threshold: 4
[     4.009] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event13)
[     4.009] (II) No input driver specified, ignoring this device.
[     4.009] (II) This device may have been added with another device file.
[     4.009] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event12)
[     4.009] (II) No input driver specified, ignoring this device.
[     4.009] (II) This device may have been added with another device file.
[     4.009] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event11)
[     4.009] (II) No input driver specified, ignoring this device.
[     4.009] (II) This device may have been added with another device file.
[     4.009] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event10)
[     4.009] (II) No input driver specified, ignoring this device.
[     4.009] (II) This device may have been added with another device file.
[     4.009] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event9)
[     4.009] (II) No input driver specified, ignoring this device.
[     4.009] (II) This device may have been added with another device file.
[     4.009] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event8)
[     4.009] (II) No input driver specified, ignoring this device.
[     4.009] (II) This device may have been added with another device file.
[     4.010] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event7)
[     4.010] (II) No input driver specified, ignoring this device.
[     4.010] (II) This device may have been added with another device file.
[     4.010] (II) config/udev: Adding input device Kensington      Kensington Expert Mouse (/dev/input/event5)
[     4.010] (**) Kensington      Kensington Expert Mouse: Applying InputClass "evdev pointer catchall"
[     4.010] (II) Using input driver 'evdev' for 'Kensington      Kensington Expert Mouse'
[     4.010] (**) Kensington      Kensington Expert Mouse: always reports core events
[     4.010] (**) evdev: Kensington      Kensington Expert Mouse: Device: "/dev/input/event5"
[     4.010] (--) evdev: Kensington      Kensington Expert Mouse: Vendor 0x47d Product 0x1020
[     4.010] (--) evdev: Kensington      Kensington Expert Mouse: Found 8 mouse buttons
[     4.010] (--) evdev: Kensington      Kensington Expert Mouse: Found scroll wheel(s)
[     4.010] (--) evdev: Kensington      Kensington Expert Mouse: Found relative axes
[     4.010] (--) evdev: Kensington      Kensington Expert Mouse: Found x and y relative axes
[     4.010] (II) evdev: Kensington      Kensington Expert Mouse: Configuring as mouse
[     4.010] (II) evdev: Kensington      Kensington Expert Mouse: Adding scrollwheel support
[     4.010] (**) evdev: Kensington      Kensington Expert Mouse: YAxisMapping: buttons 4 and 5
[     4.010] (**) evdev: Kensington      Kensington  Expert Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10,  EmulateWheelTimeout: 200
[     4.010] (**) Option "config_info"  "udev:/sys/devices/pci0000:00/0000:00:1c.6/0000:04:00.0/usb5/5-1/5-1:1.0/input/input8/event5"
[     4.010] (II) XINPUT: Adding extended input device "Kensington      Kensington Expert Mouse" (type: MOUSE, id 12)
[     4.010] (II) evdev: Kensington      Kensington Expert Mouse: initialized for relative axes.
[     4.010] (**) Kensington      Kensington Expert Mouse: (accel) keeping acceleration scheme 1
[     4.010] (**) Kensington      Kensington Expert Mouse: (accel) acceleration profile 0
[     4.010] (**) Kensington      Kensington Expert Mouse: (accel) acceleration factor: 2.000
[     4.010] (**) Kensington      Kensington Expert Mouse: (accel) acceleration threshold: 4
[     4.010] (II) config/udev: Adding input device Kensington      Kensington Expert Mouse (/dev/input/mouse0)
[     4.010] (II) No input driver specified, ignoring this device.
[     4.010] (II) This device may have been added with another device file.
[     4.608] (II) NVIDIA(GPU-0): Display (BenQ XL2720Z (DFP-0)) supports NVIDIA 3D Vision
[     4.608] (II) NVIDIA(GPU-0):     stereo.
[     4.777] (II) NVIDIA(GPU-0): Display (BenQ XL2720Z (DFP-0)) supports NVIDIA 3D Vision
[     4.777] (II) NVIDIA(GPU-0):     stereo.
[    14.388] (II) NVIDIA(GPU-0): Display (BenQ XL2720Z (DFP-0)) supports NVIDIA 3D Vision
[    14.388] (II) NVIDIA(GPU-0):     stereo.
[    14.569] (II) NVIDIA(GPU-0): Display (BenQ XL2720Z (DFP-0)) supports NVIDIA 3D Vision
[    14.569] (II) NVIDIA(GPU-0):     stereo.
[    14.588] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.369] (II) NVIDIA(GPU-0): Display (BenQ XL2720Z (DFP-0)) supports NVIDIA 3D Vision
[    15.369] (II) NVIDIA(GPU-0):     stereo.
[    15.401] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.407] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.450] (II) NVIDIA(GPU-0): Display (BenQ XL2720Z (DFP-0)) supports NVIDIA 3D Vision
[    15.450] (II) NVIDIA(GPU-0):     stereo.
[    15.997] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    28.918] (II) NVIDIA(GPU-0): Display (BenQ XL2720Z (DFP-0)) supports NVIDIA 3D Vision
[    28.918] (II) NVIDIA(GPU-0):     stereo.
[    29.369] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    30.618] (II) NVIDIA(GPU-0): Display (BenQ XL2720Z (DFP-0)) supports NVIDIA 3D Vision
[    30.618] (II) NVIDIA(GPU-0):     stereo.
[    45.709] (II) NVIDIA(GPU-0): Display (BenQ XL2720Z (DFP-0)) supports NVIDIA 3D Vision
[    45.709] (II) NVIDIA(GPU-0):     stereo.
[    45.987] (II) NVIDIA(GPU-0): Display (BenQ XL2720Z (DFP-0)) supports NVIDIA 3D Vision
[    45.987] (II) NVIDIA(GPU-0):     stereo.
[   523.642] (II) NVIDIA(GPU-0): Display (BenQ XL2720Z (DFP-0)) supports NVIDIA 3D Vision
[   523.642] (II) NVIDIA(GPU-0):     stereo.


```

Edited to put logs inline instead of pastebin

---

### Post by akaylor on 2014-11-14
Is there another section of ubuntuforums or a different forum that would be more appropriate for this?

---

### Post by akaylor on 2014-11-14
I decided just to spring for a second NVIDIA card and run two instances of the one driver.  Much easier.  It pop'ed up the first time with my new xorg.conf.

---

