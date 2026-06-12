---
title: "Can't Boot All of a Sudden"
date: 2007-05-14
forum: General Help
---

### Post by 64mgb on 2007-05-14
This happened a couple of weeks ago after some updates, but I don't remember what the updates were, and I've been trying various things to get it to work again, with no luck.

My system will act like it's starting...it'll get to the progress indicator which goes about a third of the way across, then the graphical screen goes away and a terminal displays.  First it says it's "Activating swap" and says it's ok.  Then it says "Checking root file system" and says "Superblock last write time is in the future.  FIXED" and then "ok".  Finally it says it's

Checking file systems
/dev/sda3  Recovering journal
XFS file system    ok

Then it just hangs there.

Any ideas what I can do?  I can wipe everything out and start over, but would rather not if I can get by this.

Thanks,
Rich

---

### Post by jsmidt on 2007-05-14
I do not not how to fix those errors.  I will say if you put in a live cd you can access your files by mounting them.  Then you can alter needed files or copy files you don't want to loose.  However hopefully somebody can help you with your specific problem.

---

### Post by 64mgb on 2007-05-14
> **jsmidt said:**
> I do not not how to fix those errors.  I will say if you put in a live cd you can access your files by mounting them.  Then you can alter needed files or copy files you don't want to loose.  However hopefully somebody can help you with your specific problem.
Yea, I managed to figure out how to get the files I wanted off the drive and onto another computer on my network.  This is my MythTV box so I wanted to save my recordings.  Other than that there's no reason I can't just start over, but I'm trying to learn as much as I can, so I'd like to get this fixed.

Thanks,
Rich

---

### Post by phidia on 2007-05-14
> **64mgb said:**
> This happened a couple of weeks ago after some updates, but I don't remember what the updates were, and I've been trying various things to get it to work again, with no luck.

My system will act like it's starting...it'll get to the progress indicator which goes about a third of the way across, then the graphical screen goes away and a terminal displays.  First it says it's "Activating swap" and says it's ok.  Then it says "Checking root file system" and says "Superblock last write time is in the future.  FIXED" and then "ok".  Finally it says it's

Checking file systems
/dev/sda3  Recovering journal
XFS file system    ok

Then it just hangs there.

Any ideas what I can do?  I can wipe everything out and start over, but would rather not if I can get by this.


Thanks,
Rich


Have you tried opening a shell from the point where you no longer see any system activity?

i.e Alt+Ctrl+F1 if you get to login you can try startx and copy the error messages.

You can also use the livecd to try and repair the filesystem. I don't use xfs so I don't know how to help you specifically with that filesystem.

---

### Post by pmg on 2007-05-14
How long have you left it at the hang, and have you checked for any disk activity... and do you have any other fliesystems that need to mount?  If one filesystem needs recovery and you have others, they may need recovery too, and in some cases that may take awhile.

---

### Post by 64mgb on 2007-05-15
> **pmg said:**
> How long have you left it at the hang, and have you checked for any disk activity... and do you have any other fliesystems that need to mount?  If one filesystem needs recovery and you have others, they may need recovery too, and in some cases that may take awhile.
I left it overnight a couple of times.  It sounds like there is disk activity from time to time, but the disk activity light does not flash (it does flash up to this point).  I have other file systems to mount.

To answer a previous response, I'll try to see if I can open a shell and see where that gets me.  I've tried using the live cd but don't see how to use it to repair the filesystem.

Thanks,
Rich

---

### Post by Lal2017 on 2007-10-23
> **64mgb said:**
> ...My system will act like it's starting...Then it says "Checking root file system"...

Then it just hangs there.



I also faced a similar problem with Ubuntu Kernel 2.6.20-16, where after 23 boot-ups it says: checking file system, you see a percentage increase as it scans the drive then totally HANGS halfway through. 

I hard-booted, (i.e. pressed on the on/off button), as ctrl-alt-del or any other key combination just didn't work. Upon reboot it tries to perform the check again however I hit ctrl-alt-F1 and this seemed to bypass that check and worked. 

i am expecting the problem to re-occur after 23 sucessful bootups or perhaps it will be a problem fixed in a next release??? By googling this it seems there are quite a few out there having this problem.  

I am very new to Ubuntu but I think there ought to be some instructions flash up on screen advising users what to do if something hangs duriing boot up.

---

