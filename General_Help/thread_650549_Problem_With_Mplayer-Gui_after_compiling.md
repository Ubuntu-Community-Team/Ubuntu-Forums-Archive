---
title: "Problem With Mplayer-Gui after compiling"
date: 2007-12-26
forum: General Help
---

### Post by me4oslav on 2007-12-26
Well,i am having the following problem,i have compiled my mplayer from the 1.0 RC Source in the mplayer homepage,just by typing the following:
```
**cd /path/to/mplayer/**
```
```
**./configure --enable-gui**
```
```
**make**
```
```
**sudo make install**
```
It compiled just perfect,no problems really.
But however one major problem just appeared.I am not having GUI for the mplayer.When i execute gmplayer in a terminal here is what i got:
```
[i][u]gmplayer
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Sempron(tm) 2800+ (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE
Warning unknown option vo_dxr3_device at line 6
xscreensaver_disable: Could not find XScreenSaver window.
/usr/share/fonts/truetype/ttf-dejavu/DejaVuSerifCondensed-BoldItalic.ttf doesn't look like a bitmap font description, ignoring.
Cannot load bitmap font: /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerifCondensed-BoldItalic.ttf
[skin] file ( /usr/local/share/mplayer/skins/default/skin ) not readable.
Skin not found (default).[/i][/u]
```
Well i am not a noob and i have put a skin into **/usr/local/share/mplayer/skins/default/skin**,but it wasn't having a gui yet,then i tried putting a skin into **/usr/local/share/mplayer/skins/default/**,even in a **/usr/local/share/mplayer/skins/**,but still no GUI.I have tried to use the tar.gz/bz2 files as skins,the extracted archives and even their content,but still it doesn't want to enable the GUI.
I must admit that i am not planning to use mplayer for myself,i only plan to use its engine for the kmplayer,but i have to setup the panscan of the mplayer itself and i really don't know how to do that without GUI.I have tried to use the mplayer from the sources.list,but i was unable to change his panscan,too.As you know the panscan control the resolution of the movie on a fullscreen mode and i really don't want to use kmplayer in a fullscreen mode with 300-200(or sth. like that).
Thanks in advance.

---

### Post by taurus on 2007-12-26
Edit ~/.mplayer/gui.conf

```
gedit ~/.mplayer/gui.conf
```
and look for the line that says **gui_skin =**, change it to look like this.

```
gui_skin = "Blue"
```
Save it and see if you can start gmplayer from a terminal again.

---

### Post by me4oslav on 2007-12-26
Thanks,i will try this tomorrow,because is getting late now in Bulgaria and i want to go to sleep,but i hope it works.If i still am having any problems i will write down.

---

### Post by disturbedite on 2007-12-26
can i ask why you compiled it when it is available in the repo?

i would also like to recommend smplayer.  it is a frontend/gui for mplayer.  (the best one imo).

---

### Post by me4oslav on 2007-12-26
well,i wasn't able changing the panscan of the the version from the repos,and so all my frontends for the mplayer(k&smplayer) were giving a extremely small resolution on a fullscreen mode.Like 300x200 witch is pretty bad.I am happy with my kaffeine now,but the problem with the mplayer really makes me nervous.

---

