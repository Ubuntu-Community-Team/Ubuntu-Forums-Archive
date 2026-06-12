---
title: "Some resolution help with the new kernel"
date: 2007-05-29
forum: General Help
---

### Post by lckeeper1 on 2007-05-29
Hey all,

I was pretty fortunate it seems with the updated kernel, as it has barely affected me. However, there is one bug that I can't seem to figure out. I recently bought a widescreen monitor, and before the update I could get the native 1440x900 resolution through both nvidia-settings, and through my xorg.

After the update and the move to the new drivers, I can't seem to find my 1440x900 resolution anywhere. I haven't done anything different to my xorg, and it is still listed in there, but I can't select it from nvidia-settings or the Preferences menu. So now I have this pretty, new widescreen but I'm looking at it in 1280x900. I was just wondering what the problem could be.

I almost forgot, I'm running on a GeForce 6600, so I'm assuming it should run with the new drivers. Here is a copy of my xorg as well:

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event9"
	Option		"Protocol" "ExplorerPS/2"
	Option		"Emulate3Buttons" "true"
	Option		"Buttons" "7"
	Option		"ButtonMapping" "1 2 3 6 7"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600]"
	Driver		"nvidia"
	Busid		"PCI:4:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL1916W"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6600]"
	Monitor		"Monitor0"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1440x900"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection



Thanks in advance!

---

### Post by n8bounds on 2007-05-29
have you rebooted into the older kernel and had the same problems??

---

### Post by lckeeper1 on 2007-05-30
Yup, I've booted into both the 16 and 15 kernel and now I have the same problem regarding resolutions. I also forgot to mention I'm running 7.04.

---

### Post by lckeeper1 on 2007-05-30
A lil bumpity bump.

I'm still using the -9755 nvidia driver on either the -15 or -16 kernel, as the -96xx driver won't let me start X.

If anyone has any ideas how I can get my 1440x900 res back, it would be very much appreciated! Thanks so much!

---

### Post by DoktorSeven on 2007-05-30
[http://eccentric.cx/wordpress/?p=112](http://eccentric.cx/wordpress/?p=112)

---

### Post by lckeeper1 on 2007-05-30
Thanks for the quick reply Dok. I've made the appropriate amendments to my xorg by adding the lines described in your link. However, I'm still facing the same problem. No 1440x900 res for me :(.

I also get the following errors when i run "sudo nvidia-settings" in a terminal. This has also occured following the update in drivers and had never happened prior. 

ERROR: Cannot open display 'dan-desktop:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 19 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 20 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 21 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 22 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 23 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 24 of configuration
       file '/home/dan/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 25 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ForceGenericCpu specified on line 26 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadow specified on line 27 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 28 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 29 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 30 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 31 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 32 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 33 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 34 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 35 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GPUScaling specified on line 36 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 37 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 38 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 39 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 40 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 41 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 42 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 43 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 44 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 45 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 46 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       47 of configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       48 of configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 49 of
       configuration file '/home/dan/.nvidia-settings-rc' (no Display
       connection).


Thanks for taking the time to read this. I'm loving Ubuntu with a passion and spreading the good word, but I want it to look pretty too on my nice new monitor;)

---

### Post by lckeeper1 on 2007-05-31
A lil bump.

I'm still experiencing the same problems as before. If anyone can point me in the right direction, any help is appreciated. Thanks!

---

### Post by justinraged on 2007-09-30
I had the same problem - disabling the "Include X Display Names in Config File" in nvidia-settings Configuration solved it...

---

