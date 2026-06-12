---
title: "ubuntu server 16.0.4.1 networkk problems"
date: 2016-12-25
forum: General Help
---

### Post by garrett13 on 2016-12-25
I'm stuck on the guide [https://ubuntuforums.org/showthread.php?t=2034067](https://ubuntuforums.org/showthread.php?t=2034067)   I'm on the last part when I run 
cat /etc/network/interfaces  all i'm getting back is

 source etc/network/interface.d/*

# The loopback network interface 
auto lo
 iface lo inet loopback

---

### Post by cariboo on 2016-12-25
The output of /etc/network/interfaces should look similar to this:

```
 cat interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

which is normal if you are using NetworkManager

On a server with no GUI (the default install), /etc/network/interfaces should look like this:

```
cat interfaces
# This file describes the network interfaces available on your system 
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp2s0
iface enp2s0 inet static 
	address	192.168.0.205
	netmask	255.255.255.0
	gateway	192.168.0.1
	dns-nameservers	8.8.8.8 8.8.4.4
```

The above output sets the ip address to 192.168.0.205, and uses Google for DNS.

---

### Post by garrett13 on 2016-12-25
So all I need to do is edit the cat interfaces to that? How?

---

