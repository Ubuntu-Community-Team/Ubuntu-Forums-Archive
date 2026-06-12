---
title: "Sometimes program windows black-out"
date: 2008-05-11
forum: General Help
---

### Post by ilikeroflcopters on 2008-05-11
I just recently updated from Ubuntu 7.10 to 8.04, and I tried out the desktop cube, but when it was enabled and after i disabled it, if i have a window maximized and open another window,the newest one will black out.But if i unmaximize the blacked out window, it'll show up again.The same goes if its on another desktop.

Screenshots:
maximized on another desktop
[http://i168.photobucket.com/albums/u194/ilikeroflcopters/problem.png](http://i168.photobucket.com/albums/u194/ilikeroflcopters/problem.png)

unmaximized on another desktop
[http://i168.photobucket.com/albums/u194/ilikeroflcopters/fixed.png](http://i168.photobucket.com/albums/u194/ilikeroflcopters/fixed.png)

Help appreciated =D

---

### Post by RAOF on 2008-05-11
You're probably seeing the infamous nvidia black window bug: [https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/96473](https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/96473)
That was meant to be fixed in Hardy's nvidia drivers, but maybe it still occurs in some situations?  The nvidia changelog I remember seemed a bit ambiguous.

---

### Post by aidave on 2009-06-09
Same thing happens to me.  No solution found yet.

I have the latest Hardy and Nvidia drivers as of June 9 2009.

After a day of running, new windows become black.
Requires rebooting (can restart Compiz, but then everything becomes super slow).

Very frustrating having to REBOOT LINUX everyday, when it is supposed to be stable and not require reboots...

---

### Post by meekamoo on 2010-11-17
I also haven't managed to find a solution for it either, I'm on 10.10 maverick and its STILL happening.

I don't need to reboot though - I close down a few of my windows and then they work. Seems like maybe its when the video ram fills up or similar?

---

