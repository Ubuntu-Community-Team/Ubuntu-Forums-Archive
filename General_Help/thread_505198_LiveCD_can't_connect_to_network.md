---
title: "LiveCD can't connect to network"
date: 2007-07-20
forum: General Help
---

### Post by zergberg on 2007-07-20
I've tried this with both a standard Feisty and Xubuntu Dapper CD:

On my neighbor's wired connection (no idea on the modem settings) the LiveCD automatically connects okay to the network on my neighbor's desktop, but when I move the ehternet cable over to my laptop it doesn't work. I haven't been able to test my laptop with any other modems/routers, unfortunately. Is it more likely that something's wrong with the LiveCD or that my ethernet jack is broken? (I know that it's recognized (at least in Arch Linux, which won't connect either,) and someone using Redhat didn't mention any problems with it.) A very small amount of data does appear to transfer when I try to connect.

---

### Post by overdrank on 2007-07-20
> **zergberg said:**
> I've tried this with both a standard Feisty and Xubuntu Dapper CD:

On my neighbor's wired connection (no idea on the modem settings) the LiveCD automatically connects okay to the network on my neighbor's desktop, but when I move the ehternet cable over to my laptop it doesn't work. I haven't been able to test my laptop with any other modems/routers, unfortunately. Is it more likely that something's wrong with the LiveCD or that my ethernet jack is broken? (I know that it's recognized (at least in Arch Linux, which won't connect either,) and someone using Redhat didn't mention any problems with it.) A very small amount of data does appear to transfer when I try to connect.

Hi can you post the out put of the command in the teminal
```
lspci
```
Terminal is located under applications, accessories, terminal  this will give us info on your nic card and we can search from there

---

