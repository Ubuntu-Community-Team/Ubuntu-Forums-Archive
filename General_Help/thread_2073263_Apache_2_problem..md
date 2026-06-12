---
title: "Apache 2 problem."
date: 2012-10-19
forum: General Help
---

### Post by kutalion on 2012-10-19
Hello,

It seems that I have particular apache2 problem. As far as I understand the only problem is that I face in running apache is that it can't connect to any port that I give to it. I prefer to use :80 so i keep this in my configuration. As I run service apache2 start I get (among multiple errors NameVirtualHost *:80 has no VirtualHost)
```
(98)Address already in use: make_sock: could not bind to address [::]:80.
```

in netstat there is NOTHING using that particular port so it is definitely NOT in use. Is apache2 gone crazy?
Netstat -plant shows only two ports in use :22 and :53 nothing else!

Can someone help a bit in here?

---

