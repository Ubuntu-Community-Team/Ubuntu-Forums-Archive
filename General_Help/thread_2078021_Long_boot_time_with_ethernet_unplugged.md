---
title: "Long boot time with ethernet unplugged"
date: 2012-10-29
forum: General Help
---

### Post by Hydrohs on 2012-10-29
As the title says I experience a very long boot time if I have the ethernet cable unplugged on my laptop, 2:30 vs 30 second with it plugged in. No idea where to start with fixing it.

---

### Post by sucksatcompiling on 2012-10-29
Check this out.  I used to get an error "Waiting for network configuration" which caused really long boot times as well.

[http://askubuntu.com/questions/63456/waiting-for-network-configuration-adding-3-to-5-minutes-to-boot-time](http://askubuntu.com/questions/63456/waiting-for-network-configuration-adding-3-to-5-minutes-to-boot-time)

---

### Post by Hydrohs on 2012-10-29
> **sucksatcompiling said:**
> Check this out.  I used to get an error "Waiting for network configuration" which caused really long boot times as well.

[http://askubuntu.com/questions/63456/waiting-for-network-configuration-adding-3-to-5-minutes-to-boot-time](http://askubuntu.com/questions/63456/waiting-for-network-configuration-adding-3-to-5-minutes-to-boot-time)

Ah! Thank you very much, that worked like a charm. Commented out the two lines for eth0 and now my laptop boots in about 25 seconds whether I have the cable plugged in or not.

---

