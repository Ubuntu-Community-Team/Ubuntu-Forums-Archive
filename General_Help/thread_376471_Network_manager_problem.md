---
title: "Network manager problem"
date: 2007-03-04
forum: General Help
---

### Post by FIONEX on 2007-03-04
I just found a funny but lame bug in the network manager and the nm-applet.  But i'm not sure if it's even bug, but tell me what you think.
I was over at a cousin's house and obviously 50% of people don't change the SSID of their wireless networks.  So you have 2 linksys networks in range and I'm trying to connect to the unsecured "linksys" SSID.  However, it ends up going to the WPA secured "linksys" (the second network). So I had to change my cousin's network SSID to something else in order to connect.

In case I run into something like that again, how would I connect to the mac address of a network so that I don't run into this SSID overlap problem.

---

### Post by caldevil on 2007-03-05
Seems like a bug to me. Do you wanna report it?

---

### Post by FIONEX on 2007-03-05
Will do.  Just a question though.  How would I connect to a network without using network manager/

---

### Post by gejr on 2007-03-05
Could use the integrated network-admin in ubuntu. It doesn't show any ssid's, but a iwlist <device> scanning lists the ssid's currently available. Then you'll have to write them into network-admin manually. Its not as WPA-friendly as networkmanager, but for WEP it works fine. 

You can also check out wifi-radar.

---

