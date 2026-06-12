---
title: "Redetecting partitions"
date: 2008-04-18
forum: General Help
---

### Post by Xzenome on 2008-04-18
I just used GParted (on a live CD) to modify my partitions. How can I get Ubuntu to rebuild fstab like it does on first install?

---

### Post by ajgreeny on 2008-04-18
Not sure you can, but show us what you did and the changes made, and, assuming you can get into ubuntu, we can probably help you edit the fstab file to a fully working one.

The output of ```
cat /etc/fstab
``` and ```
sudo fdisk -l
``` would help a lot.

---

### Post by Xzenome on 2008-04-18
Don't worry, I can do it manually, I was just hoping for an automated method. Thanks for the offer though.

---

