---
title: "Problem with cron.weekly"
date: 2006-07-29
forum: General Help
---

### Post by erland on 2006-07-29
I have a problem with the /etc/cron.weekly script

I have added a script in this directory but for some reason it does not seem to run. It clearly run other scripts in this directory but  my new hdup.daily script don't run for some reason. I didn't get any mail about any failure as I do when the daily scripts in cron.daily runs.

I have tried to do a "sudo -s" and then call the script "/etc/cron.weekly/hdup.daily" manually and then it runs correctly.

Here is the output from /var/log/syslog when the weekly jobs where run:
```

Jul 28 07:40:01 xp2500 anacron[26586]: Job `cron.weekly' started
Jul 28 07:40:01 xp2500 anacron[26830]: Updated timestamp for job `cron.weekly' to 2006-07-28
Jul 28 07:40:02 xp2500 /USR/SBIN/CRON[26835]: (erland) CMD (/home/erland/bin/getmymail)
Jul 28 07:40:02 xp2500 hotwayd[26884]: connect from localhost (::ffff:127.0.0.1)
Jul 28 07:40:03 xp2500 exiting on signal 15
Jul 28 07:40:04 xp2500 syslogd 1.4.1#17ubuntu7: restart.
Jul 28 07:40:04 xp2500 anacron[26586]: Job `cron.weekly' terminated
Jul 28 07:40:04 xp2500 anacron[26586]: Normal exit (2 jobs run)

```

The cron stuff in the middle is just a mail script that is run as a separate crontab every 5'th minute, so that has nothing to do with the weekly script. The syslogd restart is probably comming from the /etc/cron.weekly/sysklogd script which would indicate that some weekly scripts run.

The permissions of my weekly hdup.daily script should be correct (the permissions in /etc/cron.weekly looks as follows):
```

-rwxr-xr-x 1 root root  312 2005-05-03 04:10 0anacron
-rwxr-xr-x 1 root root 1370 2005-11-22 06:17 cvs
-rwxr-xr-x 1 root root 1508 2006-07-27 11:17 hdup.daily
-rwxr-xr-x 1 root root  520 2005-09-26 17:12 man-db
-rwxr-xr-x 1 root root  665 2006-05-29 04:48 ntp-server
-rwxr-xr-x 1 root root 2730 2006-05-11 18:40 popularity-contest
-rwxr-xr-x 1 root root 1092 2006-04-24 20:36 sysklogd

```

Does anyone have any idea why my weekly hdup.daily script is not run and why I don't get any mail indicating the problem ?

---

### Post by erland on 2006-08-02
Does anyone have any idea how to find and solve this problem ?

---

### Post by keithweddell on 2006-08-02
I think I remember reading that for some reason your file in cron.weekly can't have a file extension - can't remember why not though.  Try renaming the file "hdupdaily".  Also I think the file must be owned by root. And just to be safe, check the permissions to make sure it's executable.

Good luck.

Keith

---

