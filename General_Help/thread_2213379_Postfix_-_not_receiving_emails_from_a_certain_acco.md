---
title: "Postfix - not receiving emails from a certain account/sender"
date: 2014-03-26
forum: General Help
---

### Post by adam43 on 2014-03-26
Hello,

I apologise in advance if I have posted this in the wrong section.
 
I am experiencing an unusual issue whereby my mail server is not accepting emails from a particular account from a certain domain. I.E. we are getting emails through OK from [EMAIL="payments@example.com"]payments@example.com[/EMAIL] but not from [EMAIL="info@example.com"]info@example.com[/EMAIL]. These emails are coming from a financial company so it may be possible that the emails from different accounts are coming from a range of different sending servers? 
 
The steps I have taken so far:
 
  
[LIST]
[*]I have confirmed the sending server IP address – I cannot see any instances of this IP in any of the mail-postfix* logs nor the postscreen log or Firewall log.
[*]I have ensured that the IP is not listed on the Blacklists that this mail server is following (Invaluement, Spamhaus)
[*]The sender has provided me with a snippet of their mail log and what they are seeing at the time of the connection:
[/LIST]
 
> sendmail.log.0:Jun 28 13:22:45 mailserver sendmail[15824]: [ID 801593 mail.info] r5R9BSU2021287: to=<[EMAIL="accounts@adeptgroup.org"]example.com[/EMAIL]>, delay=1+03:11:17, xdelay=00:05:00, mailer=esmtp, pri=7590623, relay=example-relay [176.31.241.80], dsn=4.0.0, stat=Deferred: Connection timed out with example.com.
 
sendmail.log.0:Jun 28 13:23:00 mailserver sendmail[15824]: [ID 801593 mail.info] r5R7jL4I003663: to=<example.com>, delay=1+04:37:39, xdelay=00:00:05, mailer=esmtp, pri=7680615, relay=mailhost.internet....ise.sending-company.co.uk, dsn=4.0.0, stat=Deferred

This is a more recent example they were able to provide:

> Feb  7 03:12:28 zzz  sendmail[8031]: [ID 801593 mail.notice] s15EWeZE024810: timeout waiting for input from a.example.com. during client greeting
.
Feb  7 03:13:02 zzz  sendmail[25470]: [ID 801593 mail.info] s152J1Sb018752: to=<[EMAIL="breege@barrettsconcrete.com"]a[/EMAIL]ccount@example.com>, delay=2+00:54:01, xdelay=00:20:00, mailer=es
mtp, pri=8580619, relay=My relay. [77.107.230.22], dsn=4.0.0, stat=Deferred: Connection timed out with a.example.com.
 
 
They also attempted a telnet session
 
> telnet 91.xx.xx.xx
Trying 91.xx.xx.xx
Connected to 91.xx.xx.xx
Escape character is '^]'.
ehlo A
Connection to 91.xx.xx.xx closed by foreign host.
 
As well as this, they have provided me with a packet capture session, which shows my mail server not accepting packet 3. (See attached)

Is there any way to confirm if this issue is on the sending side? If they send the email to my gmail it arrives fine.

If there is an issue with my mail server can anyone advise what i should be looking for?
 
Right now I am unable to provide the Postfix config's.

Any input would be greatly appreciated. 


Thanks
Adam

---

### Post by SeijiSensei on 2014-03-26
What do your logs report for those messages?  Are you using a virus scanner?  SpamAssassin?

---

### Post by adam43 on 2014-03-26
Hi,

Unfortunately the logs are only kept for 30 days so I cannot confirm, however I don't recall seeing any entries in our logs at the time. I still have the logs from the packet capture (telnet) session that took place, although again, there is nothing in our postfix/postscreen/firewall logs from this sender.

Yes, we are using Spam Assassin as well as Clam-AV, DSpam and F-Secure.

Thanks

---

### Post by SeijiSensei on 2014-03-27
> **adam43 said:**
> Unfortunately the logs are only kept for 30 days so I cannot confirm
Perhaps you could ask them to send you another test message so you can see what happens in the logs.

> Yes, we are using Spam Assassin as well as Clam-AV, DSpam and F-Secure.
And these messages are not quarantined, I presume?

No offense; just trying to eliminate the obvious.

---

