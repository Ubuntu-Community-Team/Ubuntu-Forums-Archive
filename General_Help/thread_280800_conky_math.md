---
title: "conky math"
date: 2006-10-20
forum: General Help
---

### Post by m.musashi on 2006-10-20
I set up conky to display my / and /home partitions including the amount of used and free space. Interestingly enough, the numbers don't correspond to nautilus. They also don't add up. Conky says my /home partition is 98.43GB with 5.11GB used. If you do the math that means about 5.2% used. Conky says 11% used (i.e. 89% free). Nautilus tells me I have 88.3GB free which is much closer to the free % from conky but doesn't match the amount used as reported by conky.

Not really a problem but interesting.

---

### Post by hearnden on 2006-10-20
what does df say?

---

### Post by m.musashi on 2006-10-20
> **hearnden said:**
> what does df say?

```
/dev/sda5            103210940   5336684  92631448   6% /home
/dev/sda6             41286796   3742804  35446708  10% /
```
Which are the precise sizes reported by conky but conky says that 11% of /home is used and 15% of / while df reports 6% and 10% respectively.

---

