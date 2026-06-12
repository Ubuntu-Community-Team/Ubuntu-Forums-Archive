---
title: "right click options become grayed out in nautilus"
date: 2013-03-13
forum: General Help
---

### Post by ***J*** on 2013-03-13
Lately whenever I have nautilus open for long enough several of the options in the right click menu will become disabled when I right click on a file or folder. When I close and reopen nautilus they'll be back but it's only a matter of time until they're disabled again. The options that become gray and unclickable are cut, copy, make links, rename, copy to, move to, and move to trash (tried to take a screenshot but can't while right clicking apparently). Can someone tell me why this is happening?


ubuntu 12.04 lts
8 gb memory
amd fx 8120 cpu
geforce gtx 550 ti graphics card
64-bit
1.5 tb hdd space

---

### Post by Frogs Hair on 2013-03-13
Try the following in the terminal. ```
sudo apt get install --reinstal nautilus 
``` ```
nautilis -q
```

---

