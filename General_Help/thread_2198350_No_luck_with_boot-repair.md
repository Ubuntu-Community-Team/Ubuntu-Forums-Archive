---
title: "No luck with boot-repair"
date: 2014-01-08
forum: General Help
---

### Post by vincent.fortin on 2014-01-08
Hi,

I have both Windows 7 and ubuntu 10 installed on my DELL M4500 laptop.

I recently started to experiment problems with my Windows OS, which would freeze shortly after starting up. It worked fine in failsafe mode.

Last night I launched CHKDSK to see if there were any bad sectors on the disk, and today I woke up with the dreaded "grub rescue" prompt. I guess I messed with the MBR.

I could boot with the boot-repair disk, but only in failsafe mode, which seems to only offer the possibility of creating a BootInfo summary (I could not see the "Recommended Repair" button).

So here is the BootInfo summary:


[http://paste.ubuntu.com/6714973](http://paste.ubuntu.com/6714973)

Can anybody help me figure out what's going on (and hopefully how to fix it?).

At this point I'd be happy just to be able to do a backup and reinstall the OS from scratch.

Thanks,

V.

---

### Post by vincent.fortin on 2014-01-08
Update: when I wait long enough boot-repair does load in normal mode (not failsafe). Same result: I only see the "Create a BootInfo summary" button

---

### Post by Impavidus on 2014-01-08
It seems there is no boot loader nor partition table. Maybe data recovery can retrieve something ([https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)). Judging from the many I/O errors, it seems that your hard drive is broken.

---

### Post by Mark Phelps on 2014-01-08
> problems with my Windows OS, which would freeze shortly after starting up.

Not always the case, but very often, an indication of impending hard drive failure.

Since the partition tables are gone, you may not be able to restore them using Linux data recovery apps.

If you want to recover files and folders from the Win7 install, are able to attach the drive to an MS Windows PC, and are willing to spend some money to get the data back, then read on ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from [http://getdata.com](http://getdata.com).
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to their website, you can compare versions and features.

Your data ... your money ... your choice.

---

