---
title: "2 network cards"
date: 2005-08-12
forum: General Help
---

### Post by [pl]ice on 2005-08-12
hi, i got wlan0 going through router, and now eth0, i would like to put eth0 on p2p, and currently my wlan is for the net.
  not sure how to configure routing table; i can only ifup one card at a time, so that other pc/router can see it. but when i put both up, things are messing up. 
route table:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
192.168.0.0     *               255.255.0.0     U     0      0        0 eth0
default         router           0.0.0.0         UG    0      0        0 wlan0
/etc/networks/interfaces


The primary network interface
iface wlan0 inet static
        address 192.168.0.5
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid 123456789
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 203.161.127.1 203.153.224.41

up iwconfig wlan0 rate 54M


#eth0

iface eth0  inet static
        address 192.168.1.6
        netmask 255.255.0.0
        network 192.168.1.0
        broadcast 192.168.0.255

EDIT:  the router is 192.168.0.1

please advise.
thanks!

---

### Post by [pl]ice on 2005-08-13
yeh, thnx to #ubuntu irc :]

subnets are wrong, should be:
 192,168,1,x for eg. wlan
for my other card 192,168,2,x on both boxes, then the router is 192,168,1,1 and all works, except i can't figure out firewall :]

hopefully it will help someone....

---

