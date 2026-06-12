---
title: "Buggy System"
date: 2007-05-26
forum: General Help
---

### Post by ADloser on 2007-05-26
Lately my computer has been running VERY slow when I'm using Ubuntu.
I have my system set up with Windows (works fine) on the Master and Ubuntu on Slave.

The last time I tried to boot up it froze and I had to go into the configure screen where I guess I restored a backup that Ubuntu had made. I also ran fsck, and basically hit YES to everything because I had no idea what I was doing.

My question, is there a way to check to see if there is anything wrong with my system. and to "clean" or fix any problems?

 Thanks!

---

### Post by mbradlcu on 2007-05-27
when you say slow do you mean apps starting up,, apps running slow? most of the time I see systems running overall slower or at a dead craw it's dns issues,, maybe not in your case.. anyway after the machine is up run the 'top' command and see if anything is eating the cpu. Another check would be to look at the /var/log/syslog and messages for any problems, disk, etc..

---

