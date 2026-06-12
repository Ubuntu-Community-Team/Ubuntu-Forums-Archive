---
title: "NTFS partition Mounting"
date: 2008-06-12
forum: General Help
---

### Post by tsimiao on 2008-06-12
I am having problems getting my NTFS partition to mount. I am running Ubuntu 8.04 and I have one hard drive where I had 4 partitions. 

A NTFS for Windows
A ext3 for Linux 
A swap partition 
A Fat32 partitions for my files.

One day I got a message that I didn't have write privileges, but I still could read it. 

I then formatted this partition to NTFS, but now I cant get it to mount automatically. The only way to mount it is to go in gparted and mount it manually. I am using Storage Device Manager to mount the other partitions automatically, but it wont mount this one.

---

### Post by heatblazer on 2008-06-12
apt-get install ntfs-config

---

### Post by tsimiao on 2008-06-12
I installed the NTFS configuration tool but when i run it, it only shows my windows NTFS partition. I tried mounting it manually through gparted, but it still doesnt show.

---

