---
title: "not able to add multiple vlans"
date: 2013-09-19
forum: General Help
---

### Post by deees2 on 2013-09-19
Not able to add vlan 1 on 10.50.64.x and vlan 5. on 10.50.65.x  They are in different subnet but OS seems to think they are in same subnet and doesn't allow to add both only either one. Any clues if these can be added.

auto eth0.11
iface eth0.11 inet static
   address 10.1.10.1
   netmask 255.255.255.0
   vlan-raw-device eth0


auto eth0.5
iface eth0.5 inet static
    address 10.50.65.251
    netmask 255.255.255.0
    vlan-raw-device eth0
    gateway 10.50.65.1

auto eth0.1
iface eth0.5 inet static
    address 10.50.64.251
    netmask 255.255.255.0
    vlan-raw-device eth0
    gateway 10.50.64.1

---

