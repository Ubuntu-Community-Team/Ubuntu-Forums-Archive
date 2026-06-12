---
title: "3rd Level choosers"
date: 2008-05-20
forum: General Help
---

### Post by ricardisimo on 2008-05-20
I've been replying like a dummy to [this thread]("http://ubuntuforums.org/showthread.php?t=437214") in the archives and wondering why a.) no one was responding, and b.) my post wasn't appearing in this forum. Fool me twenty-seven times, shame on... someone.

Basically, I'd like to know how to edit keyboard settings in Kubuntu 8.04, so as to make either ALT key a 3rd level chooser, as I had it in Ubuntu 7.04. This seems to be a rare instance where KDE has less modifiable options than Gnome. Here's the pertinent lines from my xorg.conf:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"altgr-intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
```
What would that last line look like with both ALT keys activated as 3rd level switches? Thanks in advance.

---

