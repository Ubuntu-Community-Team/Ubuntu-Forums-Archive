---
title: "Intermittent boot problem - trying to diagnose (12.04)"
date: 2013-01-31
forum: General Help
---

### Post by wormbuntu on 2013-01-31
Hi,

Am on the 64bit version of 12.04 on Dell xps L502x. Generally things work ok. I'm using bumbleebee, but other than that everything standard.

Problem I have is that sometimes the system hangs during boot. I've got a black screen full of text, the mouse cursor appears and then... nothing.

Interestingly the last line of text prior to the crash/hang varies. e.g. "Starting crash report submission daemon" or "Stopping save kernal messages". The only unifying factor is the hang, and the mouse cursor appearing.

Any advice on how I can go about diagnosing this would be much appreciated. To reiterate, the problem is intermittent, which is confusing the hell out of me.

---

### Post by dino99 on 2013-01-31
the first step is watching the logs to find usefull errors (.xsession-errors & /var/log/)

---

### Post by wormbuntu on 2013-01-31
Thanks - I was told the logs might not be written to given that the PC crashes totally. That's wrong i assume?

---

