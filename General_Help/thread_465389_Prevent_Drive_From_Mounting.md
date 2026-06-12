---
title: "Prevent Drive From Mounting"
date: 2007-06-05
forum: General Help
---

### Post by GuitarRocker2562 on 2007-06-05
Ok, I have a USB pendrive with 3 partitions, 2 of them are for DSL (Damn Small Linux) and the other  is for data. I have the first two partitions set to mount at /media/disk and /media/disk-1 respectively, the 3rd (my data) mounts at /media/SanDisk-USB . How do I make it so that when I plug in the drive the first 2 partitions do not mount, but the 3rd does?

---

### Post by GuitarRocker2562 on 2007-06-05
Anyone?

---

### Post by x1a4 on 2007-06-05
Hi,

In your _/etc/fstab_ file, add/change the **noauto** option to the drives you DO NOT want to auto mount, and **auto** to the ones you do.

If you don't know what I mean, reply with the contents of _/etc/fstab_ and I'll show you.

---

