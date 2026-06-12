---
title: "NES Emulator?"
date: 2008-05-09
forum: General Help
---

### Post by Uruz on 2008-05-09
I've been looking everywhere and can't seem to find a NES emulator for my Gutsy 7.10. Zsnes was easy to get, but synaptic's Nes emulator can't open my roms. I also tried Wine's guide to install Nestopia (My personal Favorite), but that didn't work either.

Is there a script I could use or something?

---

### Post by motersho on 2008-05-09
try this one of these 

sudo apt-cache search nintendo | grep nes

You should see the one that you tried and two others.

---

### Post by disturbedite on 2008-05-09
there is no reason anyone should run nestopia through wine when on can get nestopia for linux here:
[http://rbelmont.mameworld.info/](http://rbelmont.mameworld.info/)

btw, a new version (1.39) for linux is coming soon, if you can sit tight.

nestopia really is the best NES emulator there is.

---

### Post by LuxVoodoo on 2008-05-09
> **Uruz said:**
> I've been looking everywhere and can't seem to find a NES emulator for my Gutsy 7.10. Zsnes was easy to get, but synaptic's Nes emulator can't open my roms. I also tried Wine's guide to install Nestopia (My personal Favorite), but that didn't work either.

Is there a script I could use or something?

I've always used GFCE Ultra without any problems. The original Legend Of Zelda never gets old!  :)

---

### Post by angry_johnnie on 2008-05-09
There's fceu (with gfceu as a graphical frontend).

just do:

```
sudo apt-get install gfceu
```

there's also zsnes (for super nes), which is pretty good, too.

---

### Post by rubicon on 2008-05-10
There's also *mednafen* :) Which works excellent with a lot of systems: 
> The systems supported by Mednafen are:
    * Atari Lynx
    * GameBoy
    * GameBoy Color
    * GameBoy Advance
    * **NES**
    * PC Engine (TurboGrafx 16)
    * PC-FX
    * SuperGrafx
    * NeoGeo Pocket, NeoGeo Pocket Color
    * WonderSwan

---

### Post by Uruz on 2008-05-10
I've tried Gfceu, but I can't seem to run it. gfceu in terminal just gives me options and when I type 'gfceu /home/zach/NinjaGaiden(U).nes' to open the rom, It says it can't do it.

I used Mameworld's thing, but I can't get it to compile nestopia.

**EDIT**
Nevermind, I got Nestra working (the parenthesis in the file name messed it up) But I'd still prefer Nestopia

---

### Post by disturbedite on 2008-05-10
as i said, it would be better to wait a little bit to get the latest version of nestopia.  (it hasn't been released just yet).

but if you really wanna try it now, it is very simple to compile.  the instructions are on the nestopia homepage link i posted:

Unzip the core source, then unzip the Linux overlay source over it. Change to the directory you unzipped everything in and type &#8220;make&#8221;. If you have problems, make sure you have these packages:
 - General development (also called &#8220;GCC&#8221; and &#8220;G++&#8221;) plus their dependencies
- GTK+ 2.4 or later and the development packages
- The ALSA library and it&#8217;s development packages
- SDL 1.2.11 and it&#8217;s development package

---

