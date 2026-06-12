---
title: "[SOLVED] Persistent High CPU Usage"
date: 2007-11-09
forum: General Help
---

### Post by apple_and _linux on 2007-11-09
Even when I have nothing running, my CPU usage is generally staying at 100- dipping down sometimes to 50.  I have checked the process manager and nothing seems to be taking up much processor power...  mostly little processes running at 0 and a few between 1 and 5%.
It's really bugging me.  I think it's making my screensaver act up (as in slow graphics).  It never used to be like this... any ideas?
-Jeremy

---

### Post by skymera on 2007-11-09
go to terminal and type:

top

see what it says

---

### Post by mahiyar on 2007-11-09
If something is running it has to show up, try sorting the the cpu column by clicking at t he top. Maybe the process which isa really is consuming power is below. Also if it is a new Gutsy install the search function takes a lot of power and time to index everything properly.

---

### Post by apple_and _linux on 2007-11-09
Thanks for the answers guys.
However, after some piddling around, I uninstalled "EasyBackup" and now my cpu usage is down quite a bit.  I think it must have been doing stuff in the background.
However, I will keep in mind that "top" thing- it looks cool.
Regards,
Jeremy

---

### Post by skymera on 2007-11-09
no problem, glad its all good :)

---

### Post by mahiyar on 2007-11-10
If you like top there is another programe which I use it all the time it is htop, a small CLI utility.

---

