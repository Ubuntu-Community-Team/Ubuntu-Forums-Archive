---
title: "FYI - how to use Sharing feature in Azureus!"
date: 2007-08-02
forum: General Help
---

### Post by bsmith1051 on 2007-08-02
FYI
Using Ubuntu 7.04 I was having trouble with the Sharing feature in Azureus.  First of all, I had to manually update the 2.5.0.0 version installed by Add/Remove Programs because it kept crashing.  Version 2.5.0.4 has been solid!  But Azureus continued to complain that it couldn't open the port I'd selected for sharing.  My firewall showed it as opened and Shields Up reported it as open.  Finally, I found this FAQ on the Azureus wiki and the instructions re Ubuntu solved the problem,
[http://www.azureuswiki.com/index.php/NAT_problem#Port_Forwarding_on_Linux.2C_specifically_Ubuntu](http://www.azureuswiki.com/index.php/NAT_problem#Port_Forwarding_on_Linux.2C_specifically_Ubuntu)

Basically, Ubuntu has the iptables internal firewall enabled by default and it blocks Azureus from listening on new ports.  The instructions tell you how to exempt the port you want to use, and also how to make the change permanent.

UPDATE #2: In the Azureus Tools > Options configuration, you want to set the port for Sharing _different_ than the port for incoming!  Basically, the port you see on the very first settings screen is really for you regular download/seeding, whereas the port you find under the Tracker options is what gets advertised in the .torrent.

UPDATE #2:  You _also_ need to then load the torrent in Azureus and not only share it (anything you create should immediately be listed in the lower Seeding window) but also right-click on it and select "Host".  A new My Tracker tab will then open, with your hosted/shared file!

P.S.  You should be able to check that the Sharing feature is working if you can browse to the built-in status page at 'hostname:share-port', e.g. [www.mysite.com:1234](www.mysite.com:1234).  Not only should you see the status page, but you should also see the hosted file(s).

---

### Post by kelvin spratt on 2007-08-02
very strange i use the blue frog never had a problem with ports.

---

### Post by bsmith1051 on 2007-08-02
for regular torrents, there's no problem.  The issue is specific to the Sharing feature, where you are acting as the tracker and need to be able to receive unsolicited incoming traffic.

---

