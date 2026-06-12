---
title: "Damaged Hard drive. Can I scan it to see whats going on?"
date: 2007-03-06
forum: General Help
---

### Post by makhani on 2007-03-06
Hi, I am just making a step from Windows to Ubuntu and have hit a major hardware disaster after only a few hours of of having 6.06 LTS running. I was just getting to grips with Synaptic manager when we had a power cut!  Once the storm settled I attempted to re-boot the desktop on which it is installed and I got pages of error codes relating to bad blocks on the hard drive.
I have booted off CD-ROM and the disks manager displays 3 hard drives, the first in the list is recognised as my Maxtor Athena dive and the other two  are unknown, there are no other hard drives attatched to the system.  I have run fsck on the first drive but I get the following message:
 "Attempt to read block from filesystem resulted in short read while trying to open /dev/hda
Could this be a zero length partition?"

Like I say I'm new to Linux and still haven't grasped it fully but I am now occupied with a problem I had not forseen.  Is the drive damaged beyo:confused: :confused: :) :) :( nd repair or is there something else I should be doing?

many thanks for your time reading this

Jim

---

### Post by K.Mandla on 2007-03-06
It's hard to say offhand. If you're getting bad block messages, then it's altogether possible that the data was corrupted, even if the physical platters of the drive were not damaged. Let's hope that's the case.

If you need to recover data from that drive, look into the dd command, and with some luck you should be able to make a virtual image of the drive and recover some of the information.

On the other hand, if you're prepared to cut your losses, you might try low-level formatting the drive with something like [KillDisk]("http://www.killdisk.com") and starting from scratch.

My sympathies, by the way. It's not a good way to start out with Ubuntu, and I can only say that I've been where you're at before. :-?

---

### Post by viper on 2007-03-06
A nice tool to have in your collection is Hiren`s Boot CD, check out this link 
[http://maxt.dk/archives/2007/01/01/hirens-bootcd-87/](http://maxt.dk/archives/2007/01/01/hirens-bootcd-87/)

---

### Post by makhani on 2007-03-06
Well Killdisk could not find my hard drive and I am getting "Primary hard disk drive 0 failure" now, so I guess it is for the recycling bin!  Fortunately no data was lost.   

I have an identical drive with data on, so could hiren help me to partition the data and then install Ubuntu which in turn would of course let me back up the data from this drive using my USB DVD writer.  

Until my clash with the elemnets I was having a great time wit Ubuntu, like I read it just works. No hassle that I've had before installing various windows platforms. Online with just one simple connection of the cable - awesome! 

Thanks for your help will move on to plan B tomorrow.  Still can't believe how good Linux is, to know such help is so close to hand is great

jim

---

