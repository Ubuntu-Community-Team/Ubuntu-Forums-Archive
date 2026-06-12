---
title: "Logwatch &amp; Postfix problems"
date: 2008-02-29
forum: General Help
---

### Post by MrCaptainC on 2008-02-29
Hello.

First of all I want to say thanks to everyone on here because without this forum I doub't I would have my server up and running at all.

Ok on to my problem...

I have a VPS which is running Ubuntu 7.04 according to my /etc/issue file.  On this I have installed postfix and logwatch using apt-get.

I have also installed the postfix-logwatch logwatch script from here [http://www.mikecappella.com/logwatch/](http://www.mikecappella.com/logwatch/)

Everything seems to run ok except the logs that logwatch email to me every day don't seem to match the log files when it comes to postfix.

For example, today I recieved this in my logwatch email from the standard logwatch postfix script...
```
 189726 bytes transferred
 10 messages sent
 10 messages removed from queue
 
 Top ten local senders:
    10 messages sent by:
       root (uid=0): 
 
 
 Relaying denied:
    From 219-84-254-55-adsl-kao.dynamic.so-net.net.tw[219.84.254.55] to send_1688_send@yahoo.com.tw : 2 Time(s)
 
 
 Connections lost:
    Connection lost while CONNECT : 4 Time(s)
    Connection lost while RCPT : 2 Time(s)
```

So off I went to look at the log files and notice that relaying was only denied once...
```
Feb 28 10:38:10 server postfix/smtpd[26318]: connect from 219-84-254-55-adsl-kao.dynamic.so-net.net.tw[219.84.254.55]
Feb 28 10:38:11 server postfix/smtpd[26318]: NOQUEUE: reject: RCPT from 219-84-254-55-adsl-kao.dynamic.so-net.net.tw[219.84.254.55]: 554 5.7.1 <send_1688_send@yahoo.com.tw>: Relay access denied; from=<p1h9op2g14s3@yahoo.com> to=<send_1688_send@yahoo.com.tw> proto=SMTP helo=<myip>
Feb 28 10:38:11 server postfix/smtpd[26318]: lost connection after RCPT from 219-84-254-55-adsl-kao.dynamic.so-net.net.tw[219.84.254.55]
Feb 28 10:38:11 server postfix/smtpd[26318]: disconnect from 219-84-254-55-adsl-kao.dynamic.so-net.net.tw[219.84.254.55]
Feb 28 10:40:24 server postfix/postfix-script: refreshing the Postfix mail system
Feb 28 10:40:24 server postfix/master[16187]: reload configuration /etc/postfix
Feb 28 10:40:24 server postfix/anvil[26331]: statistics: max connection rate 1/60s for (smtp:219.84.254.55) at Feb 28 10:38:10
Feb 28 10:40:24 server postfix/anvil[26331]: statistics: max connection count 1 for (smtp:219.84.254.55) at Feb 28 10:38:10
Feb 28 10:40:24 server postfix/anvil[26331]: statistics: max cache size 1 at Feb 28 10:38:10
```

The number of senders is also double what it should be too.

This is double count is also repeated in the the postfix-logwatch script section in the email aswell.

Now I think that this may be due to the fact that the default logfile list for maillogs includes both mail.log and syslog which seem to both carry the same information.  So I was wondering if it would be safe to remove the syslog from the maillist config and I would still catch everything that I need to catch in the logwatch output?

Thanks in advance,
Chris

---

### Post by Mr. C. on 2008-03-18
Chris,

There is no reason to have postfix output go to the main syslog log file.  Instead of removing entries from the logwatch configuration, instead, modify your syslog.conf file to have mail go only to mail.log.

If you're not sure how to do this, let us know.

btw. since you downloaded the postfix-logwatch package, why not install it into logwatch as well.  The report you are getting currently is from an ancient postfix logwatch filter.

---

