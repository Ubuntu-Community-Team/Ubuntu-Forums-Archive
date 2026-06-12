---
title: "Constant Lockups, Random Reboots w/ Fiesty"
date: 2007-11-11
forum: General Help
---

### Post by Mark OTVII on 2007-11-11
Hello - 

I've been trying to find a fix for this problem, have searched around and seen similar problems but nothing quite like I'm experiencing.

After installing Fiesty about two months ago, things were going great. I had been using Gentoo but quickly came to prefer Ubuntu. Now, I'm ready to smash my computer to pieces with a baseball bat.

At random intervals, ranging from two minutes to two hours (or days), X will crash and I'll be left at the GDM login screen. Sometimes it will freeze and I'll be able to "properly" halt the system from another terminal or ssh. Other times it will freeze and I will need to literally pull the plug to get it to reboot.


And just now, as I was looking at the xorg.conf for anything amiss, the same damn happened. I have absolutely no idea why this keeps happening, other than possibly an old power supply. That was the only help I've found from searching around, reading posts, etc.

Ubuntu was great while it lasted but this is intolerable. Having to reboot ~30 times daily is getting old, and I've all but stopped using my ubuntu desktop since I've lost so much work.

Has anyone experienced this? Any recommendations? I am preparing to spend the day moving /home to another drive and possibly reinstalling the os, but would appreciate some feedback before I get too involved.

Several peripheral devices and a monitor have already suffered from the baseball bat I keep at my workstation. I'd like to keep this comp running a bit longer but don't know if I'll be able to resist.
:x

---

### Post by Sef on 2007-11-11
Run a mem86 test.  When you first boot up, go into GRUB (push esc key), and it is on the bottom.  Let it run overnight and see if there is a problem.  I have the same problem of freezing, and it freezes doing the test.   After checking the ram in each slot by itself, I have discovered that the problem lies with my memory module unit in my motherboard.

---

### Post by jeffjohn on 2007-11-11
I resolved similar, though rarer events.  Finally cured by swapping out all my memory.  1024 GB of new RAM from Crucial and it has been stable for two weeks now!  The memory tests had not revealed  any problems, but like you it was "solve it or sling it!"

---

### Post by Mark OTVII on 2007-11-11
> **Sef said:**
> Run a mem86 test.  When you first boot up, go into GRUB (push esc key), and it is on the bottom.  Let it run overnight and see if there is a problem.  I have the same problem of freezing, and it freezes doing the test.   After checking the ram in each slot by itself, I have discovered that the problem lies with my memory module unit in my motherboard.


Thanks Sef. 

I'm running memory test right now and figure it will be running all day. Now, if it freezes during the course of the test, I'm assuming I should be on the way to the store for a new stick of ram? Or could there be a more serious problem..

I've read about firefox causing problems with Ubuntu. After I installed feisty it worked fine, now it crashes in under a minute.

Argh.
:confused:

---

### Post by Mark OTVII on 2007-11-11
> **jeffjohn said:**
> I resolved similar, though rarer events.  Finally cured by swapping out all my memory.  1024 GB of new RAM from Crucial and it has been stable for two weeks now!  The memory tests had not revealed  any problems, but like you it was "solve it or sling it!"


Well, memory tests indicated a problem after 9 hours or so; new 1GB stick in the mail soon...

Thanks for the help - I hope this'll do the trick.

---

