---
title: "SATA install?"
date: 2007-02-07
forum: General Help
---

### Post by Imsati on 2007-02-07
Hello everyone. I recently purchased a new SATA HDD, but none of my Live CD's will install correctly. I've the Kubuntu Dapper CD and the Dapper Alternate CD. When using the live CD, it will stop at the partition section and tell me that it can't proceed. When using the Alternate, it will allow me to partition, but always hangs on the file installs (747 files, hangs at either 306 or 747). And suggestions? Would Edgy possibly be better? Last I tried Edgy, it was new and gave me a bit of problems, but if it's more stable now, I'll give it another go (Love my Dapper though!)

Thanks!

Jay

---

### Post by ^rooker on 2007-02-07
Could you tell us which hardware models (controller, harddisk) are involved. Usually the chipsets are interesting for finding such tricky errors.

I've had nasty problems like that with SATA once and it was because the Marvel-whatever-chip on the disk didn't play well with the SiliconImage chip of my controller.

---

### Post by Imsati on 2007-02-07
SATA HDD is a Maxtor 6V080E0. North Bridge is VIA P4M800 and South Bridge is VIA VT 8237R.  It's a P4MSD800 MoBo.

---

### Post by ^rooker on 2007-02-07
As soon as I've finished dinner, I'll see if I can find out which chipset's used on the Maxtor drive you got.

hm.... coincidence that my drive causing similiar problems was a Maxtor,too? (but it was one of the early SATA drives)

---

### Post by Imsati on 2007-02-07
Would be greatly appreciated, thank you! This is a brand new Maxtor capable of 3GB/sec transfer rates. Only thing I can think of is my Mobo and cables are only good for 1.5BG/sec and that's somehow doing something quirky. I know it's thinking out of the box, but when both the Live CD and Alternate Install fail, gotta look for other reasons.

I'm not dead-set against trying Edgy again, but would prefer to stay with Dapper. If necessary though, I'll try out 6.10 again and see how I fare.

--Jay

---

### Post by Imsati on 2007-02-07
Just one bump before I head off to bed. If no other responses by the morning, I'll just try Edgy.

---

### Post by Coelocanth on 2007-02-08
I don't know if this will make any difference to your problem, but did you set the jumpers on your SATA drive (it's a SATA 2 if it's 3 GB/sec) to throttle it down to the lower transfer speed of your mobo? This may cause all manner of problems if you don't.

---

### Post by Imsati on 2007-02-08
Yes, it's SATA2 and yes, I did set the jumper for 150GB/sec. I'm looking at a new SATA2 capable MoBo and cables, but not sure if I want it yet. XP works fine (shudder).

---

### Post by ^rooker on 2007-02-08
Sorry, but I couldn't find any obvious evidence of your harddisk having known problems with your controller.

Since I guess it's going to be almost impossible to pinpoint the error without an errormessage, I thought of something you might try:

- Boot the Dapper live-install CD (I guess that's default for desktop install).
- DO NOT install dapper on your harddrive.
- Try to partition it manually.
- Move some large amount of data to/from the HDD.

Usually you should be lucky and find some more informative output in 'dmesg' then. In case your system locks up, you might still find something in /var/log/messages?


Oh! and something else: I've found out over the years, that in order to find/fix a hardware problem it's always a good idea to remove **everything** which is not "vitally necessary" for the computer to run (leaving CPU, RAM, graphics and HDD in this case).

Good luck!

---

### Post by Imsati on 2007-02-13
Ok, so on a whim, I decided to try my Ubuntu Live CD and everything installed perfectly the first go-around. Liking KDE better, I loaded on the KDE package on top of the Ubuntu. The look and feel wasn't quite right for me, so I added on the Kubuntu through Synaptic. I set my default Session Login for KDE.

Is it safe to remove Ubuntu from my system now that Kubuntu is loaded? I noticed that the messaging under Request Removal is a bit different for Ubuntu than it is for K/Xubuntu. All I want is a perfect Kubuntu install:-)

Thanks!

Jay

---

### Post by Imsati on 2007-02-14
Well I'm off to work now and unless I hear otherwise, I'll remove the ubuntu package when I get home and hope for the best. I've no idea why the KDE version is giving me so much trouble on this run.

---

