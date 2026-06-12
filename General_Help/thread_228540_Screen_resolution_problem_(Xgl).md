---
title: "Screen resolution problem (Xgl)"
date: 2006-08-03
forum: General Help
---

### Post by abiezerm on 2006-08-03
hi everyone

yestarday i installed a Xgl and my screen resolution was before 
1280*1024 now is 800*600, and i change the xorg.conf and nothing happens

this is my xorg.conf:
[COLOR="Silver"][I]
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
			# local font server
	# if the local font server has problems, we can fall back on these
        # paths to defoma fonts
	FontPath     "unix/:7100"
	FontPath     "/usr/lib/X11/fonts/misc"
	FontPath     "/usr/lib/X11/fonts/cyrillic"
	FontPath     "/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/lib/X11/fonts/Type1"
	FontPath     "/usr/lib/X11/fonts/CID"
	FontPath     "/usr/lib/X11/fonts/100dpi"
	FontPath     "/usr/lib/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "dbe"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "record"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "keyboard"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "&#136;"
	VendorName   "AOC"
	ModelName    "7ElrA"
 ### Uncomment if you don't want to default to DDC:
	#HorizSync    	31.5 - 64.3
	HorizSync	30 - 70
	VertRefresh  	40.0 - 150.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"	
	BusID		"PCI:1:0:0"
	Option 	"RenderAccel" 		"true"
	Option 	"AllowGLXWithComposite" "true"
EndSection

Section "Screen"
	Identifier 	"Default Screen"
	Device     	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor    	"&#136;"
	DefaultDepth     24

	SubSection "Display"
		Viewport	0 0
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth     27
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
          Option  "Composite" "Enable"
EndSection
[/I][/COLOR]

any idias??

thanks

---

### Post by thingy on 2006-08-03
Try commenting out the:

[COLOR=Silver][I] 	HorizSync	30 - 70
	VertRefresh  	40.0 - 150.0

[/I][/COLOR]Also the line that say Depth 27 is prob. wrong as you can't have a depth of 27. I'd put down Depth 16 instead!

jin

---

### Post by abiezerm on 2006-08-03
> **thingy said:**
> Try commenting out the:

[COLOR=Silver][I] 	HorizSync	30 - 70
	VertRefresh  	40.0 - 150.0

[/I][/COLOR]Also the line that say Depth 27 is prob. wrong as you can't have a depth of 27. I'd put down Depth 16 instead!

jin

it dosn't work... now i can't enter in grafical mode
i try to change it.

other idea?

---

