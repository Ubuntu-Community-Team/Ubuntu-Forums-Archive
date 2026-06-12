---
title: "color corruption in Ubuntu 6.10 with nv or nvidia driver"
date: 2006-11-07
forum: General Help
---

### Post by stefano75 on 2006-11-07
Hi everybody,
I'm running Ubuntu 6.10 on x86_64 machine.
I experiment color (pixel) corruption in all the images.
I own a Nvidia 6600GT AGP video card.
The problem arises with open nv or binary nvidia driver.
I've already posted the problem on the nvidia forum.
There some users have experimented the same behaviour and finally I guess that is a xorg 7.1(.1) problem.
Before filling a bug report addressed to xorg team I woul like to know if anyone in this forum has the same trouble.

TIA
Stefano

---

### Post by pureblood on 2006-12-27
I have the same problem. When I start the X server, both with the nv and the nvidia drivers, the colors are corrupted. I have the problem on two different machines and I use on them the 64 bits version of ubuntu edgy 6.10. I have noticed, though, that it is enough to switch to console mode (with Alt+F1) and back to graphic mode (with Alt+F7) and the problem is fixed. Nevertheless, the problem respawns when you reboot the machine. Did you find a solution to that?

---

### Post by barkholt on 2007-01-06
I have the same problem on a 32bit 6.10 installation...

---

### Post by pureblood on 2007-02-08
I am really upset about this problem because after a month I still haven't found anywhere on the internet where they explain how to solve it. It seems like an Xorg 7.1 bug but I am surprised that there is still no solutions for something so important.
This bug makes the computer multimedially useless for the inexperienced user. Anyway, someone talks about it in this forum:
[http://www.nvnews.net/vbulletin/showthread.php?t=77435](http://www.nvnews.net/vbulletin/showthread.php?t=77435)
But the solutions they talk about did not work for me.
Has anybody found anything on the Xorg forums? Could you post a link here if you find?

---

### Post by pureblood on 2007-03-25
I just discovered that if you run a program like lbreakout2, the problem suddenly disappears (you can put that program in your autostart). There must be some kind of SDL call that restores the parameters to what they should be. Since no solution has been found to this problem, I hope that the new Ubuntu with X.org 7.2 will just not be affected.

---

