---
title: "eth0 not working when ppp0 is online?"
date: 2004-11-01
forum: General Help
---

### Post by rapha on 2004-11-01
Hi all,

when I go online using my dial-up connection, the ethernet connection stops working. The PCMCIA card is still having a link, but other computers in the LAN can't reach my laptop anymore and vice versa.

I suspected some problem with the routing table, since the default route doesn't get set either for the dial-up connection (gotta do it manually), but playing around with route didn't help so far.

Best regards,
Raphael

---

### Post by ynef on 2004-11-01
When ppp0 is connected, what does "ifconfig -a" tell you? Does it IP adress change for eth0? In that case, it might just be that -- that it has the LED for Link lit only means that the cards can possibly talk to each other, not that they are correctly set up.

(No, I don't have any idea why on earth it would change because of that :wink: )

---

### Post by mr_ed on 2004-11-08
Ubuntu is not alone here.

With my Windows 2000 box at work, when I make a SLIP or PPP connection, I lose access to the Internet; I can still browse the local intranet, though.

I've seen it on other distros as well.

It must be a routing issue.

---

