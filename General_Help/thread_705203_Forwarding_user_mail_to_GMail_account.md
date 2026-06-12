---
title: "Forwarding user mail to GMail account"
date: 2008-02-23
forum: General Help
---

### Post by SumnerBoy on 2008-02-23
Hi,

I am new to Linux and Ubuntu and have a (probably stupid) question re. user mail. I have Postfix installed and am getting mail generated and delivered to my user mailbox (mainly via crontab etc).

I would like this mail to actually be delivered or forwarded to my personal GMail account - is this possible? If so, how do I go about configuring Postfix etc?

Thanks in advance,
Ben

PS - I am running Ubuntu 7.10 Server Edition - i.e. no GUI bar Webmin.

---

### Post by rapiscan on 2008-02-23
This is a bit documentation intensive, but I think it's what you need:

[http://www.postfix.org/VIRTUAL_README.html](http://www.postfix.org/VIRTUAL_README.html)

Look at the "Postfix virtual ALIAS example" section.

---

### Post by SumnerBoy on 2008-02-23
I had a read of those docs but I am not sure it is doing what I require. I want any mail sent to <user>@<localhost> to be delivered to my personal Gmail account - rather than the local user mailbox.

So when a cron job fails and sends an email to the user, it will actually be forwarded to my gmail inbox - which I check regularly.

I found this...[http://freshmeat.net/articles/view/1673/...which](http://freshmeat.net/articles/view/1673/...which) seems to talk about what I want to acheive but after following the steps defined I am still not getting any mail forwarded to my gmail inbox.

Am I missing something here? I am pretty new to Linux so please be patient! ;-)

---

### Post by rapiscan on 2008-02-24
I'm more familiar with sendmail than I am with postfix and I don't have postfix installed.  I would recommend posting your question in the server section.

---

### Post by SumnerBoy on 2008-02-24
Will do - thanks for the tip!

---

