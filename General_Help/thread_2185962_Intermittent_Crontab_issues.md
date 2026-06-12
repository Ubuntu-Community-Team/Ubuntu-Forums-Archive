---
title: "Intermittent Crontab issues"
date: 2013-11-05
forum: General Help
---

### Post by adam.watson1 on 2013-11-05
I have an old desktop with ubuntu server 12.04 on it. I have crontab set up to run a python script every night at 6pm. It will work for a few weeks then not run and I have to manually run it. After that it runs again.

I added a line to crontab to just touch a file to see if it is a problem with cron not running the jobs or the python script not running and it seems to be cron.

Here is the extract from crontab -l:

```
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command
SHELL=/bin/bash
0 18 * * * touch /home/sabrefish/Adam/OOH/crontest.log
01 18 * * * cd /home/sabrefish/Adam/OOH && source /home/sabrefish/py33/bin/activate && python NumberChecker.py
0 19 * * * cd ~ && ./oohbckup.sh

```
It ran fine until 31 Oct. crontest.log has not been touched since then and the python script hasn't been run since.

Why would cron randomly stop? What can I do to debug this?

Many thanks for any help

Adam

---

### Post by ian-weisser on 2013-11-05
Look for cron-related events in /var/log/syslog: **cat /var/log/syslog | grep cron**
Since your crontab jobs run at an obscure hour, look in the previous syslog also: **cat /var/log/syslog.1 | grep cron**

---

### Post by spjackson on 2013-11-05
Is this machine on constantly?
Do cron processes for any other users continue to run successfully?

When it appears to have stopped, check if the process is running, e.g.
```

ps -eF | fgrep cron

```
Look in /var/log for any messages.

Maybe change the touch job to run every minute to give more precise information about when it stops.

If the problem is related to cron/crontab, which is suggested by the fact that crontest.log is not touched, then I can't see how running your python script manually is going to start cron running again. So that is very puzzling.

---

### Post by adam.watson1 on 2013-11-05
Thanks for the replies. I have found the logs and the one from the first day it failed (last sucessfully ran 31/10, then failed every night since) 

here is a section of the log:

```

Nov  1 17:17:01 kevin CRON[22012]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 17:39:02 kevin CRON[22067]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdept$
Nov  1 18:00:01 kevin CRON[22139]: (sabrefish) CMD (touch /home/sabrefish/Adam/OOH/crontest.log)
Nov  1 18:00:01 kevin CRON[22137]: (CRON) info (No MTA installed, discarding output)
Nov  1 18:01:01 kevin CRON[22146]: (sabrefish) CMD (cd /home/sabrefish/Adam/OOH && source /home/sabrefish/py33/bin/activate && python NumberChecker.py)
Nov  1 18:01:01 kevin CRON[22144]: (CRON) info (No MTA installed, discarding output)
Nov  1 18:09:01 kevin CRON[22168]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdept$
Nov  1 18:17:01 kevin CRON[22194]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 18:39:01 kevin CRON[22263]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdept$
Nov  1 19:00:01 kevin CRON[22321]: (sabrefish) CMD (cd ~ && ./oohbckup.sh)
Nov  1 19:00:01 kevin CRON[22319]: (CRON) info (No MTA installed, discarding output)



```

The machine is on all the time, there aren't any other users other than root.

It looks to my untrained eye that it is trying to run it and failing for some reason. I believe the no MTA error is due to no mail server set up? 

I ran the python script earlier and it ran fine, I have changed the touch cron job to run every minute and its running fine now.

I'm at a loss. Could the python script be blocking cron somehow? I have added > /tmp/adam.log and > /tmp/adam2.log to the python job to see if it reports an error next time it fails.

Any more ideas?

Adam

---

### Post by ian-weisser on 2013-11-05
It's a scripting issue, not a cron issue.

Here is how we can tell.

Here is what normal cron output looks like. This script ran just fine.
```
Nov  1 17:17:01 kevin CRON[22012]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

Here is what a cronjob with a broken script looks like. This script aborted, and the system tried to e-mail you notice of the failure. An unrelated MTA problem prevented the notice from reaching you.
```

Nov  1 18:00:01 kevin CRON[22139]: (sabrefish) CMD (touch /home/sabrefish/Adam/OOH/crontest.log)
Nov  1 18:00:01 kevin CRON[22137]: (CRON) info (No MTA installed, discarding output)

