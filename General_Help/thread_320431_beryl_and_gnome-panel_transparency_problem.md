---
title: "beryl and gnome-panel transparency problem"
date: 2006-12-17
forum: General Help
---

### Post by bluemerle27 on 2006-12-17
Have a small problem with gnome-panel transparency/opacity that I was hoping someone might have experience with and know a solution
Basically have set in windows criteria W:DOCK:80 to set the opacity (beryl 0.13 btw). however i notice that at time the panel seems to be more transparent than at other times, ie flucating in transparency. I and using ubuntu 6.10 with XGL and an ati card using fglrx drivers 8.25 that are on the disc. It does not bother me most of the time but was wondering if anyone know about this and might be able to help. It mainly gets more transparent as you click on an object on the panel

Thanks in advance

---

### Post by dad311 on 2006-12-17
I had opacity issues while running  tsclient.   I fixed the problem by setting setting  "XLIB_SKIP_ARGB_VISUALS=1"  before the command.

For example to start tsclinet, I do "export XLIB_SKIP_ARGB_VISUALS=1;/usr/bin/tsclient

---

### Post by mcduck on 2006-12-17
You could try p:Gnome-panel:80 instead. That's what I've been using and I haven't had any problems.

---

### Post by bluemerle27 on 2006-12-17
thanks tryed that but still actually had the same problem. It is only a slight problem and have to be kind of quick to notice it

---

