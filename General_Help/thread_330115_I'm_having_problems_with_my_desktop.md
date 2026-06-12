---
title: "I'm having problems with my desktop"
date: 2007-01-02
forum: General Help
---

### Post by jaimz on 2007-01-02
well xgl ended up crashing on me
and for some reason I can't right click on the desktop anymore 
I can't see the icons either
I can go to the home folder and check the things there but it just doesn't appear on the desktop

also when I log into ubuntu, my wallpaper doesn't load up either
and I was wondering if there's some way I'll be able to fix it

edit - I've also logged onto a gnome session, still the same problem

---

### Post by cmost on 2007-01-02
You appear to to have "really screwed things up!"  To use the technical vernacular.  :-)  Can you provide more details on what you were doing when the problems started?  Which tutorial did you use to install XGL?  Are you using Beryl or Compiz?  Personally, I would simply backup my data and start all over.  That might actually take less time than trying to unravel the mess you're in now.  Good luck!

---

### Post by jaimz on 2007-01-02
well I tried watching a streaming video in full screen while on xgl and then it crashed XD

but no worries, I re-installed ubuntu
not like I had anything important to save
and it won't take me long to set everything back up

=p

the tut I used was.... I can't find it
but it was with beryl
everything worked fine

until that crash, and the desktop was the only thing giving me a problem

oh well!

---

### Post by cmost on 2007-01-02
You may want to try AIGLX instead of XGL, if your hardware supports it.  It's much better than XGL.

---

### Post by jaimz on 2007-01-02
I have a radeon x800
and well... it seems too much of a hassle to get aiglx working
I've tried, failed, so I'll settle for xgl until AMD/ATI decides to add support for it

---

### Post by strabes on 2007-01-03
run gnome-settings-daemon

---

### Post by jaimz on 2007-01-04
gnome-settings-daemon isn't the problem

I already knew about that

I'm was talking about the dekstop only being screwed up

I can do everything minus right click the desktop
as though it's not there, like if it didn't load

and it just happened to me again

Idgi
this time without a crash too

---

### Post by strabes on 2007-01-04
Maybe try "killall nautilus" since nautilus manages the desktop and it would restart it?

---

### Post by jaimz on 2007-01-04
omg thank you!

the problem was that nautilus wasn't loading

XD

---

