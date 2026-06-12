---
title: "Can receive mail but not send"
date: 2013-07-15
forum: General Help
---

### Post by caleb12134 on 2013-07-15
We use Zpanel. Here is the error we get. We can get mail just not send. thanks!


[COLOR=#333333][FONT=Lucida Grande]
This is the mail system at host control.yourdomain.com.##################################################################### THIS IS A WARNING ONLY.  YOU DO NOT NEED TO RESEND YOUR MESSAGE. #####################################################################Your message could not be delivered for more than 4 hour(s).It will be retried until it is 5 day(s) old.For further assistance, please send mail to postmaster.If you do so, please include this problem report. You candelete your own text from the attached returned message.                   The mail system<[REMOVED]>: connect to    alt2.gmail-smtp-in.l.google.com[173.194.65.26]:25: Connection timed out

Reporting-MTA: dns; control.yourdomain.comX-Postfix-Queue-ID: 913E0642425X-Postfix-Sender: rfc822; [REMOVED]Arrival-Date: Fri, 12 Jul 2013 14:51:31 -0400 (EDT)Final-Recipient: rfc822; [REMOVED]Original-Recipient: rfc822;[REMOVED]Action: delayedStatus: 4.4.1Diagnostic-Code: X-Postfix; connect to    alt2.gmail-smtp-in.l.google.com[173.194.65.26]:25: Connection timed outWill-Retry-Until: Wed, 17 Jul 2013 14:51:31 -0400 (EDT)

Return-Path: <[REMOVED]>Received: from 192.168.1.3 (localhost [127.0.0.1])    by control.yourdomain.com (Postfix) with ESMTPA id 913E0642425    for <[REMOVED]>; Fri, 12 Jul 2013 14:51:31 -0400 (EDT)MIME-Version: 1.0Content-Type: multipart/alternative; boundary="=_a46847dd2d2d928429962aa8dc9f6301"Date: Fri, 12 Jul 2013 14:51:31 -0400From: [REMOVED]To: <[REMOVED]>Subject: [REMOVED]Message-ID: <[REMOVED]>X-Sender: [REMOVED]User-Agent: Roundcube Webmail/0.8.1



[/FONT][/COLOR]

---

### Post by sanderj on 2013-07-15
what happens if you open a terminal on your mail system, and type:

```
telnet alt2.gmail-smtp-in.l.google.com smtp
```

Post the output here

---

### Post by caleb12134 on 2013-07-15
i get this

caleb1@ubuntu:~$ telnet alt2.gmail-smtp-in.l.google.com smtp
Trying 173.194.65.26...
Trying 2a00:1450:4013:c00::1a...
telnet: Unable to connect to remote host: Network is unreachable
caleb1@ubuntu:~$

---

### Post by sanderj on 2013-07-15
I see. Could be an IPv6 problem, or it could a firewall blocking port 25. Let's find out:

What's the output of:

```
telnet smtp.telfort.nl smtp
```

Post the output here.

---

### Post by caleb12134 on 2013-07-15
i got this

caleb1@ubuntu:~$ telnet smtp.telfort.nl smtp
Trying 213.75.63.9...
telnet: Unable to connect to remote host: Connection timed out
caleb1@ubuntu:~$

---

### Post by sanderj on 2013-07-16
OK, clear: you're not allowed to do outbound SMTP sessions. Possible reasons:
- there is a firewall on your LAN or WAN blocking it. Check with yourself or your admin
- your ISP is blocking it. If so, your ISP usually provides SMTP-smart-host

HTH

---

### Post by efflandt on 2013-07-16
Most likely your ISP is blocking outgoing port 25 (smtp) other than to their own relays, or they might use a different port with authentication for secure mail. That is to avoid spreading worms, viruses, or spam trojans that contain their own smtp server.

Many mail servers do not accept mail directly from what they perceive as dynamic IP addresses, but you have not gotten that far because your port 25 appears to be blocked.

In any case you likely need to relay any outgoing mail through your ISP's relays (smart-host), whatever you would typically configure for an smtp client program for your ISP.

---

### Post by caleb12134 on 2013-07-18
Ok. They are blocking it so in the zpanel config I changed the port for smtp to 587. It still doesnt work?

---

### Post by sanderj on 2013-07-19
> **caleb12134 said:**
> Ok. They are blocking it so in the zpanel config I changed the port for smtp to 587. It still doesnt work?

Why have you changed it to port 587?
Do you information that alt2.gmail-smtp-in.l.google.com listens on port 587?

What have you done with my SMTP-smart-host information?

---

### Post by caleb12134 on 2013-07-20
iI don't know what smtp-smart-host info is? :)

---

