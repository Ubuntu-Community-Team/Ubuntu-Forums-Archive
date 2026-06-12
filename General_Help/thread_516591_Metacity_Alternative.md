---
title: "Metacity Alternative"
date: 2007-08-03
forum: General Help
---

### Post by BarfBag on 2007-08-03
I've fought endlessly to get Xine-UI (one of my favorite packages) working properly.  I've come to the conclusion that it's Metacity that's causing my problems.  I need some recommendations for a new window manager, and instructions on how to install it.

---

### Post by Steveway on 2007-08-03
XFWM4?
$sudo apt-get install xfwm4
That should do the trick.
Then in a terminal do this:
$xfwm4 --replace

---

### Post by BarfBag on 2007-08-03
> **Steveway said:**
> XFWM4?
$sudo apt-get install xfwm4
That should do the trick.
Then in a terminal do this:
$xfwm4 --replace

Xfwm4 --replace isn't working.  It spits out an error that says there is another window manager running.  I tried dropping into a virtual terminal and doing it from there, but then it spit out a GTK2 error.

---

### Post by Nekiruhs on 2007-08-03
> **BarfBag said:**
> Xfwm4 --replace isn't working.  It spits out an error that says there is another window manager running.  I tried dropping into a virtual terminal and doing it from there, but then it spit out a GTK2 error.
killall metacity && xfwm4

---

### Post by BarfBag on 2007-08-03
> **Nekiruhs said:**
> killall metacity && xfwm4

Thanks!  That did it!  Is there a way to skin this?

---

### Post by Steveway on 2007-08-03
Sure! Here you can find themes: [http://xfce-look.org/index.php?xsortmode=high&page=0&xcontentmode=420](http://xfce-look.org/index.php?xsortmode=high&page=0&xcontentmode=420)
I prefer the Murrine-XFWM-Theme.

---

### Post by BarfBag on 2007-08-04
I rebooted and it switched back to Metacity.  How do I permanently make it xfwm4?

---

### Post by smartbei on 2007-08-04
Hmmm...When I need to I usually use the berly manager icon to switch window managers - and I don't have beryl running most of the time, it's just convenient.

---

### Post by the yawner on 2007-08-04
> **BarfBag said:**
> I rebooted and it switched back to Metacity.  How do I permanently make it xfwm4?
Try the following:
Alt+F2, then run conf-editor
On the config editor, follow the tree:

desktop>gnome>applications>window manager

Then change the value for default.

---

