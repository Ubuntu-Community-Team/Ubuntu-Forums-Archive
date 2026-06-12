---
title: "disc space allocation"
date: 2020-11-14
forum: General Help
---

### Post by antecedens on 2020-11-14
I have a laptop with MBR and win10 already there.
I wish to keep win10, but have Ubuntu as my main OS
Somehow, after installing Unbuntu 20.04.1, it received mere 20GB of disc space and i don't know how to change it. I don't even know how to find similar questions on the forums.

---

### Post by oldfred on 2020-11-14
Is this a very old system?
Microsoft has requried vendors to install Windows in UEFI boot mode since 2012.

Auto install just resizes a partition and fits a new ext4 partition in for Ubuntu.
You have to use Something Else to have the options to choose partitions, or sizes of partitions.
And always best to shrink Windows using Windows tools to avoid issues.

Windows 10 also turn fast start up back on with updates, and then grub will not boot it. 
With MBR, you must have Windows repair/recovery flash drive to fix Windows when grub will not boot it. And your Ubuntu live installer.
You may have to temporarily install Windows boot loader, fix Windows, then restore grub.

Post this, if drive is sda, or change to your drive(s):
sudo parted /dev/sda unit s print

---

### Post by antecedens on 2020-11-16
I solved my problem with advice from the link
Thank you.

---

