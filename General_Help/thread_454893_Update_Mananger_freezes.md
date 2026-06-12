---
title: "Update Mananger freezes"
date: 2007-05-26
forum: General Help
---

### Post by varchar255 on 2007-05-26
Hi all,

I installed Wubi using Wubi-7.04-test1.exe on a Dell Inspiron 6000. It is running well except for hibernation/suspend problems (see [http://ubuntuforums.org/showthread.php?t=436910](http://ubuntuforums.org/showthread.php?t=436910) and [http://ubuntuforums.org/showthread.php?t=453569](http://ubuntuforums.org/showthread.php?t=453569)) and issues with update-manager. Every so often update-manager will stop working. The window freezes and will not respond to input. The rest of the machine still works, it's just that updater window that stops. When running the automatic Ubuntu updater, it will freeze right after I click "Install Updates" and before the password prompt comes up. It also freezes sometimes when I run Add/Remove Applications, with similar symptoms. This doesn't happen every time so it's quite frustrating.

I'm not sure this is a Wubi problem, but I thought I'd post here to see if anyone is having similar issues.

*edit*: I manually killed the process, then ran update-manager from the terminal and it worked the second time. The first time, I had launched it by clicking the orange update-notifier icon.

---

### Post by varchar255 on 2007-05-26
Not sure if this is part of the same issue, but even if update-manager doesn't freeze right away and downloads the packages successfully, occasionally it will get stuck on the "installing" stage and at that point, my whole machine freezes and I have to hard reset. Again, this doesn't happen every time and I don't know why.

---

### Post by cdinoz on 2007-05-30
I too have been having issues with the update manager.

Intermittently when the Update Manager notifier pops up - the pc freezes and I have to do a hard reset.

Similarly when using the update manager - when beginning a d/l it sometimes freezes and have no option but to hard reset the pc

---

### Post by ago on 2007-05-31
Try not to hard reset consider [www.developertutorials.com/tutorials/linux/magic-sysrq-050503/page1.html](www.developertutorials.com/tutorials/linux/magic-sysrq-050503/page1.html) 
How much free space do you have on the virtual disk? You can run "df" in a terminal

---

### Post by varchar255 on 2007-06-09
On / I have 1424580 1-K blocks remaining. It's 63% in use. Everything else is 15% or lower, so it doesn't seem like a disk space problem.

Today I ran Update Manager and for the first time, it completed successfully (although at times, my whole machine seemed to freeze and lag but then resumed after a few moments). I think the last update I did was updating the kernel to 2.6.20-16, maybe that fixed something.

---

### Post by Compactman on 2007-06-22
I to am having this very same problem but only on one machine. 

It doesn't freeze so much as the hard drive is constantly in use and lagging everything else.  I have had other problems with this intel chipset already and I'm concerned that the IDE controller isn't being setup properly during installation.

It's a dell machine,  The chipset is 82845G Brookdale-G

---

### Post by ago on 2007-06-22
Isn't that a graphic controller?

---

### Post by K3l3v on 2008-01-05
I'm having a similar problem.  Running 7.10, clean install...

Any time I try to install a program or update my system, it hangs.  No mouse, no alt + tab, no nothing.  Takes a hard reboot to bring the system back.  Has anyone found a fix for this?

---

### Post by ago on 2008-01-07
If you are out of (virtual) disk space that is normal, you will have to free up some space first.

sudo apt-get clean 

is a first step to free up disk space. If you are not out of disk space then it is a bug.

As mentioned use the command "df" to monitor disk space

---

### Post by K3l3v on 2008-01-07
Thanks for the quick reply!

'df' says I have 168592816 available, so...  I'm guessing a bug...

I'll keep trolling the fora and see if anyone's got a similar problem/fix.

---

