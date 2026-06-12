---
title: "Corrupt video driver?"
date: 2007-05-25
forum: General Help
---

### Post by love_the_drake on 2007-05-25
I am dual booting Ubuntu 6.06 with WinXP.  While Ubuntu was starting, I accidentally switched off the computer.  When I restarted and booted Ubuntu, the logo looked "psychedelic," for lack of a better term, and when the GUI finally started, the entire screen was filled with different colored pixels and I couldn't make anything out.  When I move the mouse, I can see the motion on the screen, but it's just a big mess.

I'm assuming that when I turned off the computer, the graphics driver became corrupted.  I can boot into the rescue mode fine.   Is there anything I can do to fix this, short of reinstalling from CD?

---

### Post by vtel57 on 2007-05-26
Try running this command from the command line:

```
 # dpkg-reconfigure xserver-xorg
```

Follow the directions.

---

