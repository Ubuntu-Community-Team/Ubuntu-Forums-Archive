---
title: "tar order"
date: 2008-01-11
forum: General Help
---

### Post by steveneo on 2008-01-11
In ubuntu 6.06, run
touch d/1.txt
touch d/2.txt
touch d/3.txt
tar czvf d.tar.gz d/

tar will package file in order 1-3
d/
d/1.txt
d/2.txt
d/3.txt

But in any version above 6.06, the order is disturb, 
d/
d/2.txt
d/1.txt
d/3.txt

I test in CentOS4.6, it is also disturb order... I tried different version, no help.

WHY?

---

