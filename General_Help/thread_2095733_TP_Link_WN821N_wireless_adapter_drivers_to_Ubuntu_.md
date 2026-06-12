---
title: "TP Link WN821N wireless adapter drivers to Ubuntu 12.10. PLEASE"
date: 2012-12-17
forum: General Help
---

### Post by dawid177 on 2012-12-17
Hi, Can someone send me drivers for TP Link WN821N wireless adapter for Ubuntu 12.10, or explain step by step how to instal that staff. Im beginner as a ubuntu user.

Regards

Dawid

---

### Post by slixz85 on 2012-12-17
hmm. [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link) shows that your usb dongle is supported. try to type "ifconfig" and "iwconfig" in terminal and see if it finds it that way. it should say wlan0 or wlan1 something like that. if you see a wlan0 or wlan1 depending on which one in terminal type sudo iwlist scan and see if it finds networks. need to know this much since the ubuntu site shows it is supported. also found this website but from a previous ubuntu 10.10 but if you kinda know your ways around computers it could help [http://myubuntunotes.wordpress.com/2011/03/03/hello-world/](http://myubuntunotes.wordpress.com/2011/03/03/hello-world/)

---

### Post by slixz85 on 2012-12-17
also in case it does find your wireless using wlan0 I would just install wicd to test it out from terminal. sudo apt-get install wicd then open it. it wont show anything connected just click preferences and under wireless put wlan0 or wlan1 IF ifconfig pulls back a connection then hit refresh. i just need to know this much cause i will help ya but sometimes wireless is a pain

---

