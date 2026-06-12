---
title: "Synaptics Touchpad | Toshiba m115"
date: 2007-04-29
forum: General Help
---

### Post by funnyguyfunnyguy on 2007-04-29
I justed installed Ubuntu 7.04 on my Toshiba m115 laptop. Things are working much better than in the past. However, I am having issues with my touch pad. It isn't nearly as accurate as it is under windows, which uses the synaptics driver. I have done some reading, which refers me to my Xorg file and recommends that I modify the "synaptics" section; however, I don't have a "synaptics" section. I also installed "qsynaptics," which I believe interacts with the synaptics driver/Xorg file, but since I don't have a synaptics driver it won't run.

How do I install the synaptics driver?

Should I be adding a section in my Xorg file?

Any thoughts?

---

### Post by strabes on 2007-04-29
Add this to the ServerLayout section in your xorg.conf: > 	InputDevice    "Synaptics Touchpad"

Add this to the bottom of your xorg.conf: > Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "SHMConfig" "true"
	Option	    "MaxTapTime" "150"
	Option	    "MaxDoubleTapTime" "150"
	Option	    "VertEdgeScroll" "1"
	Option	    "HorizEdgeScroll" "1"
EndSection

Save the file and restart your X server with Ctrl+Alt+Backspace. If you want to disable tap-to-click, just change MaxTapTime and MaxDoubleTapTime to 0.

---

### Post by Tripletaco on 2007-04-30
FunnyGuy,  This is my first time to reply here on the ubuntu forum.  I was working on the same problem on my Toshiba M115-S3094 today.  When I tried running gsynaptics it said I needed to have SHMConfig set to "true".  I spent a lot of time trying to get to the xorg.conf file.  Once there I tried pasting something similar to what Strabes suggested, but it said xorg.conf was read only.  Never could figure out how to modify that file.  Tried being su, but I really don't know what I'm doing.  Maybe I'll get some help here.

Strabes,  how do you modify xorg.conf?  I'm a newbie, Just learning Linux and enjoying it.=)

Paul

---

### Post by funnyguyfunnyguy on 2007-04-30
This fix worked great for me.

Maybe this will help you.
Open the terminal and type:

> sudo gedit /etc/X11/xorg.conf

Then find the section labeled "serverlayout." I just searched for it. (It is the first section that comes up when you search.)

Then I added:

> InputDevice 	"Synaptics Touchpad"

To the bottom of the list. (Order doesn't matter here.) This is what mine looks like.

> Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice 	"Synaptics Touchpad"
EndSection

Then, at the bottom of the page, I pasted the following:

> Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "SHMConfig" "true"
Option "MaxTapTime" "150"
Option "MaxDoubleTapTime" "150"
Option "VertEdgeScroll" "1"
Option "HorizEdgeScroll" "1"
EndSection

Next, save the file and close gedit. Press ctrl+alt+backspace and you should be in business.

---

### Post by Tripletaco on 2007-05-01
Funnyguy,  THANK YOU VERY MUCH!!!!! 

It worked for me.  I've been struggling with this a while.  I added every thing you said except for: 

Option "MaxTapTime" "150"
Option "MaxDoubleTapTime" "150"
Option "VertEdgeScroll" "1"
Option "HorizEdgeScroll" "1"

Under Section "InputDevice"

Now that my touchpad scrolls I can move on to bigger and better things. Yea!!!!!

---

### Post by tcouto on 2007-05-07
well... the clues stated above helped  a lot, but didnt quite do it for me!!
this settings worked fabulous:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "SHMConfig" "true"
Option "MaxTapTime" "300"
Option "MaxDoubleTapTime" "300"
Option "Minspeed" "1.00"
Option "Maxspeed" "1.00"
EndSection

By the way... my notebook is a sony vaio vgn-c1s

ubuntu forum rules!!

---

