---
title: "Recovery - damage control"
date: 2008-01-23
forum: General Help
---

### Post by ele_mugv on 2008-01-23
Wat is the recovery command on the linux terminal...while selecting a bootable partition..i lost al my partitions and everything within them..pls if u can be of assistance i'd appreciate it

---

### Post by bodhi.zazen on 2008-01-23
So sorry you are having problems, but slow down.

What happened ?

Are you wanting linux commands to use on a live CD or grub commands ?

you can list your partitions with

```
sudo fdisk -l
```

See if testdisk helps (it is in the ubuntu repos and you can install and use it with the ubuntu live CD).

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

How to testdisk : [http://www.debian-administration.org/articles/420](http://www.debian-administration.org/articles/420)

grub uses tab completion and find

root=(<tab>

find /boot/grub/stage1

---

