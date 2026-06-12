---
title: "&quot;Disk Cleanup&quot; of Ubuntu?"
date: 2007-07-28
forum: General Help
---

### Post by taekwondodogoof on 2007-07-28
Hi,
        I do a lot of multimedia editing, and I'm starting to run out of space. In a last struggle to squeeze the most of my miserly 80 gb harddrive, I'm trying to get some more hard space by removing older files and such. I keep all of my files in one place, amounting to around 62gb of stuff. The hard-drive, in actual OS terms, should be around 74gb according to my calculations due to the difference between manufacturer size and OS size of hard drives. So, I'm "missing" around 10gb of space, and I've looked through add/remove programs, and haven't found any real space hoggers. Does anybody have any ideas on how to get some of the 10gb back? Thanks! :)

---

### Post by forestpixie on 2007-07-28
sudo apt-get clean

will clear the downloaded cached files

---

### Post by bodhi.zazen on 2007-07-28
> **taekwondodogoof said:**
> Hi,
        I do a lot of multimedia editing, and I'm starting to run out of space. In a last struggle to squeeze the most of my miserly 80 gb harddrive, I'm trying to get some more hard space by removing older files and such. I keep all of my files in one place, amounting to around 62gb of stuff. The hard-drive, in actual OS terms, should be around 74gb according to my calculations due to the difference between manufacturer size and OS size of hard drives. So, I'm "missing" around 10gb of space, and I've looked through add/remove programs, and haven't found any real space hoggers. Does anybody have any ideas on how to get some of the 10gb back? Thanks! :)

It is unlikely applications are taking up 10 Gb of missing space. Search your home folder, including hidden directories and backups.

Also check your trash ~ when you delete stuff it goes to trash first ... 

EDIT: well from the gui at least ... don't try this on the command line

HTH

---

### Post by ThrobbingBrain66 on 2007-07-28
One time I had over 800MB of stuff in the .Trash folder in the /root directory.  Took me a long time to find it.  It was just never a place I thought to look.

---

### Post by taekwondodogoof on 2007-07-29
Thanks for the help! I've cleared about a gig with that advice, but I have an odd problem. The disk usage analyzer says I have 8.3gb free on my hard disk, but my folders (at the bottom) say I have 4.7 gb free space. I've made sure to only include my ext3 in the filesystem scan. Does anybody know an explanation for this discrepancy?

---

### Post by rillip on 2007-07-29
I can't address the discrepenacy between what you see in the analyzer and the folder list, but part of your "missing" disk space may be due to the ext3 file system.  Ext3 reserves 5%, I believe, for the root user.  This way, if you get the disk full, you can still work in recovery mode. This is usually a little... conservative for most people.  Check out this page for more details:

[http://boncey.org/2006_11_18_reclaiming_ext3_disk_space]("http://boncey.org/2006_11_18_reclaiming_ext3_disk_space")

You can reduce this ammount so that you have more available disk space.  I set mine to 1%, as on an 80 gig hard drive, 1% is .8 gigs, i,e, 800 megabytes.  I don't think I'm ever going to need that much just to clean up disk space in the case of getting fully being a problem.

---

### Post by ThrobbingBrain66 on 2007-08-01
> **rillip said:**
> I can't address the discrepenacy between what you see in the analyzer and the folder list, but part of your "missing" disk space may be due to the ext3 file system.  Ext3 reserves 5%, I believe, for the root user.  This way, if you get the disk full, you can still work in recovery mode. This is usually a little... conservative for most people.  Check out this page for more details:

[http://boncey.org/2006_11_18_reclaiming_ext3_disk_space]("http://boncey.org/2006_11_18_reclaiming_ext3_disk_space")

You can reduce this ammount so that you have more available disk space.  I set mine to 1%, as on an 80 gig hard drive, 1% is .8 gigs, i,e, 800 megabytes.  I don't think I'm ever going to need that much just to clean up disk space in the case of getting fully being a problem.

I remember wondering about that when I first started on Ubuntu but eventually forgot about it,  Thanks for the linkage.

---

### Post by Sayers on 2007-08-02
Applications -> Accessories -> Disk Usage Analyzer

This is a wonderful tool that makes a great pie chart that is simply amazing!

---

### Post by Blofeld on 2007-08-07
> **ThrobbingBrain66 said:**
> One time I had over 800MB of stuff in the .Trash folder in the /root directory.  Took me a long time to find it.  It was just never a place I thought to look.

It's just too obvious!
But boy did it do wonders for me ... ;-)
Thanks, Throbby.

---

### Post by Seisen on 2007-08-07
This might help you guys to.

[http://ubuntuforums.org/showthread.php?t=140920]("http://ubuntuforums.org/showthread.php?t=140920")

---

