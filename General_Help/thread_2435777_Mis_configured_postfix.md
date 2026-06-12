---
title: "Mis configured postfix"
date: 2020-01-25
forum: General Help
---

### Post by cearlp on 2020-01-25
Installed & configured Postfix according to online directions after looking at several examples. All seemed straight forward and similar,
When I run a program that uses the php mail function I can't connect to the mail server.
Does the following excerpt from the mail.log file point to a wrongly configured Postfix?

Jan 25 14:48:14 dv7 postfix/qmgr[3841]: B2EEEFA0D03: from=<www-data@dv7.com>, size=499, nrcpt=1 (queue active)
Jan 25 14:48:14 dv7 postfix/qmgr[3841]: B9067FA28BA: from=<www-data@dv7.com>, size=514, nrcpt=1 (queue active)
Jan 25 14:48:14 dv7 postfix/smtp[24633]: connect to gmail-smtp-in.l.google.com[2607:f8b0:4001:c0f::1a]:25: Network is unreachable
Jan 25 14:48:14 dv7 postfix/smtp[24672]: connect to gmail-smtp-in.l.google.com[2607:f8b0:4001:c0f::1a]:25: Network is unreachable
Jan 25 14:48:44 dv7 postfix/smtp[24633]: connect to gmail-smtp-in.l.google.com[173.194.194.27]:25: Connection timed out
Jan 25 14:48:44 dv7 postfix/smtp[24672]: connect to gmail-smtp-in.l.google.com[173.194.194.27]:25: Connection timed out
Jan 25 14:49:14 dv7 postfix/smtp[24633]: connect to alt1.gmail-smtp-in.l.google.com[173.194.77.26]:25: Connection timed out
Jan 25 14:49:14 dv7 postfix/smtp[24633]: connect to alt1.gmail-smtp-in.l.google.com[2607:f8b0:4023:401::1b]:25: Network is unreachable
Jan 25 14:49:14 dv7 postfix/smtp[24633]: connect to alt2.gmail-smtp-in.l.google.com[2607:f8b0:4002:c08::1b]:25: Network is unreachable
Jan 25 14:49:14 dv7 postfix/smtp[24672]: connect to alt1.gmail-smtp-in.l.google.com[173.194.77.26]:25: Connection timed out
Jan 25 14:49:14 dv7 postfix/smtp[24672]: connect to alt1.gmail-smtp-in.l.google.com[2607:f8b0:4023:401::1b]:25: Network is unreachable
Jan 25 14:49:14 dv7 postfix/smtp[24672]: connect to alt2.gmail-smtp-in.l.google.com[2607:f8b0:4002:c08::1b]:25: Network is unreachable
Jan 25 14:49:14 dv7 postfix/smtp[24633]: B2EEEFA0D03: to=<eporter1955@gmail.com>, relay=none, delay=15292, delays=15232/0.02/60/0, dsn=4.4.1, status=deferred (connect to alt2.gmail-smtp-in.l.google.com[2607:f8b0:4002:c08::1b]:25: Network is unreachable)
Jan 25 14:49:14 dv7 postfix/smtp[24672]: B9067FA28BA: to=<eporter1955@gmail.com>, relay=none, delay=11239, delays=11179/0.01/60/0, dsn=4.4.1, status=deferred (connect to alt2.gmail-smtp-in.l.google.com[2607:f8b0:4002:c08::1b]:25: Network is unreachable)

---

### Post by TheFu on 2020-01-26
Does IPv4 work?

---

### Post by cearlp2 on 2020-01-26
I can send and receive data on the ubuntu 18.04 machine. I guess the indicates iPv4 works.
What exactly tests IPv4?

---

### Post by TheFu on 2020-01-26
> **cearlp2 said:**
> I can send and receive data on the ubuntu 18.04 machine. I guess the indicates iPv4 works.
What exactly tests IPv4?

Which protocols are working and from where?  Some simple network troubleshooting steps:
[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)  
It looks like DNS is working at some level.

The SMTP doesn't appear to work based on the logs and it also seems IPv6 is prioritized over IPv4.  If only SMTP isn't working, that could mean the ISP is blocking outbound 25/tcp, which is common. ISPs do that to prevent spam on their networks.  If the connection is residential, then you'll need to use the ISP's relay. There's 1 line in one of the postfix config files that's needed. In the main.cf for postfix, modify or add:
```
relayhost = {put ISP relay IP here.}
```
Check that file with **postconf -n** to see what options are actually being uses.  If you need specific relays for different target email domains, there's a *transport_custom* file available. 

If it is a business connection, probably just need to call the support line and get outbound SMTP opened for your static IP.  If you don't have a static IP, it is likely that nobody will accept email, so just use the ISP's SMTP relay.

---

### Post by SeijiSensei on 2020-01-26
Most likely your ISP is blocking outbound connections to port 25 on remote servers. That's the port used to send mail via SMTP. Many ISPs block port 25 connections to thwart spambots running on their customers' machines. You need to check with your ISP to see if they block port 25.

---

### Post by cearlp2 on 2020-01-27
I've changed the Postfix configuration to also use port 587 but that changed nothing. My ISP (Comcast) said they have no relay IP. 
How do I prioritize IPv4 over IPv6?

---

### Post by TheFu on 2020-01-27
> **cearlp2 said:**
> I've changed the Postfix configuration to also use port 587 but that changed nothing. My ISP (Comcast) said they have no relay IP. 
How do I prioritize IPv4 over IPv6?

Comcast business or residential? It matters for email.

---

### Post by kevdog on 2020-01-28
Hey what are you trying to accomplish?  Is this postfix server just for you or are you going to be sending a lot of mail for it?  For personal use I usually need to forward my postfix through gmail since my internet provider doesn't allow port 25.

---

### Post by SeijiSensei on 2020-01-28
Port 25 is blocked for Comcast residential subscribers. DK about 587.

---

### Post by kevdog on 2020-01-29
I'm a comcast subscriber and port 465 and 587 are not blocked by Comcast.  In some situations I use 465 and others I use 587 -- seems most of the time 465 works better.  I've read the difference between the two protocols - SMTPS (465) vs msa (587) and to be honest I don't really understand the difference between the two scenarios other than the time encryption of the payload starts.  With 465 it seems to start encryption at the time of authentication and with 587 its after transmission of the STARTTLS command.  I really have no idea why you would prefer one over the other.

---

