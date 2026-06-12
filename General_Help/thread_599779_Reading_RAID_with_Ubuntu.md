---
title: "Reading RAID with Ubuntu"
date: 2007-11-01
forum: General Help
---

### Post by Amarishi on 2007-11-01
I have installed 7.10 as second OS on a machine which runs XP on a Raid Lvl 1. The Hardware situation is that Ubuntu is working on a separate IDE Drive (as second Master Drive) on the same machine of which the RAID is part of. My problem is: I want to lay my Linuxhands on the Datas of the RAID (which is the first Master Drive) but I can't figure out how I can do this: It does not appear anywhere and obviously cannot be reached from Ubuntu (or any other Linux Dist?)

I appreciate any good hint or idea how to solve this problem.

Yours,

Amarishi

---

### Post by fjgaude on 2007-11-01
I don't know how the raid was created by you might be able to recognize it with a Linux program called dmraid. It is in the Ubuntu depository. Learn how to use it and you should be able to mount the raid1 array in Ubuntu and get to the data.

---

