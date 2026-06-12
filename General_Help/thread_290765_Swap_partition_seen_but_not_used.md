---
title: "Swap partition seen but not used?"
date: 2006-11-01
forum: General Help
---

### Post by voice06 on 2006-11-01
I recently installed Ubuntu Edgy Eft, and since installing it I've had problems with it freezing due to all the ram being used up. I've looked at it through the top command and it seems the swap memory is never being used, even after doing the swapoff/swapon. Any ideas as to what would prevent Ubuntu from using the swap partition?

---

### Post by matthewstory on 2006-11-01
sudo fdisk -l

make sure the id for the swap is 82 and the type is linux / solaris swap.

df -h /dev/hda2

or whatever your swap is, this will tell you how big it is, and give you general stats about its usage.

Unfortunately this could also be an issue with your HDD having bad blocks, which is harder to detect.

---

