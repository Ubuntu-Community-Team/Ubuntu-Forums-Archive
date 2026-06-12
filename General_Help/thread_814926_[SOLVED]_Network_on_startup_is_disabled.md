---
title: "[SOLVED] Network on startup is disabled"
date: 2008-06-01
forum: General Help
---

### Post by Plasma_NZ on 2008-06-01
Ok.. slight problem im gettin annoyed with...

Every time i reboot, and login i have to open terminal and type

```
sudo ifup eth0
```

to enable my internet - how can i change this so its active on startup.?

---

### Post by phidia on 2008-06-01
I believe the /etc/network/interfaces file handles that, although you might be able to open the gui System>network or network tools to configure it.

Anyway my interfaces file looks like this:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface




iface eth0 inet dhcp

auto eth0
You could compare yours to that and see if your missing anything. Hope that helps.

---

### Post by Plasma_NZ on 2008-06-01
> **phidia said:**
> I believe the /etc/network/interfaces file handles that, although you might be able to open the gui System>network or network tools to configure it.

Anyway my interfaces file looks like this:


You could compare yours to that and see if your missing anything. Hope that helps.

Mines as follows currently..

```
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.24
netmask 255.255.255.0
gateway 192.168.0.1
```

---

### Post by Plasma_NZ on 2008-06-02
Thanks phidia - worked a treat..

---

