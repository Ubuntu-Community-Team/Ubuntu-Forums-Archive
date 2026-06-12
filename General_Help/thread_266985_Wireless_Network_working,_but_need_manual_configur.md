---
title: "Wireless Network working, but need manual configuration everytime"
date: 2006-09-28
forum: General Help
---

### Post by inkybutton on 2006-09-28
Hi,
I can now access my wireless network through my Wifi USB card. However:

1. It is ran under the "Restricted" security mode, which means I will have to write ```
sudo iwconfig wlan0 key restricted
``` everytime I want to go the computer. What do I write to the /etc/network/interfaces file in order to achieve the same effect?

2. After typing ```
sudo iwconfig wlan0 key restricted [password]
```, I will always have to go into System > Administration > Networking and activate the interface wlan0 before I can connect to the internet. However, after I type ```
sudo iwconfig wlan0 key restricted [password]
```, ```
sudo iwevent
``` tells me that the hardware address of my access point is found. But still internet until I go into System > Administration > Networking. Any ideas? Greatly appreciated.

---

