---
title: "[SOLVED] gnome desktop over rides fluxbox"
date: 2008-05-31
forum: General Help
---

### Post by blampars on 2008-05-31
I've decided, just for kicks, to install fluxbox to play with.  I'm running it on an old lappy of mine and it runs great, so I figured why not see what I can do on my main computer.

the problem is, after about a minute of fluxbox running fine, my gnome background and desktop icons appear, but with the fluxbox menu bar at the bottom.

i can no longer right click for the fluxbox menu, i just get gnomes right click menu of create a folder, create launcher, etc...

what's the deal? and how do i fix it? :)

thanks
-b

EDIT - i was running nautilus at startup which in turn was starting part of the gnome desktop for some reason. o_O

---

### Post by RedSquirrel on 2008-06-01
When you use nautilus in fluxbox, run it with the --no-desktop option so that it won't take over your desktop.

```
nautilus --no-desktop
```

---

