---
title: "Problem installing wtorrent for rtorrent"
date: 2008-03-05
forum: General Help
---

### Post by falken264 on 2008-03-05
I am trying to install wtorrent and i am following the guide on: [http://canbruixa.homelinux.net/wt/]("http://canbruixa.homelinux.net/wt/")
The guide is on the page Install.

I have followed the instruction but after i use ./configure --with-xmlrpc-c there is no Makefile.
There is a Makefile.am and a Makefile.in but when i do make it says that it cannot find a Makefile.

I have been following the instruction so i am trying with the svn version of rtorrent

Thanks
David Falk

When I use ./compile the last two lines are:
> ./configure: line 22683: syntax error near unexpected token `OPENSSL,'
./configure: line 22683: `      PKG_CHECK_MODULES(OPENSSL, openssl,'

---

### Post by panGa on 2008-03-15
Bump, I have exactly the same problem.
I'm very thankful for help.

---

### Post by panGa on 2008-03-15
Anyone?

---

### Post by falken264 on 2008-03-15
I solved my problem by using torrentflux instead.
It is already added to ubuntu so all you have to do is use apt-get

---

### Post by nmat on 2008-04-18
you need to install openssl-dev or openssl-devel, I'm not sure which name is used by ubuntu

---

