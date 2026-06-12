---
title: "Mate caja grinding whole system to a halt... literally."
date: 2015-09-22
forum: General Help
---

### Post by Nixarter on 2015-09-22
I suddenly noticed my hard drive grinding full-out and not stopping.  all i hear is the hdd grinding, and closing programs seems to do nothing.  caja is using 60%+ cpu, 100% HDD, all my RAM, and won't let me do anything.

What is it doing, and how do I make sure it doesn't do that anymore?

---

### Post by v3.xx on 2015-09-22
Sounds like you went to swap.  You can monitor memory in terminal with the command:
```
free -m
```

You could also post your specs.
```
sudo apt-get install inxi && inxi -Ibl  ##thats  -capital eye;  small bee and small L
```

---

