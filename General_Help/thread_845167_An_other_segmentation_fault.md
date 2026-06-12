---
title: "An other segmentation fault"
date: 2008-06-30
forum: General Help
---

### Post by vincentweb on 2008-06-30
Good morning
I used without any problem the flight simulator YSFlight on Gutsy and Hardy.
After having installed Hardy on a new partition, I got this error:
```

    YSFLIGHT
    VERSION 20080220
    YFSVERSION 20080220
    NETVERSION 20080220
    Erreur de segmentation
```
I have a 32bit CPU
After several searches, I've seen it could be come from several reasons:
- a bug, the program would try to access memory that it should not, but I exclude this possibility because the program worked perfectly with Gutsy and Feisty
- my NVidia card, however all the other OpenGL programs work
- the RAM, but it would not explain ysflight is the only application not working

I've tried several versions of the simulator: always the same error

I am not the only person who got this problem, other cases are presented here:
[http://www.yspilots.com/forum/viewtopic.php?t=7057](http://www.yspilots.com/forum/viewtopic.php?t=7057)

The program can be downloaded here
[http://homepage3.nifty.com/ysflight/aircraftsoft/aircraftsofte.html#YSFLIGHT](http://homepage3.nifty.com/ysflight/aircraftsoft/aircraftsofte.html#YSFLIGHT)

Does anyone with the same kernel (2.6.24-19-generic) and using an other distribution get the same error?
It's weird the problem comes from Ubuntu.
Any clue?
Thanks in advance.

---

### Post by barretr on 2008-06-30
I'm experiencing a similar issue, except with Inkscape. I used to have no problem launching the program, now I get a segmentation fault. I'm using 8.04(hardy) and the same kernel (2.6.24-19-generic).

---

### Post by vincentweb on 2008-07-05
I've seen that other people using Fedora or Mandriva don't have this problem. I guess they might have a recent kernel too. 
[http://www.yspilots.com/forum/viewtopic.php?t=6375&highlight=ubuntu](http://www.yspilots.com/forum/viewtopic.php?t=6375&highlight=ubuntu)

Is it possible to install an old kernel for Hardy, and if yes how ?

---

### Post by barretr on 2008-07-14
Did you upgrade to 2.6.24-19-generic? If so, you should be able to select an older kernel in the GRUB loader. I reinstalled 8.04 and am no longer getting a segmentation fault.

---

### Post by YaroMan86 on 2008-07-14
Usually what I do with persistant segfaults is I remove the software through Synaptic, hunt down the source, and compile. I've cleared up a lot of segfault problems that way. Just be sure to compile it into a Debian package so you can come back and remove it, later.

---

### Post by vincentweb on 2008-07-14
Thank you for the replies, but YSFlight is a game which is not open-source, on which I am working to make an add-in. It is distributed only as a binary.
I'll try to reinstall Ubuntu Hardy on VirtualBox, but I'll doubt it'll solve the problems, as several people got the same problem.
I have the kernels
2.6.24-16-generic
and 
2.6.24-19-generic
but on both I have the problem.

I thought with an older kernel than 2.6.24-16-generic would solve the problem, as on Gutsy YSFlight works perfectly.

---

