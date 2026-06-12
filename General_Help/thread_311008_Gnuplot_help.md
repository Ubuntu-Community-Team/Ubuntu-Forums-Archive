---
title: "Gnuplot help"
date: 2006-12-02
forum: General Help
---

### Post by Arrhenius on 2006-12-02
I want to plot in gnuplot the function [IMG]http://algol.fis.uc.pt/quark/latexrender/pictures/c06a7dd2d438f9fbfc5e2fd7b939cd73.gif[/IMG], with the range being:

0<z<3
-5<x<5
-5<y<5

What is the command?

Thanks in advance, fellows.

---

### Post by Arrhenius on 2006-12-02
Help.

---

### Post by jazzgossen on 2007-01-19
You should read the gnuplot documentation on "plot" and "splot" (type "help plot", for example).

Try this:
splot [-5:5] [-5:5] [0:3] -x*x/8 - y*y/8 + 2

---

