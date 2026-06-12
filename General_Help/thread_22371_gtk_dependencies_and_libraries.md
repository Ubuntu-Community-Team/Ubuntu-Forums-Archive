---
title: "gtk dependencies and libraries"
date: 2005-03-27
forum: General Help
---

### Post by thierry on 2005-03-27
Hi !

I'm facing a problem with packages (stellarium, eboard) requiring gtk related dependencies and libraries (gdk-imlib1, libglid1.2, libgtk1.2) Install ok, run fine, restarted computer ok, but when I shut down on turning on there's no more display. When in recovery mode gnome-panel I get message gtk warning : cannot open display  :-k 

Does anyone have an idea of what can cause that ? What is here the difference between restarting and turning off ? I looked around a lot in documentation already but couldn't find a possible solution.

Cheers.

---

### Post by thierry on 2005-04-01
Well it seems I found a solution, so here it is maybe it will be useful to someone...

Instead of just installing the dependencies required in Synaptic, I downloaded the whole gnome-bin package, which contains miscellaneous binaries needed by Gnome, including the above mentioned libraries. Better too much than not enough !

Now everything works fine, and I won't try to find an explanation  8-)

---

