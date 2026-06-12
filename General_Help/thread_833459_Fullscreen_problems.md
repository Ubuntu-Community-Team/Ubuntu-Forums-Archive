---
title: "Fullscreen problems"
date: 2008-06-18
forum: General Help
---

### Post by lieryan on 2008-06-18
Whenever I'm using a fullscreen apps, the app would quit fullscreen and go to windowed mode. This happens consistently across many fullscreen application: 20.000 Light Years Into Space, OpenArena, SavageFE, etc. When they would switch to windowed mode varies a bit, in 20.000 LYIS, it would go on and off when playing without visible patterns, on OpenArena whenever it switch to windowed the keyboard and mouse is rendered useless (again without visible patterns), on SavageFE it happens only at startup if the startup is passed it'd be fine for the rest of the time (again, when and why the game would goes to windowed mode has no visible patterns).

As you can see, I can't see any pattern here, and that's annoying me. The only thing that is consistent is it happens across many full screen apps without any visible patterns on what I did.

PS: I'm on Ubuntu Hardy 64-bit (upgraded from Gutsy 64-bit), on HP Compaq Presario V3221AU (AMD Turion X2 64, nVidia GeForce 6150 Go - Proprietary Driver - nvidia-glx-new).

PPS: I also have other minor problems, my startup/login screen is displayed at the wrong resolution and the bottom panel is cut off and the please-wait-I'm-working-cursor is vertical ellipse instead of circle. If this might indicate some problems with my graphic card or drivers.

PPPS: I have a history of messing up with my xorg.conf to get dual screen working, it never worked fully, usually one screen would have incorrect resolution or when I got back to single screen, it would have incorrect resolution. That was while on Gutsy, never tried again since Hardy.

---

### Post by lieryan on 2008-06-19
any ideas?

---

### Post by Pjotr123 on 2008-06-19
Get the resolution right:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

That's assuming you're running the restricted driver already. If not:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2 as well).

Lastly, before starting a full screen movie: temporarily disable the visual effects:
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(number 5 )

That should help.  :-)

---

### Post by lieryan on 2008-06-19
I already get my resolution right, the "minor problem" is only in the logon screen, after that, the resolution would change into the correct resolution. And I am using the restricted drivers already: nvidia-glx-new.

It's not full-screen movies, it's full-screen games. But I'll try that (using no desktop effects), cause I make many small tweaks on compiz here and there. 

Anyway, do you know where compiz saves its configurations file, cause I don't want to reconfigure compiz again if it can't be helped? I found /etc/compizconfig/config but that doesn't seem to be all of it and neither google nor man seems to be of help.

---

