---
title: "Cannot access all RAID partitions"
date: 2007-11-15
forum: General Help
---

### Post by sdhog2002 on 2007-11-15
I am using Gutsy on a dual boot (WinXP) RAID1 Dell, succesfully set up by following various threads and How-To's. This is an upgrade of a previous Feisty set-up of the same. I have a separate FAT32 partition which I use to share data between WinXP and uBuntu which I was able to access running Feisty. Since the Gutsy upgrade, I cannot access it. It is the last RAID set in the following list:

blah@sblah-desktop:~$ sudo dmraid -ay

RAID set "nvidia_cehccefe" already active

RAID set "nvidia_cehccefe1" already active

RAID set "nvidia_cehccefe3" already active

RAID set "nvidia_cehccefe4" already active

RAID set "nvidia_cehccefe5" already active

RAID set "nvidia_cehccefe6" already active

RAID set "nvidia_cehccefe7" already active

RAID set "nvidia_cehccefe8" already active

RAID set "nvidia_cehccefe9" already active

RAID set "nvidia_cehccefe10" already active


My list of places shows all partitions listed twice, once on each mirrored RAID drive

Anyone with suggestions, please.

---

### Post by sdhog2002 on 2007-11-15
Used this:
[http://flomertens.free.fr/disk-manager/](http://flomertens.free.fr/disk-manager/)
Now can access the partition. Don't know why I need to do this extra step with Gutsy. Wasn't necessary with Feisty.

---

