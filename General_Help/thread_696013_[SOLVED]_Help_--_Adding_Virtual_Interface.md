---
title: "[SOLVED] Help -- Adding Virtual Interface"
date: 2008-02-13
forum: General Help
---

### Post by sgardne on 2008-02-13
I am attempting to do this on a server I have. Here is my /etc/network/interfaces:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address x.x.x.x
netmask 255.255.255.248
gateway x.x.x.y
hwaddress ether 00:14:22:1b:58:c0

iface eth1:2000 inet static
address 192.168.2.1
netmask 255.255.255.0
gateway 192.168.2.2
hwaddress ether 00:14:22:1B:58:C1
```

Whenever i issue sudo ifup eth1:2000 i get the following:
```
$ sudo ifup eth1:2000
SIOCADDRT: No such process
Failed to bring up eth1:2000.
```

I have found that if I comment out the gateway entry of the interfaces file, I can get eth1:2000 to come up, but that's not enough. How do I make a route to 192.168.2.2?

---

### Post by mrsteveman1 on 2008-02-13
Is this an ip-aliasing setup?

Does eth1 exist as a physical interface?

---

### Post by sgardne on 2008-02-13
> **mrsteveman1 said:**
> Is this an ip-aliasing setup?

Does eth1 exist as a physical interface?

I don't know what ip-aliasing is. I'm trying to set up a static route for traffic on 192.168.2.0. eth1 does exist as a physical interface but is giving me similar headache trying to get it configured.

---

### Post by mrsteveman1 on 2008-02-13
Elaborate a little bit, is this box going to be multihomed or something (multiple internet connections)? Is it doing routing?

i assumed you were using virtual interfaces for ip-aliasing, which is what you do when you want a single nic to respond to traffic on multiple IPs.

---

### Post by sgardne on 2008-02-13
> **mrsteveman1 said:**
> Elaborate a little bit, is this box going to be multihomed or something (multiple internet connections)? Is it doing routing?

i assumed you were using virtual interfaces for ip-aliasing, which is what you do when you want a single nic to respond to traffic on multiple IPs. The box has 2 physical interfaces. eth0 is going to have contact to the internet and eth1 is going to be in contact with several vlans for our clients. The box will be providing NAT as well as firewall. Each network segment will come in on its own virtual interface and go out on eth0 (if it's bound for internet).

Judging by your sig, you probably know way more about this than I do. I suspect this ip-aliasing is what I'm looking for, and I will definitely check into that tomorrow.


Thanks for your interest.

---

### Post by mrsteveman1 on 2008-02-13
IP-aliasing is used when you want a single box to respond to traffic as if it were multiple boxes, so for instance if you want to have web traffic coming in on one IP, and VPN traffic on another IP, but all going to the same box etc. This isn't what you want as far as i can tell.

I think what you want is to configure this box as a VLAN router for a VLAN switch. We call it router on a stick :D

Do you have a switch that supports VLANs and VLAN trunking? The documentation for the switch will mention 802.1q somewhere if it does support trunking. Without using a VLAN switch there is no way to support VLANs on a single ethernet interface on a box like this.

---

### Post by sgardne on 2008-02-15
Turns out I was actually barking up the wrong tree, like you said. What I actually need is a VLAN interface. This requires the vlan package and 802.1q drivers.

---

### Post by scorp123 on 2008-02-15
> **mrsteveman1 said:**
> IP-aliasing is used when you want a single box to respond to traffic as if it were multiple boxes, so for instance if you want to have web traffic coming in on one IP, and VPN traffic on another IP, but all going to the same box etc.  I wanted that ... and I found this thread, and it didn't really help me. But via Google I found a posting that showed me how to solve this:

[http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html](http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html)

So I am posting this here just in case someone finds himself in the same situation and happens to stumble across this thread, in the hope that this may be useful for someone one day.

---

