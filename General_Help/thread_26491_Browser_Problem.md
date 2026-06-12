---
title: "Browser Problem"
date: 2005-04-13
forum: General Help
---

### Post by spot on 2005-04-13
I've just gotten Ububtu installed on my machine (which has an integrated RealTek 8100B nic).  I did a vanilla install and everything seems to work nicely except web browsing.  I'm using DHCP and I know that at some level my network is functioning since ssh, ftp, and ping work fine.  However, whenever I fire up a web browser (I've tried Firefox, Mozilla, and Epiphany), few sites will ever load (even though I can ping them).

Is this a known issue, or do I have something uniquely scewed up?

Thanks!

---

### Post by nad on 2005-04-13
If you are using dhcp, you are connecting through another machine. What is your physical setup.

Dan M

---

### Post by spot on 2005-04-13
I'm connected through an ActionTec DSL modem/router.

---

### Post by nad on 2005-04-13
I suspect that your modem/router is not initialized or setup correctly.

Please see,

[http://www.actiontec.com/support/broadband/54mbpswru_faqs.html](http://www.actiontec.com/support/broadband/54mbpswru_faqs.html)

 for information about one ActionTec product.

Dan M

---

### Post by spot on 2005-04-14
I stumbled on a thread discussing a similar problem... it turned out I needed to disable IPv6 in the FireFox config.  Works like a charm now.

[http://ubuntuforums.org/showthread.php?t=3699&page=1&pp=10&highlight=iPv6](http://ubuntuforums.org/showthread.php?t=3699&page=1&pp=10&highlight=iPv6)

---

