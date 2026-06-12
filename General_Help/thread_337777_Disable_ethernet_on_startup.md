---
title: "Disable ethernet on startup"
date: 2007-01-13
forum: General Help
---

### Post by Burgresso on 2007-01-13
I'm trying to disable my ethernet connection (I don't use it) by default on startup. I use a wireless connection. The ethernet card is part of the MOBO. 

I can manually disable it by system->Admin->networking tools, but I must do it everytime.

Sometimes my wireless acts funny, and I would like to disable the ethernet by default to help troubleshoot next time it acts up. I want to be sure its not using the wrong connection if both wireless and ethernet are disabled.

Here is my /etc/network/interfaces:

```

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




iface ra0 inet dhcp
wireless-essid [mynetwork]
wireless-key [mykey]

auto ra0

```

thank you so much,

burgresso

---

### Post by dcstar on 2007-01-13
> **Burgresso said:**
> I'm trying to disable my ethernet connection (I don't use it) by default on startup. I use a wireless connection. The ethernet card is part of the MOBO. 

I can manually disable it by system->Admin->networking tools, but I must do it everytime.

Sometimes my wireless acts funny, and I would like to disable the ethernet by default to help troubleshoot next time it acts up. I want to be sure its not using the wrong connection if both wireless and ethernet are disabled.

Here is my /etc/network/interfaces:

```

auto lo
iface lo inet loopback


[B]iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp[/B]

auto ath0
iface ath0 inet dhcp
.......

```

thank you so much,

burgresso

Comment out all of the "eth" entries.

---

### Post by Hub-1 on 2007-01-13
nevermind :)

---

### Post by dcstar on 2007-01-13
> **Hub-1 said:**
> An other solution would be to disable the networking script in the startup folder. 
......

Which would also disable the Wireless networking that is in use...........

---

### Post by Hub-1 on 2007-01-13
> **dcstar said:**
> Which would also disable the Wireless networking that is in use...........

Oops this is true.

---

### Post by Burgresso on 2007-01-15
Thanks dcstar, it seemed to do the trick.

---

### Post by paulyche on 2007-01-15
You can probably also disable the card in the computer's BIOS....

---

