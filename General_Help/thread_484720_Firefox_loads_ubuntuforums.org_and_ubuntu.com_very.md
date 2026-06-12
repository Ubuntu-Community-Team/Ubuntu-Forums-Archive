---
title: "Firefox loads ubuntuforums.org and ubuntu.com very slowly"
date: 2007-06-26
forum: General Help
---

### Post by wersdaluv on 2007-06-26
Using Firefox, I went to ubuntuforums.org and thought that it was down because it does not load. I also tried ubuntu.com and it does not load too. Firefox just says at the buttom "waiting for ubuntu.com." I am not sure, but it maybe, there is a problem with other sites too. I tried to go to ubuntu.com again using Firefox and  it loaded but it took about 5mins while in other browsers, just about ten seconds.

I tried Epiphany and Konqueror and there were no problems with browsing those sites.

What could the problem with Firefox be and how can I fix this?

---

### Post by PaulFr on 2007-06-26
Is it all sites, or just ubuntu.com and ubuntuforums.org ? If it is only these two sites, then you may have a connection problem. For me, after installing Feisty Fawn, all sites were slow - however, performance improved drastically after disabling IPv6 (see **[http://ubuntuforums.org/archive/index.php/t-6841.html](http://ubuntuforums.org/archive/index.php/t-6841.html)** for details) and switching to OpenDNS (**[http://www.opendns.com/start/ubuntu.php](http://www.opendns.com/start/ubuntu.php)**). YMMV, of course.

---

### Post by wersdaluv on 2007-06-26
Only those two sites are loaded very slowly. Also, right now, even in Epiphany and Konqueror, ubuntuforums.org loads slowly.

I am already using OpenDNS.

What does disabling IPv6 do?

---

### Post by PaulFr on 2007-06-26
Essentially, due to bugs in DNS servers for IPv6, an unnecessary second step is required to get the name resolved to an IPv4 address. See **[http://kb.mozillazine.org/Network.dns.disableIPv6](http://kb.mozillazine.org/Network.dns.disableIPv6)** for some more details. For other configuration options that may help Firefox performance, see **[http://kb.mozillazine.org/Category:Tweaking_preferences](http://kb.mozillazine.org/Category:Tweaking_preferences)**.

Here are some sample values for these parameters : **[http://www.testingreflections.com/node/view/1549](http://www.testingreflections.com/node/view/1549)**

---

