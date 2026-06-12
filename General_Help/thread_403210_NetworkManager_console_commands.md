---
title: "NetworkManager console commands?"
date: 2007-04-06
forum: General Help
---

### Post by brottman on 2007-04-06
When I boot either a Edgy or Feisty CD on my laptop, X does not work properly. To fix it, I need to be able to get online with my wireless to download the nvidia-glx package.  My problem though, is that with Feisty, since I can't get to the GUI, I have no access to my wireless network. So on to the question:

Is there a way to control NetworkManager with console commands to tell it to connect to my wiress network?

---

### Post by kpkeerthi on 2007-04-06
I don't think so. Wire your PC to the modem and do the repair.

---

### Post by zvacet on 2007-04-07
```
sudo ifup eth0
sudo ifdown eth0
sudo ifup etho
```
replace eth0 with ath0 or whatever you use to define your wireless.You can also try 
```
pon dsl-provider
```

---

