---
title: "Dell Wireless Problem!"
date: 2007-01-10
forum: General Help
---

### Post by Mr Underhill on 2007-01-10
Help!

Getting a really irritating problem.

Loaded Ubuntu 6.10 on a DELL Latitude D820, with an Intel WLAN IWP3945.

I loaded NetworkManager (NM), and can now see my Netgear AP, amongst others.

The AP does not, and cannot, act as a DHCP server.

If I click on the network in NM (v6.3) I can see my laptop in the AP Station List ...but I have no IP address.

If I manually assign a Static IP address, either by directly editing the interfaces file OR via the applett, NM no longer detects any wireless networks; and the "Enable Wireless" option is not available in NM.

Been going round in circles, any suggestions gratefully accepted!

Martin

---

### Post by groggyboy on 2007-01-10
have you edited the file "/etc/network/interfaces" ("gksu gedit /etc/network/interfaces" from the terminal)?  the only lines in the file should be these:```
auto lo
iface lo inet loopback
```
this is so gnome's built-in network app doesn't interfere with NetworkManager.  If you do have to edit/remove entries from that file, run "/etc/init.d/networking restart" from the terminal afterwards to restart your networking (or just reboot the whole computer).  Hopefully that'll help.

there's a [wiki page]("http://https://help.ubuntu.com/community/WifiDocs/NetworkManager") over at Ubuntu Documentation with more info on NetworkManager, which might be worth your time.

good luck and have fun!  ;)

---

