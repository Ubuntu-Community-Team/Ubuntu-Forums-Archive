---
title: "huge login screen res"
date: 2008-05-10
forum: General Help
---

### Post by bandofmercy on 2008-05-10
with 7.10 i was working in 800x600 resolution (after trying in vain for a year to get something higher for my cheap via chrome9 hc igp).  it was ugly but pretty much worked.  now with 8.04 i have a much prettier resolution 12something by something, but my login screen is HUGE.  I can only see the upper left corner.  same goes for the booting ubuntu logo and loading bar... it is like i can only see the upper left corner of the screen, with the login/loading area (that should be the center of the scree) in the lower right.  this also means i can't click the buttons for my session, shutdown, etc.  how can i change my login/boot resolution?

as a side note, my xorg.conf doesn't seem to have any driver listed, nor can i find a gui applet that allows me to manage drivers.  what gives?

---

### Post by X-dark on 2008-05-10
the resolution used for the login screen is the first listed in your screen resolution of your xorg.conf.

---

### Post by bandofmercy on 2008-05-10
> **X-dark said:**
> the resolution used for the login screen is the first listed in your screen resolution of your xorg.conf.

so where would that be on here?  like i say, my xorg doesnt seem to have as much listed as it did in the past.

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"alt-intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by X-dark on 2008-05-10
If you have an Nvidia card this is in fact a known bug.
Try this :
```
sudo dpkg-reconfigure xserver-xorg
sudo nvidia-xconfig
```

The bug is documented here : [GDM login screen too wide]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/214704")

---

### Post by stream303 on 2008-05-10
Huge login screens can sometimes be cured by using the -Virtual- option in xorg and making it the same size as your desired resolution on the desktop.

Here's a snippet from my manually edited /etc/X11/xorg.conf on Hardy:

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
  [b]SubSection "Display"
      Virtual 1680 1050
  EndSubSection[/b] 
EndSection
```

---

### Post by bandofmercy on 2008-05-11
> **stream303 said:**
> Huge login screens can sometimes be cured by using the -Virtual- option in xorg and making it the same size as your desired resolution on the desktop.

Here's a snippet from my manually edited /etc/X11/xorg.conf on Hardy:

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
  [b]SubSection "Display"
      Virtual 1680 1050
  EndSubSection[/b] 
EndSection
```

boo ya!  someday i hope to get some basic desktop effects working with my chrome9 hc but thanks to you it will be at least another month before i ruin my computer again thank you thank you

---

### Post by jocko_johnson on 2008-05-12
To Stream303 - 
Thank you so much for that fix re: login screen resolution.  my text was all fuzzy and I couldn't figure out how to fix it. 

I put the Subsection lines of code you posted and it worked perfectly.
Thanks a lot.

---

