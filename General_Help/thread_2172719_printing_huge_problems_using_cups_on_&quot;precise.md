---
title: "printing: huge problems using cups on &quot;precise&quot; ubuntu server, clients raring"
date: 2013-09-06
forum: General Help
---

### Post by jojoax on 2013-09-06
:confused:
The server installation for pure precise environment worked fine.
The server is responsible for serving an network workgoup printing station, i.E. Minolta C353.
Installed is: 
root@server:cups # apt-cache show cups
Package: cups
Priority: optional
Section: net
Installed-Size: 4193
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian CUPS Maintainers <pkg-cups-devel@lists.alioth.debian.org>
Architecture: amd64
Version: 1.5.3-0ubuntu8
[...]

Installing the Minolta C353 Printer via Webinterface (port 631) in connection to minolta:631 woks like a charm - for a few hours.
Next Day neither printing or spooling woks.
This occours since a few "raring" clients within the local network are active.

WTF?

I hate to reinstall the Printer on the server Day-by-Day 

WTF?

Jojo

---

### Post by rai_shu2 on 2013-09-06
Printing can become a big headache, yes. I think you're going to need to update the print server to 13.04 in order to avoid conflicts with those clients.

If that is the problem, it's just a once-every-six-months problem. :)

---

