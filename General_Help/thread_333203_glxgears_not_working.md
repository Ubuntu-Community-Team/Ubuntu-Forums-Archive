---
title: "glxgears not working"
date: 2007-01-07
forum: General Help
---

### Post by akudewan on 2007-01-07
Hi,

I was trying to run glxgears, and it gives me this output:
```

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

I'm using the non-free nvidia driver, and *Load "glx"* is present in xorg.conf.

Even those cool openGL screensavers aren't working. Here's my xorg.conf file:
```

# bare-bones XFree86 config to start the server in probe-only mode
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
	FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
	FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
	FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

EndSection
Section "ServerFlags"
	Option "AllowMouseOpenFail"
EndSection
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
	Load	"glx"
EndSection
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection
Section "InputDevice"
	Identifier	"Generic Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "Device"
	Identifier	"Generic Device"
	Driver		"nvidia"
	
EndSection
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Generic Mouse"
	Option "OffTime" "20"
EndSection

Section "Extensions"
#    Option "Composite" "Enable"
EndSection

```

Can anyone help me with this?

---

### Post by energiya on 2007-01-07
If your not using Beryl/Compiz try disabling composite or add
> Option "AllowGLXWithComposite" "1"
to your Device section in xorg.conf . Don't forget restarting X (or even reboot).
That worked for me.

---

### Post by akudewan on 2007-01-07
Thanks energiya. That did the trick! :)

---

