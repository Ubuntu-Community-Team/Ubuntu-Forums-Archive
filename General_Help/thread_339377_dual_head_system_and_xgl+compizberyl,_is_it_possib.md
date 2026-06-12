---
title: "dual head system and xgl+compiz/beryl, is it possible?"
date: 2007-01-15
forum: General Help
---

### Post by rabid9797 on 2007-01-15
i haven't found any guides that warn against it, but i also haven't found any that show if xgl has dual head support.

does anybody know if xgl supports it and if you can, please point out some guides to help me here?

thanks

-rabid

---

### Post by spd106 on 2007-01-18
There are loads of videos around youtube and [ubuntuvideo]("http://www.ubuntuvideo.com/dual_monitor_xgl_in_ubuntu") with two dualview. 

I have it here at the moment. AFAIK it works best on nvidia card with aiglx and dualview (xinerama not so good). Compiz and Beryl both work great. I followed the dualview [guide]("https://help.ubuntu.com/community/XineramaHowTo") in the wiki.

Nvidia works fine for most people, not sure about ATI or Intel cards though.


I'm talking about two monitors from the same card. I'm not sure about multiple cards, I think compiz has had a lot of work done on this recently. Whether it's stable on not, I've no idea.

---

### Post by tbeld on 2007-01-18
I have an ATI X1300 and xgl+beryl is working for me with a dual-head setup exept that I only have xgl on 1 display. See my post: [http://www.ubuntuforums.org/showthread.php?t=341110&highlight=beryl](http://www.ubuntuforums.org/showthread.php?t=341110&highlight=beryl)
for the link to the guide I followed and more info.

---

### Post by VincentVX73 on 2007-06-23
I could be wrong but I think rabid9797 is looking to have two displays from the same card, each running its own beryl cube.  I recently figured out how to make that happen, albeit with a few drawbacks.  Since the two displays I'm running are different physical dimensions with different resolutions, I opted not to use xinerama (experimenting with it proved unstable anyway.)  And since I'm using an ATi card, Twinview was also out of the question.  So I setup my two screens in xorg.conf. The relevant sections are below:

```
Section "ServerLayout"
	Identifier     "Dual Monitors"
	Screen         0 "screen0"
	Screen	       1 "screen1" Relative "screen0" 2550 900
	InputDevice    "Generic Keyboard"
	InputDevice    "Logitech MX1000" "CorePointer"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Monitor"
	Identifier "Cinema HD"
	Option		"DPMS"
	HorizSync	99.58
	VertRefresh	60
EndSection

Section "Monitor"
	Identifier "Samsung"
	Option		"DPMS"
EndSection

Section "Device"
	Identifier  "ati0"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
	Screen	    0
	Option 	    "MergedFB" "True"
  	Option      "EnablePageFlip" "True"
  	Option      "AGPMode" "4"
  	Option      "AGPFastWrite" "True"
  	Option      "MergedXineramaCRT2IsScreen0" "True"
  	Option      "CRT2Position" "RightOf"
EndSection

Section "Device"
	Identifier  "ati1"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
	Screen	    1
EndSection

Section "Screen"
	Identifier "screen0"
	Device     "ati0"
	Monitor    "Cinema HD"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection

	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection

	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection

	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection

	SubSection "Display"
		Depth     24
		Modes    "2560x1600"
	EndSubSection

EndSection

Section "Screen"
	Identifier "screen1"
	Device     "ati1"
	Monitor    "Samsung"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x768"
	EndSubSection

	SubSection "Display"
		Depth     4
		Modes    "1280x768"
	EndSubSection

	SubSection "Display"
		Depth     8
		Modes    "1280x768"
	EndSubSection

	SubSection "Display"
		Depth     15
		Modes    "1280x768"
	EndSubSection

	SubSection "Display"
		Depth     16
		Modes    "1280x768"
	EndSubSection

	SubSection "Display"
		Depth     24
		Modes    "1280x768"
	EndSubSection

EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

Then to get XGL running properly on both of my screens I altered my startxgl.sh script which was formerly set up for a single monitor. 

```
#!/bin/sh
DISPLAY=:0.0
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer -br & 
DISPLAY=:0.1
Xgl :2 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer -br & 

export DISPLAY=:2
exec dbus-launch --exit-with-session gnome-session &

export DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session
```

As I mentioned before this method does have one really annoying drawback that I'm currently trying to figure out and eliminate.  Something in the way the startxgl.sh script is set up is causing the desktops to be redundant.  I don't mean they are clones of one another, but rather that any changes made on one screen are reflected on the other.  For example, desktop icons are being displayed on both screens and moving them around on one screen, moves them on the other. Another example of redundancy is the panel.  If any changes are made to the contents of one screen's panel, they are reflected on the other, ie moving the panel from the top to the bottom affects both screens.  The same is true for creating or removing a panel.  The other drawback to this dual head method is that windows cannot be moved between the displays.  The cursor can switch between the two via the shared edge, but windows are confined.

---

### Post by VincentVX73 on 2007-06-23
yikes, i just noticed how old this thread is...hope someone finds this useful anyway

---

### Post by zaebo on 2007-06-27
omg, I have searched so long for such a solution!
The first thing I will do tomorrow is do try your way,
and when it will work, you will be my personal hero! 
thank you for posting it, even the thread is old! :D

edit:
I tried it and it worked great. thank you.
but there is one strange thing: 
when I start the new xgl-session to use
both screens, I can't shut down the pc.
when I click on the red button, to shut down,
the option is missing. reboot is also missing.
strange thing =(

---

### Post by alexei.colin on 2008-05-28
Hi guys,

This post is old, but that is only a good thing: if the title was possible then, it should be possible today! I have dual heads working in metacity, and am trying to move to dual-heads with compiz.

My system is: Ubuntu 8.04 with fglrx 8.05 on Thinkpad T60 (Radeon X1400).
I am using xorg.conf modeled after the one above -- it works for dual-heading in metacity. 

With xserver-xgl package installed, the second screen is on, but blank and with a cross-icon for the mouse. The primary screen is well with compiz effects.

So, is startxgl.sh supposed to be run automatically? I did not have it on my system. I created it with the code above. When I run it manually, the system freezes completely after printing a message saying that I am already running an Xgl session.

Thank you in advance!!

---

