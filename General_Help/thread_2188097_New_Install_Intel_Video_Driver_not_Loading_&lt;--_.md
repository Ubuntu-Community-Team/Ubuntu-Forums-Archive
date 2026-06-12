---
title: "New Install Intel Video Driver not Loading &lt;-- should be easy :)"
date: 2013-11-15
forum: General Help
---

### Post by proksy on 2013-11-15
So I am out of town and want to play a game on my laptop which runs ubuntu 13.04 64bit.  I have just run a fresh install of 13.04 and had to install with the nomodeset option, otherwise the system would sit at a black screen.  Once I finished I navigated here:  [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads) and downloaded the 13.04 64bit version and installed the drivers with no issue.  Rebooted and I imediately realized, hey my driver didn't load.  It keeps falling back on the VESA driver instead of using the Intel.  

Here is my Xorg.0.log

```

[     3.040] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[     3.040] X Protocol Version 11, Revision 0
[     3.040] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[     3.040] Current Operating System: Linux walt-laptop 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64
[     3.040] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=8c499301-1cbf-41d1-88a1-f7c86b6ecdd9 ro nomodeset quiet splash vt.handoff=7
[     3.040] Build Date: 17 April 2013  10:43:13PM
[     3.040] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[     3.040] Current version of pixman: 0.28.2
[     3.040]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     3.040] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.040] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov 15 09:44:29 2013
[     3.040] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     3.040] (==) No Layout section.  Using the first Screen section.
[     3.040] (==) No screen section available. Using defaults.
[     3.041] (**) |-->Screen "Default Screen Section" (0)
[     3.041] (**) |   |-->Monitor "<default monitor>"
[     3.041] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     3.041] (==) Automatically adding devices
[     3.041] (==) Automatically enabling devices
[     3.041] (==) Automatically adding GPU devices
[     3.041] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.041]     Entry deleted from font path.
[     3.041] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     3.041]     Entry deleted from font path.
[     3.041] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     3.041]     Entry deleted from font path.
[     3.041] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     3.041]     Entry deleted from font path.
[     3.041] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     3.041]     Entry deleted from font path.
[     3.041] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     3.041]     Entry deleted from font path.
[     3.041] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     3.041] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     3.041] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     3.041] (II) Loader magic: 0x7f3931959d20
[     3.041] (II) Module ABI versions:
[     3.041]     X.Org ANSI C Emulation: 0.4
[     3.041]     X.Org Video Driver: 13.1
[     3.041]     X.Org XInput driver : 18.0
[     3.041]     X.Org Server Extension : 7.0
[     3.042] (--) PCI:*(0:0:2:0) 8086:0126:1179:fcd0 rev 9, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00004000/64
[     3.042] (II) Open ACPI successful (/var/run/acpid.socket)
[     3.042] Initializing built-in extension Generic Event Extension
[     3.042] Initializing built-in extension SHAPE
[     3.042] Initializing built-in extension MIT-SHM
[     3.042] Initializing built-in extension XInputExtension
[     3.042] Initializing built-in extension XTEST
[     3.042] Initializing built-in extension BIG-REQUESTS
[     3.042] Initializing built-in extension SYNC
[     3.042] Initializing built-in extension XKEYBOARD
[     3.042] Initializing built-in extension XC-MISC
[     3.042] Initializing built-in extension SECURITY
[     3.042] Initializing built-in extension XINERAMA
[     3.042] Initializing built-in extension XFIXES
[     3.042] Initializing built-in extension RENDER
[     3.042] Initializing built-in extension RANDR
[     3.042] Initializing built-in extension COMPOSITE
[     3.042] Initializing built-in extension DAMAGE
[     3.042] Initializing built-in extension MIT-SCREEN-SAVER
[     3.042] Initializing built-in extension DOUBLE-BUFFER
[     3.042] Initializing built-in extension RECORD
[     3.042] Initializing built-in extension DPMS
[     3.042] Initializing built-in extension X-Resource
[     3.042] Initializing built-in extension XVideo
[     3.042] Initializing built-in extension XVideo-MotionCompensation
[     3.042] Initializing built-in extension SELinux
[     3.042] Initializing built-in extension XFree86-VidModeExtension
[     3.042] Initializing built-in extension XFree86-DGA
[     3.042] Initializing built-in extension XFree86-DRI
[     3.042] Initializing built-in extension DRI2
[     3.042] (II) LoadModule: "glx"
[     3.043] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     3.043] (II) Module glx: vendor="X.Org Foundation"
[     3.043]     compiled for 1.13.3, module version = 1.0.0
[     3.043]     ABI class: X.Org Server Extension, version 7.0
[     3.043] (==) AIGLX enabled
[     3.043] Loading extension GLX
[     3.043] (==) Matched intel as autoconfigured driver 0
[     3.043] (==) Matched vesa as autoconfigured driver 1
[     3.043] (==) Matched modesetting as autoconfigured driver 2
[     3.043] (==) Matched fbdev as autoconfigured driver 3
[     3.043] (==) Assigned the driver to the xf86ConfigLayout
[     3.043] (II) LoadModule: "intel"
[     3.043] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     3.044] (II) Module intel: vendor="X.Org Foundation"
[     3.044]     compiled for 1.13.3, module version = 2.21.9
[     3.044]     Module class: X.Org Video Driver
[     3.044]     ABI class: X.Org Video Driver, version 13.1
[     3.044] (II) LoadModule: "vesa"
[     3.044] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     3.044] (II) Module vesa: vendor="X.Org Foundation"
[     3.044]     compiled for 1.12.99.902, module version = 2.3.2
[     3.044]     Module class: X.Org Video Driver
[     3.044]     ABI class: X.Org Video Driver, version 13.0
[     3.044] (II) LoadModule: "modesetting"
[     3.045] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     3.045] (II) Module modesetting: vendor="X.Org Foundation"
[     3.045]     compiled for 1.13.3, module version = 0.7.0
[     3.045]     Module class: X.Org Video Driver
[     3.045]     ABI class: X.Org Video Driver, version 13.1
[     3.045] (II) LoadModule: "fbdev"
[     3.045] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     3.045] (II) Module fbdev: vendor="X.Org Foundation"
[     3.045]     compiled for 1.12.99.902, module version = 0.4.3
[     3.045]     Module class: X.Org Video Driver
[     3.045]     ABI class: X.Org Video Driver, version 13.0
[     3.045] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
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
[     3.045] (II) VESA: driver for VESA chipsets: vesa
[     3.045] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     3.045] (II) FBDEV: driver for framebuffer: fbdev
[     3.045] (++) using VT number 7

[     3.047] (WW) Falling back to old probe method for modesetting
[     3.047] (EE) open /dev/dri/card0: No such file or directory
[     3.047] (WW) Falling back to old probe method for fbdev
[     3.047] (II) Loading sub module "fbdevhw"
[     3.047] (II) LoadModule: "fbdevhw"
[     3.047] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     3.047] (II) Module fbdevhw: vendor="X.Org Foundation"
[     3.047]     compiled for 1.13.3, module version = 0.0.2
[     3.047]     ABI class: X.Org Video Driver, version 13.1
[     3.047] (II) Loading sub module "vbe"
[     3.047] (II) LoadModule: "vbe"
[     3.047] (II) Loading /usr/lib/xorg/modules/libvbe.so
[     3.047] (II) Module vbe: vendor="X.Org Foundation"
[     3.047]     compiled for 1.13.3, module version = 1.1.0
[     3.047]     ABI class: X.Org Video Driver, version 13.1
[     3.047] (II) Loading sub module "int10"
[     3.047] (II) LoadModule: "int10"
[     3.047] (II) Loading /usr/lib/xorg/modules/libint10.so
[     3.047] (II) Module int10: vendor="X.Org Foundation"
[     3.047]     compiled for 1.13.3, module version = 1.0.0
[     3.047]     ABI class: X.Org Video Driver, version 13.1
[     3.047] (II) VESA(0): initializing int10
[     3.047] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[     3.048] (II) VESA(0): VESA BIOS detected
[     3.048] (II) VESA(0): VESA VBE Version 3.0
[     3.048] (II) VESA(0): VESA VBE Total Mem: 32704 kB
[     3.048] (II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Mobile Graphics Chipset Accelerated VGA BIOS
[     3.048] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[     3.048] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[     3.048] (II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Mobile Graphics Controller
[     3.048] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[     3.053] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     3.053] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[     3.053] (==) VESA(0): RGB weight 888
[     3.053] (==) VESA(0): Default visual is TrueColor
[     3.053] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[     3.053] (II) Loading sub module "ddc"
[     3.053] (II) LoadModule: "ddc"
[     3.053] (II) Module "ddc" already built-in
[     3.053] (II) VESA(0): VESA VBE DDC supported
[     3.053] (II) VESA(0): VESA VBE DDC Level 2
[     3.053] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[     3.066] (II) VESA(0): VESA VBE DDC read successfully
[     3.066] (II) VESA(0): Manufacturer: AUO  Model: 163c  Serial#: 0
[     3.066] (II) VESA(0): Year: 2009  Week: 1
[     3.066] (II) VESA(0): EDID Version: 1.3
[     3.066] (II) VESA(0): Digital Display Input
[     3.066] (II) VESA(0): Max Image Size [cm]: horiz.: 31  vert.: 17
[     3.066] (II) VESA(0): Gamma: 2.20
[     3.066] (II) VESA(0): No DPMS capabilities specified
[     3.066] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     3.066] (II) VESA(0): First detailed timing is preferred mode
[     3.066] (II) VESA(0): redX: 0.620 redY: 0.340   greenX: 0.330 greenY: 0.570
[     3.066] (II) VESA(0): blueX: 0.150 blueY: 0.600   whiteX: 0.313 whiteY: 0.329
[     3.066] (II) VESA(0): Manufacturer's mask: 0
[     3.066] (II) VESA(0): Supported detailed timing:
[     3.066] (II) VESA(0): clock: 69.3 MHz   Image Size:  309 x 173 mm
[     3.066] (II) VESA(0): h_active: 1366  h_sync: 1404  h_sync_end 1426 h_blank_end 1436 h_border: 0
[     3.066] (II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
[     3.066] (II) VESA(0): Unknown vendor-specific block f
[     3.066] (II) VESA(0):  AUO
[     3.066] (II) VESA(0):  B140XW01 V6
[     3.066] (II) VESA(0): EDID (in hex):
[     3.066] (II) VESA(0):     00ffffffffffff0006af3c1600000000
[     3.066] (II) VESA(0):     01130103801f11780ac8a59e57549226
[     3.066] (II) VESA(0):     99505400000001010101010101010101
[     3.066] (II) VESA(0):     010101010101121b5646500023302616
[     3.066] (II) VESA(0):     360035ad100000180000000f00000000
[     3.066] (II) VESA(0):     00000000000000000020000000fe0041
[     3.066] (II) VESA(0):     554f0a202020202020202020000000fe
[     3.066] (II) VESA(0):     004231343058573031205636200a001b
[     3.066] (II) VESA(0): EDID vendor "AUO", prod id 5692
[     3.066] (II) VESA(0): Printing DDC gathered Modelines:
[     3.066] (II) VESA(0): Modeline "1366x768"x0.0   69.30  1366 1404 1426 1436  768 771 777 803 -hsync -vsync (48.3 kHz eP)
[     3.066] (II) VESA(0): Searching for matching VESA mode(s):
[     3.066] Mode: 160 (0x0)
[     3.066]     ModeAttributes: 0x0
[     3.066]     WinAAttributes: 0x0
[     3.066]     WinBAttributes: 0x0
[     3.066]     WinGranularity: 0
[     3.066]     WinSize: 0
[     3.066]     WinASegment: 0x0
[     3.066]     WinBSegment: 0x0
[     3.066]     WinFuncPtr: 0x0
[     3.066]     BytesPerScanline: 0
[     3.066]     XResolution: 0
[     3.066]     YResolution: 0
[     3.066]     XCharSize: 0
[     3.066]     YCharSize: 0
[     3.066]     NumberOfPlanes: 0
[     3.066]     BitsPerPixel: 0
[     3.066]     NumberOfBanks: 0
[     3.066]     MemoryModel: 0
[     3.066]     BankSize: 0
[     3.066]     NumberOfImages: 0
[     3.066]     RedMaskSize: 0
[     3.066]     RedFieldPosition: 0
[     3.066]     GreenMaskSize: 0
[     3.066]     GreenFieldPosition: 0
[     3.066]     BlueMaskSize: 0
[     3.066]     BlueFieldPosition: 0
[     3.066]     RsvdMaskSize: 0
[     3.066]     RsvdFieldPosition: 0
[     3.066]     DirectColorModeInfo: 0
[     3.066]     PhysBasePtr: 0x0
[     3.066]     LinBytesPerScanLine: 0
[     3.066]     BnkNumberOfImagePages: 0
[     3.066]     LinNumberOfImagePages: 0
[     3.066]     LinRedMaskSize: 0
[     3.066]     LinRedFieldPosition: 0
[     3.066]     LinGreenMaskSize: 0
[     3.066]     LinGreenFieldPosition: 0
[     3.066]     LinBlueMaskSize: 0
[     3.066]     LinBlueFieldPosition: 0
[     3.066]     LinRsvdMaskSize: 0
[     3.066]     LinRsvdFieldPosition: 0
[     3.066]     MaxPixelClock: 0
[     3.066] Mode: 161 (0x0)
[     3.066]     ModeAttributes: 0x0
[     3.066]     WinAAttributes: 0x0
[     3.066]     WinBAttributes: 0x0
[     3.066]     WinGranularity: 0
[     3.066]     WinSize: 0
[     3.066]     WinASegment: 0x0
[     3.066]     WinBSegment: 0x0
[     3.066]     WinFuncPtr: 0x0
[     3.066]     BytesPerScanline: 0
[     3.066]     XResolution: 0
[     3.066]     YResolution: 0
[     3.066]     XCharSize: 0
[     3.066]     YCharSize: 0
[     3.066]     NumberOfPlanes: 0
[     3.066]     BitsPerPixel: 0
[     3.066]     NumberOfBanks: 0
[     3.066]     MemoryModel: 0
[     3.066]     BankSize: 0
[     3.066]     NumberOfImages: 0
[     3.066]     RedMaskSize: 0
[     3.066]     RedFieldPosition: 0
[     3.066]     GreenMaskSize: 0
[     3.066]     GreenFieldPosition: 0
[     3.066]     BlueMaskSize: 0
[     3.066]     BlueFieldPosition: 0
[     3.066]     RsvdMaskSize: 0
[     3.066]     RsvdFieldPosition: 0
[     3.066]     DirectColorModeInfo: 0
[     3.066]     PhysBasePtr: 0x0
[     3.066]     LinBytesPerScanLine: 0
[     3.066]     BnkNumberOfImagePages: 0
[     3.066]     LinNumberOfImagePages: 0
[     3.066]     LinRedMaskSize: 0
[     3.066]     LinRedFieldPosition: 0
[     3.066]     LinGreenMaskSize: 0
[     3.066]     LinGreenFieldPosition: 0
[     3.066]     LinBlueMaskSize: 0
[     3.066]     LinBlueFieldPosition: 0
[     3.066]     LinRsvdMaskSize: 0
[     3.066]     LinRsvdFieldPosition: 0
[     3.066]     MaxPixelClock: 0
[     3.066] Mode: 162 (0x0)
[     3.066]     ModeAttributes: 0x0
[     3.066]     WinAAttributes: 0x0
[     3.066]     WinBAttributes: 0x0
[     3.066]     WinGranularity: 0
[     3.066]     WinSize: 0
[     3.066]     WinASegment: 0x0
[     3.066]     WinBSegment: 0x0
[     3.066]     WinFuncPtr: 0x0
[     3.066]     BytesPerScanline: 0
[     3.066]     XResolution: 0
[     3.066]     YResolution: 0
[     3.066]     XCharSize: 0
[     3.066]     YCharSize: 0
[     3.066]     NumberOfPlanes: 0
[     3.066]     BitsPerPixel: 0
[     3.066]     NumberOfBanks: 0
[     3.066]     MemoryModel: 0
[     3.066]     BankSize: 0
[     3.066]     NumberOfImages: 0
[     3.066]     RedMaskSize: 0
[     3.066]     RedFieldPosition: 0
[     3.066]     GreenMaskSize: 0
[     3.066]     GreenFieldPosition: 0
[     3.066]     BlueMaskSize: 0
[     3.066]     BlueFieldPosition: 0
[     3.066]     RsvdMaskSize: 0
[     3.066]     RsvdFieldPosition: 0
[     3.066]     DirectColorModeInfo: 0
[     3.066]     PhysBasePtr: 0x0
[     3.066]     LinBytesPerScanLine: 0
[     3.066]     BnkNumberOfImagePages: 0
[     3.066]     LinNumberOfImagePages: 0
[     3.066]     LinRedMaskSize: 0
[     3.066]     LinRedFieldPosition: 0
[     3.066]     LinGreenMaskSize: 0
[     3.066]     LinGreenFieldPosition: 0
[     3.066]     LinBlueMaskSize: 0
[     3.067]     LinBlueFieldPosition: 0
[     3.067]     LinRsvdMaskSize: 0
[     3.067]     LinRsvdFieldPosition: 0
[     3.067]     MaxPixelClock: 0
[     3.067] Mode: 163 (0x0)
[     3.067]     ModeAttributes: 0x0
[     3.067]     WinAAttributes: 0x0
[     3.067]     WinBAttributes: 0x0
[     3.067]     WinGranularity: 0
[     3.067]     WinSize: 0
[     3.067]     WinASegment: 0x0
[     3.067]     WinBSegment: 0x0
[     3.067]     WinFuncPtr: 0x0
[     3.067]     BytesPerScanline: 0
[     3.067]     XResolution: 0
[     3.067]     YResolution: 0
[     3.067]     XCharSize: 0
[     3.067]     YCharSize: 0
[     3.067]     NumberOfPlanes: 0
[     3.067]     BitsPerPixel: 0
[     3.067]     NumberOfBanks: 0
[     3.067]     MemoryModel: 0
[     3.067]     BankSize: 0
[     3.067]     NumberOfImages: 0
[     3.067]     RedMaskSize: 0
[     3.067]     RedFieldPosition: 0
[     3.067]     GreenMaskSize: 0
[     3.067]     GreenFieldPosition: 0
[     3.067]     BlueMaskSize: 0
[     3.067]     BlueFieldPosition: 0
[     3.067]     RsvdMaskSize: 0
[     3.067]     RsvdFieldPosition: 0
[     3.067]     DirectColorModeInfo: 0
[     3.067]     PhysBasePtr: 0x0
[     3.067]     LinBytesPerScanLine: 0
[     3.067]     BnkNumberOfImagePages: 0
[     3.067]     LinNumberOfImagePages: 0
[     3.067]     LinRedMaskSize: 0
[     3.067]     LinRedFieldPosition: 0
[     3.067]     LinGreenMaskSize: 0
[     3.067]     LinGreenFieldPosition: 0
[     3.067]     LinBlueMaskSize: 0
[     3.067]     LinBlueFieldPosition: 0
[     3.067]     LinRsvdMaskSize: 0
[     3.067]     LinRsvdFieldPosition: 0
[     3.067]     MaxPixelClock: 0
[     3.067] Mode: 164 (0x0)
[     3.067]     ModeAttributes: 0x0
[     3.067]     WinAAttributes: 0x0
[     3.067]     WinBAttributes: 0x0
[     3.067]     WinGranularity: 0
[     3.067]     WinSize: 0
[     3.067]     WinASegment: 0x0
[     3.067]     WinBSegment: 0x0
[     3.067]     WinFuncPtr: 0x0
[     3.067]     BytesPerScanline: 0
[     3.067]     XResolution: 0
[     3.067]     YResolution: 0
[     3.067]     XCharSize: 0
[     3.067]     YCharSize: 0
[     3.067]     NumberOfPlanes: 0
[     3.067]     BitsPerPixel: 0
[     3.067]     NumberOfBanks: 0
[     3.067]     MemoryModel: 0
[     3.067]     BankSize: 0
[     3.067]     NumberOfImages: 0
[     3.067]     RedMaskSize: 0
[     3.067]     RedFieldPosition: 0
[     3.067]     GreenMaskSize: 0
[     3.067]     GreenFieldPosition: 0
[     3.067]     BlueMaskSize: 0
[     3.067]     BlueFieldPosition: 0
[     3.067]     RsvdMaskSize: 0
[     3.067]     RsvdFieldPosition: 0
[     3.067]     DirectColorModeInfo: 0
[     3.067]     PhysBasePtr: 0x0
[     3.067]     LinBytesPerScanLine: 0
[     3.067]     BnkNumberOfImagePages: 0
[     3.067]     LinNumberOfImagePages: 0
[     3.067]     LinRedMaskSize: 0
[     3.067]     LinRedFieldPosition: 0
[     3.067]     LinGreenMaskSize: 0
[     3.067]     LinGreenFieldPosition: 0
[     3.067]     LinBlueMaskSize: 0
[     3.067]     LinBlueFieldPosition: 0
[     3.067]     LinRsvdMaskSize: 0
[     3.067]     LinRsvdFieldPosition: 0
[     3.067]     MaxPixelClock: 0
[     3.067] Mode: 165 (0x0)
[     3.067]     ModeAttributes: 0x0
[     3.067]     WinAAttributes: 0x0
[     3.067]     WinBAttributes: 0x0
[     3.067]     WinGranularity: 0
[     3.067]     WinSize: 0
[     3.067]     WinASegment: 0x0
[     3.067]     WinBSegment: 0x0
[     3.067]     WinFuncPtr: 0x0
[     3.067]     BytesPerScanline: 0
[     3.067]     XResolution: 0
[     3.067]     YResolution: 0
[     3.067]     XCharSize: 0
[     3.067]     YCharSize: 0
[     3.067]     NumberOfPlanes: 0
[     3.067]     BitsPerPixel: 0
[     3.067]     NumberOfBanks: 0
[     3.067]     MemoryModel: 0
[     3.067]     BankSize: 0
[     3.067]     NumberOfImages: 0
[     3.067]     RedMaskSize: 0
[     3.067]     RedFieldPosition: 0
[     3.067]     GreenMaskSize: 0
[     3.067]     GreenFieldPosition: 0
[     3.067]     BlueMaskSize: 0
[     3.067]     BlueFieldPosition: 0
[     3.067]     RsvdMaskSize: 0
[     3.067]     RsvdFieldPosition: 0
[     3.067]     DirectColorModeInfo: 0
[     3.067]     PhysBasePtr: 0x0
[     3.067]     LinBytesPerScanLine: 0
[     3.067]     BnkNumberOfImagePages: 0
[     3.067]     LinNumberOfImagePages: 0
[     3.067]     LinRedMaskSize: 0
[     3.067]     LinRedFieldPosition: 0
[     3.067]     LinGreenMaskSize: 0
[     3.067]     LinGreenFieldPosition: 0
[     3.067]     LinBlueMaskSize: 0
[     3.067]     LinBlueFieldPosition: 0
[     3.067]     LinRsvdMaskSize: 0
[     3.067]     LinRsvdFieldPosition: 0
[     3.067]     MaxPixelClock: 0
[     3.067] Mode: 166 (0x0)
[     3.067]     ModeAttributes: 0x0
[     3.067]     WinAAttributes: 0x0
[     3.067]     WinBAttributes: 0x0
[     3.067]     WinGranularity: 0
[     3.067]     WinSize: 0
[     3.067]     WinASegment: 0x0
[     3.067]     WinBSegment: 0x0
[     3.067]     WinFuncPtr: 0x0
[     3.067]     BytesPerScanline: 0
[     3.067]     XResolution: 0
[     3.067]     YResolution: 0
[     3.067]     XCharSize: 0
[     3.067]     YCharSize: 0
[     3.067]     NumberOfPlanes: 0
[     3.067]     BitsPerPixel: 0
[     3.067]     NumberOfBanks: 0
[     3.067]     MemoryModel: 0
[     3.067]     BankSize: 0
[     3.067]     NumberOfImages: 0
[     3.067]     RedMaskSize: 0
[     3.067]     RedFieldPosition: 0
[     3.067]     GreenMaskSize: 0
[     3.067]     GreenFieldPosition: 0
[     3.067]     BlueMaskSize: 0
[     3.067]     BlueFieldPosition: 0
[     3.067]     RsvdMaskSize: 0
[     3.067]     RsvdFieldPosition: 0
[     3.067]     DirectColorModeInfo: 0
[     3.067]     PhysBasePtr: 0x0
[     3.067]     LinBytesPerScanLine: 0
[     3.067]     BnkNumberOfImagePages: 0
[     3.067]     LinNumberOfImagePages: 0
[     3.067]     LinRedMaskSize: 0
[     3.067]     LinRedFieldPosition: 0
[     3.067]     LinGreenMaskSize: 0
[     3.067]     LinGreenFieldPosition: 0
[     3.067]     LinBlueMaskSize: 0
[     3.067]     LinBlueFieldPosition: 0
[     3.067]     LinRsvdMaskSize: 0
[     3.067]     LinRsvdFieldPosition: 0
[     3.067]     MaxPixelClock: 0
[     3.068] Mode: 167 (0x0)
[     3.068]     ModeAttributes: 0x0
[     3.068]     WinAAttributes: 0x0
[     3.068]     WinBAttributes: 0x0
[     3.068]     WinGranularity: 0
[     3.068]     WinSize: 0
[     3.068]     WinASegment: 0x0
[     3.068]     WinBSegment: 0x0
[     3.068]     WinFuncPtr: 0x0
[     3.068]     BytesPerScanline: 0
[     3.068]     XResolution: 0
[     3.068]     YResolution: 0
[     3.068]     XCharSize: 0
[     3.068]     YCharSize: 0
[     3.068]     NumberOfPlanes: 0
[     3.068]     BitsPerPixel: 0
[     3.068]     NumberOfBanks: 0
[     3.068]     MemoryModel: 0
[     3.068]     BankSize: 0
[     3.068]     NumberOfImages: 0
[     3.068]     RedMaskSize: 0
[     3.068]     RedFieldPosition: 0
[     3.068]     GreenMaskSize: 0
[     3.068]     GreenFieldPosition: 0
[     3.068]     BlueMaskSize: 0
[     3.068]     BlueFieldPosition: 0
[     3.068]     RsvdMaskSize: 0
[     3.068]     RsvdFieldPosition: 0
[     3.068]     DirectColorModeInfo: 0
[     3.068]     PhysBasePtr: 0x0
[     3.068]     LinBytesPerScanLine: 0
[     3.068]     BnkNumberOfImagePages: 0
[     3.068]     LinNumberOfImagePages: 0
[     3.068]     LinRedMaskSize: 0
[     3.068]     LinRedFieldPosition: 0
[     3.068]     LinGreenMaskSize: 0
[     3.068]     LinGreenFieldPosition: 0
[     3.068]     LinBlueMaskSize: 0
[     3.068]     LinBlueFieldPosition: 0
[     3.068]     LinRsvdMaskSize: 0
[     3.068]     LinRsvdFieldPosition: 0
[     3.068]     MaxPixelClock: 0
[     3.068] Mode: 168 (0x0)
[     3.068]     ModeAttributes: 0x0
[     3.068]     WinAAttributes: 0x0
[     3.068]     WinBAttributes: 0x0
[     3.068]     WinGranularity: 0
[     3.068]     WinSize: 0
[     3.068]     WinASegment: 0x0
[     3.068]     WinBSegment: 0x0
[     3.068]     WinFuncPtr: 0x0
[     3.068]     BytesPerScanline: 0
[     3.068]     XResolution: 0
[     3.068]     YResolution: 0
[     3.068]     XCharSize: 0
[     3.068]     YCharSize: 0
[     3.068]     NumberOfPlanes: 0
[     3.068]     BitsPerPixel: 0
[     3.068]     NumberOfBanks: 0
[     3.068]     MemoryModel: 0
[     3.068]     BankSize: 0
[     3.068]     NumberOfImages: 0
[     3.068]     RedMaskSize: 0
[     3.068]     RedFieldPosition: 0
[     3.068]     GreenMaskSize: 0
[     3.068]     GreenFieldPosition: 0
[     3.068]     BlueMaskSize: 0
[     3.068]     BlueFieldPosition: 0
[     3.068]     RsvdMaskSize: 0
[     3.068]     RsvdFieldPosition: 0
[     3.068]     DirectColorModeInfo: 0
[     3.068]     PhysBasePtr: 0x0
[     3.068]     LinBytesPerScanLine: 0
[     3.068]     BnkNumberOfImagePages: 0
[     3.068]     LinNumberOfImagePages: 0
[     3.068]     LinRedMaskSize: 0
[     3.068]     LinRedFieldPosition: 0
[     3.068]     LinGreenMaskSize: 0
[     3.068]     LinGreenFieldPosition: 0
[     3.068]     LinBlueMaskSize: 0
[     3.068]     LinBlueFieldPosition: 0
[     3.068]     LinRsvdMaskSize: 0
[     3.068]     LinRsvdFieldPosition: 0
[     3.068]     MaxPixelClock: 0
[     3.068] Mode: 169 (0x0)
[     3.068]     ModeAttributes: 0x0
[     3.068]     WinAAttributes: 0x0
[     3.068]     WinBAttributes: 0x0
[     3.068]     WinGranularity: 0
[     3.068]     WinSize: 0
[     3.068]     WinASegment: 0x0
[     3.068]     WinBSegment: 0x0
[     3.068]     WinFuncPtr: 0x0
[     3.068]     BytesPerScanline: 0
[     3.068]     XResolution: 0
[     3.068]     YResolution: 0
[     3.068]     XCharSize: 0
[     3.068]     YCharSize: 0
[     3.068]     NumberOfPlanes: 0
[     3.068]     BitsPerPixel: 0
[     3.068]     NumberOfBanks: 0
[     3.068]     MemoryModel: 0
[     3.068]     BankSize: 0
[     3.068]     NumberOfImages: 0
[     3.068]     RedMaskSize: 0
[     3.068]     RedFieldPosition: 0
[     3.068]     GreenMaskSize: 0
[     3.068]     GreenFieldPosition: 0
[     3.068]     BlueMaskSize: 0
[     3.068]     BlueFieldPosition: 0
[     3.068]     RsvdMaskSize: 0
[     3.068]     RsvdFieldPosition: 0
[     3.068]     DirectColorModeInfo: 0
[     3.068]     PhysBasePtr: 0x0
[     3.068]     LinBytesPerScanLine: 0
[     3.068]     BnkNumberOfImagePages: 0
[     3.068]     LinNumberOfImagePages: 0
[     3.068]     LinRedMaskSize: 0
[     3.068]     LinRedFieldPosition: 0
[     3.068]     LinGreenMaskSize: 0
[     3.068]     LinGreenFieldPosition: 0
[     3.068]     LinBlueMaskSize: 0
[     3.068]     LinBlueFieldPosition: 0
[     3.068]     LinRsvdMaskSize: 0
[     3.068]     LinRsvdFieldPosition: 0
[     3.068]     MaxPixelClock: 0
[     3.068] Mode: 16a (0x0)
[     3.068]     ModeAttributes: 0x0
[     3.068]     WinAAttributes: 0x0
[     3.068]     WinBAttributes: 0x0
[     3.068]     WinGranularity: 0
[     3.068]     WinSize: 0
[     3.068]     WinASegment: 0x0
[     3.068]     WinBSegment: 0x0
[     3.068]     WinFuncPtr: 0x0
[     3.068]     BytesPerScanline: 0
[     3.068]     XResolution: 0
[     3.068]     YResolution: 0
[     3.068]     XCharSize: 0
[     3.068]     YCharSize: 0
[     3.068]     NumberOfPlanes: 0
[     3.068]     BitsPerPixel: 0
[     3.068]     NumberOfBanks: 0
[     3.068]     MemoryModel: 0
[     3.068]     BankSize: 0
[     3.068]     NumberOfImages: 0
[     3.068]     RedMaskSize: 0
[     3.068]     RedFieldPosition: 0
[     3.068]     GreenMaskSize: 0
[     3.068]     GreenFieldPosition: 0
[     3.068]     BlueMaskSize: 0
[     3.068]     BlueFieldPosition: 0
[     3.068]     RsvdMaskSize: 0
[     3.068]     RsvdFieldPosition: 0
[     3.068]     DirectColorModeInfo: 0
[     3.068]     PhysBasePtr: 0x0
[     3.068]     LinBytesPerScanLine: 0
[     3.068]     BnkNumberOfImagePages: 0
[     3.068]     LinNumberOfImagePages: 0
[     3.068]     LinRedMaskSize: 0
[     3.068]     LinRedFieldPosition: 0
[     3.068]     LinGreenMaskSize: 0
[     3.068]     LinGreenFieldPosition: 0
[     3.068]     LinBlueMaskSize: 0
[     3.068]     LinBlueFieldPosition: 0
[     3.068]     LinRsvdMaskSize: 0
[     3.068]     LinRsvdFieldPosition: 0
[     3.068]     MaxPixelClock: 0
[     3.069] Mode: 16b (0x0)
[     3.069]     ModeAttributes: 0x0
[     3.069]     WinAAttributes: 0x0
[     3.069]     WinBAttributes: 0x0
[     3.069]     WinGranularity: 0
[     3.069]     WinSize: 0
[     3.069]     WinASegment: 0x0
[     3.069]     WinBSegment: 0x0
[     3.069]     WinFuncPtr: 0x0
[     3.069]     BytesPerScanline: 0
[     3.069]     XResolution: 0
[     3.069]     YResolution: 0
[     3.069]     XCharSize: 0
[     3.069]     YCharSize: 0
[     3.069]     NumberOfPlanes: 0
[     3.069]     BitsPerPixel: 0
[     3.069]     NumberOfBanks: 0
[     3.069]     MemoryModel: 0
[     3.069]     BankSize: 0
[     3.069]     NumberOfImages: 0
[     3.069]     RedMaskSize: 0
[     3.069]     RedFieldPosition: 0
[     3.069]     GreenMaskSize: 0
[     3.069]     GreenFieldPosition: 0
[     3.069]     BlueMaskSize: 0
[     3.069]     BlueFieldPosition: 0
[     3.069]     RsvdMaskSize: 0
[     3.069]     RsvdFieldPosition: 0
[     3.069]     DirectColorModeInfo: 0
[     3.069]     PhysBasePtr: 0x0
[     3.069]     LinBytesPerScanLine: 0
[     3.069]     BnkNumberOfImagePages: 0
[     3.069]     LinNumberOfImagePages: 0
[     3.069]     LinRedMaskSize: 0
[     3.069]     LinRedFieldPosition: 0
[     3.069]     LinGreenMaskSize: 0
[     3.069]     LinGreenFieldPosition: 0
[     3.069]     LinBlueMaskSize: 0
[     3.069]     LinBlueFieldPosition: 0
[     3.069]     LinRsvdMaskSize: 0
[     3.069]     LinRsvdFieldPosition: 0
[     3.069]     MaxPixelClock: 0
[     3.069] Mode: 16c (0x0)
[     3.069]     ModeAttributes: 0x0
[     3.069]     WinAAttributes: 0x0
[     3.069]     WinBAttributes: 0x0
[     3.069]     WinGranularity: 0
[     3.069]     WinSize: 0
[     3.069]     WinASegment: 0x0
[     3.069]     WinBSegment: 0x0
[     3.069]     WinFuncPtr: 0x0
[     3.069]     BytesPerScanline: 0
[     3.069]     XResolution: 0
[     3.069]     YResolution: 0
[     3.069]     XCharSize: 0
[     3.069]     YCharSize: 0
[     3.069]     NumberOfPlanes: 0
[     3.069]     BitsPerPixel: 0
[     3.069]     NumberOfBanks: 0
[     3.069]     MemoryModel: 0
[     3.069]     BankSize: 0
[     3.069]     NumberOfImages: 0
[     3.069]     RedMaskSize: 0
[     3.069]     RedFieldPosition: 0
[     3.069]     GreenMaskSize: 0
[     3.069]     GreenFieldPosition: 0
[     3.069]     BlueMaskSize: 0
[     3.069]     BlueFieldPosition: 0
[     3.069]     RsvdMaskSize: 0
[     3.069]     RsvdFieldPosition: 0
[     3.069]     DirectColorModeInfo: 0
[     3.069]     PhysBasePtr: 0x0
[     3.069]     LinBytesPerScanLine: 0
[     3.069]     BnkNumberOfImagePages: 0
[     3.069]     LinNumberOfImagePages: 0
[     3.069]     LinRedMaskSize: 0
[     3.069]     LinRedFieldPosition: 0
[     3.069]     LinGreenMaskSize: 0
[     3.069]     LinGreenFieldPosition: 0
[     3.069]     LinBlueMaskSize: 0
[     3.069]     LinBlueFieldPosition: 0
[     3.069]     LinRsvdMaskSize: 0
[     3.069]     LinRsvdFieldPosition: 0
[     3.069]     MaxPixelClock: 0
[     3.069] Mode: 16d (0x0)
[     3.069]     ModeAttributes: 0x0
[     3.069]     WinAAttributes: 0x0
[     3.069]     WinBAttributes: 0x0
[     3.069]     WinGranularity: 0
[     3.069]     WinSize: 0
[     3.069]     WinASegment: 0x0
[     3.069]     WinBSegment: 0x0
[     3.069]     WinFuncPtr: 0x0
[     3.069]     BytesPerScanline: 0
[     3.069]     XResolution: 0
[     3.069]     YResolution: 0
[     3.069]     XCharSize: 0
[     3.069]     YCharSize: 0
[     3.069]     NumberOfPlanes: 0
[     3.069]     BitsPerPixel: 0
[     3.069]     NumberOfBanks: 0
[     3.069]     MemoryModel: 0
[     3.069]     BankSize: 0
[     3.069]     NumberOfImages: 0
[     3.069]     RedMaskSize: 0
[     3.069]     RedFieldPosition: 0
[     3.069]     GreenMaskSize: 0
[     3.069]     GreenFieldPosition: 0
[     3.069]     BlueMaskSize: 0
[     3.069]     BlueFieldPosition: 0
[     3.069]     RsvdMaskSize: 0
[     3.069]     RsvdFieldPosition: 0
[     3.069]     DirectColorModeInfo: 0
[     3.069]     PhysBasePtr: 0x0
[     3.069]     LinBytesPerScanLine: 0
[     3.069]     BnkNumberOfImagePages: 0
[     3.069]     LinNumberOfImagePages: 0
[     3.069]     LinRedMaskSize: 0
[     3.069]     LinRedFieldPosition: 0
[     3.069]     LinGreenMaskSize: 0
[     3.069]     LinGreenFieldPosition: 0
[     3.069]     LinBlueMaskSize: 0
[     3.069]     LinBlueFieldPosition: 0
[     3.069]     LinRsvdMaskSize: 0
[     3.069]     LinRsvdFieldPosition: 0
[     3.069]     MaxPixelClock: 0
[     3.069] Mode: 16e (0x0)
[     3.069]     ModeAttributes: 0x0
[     3.069]     WinAAttributes: 0x0
[     3.069]     WinBAttributes: 0x0
[     3.069]     WinGranularity: 0
[     3.069]     WinSize: 0
[     3.069]     WinASegment: 0x0
[     3.069]     WinBSegment: 0x0
[     3.069]     WinFuncPtr: 0x0
[     3.069]     BytesPerScanline: 0
[     3.069]     XResolution: 0
[     3.069]     YResolution: 0
[     3.069]     XCharSize: 0
[     3.069]     YCharSize: 0
[     3.069]     NumberOfPlanes: 0
[     3.069]     BitsPerPixel: 0
[     3.069]     NumberOfBanks: 0
[     3.069]     MemoryModel: 0
[     3.069]     BankSize: 0
[     3.069]     NumberOfImages: 0
[     3.069]     RedMaskSize: 0
[     3.069]     RedFieldPosition: 0
[     3.069]     GreenMaskSize: 0
[     3.069]     GreenFieldPosition: 0
[     3.069]     BlueMaskSize: 0
[     3.069]     BlueFieldPosition: 0
[     3.069]     RsvdMaskSize: 0
[     3.069]     RsvdFieldPosition: 0
[     3.069]     DirectColorModeInfo: 0
[     3.069]     PhysBasePtr: 0x0
[     3.069]     LinBytesPerScanLine: 0
[     3.069]     BnkNumberOfImagePages: 0
[     3.069]     LinNumberOfImagePages: 0
[     3.069]     LinRedMaskSize: 0
[     3.069]     LinRedFieldPosition: 0
[     3.069]     LinGreenMaskSize: 0
[     3.069]     LinGreenFieldPosition: 0
[     3.069]     LinBlueMaskSize: 0
[     3.069]     LinBlueFieldPosition: 0
[     3.069]     LinRsvdMaskSize: 0
[     3.069]     LinRsvdFieldPosition: 0
[     3.069]     MaxPixelClock: 0
[     3.069] Mode: 16f (0x0)
[     3.069]     ModeAttributes: 0x0
[     3.069]     WinAAttributes: 0x0
[     3.069]     WinBAttributes: 0x0
[     3.069]     WinGranularity: 0
[     3.069]     WinSize: 0
[     3.069]     WinASegment: 0x0
[     3.070]     WinBSegment: 0x0
[     3.070]     WinFuncPtr: 0x0
[     3.070]     BytesPerScanline: 0
[     3.070]     XResolution: 0
[     3.070]     YResolution: 0
[     3.070]     XCharSize: 0
[     3.070]     YCharSize: 0
[     3.070]     NumberOfPlanes: 0
[     3.070]     BitsPerPixel: 0
[     3.070]     NumberOfBanks: 0
[     3.070]     MemoryModel: 0
[     3.070]     BankSize: 0
[     3.070]     NumberOfImages: 0
[     3.070]     RedMaskSize: 0
[     3.070]     RedFieldPosition: 0
[     3.070]     GreenMaskSize: 0
[     3.070]     GreenFieldPosition: 0
[     3.070]     BlueMaskSize: 0
[     3.070]     BlueFieldPosition: 0
[     3.070]     RsvdMaskSize: 0
[     3.070]     RsvdFieldPosition: 0
[     3.070]     DirectColorModeInfo: 0
[     3.070]     PhysBasePtr: 0x0
[     3.070]     LinBytesPerScanLine: 0
[     3.070]     BnkNumberOfImagePages: 0
[     3.070]     LinNumberOfImagePages: 0
[     3.070]     LinRedMaskSize: 0
[     3.070]     LinRedFieldPosition: 0
[     3.070]     LinGreenMaskSize: 0
[     3.070]     LinGreenFieldPosition: 0
[     3.070]     LinBlueMaskSize: 0
[     3.070]     LinBlueFieldPosition: 0
[     3.070]     LinRsvdMaskSize: 0
[     3.070]     LinRsvdFieldPosition: 0
[     3.070]     MaxPixelClock: 0
[     3.070] Mode: 170 (0x0)
[     3.070]     ModeAttributes: 0x0
[     3.070]     WinAAttributes: 0x0
[     3.070]     WinBAttributes: 0x0
[     3.070]     WinGranularity: 0
[     3.070]     WinSize: 0
[     3.070]     WinASegment: 0x0
[     3.070]     WinBSegment: 0x0
[     3.070]     WinFuncPtr: 0x0
[     3.070]     BytesPerScanline: 0
[     3.070]     XResolution: 0
[     3.070]     YResolution: 0
[     3.070]     XCharSize: 0
[     3.070]     YCharSize: 0
[     3.070]     NumberOfPlanes: 0
[     3.070]     BitsPerPixel: 0
[     3.070]     NumberOfBanks: 0
[     3.070]     MemoryModel: 0
[     3.070]     BankSize: 0
[     3.070]     NumberOfImages: 0
[     3.070]     RedMaskSize: 0
[     3.070]     RedFieldPosition: 0
[     3.070]     GreenMaskSize: 0
[     3.070]     GreenFieldPosition: 0
[     3.070]     BlueMaskSize: 0
[     3.070]     BlueFieldPosition: 0
[     3.070]     RsvdMaskSize: 0
[     3.070]     RsvdFieldPosition: 0
[     3.070]     DirectColorModeInfo: 0
[     3.070]     PhysBasePtr: 0x0
[     3.070]     LinBytesPerScanLine: 0
[     3.070]     BnkNumberOfImagePages: 0
[     3.070]     LinNumberOfImagePages: 0
[     3.070]     LinRedMaskSize: 0
[     3.070]     LinRedFieldPosition: 0
[     3.070]     LinGreenMaskSize: 0
[     3.070]     LinGreenFieldPosition: 0
[     3.070]     LinBlueMaskSize: 0
[     3.070]     LinBlueFieldPosition: 0
[     3.070]     LinRsvdMaskSize: 0
[     3.070]     LinRsvdFieldPosition: 0
[     3.070]     MaxPixelClock: 0
[     3.070] Mode: 171 (0x0)
[     3.070]     ModeAttributes: 0x0
[     3.070]     WinAAttributes: 0x0
[     3.070]     WinBAttributes: 0x0
[     3.070]     WinGranularity: 0
[     3.070]     WinSize: 0
[     3.070]     WinASegment: 0x0
[     3.070]     WinBSegment: 0x0
[     3.070]     WinFuncPtr: 0x0
[     3.070]     BytesPerScanline: 0
[     3.070]     XResolution: 0
[     3.070]     YResolution: 0
[     3.070]     XCharSize: 0
[     3.070]     YCharSize: 0
[     3.070]     NumberOfPlanes: 0
[     3.070]     BitsPerPixel: 0
[     3.070]     NumberOfBanks: 0
[     3.070]     MemoryModel: 0
[     3.070]     BankSize: 0
[     3.070]     NumberOfImages: 0
[     3.070]     RedMaskSize: 0
[     3.070]     RedFieldPosition: 0
[     3.070]     GreenMaskSize: 0
[     3.070]     GreenFieldPosition: 0
[     3.070]     BlueMaskSize: 0
[     3.070]     BlueFieldPosition: 0
[     3.070]     RsvdMaskSize: 0
[     3.070]     RsvdFieldPosition: 0
[     3.070]     DirectColorModeInfo: 0
[     3.070]     PhysBasePtr: 0x0
[     3.070]     LinBytesPerScanLine: 0
[     3.070]     BnkNumberOfImagePages: 0
[     3.070]     LinNumberOfImagePages: 0
[     3.070]     LinRedMaskSize: 0
[     3.070]     LinRedFieldPosition: 0
[     3.070]     LinGreenMaskSize: 0
[     3.070]     LinGreenFieldPosition: 0
[     3.070]     LinBlueMaskSize: 0
[     3.070]     LinBlueFieldPosition: 0
[     3.070]     LinRsvdMaskSize: 0
[     3.070]     LinRsvdFieldPosition: 0
[     3.070]     MaxPixelClock: 0
[     3.070] Mode: 13c (0x0)
[     3.070]     ModeAttributes: 0x0
[     3.070]     WinAAttributes: 0x0
[     3.070]     WinBAttributes: 0x0
[     3.070]     WinGranularity: 0
[     3.070]     WinSize: 0
[     3.070]     WinASegment: 0x0
[     3.070]     WinBSegment: 0x0
[     3.070]     WinFuncPtr: 0x0
[     3.070]     BytesPerScanline: 0
[     3.070]     XResolution: 0
[     3.070]     YResolution: 0
[     3.070]     XCharSize: 0
[     3.070]     YCharSize: 0
[     3.070]     NumberOfPlanes: 0
[     3.070]     BitsPerPixel: 0
[     3.070]     NumberOfBanks: 0
[     3.070]     MemoryModel: 0
[     3.070]     BankSize: 0
[     3.070]     NumberOfImages: 0
[     3.070]     RedMaskSize: 0
[     3.070]     RedFieldPosition: 0
[     3.070]     GreenMaskSize: 0
[     3.070]     GreenFieldPosition: 0
[     3.070]     BlueMaskSize: 0
[     3.070]     BlueFieldPosition: 0
[     3.070]     RsvdMaskSize: 0
[     3.070]     RsvdFieldPosition: 0
[     3.070]     DirectColorModeInfo: 0
[     3.070]     PhysBasePtr: 0x0
[     3.070]     LinBytesPerScanLine: 0
[     3.070]     BnkNumberOfImagePages: 0
[     3.070]     LinNumberOfImagePages: 0
[     3.070]     LinRedMaskSize: 0
[     3.070]     LinRedFieldPosition: 0
[     3.070]     LinGreenMaskSize: 0
[     3.070]     LinGreenFieldPosition: 0
[     3.070]     LinBlueMaskSize: 0
[     3.070]     LinBlueFieldPosition: 0
[     3.070]     LinRsvdMaskSize: 0
[     3.070]     LinRsvdFieldPosition: 0
[     3.070]     MaxPixelClock: 0
[     3.071] Mode: 14d (0x0)
[     3.071]     ModeAttributes: 0x0
[     3.071]     WinAAttributes: 0x0
[     3.071]     WinBAttributes: 0x0
[     3.071]     WinGranularity: 0
[     3.071]     WinSize: 0
[     3.071]     WinASegment: 0x0
[     3.071]     WinBSegment: 0x0
[     3.071]     WinFuncPtr: 0x0
[     3.071]     BytesPerScanline: 0
[     3.071]     XResolution: 0
[     3.071]     YResolution: 0
[     3.071]     XCharSize: 0
[     3.071]     YCharSize: 0
[     3.071]     NumberOfPlanes: 0
[     3.071]     BitsPerPixel: 0
[     3.071]     NumberOfBanks: 0
[     3.071]     MemoryModel: 0
[     3.071]     BankSize: 0
[     3.071]     NumberOfImages: 0
[     3.071]     RedMaskSize: 0
[     3.071]     RedFieldPosition: 0
[     3.071]     GreenMaskSize: 0
[     3.071]     GreenFieldPosition: 0
[     3.071]     BlueMaskSize: 0
[     3.071]     BlueFieldPosition: 0
[     3.071]     RsvdMaskSize: 0
[     3.071]     RsvdFieldPosition: 0
[     3.071]     DirectColorModeInfo: 0
[     3.071]     PhysBasePtr: 0x0
[     3.071]     LinBytesPerScanLine: 0
[     3.071]     BnkNumberOfImagePages: 0
[     3.071]     LinNumberOfImagePages: 0
[     3.071]     LinRedMaskSize: 0
[     3.071]     LinRedFieldPosition: 0
[     3.071]     LinGreenMaskSize: 0
[     3.071]     LinGreenFieldPosition: 0
[     3.071]     LinBlueMaskSize: 0
[     3.071]     LinBlueFieldPosition: 0
[     3.071]     LinRsvdMaskSize: 0
[     3.071]     LinRsvdFieldPosition: 0
[     3.071]     MaxPixelClock: 0
[     3.071] Mode: 15c (0x0)
[     3.071]     ModeAttributes: 0x0
[     3.071]     WinAAttributes: 0x0
[     3.071]     WinBAttributes: 0x0
[     3.071]     WinGranularity: 0
[     3.071]     WinSize: 0
[     3.071]     WinASegment: 0x0
[     3.071]     WinBSegment: 0x0
[     3.071]     WinFuncPtr: 0x0
[     3.071]     BytesPerScanline: 0
[     3.071]     XResolution: 0
[     3.071]     YResolution: 0
[     3.071]     XCharSize: 0
[     3.071]     YCharSize: 0
[     3.071]     NumberOfPlanes: 0
[     3.071]     BitsPerPixel: 0
[     3.071]     NumberOfBanks: 0
[     3.071]     MemoryModel: 0
[     3.071]     BankSize: 0
[     3.071]     NumberOfImages: 0
[     3.071]     RedMaskSize: 0
[     3.071]     RedFieldPosition: 0
[     3.071]     GreenMaskSize: 0
[     3.071]     GreenFieldPosition: 0
[     3.071]     BlueMaskSize: 0
[     3.071]     BlueFieldPosition: 0
[     3.071]     RsvdMaskSize: 0
[     3.071]     RsvdFieldPosition: 0
[     3.071]     DirectColorModeInfo: 0
[     3.071]     PhysBasePtr: 0x0
[     3.071]     LinBytesPerScanLine: 0
[     3.071]     BnkNumberOfImagePages: 0
[     3.071]     LinNumberOfImagePages: 0
[     3.071]     LinRedMaskSize: 0
[     3.071]     LinRedFieldPosition: 0
[     3.071]     LinGreenMaskSize: 0
[     3.071]     LinGreenFieldPosition: 0
[     3.071]     LinBlueMaskSize: 0
[     3.071]     LinBlueFieldPosition: 0
[     3.071]     LinRsvdMaskSize: 0
[     3.071]     LinRsvdFieldPosition: 0
[     3.071]     MaxPixelClock: 0
[     3.071] Mode: 13a (0x0)
[     3.071]     ModeAttributes: 0x0
[     3.071]     WinAAttributes: 0x0
[     3.071]     WinBAttributes: 0x0
[     3.071]     WinGranularity: 0
[     3.071]     WinSize: 0
[     3.071]     WinASegment: 0x0
[     3.071]     WinBSegment: 0x0
[     3.071]     WinFuncPtr: 0x0
[     3.071]     BytesPerScanline: 0
[     3.071]     XResolution: 0
[     3.071]     YResolution: 0
[     3.071]     XCharSize: 0
[     3.071]     YCharSize: 0
[     3.071]     NumberOfPlanes: 0
[     3.071]     BitsPerPixel: 0
[     3.071]     NumberOfBanks: 0
[     3.071]     MemoryModel: 0
[     3.071]     BankSize: 0
[     3.071]     NumberOfImages: 0
[     3.071]     RedMaskSize: 0
[     3.071]     RedFieldPosition: 0
[     3.071]     GreenMaskSize: 0
[     3.071]     GreenFieldPosition: 0
[     3.071]     BlueMaskSize: 0
[     3.071]     BlueFieldPosition: 0
[     3.071]     RsvdMaskSize: 0
[     3.071]     RsvdFieldPosition: 0
[     3.071]     DirectColorModeInfo: 0
[     3.071]     PhysBasePtr: 0x0
[     3.071]     LinBytesPerScanLine: 0
[     3.071]     BnkNumberOfImagePages: 0
[     3.071]     LinNumberOfImagePages: 0
[     3.071]     LinRedMaskSize: 0
[     3.071]     LinRedFieldPosition: 0
[     3.071]     LinGreenMaskSize: 0
[     3.071]     LinGreenFieldPosition: 0
[     3.071]     LinBlueMaskSize: 0
[     3.071]     LinBlueFieldPosition: 0
[     3.071]     LinRsvdMaskSize: 0
[     3.071]     LinRsvdFieldPosition: 0
[     3.071]     MaxPixelClock: 0
[     3.071] Mode: 14b (0x0)
[     3.071]     ModeAttributes: 0x0
[     3.071]     WinAAttributes: 0x0
[     3.071]     WinBAttributes: 0x0
[     3.072]     WinGranularity: 0
[     3.072]     WinSize: 0
[     3.072]     WinASegment: 0x0
[     3.072]     WinBSegment: 0x0
[     3.072]     WinFuncPtr: 0x0
[     3.072]     BytesPerScanline: 0
[     3.072]     XResolution: 0
[     3.072]     YResolution: 0
[     3.072]     XCharSize: 0
[     3.072]     YCharSize: 0
[     3.072]     NumberOfPlanes: 0
[     3.072]     BitsPerPixel: 0
[     3.072]     NumberOfBanks: 0
[     3.072]     MemoryModel: 0
[     3.072]     BankSize: 0
[     3.072]     NumberOfImages: 0
[     3.072]     RedMaskSize: 0
[     3.072]     RedFieldPosition: 0
[     3.072]     GreenMaskSize: 0
[     3.072]     GreenFieldPosition: 0
[     3.072]     BlueMaskSize: 0
[     3.072]     BlueFieldPosition: 0
[     3.072]     RsvdMaskSize: 0
[     3.072]     RsvdFieldPosition: 0
[     3.072]     DirectColorModeInfo: 0
[     3.072]     PhysBasePtr: 0x0
[     3.072]     LinBytesPerScanLine: 0
[     3.072]     BnkNumberOfImagePages: 0
[     3.072]     LinNumberOfImagePages: 0
[     3.072]     LinRedMaskSize: 0
[     3.072]     LinRedFieldPosition: 0
[     3.072]     LinGreenMaskSize: 0
[     3.072]     LinGreenFieldPosition: 0
[     3.072]     LinBlueMaskSize: 0
[     3.072]     LinBlueFieldPosition: 0
[     3.072]     LinRsvdMaskSize: 0
[     3.072]     LinRsvdFieldPosition: 0
[     3.072]     MaxPixelClock: 0
[     3.072] Mode: 15a (0x0)
[     3.072]     ModeAttributes: 0x0
[     3.072]     WinAAttributes: 0x0
[     3.072]     WinBAttributes: 0x0
[     3.072]     WinGranularity: 0
[     3.072]     WinSize: 0
[     3.072]     WinASegment: 0x0
[     3.072]     WinBSegment: 0x0
[     3.072]     WinFuncPtr: 0x0
[     3.072]     BytesPerScanline: 0
[     3.072]     XResolution: 0
[     3.072]     YResolution: 0
[     3.072]     XCharSize: 0
[     3.072]     YCharSize: 0
[     3.072]     NumberOfPlanes: 0
[     3.072]     BitsPerPixel: 0
[     3.072]     NumberOfBanks: 0
[     3.072]     MemoryModel: 0
[     3.072]     BankSize: 0
[     3.072]     NumberOfImages: 0
[     3.072]     RedMaskSize: 0
[     3.072]     RedFieldPosition: 0
[     3.072]     GreenMaskSize: 0
[     3.072]     GreenFieldPosition: 0
[     3.072]     BlueMaskSize: 0
[     3.072]     BlueFieldPosition: 0
[     3.072]     RsvdMaskSize: 0
[     3.072]     RsvdFieldPosition: 0
[     3.072]     DirectColorModeInfo: 0
[     3.072]     PhysBasePtr: 0x0
[     3.072]     LinBytesPerScanLine: 0
[     3.072]     BnkNumberOfImagePages: 0
[     3.072]     LinNumberOfImagePages: 0
[     3.072]     LinRedMaskSize: 0
[     3.072]     LinRedFieldPosition: 0
[     3.072]     LinGreenMaskSize: 0
[     3.072]     LinGreenFieldPosition: 0
[     3.072]     LinBlueMaskSize: 0
[     3.072]     LinBlueFieldPosition: 0
[     3.072]     LinRsvdMaskSize: 0
[     3.072]     LinRsvdFieldPosition: 0
[     3.072]     MaxPixelClock: 0
[     3.072] Mode: 107 (0x0)
[     3.072]     ModeAttributes: 0x0
[     3.072]     WinAAttributes: 0x0
[     3.072]     WinBAttributes: 0x0
[     3.072]     WinGranularity: 0
[     3.072]     WinSize: 0
[     3.072]     WinASegment: 0x0
[     3.072]     WinBSegment: 0x0
[     3.072]     WinFuncPtr: 0x0
[     3.072]     BytesPerScanline: 0
[     3.072]     XResolution: 0
[     3.072]     YResolution: 0
[     3.072]     XCharSize: 0
[     3.072]     YCharSize: 0
[     3.072]     NumberOfPlanes: 0
[     3.072]     BitsPerPixel: 0
[     3.072]     NumberOfBanks: 0
[     3.072]     MemoryModel: 0
[     3.072]     BankSize: 0
[     3.072]     NumberOfImages: 0
[     3.072]     RedMaskSize: 0
[     3.072]     RedFieldPosition: 0
[     3.072]     GreenMaskSize: 0
[     3.072]     GreenFieldPosition: 0
[     3.072]     BlueMaskSize: 0
[     3.072]     BlueFieldPosition: 0
[     3.072]     RsvdMaskSize: 0
[     3.072]     RsvdFieldPosition: 0
[     3.072]     DirectColorModeInfo: 0
[     3.072]     PhysBasePtr: 0x0
[     3.072]     LinBytesPerScanLine: 0
[     3.072]     BnkNumberOfImagePages: 0
[     3.072]     LinNumberOfImagePages: 0
[     3.072]     LinRedMaskSize: 0
[     3.072]     LinRedFieldPosition: 0
[     3.072]     LinGreenMaskSize: 0
[     3.072]     LinGreenFieldPosition: 0
[     3.072]     LinBlueMaskSize: 0
[     3.072]     LinBlueFieldPosition: 0
[     3.072]     LinRsvdMaskSize: 0
[     3.072]     LinRsvdFieldPosition: 0
[     3.072]     MaxPixelClock: 0
[     3.072] Mode: 11a (0x0)
[     3.072]     ModeAttributes: 0x0
[     3.072]     WinAAttributes: 0x0
[     3.072]     WinBAttributes: 0x0
[     3.072]     WinGranularity: 0
[     3.072]     WinSize: 0
[     3.072]     WinASegment: 0x0
[     3.072]     WinBSegment: 0x0
[     3.072]     WinFuncPtr: 0x0
[     3.072]     BytesPerScanline: 0
[     3.072]     XResolution: 0
[     3.072]     YResolution: 0
[     3.072]     XCharSize: 0
[     3.073]     YCharSize: 0
[     3.073]     NumberOfPlanes: 0
[     3.073]     BitsPerPixel: 0
[     3.073]     NumberOfBanks: 0
[     3.073]     MemoryModel: 0
[     3.073]     BankSize: 0
[     3.073]     NumberOfImages: 0
[     3.073]     RedMaskSize: 0
[     3.073]     RedFieldPosition: 0
[     3.073]     GreenMaskSize: 0
[     3.073]     GreenFieldPosition: 0
[     3.073]     BlueMaskSize: 0
[     3.073]     BlueFieldPosition: 0
[     3.073]     RsvdMaskSize: 0
[     3.073]     RsvdFieldPosition: 0
[     3.073]     DirectColorModeInfo: 0
[     3.073]     PhysBasePtr: 0x0
[     3.073]     LinBytesPerScanLine: 0
[     3.073]     BnkNumberOfImagePages: 0
[     3.073]     LinNumberOfImagePages: 0
[     3.073]     LinRedMaskSize: 0
[     3.073]     LinRedFieldPosition: 0
[     3.073]     LinGreenMaskSize: 0
[     3.073]     LinGreenFieldPosition: 0
[     3.073]     LinBlueMaskSize: 0
[     3.073]     LinBlueFieldPosition: 0
[     3.073]     LinRsvdMaskSize: 0
[     3.073]     LinRsvdFieldPosition: 0
[     3.073]     MaxPixelClock: 0
[     3.073] Mode: 11b (0x0)
[     3.073]     ModeAttributes: 0x0
[     3.073]     WinAAttributes: 0x0
[     3.073]     WinBAttributes: 0x0
[     3.073]     WinGranularity: 0
[     3.073]     WinSize: 0
[     3.073]     WinASegment: 0x0
[     3.073]     WinBSegment: 0x0
[     3.073]     WinFuncPtr: 0x0
[     3.073]     BytesPerScanline: 0
[     3.073]     XResolution: 0
[     3.073]     YResolution: 0
[     3.073]     XCharSize: 0
[     3.073]     YCharSize: 0
[     3.073]     NumberOfPlanes: 0
[     3.073]     BitsPerPixel: 0
[     3.073]     NumberOfBanks: 0
[     3.073]     MemoryModel: 0
[     3.073]     BankSize: 0
[     3.073]     NumberOfImages: 0
[     3.073]     RedMaskSize: 0
[     3.073]     RedFieldPosition: 0
[     3.073]     GreenMaskSize: 0
[     3.073]     GreenFieldPosition: 0
[     3.073]     BlueMaskSize: 0
[     3.073]     BlueFieldPosition: 0
[     3.073]     RsvdMaskSize: 0
[     3.073]     RsvdFieldPosition: 0
[     3.073]     DirectColorModeInfo: 0
[     3.073]     PhysBasePtr: 0x0
[     3.073]     LinBytesPerScanLine: 0
[     3.073]     BnkNumberOfImagePages: 0
[     3.073]     LinNumberOfImagePages: 0
[     3.073]     LinRedMaskSize: 0
[     3.073]     LinRedFieldPosition: 0
[     3.073]     LinGreenMaskSize: 0
[     3.073]     LinGreenFieldPosition: 0
[     3.073]     LinBlueMaskSize: 0
[     3.073]     LinBlueFieldPosition: 0
[     3.073]     LinRsvdMaskSize: 0
[     3.073]     LinRsvdFieldPosition: 0
[     3.073]     MaxPixelClock: 0
[     3.073] Mode: 105 (1024x768)
[     3.073]     ModeAttributes: 0x9b
[     3.073]     WinAAttributes: 0x7
[     3.073]     WinBAttributes: 0x0
[     3.073]     WinGranularity: 64
[     3.073]     WinSize: 64
[     3.073]     WinASegment: 0xa000
[     3.073]     WinBSegment: 0x0
[     3.073]     WinFuncPtr: 0xc000867f
[     3.073]     BytesPerScanline: 1024
[     3.073]     XResolution: 1024
[     3.073]     YResolution: 768
[     3.073]     XCharSize: 8
[     3.073]     YCharSize: 16
[     3.073]     NumberOfPlanes: 1
[     3.073]     BitsPerPixel: 8
[     3.073]     NumberOfBanks: 1
[     3.073]     MemoryModel: 4
[     3.073]     BankSize: 0
[     3.073]     NumberOfImages: 41
[     3.073]     RedMaskSize: 0
[     3.073]     RedFieldPosition: 0
[     3.073]     GreenMaskSize: 0
[     3.073]     GreenFieldPosition: 0
[     3.073]     BlueMaskSize: 0
[     3.073]     BlueFieldPosition: 0
[     3.073]     RsvdMaskSize: 0
[     3.073]     RsvdFieldPosition: 0
[     3.073]     DirectColorModeInfo: 0
[     3.073]     PhysBasePtr: 0xb0000000
[     3.073]     LinBytesPerScanLine: 1024
[     3.073]     BnkNumberOfImagePages: 41
[     3.073]     LinNumberOfImagePages: 41
[     3.073]     LinRedMaskSize: 0
[     3.073]     LinRedFieldPosition: 0
[     3.073]     LinGreenMaskSize: 0
[     3.073]     LinGreenFieldPosition: 0
[     3.073]     LinBlueMaskSize: 0
[     3.073]     LinBlueFieldPosition: 0
[     3.073]     LinRsvdMaskSize: 0
[     3.073]     LinRsvdFieldPosition: 0
[     3.073]     MaxPixelClock: 230000000
[     3.074] Mode: 117 (1024x768)
[     3.074]     ModeAttributes: 0x9b
[     3.074]     WinAAttributes: 0x7
[     3.074]     WinBAttributes: 0x0
[     3.074]     WinGranularity: 64
[     3.074]     WinSize: 64
[     3.074]     WinASegment: 0xa000
[     3.074]     WinBSegment: 0x0
[     3.074]     WinFuncPtr: 0xc000867f
[     3.074]     BytesPerScanline: 2048
[     3.074]     XResolution: 1024
[     3.074]     YResolution: 768
[     3.074]     XCharSize: 8
[     3.074]     YCharSize: 16
[     3.074]     NumberOfPlanes: 1
[     3.074]     BitsPerPixel: 16
[     3.074]     NumberOfBanks: 1
[     3.074]     MemoryModel: 6
[     3.074]     BankSize: 0
[     3.074]     NumberOfImages: 20
[     3.074]     RedMaskSize: 5
[     3.074]     RedFieldPosition: 11
[     3.074]     GreenMaskSize: 6
[     3.074]     GreenFieldPosition: 5
[     3.074]     BlueMaskSize: 5
[     3.074]     BlueFieldPosition: 0
[     3.074]     RsvdMaskSize: 0
[     3.074]     RsvdFieldPosition: 0
[     3.074]     DirectColorModeInfo: 0
[     3.074]     PhysBasePtr: 0xb0000000
[     3.074]     LinBytesPerScanLine: 2048
[     3.074]     BnkNumberOfImagePages: 20
[     3.074]     LinNumberOfImagePages: 20
[     3.074]     LinRedMaskSize: 5
[     3.074]     LinRedFieldPosition: 11
[     3.074]     LinGreenMaskSize: 6
[     3.074]     LinGreenFieldPosition: 5
[     3.074]     LinBlueMaskSize: 5
[     3.074]     LinBlueFieldPosition: 0
[     3.074]     LinRsvdMaskSize: 0
[     3.074]     LinRsvdFieldPosition: 0
[     3.074]     MaxPixelClock: 230000000
[     3.074] *Mode: 118 (1024x768)
[     3.074]     ModeAttributes: 0x9b
[     3.074]     WinAAttributes: 0x7
[     3.074]     WinBAttributes: 0x0
[     3.074]     WinGranularity: 64
[     3.074]     WinSize: 64
[     3.074]     WinASegment: 0xa000
[     3.074]     WinBSegment: 0x0
[     3.074]     WinFuncPtr: 0xc000867f
[     3.074]     BytesPerScanline: 4096
[     3.074]     XResolution: 1024
[     3.074]     YResolution: 768
[     3.074]     XCharSize: 8
[     3.074]     YCharSize: 16
[     3.074]     NumberOfPlanes: 1
[     3.074]     BitsPerPixel: 32
[     3.074]     NumberOfBanks: 1
[     3.074]     MemoryModel: 6
[     3.074]     BankSize: 0
[     3.074]     NumberOfImages: 9
[     3.074]     RedMaskSize: 8
[     3.074]     RedFieldPosition: 16
[     3.074]     GreenMaskSize: 8
[     3.074]     GreenFieldPosition: 8
[     3.074]     BlueMaskSize: 8
[     3.074]     BlueFieldPosition: 0
[     3.074]     RsvdMaskSize: 8
[     3.074]     RsvdFieldPosition: 24
[     3.074]     DirectColorModeInfo: 0
[     3.074]     PhysBasePtr: 0xb0000000
[     3.074]     LinBytesPerScanLine: 4096
[     3.074]     BnkNumberOfImagePages: 9
[     3.074]     LinNumberOfImagePages: 9
[     3.074]     LinRedMaskSize: 8
[     3.074]     LinRedFieldPosition: 16
[     3.074]     LinGreenMaskSize: 8
[     3.074]     LinGreenFieldPosition: 8
[     3.074]     LinBlueMaskSize: 8
[     3.074]     LinBlueFieldPosition: 0
[     3.074]     LinRsvdMaskSize: 8
[     3.074]     LinRsvdFieldPosition: 24
[     3.074]     MaxPixelClock: 230000000
[     3.074] *Mode: 112 (640x480)
[     3.075]     ModeAttributes: 0x9b
[     3.075]     WinAAttributes: 0x7
[     3.075]     WinBAttributes: 0x0
[     3.075]     WinGranularity: 64
[     3.075]     WinSize: 64
[     3.075]     WinASegment: 0xa000
[     3.075]     WinBSegment: 0x0
[     3.075]     WinFuncPtr: 0xc000867f
[     3.075]     BytesPerScanline: 2560
[     3.075]     XResolution: 640
[     3.075]     YResolution: 480
[     3.075]     XCharSize: 8
[     3.075]     YCharSize: 16
[     3.075]     NumberOfPlanes: 1
[     3.075]     BitsPerPixel: 32
[     3.075]     NumberOfBanks: 1
[     3.075]     MemoryModel: 6
[     3.075]     BankSize: 0
[     3.075]     NumberOfImages: 25
[     3.075]     RedMaskSize: 8
[     3.075]     RedFieldPosition: 16
[     3.075]     GreenMaskSize: 8
[     3.075]     GreenFieldPosition: 8
[     3.075]     BlueMaskSize: 8
[     3.075]     BlueFieldPosition: 0
[     3.075]     RsvdMaskSize: 8
[     3.075]     RsvdFieldPosition: 24
[     3.075]     DirectColorModeInfo: 0
[     3.075]     PhysBasePtr: 0xb0000000
[     3.075]     LinBytesPerScanLine: 2560
[     3.075]     BnkNumberOfImagePages: 25
[     3.075]     LinNumberOfImagePages: 25
[     3.075]     LinRedMaskSize: 8
[     3.075]     LinRedFieldPosition: 16
[     3.075]     LinGreenMaskSize: 8
[     3.075]     LinGreenFieldPosition: 8
[     3.075]     LinBlueMaskSize: 8
[     3.075]     LinBlueFieldPosition: 0
[     3.075]     LinRsvdMaskSize: 8
[     3.075]     LinRsvdFieldPosition: 24
[     3.075]     MaxPixelClock: 230000000
[     3.075] Mode: 114 (800x600)
[     3.075]     ModeAttributes: 0x9b
[     3.075]     WinAAttributes: 0x7
[     3.075]     WinBAttributes: 0x0
[     3.075]     WinGranularity: 64
[     3.075]     WinSize: 64
[     3.075]     WinASegment: 0xa000
[     3.075]     WinBSegment: 0x0
[     3.075]     WinFuncPtr: 0xc000867f
[     3.075]     BytesPerScanline: 1600
[     3.075]     XResolution: 800
[     3.075]     YResolution: 600
[     3.075]     XCharSize: 8
[     3.075]     YCharSize: 16
[     3.075]     NumberOfPlanes: 1
[     3.075]     BitsPerPixel: 16
[     3.075]     NumberOfBanks: 1
[     3.075]     MemoryModel: 6
[     3.075]     BankSize: 0
[     3.075]     NumberOfImages: 33
[     3.075]     RedMaskSize: 5
[     3.075]     RedFieldPosition: 11
[     3.075]     GreenMaskSize: 6
[     3.075]     GreenFieldPosition: 5
[     3.075]     BlueMaskSize: 5
[     3.075]     BlueFieldPosition: 0
[     3.075]     RsvdMaskSize: 0
[     3.075]     RsvdFieldPosition: 0
[     3.075]     DirectColorModeInfo: 0
[     3.075]     PhysBasePtr: 0xb0000000
[     3.075]     LinBytesPerScanLine: 1600
[     3.075]     BnkNumberOfImagePages: 33
[     3.075]     LinNumberOfImagePages: 33
[     3.075]     LinRedMaskSize: 5
[     3.075]     LinRedFieldPosition: 11
[     3.075]     LinGreenMaskSize: 6
[     3.075]     LinGreenFieldPosition: 5
[     3.075]     LinBlueMaskSize: 5
[     3.075]     LinBlueFieldPosition: 0
[     3.075]     LinRsvdMaskSize: 0
[     3.075]     LinRsvdFieldPosition: 0
[     3.075]     MaxPixelClock: 230000000
[     3.075] *Mode: 115 (800x600)
[     3.075]     ModeAttributes: 0x9b
[     3.075]     WinAAttributes: 0x7
[     3.075]     WinBAttributes: 0x0
[     3.075]     WinGranularity: 64
[     3.075]     WinSize: 64
[     3.075]     WinASegment: 0xa000
[     3.075]     WinBSegment: 0x0
[     3.075]     WinFuncPtr: 0xc000867f
[     3.075]     BytesPerScanline: 3200
[     3.075]     XResolution: 800
[     3.075]     YResolution: 600
[     3.075]     XCharSize: 8
[     3.075]     YCharSize: 16
[     3.075]     NumberOfPlanes: 1
[     3.075]     BitsPerPixel: 32
[     3.075]     NumberOfBanks: 1
[     3.075]     MemoryModel: 6
[     3.075]     BankSize: 0
[     3.075]     NumberOfImages: 16
[     3.075]     RedMaskSize: 8
[     3.075]     RedFieldPosition: 16
[     3.075]     GreenMaskSize: 8
[     3.075]     GreenFieldPosition: 8
[     3.075]     BlueMaskSize: 8
[     3.075]     BlueFieldPosition: 0
[     3.075]     RsvdMaskSize: 8
[     3.075]     RsvdFieldPosition: 24
[     3.075]     DirectColorModeInfo: 0
[     3.075]     PhysBasePtr: 0xb0000000
[     3.075]     LinBytesPerScanLine: 3200
[     3.076]     BnkNumberOfImagePages: 16
[     3.076]     LinNumberOfImagePages: 16
[     3.076]     LinRedMaskSize: 8
[     3.076]     LinRedFieldPosition: 16
[     3.076]     LinGreenMaskSize: 8
[     3.076]     LinGreenFieldPosition: 8
[     3.076]     LinBlueMaskSize: 8
[     3.076]     LinBlueFieldPosition: 0
[     3.076]     LinRsvdMaskSize: 8
[     3.076]     LinRsvdFieldPosition: 24
[     3.076]     MaxPixelClock: 230000000
[     3.076] Mode: 101 (640x480)
[     3.076]     ModeAttributes: 0x9b
[     3.076]     WinAAttributes: 0x7
[     3.076]     WinBAttributes: 0x0
[     3.076]     WinGranularity: 64
[     3.076]     WinSize: 64
[     3.076]     WinASegment: 0xa000
[     3.076]     WinBSegment: 0x0
[     3.076]     WinFuncPtr: 0xc000867f
[     3.076]     BytesPerScanline: 640
[     3.076]     XResolution: 640
[     3.076]     YResolution: 480
[     3.076]     XCharSize: 8
[     3.076]     YCharSize: 16
[     3.076]     NumberOfPlanes: 1
[     3.076]     BitsPerPixel: 8
[     3.076]     NumberOfBanks: 1
[     3.076]     MemoryModel: 4
[     3.076]     BankSize: 0
[     3.076]     NumberOfImages: 101
[     3.076]     RedMaskSize: 0
[     3.076]     RedFieldPosition: 0
[     3.076]     GreenMaskSize: 0
[     3.076]     GreenFieldPosition: 0
[     3.076]     BlueMaskSize: 0
[     3.076]     BlueFieldPosition: 0
[     3.076]     RsvdMaskSize: 0
[     3.076]     RsvdFieldPosition: 0
[     3.076]     DirectColorModeInfo: 0
[     3.076]     PhysBasePtr: 0xb0000000
[     3.076]     LinBytesPerScanLine: 640
[     3.076]     BnkNumberOfImagePages: 101
[     3.076]     LinNumberOfImagePages: 101
[     3.076]     LinRedMaskSize: 0
[     3.076]     LinRedFieldPosition: 0
[     3.076]     LinGreenMaskSize: 0
[     3.076]     LinGreenFieldPosition: 0
[     3.076]     LinBlueMaskSize: 0
[     3.076]     LinBlueFieldPosition: 0
[     3.076]     LinRsvdMaskSize: 0
[     3.076]     LinRsvdFieldPosition: 0
[     3.076]     MaxPixelClock: 230000000
[     3.076] Mode: 103 (800x600)
[     3.076]     ModeAttributes: 0x9b
[     3.076]     WinAAttributes: 0x7
[     3.076]     WinBAttributes: 0x0
[     3.076]     WinGranularity: 64
[     3.076]     WinSize: 64
[     3.076]     WinASegment: 0xa000
[     3.076]     WinBSegment: 0x0
[     3.076]     WinFuncPtr: 0xc000867f
[     3.076]     BytesPerScanline: 832
[     3.076]     XResolution: 800
[     3.076]     YResolution: 600
[     3.076]     XCharSize: 8
[     3.076]     YCharSize: 16
[     3.076]     NumberOfPlanes: 1
[     3.076]     BitsPerPixel: 8
[     3.076]     NumberOfBanks: 1
[     3.076]     MemoryModel: 4
[     3.076]     BankSize: 0
[     3.076]     NumberOfImages: 62
[     3.076]     RedMaskSize: 0
[     3.076]     RedFieldPosition: 0
[     3.076]     GreenMaskSize: 0
[     3.076]     GreenFieldPosition: 0
[     3.076]     BlueMaskSize: 0
[     3.076]     BlueFieldPosition: 0
[     3.076]     RsvdMaskSize: 0
[     3.076]     RsvdFieldPosition: 0
[     3.076]     DirectColorModeInfo: 0
[     3.076]     PhysBasePtr: 0xb0000000
[     3.076]     LinBytesPerScanLine: 832
[     3.076]     BnkNumberOfImagePages: 62
[     3.076]     LinNumberOfImagePages: 62
[     3.076]     LinRedMaskSize: 0
[     3.076]     LinRedFieldPosition: 0
[     3.076]     LinGreenMaskSize: 0
[     3.076]     LinGreenFieldPosition: 0
[     3.076]     LinBlueMaskSize: 0
[     3.076]     LinBlueFieldPosition: 0
[     3.076]     LinRsvdMaskSize: 0
[     3.076]     LinRsvdFieldPosition: 0
[     3.076]     MaxPixelClock: 230000000
[     3.077] Mode: 111 (640x480)
[     3.077]     ModeAttributes: 0x9b
[     3.077]     WinAAttributes: 0x7
[     3.077]     WinBAttributes: 0x0
[     3.077]     WinGranularity: 64
[     3.077]     WinSize: 64
[     3.077]     WinASegment: 0xa000
[     3.077]     WinBSegment: 0x0
[     3.077]     WinFuncPtr: 0xc000867f
[     3.077]     BytesPerScanline: 1280
[     3.077]     XResolution: 640
[     3.077]     YResolution: 480
[     3.077]     XCharSize: 8
[     3.077]     YCharSize: 16
[     3.077]     NumberOfPlanes: 1
[     3.077]     BitsPerPixel: 16
[     3.077]     NumberOfBanks: 1
[     3.077]     MemoryModel: 6
[     3.077]     BankSize: 0
[     3.077]     NumberOfImages: 50
[     3.077]     RedMaskSize: 5
[     3.077]     RedFieldPosition: 11
[     3.077]     GreenMaskSize: 6
[     3.077]     GreenFieldPosition: 5
[     3.077]     BlueMaskSize: 5
[     3.077]     BlueFieldPosition: 0
[     3.077]     RsvdMaskSize: 0
[     3.077]     RsvdFieldPosition: 0
[     3.077]     DirectColorModeInfo: 0
[     3.077]     PhysBasePtr: 0xb0000000
[     3.077]     LinBytesPerScanLine: 1280
[     3.077]     BnkNumberOfImagePages: 50
[     3.077]     LinNumberOfImagePages: 50
[     3.077]     LinRedMaskSize: 5
[     3.077]     LinRedFieldPosition: 11
[     3.077]     LinGreenMaskSize: 6
[     3.077]     LinGreenFieldPosition: 5
[     3.077]     LinBlueMaskSize: 5
[     3.077]     LinBlueFieldPosition: 0
[     3.077]     LinRsvdMaskSize: 0
[     3.077]     LinRsvdFieldPosition: 0
[     3.077]     MaxPixelClock: 230000000
[     3.077] 
[     3.077] (II) VESA(0): Total Memory: 511 64KB banks (32704kB)
[     3.077] (II) VESA(0): <default monitor>: Using hsync value of 48.26 kHz
[     3.077] (II) VESA(0): <default monitor>: Using vrefresh value of 60.10 Hz
[     3.077] (WW) VESA(0): Unable to estimate virtual size
[     3.077] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[     3.077] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[     3.077] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[     3.077] (WW) VESA(0): No valid modes left. Trying less strict filter...
[     3.077] (II) VESA(0): <default monitor>: Using hsync value of 48.26 kHz
[     3.077] (II) VESA(0): <default monitor>: Using vrefresh value of 60.10 Hz
[     3.077] (WW) VESA(0): Unable to estimate virtual size
[     3.077] (II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
[     3.077] (II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
[     3.077] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[     3.077] (**) VESA(0): *Built-in mode "1024x768"
[     3.077] (**) VESA(0): Display dimensions: (310, 170) mm
[     3.077] (**) VESA(0): DPI set to (83, 114)
[     3.077] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
[     3.077] (**) VESA(0): Using "Shadow Framebuffer"
[     3.077] (II) Loading sub module "shadow"
[     3.077] (II) LoadModule: "shadow"
[     3.077] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     3.077] (II) Module shadow: vendor="X.Org Foundation"
[     3.077]     compiled for 1.13.3, module version = 1.1.0
[     3.077]     ABI class: X.Org ANSI C Emulation, version 0.4
[     3.077] (II) Loading sub module "fb"
[     3.077] (II) LoadModule: "fb"
[     3.077] (II) Loading /usr/lib/xorg/modules/libfb.so
[     3.077] (II) Module fb: vendor="X.Org Foundation"
[     3.077]     compiled for 1.13.3, module version = 1.0.0
[     3.077]     ABI class: X.Org ANSI C Emulation, version 0.4
[     3.077] (II) UnloadModule: "modesetting"
[     3.077] (II) Unloading modesetting
[     3.077] (II) UnloadModule: "fbdev"
[     3.077] (II) Unloading fbdev
[     3.077] (II) UnloadSubModule: "fbdevhw"
[     3.077] (II) Unloading fbdevhw
[     3.077] (==) Depth 24 pixmap format is 32 bpp
[     3.078] (II) Loading sub module "int10"
[     3.078] (II) LoadModule: "int10"
[     3.078] (II) Loading /usr/lib/xorg/modules/libint10.so
[     3.078] (II) Module int10: vendor="X.Org Foundation"
[     3.078]     compiled for 1.13.3, module version = 1.0.0
[     3.078]     ABI class: X.Org Video Driver, version 13.1
[     3.078] (II) VESA(0): initializing int10
[     3.078] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[     3.078] (II) VESA(0): VESA BIOS detected
[     3.078] (II) VESA(0): VESA VBE Version 3.0
[     3.078] (II) VESA(0): VESA VBE Total Mem: 32704 kB
[     3.078] (II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Mobile Graphics Chipset Accelerated VGA BIOS
[     3.078] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[     3.078] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[     3.078] (II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Mobile Graphics Controller
[     3.078] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[     3.079] (II) VESA(0): virtual address = 0x7f392ab51000,
    physical address = 0xb0000000, size = 33488896
[     3.083] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[     3.155] (==) VESA(0): Default visual is TrueColor
[     3.155] (==) VESA(0): Backing store disabled
[     3.155] (==) VESA(0): DPMS enabled
[     3.155] (==) RandR enabled
[     3.158] (II) SELinux: Disabled on system
[     3.158] (II) AIGLX: Screen 0 is not DRI2 capable
[     3.158] (II) AIGLX: Screen 0 is not DRI capable
[     3.173] (II) AIGLX: Loaded and initialized swrast
[     3.173] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[     3.179] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     3.180] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     3.180] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.180] (II) LoadModule: "evdev"
[     3.181] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     3.181] (II) Module evdev: vendor="X.Org Foundation"
[     3.181]     compiled for 1.13.3, module version = 2.7.3
[     3.181]     Module class: X.Org XInput Driver
[     3.181]     ABI class: X.Org XInput driver, version 18.0
[     3.181] (II) Using input driver 'evdev' for 'Power Button'
[     3.181] (**) Power Button: always reports core events
[     3.181] (**) evdev: Power Button: Device: "/dev/input/event2"
[     3.181] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.181] (--) evdev: Power Button: Found keys
[     3.181] (II) evdev: Power Button: Configuring as keyboard
[     3.181] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[     3.181] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     3.181] (**) Option "xkb_rules" "evdev"
[     3.181] (**) Option "xkb_model" "pc105"
[     3.181] (**) Option "xkb_layout" "us"
[     3.181] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     3.181] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.181] (II) Using input driver 'evdev' for 'Power Button'
[     3.181] (**) Power Button: always reports core events
[     3.181] (**) evdev: Power Button: Device: "/dev/input/event0"
[     3.182] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.182] (--) evdev: Power Button: Found keys
[     3.182] (II) evdev: Power Button: Configuring as keyboard
[     3.182] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     3.182] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     3.182] (**) Option "xkb_rules" "evdev"
[     3.182] (**) Option "xkb_model" "pc105"
[     3.182] (**) Option "xkb_layout" "us"
[     3.182] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[     3.182] (II) No input driver specified, ignoring this device.
[     3.182] (II) This device may have been added with another device file.
[     3.182] (II) config/udev: Adding input device TOSHIBA Web Camera - MP (/dev/input/event5)
[     3.182] (**) TOSHIBA Web Camera - MP: Applying InputClass "evdev keyboard catchall"
[     3.182] (II) Using input driver 'evdev' for 'TOSHIBA Web Camera - MP'
[     3.182] (**) TOSHIBA Web Camera - MP: always reports core events
[     3.182] (**) evdev: TOSHIBA Web Camera - MP: Device: "/dev/input/event5"
[     3.182] (--) evdev: TOSHIBA Web Camera - MP: Vendor 0x58f Product 0xb003
[     3.182] (--) evdev: TOSHIBA Web Camera - MP: Found keys
[     3.182] (II) evdev: TOSHIBA Web Camera - MP: Configuring as keyboard
[     3.182] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input5/event5"
[     3.182] (II) XINPUT: Adding extended input device "TOSHIBA Web Camera - MP" (type: KEYBOARD, id 8)
[     3.182] (**) Option "xkb_rules" "evdev"
[     3.182] (**) Option "xkb_model" "pc105"
[     3.182] (**) Option "xkb_layout" "us"
[     3.182] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event6)
[     3.182] (II) No input driver specified, ignoring this device.
[     3.182] (II) This device may have been added with another device file.
[     3.182] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event7)
[     3.182] (II) No input driver specified, ignoring this device.
[     3.182] (II) This device may have been added with another device file.
[     3.182] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event8)
[     3.183] (II) No input driver specified, ignoring this device.
[     3.183] (II) This device may have been added with another device file.
[     3.183] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[     3.183] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     3.183] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     3.183] (**) AT Translated Set 2 keyboard: always reports core events
[     3.183] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[     3.183] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     3.183] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     3.183] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     3.183] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[     3.183] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[     3.183] (**) Option "xkb_rules" "evdev"
[     3.183] (**) Option "xkb_model" "pc105"
[     3.183] (**) Option "xkb_layout" "us"
[     3.184] (II) config/udev: Adding input device Toshiba input device (/dev/input/event4)
[     3.184] (**) Toshiba input device: Applying InputClass "evdev keyboard catchall"
[     3.184] (II) Using input driver 'evdev' for 'Toshiba input device'
[     3.184] (**) Toshiba input device: always reports core events
[     3.184] (**) evdev: Toshiba input device: Device: "/dev/input/event4"
[     3.184] (--) evdev: Toshiba input device: Vendor 0 Product 0
[     3.184] (--) evdev: Toshiba input device: Found keys
[     3.184] (II) evdev: Toshiba input device: Configuring as keyboard
[     3.184] (**) Option "config_info" "udev:/sys/devices/virtual/input/input4/event4"
[     3.184] (II) XINPUT: Adding extended input device "Toshiba input device" (type: KEYBOARD, id 10)
[     3.184] (**) Option "xkb_rules" "evdev"
[     3.184] (**) Option "xkb_model" "pc105"
[     3.184] (**) Option "xkb_layout" "us"
[     3.769] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[     3.769] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     3.769] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     3.769] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     3.769] (II) LoadModule: "synaptics"
[     3.770] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     3.770] (II) Module synaptics: vendor="X.Org Foundation"
[     3.770]     compiled for 1.13.1.901, module version = 1.6.2
[     3.770]     Module class: X.Org XInput Driver
[     3.770]     ABI class: X.Org XInput driver, version 18.0
[     3.770] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     3.770] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     3.770] (**) Option "Device" "/dev/input/event9"
[     3.784] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[     3.784] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5686
[     3.784] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4786
[     3.784] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     3.784] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     3.784] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[     3.784] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     3.784] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     3.784] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     3.788] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input9/event9"
[     3.788] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[     3.788] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     3.788] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[     3.788] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[     3.788] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     3.788] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     3.788] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     3.788] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     3.788] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     3.788] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[     3.788] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    14.199] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm

```

