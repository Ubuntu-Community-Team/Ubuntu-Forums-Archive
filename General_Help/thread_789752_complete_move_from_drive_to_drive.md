---
title: "complete move from drive to drive"
date: 2008-05-10
forum: General Help
---

### Post by Kirce on 2008-05-10
i have an 80g drive with my current install of Ubuntu hardy and i just bought a new 200g drive and really don't want to reinstall and get all my stuff back, so i was wondering if there is a way i can completely move my current install to the new 200g drive, i was thinking a ghost image of my current install then just move it to the 200g but not sure if it will work and not sure what app to use any suggestions would be great thanks

---

### Post by r76 on 2008-05-13
Partimage sounds like what you need - you make an image of the partition(s).  Good instructions [in this thread]("http://ubuntuforums.org/showthread.php?t=287522").  I'd run it from a live system rescue cd ([here]("http://www.sysresccd.org/Main_Page")).  For example, assuming you have a single 80GB partition plus swap:

1) Using gparted (also on that CD) to create an 80GB partition plus a swap and a ~120GB (whatever's left) partition on the new drive.
2) mount the ~120GB partition, and run partimage - image the 80GB partition on the old drive and save the file into the larger partition on the new drive.
3) to create the MBR I'd use your ubuntu install cd (by installing ubuntu on the empty 80GB partition) but someone else probably knows a quicker way.
4) Once you have this you can just go back to the liveCD and use partimage to extract the image, copying over the partition where you just installed ubuntu.

At this point the 80GB partition on the new drive should be the same as it was on the old drive, plus you now have an extra ~120GB partition (which contains a handy backup image, although you can now do with this partition whatever you like).

---

### Post by chchandler on 2008-05-13
Well, I'm interested in almost the same thing.  I found a thinkpad for a great price with a wiped 40 GB HD.  I've got Ubuntu HH installed just fine but am considering buying a new larger HD to dual boot to WinXP and Ubuntu.  I've got the re-install discs to set the Thinkpad up like new with WinXP, so I'll do that first, then add Ubuntu.  

I know I could just install from the CD and copy my /home over.  That would, however, still leave system tweaks to be re-done, right?

---

### Post by bodhi.zazen on 2008-05-13
I wrote a how-to that covers the issues, can likely be adapted :

[How to run bleeding edge - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=316237") 

The only thing you would likely need to do is install grub into the new HD MBR 

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by Ender305 on 2008-05-13
```
dd if=/dev/[80 gig hard drive] of=/dev/[200 gig]
```

I think that will work, I'm not totally sure though

---

