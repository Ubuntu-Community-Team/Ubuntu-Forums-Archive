---
title: "Unable to connect to the Internet"
date: 2004-11-05
forum: General Help
---

### Post by nbliang on 2004-11-05
Hi, I am having problem with my Internet connection. For your information, I am using xDSL for my Internet connection and I have setup the xDSL by using the following method:
```
sudo pppoeconf
``` The problem is although I have setup the xDSL, I still unable to access the Internet. My Mozilla Firefox always have this status at it's statusbar "resolving..." and will not display the page, instead it shows an error message of "page not found".

Anyone know how to solve this problem? Please I need help here.

---

### Post by az on 2004-11-05
Did you set it up right?

Open a terminal and try

ping [www.debian.org](www.debian.org)

and see ifyou are actually on the net.

sudo ifconfig
to see the status uf your connections...

---

