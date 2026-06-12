---
title: "var logs"
date: 2013-08-03
forum: General Help
---

### Post by john_burns2 on 2013-08-03
I read on here about var/ logs , taking up valuable space on someone's HDD. By going through the file system I can see that var/logs is taking up 6.5Mb of space. When I open the log folder up , I see there are sub folders, like apt, cups, dist-upgrade, console kit, fsck,  as well as files like alternatives.log1.gz, alternatives.log2.gz, apport.log1. apport.log2.gz. etc, etc (there are many)
Can someone tell me if it's safe to delete these files and folders, and how to delete these files/folders (assuming it's safe to do so) ?? 
Quite a noobie here so please don't get me opening the dreaded terminal (frightens me silly) ;);)

Cheers

---

### Post by Irihapeti on 2013-08-03
As a rule, logs shouldn't take up an excessive amount of space on a disk. By default, the system automatically deletes logs of a certain age. 

The only times I've seen this not happen is when someone has done a custom install and forgotten to install anacron. (Guilty of this myself :oops:)

Another possible cause of excessive /var/log size is a repeating error message that fills the logs up rapidly. That is also unusual on a default install and often (not always) goes with installing drivers or server software.

6.5MB is nothing unusual. For comparison, the /var/log directory on my EeePC 900 is just under 20MB. It's been a long time since I deleted anything manually.

I'd suggest leaving the logs for now. They can come in handy if something does go wrong. If they keep on madly growing, then it's probably more useful to find out what's causing that and fix the problem.

---

