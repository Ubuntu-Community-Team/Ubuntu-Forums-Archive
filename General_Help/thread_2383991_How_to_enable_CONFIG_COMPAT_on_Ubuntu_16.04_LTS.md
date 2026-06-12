---
title: "How to enable CONFIG_COMPAT on Ubuntu 16.04 LTS"
date: 2018-02-01
forum: General Help
---

### Post by bhatja on 2018-02-01
[h=2][/h]Hi All,


We are using Ubuntu 16.04 LTS on 64 bit Linux. However our application is 32 bit application. I am facing issues when I am trying to use netlink socket to communicate with XFRM. struct msghdr is the structure used in sendmsg. This is 28 bytes in 32 bit application space and 56 bytes in 64 bit kernel space. While looking for the fix, I found that there compat layer already available. This can be enabled for CONFIG_COMPAT. In our case this is not enabled. I wanted to know how to enable this option. We are using x86_64 platform.


Any help is well appreciated.


Regards
Jayalakshmi

---

### Post by coffeecat on 2018-02-01
*Thread moved to **General Help**.*

---

### Post by dragonfly41 on 2018-02-01
I have no experience in this topic and I don't know if this thread offers any clues ...

[http://lists.infradead.org/pipermail/linux-arm-kernel/2015-January/320454.html](http://lists.infradead.org/pipermail/linux-arm-kernel/2015-January/320454.html)

i.e. Does the app work in root mode?

Other than that suggestion, could you install 32bit Ubuntu as virtual machine in VirtualBox in your host 64bit Ubuntu?
Or is that too much bother just to run your 32bit app?

---

