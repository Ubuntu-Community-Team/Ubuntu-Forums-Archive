---
title: "replace boot drive"
date: 2020-08-11
forum: General Help
---

### Post by djsmirk on 2020-08-11
Hello All

Trying to think of a solution.  I am running 18.04.5 on a Samsung SSD and 3x4TB Seagate HDD in LVM:

```

Filesystem                      Size  Used Avail Use% Mounted on
**/dev/sda1                       112G   37G   76G  33% /**
**/dev/mapper/vg_media-plexmedia   11T  6.2T  4.9T  56% /mnt/Media**

```

I'm thinking about replacing this SSD with a larger "drive" (not sure of SSD or HDD, its not really important).

What is the safe way of doing this?


Thanks,

---

### Post by rsteinmetz70112 on 2020-08-11
Get your new boot drive, hook it up, clone the existing boot drive using gddrescue, edit /etc/fstab and you should be good to go unless you want to change the filesystem type or do something more exotic. You can then use gparted to edit the partitions as necessary.

---

### Post by djsmirk on 2020-08-11
Seems like a logical plan.  thanks!

---

