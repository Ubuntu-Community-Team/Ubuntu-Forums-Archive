---
title: "Dvorak keyboard on Xfce"
date: 2006-10-15
forum: General Help
---

### Post by misosofos on 2006-10-15
Hi all:

Since I installed Xfce, I can't use all thouse symbols who are written by pressing alt gr and another key.

But there is something even weirder... When I start gnome and select the correct keyboard distribution, it works properly under Xfce UNTIL the next restart.

I have a dvorak keyboard and I'd like to use spanish distribution.

I've been trying to edit my xorg.conf file, but "es", "latam", nor "devorak(es)" didn't work.

Any ideas to fix that problem? Thanks

---

### Post by mallegonian on 2007-10-24
Sorry for the gravedig, I don't know if people flame about that here... (lol first post is a gd =\  )

Anyway, I am having this problem too. I use a Dvorak keymap in xfce, xubuntu 7.10 gutsy. AltGr is seeming to be totally useless. This is really getting annoying as I have to do homework for French class and I would prefer to not have to use gnome or (be afraid, very afraid, I am) windows every time I get an assignment.
It would be fine even if I could map the FN key to AltGr, or basically any other non letter key.

If anybody has even a vague idea, please do tell...

The Mallegonian

---

### Post by videodrome on 2007-10-31
I don't know about Spanish or French, but I do know that Dvorak works great under Gutsy Xubuntu.

Here is teh relevent part of my xorg.conf. Note how holding both shift keys switches back and forth to Qwerty. I suppose you could substitite French or Spanish keyboard layouts insead of "us".

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"dvorak,us"
	Option 		"XkbOptions" 	"grp:shift_toggle,grp_led:scroll"
EndSection

---

### Post by mallegonian on 2007-11-01
Thank you so much for your reply!

This solution works, but is a hackjob one... I'd still like to see the xfce people _actually_ fix this =\

---

### Post by [eXr] on 2008-03-07
There is a simpliest way to do this:

for example to change from Spanish (es) to Spanish Dvorak variation open a terminal (ie: xfce4-terminal)

$ setxkbmap es dvorak

back to qwerty:

$ setxkbmap es

without reboot X nor touch Xorg config. I hope it helps :KS

---

### Post by mallegonian on 2008-03-07
Yes, very helpful!

*runs off to set some new hotkeys :) *

Thank you. :KS

---

