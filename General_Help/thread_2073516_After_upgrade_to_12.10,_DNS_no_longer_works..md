---
title: "After upgrade to 12.10, DNS no longer works."
date: 2012-10-19
forum: General Help
---

### Post by Go Vols Go on 2012-10-19
Hi, I upgraded to 12.10 yesterday and since then I cannot browse (or do other things such as update) that rely on DNS conversion. I can, however, go to Google via it's IP address, and ping 8.8.8.8 successfully. I'm not quite sure how to get the DNS server to work again. From reading other forums, I think my problem lies in dnsmasq. Any help would be appreciated!

---

### Post by Go Vols Go on 2012-10-19
After searching some more, I was able to use the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=12088241&postcount=31") to solve my issue. I had to purge and remove resolvconf to fix it. Initially, when I reinstalled it, it still wouldn't work. But after rebooting, it seems to work fine.

---

### Post by jdthood on 2012-10-29
Probably doing

   dpkg-reconfigure resolvconf

would have sufficed.

---

### Post by dawonn on 2013-01-08
Thanks jdthood. Worked perfect :)

---

### Post by jdthood on 2013-01-09
> **dawonn said:**
> Thanks jdthood. Worked perfect :)

Good to hear.

Lots of people have to do "dpkg-reconfigure resolvconf" after installation. See 
[https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244/comments/82](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244/comments/82) for discussion.

---

