---
title: "Swap always at 100%"
date: 2015-11-23
forum: General Help
---

### Post by metinkale38 on 2015-11-23
Hey,

my swap is always at 100%, my swappines is 0 and even after swapoff -a und swapon -a the "free" command shows:

```
             total       used       free     shared    buffers     cached
Mem:       8088896    2652448    5436448     201784      89676    1114860
-/+ buffers/cache:    1447912    6640984
Swap:      8102908          0    8102908



```


whats the problem here?

---

### Post by metinkale38 on 2015-11-23
hahhahahahaha, my mistake, in german it is shows as:
             ```
             Gesamt     Belegt       Frei  Gemeinsam     Puffer      Cache
Speicher:    8088896    3398264    4690632     312988     107720    1670264
-/+ Puffer/Cache:    1620280    6468616
Auslagerungsdatei:    8102908          0    8102908
```



where "Frei" means "free"

---

### Post by deadflowr on 2015-11-23
where is it telling you it's at 100%?

---

### Post by SlidingHorn on 2015-11-23
> **metinkale38 said:**
> hahhahahahaha, my mistake, in german it is shows as:
             ```
             Gesamt     Belegt       Frei  Gemeinsam     Puffer      Cache
Speicher:    8088896    3398264    4690632     312988     107720    1670264
-/+ Puffer/Cache:    1620280    6468616
Auslagerungsdatei:    8102908          0    8102908
```



where "Frei" means "free"

It's actually not using any swap at all...it's just misaligned in German, as the name for "swap" is so long, it makes it look like the "Used" is actually under "Free"

---

