---
title: "libXpm not found"
date: 2008-06-29
forum: General Help
---

### Post by Daniel09 on 2008-06-29
Hello all, I just recently joined and am kind of new.

I have a problem regarding libXpm. I am trying to install root:
[http://root.cern.ch/](http://root.cern.ch/)

which requires lipXpm. When running ./configure I get the message:

Checking for libXpm ... no
configure: libXpm MUST be installed

Thus I tried to look for it using the search engine and found the following files:

libXpm.so.4.11.0
libXpm.so.4

both in /usr/lib The thing that bugs me though is that I didn't find anything that looked like libXpm.a I tried specifing the location of libXpm when doing configure like so:

./configure --with-xpm-libdir=/usr/lib

Anybody have any ideas why configure complains about libXpm?

---

### Post by manfer on 2008-06-29
Try installing the development package for that library, libxpm-dev

prompt:~$ **sudo apt-get install libxpm-dev**

---

