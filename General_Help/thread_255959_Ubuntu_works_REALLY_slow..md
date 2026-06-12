---
title: "Ubuntu works REALLY slow."
date: 2006-09-12
forum: General Help
---

### Post by Thanatios on 2006-09-12
Well, I have noticed that my Ubuntu desktop works pretty slow. It feels like I have a windows, that I didnt reinstall for like 1 year.
When I click on Firefox, it takes 6 seconds to finally be started up (While in windows, this is instant).

My system specs are:
Pentium 3 800 MHZ
512 MB RAM
NVIDIA RAVE TNT2 Videocard (I got the Lagacy driver installed)

My OS is:
Linux Ubuntu Dapper 6.06 Dapper Drake 686
DMA is working
Direct Rendering is also working

Also, when I configure the screen resolution. I can't change the HZ. I only can select 60. (While on Windows, I could select 70-75 if I wanted to)

Any suggestions what actually could be wrong?

---

### Post by taurus on 2006-09-12
You can change the horizontal refeshing rate in /etc/X11/xorg.conf!!!

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Thanatios on 2006-09-12
Thanks! I got the horizontal refeshing rate to work. But still, its quite slow.

Another example, is that when I start up Ubuntu, its a bit Windows-like.

It like starts up, you can see the desktop. But then it has to load up Gaim for like 6 seconds, and also another programs. So its quite slow.

Any suggestions?

---

### Post by Amt0571 on 2006-09-12
About the Firefox issue, I also found Firefox slow and finally decided to use Epiphany. Like Firefox it uses Gecko, but on Ubuntu it's a lot faster.

---

### Post by taurus on 2006-09-12
Maybe something is eating up your RAM/swap!!!

```
top
free
```

---

### Post by Thanatios on 2006-09-12
Xorg, python, top and init use the most amount of RAM. 

Can anyone tell me, if I don't need any of these?
Looks like I have 384520 of RAM. And 363284 RAM is being used O.o

Any more suggestions?

---

### Post by NewbieLearnLinux on 2006-09-12
This may help:

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Anyway I think the FireFox on your Windoze has been Optimized whilst the Ubuntu's is not. With your computer I think FireFox usually takes about 4->6 Seconds to load . Not sure if 3 seconds is "an instant", though...

---

### Post by Thanatios on 2006-09-12
About firefox, I whas just giving an example. If I like start up GAIM its the same thing. Or Evolution mail. Also same story.

Any suggestions?

---

### Post by nrwilk on 2006-09-12
> **Thanatios said:**
> Any suggestions?

[Prelink]("http://www.ubuntuforums.org/showthread.php?t=74197&highlight=prelink").  It works well.

---

### Post by nullmind on 2006-09-12
Open System Monitor applet and check if the swap is being used at all. If you change the swap partition (for example from /dev/hda1 to /dev/hda2 when resizing partitions) the swap will fail to mount and you will get really crappy performance.

---

### Post by 3rdalbum on 2006-09-13
Firefox for Windows is more optimised than the one which comes with Ubuntu. Try warm-starting it in WINE (run Firefox in WINE, quit it, run it again) and check out the performance.

Prelinking, preloading, upgrading your memory and using an optimised kernel together produce a great speed improvement.

---

