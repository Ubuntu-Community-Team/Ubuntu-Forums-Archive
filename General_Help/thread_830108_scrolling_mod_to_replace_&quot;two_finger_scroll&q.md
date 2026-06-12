---
title: "scrolling mod to replace &quot;two finger scroll&quot; functionality?"
date: 2008-06-15
forum: General Help
---

### Post by AlexLinuxUser101 on 2008-06-15
I have an older laptop that doesn't have neither the "two fingered scroll" nor a convenient one fingered one on the side of the trackpad (it has a dysfunctional one that stops several seconds after I want it to stop and it often doesn't work).  Is there some sort of mod that allows me to hold the Fn, ctrl/shift/alt or some other convenient combination (or allows me to make my own) and use the trackpad to scroll?

---

### Post by damis648 on 2008-06-15
By default Ubuntu should configure the trackpad to scroll by sliding you finger on the right side no matter what. If it doesn't, try circular scrolling or playing around with the settings in gsynaptics by installing it in Synaptic and going into your preferences.

---

### Post by AlexLinuxUser101 on 2008-06-15
Gsynaptics doesn't work... I get this: 
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

Is there a way to make the default "side scroller" more accurate?  Right now it doesn't stop when I want it to (it keeps going down or up after I stop scrolling).

Also, are there firefox mods that allow you to do similar things to switch tabs and make new tabs?  (For example, hold Fn and go up to make a new tab and Fn+left or right to go to the right or left tab.)

---

### Post by damis648 on 2008-06-15
To get gsynaptics to work, do the following:
Open up terminal and type (or copy and paste)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
and now
```
sudo gedit /etc/X11/xorg.conf
```
and gedit should pop up with a file to edit. Scroll down to
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
```
or something like that. Find the line in that section something like
```
Option		"SHMConfig" "false"
```
and change false to true. If this line does not exist, create it. The section should now look like something similar to:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"SHMConfig" "true"
```
and save it. Log out and log back in and try gsynaptics again.

---

### Post by unutbu on 2008-06-15
[Edit: Oops -- I didn't see damis648's post. Sorry!]

Edit /etc/X11/xorg.conf:
```

gksu gedit /etc/X11/xorg.conf
```

Find the stanza that looks something like this:

```
Section "InputDevice"
   Driver      "synaptics"
   Identifier  "TouchPad"
 EndSection

```
and change it to this:

```
 Section "InputDevice"
   Driver      "synaptics"
   Identifier  "TouchPad"
**   Option      "SHMConfig" "on"**
 EndSection
``` If you have other Options in this stanza, keep them. Just add the 'Option "SHMConfig" "on"' line.
Save and Exit.

Log out of your current X session.
Restart X by pressing Ctrl-Alt-Backspace.
Log back in.
Try running gsynaptics again.

If that does not work, we can do everything gsynaptics can by editing xorg.conf directly, but let's not try that until we have to.

---

### Post by AlexLinuxUser101 on 2008-06-15
It worked... but it still keeps scrolling after I let off the touchpad.  Also, how do I get the circular scrolling to work?

---

### Post by damis648 on 2008-06-15
In System>Preferences>Touchpad Preferences go into the Scrolling tab and check the circular scrolling box. Choose a start point (i recommend the top left corner) and try it out!

---

