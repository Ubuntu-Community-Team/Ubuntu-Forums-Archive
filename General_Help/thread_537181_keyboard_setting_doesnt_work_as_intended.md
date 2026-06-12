---
title: "keyboard setting doesnt work as intended"
date: 2007-08-28
forum: General Help
---

### Post by conehead77 on 2007-08-28
I cannot use square brackets, the dollar sign, etc. It all worked before, but i cant get it work now.
The tray icon shows "USA", but the xorg.conf shows "de":

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbOptions" 	"compose:ralt"	
	Option		"XkbVariant"	"nodeadkeys"
EndSection

I thought the "compose:ralt" option is there to be able to use the right alt key to get the special signs?

Is there another file like xorg.conf that i need to modify to get my square brackets back?
I tried some settings in the keyboard GUI, but they dont seem to have any effect :(

---

### Post by conehead77 on 2007-08-28
bump

general information about how the keyboard configuration works would also be helpful :)

---

