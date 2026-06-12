---
title: "Partition not loading in Ubuntu 12.04 while using wubi"
date: 2014-03-09
forum: General Help
---

### Post by Jay Nnib on 2014-03-09
I recently installed ubuntu 12.04.4 LTS in one of my old PC. It has 75GB storage out of which  I have made 4 partitions and provided 29GB for C drive(in which windows is installed). I installed ubuntu in that same partition using wubi. Now, one of my partitions is not loaded while booting inside ubuntu but it loads while I use windows. What should I do to make it available in ubuntu?

---

### Post by oldfred on 2014-03-09
If you look in Naulitus file browser do you have /host? That would be the c: partition or the partition you have installed wubi into.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Wubi is being phased out and 12.04 is last supported version. It does not easily work with gpt partitions which are required for UEFI boot which all new systems now use.

---

