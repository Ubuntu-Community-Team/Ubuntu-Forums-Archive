---
title: "Formatting a new external HD in ubuntu?"
date: 2007-01-29
forum: General Help
---

### Post by spytek on 2007-01-29
Hi there,

I'm using GParted to format a new HD (external) in Ubuntu, GParted detects it, but it thinks its 128 gig, it should be 250 gig???  What is the workaround in Ubuntu to tell it the HD is infact 250gig????

Cheers

---

### Post by taurus on 2007-01-29
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
(That would be lower case l as in larry.)

---

