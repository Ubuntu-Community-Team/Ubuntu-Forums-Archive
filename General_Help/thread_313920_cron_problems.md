---
title: "cron problems"
date: 2006-12-06
forum: General Help
---

### Post by ryland22 on 2006-12-06
I can't get cron to work.  I opened up my shell, typed crontab -e, and put the following:

MAILTO = "me@yahoo.com"
59 18 6 * * echo "foo"

However, nothing is happening and no email is sent.  Can someone direct me as to what to try to do to get this working?

---

### Post by ryland22 on 2006-12-06
Ok, so I have now modified my crontab to point to a file and output to a logfile, ie:

01 20 6 * * /var/apache2-default/mjt_cron/test >> /var/apache2-default/mjt_cron/log

The test file has this one line:

echo "foo"

However, cron still doesn't appear to do anything.  No email is sent and nothing is written to the log file.  

Someone please help...

---

### Post by mitch.c on 2006-12-06
> **ryland22 said:**
> Ok, so I have now modified my crontab to point to a file and output to a logfile, ie:

01 20 6 * * /var/apache2-default/mjt_cron/test >> /var/apache2-default/mjt_cron/log

The test file has this one line:

echo "foo"

However, cron still doesn't appear to do anything.  No email is sent and nothing is written to the log file.  

Someone please help...

I could be wrong, but I think what you want to do is:
```
01 20 6 * * /bin/echo "foo" >> /var/apache2-default/mjt_cron/log
```

---

### Post by DaveBorealis on 2006-12-06
> **ryland22 said:**
> 
01 20 6 * * /var/apache2-default/mjt_cron/test >> /var/apache2-default/mjt_cron/log

The test file has this one line:

echo "foo"


Hello,

A couple guesses, if you don't mind me taking a shot.  Is the 'test' file executable?  If not, open a terminal and type 'sudo chmod 755 /var/apache2-default-mjt_cron/test'.  And try adding '#!/bin/sh' as the first line of your 'test' script.  (Also, giving the full path of '/bin/echo "foo"' couldn't hurt.)

HTH,
Dave

---

### Post by CoolHand on 2006-12-06
Well for starters I don't think any mail will be sent unless you have an MTA installed like sendmail.  I don't think that one is installed by default on Ubuntu.  I have noticed some environment issues with cron also but that is all.  In general it usually works for simple commands.

---

