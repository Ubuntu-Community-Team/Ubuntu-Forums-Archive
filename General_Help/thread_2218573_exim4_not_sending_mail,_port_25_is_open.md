---
title: "exim4 not sending mail, port 25 is open"
date: 2014-04-21
forum: General Help
---

### Post by nick103 on 2014-04-21
I've been trying to get this to work for the past 4 hours to no avail. I have ajenti installed as control panel and running exim4 with courier-imap as my mail system. IMAP works fine. SMTP is a no-go. My mail logs tell me the following:

```
2014-04-21 13:25:04 1WcB1Q-0002we-Jb gmail-smtp-in.l.google.com [74.125.136.27] Connection timed out
2014-04-21 13:25:04 1WcB1Q-0002we-Jb alt1.gmail-smtp-in.l.google.com [2a00:1450:4008:c01::1a] Network is unreachable
2014-04-21 13:27:11 1WcB1Q-0002we-Jb alt1.gmail-smtp-in.l.google.com [173.194.69.26] Connection timed out
2014-04-21 13:27:11 1WcB1Q-0002we-Jb alt2.gmail-smtp-in.l.google.com [2a00:1450:4010:c04::1a] Network is unreachable
2014-04-21 13:27:11 1WcB1Q-0002we-Jb alt3.gmail-smtp-in.l.google.com [2607:f8b0:400e:c03::1b] Network is unreachable
2014-04-21 13:27:11 1WcB1Q-0002we-Jb alt4.gmail-smtp-in.l.google.com [2607:f8b0:4003:c02::1b] Network is unreachable
2014-04-21 13:27:11 1WcB1Q-0002we-Jb == myemail@gmail.com R=dnslookup T=remote_smtp defer (101): Network is unreachable

```

A similar time out happens to mx2.hotmail.com.

I also tried this:
```
$ tcptraceroute gmail-smtp-in.l.google.com 25
Selected device eth0, address 192.168.1.125, port 33023 for outgoing packets
Tracing the path to gmail-smtp-in.l.google.com (74.125.136.26) on TCP port 25 (smtp), 30 hops max
 1  192.168.1.1  0.499 ms  0.605 ms  0.619 ms

```
After the first hop it times out.

All networking tools tell me that port 25 is open and responding. I can easily telnet into my mail server. My ISP also told me that port 25 is open. I have no idea what else I can do.

---

### Post by TheFu on 2014-04-21
I'd check your IPv6 settings and DNS settings.

---

### Post by nick103 on 2014-04-21
and look for what?

---

### Post by TheFu on 2014-04-21
> **nick103 said:**
> and look for what?

The reasons that connections time out and the network is unreachable. This isn't just an email issue. It is networking and most likely to be routing or DNS settings.  I'm leaning towards routing.

---

### Post by nick103 on 2014-04-21
I think so too now. I just did a complete clean install of ubuntu server 12.04 and installed zpanel. On an actual server where i'm running the exact setup the email worked out of the box with no extra config. Now i still can't send mail. I can receive though. I tried multiple tools to check if port 25 is open and it *is* in fact open so i'm clueluess what could be wrong. Any tests i can perform?

---

### Post by TheFu on 2014-04-21
route
dig

---

