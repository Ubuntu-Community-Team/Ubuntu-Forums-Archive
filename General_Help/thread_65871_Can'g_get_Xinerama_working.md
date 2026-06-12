---
title: "Can'g get Xinerama working"
date: 2005-09-15
forum: General Help
---

### Post by david_liz on 2005-09-15
Hi! This is my first post to the forum, although I've been reading for months. I've a Matrox G450, and I can't get Xinerama to work. I've two LCD monitors connected, but some problems arise:

They are both working, but in mirror mode, so I see the same image. Also, I cant manage to have different resolutions in each of them, because one is 17" and the other 15".

You can take a look at my xorg.conf and xorg.log files if you want.. any help will is welcome!

thanks in advance.

---

### Post by trash on 2005-09-15
I don't have a Maxtor but it's talked about here [http://da.gentoo-wiki.com/HOWTO_Dual_Monitors](http://da.gentoo-wiki.com/HOWTO_Dual_Monitors)
Maybe you've seen this already though.
good luck!

---

### Post by metallmann on 2005-11-20
[QUOTE=david_liz]
You can take a look at my xorg.conf and xorg.log files if you want.. any help will is welcome!
[/QUOTE]

Try to change your ServerLayout section to this (I commented the "Xinerama" "on" bit because I don't have that in my config and mine works now.. but it's ok I guess)

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0	"Default Screen" LeftOf "Default Screen2"
	Screen	1	"Default Screen2"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	Option		"Xinerama" "on"
EndSection


Furthermore:
I have : 
Section "ServerFlags"
	Option "Xinerama" "True"
EndSection

In stead  of Option "Xinerama" "on". Still I don't know whether this makes a big difference.

---

