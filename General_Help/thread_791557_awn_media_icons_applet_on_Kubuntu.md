---
title: "awn media icons applet on Kubuntu"
date: 2008-05-12
forum: General Help
---

### Post by twothird on 2008-05-12
I have a problem with AWN - media icons applet

i installed all the repositories, now I have avant-BZR running. it all works fine, but there are some applets that don't work correctly.

in order to make the 3 buttons (back, play and forward) work for amarok, i was supposed to install the library python-dcop. once i do that, the 3 buttons on awn become white lines, and don't swap back. when i remove python-dcop, they are back to normal, but I can't control the player.

i tried installing exaile, banshee and listen, but they don't work in kde. banshee actually wanted to install 350MB of additional files, I understand that is half of the gnome desktop, i don't want that.

anyway, does anyone know how to make this work?

---

### Post by twothird on 2008-05-13
Alrite.. solved it somehow.
python-dcop is needed to make this work.
I installed python-dcop after adding these lines to xorg-conf
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
[B]	Option		"AddARGBVisuals"		"True"
	Option		"AddARGBGLXVisuals"		"True"[/B]
	Option		"NoLogo"		"True"
EndSection
```

it's a rather good thing to do anyway, my compiz isn't too stable lately, seems that those lines help avoiding the white screen

---

