---
title: "shrinking NTFS Win XP partition and moving OS and Programs to a smaller drive"
date: 2014-06-05
forum: General Help
---

### Post by 777funk on 2014-06-05
Ok I've been hurting windows by dual booting and messing with it's 'My Docs' files and it's time to clean up my act.

I have XP on a (nearly full) 500GB drive. It's all one partition with the files/docs/etc (the usual windows install). I'm trying to find the simplest path do making this happen and with minimal extra software. I'm the most comfortable using the LiveCD.

I've backed up all the data and deleted all the docs another drive and have deleted the documents to bring XP and my installed software down to 125GB. 
With that done, I'd like to move XP to a new drive.

Is there a way to shrink the partition (GParted?) and move the XP and data (125GB worth) to my smaller 320GB drive? Maybe dd? or maybe even GParteds copy/paste partition? 

I can picture the Windows boot loader getting messed up. Is that as simple as editing boot.ini?

After this is done, I will relocate all the documents and have just the OS's (XP and Linux) on the new drive. I'll be taking care of the XP move first then installing the Linux install.

EDIT!: I just remembered [this "HOWTO" thread]("http://ubuntuforums.org/showthread.php?t=916146") and it mentions this:
[B][I]1. Prepare Windows XP

You NEED to reset Window's information about mounted partitions before you move it! Use "regedit" and delete all entries in 
"HKEY_LOCAL_MACHINE\SYSTEM\MountedDevices". This does not harm Windows since Windows rebuilds these entries on the next startup.

[/I][/B]Is this important in my case?


Would using Acronis True Image in Windows be wiser?

---

### Post by monkeybrain20122 on 2014-06-05
How long do you plan to hang on to XP? It is dead, this necrophilia has to stop. :) Back up your data and blow it away.

P.S. As far as I know gparted and other Linux tools do not work (or don't work reliably) on messing with Windows partitions.

P.P.S What does XP life support have to do with Ubuntu or Linux? You should ask your question in a Windows forum but I expect the response would be the same: bury XP. :)

---

### Post by 777funk on 2014-06-05
LOL on blow it away. I rarely use it (been on 12.04 since it was released) but XP does work fine on my machine when I use it. I just much prefer Linux's file management and tools. 

 I can't blow it away because I still need Windows XP for audio editing. I have $thousands in Hardware/Software for recording music and unfortunately the tools don't work too well in WINE (x-runs, latency, almost enough processing power but not enough I/O speed). In Windows all of this works fine.

So saving the XP install is important in this case. But yes, I agree, living in the past! But as far as Windows, I still prefer XP vs the later MS offerings.

---

