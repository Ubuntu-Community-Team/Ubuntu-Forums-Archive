---
title: "Identify physical hard drives"
date: 2007-12-13
forum: General Help
---

### Post by Boule on 2007-12-13
Is there a command or a way to identify the physical hard drives connected to a machine ? No matter the number of partitions, just say how many/what are the actual drives...

Thanks !

---

### Post by cmnorton on 2007-12-14
df

---

### Post by vanadium on 2007-12-14
sudo fdisk -l 

or if you want it clean

sudo fdisk -l | grep

or more clean and specific

sudo fdisk -l | grep Disk | grep bytes

The following command will tell you about the number of disks:

sudo fdisk -l | grep Disk | grep -c bytes

---

