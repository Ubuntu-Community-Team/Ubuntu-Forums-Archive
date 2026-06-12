---
title: "still about 915resolution"
date: 2006-12-16
forum: General Help
---

### Post by razzo on 2006-12-16
Hello ,
I'm running ubuntu edgy on a desktop with an intel graphic card and a 20" LCD monitor that should supports 1400x1050 resolution .

The f**kin' card have this chipset 
Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

As I have read in many thread and also in [https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)
I've installed the 915resolution package , but doesn't work .

This is the procedure that I adopt :

```

sudo 915resolution -l

Intel 800/900 Series VBIOS Hack : version 0.5.2
Chipset: 845G
BIOS: TYPE 3
Mode Table Offset: $C0000 + $4d2
Mode Table Entries: 25

Mode 30 : 640x480, 8 bits/pixel
Mode 31 : 640x400, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 40 : 640x480, 15 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 42 : 800x600, 15 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 44 : 1024x768, 15 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 48 : 1280x1024, 15 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4a : 1600x1200, 15 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4c : 1920x1440, 15 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel

```

I don't use 800x600 so i choose Mode 32 :
sudo 915resolution 32 1400 1050

the confirmation :
sudo 915resolution -l
...
Mode 32 : 800x600, 8 bits/pixel
...

but when i restart X server , gdm and X doesn't start .
The monitor remain black :(

This is some pieces of my xorg.conf :

```

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	50-75
EndSection

Section "Device"
	Identifier  "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver      "i810"
	Option	    "RenderAccel" "1"
	Option	    "NoRenderExtension" "0"
	Option	    "XAANoOffscreenPixmaps" "1"
	Option	    "AllowGLXWithComposite" "1"
	Option	    "DPMS" "true"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"SyncMaster"
	DefaultDepth	24
	Option	    "AddARGBGLXVisuals" "1"
	SubSection "Display"
		Depth		1
		Modes		"1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

and this is the most significant output of xorg log .
```

......
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers/i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.6.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
(II) Primary Device is: PCI 00:02:0
(--) Chipset 845G found

.....

(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 8000 kB
(II) I810(0): VESA VBE OEM: Brookdale-G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Brookdale-G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 845G
(--) I810(0): Chipset: "845G"
(--) I810(0): Linear framebuffer at 0xE0000000
(--) I810(0): IO registers at addr 0xEC100000
(II) I810(0): 1 display pipe available.
(II) I810(0): detected 8060 kB stolen memory.
(II) I810(0): Kernel reported 238848 total, 1 used
(II) I810(0): I830CheckAvailableMemory: 955388 kB available
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
(WW) I810(0): Extended BIOS function 0x5f11 not supported.
(II) I810(0): Before: SWF1 is 0x00000108
(II) I810(0): After: SWF1 is 0x00000108
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 8000 kB
(II) I810(0): VESA VBE OEM: Brookdale-G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Brookdale-G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): BIOS now sees 8000 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 8060 kByte
(==) I810(0): VideoRAM: 65536 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 2759
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
	      If you encounter this problem please add 
		 Option "DisplayInfo" "FALSE"
	      to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: TV: attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: DFP (digital flat panel): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: LFP (local flat panel): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: Second (second CRT): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0): 	CRT
