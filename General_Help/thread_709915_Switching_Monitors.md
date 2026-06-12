---
title: "Switching Monitors"
date: 2008-02-27
forum: General Help
---

### Post by drewtown on 2008-02-27
Hey,

We got a new 32" LCD TV and I plan on switching between my current 17" LCD monitor at my desk and the 32" LCD TV that is in the living room.

So far I've gotten the TV to run in 13xxX780 can't remember exactly but it looks great and I had no problems with it.  But as soon as I switch back to my monitor I have to rerun sudo nvidia-xconfig and restart the computer which is a huge waste of time IMO.

Is there a way to have both the TV and the monitor set up so I don't have to continue to run nvidia-xconfig every time i switch?

---

### Post by PinkFloyd102489 on 2008-02-27
You shouldnt have to restart your computer to apply a screen resolution. Run it with gksudo so that you can save the X config then simply hit Apply. Resolution should change on the fly. Ive done it with two monitors simultaneously, so I know it'll work.


If you leave the resolution on Auto, it should come fairly close to the resolution you want.

---

### Post by drewtown on 2008-02-27
Well what happens is that it destroys my xorg.conf and goes into low-resolution mode and forces me to reconfigure everytime I switch monitors.

---

### Post by PinkFloyd102489 on 2008-02-27
That's not normal. In fact, Ive never heard of that happening. Did you try running with gkskudo?



Also, make sure the Merge option is selected in the Xorg.conf save dialog.

---

