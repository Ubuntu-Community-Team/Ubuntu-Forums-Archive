---
title: "Switching languages"
date: 2007-03-27
forum: General Help
---

### Post by Slimshady on 2007-03-27
Hi, i have kubuntu, and i cant switch languages with alt+shift. i tried everything but nothing works. 
i even saw a bug report for this problem:
[http://bugs.kde.org/show_bug.cgi?id=99009](http://bugs.kde.org/show_bug.cgi?id=99009)
and i followed the solutions suggeted there and i still cant switch languages  no matter what key combination i try,

---

### Post by PurplePenguin on 2007-03-27
I'm using gnome under Edgy, just in case what you see doesn't exactly match up.

**This first option is for gnome and probably won't help you.**  
I'm not sure how it works with Kubuntu, but in gnome, the first thing to try is the simple way: Go to System - Preferences - Keyboard.  Click the Layout tab, and make sure that your other language is there.  Then go to Layout Options - Group Shift / Lock Behavior and select which hotkey combo you'd like to switch the languages (I like "Alt + Shift changes group").

I'm not sure if you need to restart X for the changes to take effect.  It's been a long time since I've done it.

If this doesn't work, which I'm sure it won't (since you're using Kubuntu), you can always manually make the change in your xorg.conf.

Here's the section in mine that switches from English to Russian:
> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us ru"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Before messing with this file, make sure it's backed up.  XkbLayout is where my two languages (US English and Russian) are listed.  XkbOptions looks like it's the ALT+Shift combo.

If you don't want to do this by hand, you can reconfigure your whole xserver (make sure you know your monitor's specs before going through with this) by typing (I'm going from memory, please double check this before actually trying it): sudo dpkg --configure -a

It'll also ask for keyboard layouts.

---

### Post by Slimshady on 2007-03-27
i already added my layout, and chose the alt+shift combo, and  tried more thousand things and nothing help. i can switch onli from english  to hebrew (my lang), with another combo, alt+shift doesnt work. (exactly as described in the bug report's comments).  

this section on my xorg file looks like yours, except 1 this line (in my file):
Option "XkbLayout" "us"
which i edited to:
Option "XkbLayout" "us il"
and i rebooted my computer, and still the same........

btw i also have gnome which works fine. but i prefer the kde.

---

