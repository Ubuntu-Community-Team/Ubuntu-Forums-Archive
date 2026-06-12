---
title: "wireless networking with NetworkManager"
date: 2006-08-31
forum: General Help
---

### Post by m0untainrebel on 2006-08-31
i'm using ubuntu dapper, and i'm using ndiswrapper for my wireless driver.

my network at home uses WPA encryption, and so i followed the ubuntu WPA howto ([https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)) and installed NetworkManager.

right now NetworkManager works fine for my encrypted network at home, but any other unsecure wireless networks at coffeeshops and such don't work with NetworkManager.  they show up when i click on the icon, but when i click on them they never succeed in connecting.  to connect to them i have to run the network-admin ubuntu GUI (System -> Administration -> Networking) and connect that way, and then it works.

but before i can connect to my home WPA network again i have to go back to network-admin and unconfigure my networks, then i have to edit /etc/network/interfaces and delete any auto connection code that network-admin added, and reboot, and then i can use NetworkManager to connect.

what i want is for NetworkManager to work for all my network connections, not just the encrypted WPA one.  does anyone know why this might be happening?  thanks.

---

### Post by phyre-x on 2006-09-09
i have the exact same problem and still no solution, must be a bug with network manager for certain cards or drivers, i can use system>networking to connect to unsecured just the same as yourself but networkmanager applet will not. if i find anything i'll share it.

---

### Post by SishGupta on 2006-09-09
Your problem might be that you followed that guide.
I use network manager and I'd say that half of the instructions in that guide are useless.

To use network manager and WPA all you have to do is install network manager and wpasuppliclant (this one might allready be installed, it was for me). Network manager handles EVERYTHING ELSE except setting a static IP. It handles wpasupplicant 100% and it will handle dhcp.

there is no need edit your /etc/wpa_supplicant.conf, but there is some need to edit your /etc/network/interfaces. Mine looks like this and yours should be similar for using NM:
```
auto lo
iface lo inet loopback
```

When you try to connect to a network, nm will attempt to connect, it the connection is encrypted it will ask for a password and tell you what encryption it is, then it will automatically use wpa_supplicant for the connection.

If you want a static IP then you need to edit some files but i never use a static ip so i dont know much about it.

For informational purposes, I use an atheros based card.

Also you should try using the latest stable network manager from [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/). This solved the infamous connection drop during AP scan for me.

---

### Post by orb9220 on 2006-09-09
To get it to work I also had to edit my /etc/network/interfaces
and comment out everything except the lo one at the top.

---

### Post by mchatel on 2006-09-14
I've never been able to get Network Manager working under Dapper, with my current hardware configuration.  I've tried letting Network Manager do all the handling/settings for my wireless network.  I wanted to use Network Manager, so I could use the WPA encryption on my home network.  I've had to stick with WEP, using the Network Monitor utility instead (not Network Manager).

In my case...  I have a sneaking suspicion that it's related to my having to use Ndiswrapper with my wireless chipset (a Broadcom 4311).  I have a functioning wireless network, if I stay away from Network Manager and WPA, for now.  Hopefully, they will improve it, in the near future.  It would be a nice utility to use.

---

