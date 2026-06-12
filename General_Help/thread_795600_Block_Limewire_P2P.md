---
title: "Block Limewire P2P ??"
date: 2008-05-15
forum: General Help
---

### Post by maconga on 2008-05-15
Hello,

I live with some idiots (real ones) that like to use limewire for certain reasons.... Is there a way i can block the limewire ports from my Linksys Wrt54g router?? 

I have tried blocking port 6346-6346 in the router, i then open limewire and i can still download content, i had limewire configured to only use those two ports that i had blocked, and it was still downloading... 

they are on Windows 2000 pro and i cant install any firewall's because they would notice .....

---

### Post by pointone on 2008-05-15
I've forgotten what the Linksys firmware allows, but if you're willing to sacrifice your warranty, I highly recommend you install [Tomato]("http://www.polarcloud.com/tomato") or [DD-WRT]("http://www.dd-wrt.com/dd-wrtv3/index.php") on your router. They're much more powerful, and offer some very neat advanced features.

Personally, I use Tomato on my WRT54GL, and it's QoS features have been wonderful for dealing with the bandwidth hogs I live with.

Tomato has an "Access Restriction" section that would probably be exactly what you're looking for. Block specific ports with scheduling options (only block on Monday and Wednesday, maybe?) with the option to use Layer 7 packet sniffing to block application-specific traffic. Really cool stuff!

---

### Post by mike555 on 2008-05-15
You could go to " [www.opendns.com](www.opendns.com) " and read about how to put their DNS numbers into your router and set it to block P2P ........ of course they will notice, but it's better than the fines .....

---

