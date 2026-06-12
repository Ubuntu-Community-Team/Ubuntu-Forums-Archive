---
title: "Vlan with specific eth interface"
date: 2014-10-26
forum: General Help
---

### Post by deepak17 on 2014-10-26
Hi):P,

I have configured ISC DHCP Server in ubuntu 12.04 box and I need to configure the DHCP leasing(relay) server from my ubuntu workstation.Here is my environment setup

eth0 - Static IP
eth0.1 - Static IP VLAN 1
eth0.2 - dhcp VLAN 2

I need to use eth0.1 as default interface to lease the IP address to other device and interface,So When I configure with DHCP and remove the static IP in eth0 it doesn't get the IP address.Any guess Why it doesn't work

May be after completion I need to use eth0 interface to provide the IP address to device connect in the network.

---

