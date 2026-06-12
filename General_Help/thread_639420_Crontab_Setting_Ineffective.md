---
title: "Crontab Setting Ineffective"
date: 2007-12-13
forum: General Help
---

### Post by LaneLester on 2007-12-13
Because I turn my computer off at night, I changed the default daily setting in crontab to:
25 14	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
so it wouldn't run slocate when I boot up in the morning. But the change seems to have no effect.

locate crontab turned up only one other instance in /usr/bin.

Lane

---

### Post by dagnabit dang doohickey on 2007-12-13
The line(s) in crontab that you're referring to will not do anything if /usr/sbin/anacron exists. The lines tell cron to run the scripts only if anacron doesn't exist.
```
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
```
To modify the jobs of anacron, you would need to edit anacrontab.
Also, if you take a look in /etc/cron.daily/ you'll see that it's not just slocate that will be affected by modifying the daily anacron job.

---

### Post by LaneLester on 2007-12-13
> **dagnabit dang doohickey said:**
> Also, if you take a look in /etc/cron.daily/ you'll see that it's not just slocate that will be affected by modifying the daily anacron job.

Yes, I see what you mean. Perhaps I should just execute slocate at a different time. Basically, I think I want something like this 
25 14 * * * lane /root/slocate
since I moved slocate to /root.

Is that line correct, and where does it go?

Lane

---

### Post by dagnabit dang doohickey on 2007-12-13
You might want to move slocate to /etc/cron.d/ then add the following line to anacrontab.
```
14       25      cron.slocate      nice /etc/cron.d/slocate
```
You can always create a new directory in /etc/ for slocate and any other scripts you may want to run at this biweekly interval you've chosen. For example: The following is a line you would add to anacrontab to run all scripts in /etc/cron.biweekly/ 25 minutes after boot every 14 days.
```
14       25      cron.biweekly      nice run-parts --report /etc/cron.biweekly
```

---

### Post by LaneLester on 2007-12-13
That just demonstrates that a little knowledge is a dangerous thing. I thought my string was to set: minutes hours (not sure about these) user command. I was trying to get it to run daily at 2:25 p.m.!  :)

I just don't want it running in the morning when I'm trying to get work done.

Lane

---

### Post by dagnabit dang doohickey on 2007-12-13
Actually, for a cron job, it was set for 2:25PM, but I falsely assumed you were going to continue using anacron to run slocate, and anacrontab has a different format than crontab.
Assuming slocate is located in /etc/cron.d/ the crontab job to run slocate at 2:25PM would be:
```
25 14    * * *   root    nice /etc/cron.d/slocate
```

---

### Post by LaneLester on 2007-12-14
> **dagnabit dang doohickey said:**
> 
Assuming slocate is located in /etc/cron.d/ the crontab job to run slocate at 2:25PM would be:
```
25 14    * * *   root    nice /etc/cron.d/slocate
```

Great! And thanks! 

Now to copy this thread to where I'll have it the next time I install a Ubuntu version. :)

Lane

---

