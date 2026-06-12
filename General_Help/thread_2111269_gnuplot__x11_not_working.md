---
title: "gnuplot / x11 not working"
date: 2013-02-01
forum: General Help
---

### Post by maximovna on 2013-02-01
Hello everybody.
I got a new laptop recently and installed gnuplot. The problem now is, that the terminal type of gnuplot is set to unknown and I can't set it to x11 (with which I guess it should work as it is supposed to do). Now when I try plotting no plot is coming out, just the next command line appears.
I've tried installing different x11-packages, however gnuplot is not recognizing them.
Can you please tell me how to understand if now I have the right x11 package and how to make gnuplot work with it.
Thank you in advance!
Irina

---

### Post by steeldriver on 2013-02-01
Hello and welcome

What terminal types are listed if you type 'set terminal' on its own at the gnuplot prompt?

```
gnuplot> set terminal
```What version of Ubuntu are you running and how did you install gnuplot?

FWIW I believe the default terminal type is now 'wxt' (wxWindows based)

---

### Post by maximovna on 2013-02-01
Hello. Thank you for the quick reply!
I use ubuntu 12.10 (32bit). In the very beginning I installed gnuplot with sudo apt-get install command line, but after trying to fix the problem I reinstalled it with the software centre.
The listed terminal types are:
canvas
cgm
context
corel
dumb
dxf
eepic
emf
emtex
epscairo
epslatex
fig
gif
gpic
hp2623A
hp2648
hpgl
imagen
jpeg
latex
lua
mf
mif
mp
pcl5
pdfcairo
png
pngcairo
postscript
pslatex
pstex
pstricks
qms
regis
svg
tek40xx
tek410x
texdraw
tgif
tikz
tkcanvas
tpic

---

### Post by sudodus on 2013-02-01
after [FONT="Courier New"][SIZE="3"]tpic[/SIZE][/FONT] I have also these

```
          unknown  Unknown terminal type - not a plotting device
            vttek  VT-like tek40xx terminal emulator
              wxt  wxWidgets cross-platform windowed terminal
              x11  X11 Window System
             xlib  X11 Window System (gnulib_x11 dump)
            xterm  Xterm Tektronix 4014 Mode

```

And as as Steeldriver wrote, my default terminal type is 'wxt', which works (can plot in X). I run lubuntu-desktop in Ubuntu 12.04 LTS.

---

### Post by maximovna on 2013-02-01
yes, my mistake
I also have

unknown
vttek

and that's it

---

### Post by steeldriver on 2013-02-01
it looks like you don't have the **gnuplot-x11** package installed - it should have installed as a dependency of gnuplot afaik - unless for some reason your system doesn't support it? you could try

```

sudo apt-get update
sudo apt-get install gnuplot-x11

```... at least if it results in an error it may tell us why

Your terminal list looks like what you'd get with **gnuplot-nox**

---

### Post by sudodus on 2013-02-01
.

---

### Post by maximovna on 2013-02-01
beautiful. I was working with -nox without knowing it. now I get my plots as usual. 
I was also considering installing the LTS, but this will take time, which I don't have now.....
thanks a lot for the help!

---

### Post by steeldriver on 2013-02-01
OK glad that worked - please take the time to mark the thread as SOLVED

For the record, it *does* look like the dependencies have changed from precise to quantal - it has gone from

> 
Precise:

[LIST]
[*]gnuplot-nox      (>= 4.4.3-0ubuntu3) A command-line driven interactive plotting program
[/LIST]

[LIST]
[*]gnuplot-x11      (>= 4.4.3-0ubuntu3) A command-line driven interactive plotting program
[/LIST]

Quantal:

[LIST]
[*]gnuplot-nox Command-line driven interactive plotting program. No-X package     also a virtual package provided by           gnuplot-qt, gnuplot-x11
[/LIST]
[INDENT]**or**     gnuplot-x11 Command-line driven interactive plotting program. X-package also a virtual package provided by           gnuplot-qt     
[/INDENT][INDENT]**or**     gnuplot-qt Command-line driven interactive plotting program. QT-package 
[/INDENT]

---

