---
title: "Video does not display on external LCD, but does on laptop LCD"
date: 2006-11-27
forum: General Help
---

### Post by kbracer on 2006-11-27
Playing video works normally when viewed on the laptop screen. This includes viewing avi, mpeg, wmv, and dvd in player applications and in Firefox plugins.

When I do the same using an external LCD monitor, the video plays but only a field of blue is shown in the player or Firefox plugin. I have tried Totem, MPlayer, and gxine with the same result. I can switch back and forth between the laptop LCD and the external LCD (using laptop fn+F10 keys) while a video plays and observe this behavior in action - laptop works and external doesn't.

Laptop is a Fujitsu S6120 having integrated Intel graphics. External LCD is a Mitsubishi NXM56LCD. Beryl is installed on this machine, but I stopped running "beryl" or "beryl-manager" once the novelty wore off.

Screenshot shows an example of the blank (blue field) video on the external LCD. On the laptop LCD it would be identical except that the video would appear normally in place of the blue field.

One more note: The fn+F10 hotkey on the laptop cycles between three monitor output settings: Laptop, External, and Both. When set to "Both", the laptop screen appears normal while the external has a wavy "interference" look about it.

Faulty hardware can probably be ruled out, as this double monitor business all behaves perfectly normal under my dual-booted Windows XP.

xorg.conf
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dbe"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	Option		"XAANoOffscreenPixmaps"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
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
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option		"AIGLX" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option	"Composite" "Enable"
EndSection

```

---

### Post by alphane on 2006-11-27
This may not be an issue per se.  I know that in Windows, when using dual/multi screens, you cannot, by default, have the same video on both your primary and secondary screens, if you are "cloning" your desktop onto an external device.

I can't recall off-hand the reason, but it's probably due to some kind of licence or copyright issue etc.

I know when I use my (WinXP) laptop and external screen, I have to close my laptop lid to get the picture to display on the monitor.

Try pressing the screen off catch button on your laptop.  My guess is that the video will display correctly.

Regards,

Alphane

---

### Post by kbracer on 2006-11-27
I have never experienced that behavior in WinXP. If both the laptop and external monitor are on and displaying the same thing, then you see the video on both. I verified that just prior to this response. Besides, my installation of Ubuntu would not be effected by any copy-management schemes found in XP.

Also, I only use Ubuntu with either the laptop screen or the external monitor - never both at the same time. I already know the issue happens when the laptop LCD is off.

> **alphane said:**
> This may not be an issue per se.  I know that in Windows, when using dual/multi screens, you cannot, by default, have the same video on both your primary and secondary screens, if you are "cloning" your desktop onto an external device.

I can't recall off-hand the reason, but it's probably due to some kind of licence or copyright issue etc.

I know when I use my (WinXP) laptop and external screen, I have to close my laptop lid to get the picture to display on the monitor.

Try pressing the screen off catch button on your laptop.  My guess is that the video will display correctly.

Regards,

Alphane

---

