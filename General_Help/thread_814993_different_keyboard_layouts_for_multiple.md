---
title: "different keyboard layouts for multiple"
date: 2008-06-01
forum: General Help
---

### Post by pawonfire on 2008-06-01
My wife wants to start using ubuntu again.  I use dvorak, she qwerty.  When I installed the system originally, I selected dvorak as the default keyboard.  When I set up her account, I changed her keyboard layout to USA default.  Whenever she logs in again, the USA default selection is still there, but she is typing in dvorak.

This worked before in either 7.04 or 7.10, but the situation was reversed.  USA default was the base setup, and my login was set to dvorak.  With 8.04, it doesn't work.  Please help me.

I have figured out how to change layouts by typing a key sequence, but I would like it to switch automatically depending on who logs in.

Phill

---

### Post by Rhubarb on 2008-06-09
This problem effects me too.
I installed Ubuntu 8.04 (64bit) with dvorak keyboard layout.
From a cold boot my (USA - dvorak) account works fine.
But another (USA - default qwerty only) account starts up typing in dvorak - when the keyboard preferences clearly state it's in USA default (qwerty).

I'll try and investigate this problem further and perhaps file a bug report on it.
I'll keep you updated about it.

---

### Post by Rhubarb on 2008-06-10
I've found a work-around which seems to work perfectly.
In your case, gnome needs to be told to use dvorak upon login to your account (because the system wide keyboard layout is qwerty).

In your account, open up your favorite text editor and type this in:
```
#!/bin/bash
setxkbmap dvorak
```
Save this as "dvorak.sh" or anything else you like somewhere in your home directory.

Make it executable (in nautilus right click on dvorak.sh, properties --> permissions, then tick the box "allow executing as a program".  (or open up a terminal and type in: *chmod +x dvorak.sh* )

Now to make this bash script load up every time you login to your account.
System --> Preferences --> Sessions.  Then click on the add button.
Give it a name, something like "Force dvorak keyboard layout"
Browse for the dvorak.sh script in the command box.
Then give it a description like "Force dvorak keyboard layout rather than qwerty".
Press OK

Now every time you log in to your account it will be using dvorak by default as it should.  Your wife's account should still be qwerty.


If you install ubuntu with dvorak set as default, and you have a qwerty user that's having problems because it defaults to dvorak upon login, modify the bash script to contain this:
```
#!/bin/bash
setxkbmap us
```

---

### Post by Rhubarb on 2008-06-10
I've discovered my /etc/X11/xorg.conf is different on two Ubuntu 8.04 computers here (one 32bit and one 64bit).
My 64bit computer is the one that had dvorak / qwerty layout problems as you describe.
As I had reconfigured my xorg.conf on my 64bit machine (by using ***sudo nvidia-xconfig***) previously, this may be the cause of the problem.


My default system-wide layout is dvorak.
This is the keyboard layout of the problematic computer:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dvorak"
EndSection
```


This is the keyboard layout of a nicely working default Ubuntu 8.04 install:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"dvorak"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
```


Notice that there are large differences between the two.
I don't have time to change my /etc/X11/xorg.conf now to check, but it seems to be a safe bet that this is the cause of the problem.

---

### Post by mettlewk on 2008-10-24
Hello,


Thank you for your assistance.

G.

---

