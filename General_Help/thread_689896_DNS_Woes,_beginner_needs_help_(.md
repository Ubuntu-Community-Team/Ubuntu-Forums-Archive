---
title: "DNS Woes, beginner needs help :("
date: 2008-02-06
forum: General Help
---

### Post by Chimei on 2008-02-06
Hey Guys,

I am currently in somewhat of a pinch at the moment and i would like to get some sort of light, after experimenting with dns for a few weeks to get nowhere. I have read many guides and tutorials, however being so locked towards these guidelines, at times i do not understand some concepts or do not have the right knowledge to make adjustments. I understand the basics to the dns system, alot of theory has made me quite confused.

**My primary goal of everything im trying to do is set up an email server, accessible from anywhere, not just internally.**
I am currently using 6.06 server edition installed on a machine, and a few more machines on standby when the time comes to balance the load on the servers.
-A purchased domain
-A public static IP ( with an additional 4 addresses)
-Internal network range 

What confuses me, is how the above all talk to each other. I have successfully managed to create an internal DNS system which resolves addresses, internal to the network. Additionally I would like to know how can i transform the current DNS server so it can manage domains.

This post may seem confusing but(im confused myself!), any help is much appreciated!!

Cheers

---

### Post by joebeasley on 2008-02-07
You need some type of firewall or router sitting between your internal and external networks.  A firewall/router with multiple interfaces would allow you to put the mail and dns servers on their own subnet (dmz).  The firewall/router would then translate your external addresses to internal addresses.

Once you have setup routing correctly between your external addresses and internal addresses, you can setup the DNS server to host the domains.

---

### Post by Chimei on 2008-02-07
Thank you for your reply Joe!

Yes i currently have 2 NICs installed, namely eth0(internet) and eth1(Internal network), masqeraded to allow eth1 access to the internet, i have minimised firewall restrictions to lessen the complications until i can properly set up the DNS server.

---

