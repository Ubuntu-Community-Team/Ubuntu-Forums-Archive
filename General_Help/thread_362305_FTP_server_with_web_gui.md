---
title: "FTP server with web gui"
date: 2007-02-15
forum: General Help
---

### Post by brian873 on 2007-02-15
Hi,

Can any one point me in the direction of setting up an ubutu ftp server that has a web gui so non technical staff can create users ?

Thanks

brian

---

### Post by stalker145 on 2007-02-15
You could always toss [WebMin]("http://www.webmin.com/") on your server. It does a lot more than create FTP users and it takes a few minutes to figure out how to use it initially, but overall is very usable (to me, anyway).

---

### Post by punx45 on 2007-02-15
do you really want non-technical staff performing administrative tasks on your system?

---

### Post by brian873 on 2007-02-16
Thanks Stalker, it has been a while since I last used webmin.  I forgot all about it.  I was not stuck on it last time but maybe the new version will be better.

I would like a dedicated web gui just for FTP but if I cannot get that I think webmin will be the way forward.

punx45; yes as stated in the first post it is a requirement unfortunately.

---

### Post by stalker145 on 2007-02-16
> **brian873 said:**
> I would like a dedicated web gui just for FTP...

Since I'm on a single-user setup for my server I don't quite know for sure, but I do believe that you can adjust permissions within Webmin to only allow users into certain modules. For instance restricting FTP admin #1 to ONLY the FTP server by deselecting everything else. 

In fact, I think I'll tinker with that for a bit. I'll get back with you if it's something that interests...

OK, two minutes later it works out pretty well. All you have to do is:
```
1) Go into Webmin users
2) Create a new group with limited access
3) Create a user and assign to the limited group
4) ????
5) Profit
```

It's actually easier than I thought. It took me longer to type the process out than to do it.

---

### Post by brian873 on 2007-02-16
Thanks again Stalker I will try and get something set-up over the next couple of days this information looks top be very useful.

Thanks

---

