---
title: "Many Python instances running in Kubuntu"
date: 2007-03-21
forum: General Help
---

### Post by kayosiii on 2007-03-21
I am getting a rediculous number of python processes running (as viewed from ksysguard - something like 40 I think). Killing these processes does not seem to affect my system in any negative way and frees up a non trivial amount of memory.

I can trace a few to amarok and associated plugins but I have no idea where the rest are comming from. In a tree view they show up in kinit.

I would very much like to track down the source of this and get rid of them.

I also have a quite a few kinit processes forming.

Oh yeah I am using Kubuntu Edgy which is fairly heavily customised...

---

### Post by energiya on 2007-03-22
Try watching what processes start at boot time. Maybe some of them are python based.

---

