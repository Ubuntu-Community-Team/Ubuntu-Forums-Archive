---
title: "Keyboard settings message when my computer starts"
date: 2007-10-24
forum: General Help
---

### Post by Mateo on 2007-10-24
This has happened ever since I upgraded to Gutsy.  The screenshot says it all.  No matter which option I choose, it still does it the next time I restart.

---

### Post by por100pre1 on 2007-10-25
Your keyboard setups in xorg.conf and gnome don't match.

Setup keyborad and language in Gnome:

```
gnome-keyboard-properties
```

Do the same in xorg.conf:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

```
gksudo gedit /etc/X11/xorg.conf
```

Look for something like this:
[I]
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
[/I]
Correct **Option "XkbModel" "pc105"** and **Option "XkbLayout" "us"** to match the number of keys and language of your Gnome configuration.

Hope it helps. :)

---

### Post by Mateo on 2007-10-25
weird, but they already match:

```
Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection
```

---

### Post by por100pre1 on 2007-10-25
Weird. When you login select to use the X settings then look xorg.conf to see the keyboard settings again. Are you actually using a 104 key keyboard? :-k

---

