---
title: "Evolution-Exchange Server 2003 Slow Synch"
date: 2007-05-24
forum: General Help
---

### Post by rhardie on 2007-05-24
I have Ubuntu on a workstation and on a LAN with my Exchange Server 2003.

Evolution sends/receives email via Exchange Server but very slow.

A previous install using 32 and 64 bit 7.04 worked fine.  I added a larger hard drive and did re-install and now slow.

Any suggestions?

Thanks in advance

---

### Post by TwiceOver on 2007-05-29
I also have this same problem.  Sorry, no solution for ya.  There seems to be a lot of posts about this around the internet so hopefully it will get fixed soon.

---

### Post by rhardie on 2007-06-03
The only thing I can think of is that I am running Exchange Server as an IIS server and my Outlook has web-based capability.

My reading, and reviewing the set up, indicates that there is a connection via a secure Outlook Web Access (OWA).  So if I log onto Outlook via a web page, then I'm doing [https://mail.DomainName.com/exchange](https://mail.DomainName.com/exchange) .

If Evolution uses OWA as the method of connecting, and there are any speed issues with the LAN or Internet connection or translations or what ever, then that might make sense to me.

Given that my work station sits about 23.5 mm away from my server, it seems like such an inefficient way to connect up to Exchange Server via the Internet when there could be a fast Ethernet connection directly from work station to server.

I don't know if this is the issue or not, but it's the only idea that I can come up with.

Any thoughts or comments?

Thanks in advance girls and boys - and we certainly honor and welcome the WOMEN of Ubuntu for their contributions and feminine genius.

Kind regards

---

### Post by rhardie on 2007-06-03
Another thought:  Would it be faster if I did [https://IPAddress.com/exchange?](https://IPAddress.com/exchange?)

I have a software application that I use on my workstation that talks directly to my IIS server and I tried using [https://DomainName.com/SoftwareName](https://DomainName.com/SoftwareName) and then someone recommended [https://DomainIPAddress.com/SoftwareName](https://DomainIPAddress.com/SoftwareName) and I believe it works better.

Any thoughts on this?

I'm not an IT guy but just someone who enjoys learning about all the cool stuff you can do with local networks and servers for my small business so I don't always 'understand' what I'm doing - YET. ;)

Regards

---

