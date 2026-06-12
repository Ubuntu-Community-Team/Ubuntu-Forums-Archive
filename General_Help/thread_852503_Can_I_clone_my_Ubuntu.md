---
title: "Can I clone my Ubuntu?"
date: 2008-07-07
forum: General Help
---

### Post by the lemming on 2008-07-07
I've managed to get Ubuntu ticking over nicely but before I start to experiment further is there any way I can make an exact copy of the OS which I can use to recover from a disaster?

Cheers

---

### Post by Spaceman9 on 2008-07-07
SystemRescueCD and bootcd are both very good. Have a look at this thread 

[http://ubuntuforums.org/showthread.php?t=837799](http://ubuntuforums.org/showthread.php?t=837799)

---

### Post by bodhi.zazen on 2008-07-07
There are several methods.

[uhelp]community/BackupYourSystem[/uhelp]

---

### Post by the lemming on 2008-07-08
> **Spaceman9 said:**
> SystemRescueCD and bootcd are both very good. Have a look at this thread 

[http://ubuntuforums.org/showthread.php?t=837799](http://ubuntuforums.org/showthread.php?t=837799)

I've tried to find these applications in the Synaptic Package Manager but I can't find them.

Could somebody please explain how I can find them?

Cheers

---

### Post by Spaceman9 on 2008-07-09
Sorry I should have told you how to get these.

System Rescue CD [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

bootcd is in Synaptic. Click the Search button on Synaptic and type in bootcd. You have to run bootcd in a terminal by typing bootcd then hit enter. If you need root permission type sudo bootcd.

System Rescue CD uses GParted to create a new partition for your disk image. It uses Partimage to create a disk image. GParted is installed on your hard drive when you install Ubuntu. It's under System>Administration>Partition Editor. You can install Partimage from Synaptic. Again do a search in Synaptic to get it from Synaptic.

I think it's always better though, when you're working on a hard drive, to not run the programs you're working with from the hard drive you're working on. This is why I'm telling you about System Rescue CD.

This tutorial is for System Rescue CD and will tell you how to create a drive image with GParted and Partimage [http://lifehacker.com/software/geek-to-live/partition-and-image-your-hard-drive-with-the-system-rescue-cd-292972.php](http://lifehacker.com/software/geek-to-live/partition-and-image-your-hard-drive-with-the-system-rescue-cd-292972.php)

---

### Post by nyarlatotheph on 2008-08-05
Thanks to everybody, I had the same problem of The Lemming, and I got a liveCD of Gparted. Playing around, I have found out how to move/resize partition, but I dont have totally clear how to restore the image I have burnt of the linux partition, one day that my system is totally messed up and I want to instantly go back to the old configuration...:confused:

---

### Post by bodhi.zazen on 2008-08-05
Depends on what and how you are backing up.

I personally use partimage 

Here is a tutorial :

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

