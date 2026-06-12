---
title: "NDIS Wrapper just gives up after a few weeks"
date: 2005-09-01
forum: General Help
---

### Post by Zotova on 2005-09-01
I have had this problem twice now. I originally installed ubuntu and after some struggling adapting to Linux I finally got ndiswrapper working. However a few weeks later I loaded ubuntu and my card refused to connect to the router. The lights appeared on the card and it flashed but it would simply not connect to the router.

Anyway the first time I put it down to my lack of Linux skills and I decided to start afresh so made a clean installation of ubuntu. With a little experience under my belt I compiled ndiswrapper (1.2) from source and this time got everything working in under 10 mins. Everything has been working perfectly for about a month now.

However this morning I boot into ubuntu and the same problem has occurred again. I've tried restarting the router, but nothing.

When I boot into xp though it connects perfectly so I would say it is safe to rule out hardware failure. Has anyone got an idea why ndiswrapper just stops working after a few months of connections?

---

### Post by az on 2005-09-01
Could it be that you get a DHCP lease from your router and it expires after a few days?

How are you configuring your connection?

---

### Post by Zotova on 2005-09-01
My router is set so it never expires the dhcp ip addresses, but once again wouldn't the problem occour in xp as well?

To configure the connection I have been using the built in network tools in gnome. I simply typed in my essid and my encryption key (128 wep) and then clicked activate. This has been working perfectly for a month now with no need to alter anything.

What is worth saying is that if I manually configure my essid via the terminal with this command:

iwconfig wlan0 essid xxx

(xxx being my essid name)

I then type iwconfig, wlan0 shows as off/any and it does not update never mind how many times I re-enter my essid. The encryption key does show however.


I thought I'd also state I am using an 3com 3c154g72 wireless 54g card.

Thanks for the help.

---

### Post by Zotova on 2005-09-02
Anyone else got any ideas?

I've installed the latest version of ndiswrapper (1.3rc) but my card still will not connect for some reason.

---

