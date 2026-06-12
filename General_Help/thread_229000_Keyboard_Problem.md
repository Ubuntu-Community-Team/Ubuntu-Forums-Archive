---
title: "Keyboard Problem"
date: 2006-08-03
forum: General Help
---

### Post by Paul41 on 2006-08-03
I am having a couple problems with my keyboard number pad.  The first problem is that toggling the num lock doesn't do anything.  The num lock always stays on.  This is a problem that I can live with because I always leave the num lock on anyway.  

The second problem is more of an issue for me.  The decimal key deletes instead of typing a decimal unless I hold down the shift key.  

I have tried installing Numlockx and it didn't make any difference at all.  Does anyone have any other suggestions that I can try?

---

### Post by yopnono on 2006-08-03
> **Paul41 said:**
> I am having a couple problems with my keyboard number pad.  The first problem is that toggling the num lock doesn't do anything.  The num lock always stays on.  This is a problem that I can live with because I always leave the num lock on anyway.  

The second problem is more of an issue for me.  The decimal key deletes instead of typing a decimal unless I hold down the shift key.  

I have tried installing Numlockx and it didn't make any difference at all.  Does anyone have any other suggestions that I can try?

Check what kind of keyboard you have installed. 
System-Preferences-Keyboard

---

### Post by Paul41 on 2006-08-04
> **yopnono said:**
> Check what kind of keyboard you have installed. 
System-Preferences-Keyboard

I had already changed the keyboard to the Dell 102 key, but this didn't solve the problem either.  It is also set for US English if that makes any difference.

---

### Post by yopnono on 2006-08-04
> **Paul41 said:**
> I had already changed the keyboard to the Dell 102 key, but this didn't solve the problem either.  It is also set for US English if that makes any difference.

Well if you have a US keyboard then it should be set to US.
Try different keyboard layouts like... Generic keyboard
That is what I use on my DELL

---

### Post by Paul41 on 2006-08-06
> Try different keyboard layouts like... Generic keyboard

OK, I have found a keyboard that fixed the decimel problem, but now I have a new problem.  alt+tab no longer moves between open windows, and ctrl+alt+d no longer shows the desk top.  I have tried several different keyboard layouts now, but I have the same problem with all of them.

---

### Post by yopnono on 2006-08-06
> **Paul41 said:**
> OK, I have found a keyboard that fixed the decimel problem, but now I have a new problem.  alt+tab no longer moves between open windows, and ctrl+alt+d no longer shows the desk top.  I have tried several different keyboard layouts now, but I have the same problem with all of them.

Question. 
Whats you modell DELL ???. And is it a US QWERTY Keyboard ?

---

### Post by Paul41 on 2006-08-06
> Whats you modell DELL
Dimensions 8200

> US QWERTY Keyboard ?
Yes

---

### Post by yopnono on 2006-08-06
> **Paul41 said:**
> Dimensions 8200


Yes

ok... Ehh.. have you tried the generic 104, also what that the xorg file say about you keybord.

This is my xorg:
 sudo gedit /etc/X11/xorg.conf
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection
```

---

### Post by Paul41 on 2006-08-06
> have you tried the generic 104
Yes, I tried this one.  This was one where the decimel worked, but the alt+tab and ctrl+alt+d did not.

> what that the xorg file say about you keybord
Where is what is in my xorg file
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection
```

---

### Post by yopnono on 2006-08-06
> **Paul41 said:**
> Yes, I tried this one.  This was one where the decimel worked, but the alt+tab and ctrl+alt+d did not.


Where is what is in my xorg file
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection
```

It's all look like it should, don't know what to say, sorry.
Try to do a websearch on this issue.

---

### Post by Paul41 on 2006-08-06
OK, thanks for trying.

---

### Post by Paul41 on 2006-08-08
I have now solved this problem.  When I first installed the NVIDIA drivers I was having a problem with shift+backspace restarting X.  I found a thread in the forums to solve this problem by adding the following to my startup:
```
xmodmap /usr/share/xmodmap/xmodmap.us
```
Out of curiosity I removed this from my start up and the problem is fixed.  Also shift+backspace is no longer causing a problem with X restarting.  I don't know if the new keyboard setup solved the problem with X or if it was a update to the NVIDIA driver.  I just wanted to give an update incase anyone else is having the same problem.

---

