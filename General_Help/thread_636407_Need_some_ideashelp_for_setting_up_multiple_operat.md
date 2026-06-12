---
title: "Need some ideas/help for setting up multiple operating systems (primarily Ubuntu)"
date: 2007-12-09
forum: General Help
---

### Post by Compeek on 2007-12-09
Hello everyone,

I'm fairly new to Linux. A couple of months ago I got into trying out Linux, but I haven't done much until now. I just got an old computer from somebody (Pentium II 450MHz, 128MB of RAM), and I decided to put Linux on it. I chose Kubuntu because I figured it was my best bet for a balance of speed/graphics/user-friendlyness. I think I was right.

Anyway, sometime in the near future I would like to build an "ultimate test PC." I would probably need a newer PC than the old one I got, or at least I would need to upgrade it. But what I want to do is set up a PC with multiple Linux operating systems. I'm talking like 10+ if possible. I will get a large HDD or two for this.

This is where I need help. I need to figure out the best way to set this up so I can easily use multiple operating systems all installed on the same PC.  I want to have a shared data partition where I will store my data.

I have read lots of people saying the best way to partition your hard drive for Ubuntu/Linux is to have a partition for like every folder: usr, var, tmp, etc. I have read other people saying you really only need three: swap, \home, and \. Which way would you recommend for me? I need to have multiple Linux OS's that don't interfere with each other, and I need to make sure the setup is not overly complicated. I'm not really worried about losing my programs if I reinstall Ubuntu or something like that, so I don't think I need to go crazy with partitions like some people do. I think the setup I will aim for is one swap partition for all OS's to share, one data partition for all to share, and then one partition for each distro of Linux. Does this sound like a good setup?

Is about 5 - 10 GB enough space for a typical installation of Linux?

My next question is on the topic of swap partitions. Some say it should be around 2x your RAM, others say no more than like 512MB is necessary. What is the best way to go? I have this old hard drive that says 545.5 MB on it. I think I could use the whole drive as one swap partition. This could be advantageous because the swap partition would be at the beginning of the drive (since it would be the only thing on the drive), but maybe it doesn't matter. Would it be a good idea to use this, or would I be better off just making a partition on the main drive?

Lastly, I might at some time put Windows on this computer. I know Window's has to have to the C drive, so I don't know how well that would work. Do I pretty much have to install Windows first before I install any other operating systems? Or will I be able to do it later with minimal problems? On the other hand, it might be easier to just forget it all together and stick with Linux for this computer.

This brings me to my last question. You can only have 4 primary partitions on a hard drive. Linux can boot from a logical partition as far as I know. However, how should I work this? I guess one primary partition for swap, one for data, and one for all my Linux OSs. The one for all the OSs would have to be an extended partition split up into one partition for each OS.

Sorry about the long post and the many questions, but I really appreciate the help! :-)

---

### Post by HermanAB on 2007-12-09
The best way to experiment with various systems, is to install one and keep it running properly, then experiment inside virtual machines: [http://vmware.com/download/server/](http://vmware.com/download/server/)

You can then experiment to your heart's delight without screwing up your base machine.

Cheers,

Herman

---

### Post by Compeek on 2007-12-09
Thanks for the suggestion, but I really would like to install multiple OS's on the PC itself. I've used virtual machines before, and they are nice, but I mostly think it would be fun to do what I explained before.

---

