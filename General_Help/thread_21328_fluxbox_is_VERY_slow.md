---
title: "fluxbox is VERY slow"
date: 2005-03-21
forum: General Help
---

### Post by arnoct on 2005-03-21
Sorry about posting this here, but I think the "other desktops" section is locked...

I recently apt-getted fluxbox. It's pretty cool; I like the minimalism. I'm having a problem with it, though, and that's that it's running VERY slowly. Some things will be very fast, but occasionally it'll hiccup and be very sluggish. For such a lightweight windowmanager, doing things like loading the wm or changing the skin shouldn't take upwards of a full minute, when doing the same thing on GNOME or xfce is instantaneous.

Any ideas?

---

### Post by bigzak on 2005-03-21
Not sure if it's the same, but Fluxbox has some real problems if the L12N environment is not properly configured. More detail here:

[http://fluxbox.sourceforge.net/docs/en/faq.php#slowstartup](http://fluxbox.sourceforge.net/docs/en/faq.php#slowstartup)
[https://www.redhat.com/archives/fedora-list/2003-December/msg04280.html](https://www.redhat.com/archives/fedora-list/2003-December/msg04280.html)

You could try editing the fluxbox session in the GDM configuration with the following line:

export LC_ALL=C

before the startfluxbox command

---

### Post by liquid on 2005-03-21
give a chance to openbox, it's much more fast than fluxbox
[http://icculus.org/openbox/](http://icculus.org/openbox/)

---

### Post by arnoct on 2005-03-22
K, I tried that, it seemed slightly faster but I don't know if it fixed the problem.

As for openbox, I apt-getted it... It's good, but useless for me since it doesn't come with its own taskbar and using gnome-panel with it is very very unreliable =\

---

### Post by az on 2005-03-22
Not that this addresses the real bug, but have you tried icewm?  It is just as fast as openbox or fluxbox and has a great panel.

Insofar as blackbox, can you reproduce the problem?  Does it happen when you do something specific, or is it just random?


Also, try opening a terminal and running top to see what is chewing up cpu power.




Icewm has a neat little cpu monitor in the bottom corner....
When my two-year-old is waiting for something (tuxpaint) on her 167Mhz laptop, she points to it and says "Its green, I'm waiting."

---

