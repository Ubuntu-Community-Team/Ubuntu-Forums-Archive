---
title: "Kubuntu 15.10, Intel graphic issues"
date: 2016-04-22
forum: General Help
---

### Post by patxi3 on 2016-04-22
[SIZE=2]Hello,

since I upgraded my Kubuntu version to 15.10, I have graphic issues
Randomly the colors displayed by my screen change,
to such extent that it becames unreadable.
(I already made a post [here]("https://forum.ubuntu-fr.org/viewtopic.php?id=1978141").)

Here are some informations about my computer's hardware:

```

[FONT=monospace][COLOR=#000000]patxi@patxi-HP-EliteBook-820-G1:~$ lscpu[/COLOR]
Architecture:          x86_64
Mode(s) opératoire(s) des processeurs :32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) par cœur : 2
Cœur(s) par socket : 2                                                                        
Socket(s):             1                                                                      
Nœud(s) NUMA :       1                                                                        
Identifiant constructeur :GenuineIntel                                                        
Famille de processeur :6                                                                      
Modèle :             69                                                                       
Model name:            Intel(R) Core(TM) i7-4600U CPU @ 2.10GHz                               
Révision :           1                                                                        
Vitesse du processeur en MHz :2072.777                                                        
CPU max MHz:           3300,0000
CPU min MHz:           800,0000
BogoMIPS:              5387.71
Virtualisation :      VT-x
Cache L1d :           32K
Cache L1i :           32K
Cache L2 :            256K
Cache L3 :            4096K
NUMA node0 CPU(s):     0-3

[/FONT]patxi@patxi-HP-EliteBook-820-G1:~$ lspci | grep "VGA compatible controller"
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)

patxi@patxi-HP-EliteBook-820-G1:~$ sudo dmidecode --type 17
# dmidecode 2.12
SMBIOS 2.7 present.


Handle 0x0008, DMI type 17, 34 bytes
Memory Device
        Array Handle: 0x0007
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 8192 MB
        Form Factor: SODIMM
        Set: None
        Locator: Bottom-Slot 1(left)
        Bank Locator: BANK 0
        Type: DDR3
        Type Detail: Synchronous
        Speed: 1600 MHz
        Manufacturer: Kingston
        Serial Number: E51807FB
        Asset Tag: 9876543210
        Part Number: HP16D3LS1KBG/8G   
        Rank: Unknown
        Configured Clock Speed: Unknown


Handle 0x000A, DMI type 17, 34 bytes
Memory Device
        Array Handle: 0x0007
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 8192 MB
        Form Factor: SODIMM
        Set: None
        Locator: Bottom-Slot 2(right)
        Bank Locator: BANK 2
        Type: DDR3
        Type Detail: Synchronous
        Speed: 1600 MHz
        Manufacturer: Kingston
        Serial Number: E2181EFB
        Asset Tag: 9876543210
        Part Number: HP16D3LS1KBG/8G   
        Rank: Unknown
        Configured Clock Speed: Unknown




```

My /var/log/Xorg.0.log