I noticed there was not xorg.conf file in use.  I read that there shouldn't be one but I've always used one with nvidia in the past.  I could sure use some help with this.  Big thanks for any help

---

### Post by proksy on 2013-12-15
Sorry everyone, I have been so busy with work I haven't had any time to troubleshoot this.  From reading through the log I see some lines that concern me:

Using system config directory "/usr/share/X11/xorg.conf.d"


[FONT=arial]I looked in this directory but there are no config files that relate to intel video/graphics driver[/FONT]. [FONT=arial]These are what I have

[/FONT]11-evdev-quirks.conf      
50-vmmouse.conf
11-evdev-trackpoint.conf  
50-wacom.conf
10-evdev.conf  
50-synaptics.conf         
51-synaptics-quirks.conf[FONT=arial][/FONT]


Loading /usr/lib/xorg/modules/drivers/intel_drv.so


[FONT=arial]This appears to load the intel driver but then...

[/FONT]
Loading /usr/lib/xorg/modules/drivers/vesa_drv.so

[FONT=arial]I don't know why it needs to load the vesa driver but I suspect as a back up incase the primary driver fails.

[/FONT]
[     3.047] (WW) Falling back to old probe method for modesetting
[     3.047] (EE) open /dev/dri/card0: No such file or directory
[     3.047] (WW) Falling back to old probe method for fbdev

