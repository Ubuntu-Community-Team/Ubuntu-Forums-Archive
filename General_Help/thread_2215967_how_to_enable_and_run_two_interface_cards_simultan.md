---
title: "how to enable and run two interface cards simultaneously"
date: 2014-04-09
forum: General Help
---

### Post by sareesh on 2014-04-09
Hi....

     I am running varnish cache server in ubuntu 12.04 LTS Server. I want to install the server to be installed as a gateway for the AAA Management Server.For that,both the cards should be enabled and running simultaneously.I configured both the lan cards as static ip.At a time only one is active and working.Anybody Please help me to sort this issue.


Regards
Sareesh

---

### Post by apohal9 on 2014-04-09
Hi,

you're talking about having f.e. eth0 and eth1 connected? How did you configure them? Can you paste /etc/network/interfaces as well as output of "ip addr" and "ip route"?

---

### Post by sareesh on 2014-04-11
Hi....

       The details are below.

FOR IP ADDR

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 34:40:b5:86:b4:f0 brd ff:ff:ff:ff:ff:ff
    inet 103.254.128.4/28 brd 103.254.128.15 scope global eth0
    inet6 fe80::3640:b5ff:fe86:b4f0/64 scope link 
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 34:40:b5:86:b4:f1 brd ff:ff:ff:ff:ff:ff
    inet 172.100.100.1/24 brd 172.100.100.255 scope global eth1
    inet6 fe80::3640:b5ff:fe86:b4f1/64 scope link 
       valid_lft forever preferred_lft forever
4: usb0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 36:40:b5:86:b4:f3 brd ff:ff:ff:ff:ff:ff
    inet 169.254.95.120/16 brd 169.254.255.255 scope global usb0
    inet6 fe80::3440:b5ff:fe86:b4f3/64 scope link 
       valid_lft forever preferred_lft forever

_FOR IP ROUTE_


default via 103.254.128.1 dev eth0  metric 100 
103.254.128.0/28 dev eth0  proto kernel  scope link  src 103.254.128.4 
169.254.0.0/16 dev usb0  proto kernel  scope link  src 169.254.95.120  metric 1 
172.100.100.0/24 dev eth1  proto kernel  scope link  src 172.100.100.1 


Regards
Sareesh

---

### Post by apohal9 on 2014-04-15
Hi,

when you say only one works at a time, do you mean you can f.e. not access 172.100.100.1 when eth0 with 103.254.128.4 is up?

---

