---
title: "opening TCP ports"
date: 2007-02-01
forum: General Help
---

### Post by DMAthlon on 2007-02-01
how do i enable TCP port 49352? it's for azureus. i assume it some firewall blocking it, so where? i uses v6.10 edgy. thanks you guys rock!

---

### Post by SeanTater on 2007-02-01
I have not used edgy, but AFAIK there is no firewall.. Are you behind a router? You may instead need port forwarding..

---

### Post by DMAthlon on 2007-02-01
i wirelessly connect to my router upstairs .... is that what it is? what do i do?

---

### Post by SeanTater on 2007-02-01
Your router probably has a web control panel, which is usually found at one of the following four addresses:

[http://192.168.1.1/](http://192.168.1.1/)
[http://192.168.1.0/](http://192.168.1.0/)
[http://192.168.0.1/](http://192.168.0.1/)
[http://192.168.0.0/](http://192.168.0.0/)

Look for "port forwarding" and forward that port to the local IP address (as **opposed** to the one at [http://www.whatismyip.com/](http://www.whatismyip.com/)) of the computer that needs to use it. 

Hint: Your **Local** IP probably resembles your router's IP

Look for "port forwarding", and forward it to your local IP (like your router control panel's IP, ** not like ** the one at [http://www.whatismyip.com/](http://www.whatismyip.com/))

---

