---
title: "multiple ips handling"
date: 2008-06-02
forum: General Help
---

### Post by alxlabs on 2008-06-02
I have:

1. Ubuntu 7.10
2. eth0 configured as following (/etc/interfaces)

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.12
netmask 255.255.255.0
gateway 192.168.2.1

auto eth0:1
iface eth0:1 inet static
address 192.168.2.16
netmask 255.255.255.0
gateway 192.168.2.1

```

So I have 2 ips - 192.168.2.12 (eth0) and 192.168.2.16 (eth0:1)

What I want: 

All the ports on eth0:1 (192.168.2.16) to be forwarded to the virtulhost guest, i.e. another instance of Ubuntu on the same machine. Problem is that host system listens for some standard ports (22, 80 etc) for both of the ips. 

How can I make all the services of the host machice listen/respond only to the ports on the eth0, but not eth0:1, so eth0:1 can be made dedicated to the guest OS on virtualbox?

---

