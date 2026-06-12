---
title: "Apache Stops over night"
date: 2007-08-08
forum: General Help
---

### Post by BodleyTunes on 2007-08-08
In the morning when I come into work, the apache service is mysteriously down.  This is running our intranet.

I checked what I thought were the logs and see no errors.

The service starts fine straight away when I click start, but I dont see what is scheduling or causing it to just stop over night?

Can anyone give me any hints and tips as how to troubleshoot this as I'm more of a Windows Server person than a linux-meister :)

Regards,

Jon.

---

### Post by mssever on 2007-08-08
Hmm...What's your setup like? On my setup, there's no start button to click. On my system, Apache is controlled entirely from the command line.

When you looked through the logs, were you looking under /var/log/apache2? If there are no errors there, that's really weird. You might want to write up a little script that checks whether Apache is currently alive and emails you (or writes a log with a timestamp somewhere) if it isn't. If you set that up as a cron job that runs every minute, you'll know when Apache is dying. Then you might be able to discover a pattern, or look through other system logs at around the same time and see if there's anything suspicious going on.

---

### Post by BodleyTunes on 2007-08-08
> **mssever said:**
> Hmm...What's your setup like? On my setup, there's no start button to click. On my system, Apache is controlled entirely from the command line.

When you looked through the logs, were you looking under /var/log/apache2? If there are no errors there, that's really weird. You might want to write up a little script that checks whether Apache is currently alive and emails you (or writes a log with a timestamp somewhere) if it isn't. If you set that up as a cron job that runs every minute, you'll know when Apache is dying. Then you might be able to discover a pattern, or look through other system logs at around the same time and see if there's anything suspicious going on.

Hi,

Sorry I should have explained.  I started the apache services from a webmin interface.

I have been checking the logs from webmin also (which are in the location you stated) and there seems to be nothing that seems like there are any errors.

Regards,

Jonathan.

---

### Post by mssever on 2007-08-08
From what I hear, webmin sounds like it's pretty good. But when something goes wrong, I have a tendency to mistrust such applications to report what's really going on. Maybe that's unfounded, but maybe you should control Apache from the command line for now.

Here's a script you could use to find out when Apache died.

```
#!/bin/bash
while true; do
    ps -ef | grep -v grep | grep apache > /dev/null
    status=$?
    if [ $status -ne 0 ]; then
        echo "Apache just died. Time: `date`"
        exit
    fi
    sleep 30
done
```Save that script in a file somewhere and make it executable (chmod +x filename). Then run it from a terminal before you go home and leave it running. This will give you a time period to use when searching your logs.

In addition to all the logs  in /var/log/apache2, be sure to look through the other system logs in /var/log, especially /var/log/daemon.log, /var/log/messages, /var/log/syslog, and possibly /var/log/kern.log.

EDIT: If you use the string apache somewhere in the filename of this script, it might not work properly.

---

### Post by BodleyTunes on 2007-08-10
Thanks for that I'll try it tonight

---

### Post by BodleyTunes on 2007-08-13
> **mssever said:**
> From what I hear, webmin sounds like it's pretty good. But when something goes wrong, I have a tendency to mistrust such applications to report what's really going on. Maybe that's unfounded, but maybe you should control Apache from the command line for now.

Here's a script you could use to find out when Apache died.

```
#!/bin/bash
while true; do
    ps -ef | grep -v grep | grep apache > /dev/null
    status=$?
    if [ $status -ne 0 ]; then
        echo "Apache just died. Time: `date`"
        exit
    fi
    sleep 30
done
```Save that script in a file somewhere and make it executable (chmod +x filename). Then run it from a terminal before you go home and leave it running. This will give you a time period to use when searching your logs.

In addition to all the logs  in /var/log/apache2, be sure to look through the other system logs in /var/log, especially /var/log/daemon.log, /var/log/messages, /var/log/syslog, and possibly /var/log/kern.log.

EDIT: If you use the string apache somewhere in the filename of this script, it might not work properly.

OK, I ran the script on friday afternoon when I was leaving, just got back and it had this on the command prompt.

**Apache just died. Time: Sat Aug 11 06:26:24 BST 2007**

