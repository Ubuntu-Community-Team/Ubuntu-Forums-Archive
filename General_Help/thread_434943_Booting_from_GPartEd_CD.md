---
title: "Booting from GPartEd CD"
date: 2007-05-06
forum: General Help
---

### Post by merlinus on 2007-05-06
When booting from the GParted CD, it automatically goes into graphics mode, and all I can see is a bunch of colored horizontal bands on my screen.

The same thing happens when I use SystemRescueCD and type startx at the CLI.

I am wanting to change the size of my swap partition, and am wondering if there might be another way?

Many thanks!

-merlin

---

### Post by davezac on 2007-05-06
merlin,
what spec do you have for your machine?
i have used gparted a great deal on several boxes from a low end dell latitude cpi laptop to a higher end desktop machine. all ran fine.

---

### Post by merlinus on 2007-05-06
2.8 Intel processor
Asus 4B533 motherboard
1.5 G RAM
60MB WD hard drive
Matrox P650 graphics card w/ 64 MB RAM
Hitachi CRT Monitor - 1280 x 1024

The vesa video driver installed by Ubuntu works fine.

Is there a way to use the livecd to change the swap partition size, and then allocate the freed-up space to /?

Thanks....

-merlin

---

### Post by davezac on 2007-05-07
have you tested the graphics card on another machine or swapped one into yours.
also try another monitor
try swapping the keyboard also.

are you intending to put ubuntu on this box after partition? - if so the install process takes you through gparted to partition drives/volumes.

there is a command line partitioner available - but i dont know what it's called.

also you can install ubuntu in text mode if you are having problems with the install i.e. conflicts with graphics hardware.

---

### Post by merlinus on 2007-05-07
Ubuntu 7.04 works perfectly on this computer, using the vesa driver for my matrox card.  So this is not an install problem.

I am wanting to boot from the gparted cd in order to re-size my swap partition, and then give the freed-up space to root.  I cannot do this whilst Ubuntu is running.

Thanks.

-merlin

---

### Post by zvacet on 2007-05-07
I don´t understand,because i used Gparted live CD many times and it work great.Another way is to boot your Ubuntu live CD and do i with it.

---

### Post by merlinus on 2007-05-07
Yeah, I don't understand it either.   :( 

But are you saying that booting from the live cd will give me the ability to simply re-size the swap partition and assign the resulting free space to /root, without screwing up my installation?

Thanks.

-merlin

---

### Post by rbmorse on 2007-05-07
Isn't there a way to force gparted to use the vesa video driver?

---

### Post by merlinus on 2007-05-08
Yes, you are correct.  I must have missed that option the first time around.

Works like a charm now....

Thanks!

-merlin

---

