---
title: "LiveCD works, but every clean install is painfully sluggish - 4GB RAM is CRAWLING"
date: 2015-01-25
forum: General Help
---

### Post by hot.sauce.jake on 2015-01-25
Embarrassingly enough, I spent most of my weekend troubleshooting my Ubuntu install.  It always works wonders from the liveCD (both usb and DVD), but a fresh install is SLOW.  I'll try to open the terminal to get updates and that takes a minimum of 10 minutes.  Every time I try the top command - nothing seems out of the ordinary.  The RAM usage is under a gig and the CPU isn't being hogged.  I've tried several different proprietary and other-sourced nVidia drivers to no avail.

I even tried several different distros (Ubuntu based) with the same issue: liveCD is "fast" but after installation a clean install makes doing anything extremely slow.  Fedora seemed to work the best (same issue in the beginning but after running an update things started to speed up) but I didn't use it for more than 30 minutes because I wanted an ubuntu-based distro.

I have looked at countless google searches on speeding things up - still no solution.  To be honest, I don't know what all I'm supposed to be looking for.

I have a Dell Latitude E6400 (laptop).

[TABLE]
[TR]
[TD="class: field"][/TD]
[TD="class: value"]2x Intel(R) Core(TM)2 Duo CPU P8700 @ 2.53GHz[/TD]
[/TR]
[TR]
[TD="class: field"][/TD]
[TD="class: value"]

[/TD]
[/TR]
[/TABLE]

4GB RAM
320GB HDD

---

### Post by sudodus on 2015-01-25
- Please tell us about your graphics chip. You might have problems with the graphics driver, and that it is bypassed by the live system.

Which proprietary drivers did you try? Did any of them work at all?

Which version of Ubuntu are you running/testing? 14.04.1 LTS ?

You could try Xubuntu with a medium light desktop environment instead of standard Ubuntu. That way the computer might work well enough, that you can really start exploring what is slowing it down.

- There might also be problems with the internal drive (hard disk drive). Please check the S.M.A.R.T. status in the BIOS menu.

---

