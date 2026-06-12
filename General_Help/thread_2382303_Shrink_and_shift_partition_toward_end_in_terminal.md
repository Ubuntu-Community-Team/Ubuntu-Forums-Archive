---
title: "Shrink and shift partition toward end in terminal?"
date: 2018-01-11
forum: General Help
---

### Post by jl303 on 2018-01-11
I have primary partition right after boot partition ends.
I'd like to shrink and shift primary partition to the end and grow boot partition.
It seems like I can change the end sector, but not the start sector without making the partition unusable.
Is that possible to do this in headless terminal?
I found some articles suggesting to shrink swap partition between boot and primary, but I don't have swap.
Thanks!

---

### Post by TheFu on 2018-01-12
Please find and run the boot-info script that is part of **boot-repair**.  We need the facts to prevent bad advice.

---

