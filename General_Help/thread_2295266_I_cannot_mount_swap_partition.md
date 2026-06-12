---
title: "I cannot mount swap partition"
date: 2015-09-17
forum: General Help
---

### Post by sam9999it on 2015-09-17
I have change mi phisical memory from 6GB to 4GB now the partition with the linux swap is not mounted from ubuntu gnome and I cannot mount if I try to mount it.
How can I solve? I have change the dimension but I cannot mount the swap patition in linux ubuntu gnome.

---

### Post by Bucky Ball on 2015-09-17
*Thread moved to **General Help**.*

Welcome. Have you tried deleting the swap partition and recreating it? You would then need to change your fstab file so it is mounted on boot. 

How are you trying to do this? Using Gparted? Have you right clicked the swap and 'swapoff'?

---

