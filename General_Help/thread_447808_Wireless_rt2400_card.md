---
title: "Wireless rt2400 card"
date: 2007-05-18
forum: General Help
---

### Post by MaestroS on 2007-05-18
Can you tell me - step by step - how to install and setup internet connection with card Wireless RT 2400 (RaLink)

I were trying to use 'Network Manager', but when I fill all infos and checking it to enabled - system freezes...

Waiting for professional help - I want net !

---

### Post by Tranux on 2007-06-15
Hi,

I have got a rt2400 chipset based wireless card as well. Network-Manager and "old" RaLink drivers do not work together. I had to remove network-manager and modify my /etc/network/interfaces file. Now I have got internet access when my computer is booting.

```
 cat /etc/network/interfaces
auto lo
iface lo inet loopback

#rt2400
iface ra0 inet static
address 192.168.100.xxx
netmask 255.255.255.0
broadcast 192.168.100.255
gateway 192.168.100.1
up  /sbin/iwconfig ra0 mode Managed &&   /sbin/iwconfig ra0 key  XXXXXXXXXXXXXXXXXXXXXXX open &&   /sbin/iwconfig ra0 ap XX:XX:XX:XX:XX:XX &&   /sbin/iwconfig ra0 essid ESSID

auto ra0

```

Patrick

---

