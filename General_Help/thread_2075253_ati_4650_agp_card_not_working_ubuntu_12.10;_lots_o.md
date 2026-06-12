---
title: "ati 4650 agp card not working ubuntu 12.10; lots of issues..."
date: 2012-10-23
forum: General Help
---

### Post by jsmi on 2012-10-23
I decided to give linux a try without having any exposure to it before. So i installed alongside win7, dualboot. But i forgot to fasten my diapers and here's what happened.

At first it crashed during installation a lot, like dozen times before it installed - monitor corruption and blackout. But it eventually installed and ran OK.

Then i decided to install drivers, so i downloaded the amd/ati proprietary ones. It said it ended with an error, so i rebooted. But then the Unity interface disappeared. I was getting some interface at the screen when i enter my user name and pass, but after logging in there was none. But i could access terminal and start UI applications like google-chrome... So i uninstalled drivers, rebooted, Unity was still gone.

Then i followed this guide: [http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/](http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/)  . I did only this part from the guide:

```
sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-legacy
```

Rebooted, this time Unity appeared. But the card is in VESA mode. Also, there is this logo/watermark in bottom right corner that has the AMD logo and beneath it written "Unsupported hardware."

In the Synaptic manager, in the Installed section, i have this: fglrx-amdcccle-legacy, fglrx-legacy, fglrx-legacy-dev. I can load the catalyst control center and find my card over there, do setting and stuff. But in the System Setting -> Software Sources -> Additional drivers, there is nothing listed.

I installed this jockey-kde thing. It says there is an "ATI Fire GL" driver and it green (in usage)...

Here is what fglrxinfo looks like:

```
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 4600 Series
OpenGL version string: 3.3.11653 Compatibility Profile Context
```

So how can i properly install drivers for my card? I tried doing the things from some of those other threads that deal with the issue, but no success.

---

### Post by Mark Phelps on 2012-10-23
You shouldn't be forcing the installation of fglrx drivers -- unless there is some feature the drivers provide that is critical to you.

I have an AMD 4290 video chipset and I get dual-monitors and full resolution features using the default Radeon drivers.

---

### Post by jsmi on 2012-10-23
> unless there is some feature the drivers provide that is critical to you

Yes, the acceleration. After the installation of ubuntu it was laggy and it didn't recognize the adapter all. Also there is this video acceleration that i'd like to use as well. Has someone managed to do it?

---

### Post by Mark Phelps on 2012-10-23
Ok, understand now.  Didn't know if you were just forcing the install of fglrx drivers out of habit.

I've seen LOTS of threads regarding 12.10 and the "broken" AMD restricted drivers.  Solution generally presented was to remove the fglrx drivers and go with the open source until AMD gets their act together and fixes the drivers.

Which, now that I recall a recent thread, may not really help you -- or me!  I read that AMD has now dropped Linux driver support for anything older than the HD 5xxx chipset.  I checked on the Win7 side and the most current AMD driver that supports the HD 4xxx chipset (what I have) is Catalyst 12.6.  Catalyst 12.8 has been out for a while and I recently saw some threads about 12.09 and beta 12.10.

Unless AMD decides to modify the Catalyst 2.6 restricted drivers to work with Ubuntu 12.10, it's likely that WE are going to be stuck now, as when they did this before, with using the open-source drivers.

---

