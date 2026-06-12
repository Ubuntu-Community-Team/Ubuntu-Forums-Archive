---
title: "Back/Forward mouse buttons are switched in Firefox"
date: 2008-04-02
forum: General Help
---

### Post by benmarvin on 2008-04-02
I know there has to be a simple fix for this, but I don't want to go playing with xorg.conf and mess up something even further. 
The Left side button on my mouse goes forward, and the Right one goes back. How do I switch this? I have the mousewheel.horizscroll.withnokey.action set to 2, but there's no setting for which does which. I'm not running imwheel or anything.

I know I'm supposed to post in the Hardy section, but I don't think this issue is isolated to Hardy.

Here's the relevant section of my xorg.conf:
> 
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Emulate3Buttons"   "false"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"       "6 7"
EndSection


---

### Post by luceerose on 2008-04-03
See how you go with this;

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ButtonMapping"	"1 2 3"
	Option		"ZAxisMapping"	"4 5"
	Option		"YAxisMapping"	"6 7"
	Option		"Emulate3Buttons"	"false"
	Option		"Resolution"	"800"
EndSection

For "Resolution", I have written "800" for you. If your mouse has a different dpi change this number to suit. Most mice are 400 or 800. I have a Gigabyte laser gamers mouse. It is 1600.

This layout will give us an indication of where your buttons are mapping.
If it ends up worse, just revert to your original text and we'll go from there again.

---

### Post by erginemr on 2008-04-03
The following thread:
[http://ubuntuforums.org/showthread.php?t=28374](http://ubuntuforums.org/showthread.php?t=28374)

post #10 suggests:
```
Option "ZAxisMapping" "4 5"
```

I can alternatively suggest you to install "All-in-One Gestures" Firefox plugin:
[https://addons.mozilla.org/en-US/firefox/addon/12](https://addons.mozilla.org/en-US/firefox/addon/12)

to use mouse dragging (such as right-click and drag left for history back and drag right for history forward) while browsing.

---

