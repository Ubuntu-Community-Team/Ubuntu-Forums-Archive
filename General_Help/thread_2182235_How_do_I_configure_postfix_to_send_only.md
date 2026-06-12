---
title: "How do I configure postfix to send only?"
date: 2013-10-20
forum: General Help
---

### Post by sgharp on 2013-10-20
Hi,

I've been trying for hours to get postfix to work.  Xubuntu v12.10 and postfix v2.9.6.  I'm trying to get it configured to send only and only 
from localhost.  I've been working with the main.cf and examples on postfix.org for a null client.
[INDENT] 1 /etc/postfix/[main.cf]("http://www.postfix.org/postconf.5.html"):
2     [myhostname]("http://www.postfix.org/postconf.5.html#myhostname") = hostname.example.com
3     [myorigin]("http://www.postfix.org/postconf.5.html#myorigin") = $[mydomain]("http://www.postfix.org/postconf.5.html#mydomain")
4     [relayhost]("http://www.postfix.org/postconf.5.html#relayhost") = $[mydomain]("http://www.postfix.org/postconf.5.html#mydomain")
5     [inet_interfaces]("http://www.postfix.org/postconf.5.html#inet_interfaces") = loopback-only
6     [mydestination]("http://www.postfix.org/postconf.5.html#mydestination") =

[/INDENT]
This doesn't work.  I can telnet to port 25 and send an email message.  It says that the message is being queued but nothing shows up in the 
queue.  The error I get in /var/log/mail.log is "(delivery temporarily suspended: connect to mydomain.com[x.x.x.x]:25: Connection refused)".

Any ideas?
[INDENT]  

[/INDENT]

---

### Post by Habitual on 2013-10-20
did you restart the postfix service/daemon after making said changes?

---

### Post by smtp on 2013-10-21
You have to change hostname.example.com with your real fully-qualified domain name.

---

