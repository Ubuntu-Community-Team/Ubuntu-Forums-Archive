---
title: "mail and crontab"
date: 2013-04-24
forum: General Help
---

### Post by jreed72 on 2013-04-24
To start I'm fairly new to ubuntu and working in Linux. In short, I'm trying to get an email notification working through a crontab for running a backup script for plone.
I'm working off Ubuntu 12.1 install.
the Story so far.
I setup thunderbird email to connect to my companies exchange network using my normal company email.
I added a mailto directive to my crontab like so :  mailto=jreed@lfinance.ca, this directive was prior to crontab directive and on a seperate line.
This did not work and wouldn't even throw an event to mail.log or mail.err
I did some research and it lead me to installing postfix. When I setup postfix it gave me a series of options of which I selected satellite as it sounded pertinent to my situation.
I amended my crontab to read as:
[HR][/HR][FONT=courier new]# mailto=jreed@lfinance.ca
41 * * * * ../../usr/local/Plone/zeocluster/bin/backup >> ../../usr/local/Plone/zeocluster/var/backups/cron.log 2>&1 mail -s 'Backup confirmation' [EMAIL="jreed@lfinance.ca"]jreed@lfinance.ca[/EMAIL][/FONT]
[HR][/HR]The time was just set so it would run after I saved current job, it will be changed later.
This gave me a log entry as:


[HR][/HR]Apr 24 11:41:02 plone postfix/pickup[14988]: D5C98A20350: uid=0 from=<root>
Apr 24 11:41:02 plone postfix/cleanup[15280]: D5C98A20350: message-id=<20130424184102.D5C98A20350@plone>
Apr 24 11:41:02 plone postfix/qmgr[14989]: D5C98A20350: from=<root@lfinance.ca>, size=653, nrcpt=1 (queue active)
Apr 24 11:41:02 plone postfix/local[15284]: D5C98A20350: to=<root@lfinance.ca>, orig_to=<root>, relay=local, delay=0.27, delays=0.23/0/0/0.03, dsn=2.0.0, status=sent (delivered to mailbox)
Apr 24 11:41:02 plone postfix/qmgr[14989]: D5C98A20350: removed


[HR][/HR]I guess I'm not sure what is going down here, and why its sending to root@ instead of jreed@
I'm guessing I have setup Postfix erroneously, but not sure how to correct and to work with my current situation.
Any help would be appreciated!

---

### Post by jreed72 on 2013-04-25
Anyone have some info or link on how to setup postfix for a situation like this?
FYI, email domain i have here has been altered...

---

### Post by Habitual on 2013-04-25
Wow. I am amazed that cron runs at all. oh well, since [Postfix has several hundred configuration parameters]("http://www.postfix.org/BASIC_CONFIGURATION_README.html"), this  is all I have.

---

### Post by jreed72 on 2013-04-25
thanks, I'll scope out that doc and see if I can figure it out

---

