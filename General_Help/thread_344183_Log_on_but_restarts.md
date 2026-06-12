---
title: "Log on but restarts"
date: 2007-01-22
forum: General Help
---

### Post by Rival on 2007-01-22
Hi all,
I did my due diligence and googled around to find an answer.  I saw references to RAID 5 and PHP related issues but neither apply to my situation.

My Ubuntu6.06 laptop was working fine for about 3 months now and today in the morning, when I fired it up, it got to the log in screen just fine.  I enter my log on info and push enter and my machine logs on (showing my desktop with all the info) and then it freezes for about 5 seconds and logs me out.  If I do it 3 or 4 times I get an error "glibc detected" corrupted double linked list.
  
I don't do anything related to double linked lists.  My only programming environment is Matlab (which was working fine).  My last software addition was KOrganizer but it was working fine.    
I tried logging into different sessions (including fail safe) and the only one that works is the failsafe terminal but I have no idea what to do from there.  

I ran ubuntu disk and now running memory tests but I'm not sure what will I do with the information.  

Any help on getting back to my session or just saving data that I haven't backed up would be appreciated.  (I do incremental back ups every 2 weeks so I won't lose much but still a sig. amount of work)

Thank you
Rival

---

### Post by scrooge_74 on 2007-01-22
Do you have enough space in the disk? Is not the same but when you disk is full or at least the partition where /home is you cant login.

---

### Post by Rival on 2007-01-22
I only have 8 of 100GB used.

Rival

---

### Post by scrooge_74 on 2007-01-22
from recovery boot can you type startx and get into the GUI?

If that works then the problem is the user account

Just an idea

---

