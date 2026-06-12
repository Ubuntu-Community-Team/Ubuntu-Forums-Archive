---
title: "copying ubuntu to a smaller disk/partition"
date: 2007-07-11
forum: General Help
---

### Post by BigCdaAnswer3 on 2007-07-11
Hey all, I have a single board computer and I am currently running ubuntu off an 8gb flash card, but I am only taking up a small fraction of that. I would love to transfer everything to a smaller card, and it seems I have tried everything including resizing the partition to fit on a smaller card, and copying the mbr...Does anyone have any tips on copying larger partitions/disks to smaller partitions/disks (assuming they will fit)??? I've hit a wall.

---

### Post by BobbyBionic on 2007-07-12
Hi

It's possible to do it but you have to take about some points :
- fstab file must be modified
- grub have to be installed on the new mbr, and the menu have to be modified if it's not automatically done.
- I think I'm forgetting something but I don't remember why...

---

