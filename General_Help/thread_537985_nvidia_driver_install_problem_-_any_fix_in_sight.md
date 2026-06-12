---
title: "nvidia driver install problem - any fix in sight?"
date: 2007-08-29
forum: General Help
---

### Post by dartmusic on 2007-08-29
I haven't touched this in about a month (I just don't have that much free time to spend messing with every possible option), but I still cannot get the nvidia driver (any of the three latest drivers) to install correctly using any option (Automatix, Envy, Restricted Drivers Manager, or manual install as per instructions from the nvidia site).

It seems that I'm not the only person that can't get around this, but I don't see any sort of ultimate fix for this problem.  I've posted numerous times about this issue and some people have tried to help, but even tselliot (creator of the Envy script) could not help and suggested that I go to the nvidia forums for help.  There was no help to be found there, either.  

I really don't want to have to re-install the entire OS, as it would mean quite a lot of backing up and data movement, not to mention reinstalling the OS, downloading and installing all the updates and re-installing MythTV, all to work around just one simple problem -- the same problem that many folks are having.

Has there been any sort of update or change in the last 4 to 6 weeks that I might have missed?

Thanks...

---

### Post by BobLand on 2007-08-29
When you install a driver, do you get an error screen with instructions?  If yes, look at the text very carefully.  Often, it will tell you the version you are trying to install is incompatable with the version in the kernel.  You should be able to see the version number.  Once you find that number, google it and you sould be able to locate the exact driver the kernel wants to see.

I had this problem that drove me nuts for months.  Once I sat down and actually read the error, I discovered I was trying to install an incompatable driver.  Now, everything works OK.

Hope this helps...

bobland

---

### Post by dartmusic on 2007-08-30
The driver (most always) installs without complaining.  It's when I try to re-start X, that it bombs.

---

### Post by rsambuca on 2007-08-30
Unfortunately latest and greatest usually means major headaches and/or complete incompatibility with any linux distro.  I think you will just have to wait until people much more competent than I can create better drivers.

The 8800 is a great card, but not necessarily for ubuntu yet.

---

### Post by phibit on 2007-08-30
A friend of mine recently bought a new rig, with a beautiful new Nvidia GeForce 8800 GS ... I went over to help install ubuntu and get Compiz-Fusion running, and installing the Nvidia Drivers was SUCH A HEADACHE.

We finally got it working though, it involved downloading the drivers directly from the nvidia site, installing them. But there's a bug, and the install doesn't create 2 file links. You need to make them manually. 

I'm at work right now, so I can't really do any of the research, but when I get home I'll try to scrape together a little mini-howto, and post it for you.

---

### Post by phibit on 2007-08-30
Turns out somebody already typed out a detailed guide, so I don't need to make one :)

It's posted here, and it's for amd64, but if you have a i386 chip just download the i386 drivers instead of the amd64 ones:

[http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)

---

