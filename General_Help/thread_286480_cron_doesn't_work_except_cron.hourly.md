---
title: "cron doesn't work except cron.hourly"
date: 2006-10-27
forum: General Help
---

### Post by larryalk on 2006-10-27
In my Kubuntu system 6.0.6 
/etc/cron.daily (and weekly/monthly) files are _never_ run  at all.    
However files in cron.hourly run ok.

My /etc/crontab indicates that cron.hourly files are run from cron but cron.daily, weekly and monthly are run by anacron.

However, anacron is not started on bootup as I would expect (per ps -al 
|grep anacron).

The questions:
Is it normal for (K)ubuntu to _not_ start anacron when booted?

What file should I edit to run anacron at boot time?

larryalk

---

### Post by scxtt on 2006-10-27
what if you remove **test -x /usr/sbin/anacron ||** from:

```
# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
```

---

### Post by larryalk on 2006-10-27
which anacron indicates that anacron is indeed in /usr/sbin/anacron so the test works.

As I said in the original post, anacron is not running at all for some reason.

larryalk

---

### Post by scxtt on 2006-10-27
what i'm saying is - cron.daily, cron.weekly, and cron.monthly are "defined" differently from cron.hourly, but cron.hourly "works" --- so why not define the other 3 in the same way, independent of anacron ... unless you specifically *need* anacron ...

```
# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    run-parts --report /etc/cron.daily
47 6    * * 7   root    run-parts --report /etc/cron.weekly
52 6    1 * *   root    run-parts --report /etc/cron.monthly
```

---

### Post by larryalk on 2006-10-27
scxtt let me thank you for your very prompt replies and concern.

I found the reason why Ubuntu uses cron to run /etc/cron.hourly and anacron to run the others.

It has to do with the ability of anacron to keep track of the last time it ran even if the machine is off.  Since anacron can only keep track of the _day_ it is not suitable for cron.hourly.

Anacron is clearly superior to cron and that's probably why Ubuntu chose it - but was forced to use something else (cron) for cron.hourly.
I accept Ubuntu's decision.

My question has to do with:
How do I run the anacron daemon which is currently not running, thus preventing Ubuntu from running scripts in /daily, /weekly and /monthly.

I'm actually a little surprised that Ubuntu does (apparently) not run anacron automatically on boot.  Of course I can run it in say /etc/rc.local with the line /usr/sbin/anacron start but, if Ubuntu is setup to run anacron on boot, I'd like to do it the same way.

Larry

---

### Post by scxtt on 2006-10-27
maybe it comes down to cron being loaded from /etc/rc2.d/S89cron fighting w/ /etc/rc2.d/S89anacron ... maybe if *cron isn't loaded, anacron will start up on boot ...

/etc/rc0.d/K11anacron
/etc/rc0.d/K11cron
/etc/rc1.d/K11anacron
/etc/rc1.d/K11cron
[B]/etc/rc2.d/S89anacron
/etc/rc2.d/S89cron
[/B]/etc/rc3.d/S89anacron
/etc/rc3.d/S89cron
/etc/rc4.d/S89anacron
/etc/rc4.d/S89cron
/etc/rc5.d/S89anacron
/etc/rc5.d/S89cron
/etc/rc6.d/K11anacron
/etc/rc6.d/K11cron

---

### Post by larryalk on 2006-10-27
scxtt:  I've looked at all the rc?.d and they appear to _all_ run anacron.  Also, when I run anacron (/usr/sbin/anacron start) it signs on but does not appear in ps -ax.  Very strange behavior indeed.

At this point, I'm hoping someone with more knowledge tells me what's going on.

Certainly, Ubuntu was designed to run both cron for /etc/cron.hourly and the other /etc/cron.*  I haven't done much that could mess that up - I think ;-)

What I don' understand is why other Ubuntu users report problems running programs in cron.daily et al.  There is no anacron.deny or anacron.accept in my /etc and all the scripts there are designed to be run by root.

At the very last resort I'll rewrite /etc/crontab to run everything with cron but I'd really rather do it the "ubuntu way".

In the meantime I'm running stuff like slocate update and ntptime every week or so although I much prefer for it to "just happen".

Thanks again for your help and responsiveness.

Larry

---

### Post by pks on 2007-03-20
the following is in the anacron documentation:

[INDENT]What is Anacron not?

Anacron is not an attempt to make cron redundant. It cannot be used to schedule commands at intervals smaller than days. It also does not guarantee that the commands will be executed at any specific day or hour.

It isn't a full-time daemon. It has to be executed from boot scripts, from cron-jobs, or explicitly. [/INDENT]

I believe the key is the last line.  the boot scripts claim to "start" anacron, when they're really only running it - anacron runs (either running jobs, or not depending on the time stamp files which reside in /var/spool/anacron) and exits.

From what I understand, cron is actually needed to run anacron periodically ... a script in /etc/cron.hourly that runs anacron -s (as the boot scripts on my system do) should do the trick.

The ultimate questions then are:

If ubuntu doesn't come configured to run periodically, how can the fact the the /etc/cron.[daily|weekly|monthly] scripts don't run slip past thousands of users?
If it comes configured to run anacron periodically, how did our systems wind up in state that doesn't?

I understand the post is pretty old, but I replied to it anyway - the questions you asked are the same questions that came to my mind.

---

### Post by pks on 2007-03-21
and a couple of hours later, I've confirmed that the /etc/cron.hourly/anacron script gets the job done - that is gets anacron to do its job.  I tested it by removing the time stamp file for the daily jobs /var/spool/anacron/cron.daily and waiting ...

the script is super simple:

#!/bin/sh
/usr/sbin/anacron -s

---

### Post by WebWeasel on 2007-03-27
I know this is an old thread but I thought I'd add a little more info.  If you're having problems getting something to run in cron.hourly make sure there are no periods "." in the script name. run-parts skips scripts with a period in their name.  A dash "-" is OK.

---

### Post by wizeman on 2007-03-28
Thanks!

I was having a hard time figuring out why my "ipmonitor.sh" script in cron.hourly wasn't running...

---

### Post by angkor on 2007-05-24
> **pks said:**
> and a couple of hours later, I've confirmed that the /etc/cron.hourly/anacron script gets the job done - that is gets anacron to do its job.  I tested it by removing the time stamp file for the daily jobs /var/spool/anacron/cron.daily and waiting ...

the script is super simple:

#!/bin/sh
/usr/sbin/anacron -s

A little late, but thanks...this helped me out. I still wonder if Ubuntu doesn't run cron.weekly or .monthly by default or that my system got changed by something I did.

---

### Post by helmingstay on 2007-05-31
I've been looking in the documentation for the answer to this for a month now!
I'm posting a bug to lauchpad.net including the fix included here.  If anyone else would like to update the wiki...

---

### Post by helmingstay on 2007-05-31
> **pks said:**
> 
If ubuntu doesn't come configured to run periodically, how can the fact the the /etc/cron.[daily|weekly|monthly] scripts don't run slip past thousands of users?
If it comes configured to run anacron periodically, how did our systems wind up in state that doesn't?


This bug only affects always-on computers.  It's hard to notice this unless your mean uptime is significantly more than one day.  

See the bug at [https://bugs.launchpad.net/ubuntu/+bug/118004](https://bugs.launchpad.net/ubuntu/+bug/118004)

---

