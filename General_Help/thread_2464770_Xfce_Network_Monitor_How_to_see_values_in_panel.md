---
title: "Xfce Network Monitor: How to see values in panel?"
date: 2021-07-11
forum: General Help
---

### Post by josefranw on 2021-07-11
Hello.

What "network device" should I put in the corresponding field of the Network Monitor Applet on XFCE for the values to show in the panel?

I am using Internet via Bluetooth.

---

### Post by Dennis N on 2021-07-11
To find the name of network device, use terminal command **ip address**
In the example below, the name(s) are right after the number(s). Ignore the one named 'lo'. and use the other. Here it's **enp1s0**. That's what you type in (yours may be different, of course).

```
dmn@Sydney-vm:~$ ip address
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: **[COLOR="#FF0000"]enp1s0[/COLOR]**: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 52:54:00:3a:bc:c0 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.56/24 brd 192.168.122.255 scope global dynamic noprefixroute enp1s0
       valid_lft 2977sec preferred_lft 2977sec
    inet6 fe80::6e72:4deb:8569:706f/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```

---

