---
title: "Video and opengl apps overlays on Ati Mobility Radeon HD2400 (laptop)"
date: 2008-03-13
forum: General Help
---

### Post by hafter on 2008-03-13
Hello people !

First of all excuse my english !

I'm posting this becouse i want to use ubuntu as my default setup but this compiz bug is killing me.

The bug is that in compiz mode or with another compositor manager (xcompmgr, xfwm4) the opengl apps and the video playback is always flickering no matter what videoplayer or gl-game i use and the window content of a gl/video app is always flickering on top leaving imposible to launch any app onto top.

**Video card: **
Ati Mobility Radeon HD2400 (laptop)

**Video of the bug:**
[http://www.youtube.com/watch?v=Rb1TphavJZI](http://www.youtube.com/watch?v=Rb1TphavJZI)

**What i tested:**
[LIST]
[*]various officiial ati drivers (actual version and previous versions)
[*]manual officiial ati driver installation
[*]automatic officiial ati driver installation
[*]making packages of the officiial ati driver installation
[*]making the module flgrx from the source
[*]repllacing "fglrx" with "radeon" or "radeonhd" in the xorg.conf driver section
[*]single head
[*]dual head
[*]lots of distros
[*]xgl (it overwrites libgl with the mesa one ... works well without flickering but horrible slooooow)
[*]lots of xorg.conf configurations
[*]ubuntu fglrx drivers (restricted, xorg-fglrx-driver, etc)
[*]ubuntu gutsy
[*]ubuntu hardy
[/LIST]

xorg.conf:
```
Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbVariant" "intl"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option	    "DesktopSetup" "horizontal,reverse"
	Option "TexturedVideo" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen"
	Device     "aticonfig-Device"
	Monitor    "aticonfig-Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x800" "1024x768" "800x600"
	EndSubSection
EndSection

```

Please help me or post here you experience with a similar bug.

Thanx to everybody !

---

### Post by hafter on 2008-03-13
Here's an interesting reply 

[http://forum.compiz-fusion.org/showthread.php?t=7471](http://forum.compiz-fusion.org/showthread.php?t=7471)

---

### Post by john-d on 2008-03-19
I've got the same card on a laptop, and I have to say I would actually be happy if that was my only problem, I experience some flickering as you do with compiz running, but I also experience very mild flickering while watching videos without any composite application running and with about any driver I tried (especially when there is a lot of movement). If you used to have the same problem and found a solution it would be nice for you to say how you did it. For you're problem, what I would do is set a keyboard shortcut for compiz and one other for metacity (or kwin if you use kde), and you'd  just have to type, for example, ctrl+alt+m to watch a video and play games (using metacity) and then to come back to compiz press ctrl+alt+c. It doesn't solve you're problem, but it makes it less annoying.

---

