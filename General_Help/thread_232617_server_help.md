---
title: "server help"
date: 2006-08-09
forum: General Help
---

### Post by firehazard17 on 2006-08-09
Ive installed the server edition of ubuntu with lamp. Apache starts fine. So what im asking is how do i host my website and i would like to use shh to remotely control it and i would like to not have to type in an ip adress so how do you register a domain name

---

### Post by scxtt on 2006-08-09
assuming you installed apache2, you can host files from the /var/www directory, so when a user enters your IP address they're served up your files located in /var/www ... you just need to make sure that if you're behind a router, that you forward port 80 (by default, unless you change it in apache2.conf) to the IP of the box you're hosting files from ...

as for registering a domain name, i'm sure there's more than a handful of them out there ... i've only bought 1 domain a few years ago and i simply just had to forward the domain i purchased to where my site was hosted @ the time (not my own box, but i was using tripod back then - it was a long time ago) ... i'm sure you'll get varied opinions on which site is best, but check out [http://www.register.com](http://www.register.com) as a start ...

as for remote managing your own server, that should be exceedingly easy using openssh-server ...

---

### Post by noof on 2006-08-09
If you have dynamic internet ip you can use [http://www.dyndns.com](http://www.dyndns.com) . You can get a xxxx.mine.nu/dyndnds.org/... for free.

---

