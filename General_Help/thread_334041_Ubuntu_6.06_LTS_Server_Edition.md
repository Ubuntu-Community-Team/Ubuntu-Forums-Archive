---
title: "Ubuntu 6.06 LTS Server Edition"
date: 2007-01-08
forum: General Help
---

### Post by mistypotato on 2007-01-08
[SIZE="3"]Hello,

I'm currently running 6.10 Ubuntu and was wondering if I could "upgrade" the version to Server or does it requires a complete re-install to go with the server edition?

Thanks[/SIZE]

---

### Post by tito2502 on 2007-01-08
Just grab the apache packages from apt.

---

### Post by az on 2007-01-08
What kind of server?  Not that it matters, you just need to install the packages you want to run.  The Desktop packages do not interfere with the LAMP server packages (and vice versa)

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by mistypotato on 2007-01-08
Apache, ColdFusion, PHP, and MySQL

Problem is...

Coldfusion only works with apache 1.3.xx

---

### Post by az on 2007-01-08
> **mistypotato said:**
> Apache, ColdFusion, PHP, and MySQL

Problem is...

Coldfusion only works with apache 1.3.xx

From:[http://livedocs.macromedia.com/coldfusion/5.0/Installing_and_Configuring_ColdFusion_Server/lininstall2.htm#1177493](http://livedocs.macromedia.com/coldfusion/5.0/Installing_and_Configuring_ColdFusion_Server/lininstall2.htm#1177493)

ColdFusion Server provides a precompiled module that is binary compatible with versions 1.3.6 through 1.3.19.


Is that version of apache 1.3 still secure to use?

The version in the repos is 1.3.33
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=apache](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=apache)

---

### Post by mistypotato on 2007-01-08
i SHOULD have said...

The version of Coldfusion Server that I have (4.5) only works with Apache 1.3.xx

Secure?

Well, I've been running it on a Windows Box (plain Home edition, not even Professional), for quite a while and allthough there have been many hack attempts, none succeeded.....yet.

I would think that just having it on a Linux server would make it "more" secure?

How hard is it for a Linux ubuntu server to be hacked into.
The worst thing would be if the MySQL databases were compromised.

---