[FONT=arial]As I posted earlier I had to install the OS with the grub nomodesetting option so I tried dissabling that so I did and my OS would
fail to load just as it did when I tried to install it initially. /dev/dri is not a directory and card0 does not exist BUT /dev/video0 DOES exist. 
There should be a config file somewhere that is pointing to this bad directory reference.  Can someone help me? I don't know anything about
this issue and am having problems googling because there are so many unrelated issues that match my search queries.  I think I need to
edit a config file somewhere. Thanks!
[/FONT]

---

### Post by efflandt on 2013-12-16
X is pretty much automatic and xorg.conf is not normally needed unless you need to do something special. In my 64-bit 12.04 desktop even with Nvidia graphics, it exists, but is empty:```
efflandt@xps8100-1204:~$ ls -l /etc/X11/xorg.conf
-rw-r--r-- 1 root root 1 May  9  2013 /etc/X11/xorg.conf
```My laptop running 64-bit 13.10 does not even have xorg.conf. It has both integrated Intel HD 4600 and Nvidia GTX 765M graphics, and with the default Intel graphics, the parts you mention in your 2nd post look the same and most of your Xorg.0.log (including VESA), other than resolution and other hardware unrelated to video.

VESA is a set of standards for video and Intel is pretty standard. So I don't think you really have a problem other than the limitations of Intel video in general (lack of speed and certain capabilities). When trying some graphics benchmarks (in Gaming forum) some worked fine on Intel, some were very slow, and some would not run at all (they all worked on Nvidia). Did you try your game?

---

