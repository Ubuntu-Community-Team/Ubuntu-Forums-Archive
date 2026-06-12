---
title: "Compiz creates Graphical glitches...."
date: 2008-06-23
forum: General Help
---

### Post by gnrathon on 2008-06-23
System Specs:
Ubuntu Hardy Heron
Dell Optiplex 320
Intel Celeron D 3.06Ghz
ATI Radeon Xpress 1100 128MB
40GB Hard drive [30GB for Ubuntu]
512MB RAm
{Ubuntu is on a Wubi install}

I downloaded the appropriate drivers for my system
and enable compiz

Every thing worked just fine nothingt was wrong and it seemed to run just smoothly

it wasn't until later i noticed that any application that uses complex graphics came out extremely glitchy, making it impossible to use screensavers, blender, emulators etc.

then i ran ubuntu in Gnome Failsafe mode and the graphics worked absolutely flawlessly. Everything ran GREAT

is there anyway to get Ubuntu to work like this and still have compiz enabled?

---

### Post by badfish591 on 2008-06-24
yeah it happens to me too, i think its a video driver issue.... ATI sucks. maybe try running EnvyNG and see if it helps out.
sudo apt-get install envyng-gtk

---

### Post by Forlong on 2008-06-24
Yeah, OpenGL applications flicker on ATI cards.
It's a known problem and it's not yet fixed by ATI.

Use e.g. Compiz-Switch to turn Compiz off when using such applications.

---

