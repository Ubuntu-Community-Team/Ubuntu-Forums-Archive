---
title: "Help with screen resolution"
date: 2007-01-18
forum: General Help
---

### Post by Papillonrus on 2007-01-18
I have installed 6.10 on a Dell Latitude LS, PIII 500, 256MB Ram, 20 GB, detached media bay.
I need assistance with the neomagic 256av video/audio device, Samsung PN: LTN121S6-T01
LCD screen. At the moment I can only use 640x480 and 800x600 @ 60 hz. with WinXP I was able to use 1024x768 w/24 bit color. I would like to use 1024x768 or to have the minimized windows to be small enough to fit on a 12.1" LCD. Any advice?](*,)

---

### Post by majoridiot on 2007-01-18
check under System-->Preferences-->Screen Resolution to see if you have higher resolutions
available. if not, then you need to make a minor change to your xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/xorg.conf.works                   <-- back it up, just in case
```
```
gksudo gedit /etc/X11/xorg.conf
```

in the editor that pops up, you are looking for a line or lines similar to:

```
Modes      "800x600" "640x480"
```

you want to change **all** occurrences of it to:

```
Modes      "1024x768" "800x600" "640x480"
```

save your changes and reboot to see what happens.  if it crashes to a terminal prompt, log
in and type:

```
 sudo cp -f /etc/X11/xorg.conf.works /etc/X11/xorg.conf
```

to restore a working config and reboot.

if you get the regular ubuntu login and the resolution hasn't changed, try setting it via the
menu as listed above.

if you do crash, or if higher resolutions are still not available, post the xorg.conf.works, the 
modified xorg.conf and your /var/log/Xorg.0.log and /var/log/Xorg.0.log.old

---

### Post by cmost on 2007-01-18
"you want to change all occurrences of it to:

Code:

Modes "1024x768" "800x600" "640x480""

Actually, you only need to change the occurrence that corresponds to your default color depth.  For example, for most people this would be 24.  Good luck!

---

### Post by Papillonrus on 2007-01-18
Here is the entries from my xorg.conf

Section "Device"
	Identifier	"NeoMagic Corporation NM2200 [MagicGraph 256AV]"
	Driver		"neomagic"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-40
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NeoMagic Corporation NM2200 [MagicGraph 256AV]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600"
	EndSubSection
EndSection

---

### Post by cmost on 2007-01-19
Is there any reason you're running a default depth of 16?  If not, I recommend you change that to 24 (assuming your video hardware is fairly recent.)  Then, scroll down to the mode line for 24 and add in your desired resolution.  If you're keeping default depth of 16, then add your desired resolution to the modeline for 16.  Save, and restart your computer.

---

### Post by majoridiot on 2007-01-19
> **cmost said:**
> "you want to change all occurrences of it to:
Code:

Modes "1024x768" "800x600" "640x480""

Actually, you only need to change the occurrence that corresponds to your default color depth.  For example, for most people this would be 24.  Good luck!

i suggested changing all of them, as no further resolution changes will 
be needed if older wine-based apps, etc. need a lower color depth.  it's 
just a good idea.

> **Papillonrus said:**
> Here is the entries from my xorg.conf

replace the existing "screen" section with this one (after you back up xorg.conf as outlined above):

```
Section "Screen"
Identifier "Default Screen"
Device "NeoMagic Corporation NM2200 [MagicGraph 256AV]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480""
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480""
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480""
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480""
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480""
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480""
EndSubSection
EndSection
```

that will set your default color depth to 24 bits and enable higher and 
lower resolutions for you. of course, restart for it to take effect.

---

### Post by Papillonrus on 2007-01-23
I was using color depth of 16 bits for smooth scrolling.  But after this reinstall I will try your suggestions and report results, Thanks

---

### Post by Papillonrus on 2007-01-23
I have changed xorg.conf as suggested. still no options other than (800x600 @60hz) and 
(640x480 @60hz)  perhaps the screen resolution gui needs to be modified also.  I had been playing with Xandros 2.0 and 1024x768 24 bit worked with Xfree86 4.x.x  .  If I can,t change the screen size.  is it possible to change the window sizes?  I believe that Ubuntu will be an 
excellent OS, competitive with Windoze.


Section "Device"
	Identifier	"NeoMagic Corporation NM2200 [MagicGraph 256AV]"
	Driver		"neomagic"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-40
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NeoMagic Corporation NM2200 [MagicGraph 256AV]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by majoridiot on 2007-01-23
> **Papillonrus said:**
> I need assistance with the neomagic 256av video/audio device, **Samsung PN: LTN121S6-T01**...

all available information i could find for that screen indicates it is native 800x600 and no
higher resolutions were listed.  at this point, i'm not sure if you can run it in 1024x768 or not.

post your /var/log/Xorg.0.log and we'll see what it says, but i don't know about this... :-\"

---

