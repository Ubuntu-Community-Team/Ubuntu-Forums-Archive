---
title: "WiFi network issues on xubuntu 22.04"
date: 2024-09-01
forum: General Help
---

### Post by 94fg on 2024-09-01
Hi all, 
I recently installed xubuntu 22.04 on my old asus laptop, which was previously running on windows os.

Since then, I've had serious connection issues when using Wifi, which make the system basically unusable. Using an ethernet cable seems to work fine instead.
There are times when for a couple minutes I have good performance with Wifi as well, but it goes back to not functioning: when I try to connect to websites, I get "server not found" error.

I get these statistics when running ping google.com using wifi connection:
--- google.com ping statistics ---
21 packets transmitted, 12 received, 42.8571% packet loss, time 20513ms
rtt min/avg/max/mdev = 5.064/66.463/736.227/201.942 ms

My wifi adapter is  Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter

Thanks!

---

### Post by currentshaft on 2024-09-01
What troubleshooting have you already done? Does the problem happen on all wireless network or just yours?

---

### Post by 94fg on 2024-09-01
Hi! The problem seems to happen on all wireless network, I tried with my mobile connection as well. 
What I tried is:
- disable ipv6
- check that there is no firewall
- disable power management for the wifi interface
- rebooting each time

---

