---
title: "Toshiba Satellite Display Blacks Out. Desktop shows at first"
date: 2013-03-26
forum: General Help
---

### Post by slixz85 on 2013-03-26
hi. just as title says. i have a toshiba satellite a205 and i have burned several iso's and tried many ubuntu variants, debian variants and even archbang. on live cd's i cant get the display to show the desktop and menu etc upon boot. but within 5 seconds or so the whole display just blackouts out and alt f2 alt f8 etc etc will not bring anything back up or any of my function keys. on most all the os's i have tried. i got one to install which is lxle but is does this if not in recovery mode. recovery mode keeps the screen on constantly in most all of these os's i have tried so i know it is not a screen problem. surely some file i need to edit or something else to do. please help as this is a pain and i would like to install any os i would like to and know what to do to fix this. with lxle (not lxde the environment the new os that came out) the noapic nolapic worked but with other os's it did not. that is how i got this to install. thanks again to any help with this tricky laptop. also wifi won't work iwconfig shows wlan0 and rfkill is unblocked on all and still no wifi sources appear. but that will be a whole other topic later.

laptop specs : [http://www.cnet.com/laptops/toshiba-satellite-a205-s5825/4507-3121_7-32976276.html](http://www.cnet.com/laptops/toshiba-satellite-a205-s5825/4507-3121_7-32976276.html)

thanks

---

### Post by papibe on 2013-03-26
Hi  slixz85.

Could you please post the content of these files:
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```
Paste them separately here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and post back the links to them.

Regards.

---

### Post by slixz85 on 2013-03-26
not seeing a xorg.conf in the x11 dir but i found the log of xorg.0.log here it is. thanks for quick reply

```

[    33.184] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    33.184] X Protocol Version 11, Revision 0
[    33.184] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    33.184] Current Operating System: Linux ace-Satellite 3.2.0-40-generic #64-Ubuntu SMP Mon Mar 25 21:22:10 UTC 2013 x86_64
[    33.185] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-40-generic root=UUID=a802dae2-e294-4cec-b385-c1c190f8ccbf ro recovery nomodeset
[    33.185] Build Date: 27 February 2013  02:07:42AM
[    33.185] xorg-server 2:1.11.4-0ubuntu10.12 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    33.185] Current version of pixman: 0.24.4
[    33.185] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    33.185] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    33.185] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 26 15:19:38 2013
[    33.185] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    33.187] (==) No Layout section.  Using the first Screen section.
[    33.187] (==) No screen section available. Using defaults.
[    33.187] (**) |-->Screen "Default Screen Section" (0)
[    33.187] (**) |   |-->Monitor "<default monitor>"
[    33.187] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    33.187] (==) Automatically adding devices
[    33.189] (==) Automatically enabling devices
[    33.189] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    33.189] 	Entry deleted from font path.
[    33.189] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    33.189] 	Entry deleted from font path.
[    33.189] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    33.189] 	Entry deleted from font path.
[    33.189] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    33.189] 	Entry deleted from font path.
[    33.189] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	built-ins
[    33.189] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    33.189] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    33.189] (II) Loader magic: 0x7fe5f5d46b00
[    33.189] (II) Module ABI versions:
[    33.189] 	X.Org ANSI C Emulation: 0.4
[    33.189] 	X.Org Video Driver: 11.0
[    33.189] 	X.Org XInput driver : 16.0
[    33.189] 	X.Org Server Extension : 6.0
[    33.190] (--) PCI:*(0:0:2:0) 8086:2a02:1179:ff00 rev 12, Mem @ 0xfc000000/1048576, 0xd0000000/268435456, I/O @ 0x00001800/8
[    33.190] (--) PCI: (0:0:2:1) 8086:2a03:1179:ff00 rev 12, Mem @ 0xfc100000/1048576
[    33.190] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    33.190] (II) LoadModule: "extmod"
[    33.213] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    33.213] (II) Module extmod: vendor="X.Org Foundation"
[    33.213] 	compiled for 1.11.3, module version = 1.0.0
[    33.213] 	Module class: X.Org Server Extension
[    33.213] 	ABI class: X.Org Server Extension, version 6.0
[    33.213] (II) Loading extension MIT-SCREEN-SAVER
[    33.213] (II) Loading extension XFree86-VidModeExtension
[    33.213] (II) Loading extension XFree86-DGA
[    33.213] (II) Loading extension DPMS
[    33.213] (II) Loading extension XVideo
[    33.213] (II) Loading extension XVideo-MotionCompensation
[    33.213] (II) Loading extension X-Resource
[    33.213] (II) LoadModule: "dbe"
[    33.214] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    33.214] (II) Module dbe: vendor="X.Org Foundation"
[    33.214] 	compiled for 1.11.3, module version = 1.0.0
[    33.214] 	Module class: X.Org Server Extension
[    33.214] 	ABI class: X.Org Server Extension, version 6.0
[    33.214] (II) Loading extension DOUBLE-BUFFER
[    33.214] (II) LoadModule: "glx"
[    33.214] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    33.214] (II) Module glx: vendor="X.Org Foundation"
[    33.214] 	compiled for 1.11.3, module version = 1.0.0
[    33.214] 	ABI class: X.Org Server Extension, version 6.0
[    33.214] (==) AIGLX enabled
[    33.214] (II) Loading extension GLX
[    33.214] (II) LoadModule: "record"
[    33.214] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    33.215] (II) Module record: vendor="X.Org Foundation"
[    33.215] 	compiled for 1.11.3, module version = 1.13.0
[    33.215] 	Module class: X.Org Server Extension
[    33.215] 	ABI class: X.Org Server Extension, version 6.0
[    33.215] (II) Loading extension RECORD
[    33.215] (II) LoadModule: "dri"
[    33.215] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    33.215] (II) Module dri: vendor="X.Org Foundation"
[    33.215] 	compiled for 1.11.3, module version = 1.0.0
[    33.215] 	ABI class: X.Org Server Extension, version 6.0
[    33.215] (II) Loading extension XFree86-DRI
[    33.215] (II) LoadModule: "dri2"
[    33.215] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    33.216] (II) Module dri2: vendor="X.Org Foundation"
[    33.216] 	compiled for 1.11.3, module version = 1.2.0
[    33.216] 	ABI class: X.Org Server Extension, version 6.0
[    33.216] (II) Loading extension DRI2
[    33.216] (==) Matched intel as autoconfigured driver 0
[    33.216] (==) Matched vesa as autoconfigured driver 1
[    33.216] (==) Matched fbdev as autoconfigured driver 2
[    33.216] (==) Assigned the driver to the xf86ConfigLayout
[    33.216] (II) LoadModule: "intel"
[    33.230] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    33.230] (II) Module intel: vendor="X.Org Foundation"
[    33.230] 	compiled for 1.11.3, module version = 2.17.0
[    33.230] 	Module class: X.Org Video Driver
[    33.230] 	ABI class: X.Org Video Driver, version 11.0
[    33.230] (II) LoadModule: "vesa"
[    33.231] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    33.231] (II) Module vesa: vendor="X.Org Foundation"
[    33.231] 	compiled for 1.11.3, module version = 2.3.0
[    33.231] 	Module class: X.Org Video Driver
[    33.231] 	ABI class: X.Org Video Driver, version 11.0
[    33.231] (II) LoadModule: "fbdev"
[    33.231] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    33.231] (II) Module fbdev: vendor="X.Org Foundation"
[    33.231] 	compiled for 1.11.3, module version = 0.4.2
[    33.232] 	ABI class: X.Org Video Driver, version 11.0
[    33.232] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
	Ivybridge Server (GT2)
[    33.232] (II) VESA: driver for VESA chipsets: vesa
[    33.232] (II) FBDEV: driver for framebuffer: fbdev
[    33.232] (++) using VT number 7

