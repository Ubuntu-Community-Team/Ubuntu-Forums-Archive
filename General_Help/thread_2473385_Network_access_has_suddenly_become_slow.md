---
title: "Network access has suddenly become slow"
date: 2022-04-02
forum: General Help
---

### Post by lelandiniowa on 2022-04-02
Since the latest updates a few days ago to my PC (ubuntu stable thread), any network access has become very slow, both on my local network and the Internet. None of the other computers on my local network are experiencing this issue, just my Ubuntu Linux PC. Message images in the Evolution browser take forever to load, if at all. Trying to print a message to my network printer from Evolution just hangs up and never prints. I'd think it is just a problem with Evolution except that accessing web pages in the Opera browser also frequently times out  (but things print fine to my network printer from Opera). I installed ubuntu on this PC about a year ago and it has been working great up until a few days ago.

Has anyone else begun to recently see slow network access like this? In any case, is there anywhere that I can find information about how to fix such problems?

About in the settings lists the following version info: Ubuntu 20.04.4 LTS, 64-bit, GNOME Version 3.36.8, X11 Windowing System.

---

### Post by HermanAB on 2022-04-03
You probably have a lame DNS server.  Check the DNS performance with “dig”. Check the network performance with “ntop”.

---

### Post by lelandiniowa on 2022-04-03
I'm not sure why but, after updates were installed today, this is no longer a problem.

---

