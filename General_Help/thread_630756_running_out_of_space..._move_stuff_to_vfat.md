---
title: "running out of space... move stuff to vfat?"
date: 2007-12-03
forum: General Help
---

### Post by Nathan_M on 2007-12-03
Hi,
When I bought my laptop with Windows Vista, there was a 10 GB recovery partition at the start of the drive. In order to install ubuntu, I deleted this partition, and installed it then. I then shrunk my Windows partition down as far as it would go, and added a swap partition and a large vfat partition for sharing stuff between the two OSs.

The problem I have is that the 10GB partition is running out of space. Moving my Windows partition further along seems pretty much impossible (either with gparted or Vista's Partition Manager). My disk will only allow four partitions. Is there a way for me to use the masses of vfat space I have when installing linux programs and such like?

---

### Post by Mikecore on 2007-12-03
> **Nathan_M said:**
> Hi,
When I bought my laptop with Windows Vista, there was a 10 GB recovery partition at the start of the drive. In order to install ubuntu, I deleted this partition, and installed it then. I then shrunk my Windows partition down as far as it would go, and added a swap partition and a large vfat partition for sharing stuff between the two OSs.

The problem I have is that the 10GB partition is running out of space. Moving my Windows partition further along seems pretty much impossible (either with gparted or Vista's Partition Manager). My disk will only allow four partitions. Is there a way for me to use the masses of vfat space I have when installing linux programs and such like?

I would think you could resize you linux partition ( taking disk space from your Vfat )

---

### Post by merlinus on 2007-12-03
Since Windows apparently is on a partition between linux and the vfats, doubt that you can grow ubuntu.

But you probably can create a new partition in the vfat space (make an extended partition and then create a logical one within it, so you will have more flexibility going forward), and then use gparted live cd to copy your existing ubuntu partition to the new one, which of course you have made larger than 10G..

---

### Post by ryanVickers on 2007-12-03
I would yes, use the vfat SPACE, but not actually Vfat ;)  Reformat the vFat as ext3 to keep it safe, and then move your stuff on to it. Also, you don't need vfat anymore - since feisty, ntfs witting has been possible, and if you need to read your Linux from windows, just "give" it some files before hand or install some of the plugins that are available to be able to read Linux filesystems.

---