[    33.236] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    33.236] (WW) Falling back to old probe method for fbdev
[    33.236] (II) Loading sub module "fbdevhw"
[    33.236] (II) LoadModule: "fbdevhw"
[    33.237] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    33.237] (II) Module fbdevhw: vendor="X.Org Foundation"
[    33.237] 	compiled for 1.11.3, module version = 0.0.2
[    33.237] 	ABI class: X.Org Video Driver, version 11.0
[    33.237] (EE) open /dev/fb0: No such file or directory
[    33.237] (II) Loading sub module "vbe"
[    33.237] (II) LoadModule: "vbe"
[    33.237] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    33.237] (II) Module vbe: vendor="X.Org Foundation"
[    33.237] 	compiled for 1.11.3, module version = 1.1.0
[    33.237] 	ABI class: X.Org Video Driver, version 11.0
[    33.237] (II) Loading sub module "int10"
[    33.237] (II) LoadModule: "int10"
[    33.238] (II) Loading /usr/lib/xorg/modules/libint10.so
[    33.238] (II) Module int10: vendor="X.Org Foundation"
[    33.238] 	compiled for 1.11.3, module version = 1.0.0
[    33.238] 	ABI class: X.Org Video Driver, version 11.0
[    33.238] (II) VESA(0): initializing int10
[    33.239] (II) VESA(0): Bad V_BIOS checksum
[    33.239] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    33.239] (II) VESA(0): VESA BIOS detected
[    33.239] (II) VESA(0): VESA VBE Version 3.0
[    33.239] (II) VESA(0): VESA VBE Total Mem: 7616 kB
[    33.239] (II) VESA(0): VESA VBE OEM: Intel(r)Crestline Graphics Chip Accelerated VGA BIOS
[    33.239] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    33.239] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    33.239] (II) VESA(0): VESA VBE OEM Product: Intel(r)Crestline Graphics Controller
[    33.239] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    33.250] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    33.250] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    33.250] (==) VESA(0): RGB weight 888
[    33.250] (==) VESA(0): Default visual is TrueColor
[    33.250] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    33.250] (II) Loading sub module "ddc"
[    33.250] (II) LoadModule: "ddc"
[    33.250] (II) Module "ddc" already built-in
[    33.251] (II) VESA(0): VESA VBE DDC supported
[    33.251] (II) VESA(0): VESA VBE DDC Level 2
[    33.251] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    33.263] (II) VESA(0): VESA VBE DDC read successfully
[    33.263] (II) VESA(0): Manufacturer: SEC  Model: 3645  Serial#: 0
[    33.263] (II) VESA(0): Year: 2005  Week: 0
[    33.263] (II) VESA(0): EDID Version: 1.3
[    33.263] (II) VESA(0): Digital Display Input
[    33.263] (II) VESA(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    33.263] (II) VESA(0): Gamma: 2.20
[    33.263] (II) VESA(0): No DPMS capabilities specified
[    33.263] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    33.263] (II) VESA(0): First detailed timing is preferred mode
[    33.263] (II) VESA(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[    33.263] (II) VESA(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    33.263] (II) VESA(0): Manufacturer's mask: 0
[    33.263] (II) VESA(0): Supported detailed timing:
[    33.263] (II) VESA(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
[    33.263] (II) VESA(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
[    33.263] (II) VESA(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
[    33.263] (II) VESA(0): Unknown vendor-specific block f
[    33.263] (II) VESA(0):  SAMSUNG
[    33.263] (II) VESA(0):  LTN154X3-L05
[    33.263] (II) VESA(0): EDID (in hex):
[    33.263] (II) VESA(0): 	00ffffffffffff004ca3453600000000
[    33.264] (II) VESA(0): 	000f0103802115780a87f594574f8c27
[    33.264] (II) VESA(0): 	27505400000001010101010101010101
[    33.264] (II) VESA(0): 	010101010101ee1a0080502010301030
[    33.264] (II) VESA(0): 	13004bcf100000190000000f00000000
[    33.264] (II) VESA(0): 	00000000002387026400000000fe0053
[    33.264] (II) VESA(0): 	414d53554e470a2020202020000000fe
[    33.264] (II) VESA(0): 	004c544e31353458332d4c30350a0061
[    33.264] (II) VESA(0): EDID vendor "SEC", prod id 13893
[    33.264] (II) VESA(0): Printing DDC gathered Modelines:
[    33.264] (II) VESA(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
[    33.264] (II) VESA(0): Searching for matching VESA mode(s):
[    33.264] Mode: 160 (1280x800)
[    33.264] 	ModeAttributes: 0x9b
[    33.264] 	WinAAttributes: 0x7
[    33.264] 	WinBAttributes: 0x0
[    33.264] 	WinGranularity: 64
[    33.264] 	WinSize: 64
[    33.264] 	WinASegment: 0xa000
[    33.264] 	WinBSegment: 0x0
[    33.264] 	WinFuncPtr: 0xc0007b7a
[    33.264] 	BytesPerScanline: 1280
[    33.264] 	XResolution: 1280
[    33.264] 	YResolution: 800
[    33.264] 	XCharSize: 8
[    33.264] 	YCharSize: 16
[    33.264] 	NumberOfPlanes: 1
[    33.265] 	BitsPerPixel: 8
[    33.265] 	NumberOfBanks: 1
[    33.265] 	MemoryModel: 4
[    33.265] 	BankSize: 0
[    33.265] 	NumberOfImages: 6
[    33.265] 	RedMaskSize: 0
[    33.265] 	RedFieldPosition: 0
[    33.265] 	GreenMaskSize: 0
[    33.265] 	GreenFieldPosition: 0
[    33.265] 	BlueMaskSize: 0
[    33.265] 	BlueFieldPosition: 0
[    33.265] 	RsvdMaskSize: 0
[    33.265] 	RsvdFieldPosition: 0
[    33.265] 	DirectColorModeInfo: 0
[    33.265] 	PhysBasePtr: 0xd0000000
[    33.265] 	LinBytesPerScanLine: 1280
[    33.265] 	BnkNumberOfImagePages: 6
[    33.265] 	LinNumberOfImagePages: 6
[    33.265] 	LinRedMaskSize: 0
[    33.265] 	LinRedFieldPosition: 0
[    33.265] 	LinGreenMaskSize: 0
[    33.265] 	LinGreenFieldPosition: 0
[    33.265] 	LinBlueMaskSize: 0
[    33.265] 	LinBlueFieldPosition: 0
[    33.265] 	LinRsvdMaskSize: 0
[    33.265] 	LinRsvdFieldPosition: 0
[    33.265] 	MaxPixelClock: 230000000
[    33.265] Mode: 161 (1280x800)
[    33.265] 	ModeAttributes: 0x9b
[    33.265] 	WinAAttributes: 0x7
[    33.265] 	WinBAttributes: 0x0
[    33.265] 	WinGranularity: 64
[    33.265] 	WinSize: 64
[    33.265] 	WinASegment: 0xa000
[    33.265] 	WinBSegment: 0x0
[    33.265] 	WinFuncPtr: 0xc0007b7a
[    33.265] 	BytesPerScanline: 2560
[    33.265] 	XResolution: 1280
[    33.265] 	YResolution: 800
[    33.265] 	XCharSize: 8
[    33.265] 	YCharSize: 16
[    33.265] 	NumberOfPlanes: 1
[    33.265] 	BitsPerPixel: 16
[    33.266] 	NumberOfBanks: 1
[    33.266] 	MemoryModel: 6
[    33.266] 	BankSize: 0
[    33.266] 	NumberOfImages: 2
[    33.266] 	RedMaskSize: 5
[    33.266] 	RedFieldPosition: 11
[    33.266] 	GreenMaskSize: 6
[    33.266] 	GreenFieldPosition: 5
[    33.266] 	BlueMaskSize: 5
[    33.266] 	BlueFieldPosition: 0
[    33.266] 	RsvdMaskSize: 0
[    33.266] 	RsvdFieldPosition: 0
[    33.266] 	DirectColorModeInfo: 0
[    33.266] 	PhysBasePtr: 0xd0000000
[    33.266] 	LinBytesPerScanLine: 2560
[    33.266] 	BnkNumberOfImagePages: 2
[    33.266] 	LinNumberOfImagePages: 2
[    33.266] 	LinRedMaskSize: 5
[    33.266] 	LinRedFieldPosition: 11
[    33.266] 	LinGreenMaskSize: 6
[    33.266] 	LinGreenFieldPosition: 5
[    33.266] 	LinBlueMaskSize: 5
[    33.266] 	LinBlueFieldPosition: 0
[    33.266] 	LinRsvdMaskSize: 0
[    33.266] 	LinRsvdFieldPosition: 0
[    33.266] 	MaxPixelClock: 230000000
[    33.266] *Mode: 162 (1280x800)
[    33.266] 	ModeAttributes: 0x9b
[    33.266] 	WinAAttributes: 0x7
[    33.266] 	WinBAttributes: 0x0
[    33.266] 	WinGranularity: 64
[    33.266] 	WinSize: 64
[    33.266] 	WinASegment: 0xa000
[    33.266] 	WinBSegment: 0x0
[    33.266] 	WinFuncPtr: 0xc0007b7a
[    33.266] 	BytesPerScanline: 5120
[    33.266] 	XResolution: 1280
[    33.266] 	YResolution: 800
[    33.266] 	XCharSize: 8
[    33.266] 	YCharSize: 16
[    33.266] 	NumberOfPlanes: 1
[    33.266] 	BitsPerPixel: 32
[    33.266] 	NumberOfBanks: 1
[    33.267] 	MemoryModel: 6
[    33.267] 	BankSize: 0
[    33.267] 	NumberOfImages: 0
[    33.267] 	RedMaskSize: 8
[    33.267] 	RedFieldPosition: 16
[    33.267] 	GreenMaskSize: 8
[    33.267] 	GreenFieldPosition: 8
[    33.267] 	BlueMaskSize: 8
[    33.267] 	BlueFieldPosition: 0
[    33.267] 	RsvdMaskSize: 8
[    33.267] 	RsvdFieldPosition: 24
[    33.267] 	DirectColorModeInfo: 0
[    33.267] 	PhysBasePtr: 0xd0000000
[    33.267] 	LinBytesPerScanLine: 5120
[    33.267] 	BnkNumberOfImagePages: 0
[    33.267] 	LinNumberOfImagePages: 0
[    33.267] 	LinRedMaskSize: 8
[    33.267] 	LinRedFieldPosition: 16
[    33.267] 	LinGreenMaskSize: 8
[    33.267] 	LinGreenFieldPosition: 8
[    33.267] 	LinBlueMaskSize: 8
[    33.267] 	LinBlueFieldPosition: 0
[    33.267] 	LinRsvdMaskSize: 8
[    33.267] 	LinRsvdFieldPosition: 24
[    33.267] 	MaxPixelClock: 230000000
[    33.267] Mode: 163 (0x0)
[    33.267] 	ModeAttributes: 0x0
[    33.267] 	WinAAttributes: 0x0
[    33.267] 	WinBAttributes: 0x0
[    33.267] 	WinGranularity: 0
[    33.267] 	WinSize: 0
[    33.267] 	WinASegment: 0x0
[    33.267] 	WinBSegment: 0x0
[    33.267] 	WinFuncPtr: 0x0
[    33.267] 	BytesPerScanline: 0
[    33.267] 	XResolution: 0
[    33.267] 	YResolution: 0
[    33.267] 	XCharSize: 0
[    33.267] 	YCharSize: 0
[    33.267] 	NumberOfPlanes: 0
[    33.267] 	BitsPerPixel: 0
[    33.267] 	NumberOfBanks: 0
[    33.267] 	MemoryModel: 0
[    33.267] 	BankSize: 0
[    33.267] 	NumberOfImages: 0
[    33.267] 	RedMaskSize: 0
[    33.267] 	RedFieldPosition: 0
[    33.267] 	GreenMaskSize: 0
[    33.267] 	GreenFieldPosition: 0
[    33.267] 	BlueMaskSize: 0
[    33.267] 	BlueFieldPosition: 0
[    33.267] 	RsvdMaskSize: 0
[    33.267] 	RsvdFieldPosition: 0
[    33.267] 	DirectColorModeInfo: 0
[    33.267] 	PhysBasePtr: 0x0
[    33.267] 	LinBytesPerScanLine: 0
[    33.267] 	BnkNumberOfImagePages: 0
[    33.267] 	LinNumberOfImagePages: 0
[    33.267] 	LinRedMaskSize: 0
[    33.267] 	LinRedFieldPosition: 0
[    33.267] 	LinGreenMaskSize: 0
[    33.267] 	LinGreenFieldPosition: 0
[    33.267] 	LinBlueMaskSize: 0
[    33.267] 	LinBlueFieldPosition: 0
[    33.267] 	LinRsvdMaskSize: 0
[    33.267] 	LinRsvdFieldPosition: 0
[    33.267] 	MaxPixelClock: 0
[    33.268] Mode: 164 (0x0)
[    33.268] 	ModeAttributes: 0x0
[    33.268] 	WinAAttributes: 0x0
[    33.268] 	WinBAttributes: 0x0
[    33.268] 	WinGranularity: 0
[    33.268] 	WinSize: 0
[    33.268] 	WinASegment: 0x0
[    33.268] 	WinBSegment: 0x0
[    33.268] 	WinFuncPtr: 0x0
[    33.268] 	BytesPerScanline: 0
[    33.268] 	XResolution: 0
[    33.268] 	YResolution: 0
[    33.268] 	XCharSize: 0
[    33.268] 	YCharSize: 0
[    33.268] 	NumberOfPlanes: 0
[    33.268] 	BitsPerPixel: 0
[    33.268] 	NumberOfBanks: 0
[    33.268] 	MemoryModel: 0
[    33.268] 	BankSize: 0
[    33.268] 	NumberOfImages: 0
[    33.268] 	RedMaskSize: 0
[    33.268] 	RedFieldPosition: 0
[    33.268] 	GreenMaskSize: 0
[    33.268] 	GreenFieldPosition: 0
[    33.268] 	BlueMaskSize: 0
[    33.268] 	BlueFieldPosition: 0
[    33.268] 	RsvdMaskSize: 0
[    33.268] 	RsvdFieldPosition: 0
[    33.268] 	DirectColorModeInfo: 0
[    33.268] 	PhysBasePtr: 0x0
[    33.268] 	LinBytesPerScanLine: 0
[    33.268] 	BnkNumberOfImagePages: 0
[    33.268] 	LinNumberOfImagePages: 0
[    33.268] 	LinRedMaskSize: 0
[    33.268] 	LinRedFieldPosition: 0
[    33.268] 	LinGreenMaskSize: 0
[    33.268] 	LinGreenFieldPosition: 0
[    33.268] 	LinBlueMaskSize: 0
[    33.268] 	LinBlueFieldPosition: 0
[    33.268] 	LinRsvdMaskSize: 0
[    33.268] 	LinRsvdFieldPosition: 0
[    33.268] 	MaxPixelClock: 0
[    33.268] Mode: 165 (0x0)
[    33.268] 	ModeAttributes: 0x0
[    33.268] 	WinAAttributes: 0x0
[    33.268] 	WinBAttributes: 0x0
[    33.268] 	WinGranularity: 0
[    33.268] 	WinSize: 0
[    33.268] 	WinASegment: 0x0
[    33.268] 	WinBSegment: 0x0
[    33.268] 	WinFuncPtr: 0x0
[    33.268] 	BytesPerScanline: 0
[    33.268] 	XResolution: 0
[    33.268] 	YResolution: 0
[    33.268] 	XCharSize: 0
[    33.268] 	YCharSize: 0
[    33.268] 	NumberOfPlanes: 0
[    33.268] 	BitsPerPixel: 0
[    33.268] 	NumberOfBanks: 0
[    33.268] 	MemoryModel: 0
[    33.268] 	BankSize: 0
[    33.268] 	NumberOfImages: 0
[    33.268] 	RedMaskSize: 0
[    33.268] 	RedFieldPosition: 0
[    33.268] 	GreenMaskSize: 0
[    33.268] 	GreenFieldPosition: 0
[    33.268] 	BlueMaskSize: 0
[    33.268] 	BlueFieldPosition: 0
[    33.268] 	RsvdMaskSize: 0
[    33.268] 	RsvdFieldPosition: 0
[    33.268] 	DirectColorModeInfo: 0
[    33.268] 	PhysBasePtr: 0x0
[    33.268] 	LinBytesPerScanLine: 0
[    33.268] 	BnkNumberOfImagePages: 0
[    33.269] 	LinNumberOfImagePages: 0
[    33.269] 	LinRedMaskSize: 0
[    33.269] 	LinRedFieldPosition: 0
[    33.269] 	LinGreenMaskSize: 0
[    33.269] 	LinGreenFieldPosition: 0
[    33.269] 	LinBlueMaskSize: 0
[    33.269] 	LinBlueFieldPosition: 0
[    33.269] 	LinRsvdMaskSize: 0
[    33.269] 	LinRsvdFieldPosition: 0
[    33.269] 	MaxPixelClock: 0
[    33.269] Mode: 166 (0x0)
[    33.269] 	ModeAttributes: 0x0
[    33.269] 	WinAAttributes: 0x0
[    33.269] 	WinBAttributes: 0x0
[    33.269] 	WinGranularity: 0
[    33.269] 	WinSize: 0
[    33.269] 	WinASegment: 0x0
[    33.269] 	WinBSegment: 0x0
[    33.269] 	WinFuncPtr: 0x0
[    33.269] 	BytesPerScanline: 0
[    33.269] 	XResolution: 0
[    33.269] 	YResolution: 0
[    33.269] 	XCharSize: 0
[    33.269] 	YCharSize: 0
[    33.269] 	NumberOfPlanes: 0
[    33.269] 	BitsPerPixel: 0
[    33.269] 	NumberOfBanks: 0
[    33.269] 	MemoryModel: 0
[    33.269] 	BankSize: 0
[    33.269] 	NumberOfImages: 0
[    33.269] 	RedMaskSize: 0
[    33.269] 	RedFieldPosition: 0
[    33.269] 	GreenMaskSize: 0
[    33.269] 	GreenFieldPosition: 0
[    33.269] 	BlueMaskSize: 0
[    33.269] 	BlueFieldPosition: 0
[    33.269] 	RsvdMaskSize: 0
[    33.269] 	RsvdFieldPosition: 0
[    33.269] 	DirectColorModeInfo: 0
[    33.269] 	PhysBasePtr: 0x0
[    33.269] 	LinBytesPerScanLine: 0
[    33.269] 	BnkNumberOfImagePages: 0
[    33.269] 	LinNumberOfImagePages: 0
[    33.269] 	LinRedMaskSize: 0
[    33.269] 	LinRedFieldPosition: 0
[    33.269] 	LinGreenMaskSize: 0
[    33.269] 	LinGreenFieldPosition: 0
[    33.269] 	LinBlueMaskSize: 0
[    33.269] 	LinBlueFieldPosition: 0
[    33.269] 	LinRsvdMaskSize: 0
[    33.269] 	LinRsvdFieldPosition: 0
[    33.269] 	MaxPixelClock: 0
[    33.269] Mode: 167 (0x0)
[    33.269] 	ModeAttributes: 0x0
[    33.269] 	WinAAttributes: 0x0
[    33.269] 	WinBAttributes: 0x0
[    33.269] 	WinGranularity: 0
[    33.269] 	WinSize: 0
[    33.269] 	WinASegment: 0x0
[    33.269] 	WinBSegment: 0x0
[    33.270] 	WinFuncPtr: 0x0
[    33.270] 	BytesPerScanline: 0
[    33.270] 	XResolution: 0
[    33.270] 	YResolution: 0
[    33.270] 	XCharSize: 0
[    33.270] 	YCharSize: 0
[    33.270] 	NumberOfPlanes: 0
[    33.270] 	BitsPerPixel: 0
[    33.270] 	NumberOfBanks: 0
[    33.270] 	MemoryModel: 0
[    33.270] 	BankSize: 0
[    33.270] 	NumberOfImages: 0
[    33.270] 	RedMaskSize: 0
[    33.270] 	RedFieldPosition: 0
[    33.270] 	GreenMaskSize: 0
[    33.270] 	GreenFieldPosition: 0
[    33.270] 	BlueMaskSize: 0
[    33.270] 	BlueFieldPosition: 0
[    33.270] 	RsvdMaskSize: 0
[    33.270] 	RsvdFieldPosition: 0
[    33.270] 	DirectColorModeInfo: 0
[    33.270] 	PhysBasePtr: 0x0
[    33.270] 	LinBytesPerScanLine: 0
[    33.270] 	BnkNumberOfImagePages: 0
[    33.270] 	LinNumberOfImagePages: 0
[    33.270] 	LinRedMaskSize: 0
[    33.270] 	LinRedFieldPosition: 0
[    33.270] 	LinGreenMaskSize: 0
[    33.270] 	LinGreenFieldPosition: 0
[    33.270] 	LinBlueMaskSize: 0
[    33.270] 	LinBlueFieldPosition: 0
[    33.270] 	LinRsvdMaskSize: 0
[    33.270] 	LinRsvdFieldPosition: 0
[    33.270] 	MaxPixelClock: 0
[    33.270] Mode: 168 (0x0)
[    33.270] 	ModeAttributes: 0x0
[    33.270] 	WinAAttributes: 0x0
[    33.270] 	WinBAttributes: 0x0
[    33.270] 	WinGranularity: 0
[    33.270] 	WinSize: 0
[    33.270] 	WinASegment: 0x0
[    33.270] 	WinBSegment: 0x0
[    33.270] 	WinFuncPtr: 0x0
[    33.270] 	BytesPerScanline: 0
[    33.270] 	XResolution: 0
[    33.270] 	YResolution: 0
[    33.270] 	XCharSize: 0
[    33.270] 	YCharSize: 0
[    33.270] 	NumberOfPlanes: 0
[    33.270] 	BitsPerPixel: 0
[    33.270] 	NumberOfBanks: 0
[    33.270] 	MemoryModel: 0
[    33.270] 	BankSize: 0
[    33.270] 	NumberOfImages: 0
[    33.270] 	RedMaskSize: 0
[    33.270] 	RedFieldPosition: 0
[    33.270] 	GreenMaskSize: 0
[    33.270] 	GreenFieldPosition: 0
[    33.270] 	BlueMaskSize: 0
[    33.270] 	BlueFieldPosition: 0
[    33.270] 	RsvdMaskSize: 0
[    33.270] 	RsvdFieldPosition: 0
[    33.270] 	DirectColorModeInfo: 0
[    33.270] 	PhysBasePtr: 0x0
[    33.270] 	LinBytesPerScanLine: 0
[    33.270] 	BnkNumberOfImagePages: 0
[    33.270] 	LinNumberOfImagePages: 0
[    33.270] 	LinRedMaskSize: 0
[    33.270] 	LinRedFieldPosition: 0
[    33.270] 	LinGreenMaskSize: 0
[    33.270] 	LinGreenFieldPosition: 0
[    33.270] 	LinBlueMaskSize: 0
[    33.270] 	LinBlueFieldPosition: 0
[    33.270] 	LinRsvdMaskSize: 0
[    33.270] 	LinRsvdFieldPosition: 0
[    33.270] 	MaxPixelClock: 0
[    33.271] Mode: 169 (0x0)
[    33.271] 	ModeAttributes: 0x0
[    33.271] 	WinAAttributes: 0x0
[    33.271] 	WinBAttributes: 0x0
[    33.271] 	WinGranularity: 0
[    33.271] 	WinSize: 0
[    33.271] 	WinASegment: 0x0
[    33.271] 	WinBSegment: 0x0
[    33.271] 	WinFuncPtr: 0x0
[    33.271] 	BytesPerScanline: 0
[    33.271] 	XResolution: 0
[    33.271] 	YResolution: 0
[    33.271] 	XCharSize: 0
[    33.271] 	YCharSize: 0
[    33.271] 	NumberOfPlanes: 0
[    33.271] 	BitsPerPixel: 0
[    33.271] 	NumberOfBanks: 0
[    33.271] 	MemoryModel: 0
[    33.271] 	BankSize: 0
[    33.271] 	NumberOfImages: 0
[    33.271] 	RedMaskSize: 0
[    33.271] 	RedFieldPosition: 0
[    33.271] 	GreenMaskSize: 0
[    33.271] 	GreenFieldPosition: 0
[    33.271] 	BlueMaskSize: 0
[    33.271] 	BlueFieldPosition: 0
[    33.271] 	RsvdMaskSize: 0
[    33.271] 	RsvdFieldPosition: 0
[    33.271] 	DirectColorModeInfo: 0
[    33.271] 	PhysBasePtr: 0x0
[    33.271] 	LinBytesPerScanLine: 0
[    33.271] 	BnkNumberOfImagePages: 0
[    33.271] 	LinNumberOfImagePages: 0
[    33.271] 	LinRedMaskSize: 0
[    33.271] 	LinRedFieldPosition: 0
[    33.271] 	LinGreenMaskSize: 0
[    33.271] 	LinGreenFieldPosition: 0
[    33.271] 	LinBlueMaskSize: 0
[    33.271] 	LinBlueFieldPosition: 0
[    33.271] 	LinRsvdMaskSize: 0
[    33.271] 	LinRsvdFieldPosition: 0
[    33.271] 	MaxPixelClock: 0
[    33.271] Mode: 16a (0x0)
[    33.271] 	ModeAttributes: 0x0
[    33.271] 	WinAAttributes: 0x0
[    33.271] 	WinBAttributes: 0x0
[    33.271] 	WinGranularity: 0
[    33.271] 	WinSize: 0
[    33.271] 	WinASegment: 0x0
[    33.271] 	WinBSegment: 0x0
[    33.271] 	WinFuncPtr: 0x0
[    33.271] 	BytesPerScanline: 0
[    33.271] 	XResolution: 0
[    33.271] 	YResolution: 0
[    33.271] 	XCharSize: 0
[    33.271] 	YCharSize: 0
[    33.271] 	NumberOfPlanes: 0
[    33.271] 	BitsPerPixel: 0
[    33.271] 	NumberOfBanks: 0
[    33.271] 	MemoryModel: 0
[    33.271] 	BankSize: 0
[    33.271] 	NumberOfImages: 0
[    33.271] 	RedMaskSize: 0
[    33.271] 	RedFieldPosition: 0
[    33.271] 	GreenMaskSize: 0
[    33.271] 	GreenFieldPosition: 0
[    33.271] 	BlueMaskSize: 0
[    33.271] 	BlueFieldPosition: 0
[    33.271] 	RsvdMaskSize: 0
[    33.272] 	RsvdFieldPosition: 0
[    33.272] 	DirectColorModeInfo: 0
[    33.272] 	PhysBasePtr: 0x0
[    33.272] 	LinBytesPerScanLine: 0
[    33.272] 	BnkNumberOfImagePages: 0
[    33.272] 	LinNumberOfImagePages: 0
[    33.272] 	LinRedMaskSize: 0
[    33.272] 	LinRedFieldPosition: 0
[    33.272] 	LinGreenMaskSize: 0
[    33.272] 	LinGreenFieldPosition: 0
[    33.272] 	LinBlueMaskSize: 0
[    33.272] 	LinBlueFieldPosition: 0
[    33.272] 	LinRsvdMaskSize: 0
[    33.272] 	LinRsvdFieldPosition: 0
[    33.272] 	MaxPixelClock: 0
[    33.272] Mode: 16b (0x0)
[    33.272] 	ModeAttributes: 0x0
[    33.272] 	WinAAttributes: 0x0
[    33.272] 	WinBAttributes: 0x0
[    33.272] 	WinGranularity: 0
[    33.272] 	WinSize: 0
[    33.272] 	WinASegment: 0x0
[    33.272] 	WinBSegment: 0x0
[    33.272] 	WinFuncPtr: 0x0
[    33.272] 	BytesPerScanline: 0
[    33.272] 	XResolution: 0
[    33.272] 	YResolution: 0
[    33.272] 	XCharSize: 0
[    33.272] 	YCharSize: 0
[    33.272] 	NumberOfPlanes: 0
[    33.272] 	BitsPerPixel: 0
[    33.272] 	NumberOfBanks: 0
[    33.272] 	MemoryModel: 0
[    33.272] 	BankSize: 0
[    33.272] 	NumberOfImages: 0
[    33.272] 	RedMaskSize: 0
[    33.272] 	RedFieldPosition: 0
[    33.272] 	GreenMaskSize: 0
[    33.272] 	GreenFieldPosition: 0
[    33.272] 	BlueMaskSize: 0
[    33.272] 	BlueFieldPosition: 0
[    33.272] 	RsvdMaskSize: 0
[    33.272] 	RsvdFieldPosition: 0
[    33.272] 	DirectColorModeInfo: 0
[    33.272] 	PhysBasePtr: 0x0
[    33.272] 	LinBytesPerScanLine: 0
[    33.272] 	BnkNumberOfImagePages: 0
[    33.272] 	LinNumberOfImagePages: 0
[    33.272] 	LinRedMaskSize: 0
[    33.272] 	LinRedFieldPosition: 0
[    33.272] 	LinGreenMaskSize: 0
[    33.272] 	LinGreenFieldPosition: 0
[    33.272] 	LinBlueMaskSize: 0
[    33.272] 	LinBlueFieldPosition: 0
[    33.272] 	LinRsvdMaskSize: 0
[    33.272] 	LinRsvdFieldPosition: 0
[    33.272] 	MaxPixelClock: 0
[    33.272] Mode: 16c (0x0)
[    33.273] 	ModeAttributes: 0x0
[    33.273] 	WinAAttributes: 0x0
[    33.273] 	WinBAttributes: 0x0
[    33.273] 	WinGranularity: 0
[    33.273] 	WinSize: 0
[    33.273] 	WinASegment: 0x0
[    33.273] 	WinBSegment: 0x0
[    33.273] 	WinFuncPtr: 0x0
[    33.273] 	BytesPerScanline: 0
[    33.273] 	XResolution: 0
[    33.273] 	YResolution: 0
[    33.273] 	XCharSize: 0
[    33.273] 	YCharSize: 0
[    33.273] 	NumberOfPlanes: 0
[    33.273] 	BitsPerPixel: 0
[    33.273] 	NumberOfBanks: 0
[    33.273] 	MemoryModel: 0
[    33.273] 	BankSize: 0
[    33.273] 	NumberOfImages: 0
[    33.273] 	RedMaskSize: 0
[    33.273] 	RedFieldPosition: 0
[    33.273] 	GreenMaskSize: 0
[    33.273] 	GreenFieldPosition: 0
[    33.273] 	BlueMaskSize: 0
[    33.273] 	BlueFieldPosition: 0
[    33.273] 	RsvdMaskSize: 0
[    33.273] 	RsvdFieldPosition: 0
[    33.273] 	DirectColorModeInfo: 0
[    33.273] 	PhysBasePtr: 0x0
[    33.273] 	LinBytesPerScanLine: 0
[    33.273] 	BnkNumberOfImagePages: 0
[    33.273] 	LinNumberOfImagePages: 0
[    33.273] 	LinRedMaskSize: 0
[    33.273] 	LinRedFieldPosition: 0
[    33.273] 	LinGreenMaskSize: 0
[    33.273] 	LinGreenFieldPosition: 0
[    33.273] 	LinBlueMaskSize: 0
[    33.273] 	LinBlueFieldPosition: 0
[    33.273] 	LinRsvdMaskSize: 0
[    33.273] 	LinRsvdFieldPosition: 0
[    33.273] 	MaxPixelClock: 0
[    33.273] Mode: 16d (0x0)
[    33.273] 	ModeAttributes: 0x0
[    33.273] 	WinAAttributes: 0x0
[    33.273] 	WinBAttributes: 0x0
[    33.273] 	WinGranularity: 0
[    33.273] 	WinSize: 0
[    33.273] 	WinASegment: 0x0
[    33.273] 	WinBSegment: 0x0
[    33.273] 	WinFuncPtr: 0x0
[    33.273] 	BytesPerScanline: 0
[    33.273] 	XResolution: 0
[    33.273] 	YResolution: 0
[    33.273] 	XCharSize: 0
[    33.273] 	YCharSize: 0
[    33.273] 	NumberOfPlanes: 0
[    33.273] 	BitsPerPixel: 0
[    33.273] 	NumberOfBanks: 0
[    33.273] 	MemoryModel: 0
[    33.273] 	BankSize: 0
[    33.273] 	NumberOfImages: 0
[    33.273] 	RedMaskSize: 0
[    33.273] 	RedFieldPosition: 0
[    33.273] 	GreenMaskSize: 0
[    33.273] 	GreenFieldPosition: 0
[    33.273] 	BlueMaskSize: 0
[    33.273] 	BlueFieldPosition: 0
[    33.273] 	RsvdMaskSize: 0
[    33.273] 	RsvdFieldPosition: 0
[    33.273] 	DirectColorModeInfo: 0
[    33.273] 	PhysBasePtr: 0x0
[    33.273] 	LinBytesPerScanLine: 0
[    33.273] 	BnkNumberOfImagePages: 0
[    33.273] 	LinNumberOfImagePages: 0
[    33.273] 	LinRedMaskSize: 0
[    33.273] 	LinRedFieldPosition: 0
[    33.273] 	LinGreenMaskSize: 0
[    33.273] 	LinGreenFieldPosition: 0
[    33.273] 	LinBlueMaskSize: 0
[    33.273] 	LinBlueFieldPosition: 0
[    33.273] 	LinRsvdMaskSize: 0
[    33.273] 	LinRsvdFieldPosition: 0
[    33.273] 	MaxPixelClock: 0
[    33.274] Mode: 16e (0x0)
[    33.274] 	ModeAttributes: 0x0
[    33.274] 	WinAAttributes: 0x0
[    33.274] 	WinBAttributes: 0x0
[    33.274] 	WinGranularity: 0
[    33.274] 	WinSize: 0
[    33.274] 	WinASegment: 0x0
[    33.274] 	WinBSegment: 0x0
[    33.274] 	WinFuncPtr: 0x0
[    33.274] 	BytesPerScanline: 0
[    33.274] 	XResolution: 0
[    33.274] 	YResolution: 0
[    33.274] 	XCharSize: 0
[    33.274] 	YCharSize: 0
[    33.274] 	NumberOfPlanes: 0
[    33.274] 	BitsPerPixel: 0
[    33.274] 	NumberOfBanks: 0
[    33.274] 	MemoryModel: 0
[    33.274] 	BankSize: 0
[    33.274] 	NumberOfImages: 0
[    33.274] 	RedMaskSize: 0
[    33.274] 	RedFieldPosition: 0
[    33.274] 	GreenMaskSize: 0
[    33.274] 	GreenFieldPosition: 0
[    33.274] 	BlueMaskSize: 0
[    33.274] 	BlueFieldPosition: 0
[    33.274] 	RsvdMaskSize: 0
[    33.274] 	RsvdFieldPosition: 0
[    33.274] 	DirectColorModeInfo: 0
[    33.274] 	PhysBasePtr: 0x0
[    33.274] 	LinBytesPerScanLine: 0
[    33.274] 	BnkNumberOfImagePages: 0
[    33.274] 	LinNumberOfImagePages: 0
[    33.274] 	LinRedMaskSize: 0
[    33.274] 	LinRedFieldPosition: 0
[    33.274] 	LinGreenMaskSize: 0
[    33.274] 	LinGreenFieldPosition: 0
[    33.274] 	LinBlueMaskSize: 0
[    33.274] 	LinBlueFieldPosition: 0
[    33.274] 	LinRsvdMaskSize: 0
[    33.274] 	LinRsvdFieldPosition: 0
[    33.274] 	MaxPixelClock: 0
[    33.274] Mode: 16f (0x0)
[    33.274] 	ModeAttributes: 0x0
[    33.274] 	WinAAttributes: 0x0
[    33.274] 	WinBAttributes: 0x0
[    33.274] 	WinGranularity: 0
[    33.274] 	WinSize: 0
[    33.274] 	WinASegment: 0x0
[    33.274] 	WinBSegment: 0x0
[    33.274] 	WinFuncPtr: 0x0
[    33.274] 	BytesPerScanline: 0
[    33.274] 	XResolution: 0
[    33.274] 	YResolution: 0
[    33.274] 	XCharSize: 0
[    33.274] 	YCharSize: 0
[    33.274] 	NumberOfPlanes: 0
[    33.274] 	BitsPerPixel: 0
[    33.274] 	NumberOfBanks: 0
[    33.274] 	MemoryModel: 0
[    33.274] 	BankSize: 0
[    33.274] 	NumberOfImages: 0
[    33.274] 	RedMaskSize: 0
[    33.274] 	RedFieldPosition: 0
[    33.274] 	GreenMaskSize: 0
[    33.275] 	GreenFieldPosition: 0
[    33.275] 	BlueMaskSize: 0
[    33.275] 	BlueFieldPosition: 0
[    33.275] 	RsvdMaskSize: 0
[    33.275] 	RsvdFieldPosition: 0
[    33.275] 	DirectColorModeInfo: 0
[    33.275] 	PhysBasePtr: 0x0
[    33.275] 	LinBytesPerScanLine: 0
[    33.275] 	BnkNumberOfImagePages: 0
[    33.275] 	LinNumberOfImagePages: 0
[    33.275] 	LinRedMaskSize: 0
[    33.275] 	LinRedFieldPosition: 0
[    33.275] 	LinGreenMaskSize: 0
[    33.275] 	LinGreenFieldPosition: 0
[    33.275] 	LinBlueMaskSize: 0
[    33.275] 	LinBlueFieldPosition: 0
[    33.275] 	LinRsvdMaskSize: 0
[    33.275] 	LinRsvdFieldPosition: 0
[    33.275] 	MaxPixelClock: 0
[    33.275] Mode: 170 (0x0)
[    33.275] 	ModeAttributes: 0x0
[    33.275] 	WinAAttributes: 0x0
[    33.275] 	WinBAttributes: 0x0
[    33.275] 	WinGranularity: 0
[    33.275] 	WinSize: 0
[    33.275] 	WinASegment: 0x0
[    33.275] 	WinBSegment: 0x0
[    33.275] 	WinFuncPtr: 0x0
[    33.275] 	BytesPerScanline: 0
[    33.275] 	XResolution: 0
[    33.275] 	YResolution: 0
[    33.275] 	XCharSize: 0
[    33.275] 	YCharSize: 0
[    33.275] 	NumberOfPlanes: 0
[    33.275] 	BitsPerPixel: 0
[    33.275] 	NumberOfBanks: 0
[    33.275] 	MemoryModel: 0
[    33.275] 	BankSize: 0
[    33.275] 	NumberOfImages: 0
[    33.275] 	RedMaskSize: 0
[    33.275] 	RedFieldPosition: 0
[    33.275] 	GreenMaskSize: 0
[    33.275] 	GreenFieldPosition: 0
[    33.275] 	BlueMaskSize: 0
[    33.275] 	BlueFieldPosition: 0
[    33.275] 	RsvdMaskSize: 0
[    33.275] 	RsvdFieldPosition: 0
[    33.275] 	DirectColorModeInfo: 0
[    33.275] 	PhysBasePtr: 0x0
[    33.275] 	LinBytesPerScanLine: 0
[    33.275] 	BnkNumberOfImagePages: 0
[    33.275] 	LinNumberOfImagePages: 0
[    33.275] 	LinRedMaskSize: 0
[    33.275] 	LinRedFieldPosition: 0
[    33.275] 	LinGreenMaskSize: 0
[    33.275] 	LinGreenFieldPosition: 0
[    33.275] 	LinBlueMaskSize: 0
[    33.275] 	LinBlueFieldPosition: 0
[    33.275] 	LinRsvdMaskSize: 0
[    33.275] 	LinRsvdFieldPosition: 0
[    33.275] 	MaxPixelClock: 0
[    33.275] Mode: 171 (0x0)
[    33.275] 	ModeAttributes: 0x0
[    33.275] 	WinAAttributes: 0x0
[    33.275] 	WinBAttributes: 0x0
[    33.276] 	WinGranularity: 0
[    33.276] 	WinSize: 0
[    33.276] 	WinASegment: 0x0
[    33.276] 	WinBSegment: 0x0
[    33.276] 	WinFuncPtr: 0x0
[    33.276] 	BytesPerScanline: 0
[    33.276] 	XResolution: 0
[    33.276] 	YResolution: 0
[    33.276] 	XCharSize: 0
[    33.276] 	YCharSize: 0
[    33.276] 	NumberOfPlanes: 0
[    33.276] 	BitsPerPixel: 0
[    33.276] 	NumberOfBanks: 0
[    33.276] 	MemoryModel: 0
[    33.276] 	BankSize: 0
[    33.276] 	NumberOfImages: 0
[    33.276] 	RedMaskSize: 0
[    33.276] 	RedFieldPosition: 0
[    33.276] 	GreenMaskSize: 0
[    33.276] 	GreenFieldPosition: 0
[    33.276] 	BlueMaskSize: 0
[    33.276] 	BlueFieldPosition: 0
[    33.276] 	RsvdMaskSize: 0
[    33.276] 	RsvdFieldPosition: 0
[    33.276] 	DirectColorModeInfo: 0
[    33.276] 	PhysBasePtr: 0x0
[    33.276] 	LinBytesPerScanLine: 0
[    33.276] 	BnkNumberOfImagePages: 0
[    33.276] 	LinNumberOfImagePages: 0
[    33.276] 	LinRedMaskSize: 0
[    33.276] 	LinRedFieldPosition: 0
[    33.276] 	LinGreenMaskSize: 0
[    33.276] 	LinGreenFieldPosition: 0
[    33.276] 	LinBlueMaskSize: 0
[    33.276] 	LinBlueFieldPosition: 0
[    33.276] 	LinRsvdMaskSize: 0
[    33.276] 	LinRsvdFieldPosition: 0
[    33.276] 	MaxPixelClock: 0
[    33.276] Mode: 13c (0x0)
[    33.276] 	ModeAttributes: 0x0
[    33.276] 	WinAAttributes: 0x0
[    33.276] 	WinBAttributes: 0x0
[    33.276] 	WinGranularity: 0
[    33.276] 	WinSize: 0
[    33.276] 	WinASegment: 0x0
[    33.276] 	WinBSegment: 0x0
[    33.276] 	WinFuncPtr: 0x0
[    33.276] 	BytesPerScanline: 0
[    33.276] 	XResolution: 0
[    33.276] 	YResolution: 0
[    33.276] 	XCharSize: 0
[    33.276] 	YCharSize: 0
[    33.276] 	NumberOfPlanes: 0
[    33.276] 	BitsPerPixel: 0
[    33.276] 	NumberOfBanks: 0
[    33.276] 	MemoryModel: 0
[    33.276] 	BankSize: 0
[    33.276] 	NumberOfImages: 0
[    33.276] 	RedMaskSize: 0
[    33.276] 	RedFieldPosition: 0
[    33.276] 	GreenMaskSize: 0
[    33.276] 	GreenFieldPosition: 0
[    33.276] 	BlueMaskSize: 0
[    33.276] 	BlueFieldPosition: 0
[    33.276] 	RsvdMaskSize: 0
[    33.276] 	RsvdFieldPosition: 0
[    33.276] 	DirectColorModeInfo: 0
[    33.277] 	PhysBasePtr: 0x0
[    33.277] 	LinBytesPerScanLine: 0
[    33.277] 	BnkNumberOfImagePages: 0
[    33.277] 	LinNumberOfImagePages: 0
[    33.277] 	LinRedMaskSize: 0
[    33.277] 	LinRedFieldPosition: 0
[    33.277] 	LinGreenMaskSize: 0
[    33.277] 	LinGreenFieldPosition: 0
[    33.277] 	LinBlueMaskSize: 0
[    33.277] 	LinBlueFieldPosition: 0
[    33.277] 	LinRsvdMaskSize: 0
[    33.277] 	LinRsvdFieldPosition: 0
[    33.277] 	MaxPixelClock: 0
[    33.277] Mode: 14d (0x0)
[    33.277] 	ModeAttributes: 0x0
[    33.277] 	WinAAttributes: 0x0
[    33.277] 	WinBAttributes: 0x0
[    33.277] 	WinGranularity: 0
[    33.277] 	WinSize: 0
[    33.277] 	WinASegment: 0x0
[    33.277] 	WinBSegment: 0x0
[    33.277] 	WinFuncPtr: 0x0
[    33.277] 	BytesPerScanline: 0
[    33.277] 	XResolution: 0
[    33.277] 	YResolution: 0
[    33.277] 	XCharSize: 0
[    33.277] 	YCharSize: 0
[    33.277] 	NumberOfPlanes: 0
[    33.277] 	BitsPerPixel: 0
[    33.277] 	NumberOfBanks: 0
[    33.277] 	MemoryModel: 0
[    33.277] 	BankSize: 0
[    33.277] 	NumberOfImages: 0
[    33.277] 	RedMaskSize: 0
[    33.277] 	RedFieldPosition: 0
[    33.277] 	GreenMaskSize: 0
[    33.277] 	GreenFieldPosition: 0
[    33.277] 	BlueMaskSize: 0
[    33.277] 	BlueFieldPosition: 0
[    33.277] 	RsvdMaskSize: 0
[    33.277] 	RsvdFieldPosition: 0
[    33.277] 	DirectColorModeInfo: 0
[    33.277] 	PhysBasePtr: 0x0
[    33.277] 	LinBytesPerScanLine: 0
[    33.277] 	BnkNumberOfImagePages: 0
[    33.277] 	LinNumberOfImagePages: 0
[    33.277] 	LinRedMaskSize: 0
[    33.277] 	LinRedFieldPosition: 0
[    33.277] 	LinGreenMaskSize: 0
[    33.277] 	LinGreenFieldPosition: 0
[    33.277] 	LinBlueMaskSize: 0
[    33.277] 	LinBlueFieldPosition: 0
[    33.277] 	LinRsvdMaskSize: 0
[    33.277] 	LinRsvdFieldPosition: 0
[    33.277] 	MaxPixelClock: 0
[    33.278] Mode: 15c (0x0)
[    33.278] 	ModeAttributes: 0x0
[    33.278] 	WinAAttributes: 0x0
[    33.278] 	WinBAttributes: 0x0
[    33.278] 	WinGranularity: 0
[    33.278] 	WinSize: 0
[    33.278] 	WinASegment: 0x0
[    33.278] 	WinBSegment: 0x0
[    33.278] 	WinFuncPtr: 0x0
[    33.278] 	BytesPerScanline: 0
[    33.278] 	XResolution: 0
[    33.278] 	YResolution: 0
[    33.278] 	XCharSize: 0
[    33.278] 	YCharSize: 0
[    33.278] 	NumberOfPlanes: 0
[    33.278] 	BitsPerPixel: 0
[    33.278] 	NumberOfBanks: 0
[    33.278] 	MemoryModel: 0
[    33.278] 	BankSize: 0
[    33.278] 	NumberOfImages: 0
[    33.278] 	RedMaskSize: 0
[    33.278] 	RedFieldPosition: 0
[    33.278] 	GreenMaskSize: 0
[    33.278] 	GreenFieldPosition: 0
[    33.278] 	BlueMaskSize: 0
[    33.278] 	BlueFieldPosition: 0
[    33.278] 	RsvdMaskSize: 0
[    33.278] 	RsvdFieldPosition: 0
[    33.278] 	DirectColorModeInfo: 0
[    33.278] 	PhysBasePtr: 0x0
[    33.278] 	LinBytesPerScanLine: 0
[    33.278] 	BnkNumberOfImagePages: 0
[    33.278] 	LinNumberOfImagePages: 0
[    33.278] 	LinRedMaskSize: 0
[    33.278] 	LinRedFieldPosition: 0
[    33.278] 	LinGreenMaskSize: 0
[    33.278] 	LinGreenFieldPosition: 0
[    33.278] 	LinBlueMaskSize: 0
[    33.278] 	LinBlueFieldPosition: 0
[    33.278] 	LinRsvdMaskSize: 0
[    33.278] 	LinRsvdFieldPosition: 0
[    33.278] 	MaxPixelClock: 0
[    33.278] Mode: 13a (0x0)
[    33.278] 	ModeAttributes: 0x0
[    33.278] 	WinAAttributes: 0x0
[    33.278] 	WinBAttributes: 0x0
[    33.278] 	WinGranularity: 0
[    33.278] 	WinSize: 0
[    33.278] 	WinASegment: 0x0
[    33.278] 	WinBSegment: 0x0
[    33.278] 	WinFuncPtr: 0x0
[    33.278] 	BytesPerScanline: 0
[    33.278] 	XResolution: 0
[    33.278] 	YResolution: 0
[    33.279] 	XCharSize: 0
[    33.279] 	YCharSize: 0
[    33.279] 	NumberOfPlanes: 0
[    33.279] 	BitsPerPixel: 0
[    33.279] 	NumberOfBanks: 0
[    33.279] 	MemoryModel: 0
[    33.279] 	BankSize: 0
[    33.279] 	NumberOfImages: 0
[    33.279] 	RedMaskSize: 0
[    33.279] 	RedFieldPosition: 0
[    33.279] 	GreenMaskSize: 0
[    33.279] 	GreenFieldPosition: 0
[    33.279] 	BlueMaskSize: 0
[    33.279] 	BlueFieldPosition: 0
[    33.279] 	RsvdMaskSize: 0
[    33.279] 	RsvdFieldPosition: 0
[    33.279] 	DirectColorModeInfo: 0
[    33.279] 	PhysBasePtr: 0x0
[    33.279] 	LinBytesPerScanLine: 0
[    33.279] 	BnkNumberOfImagePages: 0
[    33.279] 	LinNumberOfImagePages: 0
[    33.279] 	LinRedMaskSize: 0
[    33.279] 	LinRedFieldPosition: 0
[    33.279] 	LinGreenMaskSize: 0
[    33.279] 	LinGreenFieldPosition: 0
[    33.279] 	LinBlueMaskSize: 0
[    33.279] 	LinBlueFieldPosition: 0
[    33.279] 	LinRsvdMaskSize: 0
[    33.279] 	LinRsvdFieldPosition: 0
[    33.279] 	MaxPixelClock: 0
[    33.279] Mode: 14b (0x0)
[    33.279] 	ModeAttributes: 0x0
[    33.279] 	WinAAttributes: 0x0
[    33.279] 	WinBAttributes: 0x0
[    33.279] 	WinGranularity: 0
[    33.279] 	WinSize: 0
[    33.279] 	WinASegment: 0x0
[    33.279] 	WinBSegment: 0x0
[    33.279] 	WinFuncPtr: 0x0
[    33.279] 	BytesPerScanline: 0
[    33.279] 	XResolution: 0
[    33.279] 	YResolution: 0
[    33.279] 	XCharSize: 0
[    33.279] 	YCharSize: 0
[    33.279] 	NumberOfPlanes: 0
[    33.279] 	BitsPerPixel: 0
[    33.279] 	NumberOfBanks: 0
[    33.279] 	MemoryModel: 0
[    33.279] 	BankSize: 0
[    33.279] 	NumberOfImages: 0
[    33.279] 	RedMaskSize: 0
[    33.279] 	RedFieldPosition: 0
[    33.279] 	GreenMaskSize: 0
[    33.279] 	GreenFieldPosition: 0
[    33.279] 	BlueMaskSize: 0
[    33.279] 	BlueFieldPosition: 0
[    33.279] 	RsvdMaskSize: 0
[    33.279] 	RsvdFieldPosition: 0
[    33.279] 	DirectColorModeInfo: 0
[    33.279] 	PhysBasePtr: 0x0
[    33.279] 	LinBytesPerScanLine: 0
[    33.279] 	BnkNumberOfImagePages: 0
[    33.279] 	LinNumberOfImagePages: 0
[    33.279] 	LinRedMaskSize: 0
[    33.279] 	LinRedFieldPosition: 0
[    33.279] 	LinGreenMaskSize: 0
[    33.279] 	LinGreenFieldPosition: 0
[    33.279] 	LinBlueMaskSize: 0
[    33.279] 	LinBlueFieldPosition: 0
[    33.279] 	LinRsvdMaskSize: 0
[    33.279] 	LinRsvdFieldPosition: 0
[    33.279] 	MaxPixelClock: 0
[    33.280] Mode: 15a (0x0)
[    33.280] 	ModeAttributes: 0x0
[    33.280] 	WinAAttributes: 0x0
[    33.280] 	WinBAttributes: 0x0
[    33.280] 	WinGranularity: 0
[    33.280] 	WinSize: 0
[    33.280] 	WinASegment: 0x0
[    33.280] 	WinBSegment: 0x0
[    33.280] 	WinFuncPtr: 0x0
[    33.280] 	BytesPerScanline: 0
[    33.280] 	XResolution: 0
[    33.280] 	YResolution: 0
[    33.280] 	XCharSize: 0
[    33.280] 	YCharSize: 0
[    33.280] 	NumberOfPlanes: 0
[    33.280] 	BitsPerPixel: 0
[    33.280] 	NumberOfBanks: 0
[    33.280] 	MemoryModel: 0
[    33.280] 	BankSize: 0
[    33.280] 	NumberOfImages: 0
[    33.280] 	RedMaskSize: 0
[    33.280] 	RedFieldPosition: 0
[    33.280] 	GreenMaskSize: 0
[    33.280] 	GreenFieldPosition: 0
[    33.280] 	BlueMaskSize: 0
[    33.280] 	BlueFieldPosition: 0
[    33.280] 	RsvdMaskSize: 0
[    33.280] 	RsvdFieldPosition: 0
[    33.280] 	DirectColorModeInfo: 0
[    33.280] 	PhysBasePtr: 0x0
[    33.280] 	LinBytesPerScanLine: 0
[    33.280] 	BnkNumberOfImagePages: 0
[    33.280] 	LinNumberOfImagePages: 0
[    33.280] 	LinRedMaskSize: 0
[    33.280] 	LinRedFieldPosition: 0
[    33.280] 	LinGreenMaskSize: 0
[    33.280] 	LinGreenFieldPosition: 0
[    33.280] 	LinBlueMaskSize: 0
[    33.280] 	LinBlueFieldPosition: 0
[    33.280] 	LinRsvdMaskSize: 0
[    33.280] 	LinRsvdFieldPosition: 0
[    33.280] 	MaxPixelClock: 0
[    33.281] Mode: 107 (0x0)
[    33.281] 	ModeAttributes: 0x0
[    33.281] 	WinAAttributes: 0x0
[    33.281] 	WinBAttributes: 0x0
[    33.281] 	WinGranularity: 0
[    33.281] 	WinSize: 0
[    33.281] 	WinASegment: 0x0
[    33.281] 	WinBSegment: 0x0
[    33.281] 	WinFuncPtr: 0x0
[    33.281] 	BytesPerScanline: 0
[    33.281] 	XResolution: 0
[    33.281] 	YResolution: 0
[    33.281] 	XCharSize: 0
[    33.281] 	YCharSize: 0
[    33.281] 	NumberOfPlanes: 0
[    33.281] 	BitsPerPixel: 0
[    33.281] 	NumberOfBanks: 0
[    33.281] 	MemoryModel: 0
[    33.281] 	BankSize: 0
[    33.281] 	NumberOfImages: 0
[    33.281] 	RedMaskSize: 0
[    33.281] 	RedFieldPosition: 0
[    33.281] 	GreenMaskSize: 0
[    33.281] 	GreenFieldPosition: 0
[    33.281] 	BlueMaskSize: 0
[    33.281] 	BlueFieldPosition: 0
[    33.281] 	RsvdMaskSize: 0
[    33.281] 	RsvdFieldPosition: 0
[    33.281] 	DirectColorModeInfo: 0
[    33.281] 	PhysBasePtr: 0x0
[    33.281] 	LinBytesPerScanLine: 0
[    33.281] 	BnkNumberOfImagePages: 0
[    33.281] 	LinNumberOfImagePages: 0
[    33.281] 	LinRedMaskSize: 0
[    33.281] 	LinRedFieldPosition: 0
[    33.281] 	LinGreenMaskSize: 0
[    33.281] 	LinGreenFieldPosition: 0
[    33.281] 	LinBlueMaskSize: 0
[    33.281] 	LinBlueFieldPosition: 0
[    33.281] 	LinRsvdMaskSize: 0
[    33.281] 	LinRsvdFieldPosition: 0
[    33.281] 	MaxPixelClock: 0
[    33.281] Mode: 11a (0x0)
[    33.281] 	ModeAttributes: 0x0
[    33.281] 	WinAAttributes: 0x0
[    33.281] 	WinBAttributes: 0x0
[    33.281] 	WinGranularity: 0
[    33.281] 	WinSize: 0
[    33.281] 	WinASegment: 0x0
[    33.281] 	WinBSegment: 0x0
[    33.281] 	WinFuncPtr: 0x0
[    33.281] 	BytesPerScanline: 0
[    33.281] 	XResolution: 0
[    33.281] 	YResolution: 0
[    33.281] 	XCharSize: 0
[    33.281] 	YCharSize: 0
[    33.281] 	NumberOfPlanes: 0
[    33.281] 	BitsPerPixel: 0
[    33.281] 	NumberOfBanks: 0
[    33.281] 	MemoryModel: 0
[    33.282] 	BankSize: 0
[    33.282] 	NumberOfImages: 0
[    33.282] 	RedMaskSize: 0
[    33.282] 	RedFieldPosition: 0
[    33.282] 	GreenMaskSize: 0
[    33.282] 	GreenFieldPosition: 0
[    33.282] 	BlueMaskSize: 0
[    33.282] 	BlueFieldPosition: 0
[    33.282] 	RsvdMaskSize: 0
[    33.282] 	RsvdFieldPosition: 0
[    33.282] 	DirectColorModeInfo: 0
[    33.282] 	PhysBasePtr: 0x0
[    33.282] 	LinBytesPerScanLine: 0
[    33.282] 	BnkNumberOfImagePages: 0
[    33.282] 	LinNumberOfImagePages: 0
[    33.282] 	LinRedMaskSize: 0
[    33.282] 	LinRedFieldPosition: 0
[    33.282] 	LinGreenMaskSize: 0
[    33.282] 	LinGreenFieldPosition: 0
[    33.282] 	LinBlueMaskSize: 0
[    33.282] 	LinBlueFieldPosition: 0
[    33.282] 	LinRsvdMaskSize: 0
[    33.282] 	LinRsvdFieldPosition: 0
[    33.282] 	MaxPixelClock: 0
[    33.282] Mode: 11b (0x0)
[    33.282] 	ModeAttributes: 0x0
[    33.282] 	WinAAttributes: 0x0
[    33.282] 	WinBAttributes: 0x0
[    33.282] 	WinGranularity: 0
[    33.282] 	WinSize: 0
[    33.282] 	WinASegment: 0x0
[    33.282] 	WinBSegment: 0x0
[    33.282] 	WinFuncPtr: 0x0
[    33.282] 	BytesPerScanline: 0
[    33.282] 	XResolution: 0
[    33.282] 	YResolution: 0
[    33.282] 	XCharSize: 0
[    33.282] 	YCharSize: 0
[    33.282] 	NumberOfPlanes: 0
[    33.282] 	BitsPerPixel: 0
[    33.282] 	NumberOfBanks: 0
[    33.282] 	MemoryModel: 0
[    33.282] 	BankSize: 0
[    33.282] 	NumberOfImages: 0
[    33.282] 	RedMaskSize: 0
[    33.282] 	RedFieldPosition: 0
[    33.282] 	GreenMaskSize: 0
[    33.282] 	GreenFieldPosition: 0
[    33.282] 	BlueMaskSize: 0
[    33.282] 	BlueFieldPosition: 0
[    33.282] 	RsvdMaskSize: 0
[    33.282] 	RsvdFieldPosition: 0
[    33.282] 	DirectColorModeInfo: 0
[    33.282] 	PhysBasePtr: 0x0
[    33.282] 	LinBytesPerScanLine: 0
[    33.282] 	BnkNumberOfImagePages: 0
[    33.282] 	LinNumberOfImagePages: 0
[    33.282] 	LinRedMaskSize: 0
[    33.282] 	LinRedFieldPosition: 0
[    33.282] 	LinGreenMaskSize: 0
[    33.282] 	LinGreenFieldPosition: 0
[    33.282] 	LinBlueMaskSize: 0
[    33.282] 	LinBlueFieldPosition: 0
[    33.282] 	LinRsvdMaskSize: 0
[    33.282] 	LinRsvdFieldPosition: 0
[    33.282] 	MaxPixelClock: 0
[    33.283] Mode: 105 (1024x768)
[    33.283] 	ModeAttributes: 0x9b
[    33.283] 	WinAAttributes: 0x7
[    33.283] 	WinBAttributes: 0x0
[    33.283] 	WinGranularity: 64
[    33.283] 	WinSize: 64
[    33.283] 	WinASegment: 0xa000
[    33.283] 	WinBSegment: 0x0
[    33.283] 	WinFuncPtr: 0xc0007b7a
[    33.283] 	BytesPerScanline: 1024
[    33.283] 	XResolution: 1024
[    33.283] 	YResolution: 768
[    33.283] 	XCharSize: 8
[    33.283] 	YCharSize: 16
[    33.283] 	NumberOfPlanes: 1
[    33.283] 	BitsPerPixel: 8
[    33.283] 	NumberOfBanks: 1
[    33.283] 	MemoryModel: 4
[    33.283] 	BankSize: 0
[    33.283] 	NumberOfImages: 8
[    33.283] 	RedMaskSize: 0
[    33.283] 	RedFieldPosition: 0
[    33.283] 	GreenMaskSize: 0
[    33.283] 	GreenFieldPosition: 0
[    33.283] 	BlueMaskSize: 0
[    33.283] 	BlueFieldPosition: 0
[    33.283] 	RsvdMaskSize: 0
[    33.283] 	RsvdFieldPosition: 0
[    33.283] 	DirectColorModeInfo: 0
[    33.283] 	PhysBasePtr: 0xd0000000
[    33.283] 	LinBytesPerScanLine: 1024
[    33.283] 	BnkNumberOfImagePages: 8
[    33.283] 	LinNumberOfImagePages: 8
[    33.283] 	LinRedMaskSize: 0
[    33.283] 	LinRedFieldPosition: 0
[    33.283] 	LinGreenMaskSize: 0
[    33.283] 	LinGreenFieldPosition: 0
[    33.283] 	LinBlueMaskSize: 0
[    33.283] 	LinBlueFieldPosition: 0
[    33.283] 	LinRsvdMaskSize: 0
[    33.283] 	LinRsvdFieldPosition: 0
[    33.283] 	MaxPixelClock: 230000000
[    33.284] Mode: 117 (1024x768)
[    33.284] 	ModeAttributes: 0x9b
[    33.284] 	WinAAttributes: 0x7
[    33.284] 	WinBAttributes: 0x0
[    33.284] 	WinGranularity: 64
[    33.284] 	WinSize: 64
[    33.284] 	WinASegment: 0xa000
[    33.284] 	WinBSegment: 0x0
[    33.284] 	WinFuncPtr: 0xc0007b7a
[    33.284] 	BytesPerScanline: 2048
[    33.284] 	XResolution: 1024
[    33.284] 	YResolution: 768
[    33.284] 	XCharSize: 8
[    33.284] 	YCharSize: 16
[    33.284] 	NumberOfPlanes: 1
[    33.284] 	BitsPerPixel: 16
[    33.284] 	NumberOfBanks: 1
[    33.284] 	MemoryModel: 6
[    33.284] 	BankSize: 0
[    33.284] 	NumberOfImages: 3
[    33.284] 	RedMaskSize: 5
[    33.284] 	RedFieldPosition: 11
[    33.284] 	GreenMaskSize: 6
[    33.284] 	GreenFieldPosition: 5
[    33.284] 	BlueMaskSize: 5
[    33.284] 	BlueFieldPosition: 0
[    33.284] 	RsvdMaskSize: 0
[    33.284] 	RsvdFieldPosition: 0
[    33.284] 	DirectColorModeInfo: 0
[    33.284] 	PhysBasePtr: 0xd0000000
[    33.284] 	LinBytesPerScanLine: 2048
[    33.284] 	BnkNumberOfImagePages: 3
[    33.284] 	LinNumberOfImagePages: 3
[    33.284] 	LinRedMaskSize: 5
[    33.284] 	LinRedFieldPosition: 11
[    33.284] 	LinGreenMaskSize: 6
[    33.284] 	LinGreenFieldPosition: 5
[    33.284] 	LinBlueMaskSize: 5
[    33.284] 	LinBlueFieldPosition: 0
[    33.284] 	LinRsvdMaskSize: 0
[    33.284] 	LinRsvdFieldPosition: 0
[    33.284] 	MaxPixelClock: 230000000
[    33.285] *Mode: 118 (1024x768)
[    33.285] 	ModeAttributes: 0x9b
[    33.285] 	WinAAttributes: 0x7
[    33.285] 	WinBAttributes: 0x0
[    33.285] 	WinGranularity: 64
[    33.285] 	WinSize: 64
[    33.285] 	WinASegment: 0xa000
[    33.285] 	WinBSegment: 0x0
[    33.285] 	WinFuncPtr: 0xc0007b7a
[    33.285] 	BytesPerScanline: 4096
[    33.285] 	XResolution: 1024
[    33.285] 	YResolution: 768
[    33.285] 	XCharSize: 8
[    33.285] 	YCharSize: 16
[    33.285] 	NumberOfPlanes: 1
[    33.285] 	BitsPerPixel: 32
[    33.285] 	NumberOfBanks: 1
[    33.285] 	MemoryModel: 6
[    33.285] 	BankSize: 0
[    33.285] 	NumberOfImages: 1
[    33.285] 	RedMaskSize: 8
[    33.285] 	RedFieldPosition: 16
[    33.285] 	GreenMaskSize: 8
[    33.285] 	GreenFieldPosition: 8
[    33.285] 	BlueMaskSize: 8
[    33.285] 	BlueFieldPosition: 0
[    33.285] 	RsvdMaskSize: 8
[    33.285] 	RsvdFieldPosition: 24
[    33.285] 	DirectColorModeInfo: 0
[    33.285] 	PhysBasePtr: 0xd0000000
[    33.285] 	LinBytesPerScanLine: 4096
[    33.285] 	BnkNumberOfImagePages: 1
[    33.285] 	LinNumberOfImagePages: 1
[    33.285] 	LinRedMaskSize: 8
[    33.285] 	LinRedFieldPosition: 16
[    33.285] 	LinGreenMaskSize: 8
[    33.285] 	LinGreenFieldPosition: 8
[    33.285] 	LinBlueMaskSize: 8
[    33.285] 	LinBlueFieldPosition: 0
[    33.285] 	LinRsvdMaskSize: 8
[    33.285] 	LinRsvdFieldPosition: 24
[    33.285] 	MaxPixelClock: 230000000
[    33.286] *Mode: 112 (640x480)
[    33.286] 	ModeAttributes: 0x9b
[    33.286] 	WinAAttributes: 0x7
[    33.286] 	WinBAttributes: 0x0
[    33.286] 	WinGranularity: 64
[    33.286] 	WinSize: 64
[    33.286] 	WinASegment: 0xa000
[    33.286] 	WinBSegment: 0x0
[    33.286] 	WinFuncPtr: 0xc0007b7a
[    33.286] 	BytesPerScanline: 2560
[    33.286] 	XResolution: 640
[    33.286] 	YResolution: 480
[    33.286] 	XCharSize: 8
[    33.286] 	YCharSize: 16
[    33.286] 	NumberOfPlanes: 1
[    33.286] 	BitsPerPixel: 32
[    33.286] 	NumberOfBanks: 1
[    33.286] 	MemoryModel: 6
[    33.286] 	BankSize: 0
[    33.286] 	NumberOfImages: 5
[    33.286] 	RedMaskSize: 8
[    33.286] 	RedFieldPosition: 16
[    33.286] 	GreenMaskSize: 8
[    33.286] 	GreenFieldPosition: 8
[    33.286] 	BlueMaskSize: 8
[    33.286] 	BlueFieldPosition: 0
[    33.286] 	RsvdMaskSize: 8
[    33.286] 	RsvdFieldPosition: 24
[    33.286] 	DirectColorModeInfo: 0
[    33.286] 	PhysBasePtr: 0xd0000000
[    33.286] 	LinBytesPerScanLine: 2560
[    33.286] 	BnkNumberOfImagePages: 5
[    33.286] 	LinNumberOfImagePages: 5
[    33.286] 	LinRedMaskSize: 8
[    33.286] 	LinRedFieldPosition: 16
[    33.286] 	LinGreenMaskSize: 8
[    33.286] 	LinGreenFieldPosition: 8
[    33.286] 	LinBlueMaskSize: 8
[    33.286] 	LinBlueFieldPosition: 0
[    33.286] 	LinRsvdMaskSize: 8
[    33.286] 	LinRsvdFieldPosition: 24
[    33.286] 	MaxPixelClock: 230000000
[    33.287] Mode: 114 (800x600)
[    33.287] 	ModeAttributes: 0x9b
[    33.287] 	WinAAttributes: 0x7
[    33.287] 	WinBAttributes: 0x0
[    33.287] 	WinGranularity: 64
[    33.287] 	WinSize: 64
[    33.287] 	WinASegment: 0xa000
[    33.287] 	WinBSegment: 0x0
[    33.287] 	WinFuncPtr: 0xc0007b7a
[    33.287] 	BytesPerScanline: 1600
[    33.287] 	XResolution: 800
[    33.287] 	YResolution: 600
[    33.287] 	XCharSize: 8
[    33.287] 	YCharSize: 16
[    33.287] 	NumberOfPlanes: 1
[    33.287] 	BitsPerPixel: 16
[    33.287] 	NumberOfBanks: 1
[    33.287] 	MemoryModel: 6
[    33.287] 	BankSize: 0
[    33.287] 	NumberOfImages: 6
[    33.287] 	RedMaskSize: 5
[    33.287] 	RedFieldPosition: 11
[    33.287] 	GreenMaskSize: 6
[    33.287] 	GreenFieldPosition: 5
[    33.287] 	BlueMaskSize: 5
[    33.287] 	BlueFieldPosition: 0
[    33.287] 	RsvdMaskSize: 0
[    33.287] 	RsvdFieldPosition: 0
[    33.287] 	DirectColorModeInfo: 0
[    33.287] 	PhysBasePtr: 0xd0000000
[    33.287] 	LinBytesPerScanLine: 1600
[    33.287] 	BnkNumberOfImagePages: 6
[    33.287] 	LinNumberOfImagePages: 6
[    33.287] 	LinRedMaskSize: 5
[    33.287] 	LinRedFieldPosition: 11
[    33.287] 	LinGreenMaskSize: 6
[    33.287] 	LinGreenFieldPosition: 5
[    33.287] 	LinBlueMaskSize: 5
[    33.287] 	LinBlueFieldPosition: 0
[    33.287] 	LinRsvdMaskSize: 0
[    33.287] 	LinRsvdFieldPosition: 0
[    33.287] 	MaxPixelClock: 230000000
[    33.288] *Mode: 115 (800x600)
[    33.288] 	ModeAttributes: 0x9b
[    33.288] 	WinAAttributes: 0x7
[    33.288] 	WinBAttributes: 0x0
[    33.288] 	WinGranularity: 64
[    33.288] 	WinSize: 64
[    33.288] 	WinASegment: 0xa000
[    33.288] 	WinBSegment: 0x0
[    33.288] 	WinFuncPtr: 0xc0007b7a
[    33.288] 	BytesPerScanline: 3200
[    33.288] 	XResolution: 800
[    33.288] 	YResolution: 600
[    33.288] 	XCharSize: 8
[    33.288] 	YCharSize: 16
[    33.288] 	NumberOfPlanes: 1
[    33.288] 	BitsPerPixel: 32
[    33.288] 	NumberOfBanks: 1
[    33.288] 	MemoryModel: 6
[    33.288] 	BankSize: 0
[    33.288] 	NumberOfImages: 2
[    33.288] 	RedMaskSize: 8
[    33.288] 	RedFieldPosition: 16
[    33.288] 	GreenMaskSize: 8
[    33.288] 	GreenFieldPosition: 8
[    33.288] 	BlueMaskSize: 8
[    33.288] 	BlueFieldPosition: 0
[    33.288] 	RsvdMaskSize: 8
[    33.288] 	RsvdFieldPosition: 24
[    33.288] 	DirectColorModeInfo: 0
[    33.288] 	PhysBasePtr: 0xd0000000
[    33.288] 	LinBytesPerScanLine: 3200
[    33.289] 	BnkNumberOfImagePages: 2
[    33.289] 	LinNumberOfImagePages: 2
[    33.289] 	LinRedMaskSize: 8
[    33.289] 	LinRedFieldPosition: 16
[    33.289] 	LinGreenMaskSize: 8
[    33.289] 	LinGreenFieldPosition: 8
[    33.289] 	LinBlueMaskSize: 8
[    33.289] 	LinBlueFieldPosition: 0
[    33.289] 	LinRsvdMaskSize: 8
[    33.289] 	LinRsvdFieldPosition: 24
[    33.289] 	MaxPixelClock: 230000000
[    33.289] Mode: 101 (640x480)
[    33.289] 	ModeAttributes: 0x9b
[    33.289] 	WinAAttributes: 0x7
[    33.289] 	WinBAttributes: 0x0
[    33.289] 	WinGranularity: 64
[    33.289] 	WinSize: 64
[    33.289] 	WinASegment: 0xa000
[    33.289] 	WinBSegment: 0x0
[    33.289] 	WinFuncPtr: 0xc0007b7a
[    33.289] 	BytesPerScanline: 640
[    33.289] 	XResolution: 640
[    33.289] 	YResolution: 480
[    33.289] 	XCharSize: 8
[    33.289] 	YCharSize: 16
[    33.289] 	NumberOfPlanes: 1
[    33.289] 	BitsPerPixel: 8
[    33.289] 	NumberOfBanks: 1
[    33.289] 	MemoryModel: 4
[    33.289] 	BankSize: 0
[    33.289] 	NumberOfImages: 22
[    33.289] 	RedMaskSize: 0
[    33.289] 	RedFieldPosition: 0
[    33.289] 	GreenMaskSize: 0
[    33.289] 	GreenFieldPosition: 0
[    33.289] 	BlueMaskSize: 0
[    33.289] 	BlueFieldPosition: 0
[    33.289] 	RsvdMaskSize: 0
[    33.289] 	RsvdFieldPosition: 0
[    33.289] 	DirectColorModeInfo: 0
[    33.289] 	PhysBasePtr: 0xd0000000
[    33.289] 	LinBytesPerScanLine: 640
[    33.289] 	BnkNumberOfImagePages: 22
[    33.289] 	LinNumberOfImagePages: 22
[    33.289] 	LinRedMaskSize: 0
[    33.289] 	LinRedFieldPosition: 0
[    33.289] 	LinGreenMaskSize: 0
[    33.289] 	LinGreenFieldPosition: 0
[    33.289] 	LinBlueMaskSize: 0
[    33.289] 	LinBlueFieldPosition: 0
[    33.289] 	LinRsvdMaskSize: 0
[    33.289] 	LinRsvdFieldPosition: 0
[    33.289] 	MaxPixelClock: 230000000
[    33.290] Mode: 103 (800x600)
[    33.290] 	ModeAttributes: 0x9b
[    33.290] 	WinAAttributes: 0x7
[    33.290] 	WinBAttributes: 0x0
[    33.290] 	WinGranularity: 64
[    33.290] 	WinSize: 64
[    33.290] 	WinASegment: 0xa000
[    33.290] 	WinBSegment: 0x0
[    33.290] 	WinFuncPtr: 0xc0007b7a
[    33.290] 	BytesPerScanline: 832
[    33.290] 	XResolution: 800
[    33.290] 	YResolution: 600
[    33.290] 	XCharSize: 8
[    33.290] 	YCharSize: 16
[    33.290] 	NumberOfPlanes: 1
[    33.290] 	BitsPerPixel: 8
[    33.290] 	NumberOfBanks: 1
[    33.290] 	MemoryModel: 4
[    33.290] 	BankSize: 0
[    33.290] 	NumberOfImages: 13
[    33.290] 	RedMaskSize: 0
[    33.290] 	RedFieldPosition: 0
[    33.290] 	GreenMaskSize: 0
[    33.290] 	GreenFieldPosition: 0
[    33.290] 	BlueMaskSize: 0
[    33.290] 	BlueFieldPosition: 0
[    33.290] 	RsvdMaskSize: 0
[    33.290] 	RsvdFieldPosition: 0
[    33.290] 	DirectColorModeInfo: 0
[    33.290] 	PhysBasePtr: 0xd0000000
[    33.290] 	LinBytesPerScanLine: 832
[    33.290] 	BnkNumberOfImagePages: 13
[    33.290] 	LinNumberOfImagePages: 13
[    33.290] 	LinRedMaskSize: 0
[    33.290] 	LinRedFieldPosition: 0
[    33.290] 	LinGreenMaskSize: 0
[    33.290] 	LinGreenFieldPosition: 0
[    33.290] 	LinBlueMaskSize: 0
[    33.290] 	LinBlueFieldPosition: 0
[    33.290] 	LinRsvdMaskSize: 0
[    33.290] 	LinRsvdFieldPosition: 0
[    33.290] 	MaxPixelClock: 230000000
[    33.291] Mode: 111 (640x480)
[    33.291] 	ModeAttributes: 0x9b
[    33.291] 	WinAAttributes: 0x7
[    33.291] 	WinBAttributes: 0x0
[    33.291] 	WinGranularity: 64
[    33.291] 	WinSize: 64
[    33.291] 	WinASegment: 0xa000
[    33.291] 	WinBSegment: 0x0
[    33.291] 	WinFuncPtr: 0xc0007b7a
[    33.291] 	BytesPerScanline: 1280
[    33.291] 	XResolution: 640
[    33.291] 	YResolution: 480
[    33.291] 	XCharSize: 8
[    33.291] 	YCharSize: 16
[    33.291] 	NumberOfPlanes: 1
[    33.291] 	BitsPerPixel: 16
[    33.291] 	NumberOfBanks: 1
[    33.291] 	MemoryModel: 6
[    33.291] 	BankSize: 0
[    33.291] 	NumberOfImages: 10
[    33.291] 	RedMaskSize: 5
[    33.291] 	RedFieldPosition: 11
[    33.291] 	GreenMaskSize: 6
[    33.291] 	GreenFieldPosition: 5
[    33.291] 	BlueMaskSize: 5
[    33.291] 	BlueFieldPosition: 0
[    33.291] 	RsvdMaskSize: 0
[    33.291] 	RsvdFieldPosition: 0
[    33.291] 	DirectColorModeInfo: 0
[    33.291] 	PhysBasePtr: 0xd0000000
[    33.291] 	LinBytesPerScanLine: 1280
[    33.291] 	BnkNumberOfImagePages: 10
[    33.291] 	LinNumberOfImagePages: 10
[    33.291] 	LinRedMaskSize: 5
[    33.291] 	LinRedFieldPosition: 11
[    33.291] 	LinGreenMaskSize: 6
[    33.291] 	LinGreenFieldPosition: 5
[    33.291] 	LinBlueMaskSize: 5
[    33.291] 	LinBlueFieldPosition: 0
[    33.291] 	LinRsvdMaskSize: 0
[    33.291] 	LinRsvdFieldPosition: 0
[    33.291] 	MaxPixelClock: 230000000
[    33.291] 
[    33.291] (II) VESA(0): Total Memory: 119 64KB banks (7616kB)
[    33.291] (II) VESA(0): <default monitor>: Using hsync value of 48.96 kHz
[    33.291] (II) VESA(0): <default monitor>: Using vrefresh value of 60.00 Hz
[    33.291] (WW) VESA(0): Unable to estimate virtual size
[    33.294] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    33.295] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    33.295] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    33.295] (--) VESA(0): Virtual size is 1280x800 (pitch 1280)
[    33.295] (**) VESA(0): *Built-in mode "1280x800"
[    33.295] (**) VESA(0): Display dimensions: (330, 210) mm
[    33.295] (**) VESA(0): DPI set to (98, 96)
[    33.295] (**) VESA(0): Using "Shadow Framebuffer"
[    33.295] (II) Loading sub module "shadow"
[    33.295] (II) LoadModule: "shadow"
[    33.295] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    33.295] (II) Module shadow: vendor="X.Org Foundation"
[    33.295] 	compiled for 1.11.3, module version = 1.1.0
[    33.295] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    33.295] (II) Loading sub module "fb"
[    33.295] (II) LoadModule: "fb"
[    33.296] (II) Loading /usr/lib/xorg/modules/libfb.so
[    33.296] (II) Module fb: vendor="X.Org Foundation"
[    33.296] 	compiled for 1.11.3, module version = 1.0.0
[    33.296] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    33.296] (II) UnloadModule: "fbdev"
[    33.296] (II) Unloading fbdev
[    33.296] (II) UnloadModule: "fbdevhw"
[    33.296] (II) Unloading fbdevhw
[    33.296] (==) Depth 24 pixmap format is 32 bpp
[    33.296] (II) Loading sub module "int10"
[    33.296] (II) LoadModule: "int10"
[    33.296] (II) Loading /usr/lib/xorg/modules/libint10.so
[    33.296] (II) Module int10: vendor="X.Org Foundation"
[    33.296] 	compiled for 1.11.3, module version = 1.0.0
[    33.296] 	ABI class: X.Org Video Driver, version 11.0
[    33.296] (II) VESA(0): initializing int10
[    33.297] (II) VESA(0): Bad V_BIOS checksum
[    33.297] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    33.297] (II) VESA(0): VESA BIOS detected
[    33.297] (II) VESA(0): VESA VBE Version 3.0
[    33.297] (II) VESA(0): VESA VBE Total Mem: 7616 kB
[    33.297] (II) VESA(0): VESA VBE OEM: Intel(r)Crestline Graphics Chip Accelerated VGA BIOS
[    33.297] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    33.297] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    33.297] (II) VESA(0): VESA VBE OEM Product: Intel(r)Crestline Graphics Controller
[    33.297] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    33.299] (II) VESA(0): virtual address = 0x7fe5f0514000,
	physical address = 0xd0000000, size = 7798784
