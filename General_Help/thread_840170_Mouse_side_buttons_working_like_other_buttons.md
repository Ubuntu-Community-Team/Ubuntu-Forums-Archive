---
title: "Mouse side buttons working like other buttons"
date: 2008-06-25
forum: General Help
---

### Post by Sqloud on 2008-06-25
I currently run Ubuntu 8.04 hardy and I own a Canyon CNR-MSL5 optical USB mouse. I've unsuccessfully tried to configure its extra buttons but so far i got the 2 buttons on the side working like the middle and the right button respectively. This was not my intention, as I used to use these for back and forward commands back on windows.

Below is an extract from xorg.conf:
> 
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option          "Buttons" 	"8"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option          "ButtonMapping"         "1 2 3 4 5 6 7"
	Option		"Emulate3Buttons"	"false"
EndSection

If anybody can provide any helpful advice I'd appreciate it. Thank you.

---

### Post by Sqloud on 2008-06-26
bump... Is there nobody that can help? I really don't want to get another mouse/ go back to windows.

---

### Post by rolandixor on 2008-06-26
Do a search for logitech mouse, here and in the wiki. I saw some similar info for those mice that might work for yours with some tweaking. I'm in the same boat though, so if I find a solution I'll see if I can help you.

---

### Post by Victormd on 2008-07-04
I have a 7 button mouse by Dell and the side buttons work just like you want them to (back/forward). The thing is, I didn't have to do any thing to configure. Here's what my mouse section in xorg.conf looks like:
> Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

---

### Post by l0fls on 2008-07-05
i may be wrong here but just trying to help
check out
System > Prefrences > Keyboard Shortcuts

---

