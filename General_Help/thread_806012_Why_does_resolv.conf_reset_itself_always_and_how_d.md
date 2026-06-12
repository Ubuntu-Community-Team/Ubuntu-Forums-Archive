---
title: "Why does resolv.conf reset itself always and how do I turn it off?"
date: 2008-05-24
forum: General Help
---

### Post by descentspb on 2008-05-24
On my ubuntu-server machine, i've set up the resolv.conf during the installation of the system. And now if i change it, it resets back to its original state after every reboot, or maybe also every 24 hours.

How can i change it?

---

### Post by bollix47 on 2008-05-24
System > Administration > Network

Click on the DNS tab.


Oops:  Please ignore.  The server part didn't register.

---

### Post by chrisccoulson on 2008-05-24
> **descentspb said:**
> On my ubuntu-server machine, i've set up the resolv.conf during the installation of the system. And now if i change it, it resets back to its original state after every reboot, or maybe also every 24 hours.

How can i change it?

Are you using DHCP to configure the network interface? Your /etc/resolv.conf will get overwritten with settings from the DHCP server each time you take out a new lease

---

### Post by HermanAB on 2008-05-24
Stop the resolvconf and avahi daemons.  I fail to understand why those POS things are shipped with Linux these days.  They are the first things I disable.

---

### Post by chrisccoulson on 2008-05-24
> **HermanAB said:**
> Stop the resolvconf and avahi daemons.  I fail to understand why those POS things are shipped with Linux these days.  They are the first things I disable.

Avahi is shipped to facilitate discovery of services on a network.

resolvconf is not shipped by default in Ubuntu. resolvconf is only needed when more than one process needs to modify the resolv.conf

---

