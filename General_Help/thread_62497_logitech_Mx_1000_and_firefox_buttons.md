---
title: "logitech Mx 1000 and firefox buttons"
date: 2005-09-04
forum: General Help
---

### Post by Digitallysick on 2005-09-04
I saw a post a while back with a way to setup the forward and back buttons, can someone point me in the direction of this? thanks

---

### Post by woedend on 2005-09-05
open terminal and type:
sudo gedit "/etc/X11/xorg.conf"

enter password and push enter.  Make your mouse section look like this, save, reboot.

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"ZAxisMapping"		"4 5"
	Option		"Buttons"		"8"
EndSection
```

The Buttons option and emulate3buttons option are pretty much useless for time being, the main thing is to make sure ZAxisMapping is set right for scroll wheel, and change IMPS/2 to ExplorerPS/2

---

