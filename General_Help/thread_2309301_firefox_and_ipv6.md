---
title: "firefox and ipv6"
date: 2016-01-09
forum: General Help
---

### Post by Skaperen on 2016-01-09
when i visit a web site that is ipv6-only it works fine.  when i visit a web site that has both ipv6 and ipv4 addresses i get the ipv4 site.  i want ipv6 to be preferred.  anyone know where to set this?

---

### Post by QDR06VV9 on 2016-01-09
It's the standard to prioritize IPv6 over IPv4 to allow next-generation IP take over :)
You can change this by editing the precedence blocks in /etc/gai.conf (gai stands for getaddrinfo, the standard system call for resolving host names). Just comment out the line as described in the file:
> #For sites which prefer IPv4 connections change the last line to
precedence ::ffff:0:0/96 100
...
#    For sites which use site-local IPv4 addresses behind NAT there is
#    the problem that even if IPv4 addresses are preferred they do not
#    have the same scope and are therefore not sorted first.  To change
#    this use only these rules:
#
scopev4 ::ffff:169.254.0.0/112  2
scopev4 ::ffff:127.0.0.0/104    2
scopev4 ::ffff:0.0.0.0/96       14
So your server will try first ipv4 even if you are Natted!
More info here: [URL="https://wiki.ubuntu.com/IPv6"]https://wiki.ubuntu.com/IPv6
&&
 [http://askubuntu.com/questions/9181/how-to-let-the-browser-prefer-ipv6-over-ipv4](http://askubuntu.com/questions/9181/how-to-let-the-browser-prefer-ipv6-over-ipv4)


[/URL]

---

