---
title: "AA custom partitioning schematic"
date: 2017-12-09
forum: General Help
---

### Post by pointy2 on 2017-12-09
The SSD model > SK hynix SC311 SATA 256gb 
I am preparing for a (good) clean install of AA after many conflicts have arisen. 

My question has to do with hierarchy of partitions. I want separate /home, /var, /tmp, and possibly a hidden volume at the end for encryption. 
I'm reading that /swap is not needed or desired on SSD's..Is this correct?

My partitions scheme is what I need advice on. This is what I have proposed.....and need guidance on. 
*boot/efi 750mb
/root       35gb
/var        10gb
/tmp       10gb
/home    remainder of drive minus 20gb to be encrypted separately from FDE.

Is this a do-able partitions scheme? should the /var and /tmp be place before, or after /home?

---

### Post by thanekrios on 2017-12-09
As far as I am concerned, the partitions order is irrelevant. However, some say that the swap partition should be at the end or the beggining of the drive in order to make it "easier to find". About the other partitions, every documentation I have read recommends a 20Gb root partition, so 35Gb seems like a lot, but maybe you have a reason for that.

Also, I can think of a reason why the swap partition should not be placed on the SSD: flash memory is "damaged" every time you erase something you wrote, and the swap partition, depending on the size of your main memory, should be getting a lot of writes periodically. For that reason, I usually have my swap partition on an HDD, the same for the /var and /home partition, since the main reason to get an SSD is to boot and open programs faster, and that's all in the / partition, so there is no need to store documents and images on the SSD, unless you do some video editing and need to process a lot of videos in a short time.

---

### Post by oldfred on 2017-12-10
There is not much advantage to separate /var. Another partition to manage size on. Your / (root) is large enough for most desktop installs. 
And with 17.04 or later, default install does not add swap, but uses swapfile. But if swap partition found it will use it.
       [http://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files](http://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files)

If you have enough RAM, swap will not be used, unless editing videos or similar that will use an unlimited amount of RAM.
Hibernation does require swap to be size of RAM, but hibernation not recommended. And if SSD, you will boot fast enough that hibernation does not save much if any time.

If you have lots of RAM, I have seen where tmp should be in RAM.

 # Reduce SSD wear - fstab entry
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0 
or

 default 4GB, other distributions use half of RAM as default
tmpfs      /dev/shm      tmpfs   defaults,size=4g   0   0 


 
 Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
Similar to what I do, except I do use ext4 , I use a daily cron task for TRIM, 
and I have Firefox on hard drive so no issues with cache. Swap is also on hard drive, but never used.
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by pointy2 on 2017-12-10
> **oldfred said:**
> There is not much advantage to separate /var. Another partition to manage size on. Your / (root) is large enough for most desktop installs. 
And with 17.04 or later, default install does not add swap, but uses swapfile. But if swap partition found it will use it.
       [http://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files](http://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files)

If you have enough RAM, swap will not be used, unless editing videos or similar that will use an unlimited amount of RAM.
Hibernation does require swap to be size of RAM, but hibernation not recommended. And if SSD, you will boot fast enough that hibernation does not save much if any time.

If you have lots of RAM, I have seen where tmp should be in RAM.

 # Reduce SSD wear - fstab entry
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0 
or

 default 4GB, other distributions use half of RAM as default
tmpfs      /dev/shm      tmpfs   defaults,size=4g   0   0 


Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
Similar to what I do, except I do use ext4 , I use a daily cron task for TRIM, 
and I have Firefox on hard drive so no issues with cache. Swap is also on hard drive, but never used.
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

This is what I was looking for oldfred. 

As for RAM, currently, there is 8gb DDR4, and have just bought another 8gb module to give it a whopping 16gb, so the /tmp will be pointed to RAM. I have looked in to this and have considered it (the reason for the upgrade RAM module). To clarify, do programs such as Gimp and Inkscape utilize /tmp files in order to work properly? Or, are those needed tmp files placed in another directory? As graphics go, I'll be using many vector and photo images, which are hungry for RAM, as well as using many bytes of data for storage.  

I'm glad you mentioned TRIM. I had TRIMed the SSD last night of 228gb of junk (probably from the win10 leftovers). The cron command is worth looking in to and would like to set it for automatic cleansing. 

You would recommend 20gb for /root? /tmp on RAM, /home > 20gb hidden (still need to figure that out). My reasoning for /var is in case of a crash, logs will go wild and it would be good to have a localized partition for such events.

---

### Post by oldfred on 2017-12-10
I normally suggest 25GB for /, but I have /home inside / and all data then in a /mnt/data partition on my HDD.
This system has 256GB SSD, and I do not know what to do with all the space. I normally have two LTS installs, currently 16.04 & 18.04. but will totally reinstall 18.04 when released, so as to houseclean the log files & many updates.
Never had issue with log files, but run a script to houseclean regularly which removes old log files.

New install is typically 4 to 5GB, but with a couple of years use / is now 12GB including /home, but no or little data. Even Firefox & Thunderbird profiles are in /mnt/data on HDD. The sdc is a 64GB flash drive for emergency use & with ISO for install or repair. And some data as backup. All the other installs are just test or experiments. I use 16.04 as main working install.

```
fred@Z170N:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.7M  1.6G   1% /run
/dev/sda2        30G   12G   18G  40% /
tmpfs           7.8G   49M  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
tmpfs           7.8G  8.0K  7.8G   1% /tmp
/dev/sda1        50G   54M   50G   1% /boot/efi
/dev/sdb6       202G   53G  140G  28% /mnt/data
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           1.6G   56K  1.6G   1% /run/user/1000
/dev/sdc3        36G   28G  6.8G  81% /media/fred/data64
/dev/sdc2        21G  4.9G   15G  26% /media/fred/xenial64
/dev/sdc1       499M   47M  453M  10% /media/fred/efi64
/dev/sdb9        25G  4.8G   19G  20% /media/fred/Fedora
/dev/sdb5        30G  7.9G   21G  29% /media/fred/server
/dev/sdb2        30G  5.0G   24G  18% /media/fred/zesty
/dev/sdb4        49G  7.9G   39G  17% /media/fred/backup_b

```

---

