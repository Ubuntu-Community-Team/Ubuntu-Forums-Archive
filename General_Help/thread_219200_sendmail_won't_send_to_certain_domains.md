---
title: "sendmail won't send to certain domains"
date: 2006-07-19
forum: General Help
---

### Post by maino82 on 2006-07-19
i have successfully configured  sendmail to send email through my php scripts on my webpage, however it only seems to work for certain domains (gmail being one). on others it has trouble for some reason. it appears to be trying to use each individual domain's smtp server, which causes problems with some domains/isps. is there any way to either specify which smtp server sendmail uses or use my own machine as an smtp server? i have looked at the how-tos on using postfix to send/receive mail, but never was able to get it to work. those tutorials are also much more than i need since all i want to do is send email using a simple form that allows people to put in a from email address and a to email address.

> Jul 19 13:02:03 localhost sm-mta[10099]: k6JJVSbb009322: to=<ADDRESS>, ctladdr=<www-data@localhost.localdomain> (33/33), delay=00:30:35, xdelay=00:01:07, mailer=esmtp, pri=390457, relay=MAILSERVER. [64.202.166.11], dsn=4.0.0, stat=Deferred: Name server: NAMESERVER.: host name lookup failure
Jul 19 13:02:03 localhost sm-mta[10099]: k6JJ90Cr008598: to=<ADDRESS>, ctladdr=<www-data@localhost.localdomain> (33/33), delay=00:53:03, xdelay=00:00:00, mailer=esmtp, pri=661259, relay=MAILSERVER., dsn=4.0.0, stat=Deferred: Name server: NAMESERVER.: host name lookup failure
Jul 19 13:12:09 localhost sm-mta[10359]: k6JJVSbb009322: to=<ADDRESS>, ctladdr=<www-data@localhost.localdomain> (33/33), delay=00:40:41, xdelay=00:01:13, mailer=esmtp, pri=480457, relay=MAILSERVER. [64.202.166.11], dsn=4.0.0, stat=Deferred: Name server: NAMESERVER.: host name lookup failure
Jul 19 13:12:09 localhost sm-mta[10359]: k6JJ90Cr008598: to=<ADDRESS>, ctladdr=<www-data@localhost.localdomain> (33/33), delay=01:03:09, xdelay=00:00:00, mailer=esmtp, pri=751259, relay=MAILSERVER., dsn=4.0.0, stat=Deferred: Name server: NAMESERVER.: host name lookup failure

---

