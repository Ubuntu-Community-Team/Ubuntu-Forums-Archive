---
title: "Shift Key not working with some letters"
date: 2007-05-10
forum: General Help
---

### Post by sadaraine on 2007-05-10
I was working with my Logitech MX3000 keyboard to try to get some keys to function and somewhere in there some shift keys stopped working properly.  I have removed the packages   I used already, but it didn't resolve the issue.  Packages - xvkbd, xbindkeys, keytouch.  During this I did configure a .xbindkeysrc file, but that has been removed as well.

It is worth noting the following -
[LIST]
[*]The letters work when the CAPS LOCK is on
[*]The shift key is being recognized...xev shows the proper info when I hit and release the shift key
[*]xev does not register anything when the actual letter is typed, for the keys that work it reflects an entry for the capital letter
[*]This bug is affecting some symbols as well
[*]Sometimes if I keep typing the letter or if I've been typing others, the keys work properly
[*]The keys look like they work when the shift key is released before the letter key is released...is there something that I am not looking at that thinks that while shift-[key] is pressed it is a shortcut?
[/LIST]

Here is the output of me holding down the shift key and hitting each character on the keyboard starting with the ` and ending with / 

~@#$%^&*_QWETUO{}|ASDFGHJKL:"CVN?

and with the caps lock --

`1234567890-=QWERTYUIOP[]\ASDFGHJKL;'ZXCVBNM,./

I have checked the keyboard shortcuts under System > Preferences and don't anything assigned to shift-I for instance.  

xorg.conf keyboard entry -

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

---

### Post by sadaraine on 2007-05-11
After troubleshooting this farther with a freind, the problem is a hardware issue.  The keyboard acts the same inside the bios so it has nothing to do with Ubuntu. :)

---

