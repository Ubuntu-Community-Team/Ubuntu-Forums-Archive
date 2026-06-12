---
title: "Unity and Gnome Classic"
date: 2012-10-20
forum: General Help
---

### Post by SpeedGonzales on 2012-10-20
I've been using Ubuntu 12 for several months.  Unfortunately I can't use Unity because I find it too slow.  I also find it frustrating that I can't add shortcut parameters easily.

Is there a really quick replacement for Gnome Classic which I can use.  I absolutely love speed in an operating system.  I do not use much hardware, just a mouse, keyboard and a monitor.  I just need a fast work horse.

I'm happy to configure Gnome classic or Unity if I can get a bit more speed out of them.  I've installed the 3D acceleration drivers and turned off as many daemons as I can.

---

### Post by kc1di on 2012-10-20
> **SpeedGonzales said:**
> I've been using Ubuntu 12 for several months.  Unfortunately I can't use Unity because I find it too slow.  I also find it frustrating that I can't add shortcut parameters easily.

Is there a really quick replacement for Gnome Classic which I can use.  I absolutely love speed in an operating system.  I do not use much hardware, just a mouse, keyboard and a monitor.  I just need a fast work horse.

I'm happy to configure Gnome classic or Unity if I can get a bit more speed out of them.  I've installed the 3D acceleration drivers and turned off as many daemons as I can.

If your system is that simple why not go to Lubuntu or Xubuntu
if you must have unity or gnome you could try cinnamon but doubt that would add much in the way of speed. 
you can try LXDE by doing the following in a terminal

```
sudo apt-get install lubuntu-desktop
```
then logout and click on the little ubuntu symbol at the login block and select lxde.

the other possibility would be to install the Mate desktop which simulates gnome 2.x
but is not as mature yet.

good luck

---

### Post by Frogs Hair on 2012-10-20
You can also try the LXDE or XFCE session without installing the entire Xubuntu or Lubuntu desktop.

---

### Post by james_mcl on 2012-10-20
I'm a tad hesitant because I am having some teething problems, but in my opinion MATE is very close indeed to the original GNOME 2, and while it does have a few problems there aren't many of them and I've found workarounds for everything so far. I'd say it's certainly mature enough for general use.

LXDE and XFCE are both good as well, of course.

---

### Post by sgage on 2012-10-20
> **james_mcl said:**
> I'm a tad hesitant because I am having some teething problems, but in my opinion MATE is very close indeed to the original GNOME 2, and while it does have a few problems there aren't many of them and I've found workarounds for everything so far. I'd say it's certainly mature enough for general use.

LXDE and XFCE are both good as well, of course.

I find Gnome Classic to work just fine. Have you tried it in Quantal yet? Just

```
sudo apt-get install gnome-panel

```
It also gets brought in with an install of gnome-shell.

It works great for me - fast and minimal, with just enough configurability. 

I tried Mate and was not impressed with its appearance, performance, configurability, or stability. I'd rather stay with the mainline Gnome Project anyway.

---

### Post by kc1di on 2012-10-20
one other possiblity is razorqt it's pretty fast for a qt based Descktop. 

you can find that by following this links instructions
[http://razor-qt.org/install/ubuntu.php]("http://razor-qt.org/install/ubuntu.php")

you just have to try different options until you find the combo that works best for you. 
Good Luck 
:)

---

### Post by SpeedGonzales on 2012-10-20
I installed LXDE, it seems to be running a bit faster.  Thanks for the advice everyone.

---

