---
title: "send mail to user, not root"
date: 2016-04-14
forum: General Help
---

### Post by chopra on 2016-04-14
Hi Guys,
Every time the flashplugin updates, I get a mail sent to ~mail/root:

```
from [EMAIL="root@Satellite-E45-B.locald"]root@Satellite-E45-B.locald[/EMAIL]omain  Sat Apr  9 14:36:11 2016
Return-Path: <root@Satellite-E45-B.localdomain>
X-Original-To: root
Delivered-To: [EMAIL="root@Satellite-E45-B.locald"]root@Satellite-E45-B.locald[/EMAIL]omain
Received: by Satellite-E45-B.localdomain (Postfix, from userid 0)
        id EAE67CC0B0A; Sat,  9 Apr 2016 14:36:10 -0500 (CDT)
From: Anacron <root@Satellite-E45-B.localdomain>
To: [EMAIL="root@Satellite-E45-B.locald"]root@Satellite-E45-B.locald[/EMAIL]omain
Subject: Anacron job 'cron.daily' on Satellite-E45-B
Content-Type: text/plain; charset=US-ASCII
Message-Id: <20160409193610.EAE67CC0B0A@Satellite-E45-B.localdomain>
Date: Sat,  9 Apr 2016 14:36:10 -0500 (CDT)

/etc/cron.daily/update-notifier-common:
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20160407.1.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20160407.1.orig.tar.gz)
Installing from local file /tmp/tmp6qzhwC.gz
Flash Plugin installed.

```

I want mail to go to my main user account, not the root account.  In the /etc/crontab file, I added the line:
MAILTO=chopra

I also have, in the /etc/alias file:
postmaster: chopra

But this has no effect. I can't find any other file that controls this behavior.

Thanks, Chopra

---

### Post by TheFu on 2016-04-14
Did you run "newaliases" to rebuild the DB file too?

Also - you probably want all root email redirected to chopra.

/etc/aliases
```
root: chopra
```

After every change to the /etc/aliases file, **sudo newaliases** must be re-run.

---

### Post by chopra on 2016-04-20
> **TheFu said:**
> Did you run "newaliases" to rebuild the DB file too?

Also - you probably want all root email redirected to chopra.

/etc/aliases
```
root: chopra
```

After every change to the /etc/aliases file, **sudo newaliases** must be re-run.

Thanks for the info. Yes, I had run sudo newailiases after the change.  I added the extra line and ran it again.  I'll just have to wait and see what happens the next time flashplugin updates.  I'm puzzled as to why the line of code in the anacron file didn't work, but hopefully this will solve it.

---

### Post by TheFu on 2016-04-20
Is an MTA configured and working on the machine?  Don't think aliases work without an MTA.

I have about 5-15 aliases on every server that I manage.  Can't just have 1 or some email to other commonly used userids will fill up /var.  A full /var is embarrassing when it makes the server crash.  I also configure postfix as a satellite node to forward all email to the "real" email server.

BTW - you've said "alias" and "aliases" - which is it?  The other thing - always put an empty line at the bottom of every config file.  Some parsers don't read EOF as CR/LF.  I'm just throwing out guesses.

Does anacron honor a /etc/crontab MAILTO?  Quick searches says that works for crontabs under /var/spool/cron ...   I wouldn't expect it to work for the 3 other cron methods possible. Definitely check that too.

Ok - I checked the manpage for anacron - 

>        If an executed job generates any output to standard output or to
       standard error, the output is mailed to the user under whom Anacron
       is running (usually root), or to the address specified in the MAILTO
       environment variable in the /etc/anacrontab file, if such exists.  If
       the LOGNAME environment variable is set, it is used in the From:
       field of the mail.
so - the file use changed won't work.

---

### Post by chopra on 2016-05-01
> **TheFu said:**
> Is an MTA configured and working on the machine?  Don't think aliases work without an MTA.

I have about 5-15 aliases on every server that I manage.  Can't just have 1 or some email to other commonly used userids will fill up /var.  A full /var is embarrassing when it makes the server crash.  I also configure postfix as a satellite node to forward all email to the "real" email server.

BTW - you've said "alias" and "aliases" - which is it?  The other thing - always put an empty line at the bottom of every config file.  Some parsers don't read EOF as CR/LF.  I'm just throwing out guesses.

Does anacron honor a /etc/crontab MAILTO?  Quick searches says that works for crontabs under /var/spool/cron ...   I wouldn't expect it to work for the 3 other cron methods possible. Definitely check that too.

Ok - I checked the manpage for anacron - 


so - the file use changed won't work.

Ahh, anacron and crontab have different files. That should have occured to me.  I meant to say aliases, but it looks like that was a red herring. 
   
It looks like all of the config files have an empty line at the end (altough I discovered that vim supresses that by default.)

I added the MAILTO=chopra to the /etc/anacrontab so we'll see if that works.
Thanks, Chopra

---

### Post by chopra on 2016-05-14
problem solved!  Just got an update and it sent the mail to ~mail/chopra instead of ~mail/root
marking thread as solved. Thanks.

---

