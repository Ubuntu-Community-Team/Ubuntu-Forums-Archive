---
title: "Input signal out of range"
date: 2007-11-14
forum: General Help
---

### Post by explorer716 on 2007-11-14
I got a message on my computer saying  I needed  to install a restricted driver( ATI accelerated graphics) on my computer for it to function  properly and to be able to run VMware Server and Kernel Driver.

After installing  ATI accelerated driver I get a message during the PC boot-up stating, "Input signal out of range. Change settings to 1680x1080" , then in about 10 seconds the monitor goes to sleep.

You assistance in resolving this problem will be greatly appreciated

---

### Post by ddrichardson on 2007-11-15
The message means that the frequency selected for your monitor is outwith it's capabilities and the sleep is to protect the screen. Best bet is to enter the correct rates into /etc/X11/xorg.conf there's a guide on my [blog]("http://blog.lynxworks.eu/?p=20") to reconfiguring X.

---

