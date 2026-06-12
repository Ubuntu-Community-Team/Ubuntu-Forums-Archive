---
title: "disabling eth0 interface in gnome"
date: 2007-12-14
forum: General Help
---

### Post by zivxx on 2007-12-14
hey everyone, i got 2 network cards and seems to make my computer lag while the interfaces of both are enbaled,in KDE i just disabled the eth0 wich was 2 clicks work, but in Gnome i can't find the way to do that...anyone know?

---

### Post by zvacet on 2007-12-14
**network manager>manual configuration>untick card of your choice**

or you can 

```
sudo gedit /etc/network/interfaces
```

and put # in front of eth0 line

---

### Post by zivxx on 2007-12-14
thats ALL in that file,
auto lo
iface lo inet loopback


EDIT:
it looks like that now,
#auto lo
#iface lo inet loopback












#iface eth0 inet static
address 192.168.123.254
netmask 255.255.255.0


but i still seem that the interface is not disabled, also to proof myself this is the problem i right clicked the comp couple symbol and disabled networking and it worked perfectly

---

