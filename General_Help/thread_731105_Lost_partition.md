---
title: "Lost partition?"
date: 2008-03-21
forum: General Help
---

### Post by schnauzer93 on 2008-03-21
I have recently uninstalled Ubuntu and resized my NTFS partition to fill the whole 250GB disk in Gparted. However, Gparted shows that I have ~147GB of space used of my 232GB partition. When I boot into Windows, it shows that I have 67GB used (correct) out of a 158GB partition (not correct). It seems that the 80GB partition that I had Ubuntu installed on has been lost, as Gparted does not recognize it, and Windows doesn't know its partition is 250GB.

Any ideas?

---

### Post by harlan on 2008-03-21
Use testdisk, for instance. To do it, boot from Ubuntu liveCD and install it
from the universe repository (so enable it). Then run it from a terminal:
   $testdisk

---

