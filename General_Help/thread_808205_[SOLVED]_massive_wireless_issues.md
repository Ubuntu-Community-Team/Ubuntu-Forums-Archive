---
title: "[SOLVED] massive wireless issues"
date: 2008-05-26
forum: General Help
---

### Post by werries on 2008-05-26
Ok. So I installed Ubuntu Hardy Heron on my desktop. The only problem is internet.
I have a texas instruments acx 111 for my wireless card.

Using the newer nm-applet and network-manager, internet does not work at all. in fact, it manages to freeze my whole computer.
I finally figured out that wpasupplicant is not supported by my wireless driver and had to downgrade to .5 instead of .6 because it simply wouldn't work. 

However, with this, on certain startups, it tries to connect to a wired network, but i have no ethernet cable plugged in. other times, it doesnt detect a driver for anything. and other times, it works fine and i just input the WEP key and its fine, but the icon freezes up and i can't tell my signal/connection info. Not to mention update manager trying to update it and last time i tried updating it, it broke again (as in, froze).
I'm not sure what to do here, i'd like a more stable wireless connection. 

Maybe a good stable way to manager without nm-applet? or maybe support for my driver with wpasupplicant? (acx_pci).
Maybe manual configuration? (i tried stopping the nm-applet and network manager and just using the terminal, but sudo iwconfig essid <mynetwork> key <mykey> didnt properly make internet work, even though it assigned the correct essid/key.

help?

---

### Post by nick_h on 2008-05-26
You could configure you network manually in /etc/network/interfaces.

For WPA have a look at - [HowTo: WPA with wpa_supplicant](http://ubuntuforums.org/showthread.php?t=263136).

---

### Post by werries on 2008-05-26
alright. ill try that. how do i disable network-manager tho

---

### Post by werries on 2008-05-26
my /etc/network/interfaces
```
auto lo
iface lo inet loopback
```

so how do i change that to use my wireless connection only(as it tries to connect to wired w/o ethernet plugged in), and how do i set it up for my network with my open WEP key(not shared) and do i have to disable network-manager or will this override it?

---

### Post by nick_h on 2008-05-26
> how do i disable network-manager
There is a section in the [NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) page in the community docs.

> so how do i change that to use my wireless connection only
You will need to add a section for your network card.  For WPA, something like:

```
iface wlan0 inet dhcp
wpa-driver acx_pci
wpa-conf /etc/wpa_supplicant.conf
```

This assumes dhcp, and a device name wlan0.

---

### Post by werries on 2008-05-26
ah. so DHCP auto-assigns ip and such, correct?
but i only need wep, not wpa. Do i actually need to disable network manager?

---

### Post by nick_h on 2008-05-26
> so DHCP auto-assigns ip and such, correct?
Yes.
> but i only need wep, not wpa.
Then you need something like:
```
iface wlan0 inet dhcp
wireless-essid <essid>
wireless-key <key>
```

> Do i actually need to disable network manager?
I'm not sure.

---

### Post by werries on 2008-05-26
well. thanks so much. ill try it with network manager still enabled, and if its still broken, then ill disable it.

---

### Post by werries on 2008-05-26
so i did it. added that into /etc/network/interfaces, but with <key> as 6121245337 and <essid> as 2WIRE962. tried to connect, but firefox was apparently in offline mode. So i disabled network manager. no connect. reboot. no connect.
here is my /etc/network/interfaces
```
auto lo
iface lo inet loopback
iface wlan0 inet dhcp
wireless-essid 2WIRE962
wireless-key 6121245337
```

---

### Post by werries on 2008-05-26
ok so it wasn't working, so i ran
```
sudo iwconfig wlan0 essid 2WIRE962 key 6121245337 && sudo dhclient wlan0 
```
and it connected. woot.
however, on boot, it didnt work. i dont think the interfaces was correctly connecting. so, 1. why isnt the /etc/network/interfaces working, and 2. how do i made dhclient wlan0 run at startup so it connects?

---

### Post by nick_h on 2008-05-27
Try adding the following line to your /etc/network/interfaces file:
```
auto wlan0
```

---

### Post by werries on 2008-06-02
yes, this worked. lol sorry about slow response, i forgot about this thread after it worked. marking as solved.

---

