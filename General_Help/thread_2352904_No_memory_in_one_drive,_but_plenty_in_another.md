---
title: "No memory in one drive, but plenty in another?"
date: 2017-02-16
forum: General Help
---

### Post by jimcricket on 2017-02-16
Hello, I have an originally Windows PC and I have recently changed to Ubuntu due to unforeseen incidents and I am having some problems with memory. Upon installation, I have 4.2 GB in my Ubuntu "/" folder in the Disk Usage Analyser and I need probably at least 8GB's more. The thing is, I have PLENTY of GB's in another drive called 311 GB Volume (It says it has 3.9GB out of 306.5). The directory of it is /media/ubuntu/7abc7241-f6c8-4e3c-bc19-511989ca98f0 . If anyone could help me either get more space on my "/" folder or how to switch to my other drive with plenty of space. I realy want to play Counter-Strike: Global Offensive which requires at least 15 GB of available space. Thank you very much. If anyone needs any more information to help me solve my problem I am willing to provide it.

P.S. I had plenty of space on the Windows part with multiple steam games and many other applications.

---

### Post by TheFu on 2017-02-16
Well, you need to move the /media/ubuntu/7abc7241-f6c8-4e3c-bc19-511989ca98f0 mount to somewhere useful, then move files from the / partition over.  /home/ would be a normal thing to move, but as long as you follow the **file system hierarchy standards** requirements and don't move anything that must be on the boot disk, it shouldn't matter. 

First you need to decide what/which directories you want to move over. Then you need to mount the /media.... partition to that area, then move the files.

If you'd like help deciding on what to move, we need some facts.  The easiest way to provide those would be to install a tool called 'boot-repair' and run the gather info step, then post the URL that gets created from it.  This will let us know about your system, the disks, the partitions, file systems and sizes for everything.  Without that data, it is just too hard.

---

