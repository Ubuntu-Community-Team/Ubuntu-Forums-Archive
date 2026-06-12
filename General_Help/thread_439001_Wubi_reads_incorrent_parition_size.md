---
title: "Wubi reads incorrent parition size"
date: 2007-05-10
forum: General Help
---

### Post by Rictor on 2007-05-10
Hey everyone,

Last night I tried to install Ubuntu via Wubi, and encountered a problem. I have a  5gb partition set aside for this purpose (on a 250gb SATA disk), formated and ready to go. However, when I go to Settings in the installer all drives read as 0.06gb except one, which isn't even my system partition. My secondary hard-drive also reads as 0.06gb. All the drives and partitions are NTFS formatted, and only one of four has the accurate size displayed. Obviously, this makes installing Ubuntu impossible, since the installer thinks there isn't enough space.

Anyone care to make a guess at where the problem might lie?

Thanks.

---

### Post by ago on 2007-05-10
Is this for a new installation or for a reinstallation?

---

### Post by Rictor on 2007-05-10
New installation. I did install it previously on another partition (the only one that works), but I ran into some problems so I uninstalled it and decided to try it on a dedicated partition.

---

### Post by Rictor on 2007-05-11
Has anyone else run into this problem? I can't for the life of me figure out the cause, given that three partitions are showing up incorrectly and one correctly, even though there are no apparent differences between them.

---

### Post by ago on 2007-05-11
Note that the free space in the box takes into account the virtual disk sizes. So it's actual free space - space used by virtual disks. If you change the size of virtual disks, free space should change. The free space does not compensate for existing wubi installations.

Disks with less than 4GB should not be shown at all (but that section has been changed a few times and I lost track). I'll have another look tonight.

---

