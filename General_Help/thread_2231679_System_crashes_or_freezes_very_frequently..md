---
title: "System crashes or freezes very frequently."
date: 2014-06-27
forum: General Help
---

### Post by ethankschantz on 2014-06-27
It seems like whenever something fails to be extracted correctly, whenever steam fails to install (Which I still haven't been able to get it to do), whenever the download manager fails (which is very rare) or anything of this nature, my computer either freezes or goes back to a command line, which I can't do anything in. it's almost like every time there's a little problem (which is pretty often) my computer just gives up all together. I'm running 12.04 LTS, and I know my CPU isn't the best, so could that have something to do with it? I just want my computer to stop crashing whenever there's a little problem.

---

### Post by ajgreeny on 2014-06-27
So what specs does the machine have, in particular the graphic card, cpu, amount of ram etc etc, and what OS and desktop are you using?  Unity requires quite a lot of machine resources to run smoothly.

If you don't know in detail show us the output of terminal commands ```
lspci
lsusb
free -m
```
one by one, which will give us a good idea of what we are dealing with

---

### Post by ethankschantz on 2014-06-27
I have an Intel Celeron G1610  2.6 GHz processor, 1.8 GB of RAM, using the built-in graphics. As I said I'm using Ubuntu 12.04 LTS. (Sorry, I probably would've posted specs originally had I not made this post tired and frustrated at 3 a.m.)

---

### Post by ajgreeny on 2014-06-27
I suspect that your cpu and integrated graphics are probably borderline for a sensible and effective unity OS.  I have a similar cpu in an old laptop that can not run unity at all, perhaps as a result of the old ATI mobile graphic card in mine.

See what you think of Xubuntu with xfce4, which should run much smoother and hopefully without the freezes.

---

### Post by ethankschantz on 2014-06-27
I plan on upgrading my computer as soon as I have the money after dealing with a few other things, so before I jump into this, are there any drawbacks to using Xubuntu instead of Ubuntu? Would I be loosing anything in the change? I can deal with ubuntu as is for a while if it means a better experience later on.

---

### Post by ethankschantz on 2014-06-27
Nevermind. Running unity in 2D mode fixes my problems for the most part. What it doesn't is mostly avoidable. I'll just stick with that until I upgrade my hardware.

---

### Post by mörgæs on 2014-06-27
No need for new hardware. Just try Xubuntu, or maybe even better Lubuntu 14.04 if you want something fast. 
Buying more hardware is a bad Windows habit.

---

