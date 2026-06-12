---
title: "Bridge IP is in conflict with host IP for KVM network setup"
date: 2016-10-10
forum: General Help
---

### Post by chbus on 2016-10-10
I have been following the instruction on this page to setup a bridge network for KVM on Ubuntu 16.04.
[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

```
auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
        bridge_ports eno1
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
```

But, both eno1 and br0 obtained the same IP address from DHCP router. This caused my host network stop working. I guess neither NIC will work due to this conflict. How to resolve this? I am expecting to have different IP for eno1 and br0. How to achieve this?

---

### Post by TheFu on 2016-10-10
eno1 shouldn't be active.  I make my physical adapter set to manual - to prevent network-manager from touching it.  On systems with a bridge, it is best to purge network manager, actually.  I always use a static IP too, so don't know how well the DHCP will work with the bridge. For example:

```
auto eth0
iface eth0 inet manual

# ####################################
auto br0
iface br0 inet static
  address 172.xx.xx.6
  gateway 172.xx.xx.1
  netmask 255.255.255.0
  broadcast 172.xx.xx.255
  dns-nameservers 172.xx.xx.1
  dns-search example.com 
  bridge_ports eth0
  bridge_fd 9
  bridge_hello 2
  bridge_maxage 12
  bridge_stp off
```

This example is on a 14.04 KVM server. Only have toy systems on 16.04 at this point.

---

### Post by chbus on 2016-10-11
I don't have dns-server and thus I don't think I can do static IP for br0. Why do you say eno1 should not be active. It's like the eth0 in your case. 

I actually don't know what end result I should expect: will br0 take over the IP of the host eno1 and making eno1 not functional or get a new IP? Since br0 and eno1 has the same MAC address, how does DHCP know to assign different IP for each network interface. Does anyone has a sample setting for br0 and eno1 working with DHCP?

---

### Post by TheFu on 2016-10-11
DNS doesn't have **anything** to do with setting static IPs.
Sure, you can use DHCP Reservations as a way to setup a static IP, but you don't have to do it that way and most places where I've worked didn't.

I don't understand the hesitation.  It takes 20 seconds to try it (perhaps 2 min if you are a slow typist) and see what happens. Try it will answer more questions than asking here.  Plus you have a method that doesn't work. Try something different, see if it works (btw, it will). Nothing to lose, right?

Inside each VM, the virtual-NIC(s) will have a different MAC and get a different IP from the DHCP server (unless you set them statically).

Try it.

---

### Post by chbus on 2016-10-12
It is working now with DHCP directly. My config setting as that in the first post is correct one. Somehow the network service failed to restart correctly and pickup the new changes. thanks for the help.

---

