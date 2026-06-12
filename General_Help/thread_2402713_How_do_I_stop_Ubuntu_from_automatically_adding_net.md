---
title: "How do I stop Ubuntu from automatically adding network printers?"
date: 2018-10-03
forum: General Help
---

### Post by itiracha on 2018-10-03
Ubuntu has automatically added all the network printers it could find to my printer list. Since I'm on a university network, there's 20-30 printers listed that aren't mine/I can't print to. I removed them all once, but now they're all back. Is there a way to stop this and only add printers when I specify?

---

### Post by edadasiewicz on 2018-10-04
This should be controlled by the file cups-browsed.conf in /etc/cups.  Change the line

BrowseRemoteProtocols dnssd cups

to be

BrowseRemoteProtocols none

---

