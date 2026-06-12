---
title: "How do I use WPA encryption?"
date: 2006-08-03
forum: General Help
---

### Post by Face1 on 2006-08-03
I am in a place where there is a wireless network secured with WPA pre-shared key encryption using TKIP.  I would like to connect to the network, but in the Wireless Assistant in the part for providing a key, it only asks which WEP mode I want to use.  How do I use WPA?  

Thank you very much.

---

### Post by hw-tph on 2006-08-03
The by far easiest way is by installing network-manager. It will show up as a tray icon and from that you can choose to connect to all available networks - wired and wireless, unencrypted or encrypted using WEP or WPA. Works great for me.


Håkan

---

### Post by Face1 on 2006-08-03
For some reason, the network monitor only shows the grayed out option "Wired networking" when I left click on it (it is not currently plugged in to LAN), And when I right click I have the following:[LIST]
[*]Enable networking (checked)
[*]Connection Info (grayed out)
[*]About
[*]Remove
[/LIST]
What should I do?

---

### Post by hw-tph on 2006-08-03
So is your wireless network card set up and working? Can you scan for networks (**sudo iwlist eth1 scan** - replace eth1 with the device name of your network card).


Håkan

---

### Post by Face1 on 2006-08-03
Yes, it is.  If I disable the security features of the network I can get on, and I can view the list of all of the wireless networks nearby with Wireless Assistant.

---

### Post by NeoChaosX on 2006-08-03
If NetworkManager isn't showing any wireless networks, show the contents of your /etc/network/interfaces file.

---

### Post by Face1 on 2006-08-04
```
#The loopback network interface
auto lo
iface lo inet loopback

#the primary network interface
autoeth0
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid EvansHomeNetwork

auto eth1
```

eth1 is my wireless interface, and EvansHomeNetwork is my wireless network at home, don't know why that is there.

---

### Post by NeoChaosX on 2006-08-04
Remove everything in that file except the stuff related to lo, and reboot your computer. Then you should be able to use NetworkManager with your wireless connection, which will allow you to use WPA encryption. The Ubuntu version of NM doesn't use any hardware that's defined in the interfaces file.

---

### Post by Face1 on 2006-08-04
That did the trick. Thanks!

---

