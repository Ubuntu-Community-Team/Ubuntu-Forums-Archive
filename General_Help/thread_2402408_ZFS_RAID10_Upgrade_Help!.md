---
title: "ZFS RAID10 Upgrade Help!"
date: 2018-09-29
forum: General Help
---

### Post by serverman2020 on 2018-09-29
Hi all,

Linux semi-newbie here. I'm currently running a home server and am looking to upgrade the hard disks.

My set up:

x1 1tb SSD - hosts the main operating system.

x2 8tb WD HDDs. These have been set up as a simple mirror using ZFS. All of my bulk data (ie. movies, photos, music etc) goes on these drives.

I have recently purchased x8 10tb drives. I would like to essentially replace the x2 8tb drives with x8 10tb drives set up in a raid10 fashion (so 4 drives striped and mirroring 4 drives - total 40tb available).

There are only 8 drive bays and I'd like to clone the 8tb disk to the x4 10tb array but also achieve raid10. What is the best way to achieve this?

My initial thoughts were to install x4 10tb drives and create a striped pool (ie pool1). I would then clone the data from the 8tb to pool1. Once cloned, I would remove the x2 8tb drives and install the other 4 drives as a striped array (pool2) and tell ZFS to mirror pool2 with pool 1. Am I right to proceed this way - ie will I get a raid 10 set up?

---

