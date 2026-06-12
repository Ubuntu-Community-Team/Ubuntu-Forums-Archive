---
title: "Forcing resolution with a generic monitor / generic videocard"
date: 2008-02-24
forum: General Help
---

### Post by Mr.Johnny on 2008-02-24
Hi! 

How do I force the resolution for a generic monitor video card? I've tried adding a "Display" subsection in xorg.conf as seen in a few threads I found here, but I always get a parser error, and I've made sure I typed it right. :( Is there any other way?

Thanks

---

### Post by Yellow Pasque on 2008-02-24
Can you post your /etc/X11/xorg.conf file?

---

### Post by Mr.Johnny on 2008-02-24
Sure, here it goes:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pt"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
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

---

### Post by Mr.Johnny on 2008-02-24
bump

---

### Post by soldats on 2008-02-24
run in terminal "sudo dpkg-reconfigure xserver-xorg" then youll get an ncurses menu for editing the xserver-xorg. use defaults for everything until you get to the resolutions settings. use the spacebar to choose the res you want. your main problem in your xorg.conf is that your refresh rates were never correctly set. i cant see the whole xorg so i cant tell. make sure you back up xorg.conf first

---

### Post by Mr.Johnny on 2008-02-24
Hi!

I had alreay tried that, but I don't get any resolution configuration menu. That machine has a 7" touchscreen, but if I connect my 19 tft to it I can select the correct resolutions, but not with this one, it always boot in 640x480 (no other resolution is available), although in windows it's capable of 1280x768 and such. :(

---

### Post by Mr.Johnny on 2008-02-24
ps: should I enable kernel framebuffer? edit: no, i shouldn't, otherwise the xserver won't start, lol
ps2: my xorg.conf (in /etc/X11 )has nothing else than the above (all the rest was commented).

---

### Post by Mr.Johnny on 2008-02-24
:-\"

---

### Post by Yellow Pasque on 2008-02-25
What kind of video card do you have? Can you post the output of this command?:
```
lspci
```

---

### Post by Mr.Johnny on 2008-02-25
Greetings!

I have a bunch of geforce cards, series 3/4 and 7xxx.

I didn't refer this, but I have ubuntu installed on a pen drive, and I need to set a default resolution that it's compatible with all (1280x768 is fine, since the touchscreen doesn't like 1024x768 ), as I boot this on several machines. 

All work fine, except this one that has the touchscreen. If I connect another screen to it, I have the needed resolutions available.

The card in it is an abit geforce 440 mx, should I post the lspci output anyway?

---

### Post by Yellow Pasque on 2008-02-25
You need to install and configure the nvidia legacy drivers:
```
sudo apt-get install nvidia-glx-legacy
sudo nvidia-glx-config enable
```

---

### Post by dark_phantom on 2008-02-25
I had a bunch of problems with both my card and monitor (Samsung 245T).  I have it working now, but it was weird.  Install envy and see if that works if not, then do the sudo dpkg-reconfigure xserver-xorg and reinstall the drivers via envy.  Don't know why this worked like this, since I though with only installing envy would be fine.

---

