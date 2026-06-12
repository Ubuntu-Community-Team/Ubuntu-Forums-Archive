---
title: "Ubuntu 13.04 static IP not working"
date: 2013-06-13
forum: General Help
---

### Post by Higgins909 on 2013-06-13
I have recently went from some 11.?? to 13.04 and am having the hardest time getting a static ip to work

(I tried tasksel to get ubuntu desktop to bridge newly inserted wifi card with lan and then tried removing and it died...(with tasksel, unchecked it and hit ok)


sudo nano /etc/network/interfaces


auto lo
iface lo inet loopback

#LAN
#auto eth0
#iface eth0 inet static
#tab address 192.168.0.99
#tab netmask 255.255.255.0
#tab gateway 192.168.0.1
#tab dns-nameservers 8.8.4.4, 8.8.8.8

#WiFi
autowlan0
iface wlan0 inet static
tab address 192.168.0.100
tab netmask 255.255.255.0
tab dns-nameservers 8.8.4.4, 8.8.8.8
tab wpa-ssid MYsetSSID
tab wpa-psk MYsetPASSWORD


tab is where I put tabs, could not press tab in this typing box

thats what my file looks like it was working fine till I tried adding in eth0 and setting the wifi to static (wifi was just wpa-ssid and wpa-psk)

Can use the help!
have been trying dozens of setups to no anvil, and for 2+ hours


Thanks,
Higgins909

---

### Post by newbie-user on 2013-06-13
there should be a space in auto wlan0

---

### Post by HiImTye on 2013-06-13
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
are you still using NetworkManager? if so, you have to configure it in there
[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

---

