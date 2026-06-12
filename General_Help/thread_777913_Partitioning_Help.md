---
title: "Partitioning Help"
date: 2008-05-01
forum: General Help
---

### Post by dethredic on 2008-05-01
I use both Windows and Ubuntu Linux regularly. Windows is mainly for gaming, and Linux is for everyday use and programming. All of my music and movies are on my Linux partition.

I upgraded to Ubuntu 8.04, but things didn't go so well, so I am going to do a fresh install over it.

Currently I have

sda1 - Windows
sda2 - 10gb linux partition which was made when I installed
sda3 - Linux-swap
sda4 - Main linux partition.

Instead of using dvds to back everything up, I decided that making another partition would be easier. I could put all my music and movies on it, then access them from both windows and Linux. I am thinking I should format this partition ntfs, but tell me if I should make it something else. When I open gparted and try to make another partition it says I can't make more than 4 primary partitions. Does this mean I can only have 4 partitions?
If so, do I need the 10gb one that was made with Ubuntu?

---

### Post by ryanhaigh on 2008-05-01
If you want to have more than 4 you will need to create an extended partiton to put the others into. As for formatting with ntfs, if you are spending most of your time in nix you are better off with ext3 and use the driver from fs-driver.org to enable ext access from windows when you need it.

Recommended setup:

windows C:
linux / (can be less than 10gb)
swap
linux /home

---

