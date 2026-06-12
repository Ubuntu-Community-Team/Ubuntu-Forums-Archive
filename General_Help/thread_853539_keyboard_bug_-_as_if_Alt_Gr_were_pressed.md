---
title: "keyboard bug - as if Alt Gr were pressed"
date: 2008-07-08
forum: General Help
---

### Post by 11wizard on 2008-07-08
Hi,

I seem to have a keyboard problem. Since upgrading to Hardy, every time I boot up the letters come out as if Alt Gr were constantly pressed (luckily I had it set to automatic login). The only way I can resolve this is by going into Keyboard Preferences and changing the keyboard model, after which it works until the next time I start up Ubuntu, when it does the same. 

I have a Labtec Standard Keyboard Plus and my /etc/X11/xorg.conf file is 

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"hu"
EndSection

Thank you

---

