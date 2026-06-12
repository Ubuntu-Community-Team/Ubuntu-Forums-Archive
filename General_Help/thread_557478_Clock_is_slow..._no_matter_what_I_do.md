---
title: "Clock is slow... no matter what I do"
date: 2007-09-22
forum: General Help
---

### Post by messybricks on 2007-09-22
There have been several posts about clocks in Ubuntu running slow, but none of them have helped me. 

Right now, my clock runs slightly slow (about 5 minutes per day)... it isn't annoying until you end up 15 minutes for class...

Anyway, I've tried manually setting it, synchronizing it with an internet server, synchronizing it with all 60 available internet servers, and I've even switched out the CMOS battery (against my better judgment 'cause the clock worked fine in windows)

Anyone have any other ideas?  Is there a way to force it to synchronize with internet servers more often (like once an hour or so)?

---

### Post by 505 on 2007-09-22
> **messybricks said:**
> Anyone have any other ideas?  Is there a way to force it to synchronize with internet servers more often (like once an hour or so)?
If the file to synchronise the time daily is in /etc/cron.daily, move that file to /etc/cron.hourly

---

### Post by linuxchris on 2007-09-23
I have exactly the same problem in Feisty. I can manually set the software clock via Gnome, but the hardware clock is slow and stays that way no matter what I've tried: adding additional servers via gnome gui, installing full ntp,  adding servers to /etc/ntp.conf, manually running  ntp -u at the prompt, etc. etc.

---

### Post by messybricks on 2007-09-23
I copied all the files from cron.daily to cron.hourly, and it hasn't done anything different.  Is there something else I have to do to get it to run the things in cron.hourly?

---

### Post by leona on 2007-10-30
Same issue here, will not update to GMT from BST, even with "keep sync" turned on, what gives?

---

### Post by swj on 2007-10-30
Although ubuntu is the primary distro I currently use, I have noticed that several gnome based distros have time issue(s).   Perhaps, its gnome related.

---

### Post by Thelasko on 2007-11-11
I've had constant clock problems with Ubuntu.  Sometimes they go away with a fresh install.  The first clock issue I had went away when I switched to 64 bit.  However, Gusty 64-bit still seems to have a slow clock.

From my understanding the hardware clock on the CMOS is only used at boot up to sync the clock with the newly started system.  From then on the CPU is used to keep track of the time.  There must be something wrong with the way Ubuntu interfaces with the CPU that makes the clock inaccurate.  My guess is that it's in the kernel.  When I reboot my system the clock is correct and then drifts over time.  I'm no expert on the matter I'm just sharing my experiences and opinion.

---

### Post by aeg1s on 2007-11-11
Thelasko, 

Have you tried installing and configuring the  NTP package?  Afterwards, you can set your time and date preferences to update from the NTP servers automatically.  I had the opposite problem you're experiencing because I was overclocking.  That fixed my problem.

Hope it helps!

---

