---
title: "Making use of Wireless 4G - help needed !"
date: 2017-08-12
forum: General Help
---

### Post by Timmoore001 on 2017-08-12
I use Ubuntu 16.04 64 bit and a wireless  MiFi for internet using 4G.   This is massively better than the pathic landline speed of 2MB/s also better the the landline speed will be if we ever get the option of having it available.

the signal is great for the room with the computer in, but the wifi not so special in the rest of the house.

I'm told that if my desktop receives a strong signal it could share it via the ethernet port to other computers....  (i did this successfully using windows 98 many years ago !)

Anybody any ideas how I can do this with Linux ?  I'm not a Windows fan !

Any thoughts anyone?

:  )))

Tim

---

### Post by efflandt on 2017-08-12
I did that many years ago using dial up networking and sharing that connection to up to 2 other computers using ppp over serial (before USB) or plip over parallel ports (using ipchains). And when I first got DSL with a bridge modem, I used one PC with 3 nics, one for pppoe with modem, one for LAN, and one proxy_arp to a wireless AP, so that would work as part of main LAN (maybe using iptables). But I have not done that since I got a DSL gateway (wireless/router/modem).

A quick web search of "sharing an internet connection in ubuntu" brought up the following, among other things:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
And one about 16.04 referencing [https://askubuntu.com/questions/169473/sharing-connection-to-other-pcs-via-wired-ethernet](https://askubuntu.com/questions/169473/sharing-connection-to-other-pcs-via-wired-ethernet) that may provide additional clues.

In your case you need to share your mobile data device.

---

### Post by Timmoore001 on 2017-08-14
Many thanks for responding.

 Most interesting...   I shall do my best to get this working...

:  )))

Tim

---

