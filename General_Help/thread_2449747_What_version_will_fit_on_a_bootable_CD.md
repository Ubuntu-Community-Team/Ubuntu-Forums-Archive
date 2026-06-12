---
title: "What version will fit on a bootable CD?"
date: 2020-09-01
forum: General Help
---

### Post by fran_3 on 2020-09-01
- I've got a very old 32-bit PC with only 1GB of ram and a 20GB hard drive. I'm trying to save it from the landfill :-)
- It's an old IBM all-in-one NetVista X41 and it can only boot from the hard disk or a CD... it seems.
- It was running Microsoft XP before things stopped working... for whatever reason.
- I found an old  Ubuntu bootable CD from 12-20-10 in the bottom of my desk drawer and it worked! 
- The PC booted up and the Ubuntu version turned out to be 10.1. Wow!

So, the computer works... and I think I have a dedicated use for the old clunker.

My Questions...

1 - What is the most current 32-bit Ubuntu version that can be installed on a boot-able CD?
2 - Newer Ubuntu releases no longer include the 32-bit option... right?
3 - What about lubuntu or some such?
4 - Are the old Ubuntu versions safe?

FYI, I understand that newer apps probably won't work on the old version but I think what comes with the distro will do fine... with no updates.

Thanks for any help.

---

### Post by Yellow Pasque on 2020-09-01
Lubuntu 18.04 alternate installer should fit on an 80 minute CD-R.

---

### Post by GhX6GZMB on 2020-09-01
The newest and lightest you'll find is Lubuntu 18.04.5, and even that will groan with just 1 GB RAM. If you can upgrade to 2 GB (or even just 1.5 GB) somehow, things will look much brighter.

CAREFUL: lubuntu.net is NOT the official site, but is owned by a cybersquatter.

[www.lubuntu.me]("http://www.lubuntu.me") is the right place.

Good Luck.

---

### Post by Yellow Pasque on 2020-09-01
You can find the alternate installer here: 
[http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/)

---

### Post by crip720 on 2020-09-01
Lubuntu 18.04 will run with those specs, but will have to take it easy and not try running a browser with many tabs open, or too many programs open at once.  Two or three tabs on one browser and maybe one other light program you will be okay.  Think Lubuntu 18.04 only has about one more year of support, if you want to be safe on internet, there are a few other small Linuxs that you might want to check out after.

---

### Post by Impavidus on 2020-09-02
> **fran6 said:**
> I'm trying to save it from the landfill :-)
Do they still send old computers to a landfill where you live? Where I live, most of it is recycled, the rest incinerated (heat is used for city/greenhouse heating), more raw materials are extracted from the ashes and only a few percent is dumped in the landfill. Recycling of electronics is quite efficient.
> 
1 - What is the most current 32-bit Ubuntu version that can be installed on a boot-able CD?
2 - Newer Ubuntu releases no longer include the 32-bit option... right?
3 - What about lubuntu or some such?
4 - Are the old Ubuntu versions safe?Only 18.04 still has support for 32 bit and that support will end in April 2021. All Ubuntu flavours are from the same repositories, so they have the same support for the same software, but only the light flavours come with a 32 bit installer, and only up to 18.04. Versions of Ubuntu that are still supported are safe, versions that are no longer supported should be considered unsafe. Not all packages from the official repositories have the same support period. The core packages from regular Ubuntu get 5 years, the packages for the flavours get 3 years, both on LTS releases.

You may have a use for that old computer, but there comes a time when you have to decide whether a new computer could do the same job for less electricity and the raw materials from that old computer could be put to a more efficient use.

---

### Post by guiverc on 2020-09-02
I'll agree with prior comments.

The Lubuntu 18.04.5 ISO is larger than will fit on a CD.
Lubuntu 18.04 alternate ISO will ([https://lubuntu.me/downloads/](https://lubuntu.me/downloads/))

Your machine will possibly require the use of `forcepae --forcepae` to boot the ISO; I know I need to use it on old ibm thinkpad r50p & t42p  (but don't need to for later t43..)  This is not a problem with Lubuntu, but an unfixed flaw in early pentium M cpus, refer [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

My r50p only has 1GB of ram, and I still use and love it. However I'm careful with what applications I use on it as 1GB is a small amount of RAM today. It's actually currently on (*it's always on really, but it's not what I'm using here though,  I don't use it for browsing*).* I've still use a t42p & t43 as well for other duties, but they have more RAM.*

However your results may differ as what is important is the amount of RAM usable to the OS and not how much is installed. I used a HP d220 machine this week, and it also reports having 1GB of RAM so I expected the same results as my r50p but nope. I could not stream a music vid off youtube without it stopping for buffering as it lacked the RAM. Turns on the HP d220 may have 1GB of RAM,  but only 732MB is available to the OS, where as my r50p has 1GB available (*the r50p has separate ram for GPU, the d220 does not etc*)  I don't know your model.

Lubuntu 18.04 is still fully supported to 2021-April (or three years from release which was in 2018-April). The base of Lubuntu will get security upgrades until 2023-April (5 years) however Lubuntu support (ie. desktop and non-core Ubuntu software) ends after 3 years.

FYI:  It won't have been Ubuntu 10.1; there was no release in 2010-January, it'll likely be 10.10 meaning the 2010-October release of Ubuntu. The format of releases is *year.month*

---

### Post by CatKiller on 2020-09-02
> **Impavidus said:**
> You may have a use for that old computer, but there comes a time when you have to decide whether a new computer could do the same job for less electricity and the raw materials from that old computer could be put to a more efficient use.

Yep. A Raspberry Pi would use way less power and perform better, and those old components could be recycled. The OP might even be able to mount it inside that all-in-one chassis to reuse the display and speakers, depending on what it's like inside.

---

### Post by GhX6GZMB on 2020-09-02
BTW, on that HW I wouldn't even think of running FireFox. Go for a lightweight browser with proper memory management, eg, Opera.

---

### Post by CelticWarrior on 2020-09-02
While agreeing with all the comments above, let me add that the "fit on a CD" is a false problem because we have PLoP: [https://www.plop.at/en/ploplinux/downloads/full.html](https://www.plop.at/en/ploplinux/downloads/full.html)

Download and burn the PLoP ISO in a CD.
Make a BIOS bootable USB installation media as usual (here the size doesn't matter).
Boot from the PLoP CD with the USB already inserted. In the PLoP menu select the USB boot. Install as normal*.

* Given the machine, "normal" here means tasking into account everything commented above.

---

### Post by guiverc on 2020-09-02
Question also asked on [https://discourse.lubuntu.me/t/bootable-cd-lubuntu-version-needed/1530](https://discourse.lubuntu.me/t/bootable-cd-lubuntu-version-needed/1530)

---

### Post by HermanAB on 2020-09-03
Hmm, your machine is very old and 32bit.  I recommend using OpenBSD or Slackware on it, not Ubuntu.

---

