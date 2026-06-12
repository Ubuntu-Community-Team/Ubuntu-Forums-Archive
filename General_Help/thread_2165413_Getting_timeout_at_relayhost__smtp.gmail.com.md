---
title: "Getting timeout at relayhost  smtp.gmail.com"
date: 2013-08-04
forum: General Help
---

### Post by kjaspan on 2013-08-04
Since either I had my DSL service restored or I changed my gmail password due to this forum having been hacked, my sendmail and mailx have stopped working. I followed the numerous postings about reinstalling exim4 (which failed) and sendmail but still get the following message in my mail.log:

[email]to<me@gmail.com[/email]>, ctladdr=<root@localhost.localdomain> (0/20), delay=00:04:00, xdelay=00:04:00, mailer=relay, pri=120361, relay=smtp.gmail.com [74.125.130.109], dsn=4.0.0, stat=Deferred: Connection timed out with smtp.gmail.com 

I replaced my email id and hostname above for security purposes.

Can anyone suggest any fix? I changed the line with DS in sendmail.cf to DSsmtp.gmail.com and to DSatt.yahoo.com with no success.

---

### Post by thespirit3 on 2013-08-05
Can you 'telnet smtp.gmail.com 25' ?   It would appear sendmail can't connect to gmail.

Can you connect to any other mail servers on port 25?    Best check your your ISP aren't doing something stupid and blocking the port.

---

### Post by kjaspan on 2013-08-05
No, the telnet times out. My smtp settings for gmail, AT&T and Yahoo are all for ports 465, by the way and telnet to smtp.gmail.com 465 succeeds and so does telnet smtp.att.yahoo.com. Where is port 25 specified and can I change that to 465?

Thanks for the help.

---

### Post by kjaspan on 2013-08-05
I found an answer on how to change the ports in sendmail.cf here [http://www.linuxforums.org/forum/servers/23275-sendmail-how-do-i-change-ports-being-used.html](http://www.linuxforums.org/forum/servers/23275-sendmail-how-do-i-change-ports-being-used.html)
but the line mentioned did not start DAEMON but rather
O DaemonPortOptions=Family=inet,  Name=MTA-v4, Port=smtp, Addr=127.0.0.1
and changing smtp to 465 and Addr to 0.0.0.0 resulted in "connection refused"
My ISP **does block port 25** and will not unblock it.

---

### Post by kjaspan on 2013-08-05
I found an answer on how to change the ports in sendmail.cf here [http://www.linuxforums.org/forum/servers/23275-sendmail-how-do-i-change-ports-being-used.html](http://www.linuxforums.org/forum/servers/23275-sendmail-how-do-i-change-ports-being-used.html)
but the line mentioned did not start DAEMON but rather
O DaemonPortOptions=Family=inet,  Name=MTA-v4, Port=smtp, Addr=127.0.0.1
and changing smtp to 465 and Addr to 0.0.0.0 resulted in "connection refused"
My ISP **does block port 25** and will not unblock it.

---

### Post by kjaspan on 2013-08-05
Also getting
Connection timed out with alt4.gmail-smtp-in.l.google.com
in mail.log

---

### Post by CharlesA on 2013-08-05
You can relay mail to port 587 for gmail.

Change this in main.cf
```
relayhost = smtp.gmail.com:587
```

---

### Post by kjaspan on 2013-08-05
Thanks, but that didn't work. I am using sendmail - postfix is different, isn't it? There is no relayhost line in sendmail.cf. There is a line beginning with DS in sendmail.cf that is supposed to allow setting the relayhost, in the form
DSsmtp.gmail.com

but I'm not sure you can add the port as you suggested.

Anyway that didn't work either. I tried mail instead of sendmail, too. 

I appreciate your help. Any other suggestions?

---

### Post by CharlesA on 2013-08-05
In any case, you should just need to change the port sendmail is trying to relay on. I use Postfix, so I don't know what configuration changes need to be done.

---

