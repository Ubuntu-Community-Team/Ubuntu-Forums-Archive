---
title: "How to set the Squid and SquidGuard."
date: 2006-10-30
forum: General Help
---

### Post by sshgz on 2006-10-30
I have installed ubuntu 6.10 with squid and squidguard. I want to filter some websites and set the squid and squidguard, but i found that i could not filter these websites.

I am waiting for your help.

Thanks.

---

### Post by hartunnoo on 2006-10-30
hmm... ok try this.

sudo /etc/squid/squid.conf
then paste this 

> 
acl xxx url_regex -i sex playboy xxx
http_access deny xxx

or if you want to block the whole URL then use this

> acl testing url_regex [-i] [http://www.testing.com](http://www.testing.com)
http_access deny testing

hope this will help you.

---

### Post by sshgz on 2006-10-31
Thanks hartunnoo.

I have set "http_access deny all" , but i could see all the sites on the ubuntu server.
If i use the ubuntu server as proxy server then i could not see the sites on the client PC.

---

### Post by Swab on 2006-10-31
> **sshgz said:**
> Thanks hartunnoo.

I have set "http_access deny all" , but i could see all the sites on the ubuntu server.
If i use the ubuntu server as proxy server then i could not see the sites on the client PC.

"http_access deny all" will deny anyone from accessing squid, what you want to do is allow people to access, but redirect them to squidguard...

maybe [https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard) will help

---

