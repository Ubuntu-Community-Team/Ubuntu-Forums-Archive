---
title: "bind9 - custom dns records"
date: 2018-07-02
forum: General Help
---

### Post by marchello_lippi2 on 2018-07-02
Hi all, 
I got bind9 server and it works fine. 
Now I would like to add my custom dns records so that some hosts will not be resolved at all. 
For example, I would like some host like annoying-advertiser.com to be pointed to 127.0.0.1 so that I do not see its banners ever. 
I know I can use /etc/hosts on my local computer, but this is about android devices in my local network that use my local dns server. 
I tried to use /etc/hosts on dns server computer, but bind9 seems does not consider it. 
Please advise.

---

### Post by nlee2 on 2018-07-02
If you are running  Bind 9.8.1 or newer then try response policy zone to override CNAME.

---

### Post by marchello_lippi2 on 2018-07-02
> **nlee2 said:**
> If you are running  Bind 9.8.1 or newer then try response policy zone to override CNAME.
Thx, I got BIND 9.8.4 so your hint should work for me. 
Checking out response policy zone, if someone has hint for quick start, please advise.

---

### Post by nlee2 on 2018-07-02
[https://serverfault.com/questions/18748/overriding-some-dns-entries-in-bind-for-internal-networks](https://serverfault.com/questions/18748/overriding-some-dns-entries-in-bind-for-internal-networks)

---

