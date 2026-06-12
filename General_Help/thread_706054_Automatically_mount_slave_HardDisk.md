---
title: "Automatically mount slave HardDisk"
date: 2008-02-24
forum: General Help
---

### Post by dayanandasaraswati on 2008-02-24
I've two hard drives. I've ubuntu in my master disk and i also have another 40GB hard drive plugged in as Slave. My system is detecting that hard drive. I'm able to get three volumes as hdb, hdb1 and hdb5 in my /dev folder. but when i try to mount any of them it shows me the following :
>  dayanandasaraswati@dayanandasaraswati-desktop:~$ sudo mount /dev/hdb1 /media/SANATH
**mount: you must specify the filesystem type**



What should i do to mount this partition. I also want some script to automatically mount this drive at boot time.

---

### Post by dcstar on 2008-02-24
> **dayanandasaraswati said:**
> I've two hard drives. I've ubuntu in my master disk and i also have another 40GB hard drive plugged in as Slave. My system is detecting that hard drive. I'm able to get three volumes as hdb, hdb1 and hdb5 in my /dev folder. but when i try to mount any of them it shows me the following :
.........
What should i do to mount this partition. I also want some script to automatically mount this drive at boot time.

Install the **pysdm** package and let it set things up.

---

