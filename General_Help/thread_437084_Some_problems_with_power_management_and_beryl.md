---
title: "Some problems with power management and beryl"
date: 2007-05-08
forum: General Help
---

### Post by ericus on 2007-05-08
Hi!

I have a very annoying problem, when I watch a movie or something and don't use the keyboard or mouse for 20 minutes the screen goes off. I dont have any screensaver active, and the timer in the power management is set to 58 minutes. Very annoying when I'm lating in bed watching movies and have to go up and activate the screen.

Another problem, I have XGL + Beryl, and when I open a new windows, for example firefox, it is very slow. There is a outlined box that grows larger and then turns into a window. I dont have any animation on creating windows, so I cant see why it does that.

---

### Post by akudewan on 2007-05-08
If you're using mplayer, have a look at this: [http://gentoo-wiki.com/HOWTO_MPlayer#Turning_off_Annoyances](http://gentoo-wiki.com/HOWTO_MPlayer#Turning_off_Annoyances)
(xset -dpms is probably the one you need).

Can't help you with beryl though..sorry.

---

### Post by ericus on 2007-05-08
I'm using VLC media player.

---

### Post by dreadlord_chris on 2007-05-08
> **ericus said:**
> Hi!

I have a very annoying problem, when I watch a movie or something and don't use the keyboard or mouse for 20 minutes the screen goes off. I dont have any screensaver active, and the timer in the power management is set to 58 minutes. Very annoying when I'm lating in bed watching movies and have to go up and activate the screen.

Another problem, I have XGL + Beryl, and when I open a new windows, for example firefox, it is very slow. There is a outlined box that grows larger and then turns into a window. I dont have any animation on creating windows, so I cant see why it does that.

Hi ericus and welcome!

I also was very annoyed by the power managment settings for my monitor. I turned all the power managment settings off, I xset -dpms, BIOS settings, nothing worked. Seemed, that no matter what I did, that damn monitor would still blank after 15 minutes of keyboard/mouse inactivity.

After **much** digging and googling, googling and digging (I dig googling :lolflag: ) I found the solution!

*****NOTE***** This will turn off **completely** all power managment settings for you monitor - so, if you are using a laptop this may not be a good idea. My system is a desktop box w/ an HP flat panel monitor - and this works like a charm for me, with no problems.

This requires manually editing **xorg.conf**, so pull your waders on and open a terminal, it's messy down in the trenches :) .
```

sudo nano /etc/X11/xorg.conf

```
There are several lines in this file that must be added/changed. First, look for: ***Section "ServerLayout"*** - you want to add the following lines:
```

Option 	   "BlankTime" "0"
Option	   "StandbyTime" "0"
Option 	   "SuspendTime" "0"
Option	   "OffTime" "0"
Option 	   "NoPM" "true"

```
Next look for: ***Section "Module"*** - and change this line:
```

Load            "extmod"

```
to this:
```

SubSection     "extmod"
Option	   "omit DPMS"
EndSubSection

```
Save the file and reboot. Your monitor will no longer turn itself off until you tell it to.

As to your other problem - not sure but it sounds like you may just not have enough video memory.

---

### Post by chris.olsen on 2007-05-09
I am having the exact same issue when playing videos with vlc, it is pretty annoying.

---

