---
title: "Nvidia graphics update gone bad"
date: 2013-04-13
forum: General Help
---

### Post by Rich13 on 2013-04-13
I have a computer that is running Ubuntu 12.04 LTS 3.2.0-39, that was running just fine.  There was a recent update to -40 which included an Nvidia driver update.  I noticed that as soon as the new driver was updated all of the CUDA tasks in Einstein at Home failed with computational error.  I rebooted the system but could only get to a black screen that asked for Username and Password.  Nothing I entered there seemed to work, so I did a web search and eventually found all sorts of suggestions to try, but nothing there worked either, but I then found some comments that this was a symptom of a graphics driver that failed to load.  So that seems to fit the situation.

This computer originally had two partitions, one for 32 bit Ubuntu and one for 64 bit Ubuntu .... the 32 bit install still works.  I downloaded the ISO image for the current version of 12.04 LTS 64 bits and installed it in a new partition split off from the original partition with the original 64 bit install, and that new install works.  I did a memory test, and all passes, so I am pretty much positive it is only a bad graphics driver. However, I would like to repair the original 64 bit installation if I can.  What are the steps I need to take to fix graphics drivers in one partition from an install in a different partition that I cannot boot into ?

Thanks, Richard

---

### Post by deadflowr on 2013-04-13
Do you know which nvidia driver version you installed?
And how did you install this driver? Repos or web.

And for good measure, what is the card (you know nvidia gt XXX, or something)?

---

### Post by layers on 2013-04-13
I always have problems with migrating from nouveau drivers to nvidia. Try booting int osafe mode (holding shift while booting), and then try to follow these:

[http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html](http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html)

---

### Post by Rich13 on 2013-04-14
The card is an EVGA GTX 570.     As far as I know, the original driver (which worked fine) was the default driver loaded when I upgraded to the 12.04 LTS version of 64 bit Ubuntu some time ago   The new (bad) driver was burried somewhere in a long list of software updates that "appeared" in the software update routine.   I don't know what it was, it was only that I happened to catch it downloading a file called Nvidia something, si I immediately got a sinking feeling, but I had already committed to the overall update and couldn't stop it. 

Richard

---

