---
title: "Strange email from Anacron"
date: 2015-01-25
forum: General Help
---

### Post by Lappert on 2015-01-25
I'm perplexed. I'm setting up an rsync system so certain parts of my kubuntu box are daily rsynced to my Debian server. That seems to be working OK. As part of that I added a line in /etc/anacrontab "MAILTO=horse@mydomain.net" so I would get the results of the daily rsync. That is working OK. If it would help, I can post my entire anacrontab file.

So now I'm getting a separate email with the subject line "Anacron job 'cron.daily' on MyMachineName" with the following contents:

> /etc/cron.daily/rkhunter:
0 (null)
[EMAIL="tenant@tenant.net"]donkey@mydomain.net[/EMAIL]: 250 Ok

[EMAIL="root@tenant.net"]root@mydomain.net[/EMAIL]: 550 [EMAIL="root@tenant.net"]<root@mydomain.net>[/EMAIL]: Recipient address rejected: User unknown in virtual alias table

Can't send mail: sendmail process failed with error code 70

Yes, there's a rkhunter in cron.daily, but I would get a separate email for any results in rkhunter. The user "donkey" is not the same as the user "horse" I set up in the mailto line. But both email addresses are for a domain hosted on our server. In fact this strange email cones from user horse.

ANy thoughts on what might be causing this? Thank you.

---

### Post by SeijiSensei on 2015-01-25
The machine that handles local delivery for mydomain.net doesn't recognize the root account.  Try this for starters.  Log into a terminal, then type the following
```

$ telnet localhost 25
[server replies with banner]
ehlo localhost
[server replies]
mail from: horse@mydomain.net
[OK]
rcpt to: root@mydomain.net

```
What do you see next?  Presumably the SMTP server, sendmail or Postfix, will throw the same error as you reported.  If so, then something in your server's configuration fails to create an alias for root in the mydomain.net domain.

---

### Post by Lappert on 2015-01-25
Thank you.

OK, I login (using Guake) to a shell, then su root. I don't even get to ehlo localhost:

root@MyMachine:/etc# telnet localhost 25
Trying ::1...
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
root@MyMachine:/etc#

---

### Post by SeijiSensei on 2015-01-26
You have to do this on the mail server.  Is that what you tried?  If you are on a client machine, replace "localhost" with the name or IP address of the server.

---

