---
title: "Monitor wifi traffic"
date: 2018-10-14
forum: General Help
---

### Post by raleigh3 on 2018-10-14
I am trying to monitor wifi traffic from modem to a Roku stick.

I have used both bmon and slurm, but none seem to see the right connection.

wireless mac address is D8:31:34:48:38:88.

```
andy@7_~/Downloads$ ifconfig -a
enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.2  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::3340:8121:de10:5e6c  prefixlen 64  scopeid 0x20<link>
        ether 40:8d:5c:44:af:9b  txqueuelen 1000  (Ethernet)
        RX packets 130530  bytes 172312422 (172.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 80005  bytes 8642523 (8.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 4489  bytes 319529 (319.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4489  bytes 319529 (319.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether f8:1a:67:1d:ef:a2  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

---

### Post by gdesilva on 2018-10-15
Haven't used bmon or slurm but I know Wireshark can be set up in promiscuous mode to monitor wifi.

---