[/SIZE]```
[   407.168] 
X.Org X Server 1.17.2
Release Date: 2015-06-16
[   407.168] X Protocol Version 11, Revision 0
[   407.168] Build Operating System: Linux 3.13.0-68-generic x86_64 Ubuntu
[   407.168] Current Operating System: Linux patxi-HP-EliteBook-820-G1 4.2.0-27-generic #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016 x86_64
[   407.168] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-27-generic root=UUID=097cd067-1831-4289-9ea9-b1bcec2d4877 ro quiet splash vt.handoff=7
[   407.168] Build Date: 12 November 2015  05:33:29PM
[   407.168] xorg-server 2:1.17.2-1ubuntu9.1 (For technical support please see http://www.ubuntu.com/support) 
[   407.168] Current version of pixman: 0.32.6
[   407.168]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   407.168] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   407.169] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 22 11:46:21 2016
[   407.169] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   407.169] (==) No Layout section.  Using the first Screen section.
[   407.169] (==) No screen section available. Using defaults.
[   407.169] (**) |-->Screen "Default Screen Section" (0)
[   407.169] (**) |   |-->Monitor "<default monitor>"
[   407.169] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   407.169] (==) Automatically adding devices
[   407.169] (==) Automatically enabling devices
[   407.169] (==) Automatically adding GPU devices
[   407.169] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   407.169]     Entry deleted from font path.
[   407.169] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   407.169]     Entry deleted from font path.
[   407.169] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   407.169]     Entry deleted from font path.
[   407.169] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   407.169]     Entry deleted from font path.
[   407.169] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   407.169]     Entry deleted from font path.
[   407.169] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   407.170] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   407.170] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   407.170] (II) Loader magic: 0x563fbee3ad40
[   407.170] (II) Module ABI versions:
[   407.170]     X.Org ANSI C Emulation: 0.4
[   407.170]     X.Org Video Driver: 19.0
[   407.170]     X.Org XInput driver : 21.0
[   407.170]     X.Org Server Extension : 9.0
[   407.170] (II) xfree86: Adding drm device (/dev/dri/card0)
[   407.172] (--) PCI:*(0:0:2:0) 8086:0a16:103c:1991 rev 11, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x00003000/64
[   407.172] (II) LoadModule: "glx"
[   407.172] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   407.173] (II) Module glx: vendor="X.Org Foundation"
[   407.173]     compiled for 1.17.2, module version = 1.0.0
[   407.173]     ABI class: X.Org Server Extension, version 9.0
[   407.173] (==) AIGLX enabled
[   407.174] (==) Matched intel as autoconfigured driver 0
[   407.174] (==) Matched intel as autoconfigured driver 1
[   407.174] (==) Matched modesetting as autoconfigured driver 2
[   407.174] (==) Matched fbdev as autoconfigured driver 3
[   407.174] (==) Matched vesa as autoconfigured driver 4
[   407.174] (==) Assigned the driver to the xf86ConfigLayout
[   407.174] (II) LoadModule: "intel"
[   407.174] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   407.174] (II) Module intel: vendor="X.Org Foundation"
[   407.174]     compiled for 1.17.2, module version = 2.99.917
[   407.174]     Module class: X.Org Video Driver
[   407.174]     ABI class: X.Org Video Driver, version 19.0
[   407.174] (II) LoadModule: "modesetting"
[   407.174] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   407.174] (II) Module modesetting: vendor="X.Org Foundation"
[   407.174]     compiled for 1.17.2, module version = 1.17.2
[   407.174]     Module class: X.Org Video Driver
[   407.174]     ABI class: X.Org Video Driver, version 19.0
[   407.174] (II) LoadModule: "fbdev"
[   407.174] (WW) Warning, couldn't open module fbdev
[   407.174] (II) UnloadModule: "fbdev"
[   407.174] (II) Unloading fbdev
[   407.174] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   407.174] (II) LoadModule: "vesa"
[   407.175] (WW) Warning, couldn't open module vesa
[   407.175] (II) UnloadModule: "vesa"
[   407.175] (II) Unloading vesa
[   407.175] (EE) Failed to load module "vesa" (module does not exist, 0)
[   407.175] (==) Matched intel as autoconfigured driver 0
[   407.175] (==) Matched intel as autoconfigured driver 1
[   407.175] (==) Matched modesetting as autoconfigured driver 2
[   407.175] (==) Matched fbdev as autoconfigured driver 3
[   407.175] (==) Matched vesa as autoconfigured driver 4
[   407.175] (==) Assigned the driver to the xf86ConfigLayout
[   407.175] (II) LoadModule: "intel"
[   407.175] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   407.175] (II) Module intel: vendor="X.Org Foundation"
[   407.175]     compiled for 1.17.2, module version = 2.99.917
[   407.175]     Module class: X.Org Video Driver
[   407.175]     ABI class: X.Org Video Driver, version 19.0
[   407.175] (II) UnloadModule: "intel"
[   407.175] (II) Unloading intel
[   407.175] (II) Failed to load module "intel" (already loaded, 22079)
[   407.175] (II) LoadModule: "modesetting"
[   407.175] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   407.175] (II) Module modesetting: vendor="X.Org Foundation"
[   407.175]     compiled for 1.17.2, module version = 1.17.2
[   407.175]     Module class: X.Org Video Driver
[   407.175]     ABI class: X.Org Video Driver, version 19.0
[   407.175] (II) UnloadModule: "modesetting"
[   407.175] (II) Unloading modesetting
[   407.175] (II) Failed to load module "modesetting" (already loaded, 22079)
[   407.175] (II) LoadModule: "fbdev"
[   407.175] (WW) Warning, couldn't open module fbdev
[   407.175] (II) UnloadModule: "fbdev"
[   407.175] (II) Unloading fbdev
[   407.175] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   407.175] (II) LoadModule: "vesa"
[   407.176] (WW) Warning, couldn't open module vesa
[   407.176] (II) UnloadModule: "vesa"
[   407.176] (II) Unloading vesa
[   407.176] (EE) Failed to load module "vesa" (module does not exist, 0)
[   407.176] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[   407.176] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[   407.176] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[   407.176] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[   407.176] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   407.176] (++) using VT number 7


[   407.176] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20150731
[   407.176] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150808-0ubuntu4 (Robert Ancell <robert.ancell@canonical.com>)
[   407.176] (II) intel(0): SNA compiled for use with valgrind
[   407.176] (WW) Falling back to old probe method for modesetting
[   407.177] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4400
[   407.177] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 2 threads
[   407.177] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   407.177] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   407.177] (==) intel(0): RGB weight 888
[   407.177] (==) intel(0): Default visual is TrueColor
[   407.177] (II) intel(0): Output eDP1 has no monitor section
[   407.192] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[   407.192] (II) intel(0): Enabled output eDP1
[   407.192] (II) intel(0): Output DP1 has no monitor section
[   407.192] (II) intel(0): Enabled output DP1
[   407.192] (II) intel(0): Output HDMI1 has no monitor section
[   407.192] (II) intel(0): Enabled output HDMI1
[   407.192] (II) intel(0): Output DP2 has no monitor section
[   407.192] (II) intel(0): Enabled output DP2
[   407.192] (II) intel(0): Output HDMI2 has no monitor section
[   407.192] (II) intel(0): Enabled output HDMI2
[   407.192] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[   407.192] (II) intel(0): Output VIRTUAL1 has no monitor section
[   407.192] (II) intel(0): Enabled output VIRTUAL1
[   407.192] (--) intel(0): Output eDP1 using initial mode 1366x768 on pipe 0
[   407.192] (--) intel(0): Output DP2 using initial mode 1024x768 on pipe 1
[   407.192] (==) intel(0): TearFree disabled
[   407.192] (==) intel(0): DPI set to (96, 96)
[   407.192] (II) Loading sub module "dri2"
[   407.192] (II) LoadModule: "dri2"
[   407.192] (II) Module "dri2" already built-in
[   407.192] (II) Loading sub module "present"
[   407.192] (II) LoadModule: "present"
[   407.192] (II) Module "present" already built-in
[   407.193] (II) UnloadModule: "modesetting"
[   407.193] (II) Unloading modesetting
[   407.193] (==) Depth 24 pixmap format is 32 bpp
[   407.193] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[   407.193] (==) intel(0): Backing store enabled
[   407.193] (==) intel(0): Silken mouse enabled
[   407.193] (II) intel(0): HW Cursor enabled
[   407.193] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   407.193] (==) intel(0): DPMS enabled
[   407.193] (==) intel(0): Display hotplug detection enabled
[   407.193] (II) intel(0): [DRI2] Setup complete
[   407.193] (II) intel(0): [DRI2]   DRI driver: i965
[   407.193] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[   407.193] (II) intel(0): direct rendering: DRI2 enabled
[   407.193] (II) intel(0): hardware support for Present enabled
[   407.193] (--) RandR disabled
[   407.201] (II) SELinux: Disabled on system
[   407.211] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   407.211] (II) AIGLX: enabled GLX_ARB_create_context
[   407.211] (II) AIGLX: enabled GLX_ARB_create_context_profile
[   407.211] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[   407.211] (II) AIGLX: enabled GLX_INTEL_swap_event
[   407.211] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   407.211] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[   407.211] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[   407.211] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   407.211] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[   407.211] (II) AIGLX: Loaded and initialized i965
[   407.211] (II) GLX: Initialized DRI2 GL provider for screen 0
[   407.213] (II) intel(0): switch to mode 1366x768@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[   407.213] (II) intel(0): switch to mode 1024x768@60.0 on DP2 using pipe 1, position (0, 0), rotation normal, reflection none
[   407.213] (II) intel(0): Setting screen physical size to 361 x 203
[   407.222] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   407.232] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   407.232] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   407.232] (II) LoadModule: "evdev"
[   407.232] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   407.232] (II) Module evdev: vendor="X.Org Foundation"
[   407.232]     compiled for 1.17.1, module version = 2.9.2
[   407.232]     Module class: X.Org XInput Driver
[   407.232]     ABI class: X.Org XInput driver, version 21.0
[   407.232] (II) Using input driver 'evdev' for 'Power Button'
[   407.232] (**) Power Button: always reports core events
[   407.232] (**) evdev: Power Button: Device: "/dev/input/event2"
[   407.232] (--) evdev: Power Button: Vendor 0 Product 0x1
[   407.232] (--) evdev: Power Button: Found keys
[   407.232] (II) evdev: Power Button: Configuring as keyboard
[   407.232] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   407.233] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   407.233] (**) Option "xkb_rules" "evdev"
[   407.233] (**) Option "xkb_model" "pc105"
[   407.233] (**) Option "xkb_layout" "fr"
[   407.233] (**) Option "xkb_variant" "latin9_nodeadkeys"
[   407.235] (II) XKB: reuse xkmfile /var/lib/xkb/server-FEC128768DA53B808E002DA9C388CBDE558017E8.xkm
[   407.236] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[   407.236] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   407.236] (II) Using input driver 'evdev' for 'Video Bus'
[   407.236] (**) Video Bus: always reports core events
[   407.236] (**) evdev: Video Bus: Device: "/dev/input/event4"
[   407.236] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   407.236] (--) evdev: Video Bus: Found keys
[   407.236] (II) evdev: Video Bus: Configuring as keyboard
[   407.236] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10/event4"
[   407.236] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[   407.236] (**) Option "xkb_rules" "evdev"
[   407.236] (**) Option "xkb_model" "pc105"
[   407.236] (**) Option "xkb_layout" "fr"
[   407.236] (**) Option "xkb_variant" "latin9_nodeadkeys"
[   407.236] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[   407.236] (II) No input driver specified, ignoring this device.
[   407.236] (II) This device may have been added with another device file.
[   407.237] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[   407.237] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   407.237] (II) Using input driver 'evdev' for 'Sleep Button'
[   407.237] (**) Sleep Button: always reports core events
[   407.237] (**) evdev: Sleep Button: Device: "/dev/input/event0"
[   407.237] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[   407.237] (--) evdev: Sleep Button: Found keys
[   407.237] (II) evdev: Sleep Button: Configuring as keyboard
[   407.237] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"
[   407.237] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[   407.237] (**) Option "xkb_rules" "evdev"
[   407.237] (**) Option "xkb_model" "pc105"
[   407.237] (**) Option "xkb_layout" "fr"
[   407.237] (**) Option "xkb_variant" "latin9_nodeadkeys"
[   407.238] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event9)
[   407.238] (II) No input driver specified, ignoring this device.
[   407.238] (II) This device may have been added with another device file.
[   407.238] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event10)
[   407.238] (II) No input driver specified, ignoring this device.
[   407.238] (II) This device may have been added with another device file.
[   407.238] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event11)
[   407.238] (II) No input driver specified, ignoring this device.
[   407.238] (II) This device may have been added with another device file.
[   407.239] (II) config/udev: Adding input device HP HD Webcam (/dev/input/event8)
[   407.239] (**) HP HD Webcam: Applying InputClass "evdev keyboard catchall"
[   407.239] (II) Using input driver 'evdev' for 'HP HD Webcam'
[   407.239] (**) HP HD Webcam: always reports core events
[   407.239] (**) evdev: HP HD Webcam: Device: "/dev/input/event8"
[   407.239] (--) evdev: HP HD Webcam: Vendor 0x4f2 Product 0xb3ed
[   407.239] (--) evdev: HP HD Webcam: Found keys
[   407.239] (II) evdev: HP HD Webcam: Configuring as keyboard
[   407.239] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/input/input14/event8"
[   407.239] (II) XINPUT: Adding extended input device "HP HD Webcam" (type: KEYBOARD, id 9)
[   407.239] (**) Option "xkb_rules" "evdev"
[   407.239] (**) Option "xkb_model" "pc105"
[   407.239] (**) Option "xkb_layout" "fr"
[   407.239] (**) Option "xkb_variant" "latin9_nodeadkeys"
[   407.240] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event12)
[   407.240] (II) No input driver specified, ignoring this device.
[   407.240] (II) This device may have been added with another device file.
[   407.240] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event13)
[   407.240] (II) No input driver specified, ignoring this device.
[   407.240] (II) This device may have been added with another device file.
[   407.241] (II) config/udev: Adding input device HDA Intel PCH Dock Line Out (/dev/input/event14)
[   407.241] (II) No input driver specified, ignoring this device.
[   407.241] (II) This device may have been added with another device file.
[   407.241] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event15)
[   407.241] (II) No input driver specified, ignoring this device.
[   407.241] (II) This device may have been added with another device file.
[   407.242] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   407.242] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   407.242] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   407.242] (**) AT Translated Set 2 keyboard: always reports core events
[   407.242] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   407.242] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   407.242] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   407.242] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   407.242] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   407.242] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[   407.242] (**) Option "xkb_rules" "evdev"
[   407.242] (**) Option "xkb_model" "pc105"
[   407.242] (**) Option "xkb_layout" "fr"
[   407.242] (**) Option "xkb_variant" "latin9_nodeadkeys"
[   407.243] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event5)
[   407.243] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[   407.243] (II) Using input driver 'evdev' for 'PS/2 Generic Mouse'
[   407.243] (**) PS/2 Generic Mouse: always reports core events
[   407.243] (**) evdev: PS/2 Generic Mouse: Device: "/dev/input/event5"
[   407.243] (--) evdev: PS/2 Generic Mouse: Vendor 0x2 Product 0x1
[   407.243] (--) evdev: PS/2 Generic Mouse: Found 3 mouse buttons
[   407.243] (--) evdev: PS/2 Generic Mouse: Found relative axes
[   407.243] (--) evdev: PS/2 Generic Mouse: Found x and y relative axes
[   407.243] (II) evdev: PS/2 Generic Mouse: Configuring as mouse
[   407.243] (**) evdev: PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[   407.243] (**) evdev: PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   407.243] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input9/event5"
[   407.243] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE, id 11)
[   407.243] (II) evdev: PS/2 Generic Mouse: initialized for relative axes.
[   407.243] (**) PS/2 Generic Mouse: (accel) keeping acceleration scheme 1
[   407.243] (**) PS/2 Generic Mouse: (accel) acceleration profile 0
[   407.243] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000
[   407.243] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4
[   407.244] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)
[   407.244] (II) No input driver specified, ignoring this device.
[   407.244] (II) This device may have been added with another device file.
[   407.244] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[   407.244] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   407.244] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   407.244] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[   407.244] (II) LoadModule: "synaptics"
[   407.244] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   407.244] (II) Module synaptics: vendor="X.Org Foundation"
[   407.244]     compiled for 1.17.1, module version = 1.8.2
[   407.244]     Module class: X.Org XInput Driver
[   407.244]     ABI class: X.Org XInput driver, version 21.0
[   407.244] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   407.244] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   407.244] (**) Option "Device" "/dev/input/event6"
[   407.280] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1392 - 5708 (res 52)
[   407.280] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1108 - 4660 (res 85)
[   407.280] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   407.280] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   407.280] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[   407.280] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[   407.280] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   407.280] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   407.292] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio3/input/input11/event6"
[   407.292] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[   407.292] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   407.292] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[   407.292] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
[   407.292] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   407.292] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   407.292] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   407.292] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   407.292] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   407.292] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[   407.292] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[   407.293] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event17)
[   407.293] (II) No input driver specified, ignoring this device.
[   407.293] (II) This device may have been added with another device file.
[   407.293] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[   407.293] (II) No input driver specified, ignoring this device.
[   407.293] (II) This device may have been added with another device file.
[   407.294] (II) config/udev: Adding input device HP Wireless hotkeys (/dev/input/event7)
[   407.294] (**) HP Wireless hotkeys: Applying InputClass "evdev keyboard catchall"
[   407.294] (II) Using input driver 'evdev' for 'HP Wireless hotkeys'
[   407.294] (**) HP Wireless hotkeys: always reports core events
[   407.294] (**) evdev: HP Wireless hotkeys: Device: "/dev/input/event7"
[   407.294] (--) evdev: HP Wireless hotkeys: Vendor 0 Product 0
[   407.294] (--) evdev: HP Wireless hotkeys: Found keys
[   407.294] (II) evdev: HP Wireless hotkeys: Configuring as keyboard
[   407.294] (**) Option "config_info" "udev:/sys/devices/virtual/input/input13/event7"
[   407.294] (II) XINPUT: Adding extended input device "HP Wireless hotkeys" (type: KEYBOARD, id 13)
[   407.294] (**) Option "xkb_rules" "evdev"
[   407.294] (**) Option "xkb_model" "pc105"
[   407.294] (**) Option "xkb_layout" "fr"
[   407.294] (**) Option "xkb_variant" "latin9_nodeadkeys"
[   407.295] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event16)
[   407.295] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[   407.295] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[   407.295] (**) HP WMI hotkeys: always reports core events
[   407.295] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event16"
[   407.295] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[   407.295] (--) evdev: HP WMI hotkeys: Found keys
[   407.295] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[   407.295] (**) Option "config_info" "udev:/sys/devices/virtual/input/input22/event16"
[   407.295] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 14)
[   407.295] (**) Option "xkb_rules" "evdev"
[   407.295] (**) Option "xkb_model" "pc105"
[   407.295] (**) Option "xkb_layout" "fr"
[   407.295] (**) Option "xkb_variant" "latin9_nodeadkeys"
[   407.330] (II) intel(0): EDID vendor "AUO", prod id 8300
[   407.330] (II) intel(0): Printing DDC gathered Modelines:
[   407.330] (II) intel(0): Modeline "1366x768"x0.0   76.30  1366 1414 1446 1606  768 774 784 790 -hsync -vsync (47.5 kHz eP)
[   407.330] (II) intel(0): Modeline "1366x768"x0.0   50.87  1366 1414 1446 1606  768 774 784 790 -hsync -vsync (31.7 kHz e)
[   407.578] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[   430.344] (II) AIGLX: Suspending AIGLX clients for VT switch
[   431.041] (II) AIGLX: Resuming AIGLX clients after VT switch
[   431.041] (II) intel(0): switch to mode 1366x768@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[   431.052] (II) intel(0): switch to mode 1024x768@60.0 on DP2 using pipe 1, position (0, 0), rotation normal, reflection none
[   431.060] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   443.003] (II) XKB: reuse xkmfile /var/lib/xkb/server-73FF85FED47F044C52089DE17D7D73C743491E80.xkm
[  1023.941] (II) intel(0): resizing framebuffer to 1360x768
[  1023.943] (II) intel(0): switch to mode 1360x768@59.8 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[  1025.373] (II) intel(0): resizing framebuffer to 1366x768
[  1025.374] (II) intel(0): switch to mode 1366x768@60.1 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none



```

