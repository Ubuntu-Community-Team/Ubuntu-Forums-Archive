---
title: "NTFS HDs unexpected behavior"
date: 2018-08-18
forum: General Help
---

### Post by waltergallegos on 2018-08-18
At boot end my tool bar show 3 NTFS HD present, but programs do not find it until I click onto HD icon.
In others words, only after open each HD in Nautilus one time; others programs can reach files.

---

### Post by deadflowr on 2018-08-18
Not surprising or unexpected.
Nothing is automatically mounted at startup except what has been added to the mount information file, fstab. (typically)
The mere presence of the hard drives showing in various locations such as in a toolbar or in a launcher dock just means that the system can see the hard drives/partitions at least.

Some stuffs on setting up auto mounts and windows partitions and et cetra, et cetra:
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")
[https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")
[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")
[https://askubuntu.com/questions/46588/how-to-automount-ntfs-partitions]("https://askubuntu.com/questions/46588/how-to-automount-ntfs-partitions")

---

### Post by waltergallegos on 2018-08-18
Thank you; you answered my question
From the point of view of a simple user, that Nautilus access HDs and other programs do not, is very close to an unexpected behavior.

---

