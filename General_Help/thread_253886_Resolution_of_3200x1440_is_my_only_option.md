---
title: "Resolution of 3200x1440 is my only option"
date: 2006-09-09
forum: General Help
---

### Post by brentrussell on 2006-09-09
Just after adding my second monitor I tried to change the resolution of 3200x1440 however, it was my only choice for a resolution. I started searching online and saw that you need to add different modes to your xorg file. Well I have about 6 modes in there and 3200x1440 is not even on the list. 

I let the nVidia install configure it with the --twinview flag but that gave me a really small resolution and I still only had one choice in Sys>Pref>Screen Resolution

nVidia GeForce FX 5900 (Dual head card)
Monitor 1 (main monitor) Viewsonic 21" g220fb
Monitor 2 (secondary monitor) HP 1702

xorg.conf:
> 
#####Omited mouse and keyboard info######

Section "Module"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"xtrap" #added this for dual monitors
	Load	"i2c"
EndSection


Section "Device"
	Identifier	"NVIDIA Corporation NV35 [GeForce FX 5900]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
	VideoRam	131072
	Option		"IgnoreEDID"			"on"
	Option		"UseDisplayDevice"		"CRT"
	Option		"RenderAccel"			"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"MetaModes" "1920x1440; 1856x1392; 1792x1344; 1600x1200; 1280x1024; 1152x864; 1024x768; 1024x768"
	Screen 0
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV35 [GeForce FX 5900 2]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
	VideoRam	131072
	Option		"IgnoreEDID"			"on"
	Option		"UseDisplayDevice"		"DFP"
	Option		"RenderAccel"			"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"MetaModes" "1920x1440; 1856x1392; 1792x1344; 1600x1200; 1280x1024; 1152x864; 1024x768; 1024x768"
	Screen 1
EndSection

Section "Monitor"
	Identifier	"ViewSonic G220fb"
	Option		"DPMS"
	HorizSync	30-110
	VertRefresh	50-180
EndSection

Section "Monitor"
	Identifier	"HP 1702 LCD"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Screen CRT"
	Device		"NVIDIA Corporation NV35 [GeForce FX 5900]"
	Monitor		"ViewSonic G220fb"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen LCD"
	Device		"NVIDIA Corporation NV35 [GeForce FX 5900 2]"
	Monitor		"HP 1702 LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Screen CRT"	0 0
	Screen 1	"Screen LCD"	RightOf	"Screen CRT"
	Option		"xinerama"	"on"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


Here is my /var/log/Xorg.0.log file
*(Some is omitted due to character constraints)*
> 

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux saigon 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep  7 21:50:49 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen CRT" (0)
(**) |   |-->Monitor "ViewSonic G220fb"
(**) |   |-->Device "NVIDIA Corporation NV35 [GeForce FX 5900]"
(**) |-->Screen "Screen LCD" (1)
(**) |   |-->Monitor "HP 1702 LCD"
(**) |   |-->Device "NVIDIA Corporation NV35 [GeForce FX 5900 2]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "on"
(**) Xinerama: enabled
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 1043,80ac rev c1 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 1043,80ac rev c1 class 05,00,00 hdr 80

(--) PCI:*(3:0:0) nVidia Corporation NV35 [GeForce FX 5900] rev 161, Mem @ 0xe2000000/24, 0xd8000000/27
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff

0x0000e01f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "xtrap"
(II) Loading /usr/lib/xorg/modules/extensions/libxtrap.so
(II) Module xtrap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DEC-XTRAP
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[40] 0	0	0xe30003b0 - 0xe30003bb (0xc) IS[B]
	[41] 0	0	0xe30003c0 - 0xe30003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "IgnoreEDID" "on"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "UseDisplayDevice" "CRT"
