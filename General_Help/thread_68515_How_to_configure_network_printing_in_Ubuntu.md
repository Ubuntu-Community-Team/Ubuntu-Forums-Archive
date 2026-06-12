---
title: "How to configure network printing in Ubuntu?"
date: 2005-09-23
forum: General Help
---

### Post by Tux on 2005-09-23
I have a standard installation of Ubuntu.  /etc/hosts looks like this:

127.0.0.1        localhost.localdomain        localhost
10.0.0.100      tompth.noneofyour.biz      tompth

Indeed the system is reacheable by `ping` in my LAN at 10.0.0.100; however, no services at all appear to be listening at 10.0.0.100 .  In particular, there is no network printer.  cupsd is running and I can make local prints.  

The GUI sysadmin printer tool allows to set the printer type to CUPS Network; but I have to enter a URI and I have no idea what I should fill in there (my experiments didn't work out).

How do I go about configuring cupsd to accept jobs over the LAN?

Thanx,

---

