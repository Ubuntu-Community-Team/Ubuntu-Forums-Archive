---
title: "Quantal Issues - new install on Lenovo Ideapad U410"
date: 2012-12-12
forum: General Help
---

### Post by AirWreck on 2012-12-12
This will be kind of a nightmare post because its all pretty vague.  I've been using Kubuntu for the past five years.  I regularly update and have dual booted with Windows on five laptops.  In the last six months, I have gone to Kubuntu as my single OS after I discovered VirtualBox for the few things I need a windows machine for.  I haven't posted in many years as I can usually Google my way to some sort of resolution eventually.  But I am stumped on this one.

The Lenovo U410 out of the box is RAID0 w/ 32gb SSD and 1tb HDD.  I did my homework and was able to break the RAID and install Kubuntu.  But it wasn't straight forward.  I couldn't get the 12.1 installer to recognize the drives so I ended up using the alternate installer of 12.04 to get an encrypted lvm with all of Kubuntu residing on the SSD.  That worked and then I upgraded to 12.1 but as soon as I installed the updates, I was booting to a black screen but found I could ctrl+alt+delete to a boot menu and boot from the previous kernel.  I did that for a few days and then another update seemed to have taken care of the issue.

So far, so good except I was having issues with USB recognition in my W7 Guest in VirtualBox.  I installed VB4.2 by adding the repository and installing from a shell.  I installed the 4.2 Guest Additions.  I was able to access shared folders and I can select some (not all) USB's drives from the top drop down but they do not appear as available in Windows (but no errors).

I was working on this issue for the last few days but midway through the most recent round of updates, my internet connection failed yesterday.  I cancelled out and then did them in three blocks.  

Long winded I know but that's the background.  Here are my immediate issues:

-  While trouble shooting my VBox USB issue, I went to octuple check that my user account was added the vbox group.  I found that User Management is no longer listed in System Settings.

-  I then noticed that Synaptics also hasn't been loading on the boot since the update (to defeat the clickpad while typing).  Synaptics is no longer available in the Kbox, even if you search by name.

-  Now the show stopper and reason I am writing, all Muon stuff is gone as well.  Updater, package installer, software - gone.  But I still have many programs available and they work.

This is bizarre but I don't see any panicked threads from anyone else and I'm not sure where to begin on this one.  I got a Samsung Series 9 with an SSD all up and rolling six months ago and it ran smooth until it was liberated from my apartment in the middle of the night (hence the new lvm encryption).

I know enough to be extremely dangerous but not enough to fully understand the implications of kernel management etc., can someone help me out?

Many thanks!

---

### Post by Pjotr123 on 2012-12-13
I advise a clean reinstall. Install your Kubuntu fully on the SSD and use the HDD only for dumb storage. Approach:

Reinstall:
[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

Tweak your SSD right:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

Nothing like a clean slate, for good results.... :)

---

### Post by AirWreck on 2012-12-13
Roger... I think you're right.  I wouldn't touch all these weird issues with a ten foot pole either!  I'll do the reinstall this weekend and hopefully get things back on track.  Thanks for tips on SSD optimization.  I had seen a few of these but nothing as concise as this one.  Thanks!

---