(==) I810(0): Display is using Pipe A
(--) I810(0): Maximum frambuffer space: 65368 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: SAM  Model: 21b  Serial#: 1212232240
(II) I810(0): Year: 2006  Week: 47
(II) I810(0): EDID Version: 1.3
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) I810(0): Sync:  Separate  Composite  SyncOnGreen
(II) I810(0): Max H-Image Size [cm]: horiz.: 41  vert.: 30
(II) I810(0): Gamma: 2.20
(II) I810(0): DPMS capabilities: Off; RGB/Color Display
(II) I810(0): First detailed timing is preferred mode
(II) I810(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) I810(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@67Hz
(II) I810(0): 640x480@72Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@56Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 800x600@72Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 832x624@75Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@70Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): 1280x1024@75Hz
(II) I810(0): 1152x870@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
(II) I810(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) I810(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) I810(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 121.8 MHz   Image Size:  408 x 300 mm
(II) I810(0): h_active: 1400  h_sync: 1488  h_sync_end 1632 h_blank_end 1864 h_border: 0
(II) I810(0): v_active: 1050  v_sync: 1053  v_sync_end 1057 v_blanking: 1089 v_border: 0
(II) I810(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 160 MHz
(II) I810(0): Monitor name: SyncMaster
(II) I810(0): Serial No: HSALB08558
(II) I810(0): Will use BIOS call 0x5f05 to set refresh rates for CRTs.
(--) I810(0): Maximum space available for video modes: 8000 kByte
(II) I810(0): Using detected DDC timings
(II) I810(0): 	HorizSync 30-81
(II) I810(0): 	VertRefresh 56-75
(WW) I810(0): config file vrefresh range 50-75Hz not within DDC vrefresh range 56-75Hz

.......

(II) I810(0): SyncMaster: Using hsync range of 30.00-81.00 kHz
(II) I810(0): SyncMaster: Using vrefresh range of 56.00-75.00 Hz
(II) I810(0): Not using mode "1280x960" (no mode of this name)
(II) I810(0): Not using mode "1152x864" (no mode of this name)
(II) I810(0): Not using mode "800x600" (no mode of this name)
(II) I810(0): Not using built-in mode "1600x1200" (width too large for virtual size)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1400 -> 2048).
(--) I810(0): Virtual size is 1400x1050 (pitch 2048)
(**) I810(0): *Built-in mode "1400x1050"
(**) I810(0): *Built-in mode "1280x1024"
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "640x480"
(II) I810(0): Attempting to use 74.76Hz refresh for mode "1400x1050" (852)
(II) I810(0): Attempting to use 75.02Hz refresh for mode "1280x1024" (858)
(II) I810(0): Attempting to use 75.08Hz refresh for mode "1024x768" (854)
(II) I810(0): Attempting to use 75.00Hz refresh for mode "640x480" (850)
(--) I810(0): Display dimensions: (410, 300) mm
(--) I810(0): DPI set to (86, 88)

......

(WW) I810(0): Successfully set original devices
(WW) I810(0): Setting the original video mode instead of restoring
	the saved state
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.
(II) I810(0): xf86UnbindGARTMemory: unbind key 8
(II) I810(0): xf86UnbindGARTMemory: unbind key 0
(II) I810(0): xf86UnbindGARTMemory: unbind key 1
(II) I810(0): xf86UnbindGARTMemory: unbind key 3
(II) I810(0): xf86UnbindGARTMemory: unbind key 2
(II) I810(0): xf86UnbindGARTMemory: unbind key 4
(II) I810(0): xf86UnbindGARTMemory: unbind key 5
(II) I810(0): xf86UnbindGARTMemory: unbind key 6
(II) I810(0): xf86UnbindGARTMemory: unbind key 7
(WW) I810(0): Successfully set original devices (2)

```

Someone could help me ?
Thanks in advance

---

### Post by taurus on 2006-12-16
In your /etc/X11/xorg.conf, you are still using "i810" driver for your graphic card!!!

```
Driver         "i810"
```
May want to edit /etc/X11/xorg.conf and change it to "915resolution" then...

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by razzo on 2006-12-16
Uh ?
If I not mistake, 915resolution is not a video driver but a little tool that apply a patch at runtime .
In fact it patches only the RAM version of the video bios allowing to overwrite a video mode with desirable mode (1400x1050 in my case) .

Driver should be remain i810 , in fact with 915resolution as driver xorg doesn't starts .
"can't found a driver"
as described in : [http://www.ubuntuforums.org/showthread.php?t=312370&highlight=i810+915resolution](http://www.ubuntuforums.org/showthread.php?t=312370&highlight=i810+915resolution)

---

