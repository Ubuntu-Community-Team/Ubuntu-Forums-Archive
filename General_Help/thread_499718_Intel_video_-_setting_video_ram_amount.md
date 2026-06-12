---
title: "Intel video - setting video ram amount"
date: 2007-07-12
forum: General Help
---

### Post by mykrob on 2007-07-12
Hey-

I have seen a few threads here regarding setting the video ram on an integrated Intel graphics chipset.. None of them seem to have solutions.. I have a Compaq presario v5204nr running Kubuntu feisty. My BIOS does not have an option to change the video ram.. Presumably, there was an application in windows to set this.. I never used windows on it, i erased the hard drive when i got it...

When i was using Mepis, i could set the video ram in the xorg.conf file using the option "VideoRAM" and setting the value to my desired MB * 1024.. This worked fine in Mepis, but doing it in Kubuntu causes X to not load..

How can i set the video ram? I just upgraded my overall RAM to 1GB, so i would like to allocate a bit more than 8MB to video..

```

myk@kubuntu:~$ dmesg | grep agp
[   31.856000] Linux agpgart interface v0.102 (c) Dave Jones
[   31.876000] agpgart: Detected an Intel 945GM Chipset.
[   31.876000] agpgart: Detected 7932K stolen memory.
[   31.892000] agpgart: AGP aperture is 256M @ 0xc0000000
myk@kubuntu:~$


```

thanks,
-myk

---

### Post by bdtgp on 2007-07-12
Are you sure your card doesnt dynamically allocate memory for video?  Most integrated chipsets havea  maximum but they fluctuate based on usage.

---

### Post by mykrob on 2007-07-12
it may, not sure to tell you the truth.. I guess i can just assume it does?

-myk

---

### Post by bdtgp on 2007-07-12
I couldn't tell you either.  One can always hope!

---

### Post by Fadsjeik on 2007-08-11
Hey,

I'm pretty sure it doesn't. I have been trying to run some applications that require more graphical power, but they work sluggish and dmesg | grep agp keeps telling about the 8 mb of *stolen* memory. I wondered whether the new intel driver "xserver-xorg-video-intel" might do a better job, but I ended up not being able to start X at all anymore. I'm still looking into this problem, any suggestions are welcom :). You can always try to install the new drivers and see whether it works for you, if X doesn't feel like starting up you can just change back the drivers to i810 in xorg.conf.

Let me know if you find a solution!

---

### Post by tannerad on 2008-06-12
Hi,

I wondered if anybody has come up with a solution to this problem. I have a Dell Latitude D820 with an Intel 945GM graphics card. The card registers 8MB of memory in the bios and I have 4GB of RAM installed (3.4GB of which the bios recognises - another problem!). I have a dual boot system and in Windows XP I have 224MB registered on the graphics card. 
I am also running Ubuntu 8.04 (hardy) - the 64-bit version as it give me a 30% improvement in processing speed over windows for some applications. I have the Intel graphics controller installed, but am having lots of problems with slow screen update which I feel is related back to the video card - running the same program with cygwin in XP does not give any problems. When I run 'dmesg | grep agp' I get:
[   14.194277] Linux agpgart interface v0.102
[   27.166974] agpgart: Detected an Intel 945GM Chipset.
[   27.170343] agpgart: Detected 7932K stolen memory.
[   27.205516] agpgart: AGP aperture is 256M @ 0xd0000000
Can anybody tell me how to allocate more memory to the graphics card?

Many thanks
David.

---

