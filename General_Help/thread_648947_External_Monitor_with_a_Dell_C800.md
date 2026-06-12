---
title: "External Monitor with a Dell C800"
date: 2007-12-24
forum: General Help
---

### Post by imho74 on 2007-12-24
Hello,

did anyone gets an external Monitor on a Dell Latitude C800 working? It has worked with Feisty but since I have installed Gutsy the external Monitor is still black when I press FN + F8

This is the intersting part of my xorg.conf:

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage Mobility M4 AGP"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

```

Maybe someone has done this successfully?

Regards,
imho

---

