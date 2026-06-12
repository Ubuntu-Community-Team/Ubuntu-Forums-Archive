---
title: "Num keys commas dashes dont work after upgrade!"
date: 2007-11-04
forum: General Help
---

### Post by ltk5 on 2007-11-04
Ive successfully upgraded to Gutsy_ I did have some problems with my intel graphic card; but I 
solved them thanks to [this]("http://ubuntuforums.org/showthread.php?t=581364&highlight=intel+chipset+graphic+card+resolution") post_
Now  I have another problem:_ When I press on my keyboard a number thats not on the Num pad; 
nothing happens_ The same goes for full stops commas___ I can however use the characters that I 
can normally use when I press the Shift key_ (underscore #$%& and these signs)_

I checked xorg_conf and the keyboard map seems fine:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"sl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
```

Any suggestions on how to solve this? Thanks!

---

### Post by ltk5 on 2007-11-04
I also noticed that in the beginning I get a window asking me whether I want to choose the keyboard
settings from Gnome or from X


Edit. One thing I also noticed. As I was searching for a way to manually change my keyboard layout, I 
found this (2 screenshots below). I can change it to US, and it works fine, but if I change it to SL/HR
I get all sorts of special character instead of the alphabet.

[img]http://h1.ripway.com/lotko05/lotko/forum/ubuntuforums/razpored.tipk.jpg[/img]

[img]http://h1.ripway.com/lotko05/lotko/forum/ubuntuforums/kezboard.layout.jpg[/img]

---

### Post by ltk5 on 2007-11-06
I tried changing keyboard settings for Gnome; but they look alright
Where could be the problem?

---

### Post by ltk5 on 2007-11-07
bump

---

### Post by SyL on 2008-05-15
I had the same issue after upgraded.
I solved it doing the following:

Go to Preference / Keyboard / Mouse key 
disable  Allow to control the pointer using the keyboard

---

