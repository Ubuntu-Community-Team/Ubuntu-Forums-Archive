---
title: "Wireless works in gnome but not KDE"
date: 2006-12-09
forum: General Help
---

### Post by bigblop on 2006-12-09
I am using Ubuntu 6.10. I have installed network-manager-gnome which makes my wireless work in gnome (connecting an IBM T/40p to a Linksys GL router).

But it does not work in KDE. I have tried to run wlassistan, knetworkmanager, kwifimanager but that does not help either.

I have also tried running NetworkManager in KDE but that does not work either. I was told to out comment all lines in /etc/network/interfaces besides from lines containing 'lo' so my interfaces file looks like this:

auto lo
iface lo inet loopback

and all the other lines are outcommented.

Can anyone help me getting wlan to work in KDE eventhough it works in gnome?

---

### Post by gb5757870 on 2006-12-26
Hey. Have you tried KNetworkManager? My network uses WPA PSK TKIP and besides having to connect manually everytime I login,  it's great!

---

