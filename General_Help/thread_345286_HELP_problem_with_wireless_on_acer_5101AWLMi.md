---
title: "HELP: problem with wireless on acer 5101AWLMi"
date: 2007-01-24
forum: General Help
---

### Post by ghepardo on 2007-01-24
Hi,
following the guide on the ubuntu forums (ndiswrapper) I installed the drivers for my wireless card on an acer 5101awlmi.
THe problem now is that the card finds the wireless networks but it does not join them.
In ym configuration the wireless card is referred as ATH0 and not WLAN0 as stated in the guide.

Plz help me!!!

---

### Post by crispy_420 on 2007-01-24
Sounds like you have atheros chipset. If so don't even bother with ndiswrapper, your chipset has a linux driver. So this is very good news.

My laptop has the same driver and it just worked with no tweaking. In my opinion, I would look for a good network-manager guide. Takes some work to setup, but after that it is smooth sailing.

Here are some links to help you along:

[https://wiki.ubuntu.com/DapperNetworkManager?highlight=%28manager%29%7C%28network%29](https://wiki.ubuntu.com/DapperNetworkManager?highlight=%28manager%29%7C%28network%29)
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

Those should get you goning in the right direction...

---

