---
title: "Random Crashing After Install and Removal of new HDD"
date: 2007-06-30
forum: General Help
---

### Post by illu45 on 2007-06-30
Hey guys,

A few days ago, I decided to install a new HDD to test Xubuntu 7.10. However, I noticed that after I installed the new drive, my computer began crashing randomly in both Ubuntu (7.04) and Windows XP. I thought that perhaps this was due to the PSU not being able to supply enough power due to the new drive, so I decided to remove it. However, much to my dismay, the random crashing has not gone stopped :(. 

As I said, both Windows XP and Ubuntu crash, when they did not do so before, so I am guessing that it is a hardware, and not a software issue. When WinXP crashes, it is usually in the form of a BSoD, or a hard reboot. In Ubuntu, one of two things happen. Either one program (i.e. Firefox) crashes, at which point no new programs can be launched without crashing instantly, causing me to restart manually. Or, X is restarted and I am greeted with a login screen. Looking at the syslog, the error that occurs when Ubuntu restarts X seems to be:

```

gdm_slave_xioerror_handler: Fatal X error - Restarting :O

```

The PC current has two HDD's, a SATA 37 GB drive and a 80 GB IDE drive. It may be that I damaged the IDE cable while installing/removing the third drive, but I don't think that a damaged cable would case Windows, which has its system files on the SATA drive, to crash. 

Any help in resolving (and/or troubleshooting) the issue would be greatly appreciated,

Thanks,
illu45

---

### Post by illu45 on 2007-06-30
Small bump, I just finished running Windows' CheckDisk utility on both disks, and it found no errors. Will be running memtes86 to test RAM now. Any ideas on what could be causing the problem would be greatly appreciated.


Thanks,
illu45

EDIT: Hm... Running memtest shows errors on two of my four sticks of RAM. Not the first time I've had trouble with Corsair RAM *sighs*. In any case, I've got the other two sticks to use (unlike the last time this happened, when my computer was out for a few weeks while I sent the RAM in to be replaced), so its not too big a deal. Hopefully the RAM was the only problem.

---

