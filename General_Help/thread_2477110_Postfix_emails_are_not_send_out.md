---
title: "Postfix emails are not send out"
date: 2022-07-14
forum: General Help
---

### Post by tonysar on 2022-07-14
Hello. 
I have ubuntu VPS running Webserver and Postfix . I have magento 2 installed and running. I have found Issue with postfix that I can not wrap my head around. All website transactional emails being delivered to local mailbox on the server. But I want them to be routed to 
mailbox outside of my domain . 
Email Address for my domain have been created on different server. mails to these email addresses being delivered to local mail box on my postfix .how can i redirect my transactional emails outside of my postfix and not local folder. 
Thanks.

---

### Post by TheFu on 2022-07-15
do you have a relay host configured?
what email addresses are being used?  If they go to the localhost, then you'll want to setup /etc/aliases in the standard way to forward email from each account to a real domain.
If the other host, is over the internet, you'll need to know what the VPS may require for sending external email. In theory, it shouldn't need anything, but if you are reusing an email domain/IP from a prior spammer, it is probably on every DBL and nobody will accept email from that IP.  You can spend time trying to get those old records fixed at every block list or just get a new IP from the VPS. Check every IP for inclusion on block lists immediately.

Of course, of the VPS is friendly towards spammers, their entire network may be blocked at some locations.  I block over 8000 subnets these days and those aren't checked against any blocklists.

Reputable VPS fine their customers $5 per spam incident, so they have a real reason to deal with any spam from their systems, quickly.

---

### Post by SeijiSensei on 2022-07-16
Run a test manually.

Choose a message that has not been sent out, then determine the "MX" host for that domain with the command
```
host -t mx domain.name
```
You will see the host(s) that accept mail for that domain.

Next, choose one of those servers, then open a terminal and run the command
```
telnet server.domain.name 25
```

You'll see right away whether you can connect to the server and send a message.

---

