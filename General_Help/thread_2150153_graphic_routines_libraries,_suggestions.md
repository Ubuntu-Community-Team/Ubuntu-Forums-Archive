---
title: "graphic routines libraries, suggestions?"
date: 2013-05-31
forum: General Help
---

### Post by wolframio88 on 2013-05-31
good morning,
I'm doing some simulation and I have a lot of datas to analize. I'm programming in C.
Do you know some good graphic routines libraries to plot the datas? I only need to create histograms and graph, 2D or 3D.
Now I'm using pgplot, but it was meant for fortran; it lacks a proper documentation and some useful routines/subroutines for the C language version.
Any suggestion will be welcomed.
Thanks :D

---

### Post by MG&amp;TL on 2013-05-31
It depends how general you want the library and how much control you want over the output. If you want to be able to draw things exactly how you want it, I'd go for a 3D graphics library, probably OpenGL. Otherwise I would go for [URL="http://libgd.bitbucket.org/pages/about.html"]libGD.
[/URL]
Alternatively, you could just output your data in a suitable fashion and pipe it to *gnuplot* or similiar.

---

