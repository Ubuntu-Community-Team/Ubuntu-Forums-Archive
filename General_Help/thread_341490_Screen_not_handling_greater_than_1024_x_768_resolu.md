---
title: "Screen not handling greater than 1024 x 768 resolution"
date: 2007-01-18
forum: General Help
---

### Post by Natume on 2007-01-18
First of all, I'm going to apologize, since I imagine the more experienced people here have answered questions similar to this one before (though performing a search on the forums didn't yield the same sort of problem I'm having).  Being new to Linux (Edgy being my first distro), please bear with my lack of knowledge of the system.  That said, my issue is with the support for resolutions higher than 1024 x 768 on my monitor, which is built for (and runs at, in WinXP) 1680 x 1050 widescreen.  When I attempt to switch the monitor resolution to anything higher than the aforementioned resolution, the screen tears (that is, lots of horizontal and vertical lines, as if the image were stripped into little pieces and thrown across the screen).

All of the options I'd want to use (up through 1680 x 1050) are in the menu, and selectable (with the exception of refresh rates, but I'll get to that later), so that's not an issue.  I've tried reconfiguring xorg once, which resulted in a screen that was at 1400 x 1050 (or something) without tearing, but that crashed on attempting to switch to a different resolution ; additionally, scrolling online was laggy as hell, as if the system was operating on motherboard video.  Needless to say, I restored the old xorg configuration. 

So, basically my issue is the tearing at higher resolutions.  Being used to 1680 x 1050, and more importantly, the distortion of the image caused by fitting 1024 x 768 to a larger screen like that, is getting annoying, though I'm perfectly capable of using the system like this (at least for the moment).  Another issue is that I only have the option to use a refresh rate of 61 Hz... no other options offerred.  Now, it may be just me, but that seems like an odd refresh rate, and while I don't know what my monitor is capable of (go laptop monitor >_>), I doubt it likes that refresh too much.

If anybody know off the top of their head how to go about fixing the tearing, and the refresh rate, if that's possible, I'd love to hear so.  If not, any suggestions on how to go about trying things would help out.  I can get more information as needed, and I do apologize for rambling.

I suppose I'll work on the audio and whatnot in the interim ; give me a bit to do.  Oh, and if there are already tutorials out there on how to fix this sort of thing, please do feel free just to point me in that direction instead of writing a lengthy response.

---

### Post by tronica on 2007-01-18
What video card do you have? My guess you need to install the drivers for that card and it clear that up

---

### Post by Natume on 2007-01-18
ATI Radeon X800 Mobility.  You may be right, but I was under the impression that a number of drivers came with Edgy.  Anyhow, where would I go about getting those drivers and installing them?  From the ATI website, repositories (in which case they'd probably be third party drivers) or somewhere else?

---

### Post by majoridiot on 2007-01-18
take a look here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29)

---

### Post by allwin on 2007-01-18
I'm not an expert at this, but on two machines (one nVidia, one ATI) I was able to trim out every option on xorg.conf EXCEPT the exact color depth and resolution I wanted to run at.  I made manual edits and took out everything that didn't refer to the DEPTH and screen size.  I also found that I had to set the DPI resolution by hand to 96x96, which you can do in Gnome preferences if you hunt it down...I don't remember exactly where.  Another option I found useful was "IgnoreEdid" "TRUE" and "UseEdidDpi" "FALSE".  First one is for ATI second for nVidia.  They tell the driver NOT to rely upon the information which the monitor sends regarding its screen size and refresh rate.  I had to do this because I have a switch for my monitor to switch VGA between multiple boxes.  Perhaps some combination of this sugar sprinkled on your xorg.conf will work for you.  I have a combo HDTV/monitor that runs at 1280x768, and of five different flavors of Linux, I have yet to find ONE which offered me this resolution on its own.  I had to manually force things along.  Only caution is, my monitor will flash NOT SUPPORTED if I try to set some harmful combo of refresh rate and resolution.  I don't know what other monitors might do.  Hope this helps unlock the secrets!

---

### Post by Natume on 2007-01-18
Wow.  Well, installing the drivers worked perfectly ; didn't even have to change the settings when I rebooted - it detected them itself.  Thanks, major (using your full handle would be quite ironic, considering the situation).  I really do feel like an idiot now, but we all start somewhere I suppose {chuckles}.  Sorry for such a long post for such a simple thing.

Edit : Ah, but there appears to be a new issue ; different, entirely, but probably related to installing the drivers.  There appears to be an almost complete lack of 3D acceleration now that I've installed the fglrx drivers (granted, at the moment, 3D acceleration isn't too important, though later it will be).  Checking fglrxinfo, as the tutorial instructed, I came up with the following info :

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```

In the tutorial, the Xlib comment is left out, and it displays the drivers for the video card (i.e. ATI Radeon blah blah blah ; OpenGL v. 2, and all that jazz).  I have a feeling this is just a driver issue, but even so, exactly which drivers I need, or how to reconfigure xorg, I'm in the blue on.  Oh, and since I'm not running anything graphics-intensive, the only reason that I noticed a lack of 3D acceleration (or what I perceive to be a lack of it) is that when I locked the screen (putting me to the screensaver, just to test it out), it ran *very* chopily - at a rate of maybe 1 frame per 2-3 seconds, and obviously skipping frames, not just running at a slow pace.  Who knows, this issue may be as easy as the last, but I didn't read much in the tutorial on solving the problem aside from restoring the old xorg file.

---

### Post by majoridiot on 2007-01-18
i'm an nvidia man, but from what you are describing, i'm guessing your xorg.conf "Module"
section is missing:

```
Load "dri"
```

and that you need:

```
Section "DRI"
 Mode 0666
EndSection
```

also. make sure that you have the following:

```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```

and that if the following exists, it is commented as you see it here:

```
#Section "Extensions"
#       Option  "Composite" "Enable"         (or "1" or "True", etc.)
#EndSection
```


in any event, please post your /etc/X11/xorg.conf so we can take a look...

---

### Post by Natume on 2007-01-19
{Nods} Posting it up before having edited it ; just got up, so apologies for the long response time.

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
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
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/event2"   #USB ONLY
	Option	    "Type" "stylus"
	Option	    "USB" "on"                  #USB ONLY
	Option	    "PressCurve" "0,0,100,100"
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/event2"   #USB ONLY
	Option	    "Type" "eraser"
	Option	    "USB" "on"                  #USB ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/event2"   #USB ONLY
	Option	    "Type" "cursor"
	Option	    "Mode" "relative"
	Option	    "USB" "on"                  #USB ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Mobility Radeon X800 (R430)"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Mobility Radeon X800 (R430)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection
```

As of now, it appears that all I don't have is the extensions part.   I'll try adding that and see if it makes a difference.

Edit : Just did that, and everything appears to be working fine (at least as far as the screensaver goes.  Again... that section was explained in the tutorial, in the beginning, so this was mostly an oversight on my part.  Hopefully any further issues I have will actually require attention, and not just me paying closer attention to the documentation, eh?

---

### Post by majoridiot on 2007-01-19
> **Natume said:**
> Edit : Just did that, and everything appears to be working fine (at least as far as the screensaver goes.  Again... that section was explained in the tutorial, in the beginning, so this was mostly an oversight on my part.  Hopefully any further issues I have will actually require attention, and not just me paying closer attention to the documentation, eh?

it never hurts to have an extra set of eyes... ;)

glad you got it working!

---

