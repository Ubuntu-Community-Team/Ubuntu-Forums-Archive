---
title: "Dell OEM Partition"
date: 2012-10-15
forum: General Help
---

### Post by PhantomTurtle on 2012-10-15
I have a Dell laptop and I want to dual boot it with Windows 7 and Ubuntu 12.04. Currently there are 3 partitions, OS, Recovery, and a 33mb fat16 partition. I want to keep the first two, is it safe to delete the extra 33mb partition. Is it supposed to be a boot partition that will make my computer unbootable. I am manually partitioning and I will make a /boot primary partition and a extended / and swap partitions. So is safe to delete it?

---

### Post by cool110 on 2012-10-15
That partition contains a DOS system and diagnostic tools. If you have your drivers and utilities disc you can use that instead. I would back it up using dd first

---

### Post by PhantomTurtle on 2012-10-15
> **cool110 said:**
> That partition contains a DOS system and diagnostic tools. If you have your drivers and utilities disc you can use that instead. I would back it up using dd first

Well I have the CD's, so can I just delete it in the Ubuntu partitioner and everything will be fine?(as in, Windows will still boot?)

---

### Post by cool110 on 2012-10-15
Go ahead Windows doesn't use it at all, the only side effect will be the diagnostics boot option failing.

---

### Post by PhantomTurtle on 2012-10-15
> **cool110 said:**
> Go ahead Windows doesn't use it at all, the only side effect will be the diagnostics boot option failing.

Well I never use the diagnostics anyways and as long as my computer boots up I'm fine. Thanks for all the help :)

---

