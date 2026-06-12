---
title: "NetworkManager not recognizing wireless card."
date: 2006-10-01
forum: General Help
---

### Post by tscook on 2006-10-01
Irrespective of the fact it has worked until yesterday, NetworkManager seems to refuse to recognize the fact I have a wireless card while I can still connect to various wifi networks with Network Monitor. It will still recognize the fact I am plugged in directly to the router.  Anywhere I should  start?  Unfortunately I have no idea what I did to bring this upon me.

---

### Post by orb9220 on 2006-10-02
open term enter the following.
gksudo gedit /etc/network/interfaces

Put a # in front of all entries except the one titled auto lo
save and reboot.

This is mine

> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp
#wireless-essid [www.personaltelco.net](www.personaltelco.net)

#auto wlan0
#iface wlan0 inet dhcp

---

### Post by tscook on 2006-10-02
Worked like a charm, thank you.

---

### Post by landotter on 2006-10-14
This helped me immensely. A perfect simple thread and solution. Should be stickied if the forum  allows.


:-D

---

### Post by hornett on 2006-10-27
Agreed! This got nm working for me also, thanks.

---

### Post by orb9220 on 2006-10-27
Well this is pretty well known and has multiple threads. The secret is to search on keyword nm-applet to find solution.

And since you are new I say Welcome and now you are required to:

"Sacrifice one Virgin MS employee to the Fires of the Goddess Ubuntu!"

---

