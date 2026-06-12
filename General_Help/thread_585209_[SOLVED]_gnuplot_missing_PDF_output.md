---
title: "[SOLVED] gnuplot missing PDF output"
date: 2007-10-21
forum: General Help
---

### Post by yang on 2007-10-21
I just installed gnuplot on Gutsy and found a rather glaring hole:

```

gnuplot> set terminal pdf
                      ^
         unknown or ambiguous terminal type; type just 'set terminal' for a list

```

Is there any way to get PDF output, short of recompiling a crapload of stuff as suggested in (the slightly dated) [http://www.miscdebris.net/blog/2007/04/27/install-gnuplot-on-ubuntu/?](http://www.miscdebris.net/blog/2007/04/27/install-gnuplot-on-ubuntu/?)

---

### Post by smoeke on 2008-01-25
I don't know any other way. But I rewrote the howto for Gutsy Gibbon

[http://www.miscdebris.net/blog/2008/01/23/install-gnuplot-on-ubuntu-gutsy-gibbon/](http://www.miscdebris.net/blog/2008/01/23/install-gnuplot-on-ubuntu-gutsy-gibbon/)

In Gutsy Gibbon  gnuplot has now obviously GNU readline compiled in by default. Installing the pdf lite library and recompiling gnuplot is not too complicated, you can skip the instructions about wxwidgets.

Werner

---

### Post by yang on 2008-04-07
Thanks. Those instructions worked, though it'd be nice to not have to jump through those hoops each time.

FWIW, [http://toastball.net/toast](http://toastball.net/toast) helps alleviate these tasks somewhat.

---

