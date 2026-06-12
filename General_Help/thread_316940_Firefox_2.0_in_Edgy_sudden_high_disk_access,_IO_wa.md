---
title: "Firefox 2.0 in Edgy: sudden high disk access, I/O wait, system load"
date: 2006-12-11
forum: General Help
---

### Post by siennalizard on 2006-12-11
Hi folks.

I upgraded to Edgy about a month ago. I used what I now discover to be the discouraged method (changing the sources.list file and doing "apt-get dist-upgrade"). I have tidied up, and everything seems fine, except Firefox 2.0. The program will run fine for somewhere between 5 and 20 minutes. After that, I will click an ordinary link and suddenly the load meter on the gnome-panel starts to climb up, and the cpu meter shows lots of background activity (which top tells me is the cpu waiting for I/O activity to complete) and the computer becomes unusable. During this time, the hard disk light on my laptop goes solid and the drive churns.

This would not be so problematic if I were actually able to kill Firefox when it happens. Sadly, the computer slows to a crawl, and I can only kill the errant process if I jump in very fast, either with top on a virtual console or by letting Gnome try to close it. Even the mouse pointer is jerky in a manner that I don't expect having been using Linux since 2001.

It is not a reproducible error, though. I am working on Firefox now, but there is nothing to say I will be able to submit this post when I finish it!

I have obviously tried googling around for this problem, but have had no success in finding a similar issue documented. I am using a clean profile with only Adblock and Filterset.G installed. That has improved Firefox start-up times, but the intermittent load problem is still present.

Many thanks for any help or suggestions!
J.

---

### Post by DJ_Peng on 2006-12-11
You may want to grab Firefox directly from Mozilla, extract it and run it form there. You'll have to create your own launcher icons, and you won't have muc support from Ubuntu anymore, but the up side is that you can get updates more quickly (like the upcoming version 2.0.0.1) once it's released. Plus the guys over at the [MozillaZine forums]("http://forums.mozillazine.org/index.php") are great about helping fellow users with problems.

Take it from me, running Fx2 after getting it straight from the source is a piece of cake. It's my default browser and after trying the version that came with Edgy I wouldn't consider getting it any other way again.

---

