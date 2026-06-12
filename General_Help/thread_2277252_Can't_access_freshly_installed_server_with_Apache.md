---
title: "Can't access freshly installed server with Apache"
date: 2015-05-07
forum: General Help
---

### Post by jamie-2 on 2015-05-07
I've never seen this before. But I have a brand new server running Ubuntu 12.04 and have just installed apache with:
> 
sudo apt-get update
sudo apt-get install apache2

I have also turned off ufw, so I'm a little confused as to why I can't access directly. 

I'm pretty sure this is an awful question but I'd appricaite any help guys.

Thanks

[http://109.228.16.158/](http://109.228.16.158/)

---

### Post by jamie-2 on 2015-05-07
iptables [FONT=Consolas]-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT

So of course it was Iptables wasn't it.... :O[/FONT]

---

