---
title: "Crashing with graphical corruption"
date: 2014-05-10
forum: General Help
---

### Post by ggodone on 2014-05-10
Picture of what's happening: [http://i.imgur.com/gstU5Ac.jpg](http://i.imgur.com/gstU5Ac.jpg). The screen just goes like that, and the only thing that does anything is holding down the power button.

I'm on 14.04 and I use Gnome 3.10 as my desktop environment (I'm using standard Ubuntu, not Ubuntu GNOME). I'm on a mid-2012 unibody 13" Macbook Pro with 10GB of RAM (which was upgraded 2 days after updating Ubuntu) and an Intel HD 4000. I'm using the default Mesa drivers that comes with 14.04 (10.2). It's happened today, last Monday, last Sunday, and April 30th or May 2nd. I can't find any crash logs in /var.

---

### Post by tgalati4 on 2014-05-10
Looks like a graphics chip failure.  Try booting with an Ubuntu Live USB stick.  If it happens during a live session, you can be reasonably sure of a hardware problem.

Plug in an external monitor and turn off the laptop screen.  See how long your system stays up.  Have your phone handy to take a picture when it does freeze up.

---

### Post by ggodone on 2014-05-11
Unfortunately I don't have a spare external monitor, and when using the  Live USB I don't have Wifi. Is there any other thing I can do?

---

### Post by tgalati4 on 2014-05-11
Well, you need to find an external monitor--ask around.  If you don't have wireless, then perhaps use an ethernet cable.  Does this machine have Apple Care?

It's possible that you have a problem with the cable that connects the LCD screen.  It's small and runs through the hinge, so it is subject to abrasion.  Does the graphics noise change if you wiggle the screen back and forth?

It's not clear how a memory upgrade would disrupt graphics, however Intel graphics chips tend to share graphics RAM with system RAM.  Try running memtest for 30 complete cycles--it will take several hours.  If your machine locks up during memtest, then I would presume a hardware problem.

If the extra RAM is easy to remove, then remove it and see how the machine behaves.

---

