---
title: "Super key issues"
date: 2007-09-19
forum: General Help
---

### Post by ThomThom on 2007-09-19
I'm pretty new to Ubuntu. I'm finding some oddity with some of the hotkeys.

For instance; the Compiz Preferences -> Utility in the Annotate section, it says to use ALT+SUPER+Button1 to start annotate. But to me it starts when I just press ALT+Button1. It triggers even if the SUPER button isn't pressed. (SUPER I've figures is the Win, button yes?)
If I press ALT+Super+Button1 it's as if it's a regular Button1 click. What gives?

And sometimes I see references to a META key. What's that?

---

### Post by bunker on 2007-09-19
Meta refers to ALT or ESC usually.

If the super key doesn't work properly, probably your keyboard is set up wrong in xorg.conf.

In the keyboard section you need:
  Option    "XkbModel"  "pc105"

Mine looks like this in total:
```

Section "InputDevice"
  Identifier  "Generic Keyboard"
  Driver    "keyboard"
  Option    "CoreKeyboard"
  Option    "XkbRules"  "xorg"
  Option    "XkbModel"  "pc105"
  Option    "XkbLayout" "gb" # uk qwerty layout
  Option     "XkbOptions" "lv3:ralt_switch"
EndSection

```

---

### Post by ThomThom on 2007-09-19
This is from my xorg.conf file:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"uk"
EndSection

```

Also, I use a Norwegian Logitech keyboard and from Keyboard settings I tried to add a norwegian layout and the Logitech model.

When I added the norwegian layout I got:

Error activating XKB configuration.
It can happen under various circumstanses:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilites)
- X server with inompatible libxkbfile implementation

Xserver version data:
The X.Org Foundation
70200000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
-The result of gconftool-2 -R /desktopx/gnome/peripherals/keyboard/kbd

Same error occurred when I tried to add the Logitech keyboard model. 
And now I get the message each time I start up.

xprop -root | grep XKB returned:
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "uk", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "uk", "", ""


gconftool-2 -R /desktopx/gnome/peripherals/keyboard/kbd returned:
 layouts = [uk,no]
 model = logicdit
 options = [grp grp:alts_toggle]
 overrideSettings = true

---

### Post by ThomThom on 2007-09-19
The super key issue was there before I changed the keyboard layout.

---

### Post by bunker on 2007-09-19
Try switching   
  Option    "XkbLayout" "uk"
to:
  Option    "XkbLayout" "no"

The error message is pretty unhelpful but it might be because you had 'uk' in there.  'no' is for the Norwegian layout; mine is 'gb' for Great Britain (I'm not sure 'uk' is a vaild layout at all).  

You should not need to put anything about logitech in there.  Keyboard drivers are pretty generic.  Standard pc105 should do you fine - works with volume, start/stop/pause keys and so on as well as the super.

---

### Post by ThomThom on 2007-09-20
doh! yes! I removed the uk entry from the Keyboard list and added Norwegian and United Kingdom. Now it works fine.
The issue with the Super key is gone as well.

I dunnu why, but I keep thinking 'uk' instead of 'gb'. Thanks mate!

---

