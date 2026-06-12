---
title: "X11 crashes when using gedit"
date: 2013-01-24
forum: General Help
---

### Post by ubun_tut on 2013-01-24
Hi,

I am accessing my lab's server through my Macbook. The server is running Ubuntu 12.10. I am able to open gedit and make changes to text files, but whenever I save changes, X11 crashes, gedit shuts off, and I get the following error:

[HTML]
(gedit: 11802): Gdk-WARNING **: gedit: Fatal IO error 11 (Resource temporarily unavailable) on X sever localhost:10.0.
[/HTML]

I think this has to do the other X11 warning message that I get. Whenever I log onto my server using ssh -X, I get this warning message:

[HTML]
Warning: untrusted X11 forwarding setup failed: xauth key data not generated
Warning: No xauth data; using fake authentication data for X11 forwarding.
[/HTML]

Anyone can offer any help on this? Thanks.

---

### Post by Calinou on 2013-01-24
Try using another editor such as Geany (graphical) or nano (command line)?

---

