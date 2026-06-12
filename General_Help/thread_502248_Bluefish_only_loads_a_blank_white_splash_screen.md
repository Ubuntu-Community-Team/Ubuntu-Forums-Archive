---
title: "Bluefish only loads a blank white splash screen"
date: 2007-07-16
forum: General Help
---

### Post by drb43 on 2007-07-16
I'm using Feisy 7.04 and recently when I have attempted to open bluefish, all I get is a white splash screen where the usual bluefish logo would normally appear. Bluefish has previously worked and even purging and reinstalling bluefish hasn't helped any.

I'm not sure what logs may be of any and running bluefish from the command line produces no output, but will happily post them if pointed in the right direction!

Thanks for any help!

***UPDATE: Bluefish has now loaded - but a couple of minutes after starting it up and is really unresponsive.***

---

### Post by merlinus on 2007-07-16
Try removing it completely via Synaptic, and then reinstalling.

Sounds like some of its files or configs got corrupted, and your first reinstall did not fix the problems, only overwrote the existing files.

-merlin

---

### Post by drb43 on 2007-07-18
I've done another complete removal of bluefish and a fresh install but I still have the same problem. 

Anyone got any bright ideas???

---

### Post by Alchera on 2007-07-19
Delete the hidden folder (.bluefish ?) in your home directory?

---

### Post by drb43 on 2007-07-22
It turns out my loopback device (lo) wasn't starting up when I booted the computer - changing that solved all my problems.

---