[SIZE=2]Thank you.
[/SIZE]

---

### Post by patxi3 on 2016-05-02
Does someone see what might be a solution to this issue ?

---

### Post by patxi3 on 2016-05-09
up :(

---

### Post by gvlists on 2016-06-22
I am experiencing this problem on my HP Elitebook 820G1 with xubuntu. The screen becomes blurry and fuzzy sometimes. I have to reboot the laptop to get it right again. The dmesg output gives this at the end. Thi happens one or more every day.

[   16.183452] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[   16.204190] cfg80211: Regulatory domain changed to country: DE
[   16.204194] cfg80211:  DFS Master region: ETSI
[   16.204195] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   16.204197] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   16.204198] cfg80211:   (5150000 KHz - 5250000 KHz @ 80000 KHz, 200000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   16.204200] cfg80211:   (5250000 KHz - 5350000 KHz @ 80000 KHz, 200000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   16.204201] cfg80211:   (5470000 KHz - 5725000 KHz @ 160000 KHz), (N/A, 2698 mBm), (0 s)
[   16.204202] cfg80211:   (57000000 KHz - 66000000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[   16.249207] wlo1: Limiting TX power to 20 (20 - 0) dBm as advertised by 7c:4c:a5:63:3b:11

---

### Post by patxi3 on 2016-07-07
When that happen, you should try to update the resolution.
It works for me.

Hence I made a script to change resolution with one key.
I mapped the key F2 to run the following file.

file.sh
```

#!/bin/bash
xrandr -s 1360x768
xrandr -s 1366x768

```

---

