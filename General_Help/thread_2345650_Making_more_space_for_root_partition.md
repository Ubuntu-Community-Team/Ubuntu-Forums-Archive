---
title: "Making more space for root partition?"
date: 2016-12-06
forum: General Help
---

### Post by rawlins02 on 2016-12-06
In the recent past I've set my machines up with separate logical partitions for /home, /usr, swap, and root(/). On one, the root partition is 12 GB, and is now 95% full. In the past I've freed up space on /usr by deleting old OS images and headers. I'm looking for guidance on how to find and possibly remove excess "stuff" that may be filling up root partition. Before I dig around, I'll wait for your kind help...

---

### Post by gordintoronto on 2016-12-06
sudo apt-get clean

This will delete all the update .deb files you have installed over the years. Once installed, the .deb files serve no purpose.

---

### Post by Keith_Helms on 2016-12-07
Removing old kernels and headers is still something to do to reclaim space.  For instructions, read here:

[http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/)

---

### Post by rawlins02 on 2016-12-07
> **gordintoronto said:**
> sudo apt-get clean

This will delete all the update .deb files you have installed over the years. Once installed, the .deb files serve no purpose.


Yes. I did this yesterday. Gave me back about 1 GB. Still using 9.5 GB, and at 88% for the partition. Would like to make available a bit more space.

```

user@machine:~>df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.7G   12K  7.7G   1% /dev
tmpfs           1.6G  1.4M  1.6G   1% /run
/dev/sda6        12G  9.5G  1.5G  88% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            7.7G  2.1M  7.7G   1% /run/shm
none            100M   68K  100M   1% /run/user
/dev/sda5       147G  100G   40G  72% /home
/dev/sda7        14G  7.7G  5.0G  61% /usr

```

---

### Post by rawlins02 on 2016-12-07
> **Keith_Helms said:**
> Removing old kernels and headers is still something to do to reclaim space.  For instructions, read here:

[http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/)


I can't recall precisely, but I believe old kernels and headers are in /usr, which is mounted on another partition. Cleaning those up won't help with the root partition.

---

### Post by rawlins02 on 2016-12-08
> **Keith_Helms said:**
> Removing old kernels and headers is still something to do to reclaim space.  For instructions, read here:

[http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/)


OK. This solved the problem. Completely removing old images (linux-image) in Synaptic Package Manager has freed up 3.5 GB. The 12 GB root partition is now at 64%. Thanks for the help.

---

