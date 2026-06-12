---
title: "Opening a firewall port"
date: 2007-12-17
forum: General Help
---

### Post by kevindubrow on 2007-12-17
My torrent downloads in Azureus are very slow because port 22728 is apparently closed. I got this message from Azureus's NAT/ Server Port test:

Testing port 22782 ... 
NAT Error - Connect attempt to your computer timed out after 20 seconds. This means your port is probably closed.

Any clue how I could open this port? Thank you.

---

### Post by lespaul_rentals on 2007-12-17
Does Azureus have a UPnP function?  If not, you will have to forward the port from your router to your workstation, which should have a static IP.  This is most likely the connection issue.  Also, if you have a firewall such as Firestarter enabled, you must add rules to allow connections on all the Azureus ports.  I've always had problems with that part, so I usually just leave Firestarter off when using BitTorrent.

---

### Post by kevindubrow on 2007-12-17
According to Azureus's wikipedia, it does have a UPnP. I'm not sure what I would do with that though. I don't have a firewall program installed...I think I only have iptables. 
I ran sudo  iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 22782 -j ACCEPT

But it apparently did not do anything because I still get the same message from the NAT/ Server test.
Thanks for your help!

---

### Post by lespaul_rentals on 2007-12-17
Go into the Azureus settings and look for a UPnp option or plugin of some sort.  Try that.

---

