---
title: "manage internet access"
date: 2008-05-03
forum: General Help
---

### Post by tanozfood on 2008-05-03
Hello,
I would like to use a linux box to do the following :

was asked me to develop a small solution to manage
internet access from wi-fi points, from clients that manage
the user accounts, all on the same LAN via a switch.
On the clients pc should be possible to know how long
the users stay on the internet, and a server should provide
restrictions and authentication for all.
I know my description seems so complicated, however it
should be a common task.
Any experience with the same problem?

---

### Post by lynxus on 2008-05-03
To me that doesnt make much sense? maybe ive read it wrong.

However if you want to see what people are doing from what IP address's from wi-fi points.

You could have a DHCP server hand out a select few IP's from a range and have that server send its dns server / gateway of a proxy server.

From that proxy server you can then monitor whats being accessed by who and when.

Im sure then a small php script on that server could tart up a frontend to view the logs etc.

Squid is a good proxy server...

Hope this helps at all.

-G

---

### Post by tanozfood on 2008-05-03
Think as a solution that should manage internetworking
in an hotel with people using wi-fi connections and
administrators that connect via ethernet to the same server.

---

### Post by lynxus on 2008-05-03
Thinking about it more..

If this is for wi-fi spots in a hotel and anyone can connect, i would suggest making your router send any outbound port 80 traffic to the proxy.

That way people cant bypass your proxy ( unless they tunnel traffic on a different port )

Also using this way you can get your proxy to send every page to the clients browser as some form of , Hey , Pay first.. IE: if they ask for google.com it will send your own page until you allow their IP access to the big wide world.

Anywho, Just an idea.

-G

---

### Post by Monicker on 2008-05-03
> **tanozfood said:**
> Think as a solution that should manage internetworking
in an hotel with people using wi-fi connections and
administrators that connect via ethernet to the same server.

Sounds like you may want a captive portal.  Take a look into some of the solutions listed here:  [http://en.wikipedia.org/wiki/Captive_portal#Software_Captive_Portals]("http://en.wikipedia.org/wiki/Captive_portal#Software_Captive_Portals")

---

### Post by tanozfood on 2008-05-03
Yes, I read this article about 2 hours ago.. :-)
I am trying to install wifidog, but seems to be a *enormous*
task for me..

---

### Post by Monicker on 2008-05-03
> **tanozfood said:**
> Yes, I read this article about 2 hours ago.. :-)
I am trying to install wifidog, but seems to be a *enormous*
task for me..

I just did a quick check and the chillispot portal software is in the Ubuntu repositories. So you might try installing that via synaptic, and at least seeing if it might suit your needs, instead of manually compiling a different package.

---

### Post by tanozfood on 2008-05-03
Mmmhhh, I am looking for a complete solution that includes
account management via web interface and seems that chillispot
lacks of this (I should study it better, however).

---

