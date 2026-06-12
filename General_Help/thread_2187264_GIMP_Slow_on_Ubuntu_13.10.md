---
title: "GIMP Slow on Ubuntu 13.10"
date: 2013-11-11
forum: General Help
---

### Post by cessanfrancisco on 2013-11-11
Symptoms/Problem:  I am using the latest version of GIMP (installed via Ubuntu Software Center) and when I start it, GIMP works fine.  Great, actually.  But over a period of a few minutes (10-20) the performance slows down considerably and GIMP becomes very sluggish.  No other applications exhibit this behavior.  I have posted this inquiry on the GIMP Forum and it was suggested that the cause could be "memory fragmentation."

Operating System:  Ubuntu 13.10

Hardware:  Lenovo Z580, 8GB DDR3 RAM, Intel i5 2.6GHz processor, 750GB HDD

Question:  Is anyone else familiar with this happening with GIMP and Ubuntu 13.10?  Does this sound like "memory fragmentation?"  If so, do you have any suggestions, ideas, and/or solutions?

Thank you in advance.

---

### Post by youroldpalmark on 2013-11-11
I use GIMP daily under 13.10, and I haven't experienced that issue at all. Perhaps there's a particular process you're running in GIMP that has some sort of problem?  I don't know what they're calling "memory fragmentation", unless they think your disk needs to be defragged like folks used to do (maybe still do) with Windows.  It actually sounds sort of like what is usually called a "memory leak", but that's the result of the software (GIMP, in this case), and if that was the problem then everyone would be encountering it.  Perhaps you can tie the problem to a particular task you're performing in GIMP?

---

### Post by cessanfrancisco on 2013-11-11
Thanks for your reply!

It seems to slow down when I am doing any of the following:
1.  resizing image, layer, or canvas
2.  creating borders, drop shadows
3.  crop images

That's pretty much all I've been doing since installing GIMP on Ubuntu 13.10.  I have never used GIMP extensively on any other OS.

Thanks again.

---

### Post by The Spectre on 2013-11-11
> **cessanfrancisco said:**
> 
It seems to slow down when I am doing any of the following:
1.  resizing image, layer, or canvas
2.  creating borders, drop shadows
3.  crop images

What version of Gimp are you using?

I was experiencing similar issues until the Gimp 2.8.8 update.

Here is where you can get the Gimp PPA so you can install the latest version..

[https://launchpad.net/~otto-kesselgulasch/+archive/gimp](https://launchpad.net/~otto-kesselgulasch/+archive/gimp)

---

### Post by cessanfrancisco on 2013-11-11
Thanks for your reply!

I just updated to v. 2.8.8.  I'll keep my fingers crossed to see if that helps.

---

