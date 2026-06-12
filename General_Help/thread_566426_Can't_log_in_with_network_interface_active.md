---
title: "Can't log in with network interface active"
date: 2007-10-03
forum: General Help
---

### Post by Nymo on 2007-10-03
I can't log in unless I unplug the ethernet cable and unactivate the wifi-card.

Do anyone have a clue?

---

### Post by cubeist on 2007-10-03
I have had a similar problem in the past... I just can't remember how I fixed it... Lets try your interfaces file first.  Can you post the output of "cat /etc/network/interfaces" (just type that into the terminal without the quotes)

Also could you post the output of your /var/log/kern.log file.  Not the whole thing though! Because they are super long!  Just post the results from the last time you tried booting up!!

---

### Post by Nymo on 2007-10-03
Hi.

The interface file is like this:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

I noticed that when I have commented out eth0(My ethernet card) and eth1(my wlan card), then there is no prob, but again, the wireless doesn't work properly in network manager.

---

### Post by cubeist on 2007-10-03
try commenting out everything except

auto lo
iface lo inet loopback

but FIRST! make a backup by typing in the terminal sudo cp /etc/network/interfaces /etc/network/interfaces.orig

then edit the interfaces file with nano in the terminal... I have found that using gedit causes boot problems...

---

### Post by Nymo on 2007-10-03
Thank you so much :D

No it works totally fine:D

---

### Post by cubeist on 2007-10-03
no problem... I have no idea why that seems to fix a lot of network problems... I think if everything is commented out then the network manager has free reign to control all aspects of the network... when mine was broken a while back that fixed it perfectly for me too...

---

