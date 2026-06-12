---
title: "Free up space preceding LVM partition. Wanting to increase the size of Boot partition"
date: 2021-06-19
forum: General Help
---

### Post by fignewton2 on 2021-06-19
Hello,

How do I free up space preceding an LVM partition for the purpose of expanding the boot partition?


I am able to use a live version of GParted to resize or move a non-LVM partition, but it is not working for an LVM partition that I have.   

The system is Ubuntu 18.04.  Everything is backed up.  Any help is appreciated.    

Thank you.

---

### Post by Dennis N on 2021-06-19
Post the output of fdisk -l for the drive in question to reveal the partitioning. For example, if it's sda, post the output of:
```
sudo fdisk -l /dev/sda
```

---

### Post by fignewton2 on 2021-06-20
I will get that for you.

Thank you.

---

