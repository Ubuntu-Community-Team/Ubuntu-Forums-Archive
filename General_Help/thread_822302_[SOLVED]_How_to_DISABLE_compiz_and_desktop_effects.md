---
title: "[SOLVED] How to DISABLE compiz and desktop effects???"
date: 2008-06-08
forum: General Help
---

### Post by brett123 on 2008-06-08
NEVER MIND I FIGURED IT OUT - ALL OK NOW. BUT I CAN'T DELETE THIS THREAD - SORRY MR MODERATOR :(


So, I've been a bad boy and been sudo'ing (from various Google results) all afternoon trying to get the desktop cube... finally did, but then realised my computer isn't fast enough to make this stuff work, so I want to turn it all off. Go back to where I was this morning - but I can't.

I don't remember what I did to make it all work, but I've tried to:
- uninstall compiz through Synaptic
- right click desktop and choose no visual effects
- untick everything in Preferences-AdvancedDesktopSettings

Reboot, reboot, reboot...

But still all my windows are slow to drag around, my browser has some fancy effect when opening (like a Powerpoint presentation), and so forth.

I just wanna turn it ALL OFF.

Please help! What can I do? My computer is so slow now. I've learnt my lesson, won't play anymore :(

---

### Post by brett123 on 2008-06-08
I did all this. Please help me UNDO all this:

sudo aptitude install ubuntu-restricted-extras

sudo aptitude install compizconfig-settings-manager

SKIP_CHECKS=yes compiz

sudo apt-get install xserver-xgl

---

### Post by didac on 2008-06-08
Post the results of:

```
cat /etc/X11/xorg.conf
```

Type it in a terminal, copy and paste

---

### Post by brett123 on 2008-06-08
Thanks for reply, I think I got it all though (I just did a PURGE for all the above installs). But, here is that output in case I've screwed something else:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by didac on 2008-06-08
It's OK. Don't see anything wrong

---

### Post by brett123 on 2008-06-08
Thank you. It appears all back to normal. At least there is no delay in dragging things. Me computer is quite old, and I'm getting a new one soon - which is why I just installed Ubuntu to TRY. My logic was IF it stuff my computer I didn't care, just buy a new one. But, several weeks into Ubuntu and totally loving it. Shoulda made the switch earlier. But, that's enough of my life story for one night.

Thanks again.

---

