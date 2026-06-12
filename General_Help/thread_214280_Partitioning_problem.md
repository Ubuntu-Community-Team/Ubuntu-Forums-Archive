---
title: "Partitioning problem"
date: 2006-07-12
forum: General Help
---

### Post by defrex on 2006-07-12
I should start be saying that I'm new to Linux. I've wanted to make the change for quite some time, but never felt that I safely could. Well, after reading about Ubuntu, I decided to give it a shot. A friend gave me a CD that I could boot off of, and after playing with that and liking it, I've decided to do a full install.

Obviously, I want to keep XP just in case. When I begin the installation everything is fine up until it's time for partitioning. I select the drive I want to use. Then I select the 'Use largest continuous free space' option. Seems simple enough. Then:

"failed to partition the selected disk"

After this it does move me on to where I can finish the wizard and install. But after the partition error I doubt it's a good idea. So I 'manually edit the partition table'. The interface there seems is easy enough. I edit the volume of the windows partition, and use the free space to create a new one. But when I click apply:

"Error while resizing/moving /dev/hda2"

I tried using the partition editor rather then the install interface to create it, but alas, it's the exact same thing.

Any help would be fantastic.

---

### Post by defrex on 2006-07-14
Well, I solved my problem; maybe what I did will help others, too.

I tried defraging twice, but it was still no good. Then I tried using [Partition Magic]("http://www.powerquest.com/home_homeoffice/products/system_performance/pm80/index.html"). While this was still no good at making the new partition, it gave me a better error message for the purposes of googling.

What I found was [this](http://forums.winforums.org/showthread.php?t=1705): that I need to run "chkdsk /f" in a windows command prompt. 

Honestly, I have no idea what function this was supposed to serve, but it worked. I loaded up the live CD and installed Ubuntu without any more problems.

---

