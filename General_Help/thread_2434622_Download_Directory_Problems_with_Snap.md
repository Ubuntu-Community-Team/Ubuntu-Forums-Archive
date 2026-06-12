---
title: "Download Directory Problems with Snap"
date: 2020-01-08
forum: General Help
---

### Post by angel mike on 2020-01-08
I have a new laptop from Dell preloaded with Ubuntu 18.04.
I tried downloading the drivers for my Brother Printer but they are not appearing in the Download Directory. Instead they went to a 'directory?' which I cannot find on the computer called 'michaelb/Snap/Firefox/Common/Downloads'  I suspect these are stored on Firefox. 
I have never used 'Snap' and see no reason to use it - so would like to remove it from this preloaded version - otherwise will have to load a new OS using USB ISO with Ubuntu 18.04

---

### Post by CatKiller on 2020-01-08
> **angel mike said:**
> I have never used 'Snap' and see no reason to use it - so would like to remove it from this preloaded version - otherwise will have to load a new OS using USB ISO with Ubuntu 18.04

The Ubuntu iso will come with [snaps](https://tutorials.ubuntu.com/tutorial/basic-snap-usage), too.

Snaps are limited in where they can read from and write to. Sometimes that's a useful security benefit, sometimes it's a pain. You can remove the Firefox snap and use a standard apt-get Firefox from the repository.

If you want to get rid of *all* snaps, the key package to remove is **snapd**. I believe the system is sensible enough to remove all the snaps prior to removing snapd, but you can do it yourself first for a belt-and-braces approach. If you're familiar with normal packages, managing snaps will be straightforward.

---

### Post by Dennis N on 2020-01-08
Just change the Downloads directory in **Firefox > Preferences** to the "normal" Downloads folder in your Home. This works for the Firefox snap.

---

### Post by angel mike on 2020-01-09
Thanks - will do both

---

### Post by VMC on 2020-01-09
Not sure what drivers your referring too, or what Brother you have, but I've always used "linux-brprinter-installer-2.1.1-1.gz" to install driver.
Instructions and file found [HERE]("https://support.brother.com/g/b/faqend.aspx?c=us&lang=en&prod=hll2300d_us_eu_as&pfs=1&faqid=faq00100556_000").

On another note, I was impressed that after installing Kubuntu 20.04, my Brother printer driver was installed automatically without intervention?!

---

