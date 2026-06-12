---
title: "Feisty Fawn nearly unusable"
date: 2007-05-11
forum: General Help
---

### Post by Mooseknuckle on 2007-05-11
nForce 680sli MB
nVidia 8800 video
2 gigs ram

In the course of using Gnome, usually after an hour of activity or so, new windows I open up are all black, and existing windows lose their borders.   Only thing that seems to fix this is rebooting the machine ... bouncing gdm doesn't seem to help.

But the real showstopper are the freezes ... Sometimes when browsing the web, the machine just completely 100% locks up.   Cant switch to a terminal or anything.    I dont have capabilites to ssh in to diagnose it ... only thing I can do is a hard reboot.

Everyone is raving about how wonderful feisty is, and I believe they are enjoying it.   I must just be unlucky.

---

### Post by blueturtl on 2007-05-11
Stupid questions first:

1) Have you installed things from unnoficial sources (outside the repositories, or from 3rd party repositories)?

2) Have you overclocked or tweaked your hardware in anyway?

3) Do you have Beryl or Compiz (desktop effects enabled)?

4) Please include more spesific hardware specs.

---

### Post by Mooseknuckle on 2007-05-11
> **blueturtl said:**
> Stupid questions first:

1) Have you installed things from unnoficial sources (outside the repositories, or from 3rd party repositories)?

2) Have you overclocked or tweaked your hardware in anyway?

3) Do you have Beryl or Compiz (desktop effects enabled)?

4) Please include more spesific hardware specs.

1) I've installed Perl6 and Stone Soup Dungeon Crawl ... Doubt those would affect much.
2) Not at all
3) Beryl yes
4) Intel core2 duo with 1mb cache processor, 4 SATA drives ...

Another thing I forgot to mention was that i have 2 sets of plugs on my tower to hook speakers/headphones into.   Only one set is recognized by Ubuntu ... On windows, they both worked.

---

### Post by ronacc on 2007-05-11
youve certaily got pleanty of processor and video horsepower , a couple of things to try would be run without beryl for awhile and see what happens also if you are using the ubuntu driver for your video card (nvidia-glx-new I believe for the 8800)  try the one from the nvidia site and vice versa. also after you reboot do you check your logs to try and find the cause ?

---

### Post by blueturtl on 2007-05-12
My bet is also on Beryl, while it is nice it's essentially beta software. Even Compiz which ships with Ubuntu by default is considered "experimental" and it doesn't have nearly as many effects and things. As the previous poster suggested, disable Beryl for the time being and see if the same things still keep happening. The locking up and graphics corruption might be unrelated, but you'll never know unless you try and find out.

---

### Post by aldreis on 2007-05-12
> **Mooseknuckle said:**
> new windows I open up are all black, and existing windows lose their borders.

Looks like the infamous beryl black windows bug, due to a known issue on the NVIDIA driver. The company is still working on it but, meanwhile, you could try one of the workarounds to reduce this annoying behavior. First ( and easier / simpler ) to try: 

Right-click on the red diamond,  go to *Advanced Beryl Options / Rendering Path* and change it to **Copy.**

---

