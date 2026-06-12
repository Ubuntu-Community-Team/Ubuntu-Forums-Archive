---
title: "Network services not working"
date: 2014-01-28
forum: General Help
---

### Post by charlesdugger on 2014-01-28
hello every one I have searched and have not found this exact problem. My server connects to the internet but I can not connect to the local network.

I have Ubuntu 12.04 LTS with desktop installed

here is my interface file
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.1
network 192.168.1.0
broadcast 192.168.1.255
dns-nameservers 192.168.1.1

```

when I click on network I get a popup with this message
```

The system network services are not compatible with this version.

```

I have tried to install network manager from 9 as i read this would fix it. It did not help or I did not get it installed.

Possibly I broke it when i set it to a static ip.

Thanks in advance

---

