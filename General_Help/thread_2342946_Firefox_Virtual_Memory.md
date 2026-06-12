---
title: "Firefox Virtual Memory"
date: 2016-11-11
forum: General Help
---

### Post by KenF on 2016-11-11
Setup:  Ubuntu 14.04 with updated Firefox (49.0.2).  8GB RAM with 8GB swap partition.


While Firefox is taking up a normal amount of actual memory (I have 5 tabs open and resident memory for Firefox is 710MB), the VIRT memory (htop or top) is over the top.  Currently 25.7GB !!!!  This is causing very strange issues (keyboard freezes) and instability.

Why on earth would Firefox request 25.7GB?

Solved:  It was the RES (Reddit Enhancement Suite) add-on.

---

