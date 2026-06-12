---
title: "rmb + lmb = mmb?"
date: 2007-05-18
forum: General Help
---

### Post by FunkyMunky on 2007-05-18
hi. i'm using xubuntu 7.04 and i just managed to install quake 3, mod rocket arena and xqf to join multiplayer games. everything works fine, except that there's this annoying feature that seems to be built into xubuntu, that pressing left mouse button and right mouse button at the same time acts as if i was pressing middle mouse button. becouse of that, in quake, i can't jump and shoot at the same time :(

so can someone please tell me how to disable this feature?

---

### Post by aldenhg on 2007-05-18
You need to edit your /etc/X11/xorg.conf file. Look for the Mouse section and remove or comment out (put a # at the beginning of the line) the line the says Emulate3Buttons. Restart your X server (hit ctrl-alt-backspace - save your work first!) and you should be good to go.

---

### Post by FunkyMunky on 2007-05-19
emulate3buttons seems to be already enabled:confused:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

yet rmb+lmb acts like mmb.

---

### Post by FunkyMunky on 2007-05-19
nevermind it works now. thanks!

---

