---
title: "Enlarge a FAT32 partition"
date: 2007-05-21
forum: General Help
---

### Post by luca.b on 2007-05-21
Hello. I got a new HD for my work PC so I installed Kubuntu 7.04 on the new HD and moved the data from the old /home to the new. Now, on the old disk, I'm left with some partitions I'd like to delete and then resize the Windows FAT32 partition so that it covers the whole disk. The result would be having a whole HD for Windows (old one) and a whole HD for Linux (new one).
Is there such a way to do that (*enlarge* FAT32 partitions) in Linux?

---

### Post by LaRoza on 2007-05-21
Delete the old partition first, then expand the FAT32 partition.

When altering partitions, there is a risk of data loss so back up. (I have never experienced it)

You can use GParted on a live cd or use it from Ubuntu. Be sure to unmount the drive first.

---

