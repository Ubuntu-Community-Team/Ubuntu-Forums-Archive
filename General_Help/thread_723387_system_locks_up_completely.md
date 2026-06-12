---
title: "system locks up completely"
date: 2008-03-13
forum: General Help
---

### Post by vavoem on 2008-03-13
I find this in the system log at the time of the lock up which makes no sense because this runs every hour anyone an idea?

(root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)

---

### Post by McQuaid on 2008-04-02
I have the exact same thing.  That is the only thing I see in the logs near the time of the lockup.

This box was previously a dapper box for almost 2 years and never locked up.  Did a fresh install (formatting part) of hardy beta and had the lockups.  Upgraded to latest and it locked up today.  

I thought the same thing, if this is cron.hourly, I thought how can that be the issue.


When it locks, there's no response. can't ctrl alt backspace, nor ping ssh into the box.  I only caught alt sysrq REISUB once (if I don't do it quick it won't work it seems)  and the logs didn't reveal anything more.

This is what i see in syslog:

17:09:01 myth /USR/SBIN/CRON[12243]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find
Apr  2 17:17:01 myth /USR/SBIN/CRON[12253]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  2 17:25:48 myth syslogd 1.5.0#1ubuntu1: restart.

17:25 is when I rebooted.  17:17 is the closest thing in the logs I can find timestamped near the crash.

I also see this in auth.log 
Apr  2 17:09:01 myth CRON[12242]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  2 17:09:01 myth CRON[12242]: pam_unix(cron:session): session closed for user root
Apr  2 17:17:01 myth CRON[12252]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr  2 17:17:01 myth CRON[12252]: pam_unix(cron:session): session closed for user root

It's the only thing timestamped the same.

It looks up about twice a day.  But it seems if I do nothing over the network, (don't browse the web, use ssh or vnc it's stayed up for two days.)  I mainly have myth running on this box, no gnome (but gdm).  But when I was researching it in gnome, it locked as well.  Doesn't seem to matter if the box is under load or not.

I've ran cron.daily manually without issue.

---

### Post by kaurman on 2008-04-03
In my case it was the ipw3945 wifi module that was causing trouble. If you have desktop computer then this is probably not an option though.

---

