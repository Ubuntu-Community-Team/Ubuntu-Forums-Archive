---
title: "duel booting Ubuntu/WinXP"
date: 2008-04-01
forum: General Help
---

### Post by stalkingwolf on 2008-04-01
check to make sure that your / partition is formatted EXT3 not /media or something.

---

### Post by housam on 2008-04-01
Using Gparted tool ( in the live cd - sys. >> admin. >> partition editor ) , try to create 2 partitiopns for ubuntu . one for the root ( / ) ext3 format ( more than 10 GB is OK ) and the other for swap ( 1-2 GB is OK ). when reaching the partitioning step at the installation , assign them manually.and before doing any thing backup your data.

---

