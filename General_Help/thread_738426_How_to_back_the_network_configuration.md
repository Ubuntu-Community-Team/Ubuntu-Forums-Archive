---
title: "How to back the network configuration"
date: 2008-03-28
forum: General Help
---

### Post by MicroBoy on 2008-03-28
**I configurated the network but now I'm having some problems. Can I back the configurate as it was first when I installed "Ubuntu".**

---

### Post by seeker1458 on 2008-03-28
did you use Network Gui or edit the network interfaces file?

---

### Post by MicroBoy on 2008-03-28
> **seeker1458 said:**
> did you use Network Gui or edit the network interfaces file?More specific? i Configurate from terminate control ok

---

### Post by seeker1458 on 2008-03-28
sorry, did you set a static IP using the gui provided by System>Administration>Network.
or did you :
```
sudo gedit /etc/network/interfaces
```

---

### Post by seeker1458 on 2008-03-28
you should just be able to set everything back to dynamic like it was when you installed.

my /etc/network/interfaces file looks like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 172.16.1.5
netmask 255.255.255.0
network 172.16.1.0
broadcast 172.16.1.255
gateway 172.16.1.1
```

---

### Post by seeker1458 on 2008-03-28
When I tried setting a static IP using the gui, it did not create the network or the broadcast entries.  When I added them everything worked.

Just put xxx.xxx.xxx.0 for network and xxx.xxx.xxx.255 for broadcast.

---

### Post by MicroBoy on 2008-03-28
Ok Thnx

---

### Post by MicroBoy on 2008-03-30
**I need to back all the configurate. Does it have any Package that will back it all like in the first time.**

---

