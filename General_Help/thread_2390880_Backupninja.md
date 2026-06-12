---
title: "Backupninja"
date: 2018-05-03
forum: General Help
---

### Post by christon74 on 2018-05-03
Good evening fellow Ubunters:D
 I have a 131.7 Gb hard disk on this machine and 93 are already taken.  A few days back, I saw a warning that there was not enough free space on my hd. After a while, I found out it was the back-up files that were taking too much space. Is it possible to save them to an external hard disk? 

_ Ubuntu flavour: 16.04 LTS.
_ Hardware: Fujitsu Esprimo  E 5731 E-Stars.

Thanks.

Chris.

---

### Post by Autodave on 2018-05-03
Back-up files of what?  Kernels? If so, you can get rid of the old kernels (assuming that you have no reason to keep them) by running:
sudo apt autoremove --purge

---