```

You are correct - cron is trying to run it. You are also correct that there is no Mail Transport Agent (MTA) installed - Ubuntu does not ship with one, though they are available in the repositories.

If the problem was cron, no cronjobs would run. The problem is almost never cron itself.

You are correct to use redirection to a log to capture the cron output. I recommend  "> /tmp/adam.log 2>&1"
The 2>&1 will redirect STDERR and STDOUT to the tmp log (instead of cronmail) 

Python scripts cannot block cron.

The *most common* reason for a cron job failing is an incomplete path (also known as a different environment)
The two jobs of yours that fail, for example, both require access to /usr/bin.
See [http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work/23469](http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work/23469)

First thing to try: Check your env output (see that AskUbuntu link.)
Second thing to try: Use full paths. Change touch to /usr/bin/touch and python to /usr/bin/python

---

### Post by adam.watson1 on 2013-11-05
Thanks for the answer but would this explain the intermittent nature of the failures?  Today I set both the touch job and the python script to run every minute and every 3 minutes which they did all day?

I'm at home now and the box is at work so so I'll apply the suggested changes in the morning

---

### Post by ian-weisser on 2013-11-05
Intermittent failures could be due to an update, a changed environment setting, permissions, installing or uninstalling a related package, lots of possibilities. A bit like chasing an intermittent in an automobile - more data about the problem is needed to narrow the possibilities.

For example, something you installed may have changed your PATH environment variable. Or an edit may have erased cron's reference to that variable.

Happy to read it's working again!

---

### Post by adam.watson1 on 2013-11-06
I have edited the touch cron job to /usr/bin/touch so will have to sit back and wait to see if it carries on working. I did add /usr/bin to the python one but it stopped it working, I guess as python runs in a virtual environment as its 3.3 so I will have to do a bit of research to get the correct path for that.

env returned this at the command line for path:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

and this via cron
PATH=/usr/bin:/bin

Problem is I don't really know how to interpret that?

Thanks for the help, 

Adam

---

### Post by adam.watson1 on 2013-12-09
Hi,

It failed to run on 6th December and failed to run every night since. I cut and paste the command out of crontab -l and run it on the command line and it worked fine.

Here is the syslog from he first time it failed:
```
Dec  6 18:00:01 kevin CRON[15197]: (sabrefish) CMD (/usr/bin/touch /home/sabrefish/Adam/OOH/crontest.log > /tmp/adam.log 2>&1)
Dec  6 18:00:01 kevin CRON[15202]: (sabrefish) CMD (cd /home/sabrefish/Adam/OOH && source /home/sabrefish/py33/bin/activate &&  /home/sabrefish/py33/bin/python3.3 NumberChecker.py > /tmp/adam2.log 2>&1)
Dec  6 18:00:01 kevin sm-msp-queue[15216]: My unqualified host name (kevin) unknown; sleeping for retry
Dec  6 18:00:01 kevin sendmail[15204]: My unqualified host name (kevin) unknown; sleeping for retry
Dec  6 18:01:01 kevin CRON[15222]: (sabrefish) CMD (/usr/bin/touch /home/sabrefish/Adam/OOH/crontest.log > /tmp/adam.log 2>&1)
Dec  6 18:01:01 kevin sm-msp-queue[15216]: unable to qualify my own domain name (kevin) -- using short name
Dec  6 18:01:01 kevin sendmail[15204]: unable to qualify my own domain name (kevin) -- using short name
Dec  6 18:01:01 kevin sendmail[15204]: rB6I11bT015204: from=sabrefish, size=476, class=0, nrcpts=1, msgid=<201312061801.rB6I11bT015204@kevin>, relay=sabrefish@localhost
Dec  6 18:01:02 kevin sm-mta[15226]: rB6I11ET015226: from=<sabrefish@kevin>, size=704, class=0, nrcpts=1, msgid=<201312061801.rB6I11bT015204@kevin>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Dec  6 18:01:02 kevin sendmail[15204]: rB6I11bT015204: to=sabrefish, ctladdr=sabrefish (1000/1000), delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=30476, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (rB6I11ET015226 Message accepted for delivery)
Dec  6 18:01:02 kevin sm-mta[15227]: rB6I11ET015226: to=<sabrefish@kevin>, ctladdr=<sabrefish@kevin> (1000/1000), delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30901, dsn=2.0.0, stat=Sent


```


In /var/mail/ is this:

```
From sabrefish@kevin Sun Dec  8 18:01:02 2013
Return-Path: <sabrefish@kevin>
Received: from kevin (localhost [127.0.0.1])
        by kevin (8.14.4/8.14.4/Debian-2ubuntu2.1) with ESMTP id rB8I12Hk012752
        for <sabrefish@kevin>; Sun, 8 Dec 2013 18:01:02 GMT
Received: (from sabrefish@localhost)
        by kevin (8.14.4/8.14.4/Submit) id rB8I12js012731
        for sabrefish; Sun, 8 Dec 2013 18:01:02 GMT
Date: Sun, 8 Dec 2013 18:01:02 GMT
Message-Id: <201312081801.rB8I12js012731@kevin>
From: root@kevin (Cron Daemon)
To: sabrefish@kevin
Subject: Cron <sabrefish@kevin> cd /home/sabrefish/Adam/OOH && source /home/sabrefish/py33/bin/activate &&  /home/sabrefish/py33/bin/python3.3 NumberChecker.py > /tmp/adam2.log 2>&1
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/bash>
X-Cron-Env: <HOME=/home/sabrefish>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=sabrefish>
Content-Length: 75

/bin/bash: line 0: cd: /home/sabrefish/Adam/OOH: No such file or directory


```

It still points to the path being wrong but how else can I define it than from the root?

I'm at a loss so any help would be really appreciated 

Adam

---

### Post by ian-weisser on 2013-12-09
The description of the error seems to indicate an unchanged or somehow-reverted crontab lurking somewhere. Do you know where?

Cron does not keep backup copies to revert to. But you or your backup service might.

---

### Post by adam.watson1 on 2013-12-09
There is no back up of the box. 
After I ran the command manually earlier the cron job worked perfectly this evening

---

