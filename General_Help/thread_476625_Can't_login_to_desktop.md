---
title: "Can't login to desktop"
date: 2007-06-17
forum: General Help
---

### Post by saigalp on 2007-06-17
I installed Ubuntu 7.04 today. After installation it downloaded updates. After that I shut down my PC. On restarting I am stuck at the login screen because after giving user name and password I get a message" that GDM could not open the home directory and save changes. Contact your system administrator". and I am again directed to the login screen. I can start in safe mode from the GRUB menu. But I am a newbie and don't know what to do to solve this problem. Also after the updates download Firefox did not start. Please help.

---

### Post by DeeWox on 2007-06-17
Have you been editing some user permissions?

---

### Post by H.E. Pennypacker on 2007-06-17
1.  What have you been doing recently that could explain this problem?

2.  Please provide us with the EXACT wording of the error, word by word, spelling exactly as you see things on the screen.  I repeat that we need the exact error you are getting, not what the error looked like, or your phrasing of the error.  This is important to remember.

3.  What do you mean by Firefox not starting?  Is it installed (use Synaptic to verify this)?  If it is installed, start a terminal (Applications > Accessories), and type firefox to start Firefox (no quotes, just type firefox).  If it won't start, the terminal will give you errors related to Firefox.  Reproduce them exactly as you see them here.  Again, reproduce them on this forum exactly as you see them.

Please do not cut corners, and provide the information I have asked for.

---

### Post by saigalp on 2007-06-17
> **H.E. Pennypacker said:**
> 1.  What have you been doing recently that could explain this problem?

2.  Please provide us with the EXACT wording of the error, word by word, spelling exactly as you see things on the screen.  I repeat that we need the exact error you are getting, not what the error looked like, or your phrasing of the error.  This is important to remember.

3.  What do you mean by Firefox not starting?  Is it installed (use Synaptic to verify this)?  If it is installed, start a terminal (Applications > Accessories), and type firefox to start Firefox (no quotes, just type firefox).  If it won't start, the terminal will give you errors related to Firefox.  Reproduce them exactly as you see them here.  Again, reproduce them on this forum exactly as you see them.

Please do not cut corners, and provide the information I have asked for.
This problem occurred after I downloaded upgrades. there were 29 files which included updates to Firefox and Kernel upgrades as well. After upgrading Firefox also did not start. Then I had to shut down PC to attend some other work. On restart I got this problem. i feel there was some error in updates that were downloaded and installed.

The exact message I get is "**GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case it is not possible to log in. Please contact your system administrator."**

From the GRUB menu option I can login as root. I checked and found the /home/pramod/ directory and issued -chmod pramod /home/pramod/, but to no avail. Since I am a newbie I do not know all commands and am stuck here.

---

