---
title: "Help creating image of OS with partitions split in two disks?"
date: 2019-03-05
forum: General Help
---

### Post by usernamoi on 2019-03-05
Im unable to login to my ubuntu-studio, and i want to know how to properly make image files so i can keep trying to fix it. im dual booting with windows 8

My setup is as follows:
disk A
315mb
- /dev/sda1 -> boot partition 
1.5gb
- /dev/sda5 partition with folders ->  efi + grub 
30gb
- /dev/sda6 partition with folders -> bin home media mnt root 
40gb
- /dev/sda7 partition with folders -> username respin*
* i installed it before my problems to reach login screen, or mounting kernel, but didnt tested it

disk B
other partitions like 
- var
- swap

---

### Post by oldfred on 2019-03-05
Post this:
sudo parted -l

Current versions of Ubuntu do not need swap partition, and use a swap file. If swap partition is found it will be used.
Default install is now just / (root) as ext4 and if UEFI an ESP - efi system partition as FAT32.
Some users like to separate /home into another partition or have data partition(s), but unless a server most users do not need other separate system partitions.

My desktop uses a / partition of 25GB and I use 10 to 12GB of that, but have all data normally in /home in other data partition.

---

### Post by HermanAB on 2019-03-06
Basically, just copy the partition.  Yes, it really is that simple.

Boot up with a Linux install disk and explore the /dev directory to see what is there.  

Maybe the source disk is sda and the destination disk is sdb.  You can figure it out by looking at the size of the partitions.

You can copy a disk partition with cat:
# cat /dev/sda1 > /dev/sdb1/sda1.img

You can compress it with gzip:
# cat /dev/sda1 | gzip -9 > /dev/sdb1/sda1.img.gz

However, be very careful (The carpenter rule applies: Measure twice and cut once).  If you get the destination wrong, then it will be very disappointing...

---

### Post by usernamoi on 2019-04-09
Sorry for not answering sooner. i had lost my password for the forums.

i explain with more detail where im in relation to my problem(s) here:
[https://ubuntuforums.org/showthread.php?t=2414103](https://ubuntuforums.org/showthread.php?t=2414103)

---

### Post by oldfred on 2019-04-09
Thread closed, see other thread.

---

