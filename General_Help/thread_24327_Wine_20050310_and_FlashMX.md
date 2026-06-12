---
title: "Wine 20050310 and FlashMX"
date: 2005-04-06
forum: General Help
---

### Post by ulisse on 2005-04-06
Hi all,
I was succesfully running FlashMX on wine 200412sthg, but since I've updated to 20050310, flash doesn't work anymore.
The splashscreen pops up but only borders are visible.

I think it could be a common issue, because googling a bit I found other people having the seem problem, so I'm thinking to revert to wine 200412xx.
Is it possible? Where can I find the .deb ?

Tnx in advance.

---

### Post by wmcbrine on 2005-04-07
One way:

In Synaptic, find WINE, then go to the Package menu, and select Force Version.

---

### Post by ulisse on 2005-04-08
Tnx for the reply, but it doesn't work.
In the repositories there is only one version available, so the it can't be forced to a prior version.
I also checked the official wine repositories, but there is only the last version too.

---

### Post by ulisse on 2005-04-08
Solved.
I found an *ARGH!* .rpm of the old version on rpmbone, used alien to convert in .deb and succesfully installed.
When the next version of wine will pop up, I'll give it a try.

---

### Post by flyinglizard on 2005-04-08
I ran into the same problem with Lotus Notes,  kept thinking it was Notes related but I finally managed to see that it broke the day after the 20050310 wine update. (April 1 for me)

I just pulled wine from Warty and got it working for now.

Anyone know how to get the 20041201 version of wine?  I tried the morgue ([http://morgue.ubuntu.com/](http://morgue.ubuntu.com/)) but did not see it.

---

### Post by bdbell on 2005-04-10
I found a copy at this site;

[http://tuzakey.com/~scott/apt/binary/old/](http://tuzakey.com/~scott/apt/binary/old/)

does anyone know how to prevent it from being updated?

---

### Post by flyinglizard on 2005-04-10
You should be able to pin wine to the correct version:

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin)

---

