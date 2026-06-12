---
title: "help to install the latest crypto++ library"
date: 2017-02-05
forum: General Help
---

### Post by kim2007 on 2017-02-05
Hi there,
  I just install ubuntu couple hours ago. I am trying to install a c++ library called crypto++. The official release is 5.6.5 but when I following the below instruction to install the library 

[COLOR=#242729][FONT=Consolas]sudo apt-get install libcrypto++-dev libcrypto++-doc libcrypto++-utils

[/FONT][/COLOR]I find that it install 5.6.1-9 version instead of the latest one. The example program that use cypto++ need some functions given in the latest version only. I wonder if there is any way I could get the latest version installed. Should I use different repository and get it installed again? What repository am I supposed to use? Thanks.

---

### Post by steeldriver on 2017-02-05
I'm assuming you installed Ubuntu 16.04?

It looks like Ubuntu 16.10 provides libcrypto++-dev version 5.6.3 - if that is recent enough for you, that's probably the simplest route

[http://packages.ubuntu.com/yakkety/libcrypto++-dev](http://packages.ubuntu.com/yakkety/libcrypto++-dev)

If you really need the absolute newest version, you will likely need to build and install it from source

---

### Post by kim2007 on 2017-02-05
> **steeldriver said:**
> I'm assuming you installed Ubuntu 16.04?

It looks like Ubuntu 16.10 provides libcrypto++-dev version 5.6.3 - if that is recent enough for you, that's probably the simplest route

[http://packages.ubuntu.com/yakkety/libcrypto++-dev](http://packages.ubuntu.com/yakkety/libcrypto++-dev)

If you really need the absolute newest version, you will likely need to build and install it from source

Thanks a lot for your reply. I will try 5.6.3 but could you show me how to get that installed? can I use apt-get and route to that link for install? thanks.

---

