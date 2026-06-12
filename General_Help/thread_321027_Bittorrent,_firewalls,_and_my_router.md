---
title: "Bittorrent, firewalls, and my router"
date: 2006-12-18
forum: General Help
---

### Post by Pitbull11188 on 2006-12-18
I use bittornado and I never get a green circle, only yellow. I read up on what this means and it indicates that I am behind a firewall and therefore do not get optimal download/upload speeds and that I must rout bittorrent through the firewall or router. How do I go about doing this?

---

### Post by OffHand on 2006-12-18
> **Pitbull11188 said:**
> I use bittornado and I never get a green circle, only yellow. I read up on what this means and it indicates that I am behind a firewall and therefore do not get optimal download/upload speeds and that I must rout bittorrent through the firewall or router. How do I go about doing this?

Do you have a router? If you have a router you should configure your router. If your machine is connected directly to the internet you can install Firestarter (GUI for iptables) and configure your ports.

```
sudo apt-get install firestarter
```

---

### Post by hal10000 on 2006-12-18
Hi,
At [http://www.portforward.com/english/applications/port_forwarding/Tornado/Tornadoindex.htm]("http://www.portforward.com/english/applications/port_forwarding/Tornado/Tornadoindex.htm") there is (hopefully) a detailed instruction for your router and the software. I don't use bittornado, but with Azureus and my wlan router these instructions worked. You just have to fill out the forms and get the result at the bottom of the page.
Good luck.

---

### Post by OffHand on 2006-12-18
removed

---

### Post by katgfan on 2006-12-18
The suggestions above should work. If it didnt, please tell us your network setup on how you connect to internet  (e.g PC-switch-router-ISP, PC-dsl-ISP) and if you are using NAT.

---

