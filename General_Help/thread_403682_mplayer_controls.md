---
title: "mplayer controls"
date: 2007-04-07
forum: General Help
---

### Post by GuitarRocker2562 on 2007-04-07
Ok, I installed mplayer and a nice skin. I have one problem though, when I go into fullscreen, I can't access the control box (you know the one with play, pause, volume, seek). How do I view this without quitting fullscreen?

---

### Post by heimo on 2007-04-07
I've understood that some skins may lack the "playbar". Try changing to default or blue, and point your mouse bottom center of the screen. Does it work?

---

### Post by GuitarRocker2562 on 2007-04-07
i tried default, no playbar when in fullscreen

---

### Post by heimo on 2007-04-07
Hmm... Works for me. You could try downloading some other skin (I tried Abyss).
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

And check that this:
```
grep playbar ~/.mplayer/gui.conf
```

Outputs something like:
```
playbar = "yes"
```

If everything else fails, use keyboard shortcuts. 
[http://en.wikibooks.org/wiki/Mplayer](http://en.wikibooks.org/wiki/Mplayer)

---

### Post by Harold P on 2007-04-07
> **GuitarRocker2562 said:**
> Ok, I installed mplayer and a nice skin. I have one problem though, when I go into fullscreen, I can't access the control box (you know the one with play, pause, volume, seek). How do I view this without quitting fullscreen?
```
Basic keys: (complete list in the man page, also check input.conf)
 <-  or  ->       seek backward/forward 10 seconds
 down or up       seek backward/forward  1 minute
 pgdown or pgup   seek backward/forward 10 minutes
 < or >           step backward/forward in playlist
 p or SPACE       pause movie (press any key to continue)
 q or ESC         stop playing and quit program
 + or -           adjust audio delay by +/- 0.1 second
 o                cycle OSD mode:  none / seekbar / seekbar + timer
 * or /           increase or decrease PCM volume
 x or z           adjust subtitle delay by +/- 0.1 second
 r or t           adjust subtitle position up/down, also see -vf expand
```

You don't really need a playbar.

---

### Post by GuitarRocker2562 on 2007-04-07
thanks heimo, it turns out that my GUI.cfg had 
"playbar=no" for some dd reason, its fixed now!

---

