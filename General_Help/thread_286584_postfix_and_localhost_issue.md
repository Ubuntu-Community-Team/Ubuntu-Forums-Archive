---
title: "postfix and localhost issue"
date: 2006-10-27
forum: General Help
---

### Post by ryjac on 2006-10-27
I installed postfix and the following test works fine.

$telnet localhost 25 < mail_test

where mail_test contains the following:
> ehlo localhost
mail from: root@mybox
rcpt to: fmaster@mybox
data
Subject: testing email script
testing an email scripted used via telnet
.
quit


everything gets sent to the recipient without any problems.

however, when i launch mutt and attempt to send an email, i get the following.

> Oct 28 22:35:01 mybox postfix/cleanup[8963]: 95BAF1426D: message-id=<20061028023501.GA8945@mybox>
Oct 27 22:35:01 mybox postfix/qmgr[6179]: 95BAF1426D: from=<root@mybox**.home**>, size=428, nrcpt=1 (queue active)
Oct 27 22:35:01 mybox postfix/smtp[8965]: 95BAF1426D: to=<fmaster@mybox**.home**>, orig_to=<fmaster>, relay=none, delay=0, status=bounced (Host or domain name not found. Name service error for name=mybox.home type=A: Host not found)

I believe the problem is that it attaches a .home to my hostname. 

I haven't been able to find where configuration with the .home is located. I remember attaching a .home at one point when configuring postfix using postconf -e, but i've changed it back since. (in /etc/postfix/mail.cf)

If anyone can point me to any other places where it could hold the hostname value, I'd very much appreciate it.

---

### Post by ryjac on 2006-10-28
I found the config file that had mybox.com

it was located in /etc/mailname

i changed it from mybox.com to just mybox and local mail sending works properly now.

---

