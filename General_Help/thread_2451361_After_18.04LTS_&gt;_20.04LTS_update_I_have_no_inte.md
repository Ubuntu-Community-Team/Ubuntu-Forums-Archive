---
title: "After 18.04LTS &gt; 20.04LTS update I have no internet connection except with live DVD"
date: 2020-10-02
forum: General Help
---

### Post by cpollock on 2020-10-02
Software manager notified me Wednesday that the update to 20.04.1 was  available. I ran the update and saw no issues during it. After the  restart I had no internet connection. I'm connected via Ethernet. I  installed a new Ethernet cable however still no internet. I booted into a  live session (which I'm using now) and internet works perfectly. I've  not had this problem with any of my other LTS upgrades and not being  well versed on networking I really don't know what/where to check. I'm  connected directly from the desktop to the DSL modem. The computer is a  Dell Optiplex 780 with updated BIOS. Any suggestions would be  appreciated. I've added the output of ip addr for both the desktop and the live session in case it helps.

This is for the desktop:
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:25:64:c7:b1:e4 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.220/24 brd 192.168.0.255 scope global dynamic noprefixroute eth0
       valid_lft 85970sec preferred_lft 85970sec
    inet6 fd00::7840:a306:cba2:e630/64 scope global temporary dynamic 
       valid_lft 604372sec preferred_lft 85881sec
    inet6 fd00::bb65:4a5:a5fa:2a4b/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 2591940sec preferred_lft 604740sec
    inet6 fe80::f0a1:dfc9:9682:7696/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```

This is for the live session:
```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:25:64:c7:b1:e4 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.220/24 brd 192.168.0.255 scope global dynamic noprefixroute enp0s25
       valid_lft 85170sec preferred_lft 85170sec
    inet6 fd00::30b9:bf37:5969:968f/64 scope global temporary dynamic 
       valid_lft 603572sec preferred_lft 85009sec
    inet6 fd00::1d08:815c:4808:7806/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 2591964sec preferred_lft 604764sec
    inet6 fe80::cadf:f9f1:e66b:cf14/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


```

---

### Post by cpollock on 2020-10-03
This thread can be marked as solved. The network suddenly came back up late last night for no reason that I could find.

---

