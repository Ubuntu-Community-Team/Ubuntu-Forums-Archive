---
title: "RAM support on Ubuntu 8.04 32 bit"
date: 2008-05-04
forum: General Help
---

### Post by breezey on 2008-05-04
What's the maximum amount of RAM that is supported on Ubuntu 8.04 32 bit? Thank you.

---

### Post by thisiam on 2008-05-04
[This]("http://ubuntuforums.org/search.php?searchid=40578803") should keep you busy for while.

short answer is 32 bit=3.25 gb max memory

read above for more info.

---

### Post by bodhi.zazen on 2008-05-04
> **thisiam said:**
> [This]("http://ubuntuforums.org/search.php?searchid=40578803") should keep you busy for while.

short answer is 32 bit=3.25 gb max memory

read above for more info.

That information is outdated. Newer hardware / 32 bit CPU will access up to 64 Gb RAM.

64 Gb RAM - PAE support
        [http://www.cyberciti.biz/tips/redhat-enterprise-linux-4gb-plus-ram-support.html](http://www.cyberciti.biz/tips/redhat-enterprise-linux-4gb-plus-ram-support.html)
        [http://www.serverwatch.com/tutorials/article.php/3715071](http://www.serverwatch.com/tutorials/article.php/3715071)
        [http://www.enterprisenetworkingplanet.com/netos/article.php/3710641](http://www.enterprisenetworkingplanet.com/netos/article.php/3710641)

        Kernel : [http://kerneltrap.org/node/2450](http://kerneltrap.org/node/2450)

    *****
    You need to configure grub !!!!
        [http://howtoforge.com/make-your-xen-pae-kernel-work-with-more-than-4gb-ram-debian-etch-grub](http://howtoforge.com/make-your-xen-pae-kernel-work-with-more-than-4gb-ram-debian-etch-grub)
    *****

---

