---
title: "Zsnes has no sound..."
date: 2008-06-13
forum: General Help
---

### Post by morbid_bean on 2008-06-13
I cant seem to figure out why my zsnes isnt giving sound...ive played w/ the settings and nothing seems to work...is there a codec or something i need to install?

Using the ubuntu 8.04 version

---

### Post by cyberlion on 2008-06-13
Edite the menu-icon of zsnes, and add this command: zsnes -ad sdl

---

### Post by morbid_bean on 2008-06-13
> **cyberlion said:**
> Edite the menu-icon of zsnes, and add this command: zsnes -ad sdl

I take it that you right click on the icon and do properties....and in the command box you add "-ad sdl" after zsnes               so in the box would show "zsnes -ad sdl"

Did that...and nothing happens

---

### Post by Heggerud on 2008-06-14
SDL sound well sounds crappy, try my sound fix

[http://ubuntuforums.org/showthread.php?p=5183727#post5183727](http://ubuntuforums.org/showthread.php?p=5183727#post5183727)

---

### Post by windoze87 on 2008-06-14
do you run zsnes from the command line? if not, try it. when you do, do you get a bunch of lovely error messages? I had the same problem with zsnes a while back and installing pulseaudio fixed mine.

---

### Post by wolffangalchemist on 2008-07-29
put this in terminal it will fix the no sound issue 
```
 sudo aptitude install libsdl1.2debian-alsa 
```
or
```
 sudo aptitude install libsdl1.2debian-oss 
```
sound works perfect for me with this.:)

---

