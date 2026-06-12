---
title: "Ubuntu gets unresponsive"
date: 2014-09-08
forum: General Help
---

### Post by mreyna16 on 2014-09-08
Hey guys, I'm not completely new to Ubuntu. I have installed it a couple of times and ran it for a couple of months but do not know the knowledge as far as how Ubuntu works in the background, haven't gotten that far.

That being said, I have a Samsung Series 5 laptop (NP540U3C-A01UB) which has 4GB of ram, Intel® Core™ i5-3317U CPU @ 1.70GHz × 4 processor, Intel® Ivybridge Mobile graphics and is x64. I am running a fresh install with a 5gb of swap and is installed as uefi and no dual boot.

Long story short, I have installed Chrome and have about 20-30 pages open because I am downloading stuff that got erased from my previous windows installation by accident. I notice my computer starts running very slow and the fan is on a lot! I don't know what the problem may be but I have a strong feeling its either my graphics or maybe my hard drive may be failing for some reason. Anyways, how can I find out what is causing the problem? Id like to first try and see if its some sort of software problem then if its a hard disk problem, any help is appreciated!!!

---

### Post by hai3 on 2014-09-08
What about your CPU usage?

---

### Post by mreyna16 on 2014-09-09
ive got about 3-5 items that are using cpu usage under "system monitor" app and the one that is using the most is chrome ranging from 7-13 cpu

---

### Post by claracc on 2014-09-09
I think that with 20 or 30 webpages openned and downloading things, it is normal the computer slows. Perhaps one of the webpages has a lot of graphics stuff.

Try to open less pages at the same time.

---

### Post by mreyna16 on 2014-09-09
> **claracc said:**
> I think that with 20 or 30 webpages openned and downloading things, it is normal the computer slows. Perhaps one of the webpages has a lot of graphics stuff.

Try to open less pages at the same time.

maybe so, but i would like to see if theres a way to see literaly what the problem is, either by using programs or manually checking or etc etc

i wouldnt like to just think what the problem is

---

### Post by grahammechanical on 2014-09-09
Run this command

```
top
```

And sit and watch what is using the CPU and RAM. Or install System Load Indicator (indicator-multiload). That will put an app indicator in the top panel and you can see at a glance what is happening to CPU, memory, and downloads.

Regards.

---

