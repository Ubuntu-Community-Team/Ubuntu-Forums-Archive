---
title: "xrdp, x11vnc, sorta working"
date: 2007-10-24
forum: General Help
---

### Post by cytg on 2007-10-24
hello

by reading previous posts and alot of trial and error on my own i almost got xrdp working.
almost, but not quite.

-xrdp 0.4
-x11vnc from the repos
-xp's msts remote desktop client
- feisty 7.04

I get my beloved gnome desktop up .. i can drag windows around, but for the life of me i cant 'single click' anything .. cannot close windows, click menu's etc... its friggin weird, anyone have ANY idea wth im doing wrong here ? Took me some time allright to get this far, i'd really hate to stop this marathon 5 meters from the finish line :)

---

### Post by cytg on 2007-10-24
btw, im doing all the configuring from a ssh terminal (besides starting xrdp, wich i couldnot get hookd up with gnome-session unless running from the actual desktop session, so had to do that from home)..
Im also running beryl, perhaps that is fux0ring things up .. i suppose i could do a kill on that, gnome should revert to a standard (metacity?) windows handler then shouldnt it ?

edit. oh yea, im sorta still a linux n00b so please, speak slowly :)

---

### Post by cytg on 2007-10-24
muahahahah

killed beryl
started x11vnc with -allinput and -noxdamage and now its WORKING ... yessir' ..

I really should pinpoint what exactly made it work .. one of the three, two or all three .. some time later :)

---

### Post by chrwei on 2008-06-13
beryl/compiz messes up x11vnc big time, at least with the defaults.

---

### Post by krunge on 2008-06-13
> **chrwei said:**
> beryl/compiz messes up x11vnc big time, at least with the defaults.

You are not using the "-noxdamage" x11vnc option?  That is the only workaround until Xorg fixes this bug (XDAMAGE reports are not correct).

So supply it to x11vnc if you are going to use beryl/compiz stuff.

---

