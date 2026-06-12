---
title: "pcmcia wireless card help"
date: 2006-07-03
forum: General Help
---

### Post by btboudreaux on 2006-07-03
I have an HP laptop with an internal wireless broadcom card which refuses to work with Ubuntu (b/c apparently broadcom doesn't provide any linux support). The only thing really stopping me from using Ubuntu more is the fact that I can't use wireless. Im thinking of purchasing a pcmcia wireless card for my laptop for the soul purpose of using Ubuntu.

I found the list of compatable pcmcia cards here
[http://www.tldp.org/HOWTO/Hardware-HOWTO/pcmcia.html](http://www.tldp.org/HOWTO/Hardware-HOWTO/pcmcia.html)

It's a big list and I'm wondering if anyone can give me some suggestions on which cards work the best. I need one with FULL support out of the box. No installing ndiswrapper or workarounds, just full support out of the box. 54mps bit rate (although 11mbps would be fine), compatible with WEP, stable, etc etc.

Any suggestions?

---

### Post by decaturcomp on 2006-07-03
my D-link Air Plus and a cheapie airset from Fry's both worked fine without the ndis wrapper or any other problems.

---

### Post by tonyr on 2006-07-03
Sorry about your Broadcom problems.  See [this]("http://www.ubuntuforums.org/showthread.php?t=185174") thread
for a howto and mixed bag of results.

I'm using a Zonet ZEW1501 (Ralink RT2500 chipset) pcmcia card with no problems.
(It was the generic cheapie at my local hardware supplier).

---

### Post by btboudreaux on 2006-07-03
Thanks decaturcomp! I'll look into some D-link Air Plus ones.

tonyr: I've tried everything. I have the broadcom chipset that nobody can get to work unfortunately. I'll look into your card too.

Anyone else with suggestions?

---

### Post by JEBB on 2006-07-05
I have a Zonet ZEW 1501 which worked out of the box with Ubuntu 5.10 but doesn't appear to be working with Ubuntu 6.06.  My router is an Airport Extreme Base Station.  

I am also able to connect to the Internet with my PowerBook (MacOS 10.4.6) and my ThinkPad (XP/SP2)with no problems.  

Any suggestions?

---

### Post by tonyr on 2006-07-05
When I got my card the dapper release was at flight 4 and wireless setup wasn't
fully there.  I had to edit **/etc/network/interfaces** and add these lines:
```

auto ra0
iface ra0 inet dhcp
wireless-essid  <my-ssid>

```

Substitute your own SSID in that last line.  If you are using a static IP address, you
would change **dhcp** to **static**, and  there are some other lines you would have 
to add.  Unfortunately I don't recall what they are at the moment.

---