### Post by DeeWox on 2007-06-17
I had a similiar problem.I don't think it will help you, but anyways:
[http://ubuntuforums.org/showthread.php?t=476331](http://ubuntuforums.org/showthread.php?t=476331)

---

### Post by jdmcg on 2007-06-17
I think if you try to load up 20-15 kernel I believe it is from your grub menu, you may be able to log in. Wroked for me. Seems there might be a problem with the 20-16 kernel.

---

### Post by H.E. Pennypacker on 2007-06-18
saigalp, your problem may be caused by low hard drive space as another person with this same error had.  It is possible that your root partition has become full, especially after the kernel upgrade, which may account for a large chunk of the root partition.  Are you sure you have not recently been getting messages about low disk space?

If you run GParted (System > Administration), it will tell you how much space you have left.  You can also use the command df -h.  It will also tell you the same thing.

If it is a space issue, try sudo apt-get clean.  This will remove some files.  If you no longer need the old kernel, uninstall it.  

Here's the original thread:

[http://ubuntuforums.org/showthread.php?t=471356&](http://ubuntuforums.org/showthread.php?t=471356&)

Another guy had the exact same problem, with the same cause:

[http://ubuntuforums.org/showthread.php?t=465759&](http://ubuntuforums.org/showthread.php?t=465759&)

There is yet another person with same problem, and the same cause:

[http://ubuntuforums.org/showthread.php?t=450342&](http://ubuntuforums.org/showthread.php?t=450342&)

Like I said, get rid of what is not important.  Purge the old kernel, if you must.  If you can't afford the disk space, don't install new things, and keep control of your hard drive.

---

### Post by saigalp on 2007-06-18
> **H.E. Pennypacker said:**
> saigalp, your problem may be caused by low hard drive space as another person with this same error had.  It is possible that your root partition has become full, especially after the kernel upgrade, which may account for a large chunk of the root partition.  Are you sure you have not recently been getting messages about low disk space?

If you run GParted (System > Administration), it will tell you how much space you have left.  You can also use the command df -h.  It will also tell you the same thing.

If it is a space issue, try sudo apt-get clean.  This will remove some files.  If you no longer need the old kernel, uninstall it.  

Here's the original thread:

[http://ubuntuforums.org/showthread.php?t=471356&](http://ubuntuforums.org/showthread.php?t=471356&)

Another guy had the exact same problem, with the same cause:

[http://ubuntuforums.org/showthread.php?t=465759&](http://ubuntuforums.org/showthread.php?t=465759&)

There is yet another person with same problem, and the same cause:

[http://ubuntuforums.org/showthread.php?t=450342&](http://ubuntuforums.org/showthread.php?t=450342&)

Like I said, get rid of what is not important.  Purge the old kernel, if you must.  If you can't afford the disk space, don't install new things, and keep control of your hard drive.

The problem is not because of lack of space. I checked and I have 16 GB for Ubuntu. The problem appears to be broken packages after ubuntu downloaded updates. This is the list of broken packages:
1. Linux headers 2.6.20.16 generic
2. Linux-image-generic
3. Linux-restricted Modules.
These packages were downloaded and not installed/configured because of dependancy errors. Please advice how to fix this problem.
Further I can log in as root from failsafe option and tried editing users and groups. but was denied permission.

---

### Post by H.E. Pennypacker on 2007-06-19
Please post the output of df -h.  I **_still_** want to see how full your partitions are.

To uninstall those broken packages, use sudo aptitude purge thenamegoeshere or sudo apt-get remove packagenamegoeshere.  

Since you have installed a new kernel, have you tried going into the old kernel?  When starting up, press ESC repeatedly until you get to the GRUB menu.  There, select the older kernel that you are used to using (before all these problems).

---

### Post by saigalp on 2007-06-19
> **H.E. Pennypacker said:**
> Please post the output of df -h.  I **_still_** want to see how full your partitions are.

To uninstall those broken packages, use sudo aptitude purge thenamegoeshere or sudo apt-get remove packagenamegoeshere.  

Since you have installed a new kernel, have you tried going into the old kernel?  When starting up, press ESC repeatedly until you get to the GRUB menu.  There, select the older kernel that you are used to using (before all these problems).

Perhaps you are right about disk space, as earlier I checked the partition table from Win XP. But from within ubuntu it shows root as 2 GB and it is full. I think I made some mistake at the time of installation. Is there any way I can increase the disk space to 18 GB with GParted, without affecting the system, if so pleaser point to some detailed steps available on  some  site. Since right now I am in office and my PC is at home I will post the output of my df-h command later. If it is not possible to increase the disk size then only other option left with me is to re-install. Please advise.

---

### Post by Qu4k3R on 2007-06-19
I think a nice Computer has about 5G of ubuntu.

---

### Post by H.E. Pennypacker on 2007-06-19
> **saigalp said:**
> Perhaps you are right about disk space, as earlier I checked the partition table from Win XP. But from within ubuntu it shows root as 2 GB and it is full. I think I made some mistake at the time of installation. Is there any way I can increase the disk space to 18 GB with GParted, without affecting the system, if so pleaser point to some detailed steps available on  some  site. Since right now I am in office and my PC is at home I will post the output of my df-h command later. If it is not possible to increase the disk size then only other option left with me is to re-install. Please advise.

At this point, it would be a better idea for you to clear up some space first so that you can at least log into Ubuntu.  Please follow my earlier post in this thread on how to create more space, and uninstalling stuff you do not need.

Once you've done this, you should be able to enter Ubuntu.  We can then start to worry about increasing the partition.  To resize the partition, use GParted.  Decrease the size of another partition, and increase the root partition.  I believe there is a rule about how these partitions should be placed on the partition table, but I cannot be entirely sure.  I am guessing that the partition you are decreasing in size should be infront or should come after the root partition, which will be increased later on.

In any case, let's first start off by doing the first thing I asked you to do: log-in to Ubuntu.  If you no longer have this error (the one you created this thread for), and another problem occurs, please create a new thread, or do a forum search to make sure any new problems have not already been covered.  Do not use this thread for any subsequent and unrelated problems.

---

