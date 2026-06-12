---
title: "Disable IDM in Squid Proxy Ubuntu Server 12.04"
date: 2013-05-27
forum: General Help
---

### Post by ilham4official on 2013-05-27
Hi, I'm new here. Sorry if I'm entered the wrong room.
I want to ask, is it possible to disable download accelerator (such a IDM) in squid?

Thanks.

---

### Post by HiImTye on 2013-05-27
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
you can try making an acl for a specific useragent and use max_conn

---

### Post by ilham4official on 2013-05-30
it didn't work when I try using acl and maxconn. the problem is, I write my rule [COLOR=#000000][FONT=Verdana]before the "deny CONNECT !SSL_Ports. it should be right after that rule right?
so, it was my mistake, sorry.
thanks mate :D

regards.[/FONT][/COLOR]

---

