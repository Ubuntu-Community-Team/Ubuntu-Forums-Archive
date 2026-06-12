---
title: "Newbie Going Round In Circles"
date: 2008-02-12
forum: General Help
---

### Post by andyguest on 2008-02-12
I'm trying to use wubi to install kubuntu but I'm going nowhere fast.

If I try the 7.04 version then my network card isn't detected.

7.10 detects (and sets up) the network card but then I'm getting an odd error where I can't see menus. If I click on a menu or drop down list there's a flicker on screen but I never see the menu/drop down. I can use the arrow keys to scroll through drop down options but I still never actually see the menu.

8.04 seems to install, no menu problems and the network card is detected but the install turns out to be a live cd rather than an actual install. Any changes I make or software I try to install are lost when I reboot.

I'm going to try a fresh 7.10 install today to see if it was just a glitch yesterday but does anyone have any idea where to start trying to solve the menu issue in 7.10 or the install in 8.04 ?

Thanks

Andy

---

### Post by jan quark on 2008-02-12
8.04 is still only an alpha development version

the release is in April

I would create a new blank partition in windows and install ubuntu on it
I never was a friend of wubi
it is only a virtualization and not a "real" installation, and not so stable as a real one

here is a good guide how to set up a dual-boot machine
[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by andyguest on 2008-02-12
> **jan quark said:**
> 8.04 is still only an alpha development version

the release is in April

I would create a new blank partition in windows and install ubuntu on it
I never was a friend of wubi
it is only a virtualization and not a "real" installation, and not so stable as a real one

here is a good guide how to set up a dual-boot machine
[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

Hmm, yeah. Unfortunately that means getting hold of the IS guys to get someone to come and unloack the machine so I can boot from CD. Wubi looked to be a perfect shortcut. Ah well, long way round I guess.

---

### Post by ago on 2008-02-12
Please use rev410 for the time being
Rev 411-412 are supposed to work with the new ISO which is not available yet.

Do use 8.04, if you still boot into the live CD environment, please type

cat /proc/cmdline 

and post it here.

---

