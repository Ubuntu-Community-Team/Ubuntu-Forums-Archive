---
title: "Synology Hybrid RAID recovery"
date: 2015-01-29
forum: General Help
---

### Post by blackknight2 on 2015-01-29
I'm a total Linux/Ubuntu noob - please be gentle.

I'm desperately trying to recover family photos and videos from a set of 4 drives that were in a Synology NAS (Hybrid RAID).
The Volume was inadvertently deleted just before the drives were pulled and the Synology unit is now gone.

Searching the web, I learned the Synology unit runs a modified version of Ubuntu Linux.
An empty 4-bay machine is available, so I downloaded and burned a DVD of Ubuntu, loaded the 4 drives (in the same bay 
numbers as they were in the Synology unit), and booted the DVD.  

Armed with a number of helpful looking articles and stumbling around in Ubuntu, I attempted installing mdadm, which 
failed initially, but seemd to succeed after appending '--fix-missing' to the command.  In hindsight, I think a USB 
is a better choice as it permits writes, which I suspect generated at least some of the errors during mdadm installation.

I didn't get far with mdadm.  Running cat /proc/mds returned two cryptic (to me) lines:
Personalities :
unused devices: <none>

This didn't look promising.  One of the articles talked about gparted, which I was able to run.  The gparted screen 
tantalized me with data that included what appeared, to me, about my former RAID partition.  (I hope this works) gparted details:
[http://s1313.photobucket.com/user/ImportantStuff_1/library/Drive%20info](http://s1313.photobucket.com/user/ImportantStuff_1/library/Drive%20info)

So, can this data be recovered?  
My ideal scenario would be to copy the files from the RAID array to an external USB drive.
Is this possible?  Any help/direction would be greatly appreciated.

TIA

---

