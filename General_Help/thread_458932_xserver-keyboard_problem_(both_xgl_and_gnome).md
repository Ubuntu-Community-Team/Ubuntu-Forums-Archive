---
title: "xserver-keyboard problem (both xgl and gnome)"
date: 2007-05-30
forum: General Help
---

### Post by mulino18 on 2007-05-30
Hi!

first problem: gnome session:
after last updates (there were a bunch... HAL and kernel might be the cause of the problem?)
my keyboard settings were messed up. 
(I work on a dell inspiron 6400 with a german kbd), the alt gr key is no longer active.

I tried the solutions proposed in various forums, e.g. editing xorg.conf to :

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "de"
	Option	    "XkbOptions" "lv3:ralt_switch" --->this is for the alt gr I guess??
	Option      "XkbDisable" "true"
... no effect. :0(
someone suggested to replace Driver ``keyboard'' by ``kbd`` (what does this really do??)

Then, second problem, now whenever I launch my XGL session (for beryl), the xserver goes crazzy, display complettely blurred... (even whent booting under previous .15 kernel)

Thanks for help

---

