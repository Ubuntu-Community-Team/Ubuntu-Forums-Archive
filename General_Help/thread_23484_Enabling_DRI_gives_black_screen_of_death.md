---
title: "Enabling DRI gives black screen of death"
date: 2005-04-02
forum: General Help
---

### Post by movery on 2005-04-02
If I enable the DRI module in my xorg config by uncommenting the line below and restart my laptop I just get a black screen!  If I leave this commented then everything works OK but it doesn't pick up the fglrx drivers for 3D acc and uses mesa instead :(

Section "ServerLayout"
	Identifier     "XFree86 Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/usr/X11R6/lib/X11/rgb"
	ModulePath   "/usr/X11R6/lib/modules"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc/"
	FontPath     "/usr/X11R6/lib/X11/fonts/Speedo/"
	FontPath     "/usr/X11R6/lib/X11/fonts/Type1/"
	FontPath     "/usr/X11R6/lib/X11/fonts/CID/"
	FontPath     "/usr/X11R6/lib/X11/fonts/75dpi/"
	FontPath     "/usr/X11R6/lib/X11/fonts/100dpi/"
EndSection

# ************************************************** ********************
# DRI Section
# ************************************************** ********************
Section "dri"
# Access to OpenGL ICD is allowed for all users:
Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
# Group 100 # users
# Mode 0660
EndSection

Section "Module"
	Load  "record"
	Load  "extmod"
	Load  "dbe"
**#	Load  "dri"**
	Load  "glx"
	Load  "xtrap"
	Load  "type1"
	Load  "speedo"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "keyboard"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/psaux"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"	
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "ForcePCIMode"       	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "CPPIOMode"          	# [<bool>]
        #Option     "CPusecTimeout"      	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPFastWrite"       	# [<bool>]
        #Option     "AGPSize"            	# <i>
        #Option     "GARTSize"           	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "NoBackBuffer"       	# [<bool>]
        #Option     "PanelOff"           	# [<bool>]
        #Option     "DDCMode"            	# [<bool>]
        #Option     "MonitorLayout"      	# [<str>]
        #Option     "IgnoreEDID"         	# [<bool>]
        #Option     "OverlayOnCRTC2"     	# [<bool>]
        #Option     "CloneMode"          	# [<str>]
        #Option     "CloneHSync"         	# [<str>]
        #Option     "CloneVRefresh"      	# [<str>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "DisplayPriority"    	# [<str>]
        #Option     "PanelSize"          	# [<str>]
        #Option     "ForceMinDotClock"   	# <freq>
	Option 	    "UseInternalAGPGART"       "no"
	Option	    "NoDDC"
	Option      "BlockSignalsOnLock" "off"
	Option 	    "DRI" "true"
	Identifier  "Card0"
	Driver      "fglrx"
	VendorName  "ATI Technologies Inc"
	BoardName   "Unknown Board"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth     1
	EndSubSection
	SubSection "Display"
		Depth     4
	EndSubSection
	SubSection "Display"
		Depth     8
	EndSubSection
	SubSection "Display"
		Depth     15
	EndSubSection
	SubSection "Display"
		Depth     16
	EndSubSection
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection


This is the Xorg log for what happens when I leave the DRI line UNcommented is attached...  This is driving me MAD!!!  3D acceleration is at my fingertips but it won't work!!! :)

---

### Post by ubuntu_demon on 2005-04-02
do 
sudo dpg-reconfigure xserver-xorg

choose the driver that you want and make sure to disable DRI (it's also a question there)

---

### Post by movery on 2005-04-02
Is that not the same as just commenting out the line? (apologies if this is a stupid question).

Also, don't I need this module for 3D accel to work?

Thanks!

---

### Post by ubuntu_demon on 2005-04-02
[QUOTE=movery]Is that not the same as just commenting out the line? (apologies if this is a stupid question).

Also, don't I need this module for 3D accel to work?

Thanks![/QUOTE]
 yeah probably but that's not the point :)

ubuntu hoary gets upgraded constantly so sometimes you have to reconfigure your xserver and dpkg-reconfigure xserver-xorg works great for this in my experiences. If this doesn't work dist-upgrading probably will but maybe you have to wait for a while until your bug is removed.

I hope this method works if not you might have to submit a bugreport if this hasn't been done already.

---

