---
title: "[SOLVED] Configure grub after installing windows on separate disk"
date: 2008-02-13
forum: General Help
---

### Post by pjman on 2008-02-13
How can I configure grub so Windows will boot off a FakeRAID partition?

Some history - I had Feisty setup fine with dualboot on FakeRAID mirror, everything worked fine. Along comes Gutsy and I decide to do a fresh install. Low and behold FakeRAID messes up, deletes my Windows install. I decided to install a IDE drive I had and put Ubuntu on that. I'm just getting around to re-installing Windows on the FakeRAID mirror.

Ubuntu installed on IDE drive (hda1) - boots and works fine

/dev/hda                                       ext3 (Ubuntu)

FakeRAID setup on two SATA drives. I've been using second and third partition without any problems. I just installed windows on on first partition. Windows boots fine when I select the drive during POST.

/dev/mapper/nvidia_aeedigej1     NTFS (Windows OS)
/dev/mapper/nvidia_aeedigej2     NTFS (media)
/dev/mapper/nvidia_aeedigej3     ext3 (Ubuntu Storage)

***EDIT***
The grub 'map' option from this thread helped [http://ubuntuforums.org/showthread.php?t=46003](http://ubuntuforums.org/showthread.php?t=46003)

---

