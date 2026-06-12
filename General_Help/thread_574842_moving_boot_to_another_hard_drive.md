---
title: "moving /boot to another hard drive"
date: 2007-10-13
forum: General Help
---

### Post by shane_on_u on 2007-10-13
I just purchased some new hard drives. I have a partition for /boot on one of the disks that I wish to swap out, however, I'm having difficultly moving /boot to another partition on a different drive. Anyone know what the process for doing this is?

Currently I've created a small 300MB ext3 partition on one of the new drives and just copied over all the grub files from /boot and gave the partition the boot flag... but no go. I'm guessing that's entirely wrong. Any help would be much appreciated.


Shane

---

### Post by vanadium on 2007-10-13
Is there a particular reason why you want to move that boot directory, which is small anyway? In Linux, all you want is possible, but this one might require quite some insight in the system and how it boots before you can tweak this the way you want.

---

### Post by shane_on_u on 2007-10-13
The main reason I have /boot on a separate drive is because I'm running a software raid array. The drive that /boot is currently on is very old and I would like to swap it out for a newer drive. But as I mentioned, I don't seem know what the steps are for doing this. Is it as simple as creating a new partition, copying over grub, making the partition bootable and updating /etc/fstab?

---

