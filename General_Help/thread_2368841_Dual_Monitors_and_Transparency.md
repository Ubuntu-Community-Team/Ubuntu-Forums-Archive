---
title: "Dual Monitors and Transparency"
date: 2017-08-15
forum: General Help
---

### Post by Mr_Troglodyte on 2017-08-15
Hi,
I have a fresh install of Xubuntu and I'm having trouble setting transparency.  I was previously running OpenSUSE Leap 42.2 with no trouble so I expect I've missed an obvious setting somewhere but for the life of me I can't find it.  I do get transparency when using only one monitor.
The briefest of background - I'm using xfce4 as my desktop as it's proven to be the easiest to get twin monitors working under.  If someone can talk me through getting twin monitors work under regular Ubuntu I'll happily change over.  (I tried and couldn't, although the install disk seemed to display both monitors just fine so it's definitely possible) My first Linux Distro was Gentoo back in 2003 so I'm quite comfortable using command line and should it come to it compiling my own kernel.  I can't imagine that will be necessary though.
Here are my system details -


Xubuntu 17.04
cpu:  Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz, 1650 MHz (8 cores)
graphics card:
                       nVidia GM206 [GeForce GTX 960]
                       nVidia GM206 [GeForce GTX 960]


I'm using the nvidia-375 drivers

Thanks for taking the time to read this

---

### Post by Mr_Troglodyte on 2017-08-15
Worked it out.When I used nvidia X server settings to generate an xorg.conf file it added an Extension section with Composite disabled.  I commented that section out and everything is as transparent as I like it to be.

---

