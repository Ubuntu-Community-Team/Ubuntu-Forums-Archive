---
title: "Can't install updates"
date: 2013-08-31
forum: General Help
---

### Post by jack21 on 2013-08-31
Hi I cannot install updates either from the terminal or from the system settings. And also having trouble installing software too at times.

It's saying things like failed to fetch stuff and E: Some index files failed to download. They have been ignored, or old ones used instead.

Here is what comes up on the terminal: [http://pastebin.com/wUjshaZL](http://pastebin.com/wUjshaZL)
I've put it on pastebin due to how large it is.

If any of you could help me with this I'll be very grateful. Thanks.

---

### Post by mansonfan78 on 2013-08-31
Are you behind a proxy?  It looks like all the errors are related to "8080:80".  Whatever that is.  You should also check your router and firewall settings.

---

### Post by jack21 on 2013-08-31
> **mansonfan78 said:**
> Are you behind a proxy?  It looks like all the errors are related to "8080:80".  Whatever that is.  You should also check your router and firewall settings.

Well I was using Dansguardian but have removed it since. However the problem is still there. Are there any codes that I can use to remove the proxy configuration or perhaps restore the distro back to default?

---

### Post by mansonfan78 on 2013-08-31
Go to "network connections", highlight the connection you're using, "edit", and check all the tabs and see what's there.  Setting everything to automatic might do the trick.  It might be a good idea to write down what everything is currently set to in case you need to change it back.

---

### Post by jack21 on 2013-08-31
> **mansonfan78 said:**
> Go to "network connections", highlight the connection you're using, "edit", and check all the tabs and see what's there.  Setting everything to automatic might do the trick.  It might be a good idea to write down what everything is currently set to in case you need to change it back.

Wireless is set to automatic, IP4 is set to automatic DHCP what ever that is, and IP6 is set to automatic.

---

### Post by mansonfan78 on 2013-08-31
Set ipv6 to "ignore".  IPv4 and IPv6 are completely different protocols and usually won't work together.

---

### Post by jack21 on 2013-08-31
> **mansonfan78 said:**
> Set ipv6 to "ignore".  IPv4 and IPv6 are completely different protocols and usually won't work together.

Okay, done that but still experiencing the same problem.

---

### Post by mansonfan78 on 2013-08-31
Well, the only other thing I can think of would be to try connecting to ethernet with a cable.  But I somehow doubt that would work.  It could be some setting in your router or some config file in Ubuntu that got changed somehow.  Maybe someone else knows something, but that's all I've got.

---

### Post by mansonfan78 on 2013-08-31
I did just find this: [https://lists.ubuntu.com/archives/ubuntu-server/2012-June/006337.html](https://lists.ubuntu.com/archives/ubuntu-server/2012-June/006337.html)  that might be what you're looking for.

---

