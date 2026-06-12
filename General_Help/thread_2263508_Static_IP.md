---
title: "Static IP"
date: 2015-02-01
forum: General Help
---

### Post by jim999 on 2015-02-01
Hi Guys

Could somebody point me to a howto to get Ubuntu 14.10 to have a static IP address and not DHCP.  The GUI confuses the heck out of me, would be much happier using vi on a file somewhere.  

Thanks

j

---

### Post by TheFu on 2015-02-01
The file is: /etc/network/interfaces
It is critical that you setup the DNS properly inside it. Often the router, but sometimes you want external IPs there. Do not manually edit the /etc/resolv.conf (not since 12.04).
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
  address 172.22.22.20
  gateway 172.22.22.1
  netmask 255.255.255.0
  #mtu 9014
  dns-nameservers 172.22.22.1
  dns-search example.com example.lan
```

---

### Post by jim999 on 2015-02-01
Nice one, thank you :-)

---

