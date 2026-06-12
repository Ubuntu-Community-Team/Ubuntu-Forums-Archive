---
title: "Installation size"
date: 2006-07-25
forum: General Help
---

### Post by ThrobbingBrain66 on 2006-07-25
Out of curiosity, what is the approximate size of a fresh installation of Kubuntu Dapper without any extra software added?  I've read in other threads that its about 3-5 gigs, but mine, even before I added my extra software was around 6 gigs (currently approx. 8 gigs).  I've run deborphan and localepurge plus the autoclean and clean functions of aptitude/apt-get.  Are there any other utilities I can use to see what seems to be taking up so much space, and then get rid of it?

---

### Post by aysiu on 2006-07-25
A default installation is actually close to 2-3 GB.

When you're looking at disk space, are you including your /home directory, too?

---

### Post by ThrobbingBrain66 on 2006-07-25
Yes, I was including my /home partition.  In Kmenu>KinfoCenter>Partitions it shows my /root partition (which includes /home) as Total Size - 91,000MB and Free Space - 83,800MB.  So that's 7.2 gigs...could the extra 4 gigs really all be from my /home?!

EDIT: however, when i check the properties of any folder (/home for example) it states that i have 81.9 out of 88.9 gigs free.  obviously this is still 7gigs...

---

### Post by apella on 2006-07-25
I don't know if there is on this point much difference with ntfs, but if there isn't, this might be the case: Your disk exists of a lot (really a lot) little "bags", that have a certain size (e.g. 32 bits). If a file is bigger then that, it uses multiple bags. The space that is left over in the last bag (say 20 of the 32 bits) is lost, you can't use it anymore. Thus if you have a lot of files (even when they are all very small), it can take up lots of spaces, tough they aren't big at all. 
Dunno if it was understandable, nor if it is of use on the linux file system, but if it is (both points), then this might be the problem that you're looking for.

---

