---
title: "Uneven Screen Resolutions with BigDesktop (ATI)"
date: 2008-06-02
forum: General Help
---

### Post by krazykirk on 2008-06-02
Hey Guys,

I'm trying to get dual monitors to work, and I have configured Big Desktop to enable both monitors so I can display different things on each monitor. The problem is, I would like both monitors to be running at the optimum resolution of 1280x1024, but my first monitor is running at 1024x768 and the second is running at 1280x1024.

Here is my xorg.conf file.


```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "HSync2" "30-82" #This sets the horizontal sync for the secondary display. 
        Option      "VRefresh2" "56-76" #This sets the refresh rate of the secondary display.

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24 
	SubSection "Display"
	Virtual   1280 1024 
                Viewport  0 0
        Depth        24
        #Modes    "2560x1024" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

I think I may have screwed it up by trying multiple methods, but I have been reasonably careful. If I have made an error in my file, please tell me.

Thanks for your help!

---

### Post by krazykirk on 2008-06-03
I think the problem is probably in my xorg.conf file. Fglrx seems to be set up properly, fglrxinfo shows the video card instead of mesa, so it seems to be set up correctly.

---

### Post by Jagal on 2008-06-13
Hi!

I'm facing the same problem. I have one screen (internal laptop) with a resolution 1280x800 and an external screen resolution 1280x1024. I have big desktop, but the resolution is 2560x800 what results in a contorted picture on the external monitor.

I have the fglrx driver installed and it seems to work alright.

Would be great if somebody could help... I already working and trying a couple of days now on my xorg.conf.

Your
Jagal

---

### Post by krazykirk on 2008-06-13
I managed to fix my problem by forcing the types of monitors.

I used "aticonfig --force-monitor=ttds1,ttds2"

Or something to that effect. Somehow, my setup is now working without focusing, so I am not touching my xorg.conf anymore!

I'm pretty sure you just need to replace the ttdses for the correct type of monitors you have.

---

