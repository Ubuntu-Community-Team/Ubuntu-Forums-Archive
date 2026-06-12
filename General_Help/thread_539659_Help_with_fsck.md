---
title: "Help with fsck"
date: 2007-08-31
forum: General Help
---

### Post by [SkG] on 2007-08-31
I want configure fsck to check only my linux partitions.
I have 1 partition with windws (25GB) and i dont want fsck to check it. Where can I change this.

Thx. Sorry for my english, i'm spanish.

---

### Post by diatribe on 2007-08-31
in your /etc/fstab file, you will notice 2 sets of numbers at the end of the line for each device, these control when fsck is run on the drives.  I believe if you change the second number to 0 scanning will be skipped at boot, man fstab will be able to give you more info

---

### Post by [SkG] on 2007-08-31
Thx a lot! I got crazy because I wasn't be able to find any config file of fsck

---

