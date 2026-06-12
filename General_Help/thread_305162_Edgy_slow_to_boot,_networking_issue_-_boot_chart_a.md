---
title: "Edgy slow to boot, networking issue? - boot chart attached"
date: 2006-11-22
forum: General Help
---

### Post by JSVH on 2006-11-22
The attached boot chart pretty much speaks for itself. It looks like it is something with networking, probably wireless related. The boot does not take this long all the time, and I dont have any other problems besides the slow boot. My laptop is a Dell Inspiron e1505, with a intel 3945 A/G wifi card. 

Anyone have any ideas how to solve this? Edgy takes embarrassingly long to boot.

---

### Post by iamhugeinjapan on 2006-11-22
Are you able to give yourself a static ip?

---

### Post by creaturex on 2006-11-23
If it hangs during a specific part of the boot sequence (often times configuring network interfaces), you can always hit ctrl+c to skip that process, and allow it to configure after bootup which would probably be faster. Also, make sure the config files for your interfaces aren't messed up or wrong.

---

### Post by JSVH on 2006-11-23
> Are you able to give yourself a static ip?

Not really, with this laptop I am always on the go. I am connecting to different wireless networks all the time.

> Also, make sure the config files for your interfaces aren't messed up or wrong.

My /etc/network/interfaces looks normal enough:

```
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


```

I am using network-manager if that makes a difference.


Thanks for everyones help!

---

### Post by flar_p on 2006-11-29
If you are using networkmanager you should comment out all interfaces in /etc/network/interfaces except the lo interface. So the network interface will not be tried start at boot. Networkmanager will start the interfaces need by itself.

Hopes this helps.

Greetings

Flar

---

