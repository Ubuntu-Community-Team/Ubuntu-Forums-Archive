---
title: "DHCP takes ages-- but I have no network"
date: 2005-09-11
forum: General Help
---

### Post by jnoreiko on 2005-09-11
The 'configuring DHCP' phase of the Live CD boot takes forever. But I haven't got a network!

Is there any way to skip it?

(I have the same problem with the install CD: it takes ages looking for a network that doesn't exist.)

---

### Post by GreyFox503 on 2005-09-11
I haven't used the liveCD, but during boot, if I want it to skip a certain step, I press Ctrl + C when it gets to it.

This also works to kill most programs running at the command line, but during boot it causes the computer to skip whatever step it is on.

---

### Post by lompolo on 2005-09-11
I guess if you take your ethernet cable off, it boots faster. I have problem with our buildings router. It was configured wrongly. Your network card information might help. You can get it from device manager.

---

### Post by rafakl on 2005-09-12
If it detects a network card, it will still try to configure DHCP because it will wait for the server to respond (its slow because sometimes the network traffic can be high so ubuntu will wait for the server response).

---

### Post by lompolo on 2005-09-15
If some router is wrongly configured, Linux doesn't like it. For example if router changes ip. address, Linux won't take data from wrong ip.

---

