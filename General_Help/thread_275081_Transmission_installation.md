---
title: "Transmission installation"
date: 2006-10-10
forum: General Help
---

### Post by staaka on 2006-10-10
Hi guys, i recently installed the latest distrobution of dapper drake. And i'm trying to install the bittorrent client Transmission. when i type ./configure i get this output:

junkion@junkionsystems:~/Transmission$ ./configure
System:  Linux
Could not find a working compiler

I've never encoutnered this problem before, does anyone have any suggestions?
all your help would be appreciated.

thanks

---

### Post by PriceChild on 2006-10-10
Please ensure you have installed build-essential:
```
sudo apt-get install build-essential
```

---

### Post by staaka on 2006-10-10
aha! Thank you much, pricechild! I recall seeing another post about build-essential, but there were other packages listed as well, and just assumed that I wasn't able to install them..

thanks

---

