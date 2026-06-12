---
title: "RAIDS want increased performance."
date: 2008-05-26
forum: General Help
---

### Post by Vigh on 2008-05-26
Hi what is the best raid to use to increase performance? Stripped or Mirrored? I would like to have fault tolerance (mirrored) but I also want to get a performance boost out of it too. 

What is then the best RAID? 0, 1? 0+1? 1+0?
Note: I only have 2 SATA drives of equal size, make and model.

---

### Post by tamoneya on 2008-05-26
increased fault tolerance and performace = mirrored.  Stripped gives less fault tolerance and similar performance but allows you to get increased space.  You can not do a 1+0 RAID with just 2 drives.

---

### Post by fjgaude on 2008-05-26
Two-drive mirrowed gives one-drive failure fault tolerance, decreased write performance, same read as single drive.

Two-drive stripped just about doubles the read performance, about one and half times the write performance of a single drive. All lost if one of the two drives fails.

Three-drive raid5 gives twice the read/write of a single drive, and tolerance of a single drive failure.

Do a google for raid and find the exact details of raid.

---

