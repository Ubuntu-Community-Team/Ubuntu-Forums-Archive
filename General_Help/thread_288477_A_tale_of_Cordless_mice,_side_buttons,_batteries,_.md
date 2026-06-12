---
title: "A tale of Cordless mice, side buttons, batteries, and upgrades."
date: 2006-10-29
forum: General Help
---

### Post by zenwhen on 2006-10-29
I have two Logitech mice. I have a cordless MX700, and an MX500. I have two mice because the cordless mouse eventually runs out of battery power while I am using it, and I need to be able to quickly pick up a similar mouse and continue working. 

This has never been a problem for me, until I upgraded to Edgy.

I love using the side buttons on these mice to go back and forward on the internet and in Nautilus.

 I used an old guide that Panickedthumb wrote all the way up until Dapper, where they broke that guide, and then i switched to [this guide](http://ubuntuforums.org/showthread.php?t=44191&highlight=side+buttons), which did work on Dapper. 

That guide does not work now in Edgy, so I switched to [this guide](http://ubuntuforums.org/showthread.php?t=219894), which uses the evdev protocol, which didn't work properly without a downgraded .deb for evdev in Dapper. 

I can get one mouse to work properly in Edgy using this method. However, I cannot get two mice to work at the same time.

I added two evdev rules. One uses event8. One uses event9.

Heres's my /etc/udev/rules.d/19-local.rules:

```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event9"
KERNEL=="event[0-9]*", SYSFS{../name}=="B16_b_02 USB-PS/2 Optical Mouse", NAME="input/event8"
```

Here's my xorg.conf:

```
Section "Module"
    Load       "dbe"
    Load       "type1"
#    Load       "speedo"
    Load       "freetype"
    Load       "glx"
    Load       "extmod"
EndSection

Section "Files"
    RgbPath    "/usr/X11R6/lib/X11/rgb"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/TTF/"
    FontPath   "/usr/X11R6/lib/X11/fonts/artwiz-fonts/"
    FontPath   "/usr/X11R6/lib/X11/fonts/cyrillic/"
EndSection

#Section "Extensions"
#Option "Composite" "Enable"
#EndSection


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

#Section "InputDevice"
      # Identifier "MX500"
       #Driver     "mouse"
      # Option     "CorePointer"
     #  Option     "Device"  "/dev/input/mice"
    #   Option     "Protocol"  "ExplorerPS/2"
   #    Option     "Buttons"      "7"
  #     Option     "ZAxisMapping"   "4 5"
 #      Option     "Resolution"     "800"
#EndSection

Section "InputDevice"
	Identifier	"MX700"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event9"
EndSection

Section "InputDevice"
	Identifier	"MX500"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event8"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40 6800nu"
	Driver		"nvidia"
	 Option "TwinView"   "1"
	 Option "SecondMonitorHorizSync" "30-97"
	 Option "SecondMonitorVertRefresh" "50-180"
	 Option "MetaModes" "1024x768,1280x1024; NULL,1280x1024; 1280x1024,1280x1024"
         Option "TwinViewOrientation" "LeftOf"
         Option      "NoLogo" "True"
         Option      "DPMS"
         Option      "RenderAccel" "true"
         Option      "Coolbits" "1"
         Option      "NvAGP" "1"
         #Option "AllowGLXWithComposite" "true"
         #Option      "CursorShadow" "1"
         #Option      "CursorShadowAlpha" "64" 
         BusId       "AGP:01:00:0"
EndSection
Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	30-70
	VertRefresh	50-160
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Option "AddARGBGLXVisuals" "True"
        Device		"NVIDIA Corporation NV40 6800nu"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes	      "1280x1024" "2304x1024"  
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"MX700"
        InputDevice	"MX500" 
EndSection
```

Has anyone ever gotten two mice working on Ubuntu with evdev? Has anyone used any other method and gotten two mice with side buttons working under Edgy?

This should not be so hard. I am not a novice user. New users will not put up with this kind of hassle. Please see my poll above.

---

### Post by spockrock on 2006-10-29
umm do you have the mx500 working with udev rules, because it doesn't work for me for some reason.

---

### Post by zenwhen on 2006-10-30
> **spockrock said:**
> umm do you have the mx500 working with udev rules, because it doesn't work for me for some reason.

Actually, I don't, and mine won't.

I wound up combining the two guides I linked in the original post, and changing the .xbindkeysrc above to use buttons 8 and 9. I can finally do what I wanted to do, but it was sure harder to do than it should have been.

---

### Post by static chaser on 2006-11-07
I thinks we should be able to easily reassign the buttons to do whatever we want them too, like in Logitech Setpoint.

---

