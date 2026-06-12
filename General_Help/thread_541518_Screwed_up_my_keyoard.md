---
title: "Screwed up my keyoard"
date: 2007-09-02
forum: General Help
---

### Post by treis on 2007-09-02
I installed keytouch to try and change some of my keyboard functions.  It didn't have my exact model number (HP dv2000) so I tried a similar one (HP dv1000).  Big mistake.  I don't know what it did, but my lower left control button no longer seems to be working.  Everything else seems to be fine.  Any ideas?

My Xorg.conf is: 

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

---

### Post by wolfen69 on 2007-09-02
uninstall keytouch.

---

### Post by treis on 2007-09-02
I did and it didn't fix the problem.

---

