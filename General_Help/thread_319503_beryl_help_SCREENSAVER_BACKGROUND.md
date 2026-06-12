---
title: "beryl help SCREENSAVER BACKGROUND"
date: 2006-12-15
forum: General Help
---

### Post by pedwards on 2006-12-15
hey just looking for a walk through about how to make you background an active screen saver in beryl
thanks.

---

### Post by mcduck on 2006-12-15
first, you need to install xwinwrap. it should be in Beryl repositories, at least it's in the SVN packages repo I'm using.

There isn't much documention about how to use it but I'll paste here what I've gathered and some examples:

```
____________________________________________
FS is fullscreen
S is sticky
ST Skip Taskbar
SP Skip Pager
A Above
B Below
NF No Focus
O Opacity, followed by alue between 0.0 and 1.0
ARGB is for alpha-rgb colors

G is probably for Geometry
_____________________________________________

Movie as background:
xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet /path/to/movie.mpg

Matrix on foreground:
xwinwrap -ni -argb -fs -s -st -sp -a -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID -delay 10000

Matrix background:
xwinwrap -ni -argb -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID -delay 50000 -no-fog -density 40

Nice slowly changing colors:
xwinwrap -ni -argb -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/plasma -window-id WID --maxfps 10 --nice --speed 2 --resolution 10

Matrix:
xwinwrap -ni -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/xmatrix -window-id WID -delay 50000 -density 60

Slideshow:
xwinwrap -ni -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/glslideshow -window-id WID -duration 30 -pan 15 -fade 10 -clip -delay 50000

```

screensavers are located in /usr/lib/xscreensaver, and you can get their options with 'man appname', then just play with different settings to get the effect you want.

If you want you can even run many screensavers at the same time to get freaky layered effects ;)

---

### Post by cmost on 2006-12-15
Found this guide after less than a minute of googling your query.

Link:
[http://forum.beryl-project.org/viewtopic.php?t=246&sid=0b832a47ef3575274ed926f217dbc566](http://forum.beryl-project.org/viewtopic.php?t=246&sid=0b832a47ef3575274ed926f217dbc566)

Hope it helps.

---

### Post by pedwards on 2006-12-15
thank you for your help :)

---

