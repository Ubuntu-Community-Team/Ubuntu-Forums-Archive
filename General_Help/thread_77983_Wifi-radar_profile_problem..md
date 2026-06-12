---
title: "Wifi-radar profile problem."
date: 2005-10-17
forum: General Help
---

### Post by cbudden on 2005-10-17
Ok.  I cannot edit my wireless profile in wifi-radar.  I can make a new one but cannot delete or edit the current one.  Here is a screenshot. [http://flickr.com/photos/chrisbudden/53500591/](http://flickr.com/photos/chrisbudden/53500591/)
and here is my /etc/network/interfaces file :

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid Chris' Wireless Network
wireless-key 22F7FE2FC136E6EBD85EE8E0F4

auto eth1

```

---

### Post by cbudden on 2005-10-18
Anyone?

---

