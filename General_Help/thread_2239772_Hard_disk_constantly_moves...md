---
title: "Hard disk constantly moves.."
date: 2014-08-15
forum: General Help
---

### Post by Blackbug on 2014-08-15
Hello,

I have a HP laptop with decent configuration..core i5, 4GB ram, 2 GB graphic card, 25GB SSD and 500GB normal disk.
I have a dual boot windows 8 and ubuntu. I have observed that when I use ubuntu the hard disk makes a lot of clicking noise almost 80% of the time.
When I use windows 8, I don't see some frequent hard disk movement.

What could be a possible reason for this? This usually leads to less backup time and also annoying in between.

Regards,
KK

---

### Post by MrSteve on 2014-08-15
you could have a look at the swappiness of the swap file as default is set to 60 
you can reduce this to 10 which may help ...

[http://askubuntu.com/questions/103915/how-do-i-configure-swappiness](http://askubuntu.com/questions/103915/how-do-i-configure-swappiness)

---

### Post by Impavidus on 2014-08-16
First make sure whether it's actually using swap. The system monitor can tell you, or use```
free -m
```De default swappiness is quite good under most circumstances.

Which parts of your system are on the HDD and which on the SSD?

---

