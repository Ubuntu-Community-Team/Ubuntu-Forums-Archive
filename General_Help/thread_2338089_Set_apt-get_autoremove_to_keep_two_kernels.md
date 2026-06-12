---
title: "Set apt-get autoremove to keep two kernels"
date: 2016-09-24
forum: General Help
---

### Post by lou6 on 2016-09-24
I recently ran across a post here [http://askubuntu.com/questions/620266/how-does-apt-decide-how-many-old-kernels-to-keep](http://askubuntu.com/questions/620266/how-does-apt-decide-how-many-old-kernels-to-keep) which states (in the first answer) that it's possible to modify apt-get autoremove to automatically keep the most recent two kernels by entering "sudo apt-mark auto ^linux-image-".

I currently keep the most recent two by manual means and would like to use this approach since it's not a bad idea to run autoremove from time to time anyway.  My question is "will it work as advertised?"

I would simply try it and see but do not know how to reverse the mod if it does not do what I want.

Thanks in advance for any advice...

---

### Post by SeijiSensei on 2016-09-24
Autoremoval of kernels has been rather spotty in Ubuntu.  I posted [this bug report](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1275376) back in early 2014, and the problem was [supposedly fixed]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1429041") about a year later.  Nevertheless I still find I have stale kernels lying about from time to time that I need to remove manually.

Let us know if the "mark" method works for you.

---

### Post by lou6 on 2016-09-24
Well, as I dig into this a bit more it seems that my recent upgrade to 16.04 LTS may have somehow solved the original issue.  Without running the "mark" Ubuntu seems to be doing the right thing - I have two kernels installed and sudo apt-get autoremove shows no kernels to be removed which is the behavior I wanted.

I'll mark this closed for now.

Thanks for your reply.

---

### Post by ian-weisser on 2016-09-24
Yes, the autoremove 'bug' (actually a disagreement between several different projects) was solved in 16.04 when unattended-upgrades volunteered a fix.

---

### Post by SeijiSensei on 2016-09-24
Just now when running an upgrade on 14.04 I was told first that I could use autoremove to delete a stale kernel, 3.13.0-93-generic, since I had -95 and -96 as well.  After I did that, i ran the upgrade again and was told I should run autoremove to delete the -95 kernel! 

I'm glad to hear this has been fixed in 16.04, but I'm not ready to move on yet.  I'm waiting until at least Kubuntu 16.04.3 or so to make sure any bugs from the transition to systemd and KDE5 have been resolved.

---

### Post by ian-weisser on 2016-09-24
> **SeijiSensei said:**
> Just now when running an upgrade on 14.04 I was told first that I could use autoremove to delete a stale kernel, 3.13.0-93-generic, since I had -95 and -96 as well.  After I did that, i ran the upgrade again and was told I should run autoremove to delete the -95 kernel! 

I'm glad to hear this has been fixed in 16.04, but I'm not ready to move on yet.  I'm waiting until at least Kubuntu 16.04.3 or so to make sure any bugs from the transition to systemd and KDE5 have been resolved.

To be TOTALLY clear: There are several reason why kernels accumulate. The most common in 12.04/14.04 was that everything in the system worked properly: Older kernels were properly apt-marked as eligible for autoremoval, but 'apt autoremove' was simply never called by any automatic process (it is in 12.04/14.04 unattended-upgrades, but 'off' by default). The ONLY change in 16.04 is that  an equivalent of 'apt autoremove' is now run by unattended-upgrades, triggered by cron.daily. 16.04 has NO CHANGES to apt's package logic, nor to the kernel-package-marking script.

If you had old kernel accumulating for *any* other reason, those are a separate issue and not fixed in 16.04. If you can provide enough information for a Triager to duplicate, please file a bug report. I have read a lot of 'I still have accumulating kernels' anecdotes, but have been unable to duplicate any on my test systems.

---

### Post by Keith_Helms on 2016-09-24
My Xubuntu 16.04 system currently has 5 kernel versions installed.  What  configuration option(s) do I need to change in order to get it to  retain no more than 2 or 3 versions?

---

### Post by kevdog on 2016-09-25
I use the purge-old-kernels script as described here: [http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/)  It seems to work for me.  Yes I know there are more ways to purge older kernels, however the article referenced is pretty straightforward.

---

### Post by Keith_Helms on 2016-09-25
> **kevdog said:**
> I use the purge-old-kernels script as described here: [http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/)  It seems to work for me.  Yes I know there are more ways to purge older kernels, however the article referenced is pretty straightforward.

I have that script on my system and use it sometimes.  I just got the impression from the previous posts that the cleanup should now be happening automatically with 16.04.

---

