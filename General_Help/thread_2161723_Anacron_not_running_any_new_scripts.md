---
title: "Anacron not running any new scripts"
date: 2013-07-11
forum: General Help
---

### Post by mudri on 2013-07-11
I'm trying to run a command, rmtemp, using anacron. I've put the file in /etc/cron.daily, and hoped anacron would pick up the rest. rmtemp works correctly when typed into a terminal, but here it is:```
~$ cat /etc/cron.daily/rmtemp
#!/bin/bash

cd ~/Downloads
rm -rf -- temporary
mkdir temporary

```
/etc/anacrontab should be the default:```
~$ cat /etc/anacrontab
# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
HOME=/root
LOGNAME=root

# These replace cron's entries
1    5    cron.daily    run-parts --report /etc/cron.daily
7    10    cron.weekly    run-parts --report /etc/cron.weekly
@monthly    15    cron.monthly    run-parts --report /etc/cron.monthly
```
Here's some other stuff (today is Jul 11):```
~$ grep anacron /var/log/syslog
Jul 11 17:38:02 ubuntu anacron[1080]: Job `cron.daily' terminated (exit status: 1) (mailing output)
Jul 11 17:38:02 ubuntu anacron[1080]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Jul 11 17:38:02 ubuntu anacron[1080]: Normal exit (1 job run)
Jul 11 18:04:41 ubuntu anacron[3914]: Anacron 2.3 started on 2013-07-11
Jul 11 18:04:41 ubuntu anacron[3914]: Normal exit (0 jobs run)
Jul 11 18:05:02 ubuntu anacron[4110]: Anacron 2.3 started on 2013-07-11
Jul 11 18:05:02 ubuntu anacron[4110]: Normal exit (0 jobs run)
Jul 11 18:05:02 ubuntu anacron[4164]: Anacron 2.3 started on 2013-07-11
Jul 11 18:05:02 ubuntu anacron[4164]: Normal exit (0 jobs run)
Jul 11 22:48:02 ubuntu anacron[8572]: Anacron 2.3 started on 2013-07-11
Jul 11 22:48:02 ubuntu anacron[8572]: Normal exit (0 jobs run)
Jul 11 22:49:53 ubuntu anacron[8797]: Anacron 2.3 started on 2013-07-11
Jul 11 22:49:53 ubuntu anacron[8797]: Normal exit (0 jobs run)
Jul 11 22:50:15 ubuntu anacron[9004]: Anacron 2.3 started on 2013-07-11
Jul 11 22:50:15 ubuntu anacron[9004]: Normal exit (0 jobs run)
Jul 11 22:50:16 ubuntu anacron[9058]: Anacron 2.3 started on 2013-07-11
Jul 11 22:50:16 ubuntu anacron[9058]: Normal exit (0 jobs run)
Jul 11 22:59:11 ubuntu anacron[9425]: Anacron 2.3 started on 2013-07-11
Jul 11 22:59:11 ubuntu anacron[9425]: Normal exit (0 jobs run)
Jul 11 23:01:07 ubuntu anacron[9699]: Anacron 2.3 started on 2013-07-11
Jul 11 23:01:07 ubuntu anacron[9699]: Normal exit (0 jobs run)
Jul 11 23:01:07 ubuntu anacron[9753]: Anacron 2.3 started on 2013-07-11
Jul 11 23:01:07 ubuntu anacron[9753]: Normal exit (0 jobs run)
```
I also tried anacron -f, but nothing happened. Any help?

---

### Post by steeldriver on 2013-07-11
Hello and welcome to the forum

It may not be the *only* issue, but I presume you want to delete stuff in your user home directory? if so you will need to give an explicit path like 

```
/home/*yourusername*/Downloads
```
instead of 
```
~/Downloads
```

 (~ only expands to *your* home directory when *you* are logged in and running the command from an interactive shell)

---

### Post by CaptainMark on 2013-07-12
Also its good advice to avoid using the cd command in a script, there is just no need to do so and can get unexpected results. as steeldriver says use absolute paths

---

### Post by mudri on 2013-07-13
Okay; that makes sense. It's fixed now. Thanks!

---

