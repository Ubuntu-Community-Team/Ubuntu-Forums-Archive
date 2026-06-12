---
title: "powernap"
date: 2013-12-04
forum: General Help
---

### Post by Garf on 2013-12-04
Hi. I've installed powernap because I want my machine to suspend (using pm-suspend) after say 10 minutes. 

But I just can't seem to get it to work... 

I have edited the config file, and tried the default one (incase I made an error) but I just can't see any evidence of it running...

From what I gather, powernap runs powernapd every 1 second by default... but even when I set different debug levels, I still don't get anything written to the logs in /var/log/ - where the config says it is...

I ran out of ideas, and tried a few other things, including doing ```
sudo powernapd
```, which funnily enough actually did start writing to the powernap.log file...

So I'm just confused as to what is going on. Each time after I change the config, I ran ```
sudo service powernap restart
``` and it always wrote something like: 

```
stop: Unknown instance:
powernap stop/pre-start, process 2501
```

In any case, I can't get the computer to suspend (running pm-suspend works fine), and am just really at a loss as to what powernap is doing... is it running at all, is it failing? 

I should also mention that I am running a fresh install of 13.10 server.

Any help much appreciated. I realise my post might not make sense, so please ask me questions if need be so I can make things clearer...

---

### Post by Habitual on 2013-12-04
> **Garf said:**
> ```
stop: Unknown instance:
powernap stop/pre-start, process 2501
```


```
lsof -p 2501
``` may help show you what it's doing.

---

### Post by Garf on 2013-12-05
Thanks for the reply....but...

That shows nothing... obviously I changed the 2501 for the new pid when I restarted it again...

---

### Post by Garf on 2013-12-07
Powernap seems to be pretty useless at the moment, are there and forums around that might be able to provide more help?

---

### Post by pastim on 2014-01-19
I had the same problem.  It may be worth looking in /etc/default/powernap.  For reasons unknown to me it had START=no in it.  Changing this to 'yes' and rebooting fixed it.

Why I couldn't start it manually after initial installation I have no idea.

---

### Post by bellera on 2014-02-27
I think you can suspend the machine after XX minutes ajusting your power management. **powernap** not needed for this.

[http://people.canonical.com/~bradf/power-management.html](http://people.canonical.com/~bradf/power-management.html)

I'm using **powernap** because power management can't poweroff the computer after an inactivity period. But i have some troubles...

[https://bugs.launchpad.net/ubuntu/+source/powernap/+bug/872109](https://bugs.launchpad.net/ubuntu/+source/powernap/+bug/872109)

Josep Pujadas-Jubany

---

### Post by pastim on 2014-02-27
> **bellera said:**
> I think you can suspend the machine after XX minutes ajusting your power management. **powernap** not needed for this.

[http://people.canonical.com/~bradf/power-management.html](http://people.canonical.com/~bradf/power-management.html)

I'm using **powernap** because power management can't poweroff the computer after an inactivity period. But i have some troubles...

[https://bugs.launchpad.net/ubuntu/+source/powernap/+bug/872109](https://bugs.launchpad.net/ubuntu/+source/powernap/+bug/872109)

Josep Pujadas-Jubany
The ubuntu power management doesn't do the job, since the system can be very busy when I am not using it.  Fortunately I don't have the same problem as you.

---

