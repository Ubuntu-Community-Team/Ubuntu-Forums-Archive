---
title: "Making a /Home partition and moving all files across after install"
date: 2022-06-29
forum: General Help
---

### Post by mikber18 on 2022-06-29
Hello, 

I've installed my Ubuntu some few weeks ago, but as I am constantly learning, I've learnt that /Home is a good way of seperating your Core OS away from your apps + files. 

When I installed Ubuntu I did not configure a seperate /Home directory. 

Is there a way of retrospectively creating one and moving all the files across or would I need to start from scratch in order to achieve it - i.e. by installing the OS again from 0%?

Thanks for your help,

---

### Post by guiverc on 2022-06-29
You can change it; you'll find any GNU/Linux system will let you do whatever you want, providing you can work out how to do it (*ie. we're mostly limited by our skillset*/*knowledgeset*).

I'd boot *live* media (*ie. Ubuntu installation media; esp. desktop ISO*) & do it from there; then adjust the installed system's *file-system-table* (ie. `/etc/fstab`) so it knows where the /home data is, then reboot & confirm your work.  But do you need to?

I'm assuming you're talking about Ubuntu Desktop; you can re-install Ubuntu Desktop if something goes wrong, without losing your files, and having your *manually installed* packages (ie. those you added yourself post-install) automatically re-installed IF they were from Ubuntu repositories; and this works if you have a separate home, or just a single partition. It's really just a normal install where you do **not** format the partition(s) which triggers the re-install I'm talking about.

I'm involved with QA (*Quality Assurance*), particularly with a *flavor*, and as part of my *support* function keep a system with each release. On that system I don't perform any package upgrades; instead where *dailies* are produced, I just re-install which (1) performs another QA test, and (2) upgrades my packages; without impacting my installed files; my additional programs (*eg. I don't use the default music player, but if the install worked which is what I'm testing for, that gets re-installed*).  Currently that includes *focal* (*or 20.04 as our next release is 20.04.5*) and *jammy* (*next will be 22.04.1*)and of course *kinetic* (*what will be 22.10 on release*). The systems I do this to are single-partition installs; ie. no separate home partition, and my checking to ensure my *manually installed* apps re-install, my music etc survives is part of my QA..   ie. my point is it's not necessary with Ubuntu to have separate home partition.

The system I'm replying on here does sure; I tend to, if I consider I'll want to move away from Ubuntu or have a specific reason for it  (*eg. **I have no intention of moving away from Ubuntu on this box; this box has an encrypted home partition but not system partition; and I wanted more experience with encrypted  partitions*)

Yes you can, but my point is I don't think it's necessary with Ubuntu Desktop systems.  

FYI:  *I'm not trying to tell you how to do it here, just expressing my thoughts.  Moving system partitions can have consequences & I don't know if you're using a MBR or GPT partition table thus what complication(s) may exist... *

---

### Post by oldfred on 2022-06-29
Step by Step guide. But you must have good backups.


To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) & 
[https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437](https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437)
[https://ubuntuforums.org/showthread.php?t=2343317](https://ubuntuforums.org/showthread.php?t=2343317)

---