---

### Post by BodleyTunes on 2007-08-13
The only thing in apache error.log is this ??

**[Sat Aug 11 06:25:59 2007] [notice] caught SIGTERM, shutting down**

---

### Post by mssever on 2007-08-14
> **BodleyTunes said:**
> OK, I ran the script on friday afternoon when I was leaving, just got back and it had this on the command prompt.

**Apache just died. Time: Sat Aug 11 06:26:24 BST 2007**

> **BodleyTunes said:**
> The only thing in apache error.log is this ??

**[Sat Aug 11 06:25:59 2007] [notice] caught SIGTERM, shutting down**

SIGTERM is a signal usually used to ask a program to shut down normally. That message suggests that some process is asking Apache to shut down (in other words, Apache isn't crashing). You might check the crontab to see if there's a process that might be to blame. Also, you might want to check to see if Apache is shutting down at approximately the same time every morning. If so, that points further to some cron job.

---

### Post by BodleyTunes on 2007-08-14
As far as I know the only cron jobs i am running are the mysql sheduled backups of a gallery db and joomla db and also a filesystem backup that I setup to run from webmin.

?

I think it is the same time every morning.

---

### Post by BodleyTunes on 2007-08-14
I'm sure its not being rebooted because everything else is up (webmin interface etc) it must be just shutting down the apache service.

Whenever I manually reboot, apache defo comes back up.

I'll look into the cron jobs.

---

### Post by BodleyTunes on 2007-08-14
[SIZE="1"]```
Aug 12 07:09:01 ubuntu01 /USR/SBIN/CRON[14608]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 07:17:01 ubuntu01 /USR/SBIN/CRON[14619]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 07:39:01 ubuntu01 /USR/SBIN/CRON[14626]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 08:09:01 ubuntu01 /USR/SBIN/CRON[14641]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 08:17:01 ubuntu01 /USR/SBIN/CRON[14652]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 08:39:01 ubuntu01 /USR/SBIN/CRON[14659]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 09:09:02 ubuntu01 /USR/SBIN/CRON[14674]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 09:17:01 ubuntu01 /USR/SBIN/CRON[14684]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 09:39:01 ubuntu01 /USR/SBIN/CRON[14691]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 10:09:01 ubuntu01 /USR/SBIN/CRON[14708]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 10:17:01 ubuntu01 /USR/SBIN/CRON[14719]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 10:39:01 ubuntu01 /USR/SBIN/CRON[14726]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 11:09:01 ubuntu01 /USR/SBIN/CRON[14741]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 11:17:01 ubuntu01 /USR/SBIN/CRON[14752]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 11:39:01 ubuntu01 /USR/SBIN/CRON[14759]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 12:09:01 ubuntu01 /USR/SBIN/CRON[14774]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 12:17:01 ubuntu01 /USR/SBIN/CRON[14785]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 12:39:01 ubuntu01 /USR/SBIN/CRON[14792]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 13:09:01 ubuntu01 /USR/SBIN/CRON[14807]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 13:17:01 ubuntu01 /USR/SBIN/CRON[14818]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 13:39:01 ubuntu01 /USR/SBIN/CRON[14825]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 14:09:01 ubuntu01 /USR/SBIN/CRON[14840]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 14:17:02 ubuntu01 /USR/SBIN/CRON[14851]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 14:39:01 ubuntu01 /USR/SBIN/CRON[14858]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 15:09:01 ubuntu01 /USR/SBIN/CRON[14873]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 15:17:02 ubuntu01 /USR/SBIN/CRON[14884]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 15:39:01 ubuntu01 /USR/SBIN/CRON[14891]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 16:09:01 ubuntu01 /USR/SBIN/CRON[14906]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 16:17:01 ubuntu01 /USR/SBIN/CRON[14917]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 16:39:01 ubuntu01 /USR/SBIN/CRON[14924]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 17:09:01 ubuntu01 /USR/SBIN/CRON[14941]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 17:17:01 ubuntu01 /USR/SBIN/CRON[14952]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 17:39:01 ubuntu01 /USR/SBIN/CRON[14959]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 18:09:01 ubuntu01 /USR/SBIN/CRON[14974]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 18:17:01 ubuntu01 /USR/SBIN/CRON[14985]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 18:39:01 ubuntu01 /USR/SBIN/CRON[14992]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 19:09:01 ubuntu01 /USR/SBIN/CRON[15007]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 19:17:02 ubuntu01 /USR/SBIN/CRON[15018]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 19:39:01 ubuntu01 /USR/SBIN/CRON[15025]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 20:09:02 ubuntu01 /USR/SBIN/CRON[15040]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 20:17:02 ubuntu01 /USR/SBIN/CRON[15051]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 20:39:01 ubuntu01 /USR/SBIN/CRON[15058]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 21:09:01 ubuntu01 /USR/SBIN/CRON[15073]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 21:17:01 ubuntu01 /USR/SBIN/CRON[15084]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 21:39:02 ubuntu01 /USR/SBIN/CRON[15091]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 22:09:01 ubuntu01 /USR/SBIN/CRON[15105]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 22:17:01 ubuntu01 /USR/SBIN/CRON[15116]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 22:39:01 ubuntu01 /USR/SBIN/CRON[15123]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 23:09:01 ubuntu01 /USR/SBIN/CRON[15138]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 12 23:17:01 ubuntu01 /USR/SBIN/CRON[15149]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 12 23:39:01 ubuntu01 /USR/SBIN/CRON[15156]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 13 00:00:01 ubuntu01 /USR/SBIN/CRON[15170]: (root) CMD (/etc/webmin/mysql/backup.pl gallery2)
Aug 13 00:00:01 ubuntu01 /USR/SBIN/CRON[15172]: (root) CMD (/etc/webmin/mysql/backup.pl joomla01)
Aug 13 00:00:01 ubuntu01 /USR/SBIN/CRON[15175]: (root) CMD (/etc/webmin/fsdump/backup.pl 126411186561957)
Aug 13 00:09:01 ubuntu01 /USR/SBIN/CRON[15235]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0$
Aug 13 00:17:01 ubuntu01 /USR/SBIN/CRON[15246]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```[/SIZE]

^G Get Help               ^O WriteOut               ^R Read File              ^Y Prev Page              ^K Cut Text               ^C Cur Pos
^X Exit                   ^J Justify                ^W Where Is               ^V Next Page              ^U UnCut Text             ^T To Spell

---

### Post by BodleyTunes on 2007-08-14
> **mssever said:**
> SIGTERM is a signal usually used to ask a program to shut down normally. That message suggests that some process is asking Apache to shut down (in other words, Apache isn't crashing). You might check the crontab to see if there's a process that might be to blame. Also, you might want to check to see if Apache is shutting down at approximately the same time every morning. If so, that points further to some cron job.

It seems to by around this that it all happens

this is from the syslog log file:

```
Aug 11 06:25:02 ubuntu01 /USR/SBIN/CRON[13378]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Aug 11 06:25:32 ubuntu01 kernel: [933362.008355] SMB connection re-established (-5)
```

---

### Post by mssever on 2007-08-14
Well, I guess the cron log doesn't show anything enlightening. But run-parts was mentioned...

Here's a stab in the dark (because I really don't know what else to do):

First, post the output of ```
sudo crontab -l
```

Next, in the /etc directory, there are several files and directories whose names begin with cron. Look through those and see if anything jumps up. Something, somewhere, is sending SIGTERM to Apache, but I have no idea what that could be.

---

### Post by Sporkman on 2007-11-12
I'm getting the same thing, every morning at 7:35 (though apache starts back up afterwards).

It occurs after "anacron" starts up & starts cron.daily, etc. However, neither crontabl -l nor sudo crontab -l turns up any cron jobs around that time...

Any ideas? I'd like for this not to happen...

---

### Post by mssever on 2007-11-13
> **Sporkman said:**
> I'm getting the same thing, every morning at 7:35 (though apache starts back up afterwards).

It occurs after "anacron" starts up & starts cron.daily, etc. However, neither crontabl -l nor sudo crontab -l turns up any cron jobs around that time...

Any ideas? I'd like for this not to happen...
Probably something in cron.daily...

---

