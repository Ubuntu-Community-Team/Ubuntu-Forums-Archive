---
title: "Copying encrypted Lubuntu from 32 GB USB to 16 GB USB"
date: 2017-04-12
forum: General Help
---

### Post by steve169 on 2017-04-12
I use Lubuntu 16.04 installed and encrypted on a 32 GB thumb drive to do all my online financial dealings. It works fine.

Now I want to clone the installation onto a 16 GB thumb drive.

"dd" won't do it because the target drive is smaller than the source drive.

I tried Clonezilla, but the resulting copy wouldn't boot.

Is it even possible to make the 16 GB copy?

---

### Post by yancek on 2017-04-12
You could probably do it but not with something simple like dd or clonezilla.  If you want to clone a drive with clonezilla, the drive you clone "to" must be larger or at least as large as the original.  You could clone the partition or partitions from the original to the new drive individually and install Grub to the new manually which might require modifying at least the grub.cfg file as well as /etc/fstab.  Never  tried it myself so it's theory.

---

