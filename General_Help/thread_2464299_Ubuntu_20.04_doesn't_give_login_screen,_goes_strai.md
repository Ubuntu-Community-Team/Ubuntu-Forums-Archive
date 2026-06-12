---
title: "Ubuntu 20.04 doesn't give login screen, goes straight to recovery terminal"
date: 2021-06-28
forum: General Help
---

### Post by mysteriousmonkey29 on 2021-06-28
Hello, I was installing someone else's build environment on my ubuntu 20.04 machine via a bashscript, but apparently something went screwy and my computer now wont display the login screen. It boots straight to the recovery terminal. It boots up into the terminal, says:

"psmouse serio1: synaptics: unable to query device: -71" and asks for my login. I am able to log in, but I'm not sure how to ge the GUI back.

I have seen some suggestions to reinstall the unity desktop with:

[FONT=&quot]sudo apt install ubuntu-unity-desktop

Unfortunately, I cannot install this (or anything) as the internet is also broken, and I'm not sure how to get it back. I have an ethernet connection (I figure this will be easier than wifi), but no internet access. I tried to turn on the ethernet with:

sudo ifconfig enp60s0 up, but to no avail.

ifconfig -a gives:

enp60s0: flags=409<BROADCAST,MULTICAST> mtu 1500
    ether <mac address> txqueuelen 1000 (ethernet)
    RX packets 92 bytes 6174
    RX errors 0
    TX packets 25 bytes 2969
    TX errors 0
    
but no ip address.

I am unable to ping google.com (get "temporary failure in name resolution"), or 8.8.8.8 (get "network is unreachable")

"ip link" gives:

2: enp60s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether <mac address> ff:ff:ff:ff:ff:ff

Any idea how to get the GUI and/or the internet back?

I am running kernel 5.9.10-0509210-generic

Thanks!

[/FONT]

---

### Post by mysteriousmonkey29 on 2021-06-28
Ended up fixing it with:

sudo ifconfig enp60s0 up
sudo dhclient enp60s0

which connected to the internet. Then I was able to do:

sudo apt install --fix-broken

which installed almost everything I was missing.

---

