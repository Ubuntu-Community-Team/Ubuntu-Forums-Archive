---
title: "How to update /etc/network/interfaces"
date: 2014-03-27
forum: General Help
---

### Post by sim085 on 2014-03-27
Hello, I had installed Ubuntu Server edition 12.3 on a PC that had a wireless card. I am now going to remove the wireless card and use the motherboard Ethernet connection. However when I open /etc/network/interfaces file I can see that I have a reference to the wireless network but no reference to the Ethernet card. I was wondering, after I have removed the wireless card and attached the PC to the router through the wire then how can I update the /etc/network/interfaces automatically?

---

### Post by Iowan on 2014-03-27
It isn't that difficult to use an editor to update /etc/network/interfaces manually. This is from my server:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```A DHCP address is even easier...
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

---

### Post by sim085 on 2014-03-27
Thanks, I had modified the file manually but left the wireless card connected and it seems this was conflicting. I removed the card. At first PC took long to start up. Once booted I went to the interfaces file and removed the info on the wireless and now it is ok.

Thanks for the help.

---

