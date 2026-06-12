---
title: "Wireless network does not get an IP from DHCP wireless Router"
date: 2006-10-24
forum: General Help
---

### Post by moodys on 2006-10-24
I have installed Ubuntu Dapper Drake its working fine and everything is super fine just one glitch which keeps bugging me like hell man.
I can detect my wireless connection and the signal strength is super i.e 80/100 when iwconfig  my wireless card.But the problem is I cannot get an IP address from the wireless router and before I used to get and Ip address from the same router.
Please can anyone come up with a solution for this problem please I need an urgent feedback.
Will appreciate to get help from Ubuntu Gurus !!!!!!!
Best regards
Moody.

---

### Post by wieman01 on 2006-10-24
Please run these commands from a terminal windows and post the results:
> iwconfig
> iwlist scan
> route
> sudo gedit /etc/resolv.conf
> sudo gedit /etc/network/interfaces
> sudo /etc/init.d/networking restart
_Then please answer these questions:_
1. Have you configured IP tables (= firewall) recently or installed Firestarter?
2. Have you changed any settings on the router (e.g. security, static IP leases)?
3. Have you installed NetworkManager or Wifi-Radar?

---

