---
title: "Low disk space warning despite plenty of space"
date: 2013-01-14
forum: General Help
---

### Post by woodyg on 2013-01-14
Hi,
I keep getting frequent warnings about Low Disk Space, such as this latest one:

> **The volume "home" has only 838.3 MB disk space remaining.**
You can free up disk space by...when I still had 12.59 GB unused on the home partition according to GParted. Yesterday I also ran into trouble when I was trying to save a VirtualBox session, as my computer claimed there was not enough space to complete the operation.

What is going on?

---

### Post by mcduck on 2013-01-14
Could you run "*df -h*" in a terminal to list your file systems and available space on them, and then post the output here so we can have a better look at what's going on?

---

### Post by woodyg on 2013-01-14
OK, according to this output, 100% is being used, but at the same time only 220GB is used out of 233GB. What is this discrepancy about?


> *Filesystem                          Size  Used Avail Use% Mounted on*
/dev/sda6                           9.8G  5.4G  4.0G  58% /
udev                                3.8G   12K  3.8G   1% /dev
tmpfs                               1.6G  944K  1.6G   1% /run
none                                5.0M     0  5.0M   0% /run/lock
none                                3.9G   80K  3.9G   1% /run/shm
**/dev/sda8                           233G  220G  798M 100% /home**
//192.168.1.200/m-backup  214G  161G   54G  75% /media/remote_lubuntu

---

### Post by Elfy on 2013-01-14
5% of a partition is kept so that there is room for root to manouevre. 

You can change that with tune2fs

```
sudo tune2fs -m 4 /dev/sda8
```

would set the value to 4%

```
sudo tune2fs -m 3 /dev/sda8
```

would set the value to 3%

I'd not change the value for a / drive though.

---

### Post by woodyg on 2013-01-14
> **Elfy said:**
> 5% of a partition is kept so that there is room for root to manouevre. 

You can change that with tune2fs

```
sudo tune2fs -m 4 /dev/sda8
```would set the value to 4%

```
sudo tune2fs -m 3 /dev/sda8
```would set the value to 3%

I'd not change the value for a / drive though.


OK. So roughly what values should one stick to? What is advisable? Is it something that should be based on the partition size, i.e. it should be a certain percentage, or is it more of a fixed value, i.e. X GB?

---

### Post by Elfy on 2013-01-14
It's more a percentage than a fixed size, root is not likely to need 5% of a 1Tb drive to enable it to still be able to boot and work in order to run if a user has filled /home.

My data drives are all set to 0% - but I don't use a separate /home, whether that makes any difference or not I am not sure of. 

[http://community.linuxmint.com/tutorial/view/1010](http://community.linuxmint.com/tutorial/view/1010)

This tends to imply that /home would be OK without the reserved space.

---

### Post by mcduck on 2013-01-14
On the other hand the performance of the Ext filesystems decreases when the drive is too full, and anything around 95% use definitely fits in that range. So instead of tweaking the percentage reserved for root user only, you might want to try to free someace on the partition...

---

### Post by woodyg on 2013-01-14
Thanks for all the info. I solved the problem by moving 50 GB to another HD. Should be enough until I upgrade the computer...

---

