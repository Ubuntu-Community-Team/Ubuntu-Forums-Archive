---
title: "problem with server and router"
date: 2006-12-21
forum: General Help
---

### Post by yohoo on 2006-12-21
Hi guys;

Im studying how to set up a server atm; i just register a free account here [https://www.dyndns.com/](https://www.dyndns.com/) with a domain which is point to my IP address. However my internet connect through a router; whenever i access to the domain ; it will show the admin page of the router; i wonder how can i make it possible to access the web page. I have tried to install apache2 , ipcheck ,php 5 , mysql and ddclient but i dont know how to figure it out still.

Please help me out guys..

Thanks a lot.

---

### Post by gaebriel on 2006-12-21
It sounds like your firewall needs to be configured to forward external inbound HTTP (TCP port 80) and/or HTTPS (TCP port 443) traffic to your internal server. Internally, you'll probably need to run your own DNS server or modify your /etc/hosts on each box to point to the internal IP of your server. 

HTH

---

### Post by kidders on 2006-12-21
Hi there,

You need to configure your router to forward packets to the correct computer on your LAN. Depending on the router, the feature might be called NAT (Network Address Translation).

Incidentally, in my experience, DynDNS is a great service, but it can attract malicious users to your computer like moths to a flame. Make sure you disable remote access to your router's admin service!

**Edit:** Oops... too slow!

---

### Post by yohoo on 2006-12-21
thanks all for your replies; i just access to the admin page; config something about inbound port then now i cant access the page anymore for some reasons :( trying to find out how to reset it....

---

### Post by kidders on 2006-12-21
If by "the page" you mean your router's admin service, then that's exactly what you want :-) Unless you work around it yourself, you shouldn't be able to access your router admin *and* your own website at the same time from outside your LAN.

---

### Post by yohoo on 2006-12-21
hmm so how do i access to my web page? Actually i dont need to access the router admin; cause i have nothing to do with it.

Thanks for your replies

---

### Post by yohoo on 2006-12-21
and yes please; now i can not even access to the admin web page; i tried to restart the router manually ( click on the reset button on router ) and also plug the power off. However i still cant connect to it. What should i do now please?

please help 

Thanks

---

### Post by kidders on 2006-12-21
If you've reset your router, you probably need to reconfigure it from scratch. It may event have forgotten how to connect to your ISP.

Once you're done, use the router admin utility to redirect port 80 to your web server. Like gaebriel said, a DNS server would also be a smart idea ... especially if you want to host multiple websites at the same IP.

Also, be sure your web server is listening on the right network interface!

---

### Post by yohoo on 2006-12-22
thanks ; im still looking how to reconfigure the router again ; it still doesnt show ; i dunno why ...

happy xmast (early) to everyone ;)

---

