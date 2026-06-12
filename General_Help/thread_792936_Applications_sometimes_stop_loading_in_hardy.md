---
title: "Applications sometimes stop loading in hardy"
date: 2008-05-13
forum: General Help
---

### Post by Aninhumer on 2008-05-13
Since I installed hardy, occasionally it will stop loading some applications properly until I reboot. gnome-terminal opens but the prompt never appears and it freezes instantly, firefox doesn't load at all, and most importantly, the shutdown dialogue also will not load, although it does stop the panel responding. Also, when I restart X with ctrl-alt-backspace, nothing else loads, and it does not appear to be doing anything, as the hard disk is idle.
There was no output for gnome-terminal or firefox, when I tried to run them in xterm, while this was happening.
It would appear to be just X apps, or even just gnome apps, as if I drop to terminal everything works normally.

I do not think the problem is caused by any particular action, as the same thing has happened when I have left the computer on and come back to it.

---

### Post by truk77 on 2008-06-12
I've noticed this problem as well.  Has anybody come up with any sort of cause/solution for it?

I'm not totally sure, but it seems to happen after I'm running Pidgin and experience a crash with it.

**Edit**: I'm not certain, but it seems like Pulseaudio might have something to do with it.  Try killing all of your pulseaudio instances next time, and see if it fixes the issue?

---

### Post by simonasambler on 2008-06-12
Try to run apps from terminal it, it will write down what is problem and why apps dont start.

---

