---
title: "Problems with forwarding root mail"
date: 2013-03-30
forum: General Help
---

### Post by alawson on 2013-03-30
Hi,

I'm trying to get one of the machines on my home network to forward root's mail to my gmail.

I have set a .forward in /root and an alias in /etc/aliases to point to my gmail address.
I get quite a lot of mail coming through. This machine does unattended updates; mails from that come through fine.

But some system tasks seem to have problems. I have a cron job which runs at 35 mins past every hour, and it sends the mail to root, but the mail is re-directed to [email]root@hostname.domain[/email] - where hostname & domain are internal DNS entries known only inside my network.

The syslog entry looks like this;

```
Mar 30 22:04:03 hostname postfix/pickup[21316]: E30DD1603D5: uid=0 from=<root>
Mar 30 22:04:03 hostname postfix/cleanup[21762]: E30DD1603D5: message-id=<20130330120403.E30DD1603D5@hostname>
Mar 30 22:04:03 hostname postfix/qmgr[1767]: E30DD1603D5: from=<root@hostname.domain>, size=481, nrcpt=1 (queue active)
Mar 30 22:04:04 hostname postfix/smtp[21764]: E30DD1603D5: to=<root@hostname.domain>, orig_to=<root>, relay=smtp.isp.com[a.b.c.d]:25, delay=0.88, delays=0.14/0.06/0.36/0.32, dsn=2.0.0, status=sent (250 ok:  Message 100729732 accepted)
Mar 30 22:04:04 hostname postfix/qmgr[1767]: E30DD1603D5: removed

```

So I can see the mail is being forwarded, but instead of being forwarded to my gmail, it's hitting my ISPs SMTP relay with a destination address of [email]root@hostname.domain[/email]. My ISP is obviously unable to resolve that domain, and discards the email.

My question is why is the mail not being forwarded to my gmail address?

Thanks!

---

