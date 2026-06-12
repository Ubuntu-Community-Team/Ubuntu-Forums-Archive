---
title: "networking keeps breaking until reboot"
date: 2006-12-13
forum: General Help
---

### Post by pataphysician on 2006-12-13
my network/ing seems to have suddenly exploded. i can't establish a wireless connection at all, and my wired connection works but will randomly (after 10-60 minutes) stop. i can usually, but not all the time, renew the wired connection with dhclient or ifup; but after that i still can't communicate with anything. after the initial drop, i can't ping other machines on the local network by ip address (not even the dhcp server!).

if i try to restart networking, i get this:
```

# /etc/int.d/networking restart
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.

wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device

```

those devices don't exist on my system. the wired interface is eth0 and wireless is eth1. i've done /etc/int.d/networking restart before and not seen these errors. i don't know why it's all of the sudden trying to bring up interfaces that don't exist.

until about three days ago everything was working fine, including wireless which i used daily. i haven't made any changes or updated anything. it all just went haywire one day. anyone have any ideas on what i can do to restore networking?

---

