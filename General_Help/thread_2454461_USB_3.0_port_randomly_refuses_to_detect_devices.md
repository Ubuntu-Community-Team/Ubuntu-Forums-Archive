---
title: "USB 3.0 port randomly refuses to detect devices"
date: 2020-11-30
forum: General Help
---

### Post by kmfias32 on 2020-11-30
[COLOR=#242729][FONT=Arial]This is a bit of a strange issue that has baffled me. I own a Dell Inspiron laptop with Ubuntu 18.04(i upgraded from 16.04 that came pre-installed). The laptop has USB 2 ports and one USB 3.0 port(the blue one). The problem is that the USB 3.0 port does not reliably detect devices. The only device I can consistently mount on it is a Western Digital external HDD. The port refuses to detect non USB 3.0 devices at all(older pen drives, dongles), and a Sandisk 3.0 pen drive I have works sporadically: sometimes it won't be detected, but if I put in the Hard drive first and then remove it and put the pendrive in; or if I plug the pendrive in a USB 2.0 port and then take it out and put it in the USB 3.0 port; it gets detected. 

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]The port outputs power without problem, and it transfers data fine so that makes me think its not a hardware issue, but i don't feel very sure because the issue started shortly after I replaced the laptop keyboard with a cheap, spurious one that i got from Ebay, after spilling orange juice on the original one. I'm not sure if the two are related, but the port started to malfunction shortly after the juice spill.
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]
Any help would be greatly appreciated.[/FONT][/COLOR]

---

### Post by CatKiller on 2020-11-30
There are (old, cheap, usually) devices that will only work in USB 2 ports and won't work in USB 3 ports.

You can't *just* spill fluids in a laptop keyboard: it's all one unit. You have likely damaged the ports as well.

---

### Post by kmfias32 on 2020-11-30
> **CatKiller said:**
> [COLOR=#000000]There are (old, cheap, usually) devices that will only work in USB 2 ports and won't work in USB 3 ports.[/COLOR]
The devices i'm using are neither old nor cheap, and they used to work perfectly fine in the same port.

> **CatKiller said:**
> [COLOR=#000000]You can't [/COLOR]*just*[COLOR=#000000] spill fluids in a laptop keyboard: it's all one unit. You have likely damaged the ports as well.[/COLOR]
Shouldn't it cease working altogether then? Why work with USB 3.0 devices but not with 2? And why recognize a Hard disk just fine but have trouble with a pen drive?

I'm hoping to try out any software solutions before I take it to Dell to be opened and tinkered with. Will do that once software troubleshooting has been exhausted

---

### Post by CatKiller on 2020-11-30
> **kmfias32 said:**
> Shouldn't it cease working altogether then?

Not necessarily. There's a formalised dance of voltages and resistance that USB devices use to negotiate their connection and capabilities. I'd imagine that the resistance is markedly different between a conductor and a conductor that's coated in orange juice residue.

---

### Post by kurt18947 on 2020-11-30
> **CatKiller said:**
> Not necessarily. There's a formalised dance of voltages and resistance that USB devices use to negotiate their connection and capabilities. I'd imagine that the resistance is markedly different between a conductor and a conductor that's coated in orange juice residue.

Not to mention that orange juice is acidic. One thing I might try just for grins is to plug a USB hub (if you have one) into the laptop then plug different devices into the hub. See if that helps with device recognition.

---

### Post by rbmorse on 2020-11-30
Sometimes one side of the controller on the device can go bad.  It's usually the USB 3 that quits working, but I've some lose the USB 2 channel as well.  

Most pen drives aren't what you'd call high quality devices.  The only brand I've tried that hasn't failed at some point and in some way are the expensive $amsung FIT and BAR series devices.

---

