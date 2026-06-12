---
title: "Problem with XGl"
date: 2006-10-11
forum: General Help
---

### Post by Ephemeriis on 2006-10-11
I've got a quick question to ask...before I bother to look too deeply into installing Compiz/Beryl.

About a month back I installed Compiz.  It worked great...beautiful eye candy, good performance...I was quite happy with it.  Then I noticed that some of the programs and utilities I wanted to run wouldn't work anymore.

xgamma, for example, would error out.  So did Scorch3d, WoW (through WINE), and NeverWinter Nights (native).  Seems like anything that really wanted to mess with the video settings or work with 3D would error out.  I don't recall the error...but it was something to the effect of "rendering device not found".

A bit of research told me that this was because XGL/Compiz was now drawing the screens rather than the traditional X11.  The old X11 calls didn't work through XGL/Compiz.  There were a couple fixes...one involved running two sessions, both XGL and X11 at the same time...another looked like a pretty messy hack to make XGL work properly...  I decided, at the time, that it wasn't worth the trouble for more eye candy.

My question then, is whether this is still a problem.  If I install Compiz/Beryl am I going to be able to keep using all my assorted programs/utilities/games, or am I going to run into this same issue again?  I don't want to go to the trouble of setting it up if I'm just going to wind up removing it again...

FYI:  I'm using the binary nVidia drivers, NVAGP, and GNOME.

---

### Post by ayoli on 2006-10-11
i m not sure if it's the real solution to your problem, but try to launch these programs like this:
```
XLIB_SKIP_ARGB_VISUALS=1 && export XLIB_SKIP_ARGB_VISUALS && *prog_name*
```

---

### Post by PriceChild on 2006-10-14
*moved out of sticky to general help*

---

