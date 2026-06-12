---
title: "I use dvorak keyboard layout. So why is GUI login screen in qwerty?"
date: 2005-10-15
forum: General Help
---

### Post by hanzj on 2005-10-15
Hello everyone,
I use Dvorak keyboard layout on my ubuntu. I have Dvorak in the GUI, and I have it in tty1. But when I get to the graphical log-in screen after every restart, the keyboard layout in Qwerty. Then, after logging in using qwerty, the GUI switches to my dvorak layout. 

Is there a way to get the graphical login screen (as with everything else on my ubuntu/gnome pc) on dvorak?

---

### Post by Domhnull on 2005-10-16
Yes, this gets posted from time to time.  Check out this thread:
[http://www.ubuntuforums.org/showthread.php?t=31076&highlight=dvorak]("http://www.ubuntuforums.org/showthread.php?t=31076&highlight=dvorak")

---

### Post by hanzj on 2005-10-16
RE: that hyperlinked post you referred you: Is that good for Breezy users?

---

### Post by lithorus on 2005-10-16
[QUOTE=hanzj]RE: that hyperlinked post you referred you: Is that good for Breezy users?[/QUOTE]
Well, did you try it? Someone has to try to find out :)

---

### Post by hanzj on 2005-10-16
My xorg.conf has the following lines
> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"jp"
	Option		"XkbVariant"	"dvorak"
EndSection

Do you think changing 
	> Option		"XkbLayout"	"jp"
to 
> 	Option		"XkbLayout"	"us"
is the solution?

---

### Post by hanzj on 2005-10-16
I changed my xorg.conf from jp to us (as I was thinking of doing in my last post), and it works. Now the GUI login screen is in dvorak!
Thanks for your ideas and help. Much appreciated.

---

### Post by lithorus on 2005-10-16
[QUOTE=hanzj]I changed my xorg.conf from jp to us (as I was thinking of doing in my last post), and it works. Now the GUI login screen is in dvorak!
Thanks for your ideas and help. Much appreciated.[/QUOTE]
Actually I've never heard of a Japanese dvorak layout. I always thought that dvorak was refering to western characters, much like qwerty is.

Edit:
Just looked through the System -> Preferences -> Keyboard and it seems that only a few layouts have a dvorak variant, eg. France and U.S. English. Japan doesn't have a dvorak variant.

---

### Post by hanzj on 2005-10-16
there's really no special japanese dvorak layout.
what i have is the dvorak layout in both english and in japanese.

---

### Post by pizzach on 2005-10-27
LOL!!!!  I thought I was the only person in the world who typed japanese in dvorak.  I actually did this on Mac OS X and found out on linux it was just as easy.  Never figured out how to do it on windows though and so avoid tying japanese on it like the plague.

Just as a note, when installing Ubuntu if you select dvorak then, your log in and everything starts as dvorak.

Anywho, that is my contribution to this thread.

---

