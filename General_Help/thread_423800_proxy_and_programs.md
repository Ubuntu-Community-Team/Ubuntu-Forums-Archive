---
title: "proxy and programs"
date: 2007-04-26
forum: General Help
---

### Post by Flavian on 2007-04-26
I got the following problem
I am forced to sit behind a proxy server. (proxy.salzburg.at:81) - or Port 82 with user and pass.

The thing is that it annoys me not to be able to use Exaile / Amarok's last.fm function, because they don't come with native proxy support :(
Also MSN does not work.

I tried "proxychains", but it does not work, it just brings up the program but no connection could be established!
Is there some other method than proxychains to force those programs to connect through the proxy?

Thanks for help!

---

### Post by bapoumba on 2007-04-26
hello,
have you set up a global proxy in **gnome-network-preferences** (you can run that command from a terminal)?

If the proxy setup does not change (ie not on a laptop), you can add a line down your ~/.bashrc:
# Proxy 
http_proxy=http://proxyname.domain:_port
export http_proxy

edit: remove the _ between : and p. It prints a smiley on the screen if : and p are next to each other ;)

---

### Post by Flavian on 2007-04-26
Hi !
Thanks for your answer.
Yes I have. I set it up ever since I installed feisty afresh. Should that proxy setting effect ALL the programs that don't have native proxy support?
Because if the variable is set, it simply does NOTHING! The programs can not connect out  :(

Is there maybe any other solution?

---

### Post by bapoumba on 2007-04-26
[http://bugs.kde.org/show_bug.cgi?id=132165]("http://bugs.kde.org/show_bug.cgi?id=132165")
Hi, may be look at this bug and kcmshell proxy to set up Amarok.

[http://www.exaile.org/trac/ticket/151]("http://www.exaile.org/trac/ticket/151")
And this one for Exaile, but looks less promising :/

---

