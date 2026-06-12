---
title: "/etc/hosts wildcard (127.0.0.1 *.mydomain.com)"
date: 2007-05-09
forum: General Help
---

### Post by NuPagady on 2007-05-09
Hello,

I recently installed xubuntu on a laptop which I will be using for php development. I installed PHP5, MySQL5, webserver and other services I need. To make things easier, I added the following lines to my /etc/hosts file:

127.0.0.1 [www.mydomain.com](www.mydomain.com)
127.0.0.1 mydomain.com

So I can easily test my scripts by simply browsing webpage which is being developed on my laptop.

However, the project I'm working all will be using many subdomains, i.e. user.mydomain.com. So I need a working wildcard, something like *.mydomain.com. I tried adding:

127.0.0.1 *.mydomain.com

But it didn't work. How do I make this work?


Thanks
- Paul

---

### Post by Stephen Howard on 2007-05-09
Maybe resolv.conf?  I'm not sure if it would work for you, but I think it can be used for searching domain names based on the number of '.'s in a defined url.

---

### Post by Aleksandersen on 2008-01-24
You cannot use a wildcard in this config file. Which is a shame, really.

---

### Post by #Reistlehr- on 2008-02-11
honsetly, the best bet for this would be to set up virtual hosts for each project and assign a dns zone to each. Then all you have to do after the DNS server has forward and reverse is add your ipaddress to resolv.conf

---

