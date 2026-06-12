---
title: "thunderbird send messages"
date: 2013-01-19
forum: General Help
---

### Post by rnerwein on 2013-01-19
hi folks
sorry if my english isn't so good - i am a german
i got a little problem with email thunderbird ( i think it's between my ears )
i set up thunderbird to connect my primaray mail-server via imap. receiving works perfect (including notification ....). but when i want to send a mail i stuck in: loading up into folder ( hope it's nearly correct translated). 
my question is - is there a special point in the configuration for sending messages.
again - receiving everthing is ok :confused:
thanks for an hint
richi

---

### Post by sudodus on 2013-01-19
Look at

Edit -- Account settings

At the bottom of the left column:
Outgoing server

Most internet service providers (ISPs) do not allow you to use any other service for sending mail than their own. So you need to find out what is the SMTP settings for your ISP and apply that in the settings of T-bird.

Good luck :-)

---

### Post by rnerwein on 2013-01-19
> **sudodus said:**
> Look at

Edit -- Account settings

At the bottom of the left column:
Outgoing server

Most internet service providers (ISPs) do not allow you to use any other service for sending mail than their own. So you need to find out what is the SMTP settings for your ISP and apply that in the settings of T-bird.

Good luck :-)
hi
thanks for your answer but the problem is gone from alone. on my box i have all the time the message: status: store bla bla in Sent. 
but about 20 minutes later i looked into my mail-box on my provider side. heurika my testmail was still there. for me it looks like that Thunderb sends the mail but got no handshake from my provider. now i know it works but the system won't tell (egal).
ciao ;)
richi

---

### Post by sudodus on 2013-01-19
> **rnerwein said:**
> hi
thanks for your answer but the problem is gone from alone. on my box i have all the time the message: status: store bla bla in Sent. 
but about 20 minutes later i looked into my mail-box on my provider side. heurika my testmail was still there. for me it looks like that Thunderb sends the mail but got no handshake from my provider. now i know it works but the system won't tell (egal).
ciao ;)
richi
I'm glad it works now. Maybe the system was busy syncing, and was not ready until after those 20 minutes, because there were a lot of mails to take in account this first time.

---

