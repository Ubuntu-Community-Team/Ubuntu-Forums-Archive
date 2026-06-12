---
title: "Monitoring File growth"
date: 2008-05-07
forum: General Help
---

### Post by seeker1458 on 2008-05-07
Im the Network Admin for a company running several win 2k3 servers.  We use alot of proprietary software, thus the vendors build the servers to work best with their needs.  They set it up to have a 12 GB system partition and the rest is for storage.  Problem is something is growing pretty rapidly, to the point windows is bombing out.  If I didn't know better I would think it was a worm, but we have a pretty secure environment. Any one know of a way to monitor a file system to see which files are growing at a faster rate?

---

### Post by bingoUV on 2008-05-07
yes. [http://support.microsoft.com/](http://support.microsoft.com/)

---

### Post by seeker1458 on 2008-05-07
> **bingoUV said:**
> yes. [http://support.microsoft.com/](http://support.microsoft.com/)

Ok, I dunno if that was supposed to be a joke, or if you're suggesting that I troll around MSKB, and hope to find something helpful. I havn't been able to find anything concerning monitoring the growth files in a system.  Only material referencing the monitoring of how much cpu usage is being taken up by a particular file.

---

### Post by bingoUV on 2008-05-07
> **seeker1458 said:**
> Ok, I dunno if that was supposed to be a joke, or if you're suggesting that I troll around MSKB, and hope to find something helpful. I havn't been able to find anything concerning monitoring the growth files in a system.  Only material referencing the monitoring of how much cpu usage is being taken up by a particular file.

Maybe [http://forums.microsoft.com](http://forums.microsoft.com) ?  
Please, it will set a very bad precedent if someone actually gives you a good advice here. Imagine all the MS support this forum will start to proffer. Please take your question anywhere else on the whole wide internet. My humble request to you.

---

### Post by Monicker on 2008-05-07
> **seeker1458 said:**
> Ok, I dunno if that was supposed to be a joke, or if you're suggesting that I troll around MSKB, and hope to find something helpful. I havn't been able to find anything concerning monitoring the growth files in a system.  Only material referencing the monitoring of how much cpu usage is being taken up by a particular file.

I think his point was that you are asking about what appears to be a strictly Windows issue in a forum for Ubuntu linux support.

---

### Post by seeker1458 on 2008-05-07
> **bingoUV said:**
> Maybe [http://forums.microsoft.com](http://forums.microsoft.com) ?  
Please, it will set a very bad precedent if someone actually gives you a good advice here. Imagine all the MS support this forum will start to proffer. Please take your question anywhere else on the whole wide internet. My humble request to you.

Ok I see your point on that, but I have been able to apply knowledge learned in Linux, to similar problems in the MS world.  I am not really concerned with the WINDOWS ONLY solution.  If you know of a way to monitor your etc2/3 file system for rapidly growing files tell me how to do it in linux.  I'll worry about figuring out how to accomplish the same in windows.

:edit: not trying to come off as a jerk, I just didn't get your implication earlier.

---

### Post by Monicker on 2008-05-07
> **seeker1458 said:**
> Ok I see your point on that, but I have been able to apply knowledge learned in Linux, to similar problems in the MS world.  I am not really concerned with the WINDOWS ONLY solution.  If you know of a way to monitor your etc2/3 file system for rapidly growing files tell me how to do it in linux.  I'll worry about figuring out how to accomplish the same in windows.

:edit: not trying to come off as a jerk, I just didn't get your implication earlier.

Well, if it were MY linux server, I would start with the following command, run every hour via a cron job.
```

du -ch --max-depth=1 /
```


And use that to pinpoint exactly which top level directory is increasing rapidly in size, then modify the above command to narrow it down from there.

---

