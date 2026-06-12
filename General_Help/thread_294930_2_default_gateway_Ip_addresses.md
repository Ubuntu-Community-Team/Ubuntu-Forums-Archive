---
title: "2 default gateway Ip addresses?"
date: 2006-11-07
forum: General Help
---

### Post by while on 2006-11-07
the syustem I have has 2 nics and I want to use one as primary and the second one as a backup (primary wired, backup wireless) (laptop) how can i have them both up and used and set this up? I have tried addingthe gateway with a higher metric but that has only caused me issues and when the wireless comes up it seems to either cause issues or take over the default route.... 

How can I make this perminant as a secondary gateway. So if I undoc it just uses the wireless? 


Thanks 


William

---

### Post by michux on 2006-11-07
> **while said:**
> the syustem I have has 2 nics and I want to use one as primary and the second one as a backup (primary wired, backup wireless) (laptop) how can i have them both up and used and set this up? I have tried addingthe gateway with a higher metric but that has only caused me issues and when the wireless comes up it seems to either cause issues or take over the default route.... 

How can I make this perminant as a secondary gateway. So if I undoc it just uses the wireless? 

Of course it is possible to do. It just requires a few tweaks in /etc/network/interfaces. I found a guide that may be helpful to you: [http://www.debuntu.org/2006/02/23/8-using-multiple-network-device-to-connect-to-the-internet](http://www.debuntu.org/2006/02/23/8-using-multiple-network-device-to-connect-to-the-internet)

michuk

---

### Post by spd106 on 2006-11-07
Have you tried network-manager? [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

It only works with dhcp and encrypted networks at the moment.

---

### Post by while on 2006-11-07
currently running static IP on the wired and dhcp on the wireless.. 

So I guess not.. I know there has to be a way to do it... it is after all simple routing lol 



> **spd106 said:**
> Have you tried network-manager? [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

It only works with dhcp and encrypted networks at the moment.

---

