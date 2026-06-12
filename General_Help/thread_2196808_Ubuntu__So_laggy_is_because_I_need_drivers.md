---
title: "Ubuntu  So laggy is because I need drivers?"
date: 2013-12-31
forum: General Help
---

### Post by dafuqmanlolz on 2013-12-31
Hey my ubuntu is very laggy not because i have full RAM or something just idk . Do I need drivers graphics driver or what please teach me how.

---

### Post by deadflowr on 2013-12-31
Do you know what graphics card you have?

If no, then do this
Open a terminal.
Two ways to open a terminal

1)click on the dash icon in the launcher(it is the topmost icon in the panel that is on the left side of the screen)
open the dash and type "terminal" then click enter.
or
2)press ctrl+alt+T at the same time to open a terminal.

Once you have a terminal open, run
```
lspci | grep VGA
```
post the results in this thread.

---

### Post by grahammechanical on 2013-12-31
It would help if you told us the version of Ubuntu and the specification of your computer. I am using Ubuntu Trusty Tahr. That's the next version of Ubuntu that is under development. I have an Intel core 2 Duo CPU running at 2.4GHz with 1GB RAM and a Nvidia GT 220 graphic adapter with 1GB video memory.

I would say that our user experience is very much dependant on the power of the video adapter and the amount of video memory that it has.

Now if you were running  Ubuntu 13.10 I might suggest that you are running in fallback video mode. This mode is fine when we have a video adapter that cannot run accelerated graphics. At least it gets us a working Ubuntu installation. And it is useful if we have problems with video drivers but it does not give the best user experience.

I suggest that you open Additional Drivers and activate either the Nouveau open source driver (it runs my system very well) or a proprietary video driver. I cannot give directions on how to do this because I do not know which version of Ubuntu you are using and Ubuntu is under continue development - things change.

Oh, Ubuntu will use as much RAM as it needs. That is what the RAM is there for, is it not? Ubuntu uses cache memory because RAM has a faster transfer rate than a hard drive. So, it is faster than putting data into the swap partition. This use of cache memory can make it seem that ubuntu is using a lot of RAM. Right now most of my RAM is set aside as either RAM being used or cache memory. Half of the RAM is being used with another third set aside as cache memory. The system is not laggy at all.

Regards.

---

