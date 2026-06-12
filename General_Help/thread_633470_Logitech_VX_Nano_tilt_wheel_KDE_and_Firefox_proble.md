---
title: "Logitech VX Nano tilt wheel KDE and Firefox problems"
date: 2007-12-06
forum: General Help
---

### Post by aallison05 on 2007-12-06
I'm trying to get my Logitech VX Nano to work properly with Kubuntu.  I've been able to get all my buttons to work with btnx, but need a better solution for the tilt wheel.  I can configure the wheel to generate ALT+WHEELUP or ALT+WHEELDOWN when tilting left/right, and that works for horizontal scrolling in KDE, but does nothing in Firefox.  I can set btnx to generate left and right arrows for the tilt, but that will only move the cursor in other apps instead of scrolling.  I'd like to find a solution that lets me scroll properly in everything, but I guess if I have to I'll sacrifice being able to scroll horizontally in Firefox.

The relevant part of my xorg.conf is below:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"auto"
	Option		"Buttons"		"11"
	Option		"ZAxisMapping"		"4 5 6 7"
	Option		"Emulate3Buttons"	"false"
EndSection
```

Also, weird thing I noticed is that though btnx detects the tilt buttons, xev does not.  Should be buttons 6 & 7 since xev skips those two, but I don't understand why one program sees them and another does not.

Thanks for any help you can provide!

---

### Post by centyx on 2008-06-12
Did you ever find a solution? I have a different mouse but am also having the same issue.

Thanks!

---