[    33.317] (II) VESA(0): Setting up VESA Mode 0x162 (1280x800)
[    33.407] (==) VESA(0): Default visual is TrueColor
[    33.407] (==) VESA(0): Backing store disabled
[    33.407] (==) VESA(0): DPMS enabled
[    33.407] (==) RandR enabled
[    33.407] (II) Initializing built-in extension Generic Event Extension
[    33.407] (II) Initializing built-in extension SHAPE
[    33.407] (II) Initializing built-in extension MIT-SHM
[    33.407] (II) Initializing built-in extension XInputExtension
[    33.407] (II) Initializing built-in extension XTEST
[    33.407] (II) Initializing built-in extension BIG-REQUESTS
[    33.407] (II) Initializing built-in extension SYNC
[    33.407] (II) Initializing built-in extension XKEYBOARD
[    33.407] (II) Initializing built-in extension XC-MISC
[    33.407] (II) Initializing built-in extension SECURITY
[    33.407] (II) Initializing built-in extension XINERAMA
[    33.407] (II) Initializing built-in extension XFIXES
[    33.408] (II) Initializing built-in extension RENDER
[    33.408] (II) Initializing built-in extension RANDR
[    33.408] (II) Initializing built-in extension COMPOSITE
[    33.408] (II) Initializing built-in extension DAMAGE
[    33.415] (II) AIGLX: Screen 0 is not DRI2 capable
[    33.415] (II) AIGLX: Screen 0 is not DRI capable
[    33.435] (II) AIGLX: Loaded and initialized swrast
[    33.435] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    33.458] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    33.463] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    33.463] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.463] (II) LoadModule: "evdev"
[    33.463] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.464] (II) Module evdev: vendor="X.Org Foundation"
[    33.464] 	compiled for 1.11.3, module version = 2.7.0
[    33.464] 	Module class: X.Org XInput Driver
[    33.464] 	ABI class: X.Org XInput driver, version 16.0
[    33.464] (II) Using input driver 'evdev' for 'Power Button'
[    33.464] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.464] (**) Power Button: always reports core events
[    33.464] (**) evdev: Power Button: Device: "/dev/input/event2"
[    33.464] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.464] (--) evdev: Power Button: Found keys
[    33.464] (II) evdev: Power Button: Configuring as keyboard
[    33.464] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    33.464] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    33.464] (**) Option "xkb_rules" "evdev"
[    33.464] (**) Option "xkb_model" "pc105"
[    33.464] (**) Option "xkb_layout" "us"
[    33.465] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    33.465] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    33.465] (II) Using input driver 'evdev' for 'Video Bus'
[    33.465] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.465] (**) Video Bus: always reports core events
[    33.465] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    33.465] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    33.465] (--) evdev: Video Bus: Found keys
[    33.465] (II) evdev: Video Bus: Configuring as keyboard
[    33.465] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input4/event4"
[    33.465] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    33.465] (**) Option "xkb_rules" "evdev"
[    33.465] (**) Option "xkb_model" "pc105"
[    33.465] (**) Option "xkb_layout" "us"
[    33.466] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    33.466] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.466] (II) Using input driver 'evdev' for 'Power Button'
[    33.466] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.466] (**) Power Button: always reports core events
[    33.466] (**) evdev: Power Button: Device: "/dev/input/event1"
[    33.467] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.467] (--) evdev: Power Button: Found keys
[    33.467] (II) evdev: Power Button: Configuring as keyboard
[    33.467] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    33.467] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    33.467] (**) Option "xkb_rules" "evdev"
[    33.467] (**) Option "xkb_model" "pc105"
[    33.467] (**) Option "xkb_layout" "us"
[    33.468] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    33.468] (II) No input driver specified, ignoring this device.
[    33.468] (II) This device may have been added with another device file.
[    33.468] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event8)
[    33.468] (II) No input driver specified, ignoring this device.
[    33.468] (II) This device may have been added with another device file.
[    33.468] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event9)
[    33.469] (II) No input driver specified, ignoring this device.
[    33.469] (II) This device may have been added with another device file.
[    33.469] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    33.469] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    33.469] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    33.469] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.469] (**) AT Translated Set 2 keyboard: always reports core events
[    33.469] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    33.469] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    33.469] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    33.469] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    33.469] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    33.469] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    33.469] (**) Option "xkb_rules" "evdev"
[    33.469] (**) Option "xkb_model" "pc105"
[    33.469] (**) Option "xkb_layout" "us"
[    33.470] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event6)
[    33.470] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    33.470] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    33.470] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.470] (**) PS/2 Mouse: always reports core events
[    33.470] (**) evdev: PS/2 Mouse: Device: "/dev/input/event6"
[    33.470] (--) evdev: PS/2 Mouse: Vendor 0x2 Product 0x8
[    33.470] (--) evdev: PS/2 Mouse: Found 3 mouse buttons
[    33.470] (--) evdev: PS/2 Mouse: Found relative axes
[    33.471] (--) evdev: PS/2 Mouse: Found x and y relative axes
[    33.471] (II) evdev: PS/2 Mouse: Configuring as mouse
[    33.471] (**) evdev: PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    33.471] (**) evdev: PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    33.471] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    33.471] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE, id 10)
[    33.471] (II) evdev: PS/2 Mouse: initialized for relative axes.
[    33.471] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    33.471] (**) PS/2 Mouse: (accel) acceleration profile 0
[    33.471] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    33.471] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    33.472] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse0)
[    33.472] (II) No input driver specified, ignoring this device.
[    33.472] (II) This device may have been added with another device file.
[    33.472] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event7)
[    33.472] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    33.472] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    33.472] (II) LoadModule: "synaptics"
[    33.473] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    33.473] (II) Module synaptics: vendor="X.Org Foundation"
[    33.473] 	compiled for 1.11.3, module version = 1.6.2
[    33.473] 	Module class: X.Org XInput Driver
[    33.473] 	ABI class: X.Org XInput driver, version 16.0
[    33.473] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    33.473] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    33.473] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    33.473] (**) Option "Device" "/dev/input/event7"
[    33.536] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    33.536] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    33.536] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    33.536] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[    33.536] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    33.536] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[    33.536] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[    33.536] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    33.536] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    33.568] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[    33.568] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 11)
[    33.568] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    33.568] (**) synaptics: AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    33.568] (**) synaptics: AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    33.568] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    33.568] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    33.568] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    33.568] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    33.568] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    33.569] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[    33.569] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[    33.572] (II) config/udev: Adding input device Toshiba input device (/dev/input/event5)
[    33.572] (**) Toshiba input device: Applying InputClass "evdev keyboard catchall"
[    33.572] (II) Using input driver 'evdev' for 'Toshiba input device'
[    33.572] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.572] (**) Toshiba input device: always reports core events
[    33.572] (**) evdev: Toshiba input device: Device: "/dev/input/event5"
[    33.572] (--) evdev: Toshiba input device: Vendor 0 Product 0
[    33.572] (--) evdev: Toshiba input device: Found keys
[    33.572] (II) evdev: Toshiba input device: Configuring as keyboard
[    33.572] (**) Option "config_info" "udev:/sys/devices/virtual/input/input5/event5"
[    33.572] (II) XINPUT: Adding extended input device "Toshiba input device" (type: KEYBOARD, id 12)
[    33.572] (**) Option "xkb_rules" "evdev"
[    33.572] (**) Option "xkb_model" "pc105"
[    33.572] (**) Option "xkb_layout" "us"
[    34.324] (II) XKB: reuse xkmfile /var/lib/xkb/server-518754FAB1FA320CD11E67E5F27005732682D4B3.xkm
```

---

### Post by slixz85 on 2013-03-27
anyone that can help me with this, it would be very appreciated. i am having to return to work soon and need this laptop for my job. thanks

---

### Post by papibe on 2013-03-28
This is the only thing that I can see:
```
[    33.237] (EE) open /dev/fb0: No such file or directory
...
[    33.239] (II) VESA(0): Bad V_BIOS checksum
```
I don't have any concrete suggestion. I'm sorry.

The only thing I can think of is trying to get to the GUI by pressing Ctrl+Alt+F7 in case the frame buffer error is dragging you to a tty.

Regards.

---

### Post by slixz85 on 2013-03-29
thank you, unfortunately i have came to have to install windows vista onto it again as toshiba doesn't have great linux support i read about. the thing that is wierd is i am sure when it came preloaded it could play 3d games and everything was fine, i have looked for drivers for it for windows and unfortunately the drivers just pixelate the screen really badly and it becomes unusable. i tried 3 different drivers i found for this laptop. so since i am in a time crunch i will have to just do without being able to do anything 3d. that is crazy to me but my job takes alot of time anyway so no big deal in a sense.  thanks for trying to check out the log and helping out. windows gets rid of the black screen issue without a driver and does not freeze up badly like it used to when missing drivers with vista anyway.  i think it is a frame buffer issue also nomodeset worked with a couple distros but wierdly not all and noapic nolapic did the same worked with a few but not all. just a retarded deal. thanks man

---

### Post by slixz85 on 2013-05-09
display issue still remains if anyone can help. glxgears runs fine and glx direct info says yes it has direct rendering. any help would be awesome

---

### Post by papibe on 2013-05-10
Let's try to get the EDID info.

Install this package:
```
sudo apt-get install read-edid
```
Then please post the result of this command?
```
sudo get-edid | parse-edid 
```
Regards.

---

### Post by slixz85 on 2013-05-10
thanks. here is the edid info and also prob useless but i included all my glxinfo also prob for no reason :)






sudo get-edid | parse-edid
parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x2110 "Intel(r)Crestline Graphics Chip Accelerated VGA BIOS"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination supports DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call successful

parse-edid: EDID checksum passed.

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:f
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fe
	Identifier "SEC:4536"
	VendorName "SEC"
	ModelName "SEC:4536"
	# Block type: 2:0 3:f
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fe
	# DPMS capabilities: Active off:no  Suspend:no  Standby:no

	Mode 	"1280x800"	# vfreq 60.004Hz, hfreq 48.963kHz
		DotClock	68.940000
		HTimings	1280 1296 1344 1408
		VTimings	800 801 804 816
		Flags	"-HSync" "-VSync"
	EndMode
	# Block type: 2:0 3:f
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fe
EndSection









and glxinfo:



glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_MESA_copy_sub_buffer, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_EXT_texture_from_pixmap
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string: 2.1 Mesa 8.0.4
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_polygon_offset, GL_EXT_subtexture, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, GL_EXT_texture, 
    GL_EXT_texture3D, GL_IBM_rasterpos_clip, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_ARB_multitexture, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_MESA_window_pos, 
    GL_NV_packed_depth_stencil, GL_NV_texture_rectangle, GL_ARB_depth_texture, 
    GL_ARB_occlusion_query, GL_ARB_shadow, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_window_pos, 
    GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, GL_NV_fog_distance, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_wrap, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_primitive_restart, GL_ARB_fragment_program_shadow, 
    GL_ARB_half_float_pixel, GL_ARB_occlusion_query2, GL_ARB_point_sprite, 
    GL_ARB_shading_language_100, GL_ARB_sync, GL_ARB_texture_non_power_of_two, 
    GL_ARB_vertex_buffer_object, GL_ATI_blend_equation_separate, 
    GL_EXT_blend_equation_separate, GL_OES_read_format, 
    GL_ARB_pixel_buffer_object, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_float, GL_ARB_texture_rectangle, 
    GL_ATI_texture_compression_3dc, GL_EXT_packed_float, 
    GL_EXT_pixel_buffer_object, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_shared_exponent, 
    GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_packed_depth_stencil, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, 
    GL_ATI_texture_mirror_once, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_sRGB_decode, GL_OES_EGL_image, GL_ARB_copy_buffer, 
    GL_ARB_draw_instanced, GL_ARB_half_float_vertex, GL_ARB_instanced_arrays, 
    GL_ARB_map_buffer_range, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_vertex_array_bgra, GL_EXT_separate_shader_objects, 
    GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra, 
    GL_NV_conditional_render, GL_AMD_draw_buffers_blend, 
    GL_ARB_ES2_compatibility, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_provoking_vertex, 
    GL_ARB_sampler_objects, GL_ARB_shader_texture_lod, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_EXT_provoking_vertex, 
    GL_EXT_texture_snorm, GL_MESA_texture_signed_rgba, GL_ARB_robustness, 
    GL_ARB_texture_storage

96 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0d2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0d9 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0da 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0db 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0dc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0dd 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0de 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0df 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0e0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0e1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0e2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0e3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0e4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0e5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0e6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0e7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0e8 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0e9 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ea 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0eb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ec 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ed 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ee 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ef 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f4 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f5 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0fa 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0fb 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0fc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0fd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0fe 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0ff 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x100 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x101 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x102 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x103 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x104 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x105 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x106 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x107 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x108 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x109 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x10a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x10b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x10c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x10d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x10e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x10f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x110 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x111 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x112 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x113 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x114 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x115 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x116 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x117 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x118 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x119 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x11a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x11b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x11c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x11d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x11e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x11f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x120 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x121 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x122 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x123 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x124 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x125 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x126 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x127 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x128 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x129 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x12a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x12b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x12c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x12d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x12e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x12f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x041 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

144 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x042 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x043 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x044 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x045 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x046 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x047 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x048 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x049 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x04a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x04b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x04c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x04d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x04e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x04f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x050 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x051 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x052 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x053 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x054 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x055 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x056 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x057 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x058 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x059 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x05a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x05c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x05e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x060 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x061 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x062 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x063 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x064 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x065 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x066 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x06a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x06c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x06d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x06e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x06f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x070 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x071 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x072  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x073  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x074  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x075  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x076  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x077  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x078  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x079  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x07a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x07b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x07c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x07d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x07e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x07f  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x080  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x081  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x082  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x083  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x084  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x085  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x086  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x087  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x088  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x089  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x08a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x08c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x08e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x090 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x091 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x092 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x093 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x094 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x095 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x096 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x097 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x098 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x099 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x09d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x09e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x09f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0a0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0a1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0a2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a3 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a8 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0a9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ab 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ac 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ad 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ae 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0af 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0b5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0b6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0b7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0b8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0b9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0ba  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0bb  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0bc  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0bd  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0be  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0bf  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c0  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0c1  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0c2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0c3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0c4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0c5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0c6  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0c7  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0c8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0c9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ca  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0cb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0cc  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0cd  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0ce  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0cf  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0d0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0d1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow















thanks.

---

