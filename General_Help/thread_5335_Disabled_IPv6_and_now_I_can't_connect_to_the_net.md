---
title: "Disabled IPv6 and now I can't connect to the net"
date: 2004-11-17
forum: General Help
---

### Post by salemoh on 2004-11-17
Hi All,

I had a weird problem with my ubuntu installation (I'm a newbe), it took ages to resolve a dns name and then firefox would tell me request timed out.

I digged into the forms and found out it was IPv6 that was the problem.

I fixed firefox and it behaved correctly but apt-get was still giving me problem. When I change the sources.list it just hangs for ages trying to connect to archive.ubuntu.com and if I break out of it and ping the website and run apt-get again it would work.

So, I opted to disable the IPv6 module and after doing that (changing /etc/modprobe.d/aliases) I now can't access the net anymore  :cry: and I have a static IP and ipconfig reports all is well and dandy for my eth0.

Any ideas?

---

### Post by jdong on 2004-11-17
post contents of **/etc/resolv.conf**

---

### Post by salemoh on 2004-11-17
resolve.conf has one entry

nameserver 67.40.207.118

and I can't ping it, but when I **modprobe ipv6** I can ping it, but then I get stuck with the issue i described in my initial post (I need to ping every dns name in order for get-apt to see it).

---

### Post by jdong on 2004-11-17
reenable IPv6.


To fix Firefox, go to about:config, set network.dns.disableIPv6 to true.

---

### Post by salemoh on 2004-11-17
Did that for firefox and it worked, thanks for the quick response!

My other problem involves apt-get. It doesn't seem to be able to resolve any of the server names I have in sources.list unless I manually do a ping on the server name then it would start to see them.

---

