---
title: "I created ISO CD, but can't install!"
date: 2007-07-09
forum: General Help
---

### Post by rameystarman on 2007-07-09
Good Morning,
   I downloaded Ubuntu, created an ISO image CD following your instructions on the "BurningIsoHowTo" page, but when I try to boot and install on a clean hard drive, all I get is an Error 17 message.  What can I do?
Thanks for your help.  I had done it before with no problems, I don't know what am I doing wrong now.

---

### Post by bigken on 2007-07-09
what speed did you burn the disc ? burn a new cd as slow as possible

---

### Post by jeff0149 on 2007-07-09
I had to install Ubuntu a second time, the reason was that I don't know about partitions.  When I installed it the first time, there was a large section of the hard drive that was not used, but was showing used by the Partition Manager (36.63GB were showing used only by a bad partition).  Because the system thought the disk space was being used, I couldn't install anything, even a picture.  Again, I'm no expert, but check your partitions and see what you get.  When you install a second time, watch the partition process closely.

Best wishes in free computing
Jeff

---

### Post by bigken on 2007-07-09
a good partition in m y opinion is 

/ 10gig (root)

2xram ie 512=1gig Swap

the rest /home

---

### Post by rameystarman on 2007-07-09
I found out what the problem was:  I tried  burning at the lowest speed, but also, the InfraRecorder is setup by default as "Session-At-Once" as write method.  I switched to "Track-At-Once" and it burned perfectly.

Thanks,

rameystarman  :D

---

