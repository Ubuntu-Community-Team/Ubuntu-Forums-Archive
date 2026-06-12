---
title: "Cron Job Issues"
date: 2013-07-11
forum: General Help
---

### Post by thedawg on 2013-07-11
Hello everyone,

I have some trouble with my Crontab.
I want a bunch of jobs to be started daily, things like updating the pkgsync lists from a file-server, running a pkgsync and other stuff. Now these jobs are daily because sometimes the PC's are running for a few days and when I make some system changes they should update them overnight by themselves. Problem is, that's not happening. Only after I boot/reboot, anacron takes over and starts the cron.daily. But that's no permanent solution. Maybe one of you has an idea how to fix this? :) 

System: Kubuntu 12.04 lts 
Crontab: 
" SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

# "
Logsys:

" Jul 11 06:17:01 im56 CRON[14463]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 11 06:23:14 im56 dhclient: DHCPREQUEST of ***.***.***.*** on eth0 to ***.***.***.*** port XY
Jul 11 06:23:14 im56 dhclient: DHCPACK of ***.***.***.*** from ***.***.***.***
Jul 11 06:23:14 im56 dhclient: bound to ***.***.***.*** -- renewal in 1651 seconds.
Jul 11 06:25:01 im56 CRON[14631]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Jul 11 06:39:01 im56 CRON[14898]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Jul 11 06:50:45 im56 dhclient: DHCPREQUEST of ***.***.***.*** on eth0 to ***.***.***.*** port XY
Jul 11 06:50:45 im56 dhclient: DHCPACK of ***.***.***.*** from ***.***.***.***
Jul 11 06:50:45 im56 dhclient: bound to ***.***.***.*** -- renewal in 1772 seconds.
Jul 11 07:09:02 im56 CRON[15490]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Jul 11 07:17:01 im56 CRON[15635]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 11 07:20:17 im56 dhclient: DHCPREQUEST of ***.***.***.*** on eth0 to ***.***.***.*** port XY
Jul 11 07:20:17 im56 dhclient: DHCPACK of ***.***.***.*** from ***.***.***.***
Jul 11 07:20:17 im56 dhclient: bound to ***.***.***.*** -- renewal in 1704 seconds.
Jul 11 07:39:01 im56 CRON[16071]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete) "


If you find anything else helpful just say it 

Best whises Thedawg

---

### Post by Cheesehead on 2013-07-11
> **thedawg said:**
>  Problem is, [cron.daily is] not happening. Only after I boot/reboot, anacron takes over and starts the cron.daily.
[...]
Crontab: 
# m h dom mon dow user  command
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
[...]
Logsys:
Jul 11 06:25:01 im56 CRON[14631]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))

It's not a crontab problem.
You seem to be trying to say that cron is not running cron.daily, but anacron is.
But the syslog entry shows that cron is indeed triggering cron.daily at 0625 just the way you told it to.

So your crontab is running, but perhaps your job output is not what you expected?
If you want us to help look into that, we need more information about your daily jobs.

---

