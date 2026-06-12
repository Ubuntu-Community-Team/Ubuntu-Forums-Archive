---
title: "Can I use my computer login as email"
date: 2007-07-19
forum: General Help
---

### Post by xavier_r on 2007-07-19
Supppose my username in my Feisty Fawn Machine is

xavier
and my domain is
localhost.localdomain

Is there any software, or email shortcut, just like URL shortcut... to send email to 
[email]xavier@localhost.localdomain[/email]

Is it possible?
My IP is dynamic not static...

---

### Post by splintercellguy on 2007-07-19
You'll have to setup a mail server. I'm not particularly familiar with the specifics, though there's a bit of work to do, including creating a reverse DNS entry so incoming/outgoing mail with the rest of the world works. Personally, I'd say sticking to free e-mail would be better.

---

### Post by PaulFr on 2007-07-19
If you want email inside your network, it is a matter of configuring your internal machines to deliver email to your Ubuntu machine. On the other hand, if you want email from any where in the world to land up at your machine, IMHO, there are various points you should consider for running a mail server:
[LIST=1]
[*]Your machine has to be up and connected to the internet to receive mail.
[*]Your machine has to known to the outside world (see **[http://en.wikipedia.org/wiki/DynDNS](http://en.wikipedia.org/wiki/DynDNS)** for one way to achieve this, also see **[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)**).
[*] Your machine has to be known as the mail exchanger for the domain you register in the previous step (see MX records in the DynDNS service descriptions).
[*]Port 25 on your machine has to be reachable from the outside world for mail transfer (using **[http://en.wikipedia.org/wiki/SMTP](http://en.wikipedia.org/wiki/SMTP)** protocol).
[/LIST]
If you are able to do all of this, there are many software packages on Ubuntu that will set up a mail server on your machine (like Postfix, Courier, ...). Hope this helps.

---

### Post by xavier_r on 2007-07-19
> **PaulFr said:**
> If you want email inside your network, it is a matter of configuring your internal machines to deliver email to your Ubuntu machine. On the other hand, if you want email from any where in the world to land up at your machine, IMHO, there are various points you should consider for running a mail server:
[LIST=1]
[*]Your machine has to be up and connected to the internet to receive mail.
[*]Your machine has to known to the outside world (see **[http://en.wikipedia.org/wiki/DynDNS](http://en.wikipedia.org/wiki/DynDNS)** for one way to achieve this, also see **[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)**).
[*] Your machine has to be known as the mail exchanger for the domain you register in the previous step (see MX records in the DynDNS service descriptions).
[*]Port 25 on your machine has to be reachable from the outside world for mail transfer (using **[http://en.wikipedia.org/wiki/SMTP](http://en.wikipedia.org/wiki/SMTP)** protocol).
[/LIST]
If you are able to do all of this, there are many software packages on Ubuntu that will set up a mail server on your machine (like Postfix, Courier, ...). Hope this helps.

Thanks Paul for that info... Especially about that DynDNS, i'm checking that up...

---

### Post by xavier_r on 2007-07-19
Fast question...
[B]
How do i know if my ISP is using a proxy?
[/B]

---

### Post by xavier_r on 2007-07-19
problem solved
I found what my actual IP is...
Now back to topic :)

And some good news too...
There's a static IP hidden under the proxy Dynamic IP...
Wow...

EDIT:
Actually its not a static IP, its another proxy address...
I dont know how many layers of proxy there are... 
I tracerouted and it timed out...
this ISP sucks!!!

---

