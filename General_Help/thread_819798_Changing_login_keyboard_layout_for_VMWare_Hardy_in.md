---
title: "Changing login keyboard layout for VMWare Hardy install"
date: 2008-06-05
forum: General Help
---

### Post by seeker1458 on 2008-06-05
Hey guys, I just rebuilt a machine and loaded xp pro on it.  I loaded VMWare server on in and installed the Hardy w/ vmtools pre-configured virtual machine.  The keyboard is set to a German keyboard, and I being English speaking, have issues finding certain characters. I know I need to change the xorg.conf file, but how do I know what to put in there?

this is what I've got currently:
```
Section "InputDevice"
	Identifier	"VMware Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
```

I am using a standard Microsoft Internet Keyboard.  I tried changing the "de" to "en"...didn't work.  Anyone else run into this?

---

### Post by seeker1458 on 2008-06-06
bump

---

