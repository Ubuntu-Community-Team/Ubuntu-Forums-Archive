---
title: "Unique XPRESS 200 + fglrx 8.32 + beryl issue"
date: 2007-01-27
forum: General Help
---

### Post by spednik on 2007-01-27
I've been trying to work out beryl on my woeful xpress 200 card (not the 200m) for months now. 
after doing some serious searching on this forum ,  I dicovered that upgrading to the newest 8.32.5 fglrx driver (i was running 8.28) would fix my problem. I installed those last night, and i think i have it working, here is the output from fglrxinfo ```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6234 (8.32.5)

```
I am able to get direct rendering, and glxgears runs fine, etc. BUT, when i try to run beryl i get this, even though DO have xgl installed ```
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: No composite extension



```
, so i tried to outsmart it and tried to just type xgl , but i get ```
Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

```

I'm sort of at a loss here. It seems the 8.32 driver is working for me, but I still can't get beryl to run. Heres my xorg.conf ```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "VA702b"
	HorizSync    30.0 - 82.0
	VertRefresh  50.0 - 85.0
	Option	    "DPMS"
EndSection

Section "Device"

 #STOCK 4 LINES TOTAL 
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
	Driver      "fglrx"
	Option	    "no_accel" "no"
	Option	    "no_dri" "no"
	Option	    "DynamicClocks" "on"
	Option	    "mtrr" "on"
	Option	    "DesktopSetup" "Single"
	Option	    "ScreenOverlap" "0"
	Option	    "Capabilities" "0x00000000"
	Option	    "CapabilitiesEx" "0x00000000"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "CenterMode" "off"
	Option	    "PseudoColorVisuals" "off"
	Option	    "Stereo" "off"
	Option	    "StereoSyncEnable" "1"
	Option	    "FSAAEnable" "no"
	Option	    "FSAAScale" "1"
	Option	    "FSAADisableGamma" "no"
	Option	    "FSAACustomizeMSPos" "no"
	Option	    "FSAAMSPosX0" "0.000000"
	Option	    "FSAAMSPosY0" "0.000000"
	Option	    "FSAAMSPosX1" "0.000000"
	Option	    "FSAAMSPosY1" "0.000000"
	Option	    "FSAAMSPosX2" "0.000000"
	Option	    "FSAAMSPosY2" "0.000000"
	Option	    "FSAAMSPosX3" "0.000000"
	Option	    "FSAAMSPosY3" "0.000000"
	Option	    "FSAAMSPosX4" "0.000000"
	Option	    "FSAAMSPosY4" "0.000000"
	Option	    "FSAAMSPosX5" "0.000000"
	Option	    "FSAAMSPosY5" "0.000000"
	Option	    "UseFastTLS" "0"
	Option	    "BlockSignalsOnLock" "on"
	Option	    "UseInternalAGPGART" "no"
	Option	    "ForceGenericCPU" "no"
	Option	    "KernelModuleParm" "agplock=0"
	Option	    "PowerState" "1"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
	Monitor    "VA702b"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection


```

If anyone could help me out at all or point me in the right direction, that would be great , it would be much appreciated, thanks all.

---

### Post by lavinog on 2007-02-02
I think you are supposed to logout and select session->xgl then log back in?

---

