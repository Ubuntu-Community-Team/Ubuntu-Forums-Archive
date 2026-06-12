---
title: "Synaptic hangs machine"
date: 2006-12-09
forum: General Help
---

### Post by rafemonkey on 2006-12-09
I just installed 6.10 on a htpc system with a Via epia EN 1500G MB with 512mb, a c7 (i586) processor, and unichrome IGP graphics. Twice now, the machine has locked while installing packages in synaptic. This is a pretty hard lock up, the screen freezes and the machine drops off the network. (no pinging it or ssh). I have sucessfully used synaptic a few times as well. not really sure what's going on. any thoughts?

TIA

R.

---

### Post by taurus on 2006-12-09
Try aptitude from a terminal!!!

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by rafemonkey on 2006-12-09
sweet! And it works over ssh, so I don't have to sit on the floor in front of the TV :-D

---

