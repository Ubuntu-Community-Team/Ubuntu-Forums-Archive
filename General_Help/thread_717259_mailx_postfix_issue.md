---
title: "mailx postfix issue"
date: 2008-03-06
forum: General Help
---

### Post by lofftjm on 2008-03-06
I need to create a cronjob to send an email to an external mail address.  After reading a few "how-to" threads, I used the Synaptic Package Manager to install "Postfix"  I can now send email to an external mail address from the Terminal prompt using **mailx -s "Message subject text" [email]some.addr@domain.com[/email]**.  What I noticed since installing Postfix is that almost every minute I receive a local email with the following in it:


> From lofftjm@lofftjm-mpro  Thu Mar  6 20:49:01 2008
X-Original-To: lofftjm
From: root@lofftjm-mpro (Cron Daemon)
To: lofftjm@lofftjm-mpro
Subject: Cron <lofftjm@lofftjm-mpro> command to be executed
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/home/lofftjm>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=lofftjm>
Date: Thu,  6 Mar 2008 20:49:01 -0500 (EST)

/bin/sh: to: not found

If I turn of Postfix using **sudo /etc/init.d/postfix stop** I stop receiveing the local emails so I know this is somehow related to Postfix, but I'm stumped as to how to resolve it.

Any help would be greatly appreciated!

---

### Post by dcstar on 2008-03-07
> **lofftjm said:**
> I need to create a cronjob to send an email to an external mail address.  After reading a few "how-to" threads, I used the Synaptic Package Manager to install "Postfix"  I can now send email to an external mail address from the Terminal prompt using **mailx -s "Message subject text" [email]some.addr@domain.com[/email]**.  What I noticed since installing Postfix is that almost every minute I receive a local email with the following in it:




If I turn of Postfix using **sudo /etc/init.d/postfix stop** I stop receiveing the local emails so I know this is somehow related to Postfix, but I'm stumped as to how to resolve it.

Any help would be greatly appreciated!

You have a cron job that is set to run every minute, and it is not running correctly with the error reported at the end of that message.

---

### Post by lofftjm on 2008-03-07
I thought about an error in a cronjob too, but there is nothing that I can see that runs every minute.  The only thing I see is a job that runs once a day and has been working perfectly for months.

> 
root@lofftjm-mpro:~# ls -alpR /var/spool/cron/
/var/spool/cron/:
total 20
drwxr-xr-x  5 daemon daemon  4096 2007-10-15 19:20 ./
drwxr-xr-x 10 root   root    4096 2008-03-06 14:33 ../
drwxrwx--T  2 daemon daemon  4096 2007-10-15 19:27 atjobs/
drwxrwx--T  2 daemon daemon  4096 2007-02-20 08:41 atspool/
drwx-wx--T  2 root   crontab 4096 2008-02-28 11:03 crontabs/

/var/spool/cron/atjobs:
total 12
drwxrwx--T 2 daemon daemon 4096 2007-10-15 19:27 ./
drwxr-xr-x 5 daemon daemon 4096 2007-10-15 19:20 ../
-rw------- 1 daemon daemon    2 2007-10-15 19:27 .SEQ

/var/spool/cron/atspool:
total 8
drwxrwx--T 2 daemon daemon 4096 2007-02-20 08:41 ./
drwxr-xr-x 5 daemon daemon 4096 2007-10-15 19:20 ../

/var/spool/cron/crontabs:
total 12
drwx-wx--T 2 root    crontab 4096 2008-02-28 11:03 ./
drwxr-xr-x 5 daemon  daemon  4096 2007-10-15 19:20 ../
-rw------- 1 lofftjm crontab  556 2008-02-28 11:03 lofftjm

root@lofftjm-mpro:~# cat /var/spool/cron/atjobs/.SEQ 
0
root@lofftjm-mpro:~#

root@lofftjm-mpro:~# crontab -u lofftjm -l
# +---------------- minute (0 - 59)
# |  +------------- hour (0 - 23)
# |  |  +---------- day of month (1 - 31)
# |  |  |  +------- month (1 - 12)
# |  |  |  |  +---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
  *  *  *  *  *  command to be executed

  1  0  *  *  *  /home/lofftjm/mystuff/backup.bash >> /media/IomegaHDD/backups/backup.log 2>&1


---

### Post by lofftjm on 2008-03-13
I've had no luck figuring out what is running every minute so I uninstalled Postfix, then re-installed exim4 and the errors are still present when exim4 is running and stop when I stop exim4.

---

### Post by lofftjm on 2008-03-13
I just figured it out...missing a comment in a line in my crontab (see above) and it only took me 6 days to finially see it!

---

