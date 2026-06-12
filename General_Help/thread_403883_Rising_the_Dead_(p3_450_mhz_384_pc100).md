---
title: "Rising the Dead (p3 450 mhz 384 pc100)"
date: 2007-04-07
forum: General Help
---

### Post by Sugi on 2007-04-07
So, I'm on break from college and got a little board back at home.  So I thought I would build an old machine.  (I use to work at high school and got all the left over hardware.)  I built a p3 450 mhz, 384 mbs pc100, some shitty video card (i think some random video card with 64mbs for the ram), i think 3 gigs for the hard drive, and a cd drive.  That's my rig.

After doing a good amont of research I found out there should be no problem for running ubuntu on this rig.  I download 6.10 version with x86 bit, but I ran into some problems.   The cd drive sees ubuntu disc and everything and i click install, and then it gets stuck after loading the load screen.  It sticks at the black screen with the beeping underscore at the top left hard area of the monitor.  I letting it load for 24 hours (actually I had to run off and I kinda forgot about it for 24 hours.

What could be my problem?  Could it be the video card? what happens if it doesn't have enough video ram (it might be a lot less than 64mbs for the ram.)  I could always easly upgrade the video card and the hard drive, but is there another problem I'm not seeing here?

---

### Post by eggdeng on 2007-04-07
I got ubuntu 6.10 (Edgy) running on a P3 at 667MHz with 512MB SD RAM PC133. The graphics card is an ATI with 64MB. Everything runs fine though OpenOffice takes about 15 secs to load, Firefox 4 or 5 and torcs is slow and jerky. I even got Beryl up and running but it slows everything so much, I just leave it turned off. 
So the problem is unlikely to be your specs, could be bad hardware or a badly seated card or something. Why don't you try booting from something else, like the GParted live CD, for example. [http://gparted.sourceforge.net/download.php?](http://gparted.sourceforge.net/download.php?) to make sure the hardware is OK.

---

### Post by solar george on 2007-04-07
Try using the Ubuntu alternate install CD, it is better on older harware. 

I got Xubuntu running on a 300mhz laptop by using the alternate cd.

---

### Post by Sugi on 2007-04-07
I ruled it out as bad hardware.  Most likely it was the video card or something down the line as that.

But I got another problem now,  I can't get the sound card to work.  How should I even start to trying to fix that problem?  Maybe get drivers or something?  Can I get a list of my hardware or something from my rig?

P.S. Mari is cool and has big titz


The title should be "Raising The Dead"  oooops

---

### Post by eggdeng on 2007-04-08
Open a terminal and type ```
lspci
``` to get a list of all devices on the pci bus, including your sound card and ```
lsusb
``` for usb devices.```
cat /proc/asound/cards
``` ```
cat /proc/asound/version
``` and ```
cat /proc/asound/modules
``` will get information about the alsa soundcard driver.

---

