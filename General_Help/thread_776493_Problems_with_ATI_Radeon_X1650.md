---
title: "Problems with ATI Radeon X1650"
date: 2008-04-30
forum: General Help
---

### Post by Eldhelrim on 2008-04-30
Hi! I've just updated from 7.10 to 8.04 and I'm having problems with the graphic. Everything goes stumbling... I have an ATI Radeon X1650.

After updating to 8.04, the ATI privative drivers' where inhabilited, but I've reactivated them... I've also reinstalled xserver (and dpkg-reconfigure), ati drivers, and compiz. But nothing seems to work... 

Any idea? 

Thanks

If necessary, I post my xorg.conf here:
```


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

---

### Post by reclinerspud on 2008-04-30
look up "envy" in synaptic it worked for me. I have ATI 1600. just download and install it will config for you.

---

### Post by Saint Angeles on 2008-04-30
this looks like you need my "mini ATI tutorial"

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

good luck!

---

