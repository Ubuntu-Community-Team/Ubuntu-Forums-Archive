---
title: "How much space does all of your applications use?"
date: 2013-12-23
forum: General Help
---

### Post by bigtinyman on 2013-12-23
I'm curious to know how much space the common Ubuntu user finds that their OS files and Ubuntu applications take up. Disregard media and other files. Right now I dual installed Windows and Ubuntu on an SSD, and am using another HDD as media storage for both OS's. But I found out that I can't install Ubuntu applications on this HDD, like you can do in Windows. So after some hunting for a solution, I read that someone uses like, 20GB max for all their Ubuntu applications and OS files. If that's so, my 60GB of space on the SSD would be plenty. But if that's not true, I may have to reinstall Ubuntu onto it's separate drive.

So how much space does your Ubuntu OS and it's applications use up?

Thanks for the responses!

---

### Post by deadflowr on 2013-12-23
Installing applications on your ssd will be no problem.
Right now, at quick glance, I am using 80GB of space on the current machine I'm on.
Of that, 74GB are on my Home folder, so the general system is using roughly 6GB.
If I were to add and include the user configuration files and user caches that are in the users home folder, I could probably add another 1 or 2 GB to the general system's overall total, maybe.
So all told, I'm easily running with less than 10GB. -not including my personal files(the 74GB give or take the config/cache files)
20 GB should be no problem.

I don't know off hand how many programs I have installed but I know I have just over 1800 packages installed.
I would think it's right in the middle between thin and bloated.

---

### Post by Impavidus on 2013-12-23
It depends a bit on the kind of applications you want to install. Some of them, like planetarium programs or flight simulators, consume lots of disk space, up to tens of GB. Usually you can configure them such that the data is in a directory on a separate partition, which can be an NTFS partition if you really like. Other than that, 60GB should be enough for everything except your media collection, which can be savely stored on a partition shared with Windows.

---

### Post by oldfred on 2013-12-23
My working install is 12.04 and I have /home inside it with .wine and Windows Picasa using about 2GB of the 11GB used. The other installs are just about bare bones Ubuntu with maybe a few applications installed to test something.
Some games or stand alone applications can be installed in other partitions and linked back into /home. 

```
fred@fred-Precise:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd3        28G   11G   16G  40% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           791M  1.1M  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  128K  2.0G   1% /run/shm
/dev/sdc2       100G   40G   60G  40% /mnt/shared
/dev/sdc6        97G   51G   41G  56% /mnt/data
/dev/sdd4        28G  4.8G   22G  19% /media/Quantal
/dev/sdc16       25G  3.9G   19G  18% /media/saucy
/dev/sdc13       23G  5.1G   17G  24% /media/raring

```

---

### Post by Hodevah on 2013-12-23
HI. I also use about 20 GB for my Ubuntu install and put everything else ( such as downloaded material - music, films, ebooks, etc, ) on an external HDD. I have a multi boot configuration that consists of about 5 different linux distros all each having about 20 GB each with the same intent to transfer everything elso onto another hard drive.

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        21G  6.1G   13G  33% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            7.9G   12K  7.9G   1% /dev
tmpfs           1.6G  1.3M  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            7.9G   92K  7.9G   1% /run/shm
none            100M   28K  100M   1% /run/user
/dev/sdb6       105G   19G   87G  18% /media/frankenstein/T Drive Alternate Storage #B
/dev/sdb5       194G   77G  118G  40% /media/frankenstein/T Drive Alternate Storage #A

```

I do it like this to make full use of my internal HDD of which the remaining 800 GB is also used for additional partitioning and/or for storage.

---

