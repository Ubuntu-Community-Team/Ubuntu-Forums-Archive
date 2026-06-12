---
title: "Dual Monitor setup back to front"
date: 2006-10-23
forum: General Help
---

### Post by robtrev on 2006-10-23
Hi,

I have a new ATI grpahics card with the fglrx drivers and 2 monitors which are all now  working correctly

Is there a way to set what side the second monitor is on?  I.e. I am currently dragging things off the right hand side to the second monitor but would quite like to set it up so I drag things off to the left hand side to the second monitor (swapping monitors is not an option).  I tried looking through the xorg.conf but nothing jumped out.

Thanks for any help

---

### Post by mbeierl on 2006-10-23
Please post your xorg.conf file.  But off the top of my head, in xinerama layout, your ServerLayout section specifies the position like so:

Screen 0 "MonitorOne" 0 0
Screen 1 "MonitorTwo" RightOf "MonitorOne"

Using MergedFB it's something like:

Option "CRT2Position" "LeftOf"

You can find more info here:

[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by robtrev on 2006-10-26
Hi,

Thanks for your help, still having a little trouble.  The things I have tried either result in both my screens turning green (and having to reboot into single user mode / text to restore my xorg.conf) or have had no effect.  I think there could be something wrong with the declaration of my monitors, I dont know, but here are the monitor sections of my xorg.conf:

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0

	#Option "Xinerama" "on"
	##Option "Clone" "off"
EndSection

Section "Monitor"
	Identifier   "DELL 1703FP"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
        Monitor    "DELL 1703FP"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
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


```

Have removed some of the non-monitor things for ease.

Would appreciate anyhelp, cheers.

---

### Post by robtrev on 2006-10-27
This was one of my attempts using the link provided that did not crash with a green screen, although the LeftOf RightOf is having no effect :(

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Primary Screen" 0 0
	Screen      1  "Secondary Screen" LeftOf "Primary Screen"
	
	#Option "Xinerama" "on"
	##Option "Clone" "off"
EndSection

Section "Monitor"
	Identifier   "Primary Monitor"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "Secondary Monitor"
	Option	    "DPMS"
EndSection

Section "Device"
        Identifier  "Primary Driver"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Device"
        Identifier  "Secondary Driver"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Primary Screen"
        Device     "Primary Driver"
        Monitor    "Primary Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "Secondary Screen"
        Device     "Secondary Driver"
        Monitor    "Secondary Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
EndSection


```

Noticed the the fglrx drivers might have options to do things in,not sure, the fun continues...

Cheers

---

### Post by robtrev on 2006-10-30
The fglrx gui config app does not work as well, something about the xorg.conf not being well formed :/

---

### Post by dave_blob on 2006-10-30
gday mate! I had the same problem.
Theres a lot of misinformation floating around on the internet, a lot of X settings that people tell you to use that do nothing. 

If you really have fglrx drivers, what you want to use is ATI's bigdesktop feature. 

None of this:
[I]Screen 0 "MonitorOne" 0 0
Screen 1 "MonitorTwo" RightOf "MonitorOne"

Using MergedFB it's something like:

Option "CRT2Position" "LeftOf" [/I]

will help you. 

Lets clear up some confusion. **You dont need two screen sections, or two device sections**. One screen, one device and the option:
        Option      "DesktopSetup" "horizontal, reverse"

The driver will assume you have a second screen **of the same resolution** plugged in and will extend the desktop onto it. 
It took me forever to find that information, it only applies to the proprietary ati driver.

So taking a shot at cleaning up your xorg.conf(I got rid of all your extra depth modes too, no real need for them)....
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen        "Primary Screen" 0 0
EndSection

Section "Monitor"
	Identifier   "Primary Monitor"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
        Identifier  "Primary Driver"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal, reverse"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:2:0:0"  #might not need this
EndSection

Section "Screen"
        Identifier "Primary Screen"
        Device     "Primary Driver"
        Monitor    "Primary Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" " 640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option "Composite" "0"
EndSection

```

Had to add those two bits on the end to make sure direct rendering (DRI) will work. 

Make sure you change  BusID to the busid of your card!

Give it a shot, thats pretty much my xorg.conf and it works great :)

---

### Post by robtrev on 2006-10-30
:D,  works perfectly now.  Yeah the ati bit / 'horizontal, reverse' hit the spot.

Thanks very much for your help/time + cleaning it up :D

---

### Post by DC@DR on 2006-10-30
But how to make both monitors using the fglrx drivers if they have different resolutions (first is 1400x1050, second is 1280x1024)? I'm stuck in this case. I got fglrx works perfectly one one monitor, but when I use ATI control panel to set the big desktop, then I couldn't use fglrx driver any more on both screens, it's changed automatically to Mesa drivers...How to overcome this?

---

### Post by dave_blob on 2006-10-31
glad to hear it works robtrev

if you want to run the fglrx drivers, i dont think you can have monitors of different sizes, if you want a bigdesktop.

You can set them up in dual head mode, but each screen will be a seperate X session and you wont be able to drag windows betweeen them.

I heard somewhere that ati might be/or already have included support for this in a very recent driver, so you could look into that. someone want to clarify this?

But otherwise, is it so bad to have both at 1280x1024? :P

---

