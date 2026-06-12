---
title: "Ubuntu 16.04 very slow and not responding"
date: 2019-09-18
forum: General Help
---

### Post by youssefnader on 2019-09-18
I was working on ubuntu without any issues until i downloaded git, the computer became so laggy and very slow, not responding to anything even if i opened the files there is a pop up window says that it is not responding, i tried to remove git and reinstall it but it reaches the step progress 0%... and nothing happen after that, it is so frustrating and everything takes forever to open

---

### Post by TheFu on 2019-09-18
I doubt there is any relationship with git and system issues/slowness.  It is only active when actually running and it doesn't modify system-wide anything.

So ... assuming this is just a coincidence, normal troubleshooting steps are needed.
Step 1 - check the log files.  They are in /var/log/.  
```
egrep -i 'error|warn' /var/log/*g
```
will look for errors and warnings in all the files there.  If there are any, start from the first one and research what might cause it. HW issues should show up here.

Step 2 - Check which processes are running and which processes are using all the CPU and RAM.  I'd use **top** or **htop** for that.  Often, a web browser will be sucking all the CPU and RAM.  A slow system often happens when real RAM is gone and swap is being used.  This is a good thing. It lets users know that RAM is nearly exhausted so the user can back off the RAM requirements.  Some other commands:
```
free -hm
swapon -s
```
A desktop should have 4.1G of swap, never less.  More isn't really a great idea unless you hibernate the system and have more RAM.  For any desktop that doesn't hibernate, I think 4.1G is the only size for swap. More isn't necessary and less can leave today's huge browsers starving for virtual memory.  

I'm almost positive it is one of those too issues.

---

