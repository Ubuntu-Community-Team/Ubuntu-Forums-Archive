---
title: "Filtering software for the internet??"
date: 2007-06-17
forum: General Help
---

### Post by owlhoot on 2007-06-17
I want some linux friendly software for web filtering so I can keep my son on the straight and narrow. Any good suggestions?

---

### Post by thelinuxguy on 2007-06-17
A proxy server can take care of it. You can install squid from the repository. It will need some configuration though.

---

### Post by owlhoot on 2007-06-17
> **thelinuxguy said:**
> A proxy server can take care of it. You can install squid from the repository. It will need some configuration though.

A proxy server is easily bypassed. I need something which is a little more secure. Can Firefox be configured so that the proxy server settings can be accessed only by an admin?

---

### Post by Swab on 2007-06-17
> **owlhoot said:**
> A proxy server is easily bypassed. I need something which is a little more secure. Can Firefox be configured so that the proxy server settings can be accessed only by an admin?

Yes, Firefox can be locked down.  

Also if your router supports it, you could block all outward bound port 80 traffic to any machine except the proxy server.

---

### Post by owlhoot on 2007-06-17
Thanks, that helped a lot. I think I can do the port blocking thing with ease.

---

### Post by thelinuxguy on 2007-06-18
There is also an easy way which works if you want to block certain domains/IP addresses. No filtering based on content as such. Edit /etc/hosts and map the blacklisted domains/IPs to 127.0.0.1. That site will be inaccessible. This should provide some additional security. 

Given the fact that there is a preconfigured file with more than 14,000 blacklisted domains available at [http://www.mvps.org/winhelp2002/](http://www.mvps.org/winhelp2002/), it is a simple and effective solution. And you can always add your handpicked domains as well. You may want to have a look at this related thread: [http://ubuntuforums.org/showthread.php?t=110440](http://ubuntuforums.org/showthread.php?t=110440)

Regards.

---

### Post by mtn on 2007-06-21
How do you lock down Firefox? I have tried Pessulus, which seems great but only works with Epiphany. Something like Pessulus that included controls for Firefox would be really good.

---