(**) NVIDIA(0): Enabling RENDER acceleration
(WW) NVIDIA(0): 
(WW) NVIDIA(0): The IgnoreEDID and NoDDC options have been deprecated.  The
(WW) NVIDIA(0):     NVIDIA X driver makes use of a display device's EDID
(WW) NVIDIA(0):     during construction of its modePool.  It is recommended
(WW) NVIDIA(0):     that you allow the X driver to make use of any available
(WW) NVIDIA(0):     EDID.  If, however, you know what you are doing and have
(WW) NVIDIA(0):     good reason to do so, you can disable the X driver's use
(WW) NVIDIA(0):     of EDIDs by setting the "UseEDID" X configuration option
(WW) NVIDIA(0):     to FALSE; e.g.,
(WW) NVIDIA(0): 
(WW) NVIDIA(0):   Option "UseEDID" "FALSE"
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Note that, rather than globally disable all uses of the EDID,
(WW) NVIDIA(0):     you can individually disable each particular use of the
(WW) NVIDIA(0):     EDID; e.g.,
(WW) NVIDIA(0): 
(WW) NVIDIA(0):   Option "UseEDIDFreqs" "FALSE"
(WW) NVIDIA(0):   Option "UseEDIDDpi" "FALSE"
(WW) NVIDIA(0):   Option "ModeValidation" "NoEdidModes"
(WW) NVIDIA(0): 
(WW) NVIDIA(0): See the README for details on each of these options.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to read EDID for display device CRT-1
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5900 at PCI:3:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.35.20.22.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5900 at PCI:3:0:0:
(--) NVIDIA(0):     ViewSonic G220fb (CRT-0)
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0): ViewSonic G220fb (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Option "UseDisplayDevice" "CRT" converted to "CRT-0, CRT-1".
(WW) NVIDIA(0): Multiple display devices requested "CRT-0, CRT-1" but TwinView
(WW) NVIDIA(0):     not enabled; this screen will only use display device
(WW) NVIDIA(0):     "CRT-0".
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1920x1440"
(II) NVIDIA(0):     "1856x1392"
(II) NVIDIA(0):     "1792x1344"
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1440
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "IgnoreEDID" "on"
(**) NVIDIA(1): Option "RenderAccel" "true"
(**) NVIDIA(1): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(1): Option "UseDisplayDevice" "DFP"
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU GeForce FX 5900 at PCI:3:0:0
(--) NVIDIA(1): VideoRAM: 131072 kBytes
(--) NVIDIA(1): VideoBIOS: 04.35.20.22.00
(II) NVIDIA(1): Detected AGP rate: 8X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce FX 5900 at PCI:3:0:0:
(--) NVIDIA(1):     ViewSonic G220fb (CRT-0)
(--) NVIDIA(1):     CRT-1
(--) NVIDIA(1): ViewSonic G220fb (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): CRT-1: 400.0 MHz maximum pixel clock
(WW) NVIDIA(1): Option "UseDisplayDevice" requested "DFP", but no unused DFPs
(WW) NVIDIA(1):     are available.
(II) NVIDIA(1): Option "UseDisplayDevice" "DFP" converted to "".
(WW) NVIDIA(1): Unable to find any of the requested display device "" in the
(WW) NVIDIA(1):     list of available display devices "CRT-1".
(II) NVIDIA(1): Assigned Display Device: CRT-1
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "1280x1024"
(II) NVIDIA(1):     "1152x864"
(II) NVIDIA(1):     "1024x768"
(II) NVIDIA(1):     "800x600"
(II) NVIDIA(1):     "640x480"
(II) NVIDIA(1): Virtual screen size determined to be 1280 x 1024
(++) NVIDIA(1): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after preInit:
	[0] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[1] 0	0	0xe2000000 - 0xe2ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[41] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[42] 0	0	0xe30003b0 - 0xe30003bb (0xc) IS[B]
	[43] 0	0	0xe30003c0 - 0xe30003df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1920x1440"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Setting mode "1280x1024"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(1): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
Screen 0 is using RAC for io
Screen 1 is using RAC for io
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded



I tried twinview with the nVidia configure by passing it the --twinview but the same thing happened but with a very low resolution

---

