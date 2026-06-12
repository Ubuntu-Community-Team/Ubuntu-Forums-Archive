---
title: "Network card speed"
date: 2004-11-16
forum: General Help
---

### Post by russx2 on 2004-11-16
Hello,

Having a great time with Ubuntu (warty) at the moment except for one problem. Basically, my network cable is a little twisted in places which means it will only run at 10baseT speeds reliably (running at 100 just won't work). Obviously I plan to get a new cable in the future but for now I'd be happy with it just running at 10.

Is there a nice config file that I can edit to force the speed to 10?

At the moment I have to wait about a minute for it to fail detecting the network (DHCP) on bootup, then do a 'mii-diag eth0 -F 10baseT-FD' and then wait a bit longer for it to pickup.

Any advice/solutions greatly appreciated,

Thanks,
Russ

---

### Post by dataw0lf on 2004-11-16
I don't think there is a permanent way to change your NIC speed; you're probably going to have to just add it to your rc.  By the way, isn't mii deprecated? I use ethtool.  I guess it depends on your NIC, really. 
Cheers,
dataw0lf

---

