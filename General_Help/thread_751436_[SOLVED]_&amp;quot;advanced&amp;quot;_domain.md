---
title: "[SOLVED] &amp;quot;advanced&amp;quot; domain"
date: 2008-04-10
forum: General Help
---

### Post by borobudur on 2008-04-10
Hi, 
I would like to have a web address like this
```
subdomain.domain.net
```
instead like this
```
domain.net/subdir
```
I guess I need to install a DNS server on the server pointing to *domain.net* which has the next IP of *subdomain.*

Is this the only way to reach *subdomain.domain.net*? 

Thanks

---

### Post by stalker145 on 2008-04-11
> **borobudur said:**
> Hi, 
I would like to have a web address like this
```
subdomain.domain.net
```
instead like this
```
domain.net/subdir
```
I guess I need to install a DNS server on the server pointing to *domain.net* which has the next IP of *subdomain.*

Is this the only way to reach *subdomain.domain.net*? 

Thanks

If you go into your domain's control panel, depending on which registrar you are using, you should be able to easily create sub-domains. From there, I assume it would be a matter of having Apache look for the differences between **sub.domain.tld** versus **domain.tld**.

But the first place I would start with with your registrar and add a subdomain.

---

### Post by borobudur on 2008-04-16
You mean in Apache I can configure it? I don't use any config software. Does anybody know how to do that in the config file?

---

### Post by stalker145 on 2008-04-17
> **borobudur said:**
> You mean in Apache I can configure it? I don't use any config software. Does anybody know how to do that in the config file?

Nope, not in software and not in Apache... yet. 

Whomever you registered your domain through should have a way for you to control where your domain points. There should also be an option for creating a subdomain in the same general place that you change the domain's information.

Once you get that done, someone should be able to help you configure Apache to know where to send the subdomain.

---

### Post by borobudur on 2008-04-18
You mean my provider. But *subdomain.domain.net* is in my network on a internal computer. *domain.net* is the proxy of the network. Don´t think I can configure this at my providers...

---

### Post by borobudur on 2008-04-18
I was looking for this:
[http://ubuntuforums.org/showthread.php?t=592456&highlight=%2Fetc%2Fapache2%2Fsites-available+subdomain](http://ubuntuforums.org/showthread.php?t=592456&highlight=%2Fetc%2Fapache2%2Fsites-available+subdomain)

---

