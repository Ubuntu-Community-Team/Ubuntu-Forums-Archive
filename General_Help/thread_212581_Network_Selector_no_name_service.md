---
title: "Network Selector: no name service?"
date: 2006-07-10
forum: General Help
---

### Post by RikoW on 2006-07-10
Hi :)

when I was still using Breezy on my laptop, network selector fulfilled all my needs for switching between different networking environment (wifi, wired etc). However, in Dapper I now have the problem that I don't seem to have a name service when switching from the wireless connection back to a wired one.

When I work at home, I'm using a wireless connection. When I boot up my laptop the next morning at work, I remembers that I was using wireless last and connects to the wireless network at work even though the ethernet cable is plugged in. When I now switch to the wired connection using network collector, I don't have name resolution anymore (all networking is done via DHCP). I have to reboot the machine again, before it finds our mail server or any web site.

It seems to work fine when I switch at home from wired to wireless .... 

Any idea what the problem might be?

Thanks,

             Riko

---

### Post by PriceChild on 2006-07-10
I use a little program called gnome-network-manager

It's extremely useful to get wired or wireless connections sorted out.

Pricey

---

### Post by RikoW on 2006-07-10
Network Manager doesn't seem to do it for me. I installed both network manager and the applet, which is packed in the package network-manager-gnome.

However, when I start the applet and don't have a cable plugged in, it doesn't give the choice of conneceting to an available wireless network. The I click with the left mouse button on the applet, it just shows me a "wired network" option greyed out. Right mouse button just allows me to disable networking.

Am I missing something? That doesn't sound very useful ...

Cheers,

               Riko

---

### Post by zorkerz on 2007-03-11
I believe to use network manager you have to disable your manually configured networks by going to System -> Administration -> Network and under the connection tab clicking or unchecking the wireless and wired connections. This disables them in network settings and allows network manager to control them.

---

