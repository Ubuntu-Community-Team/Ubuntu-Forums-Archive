---
title: "Where is Ubuntu located on my hard drive?"
date: 2012-10-23
forum: General Help
---

### Post by kenmore on 2012-10-23
When I installed Ubuntu I believe I chose the option "Install Ubuntu Alongside Windows 7" or something like that. But it never asked me to create a partition or how large the partition should be. I remember trying Ubuntu once a couple years ago and it made me create a partition.

I see a "removable volume" 932 GB Volume, which is just my HDD, and I can see all my Windows stuff in it, but I don't know where the Linux stuff is located on it. When I install applications or create images, where do they go on my hard drive? Will I run out of space? (like partitioned space). 

Sorry, I'm new to this. Just trying to learn.
Thanks.

---

### Post by Tralce on 2012-10-24
If you installed it from a bootable CD, and selected "install alongside," it did create a partition automatically. Try running Disk Utility in Ubuntu, or diskmgmt.msc in Windows to get a look at your partitions.

---

### Post by oldfred on 2012-10-24
You can also use terminal to see partitions.

sudo fdisk -lu

And if you have clicked on the Windows partition to auto mount it, then you can run this to see use of mounted partitions.

df -h

---

