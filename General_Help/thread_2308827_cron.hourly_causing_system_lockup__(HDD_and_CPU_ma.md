---
title: "cron.hourly causing system lockup?  (HDD and CPU max)"
date: 2016-01-06
forum: General Help
---

### Post by edsjag on 2016-01-06
Hi All,

This is my first post so I'll try not to ramble. 

I'm having the exact same issue as was outlined here:  
[http://ubuntuforums.org/showthread.php?t=2238059](http://ubuntuforums.org/showthread.php?t=2238059)

This has been happening intermittently over the previous months and I just simply have to power off and reboot.   
Exact same issues:  The HDD goes mental (Samsung  840 SSD) and CPU bounces off max (C2Duo 2.6Ghz dual core).  

I've tried leaving it for up to twenty mins+ but no change,  it just  seems to get more and more involved in whatever it is doing. 
Looking in the task manager during the lock up (which takes about 2 mins to load), nothing shows up that is using more than about 5% CPU which raised an eyebrow as the CPU usage was maxed out in system tray indicator applet.

Nothing meaningful in the syslog log file, nothing in the /crash folder  and no requests for reporting of issues on reboot.  (current kernel and  all updates installed on Xubuntu).
This is always the last entry in the syslog file before the start of the reboot entries:

Jan  6 11:17:01 Edell CRON[3894]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

I have looked in the cron.hourly folder for scripts and there is only the standard placeholder file. 
I have manually run all the scripts in all the cron folders hoping that one of them will trigger the issue, but all run OK individually.

There is a small chance that the Linux version of Spotify is causing the  issue as it has been running each time that this happens, but I have it (Spotify) running on Mint on my PC and a previous install of Lubuntu with no  issues. 

Any ideas where I can look next? 
Thank you in advance!   :smile:

---

### Post by ian-weisser on 2016-01-06
Seems like you can -terribly slowly- access your system while it's in this state.
That's helpful.

Any clues in /var/log/dmesg?

Next time it happens, note the exact time.
Then open a terminal and run the 'top' and 'free' commands to see which processes are using all the CPU and memory.

---

### Post by edsjag on 2016-01-07
> **ian-weisser said:**
> Seems like you can -terribly slowly- access your system while it's in this state.
That's helpful.

Any clues in /var/log/dmesg?

Next time it happens, note the exact time.
Then open a terminal and run the 'top' and 'free' commands to see which processes are using all the CPU and memory.


Hey Ian,

I couldn't see anything obvious, so I'll wait and see if anything shows up the next time it locks.   

Got to love intermittent faults.  :/

I'll post again the next time that it spits the dummy, Hopefully sooner rather than later.

---

