---
title: "Direct cable connection between Ubuntu 12.04 and Win 7 not working"
date: 2012-11-21
forum: General Help
---

### Post by Advait on 2012-11-21
Hi All,

PC A is a laptop running 12.04 from an external hard  drive. PC B is a Win 7 laptop running Win 7. I have an ethernet cable  directly connecting them both. There's no router or ethernet hub or  switch. I've spent a number of hours trying to view the Win PC from PC  A. Nothing has worked. On PC A I've installed Samba, gvfs etc. On PC B  I've enabled network sharing, etc.

How can I get PC A to see the files on PC B? I've spent hours googling for solutions and looking on various Ubuntu forums. Nothing has worked.

On PC A the network icon is showing 2 thick arrows pointing up and down which means something is connected. 

I keep getting the errors: "Nautilus cannot handle "network" locations." and "Failed to retrieve share list from server".

Any solutions? Thanks,

Advait

---

### Post by Mark Phelps on 2012-11-21
Have you confirmed that the ethernet cable is a "crossover" cable, not a "standard" cable?  A crossover cable has some pins swapped so the devices can talk to each other; a standard cable needs a hub or router.

---

### Post by SJR Dorset on 2012-11-21
Have you manually set the IP Addresses on both computers? With a direct network connection there will not be a DHCP Server to assign IP Addresses.

---

### Post by Advait on 2012-11-24
> **Mark Phelps said:**
> Have you confirmed that the ethernet cable is a "crossover" cable, not a "standard" cable?  A crossover cable has some pins swapped so the devices can talk to each other; a standard cable needs a hub or router.

Ahhh... Interesting. That's probably it. I'll try to track down a crossover cable. Thanks!

---

