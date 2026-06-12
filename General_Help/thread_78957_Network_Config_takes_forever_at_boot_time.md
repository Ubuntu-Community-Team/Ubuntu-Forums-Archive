---
title: "Network Config takes forever at boot time"
date: 2005-10-19
forum: General Help
---

### Post by phanboy_iv on 2005-10-19
I have a laptop with a wireless connection. When I'm within range of a wireless network, this doesn't happen, but when there is no network to connect to, the boot up process pauses at "Configuring Network Interfaces" for a VERY long time before continuing. Is there a way to fix this?

---

### Post by dakira on 2005-10-19
This happens because during the network configuration ifup is trying to get a dhcp lease which is not possible since there are no networks. This takes some time.

You have two options:
1. Press CTRL+C when it says "Configuring network interfaces" to manually stop it, or
2. edit /etc/network/interfaces and remove/comment-out the line **auto eth1** (where eth1 is your WiFi interface). If it is there you can also comment-out auto eth0 since you are not using your LAN.

Now whenever you need to connect just do a *ifup eth1* (eth0 respectively).

And if you want to do it real nicely you should read through the documentation of the interfaces file and create a nice scripted one which automatically knows what to do and which network to connect to.

---

### Post by phanboy_iv on 2005-10-19
Thanks. The Ctrl+C method works for me.

---

