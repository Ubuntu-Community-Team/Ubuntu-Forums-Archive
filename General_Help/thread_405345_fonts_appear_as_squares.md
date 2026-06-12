---
title: "fonts appear as squares"
date: 2007-04-09
forum: General Help
---

### Post by egrus on 2007-04-09
hi, i run kubuntu and i've noticed that some of the programs i get using apt display squares instead of a font, e.g. mplayer or eclipse. when i start them from a terminal i get error messages referring to pango, which had to install in order to build gtk+. interestingly, mplayer works if i download the source and compile it myself.

does anyone know why this happens? thanks for your help

surge

---

### Post by pointone on 2007-04-10
I have experienced similar problems, too. Notably with xscreensaver and acroread.

I created a live CD from my installed system; this problem only occurred when booting from the CD. On the installed system, everything worked fine. From the CD, fonts in acroread and xscreensaver would appear as empty squares, and Pango-related errors would flood the console.

---

### Post by ryantmer on 2007-04-22
Same problem here, too, only in Ubuntu. Occured after upgrading to Feisty.

---

### Post by mungy on 2007-04-23
same here. anyone know what to do?

---

### Post by tx-doc on 2007-04-23
I had a similar problem with the main fonts used by Gnome (all of the X windows menus were squares) that ended up being a botched installation of fontcontrol from source.  After deleting the files installed by the build from under /usr/local, I forced an install of the original fontcontrol .deb from packages.ubuntu.com using dpkg -i <package>.  It took running "ldconfig" and reloading X  (Ctrl-Alt-Backspace) before everything was recognized properly.

You may want to try reloading the Feisty version of Pango using the packages from packages.ubuntu.com.  Just in case, reload fontcontrol too while you're at it.

---

### Post by ryantmer on 2007-04-23
I fixed mine, by blindly going into Synaptic, searching for "pango" (font thingy), and reinstalling everything that came up, and that solved the problem (after restarting).

---

