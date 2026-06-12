---
title: "question on ftp access mysterious"
date: 2008-05-08
forum: General Help
---

### Post by syrgak on 2008-05-08
Hi, folk. I'm new in english & Ubuntu (and common *nix systems), so excuse me for broken english & dummie's questions.
Yerterday I've installed ProFTPD server according to [this]("http://www.debuntu.org/how-to-ftp-virtual-host-with-proftpd-mysql-p2") step by step tutorial.
As the result i've achieved get ftp access to /var/proftpd directory ... but some strange behavior was find out - although home directory accords to /var/proftpd/firstuser but actually i've access to directory up and whole file system. What's was wrong? I just follow "how to" instructions.
Any help is appreciated, tnx :)

---

### Post by garyedwardjohnston on 2008-05-08
Why not just use XAMPP?

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by syrgak on 2008-05-09
> **garyedwardjohnston said:**
> Why not just use XAMPP?

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

XAMMP is not solution in our case. I can't make out why ftpuser, which has permissions only to /var/proftpd/firstuser directory(i've check out this by :/var/proftpd$ ls -l) Can ACCESS to other(All!) directories via ftp???

---

