---
title: "partition size"
date: 2008-06-23
forum: General Help
---

### Post by boxercbuk on 2008-06-23
Is there any way of increasing the partition size that ubuntu or do I need to set up a new partition

---

### Post by ajgreeny on 2008-06-23
You can probably use gparted on the live CD to do exactly what you want, but more info is needed before anyone can give you more details of what to do.  You certainly can not use your current ubuntu install to enlarge its own partition as it is impossible to work on a mounted partition.

From your ubuntu install use terminal and type```
 sudo fdisk -l
``` to show your current partition setup, copy the output here, and it may be possible to help further.

---

### Post by boxercbuk on 2008-06-23
what I would like to so is enlarge my home folder by nicking more space from my windows ntfs drive as I am finding I am now using ubuntu for larger and more complicated processes I could do with a bit more space eg converting to vob

here is a copy of the readout as requested any help would be appreciated
cheers steve

oot@stephen-desktop:/home/stephen# sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2dd82dd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         425       16907   132399697+   7  HPFS/NTFS
/dev/sda2               1         424     3405748+   b  W95 FAT32
/dev/sda3           16908       17034     1020127+  83  Linux
/dev/sda4           17035       19457    19462747+   5  Extended
/dev/sda5           19331       19447      939771   83  Linux
/dev/sda6           19448       19457       80293+  82  Linux swap / Solaris
/dev/sda7   *       17035       19228    17623242   83  Linux
/dev/sda8           19229       19330      819283+  82  Linux swap / Solaris

Partition table entries are not in disk order
root@stephen-desktop:/home/stephen#

---

### Post by vanadium on 2008-06-23
You can certainly rearrange your partitions using gparted running from a live CD. I see that your partition table is quite messy, however. You have three Linux partitions and two swaps. On a relatively small drive on a personal computer, one / and one swap, and perhaps one /home is all you need. I understand that your Ubuntu system is booting from /dev/sda7.

Partitions can easily be resized. However, if you need to move partitions, then you are facing a lengthy process. You will need to do that, because you want to shrink the Windows partition which comes earlier on the disk.

In your situation, I would just backup my user data stored under Ubuntu to an external disk, wipe partitions sda3 through 7 using gparted from the live CD, and make the ntfs partition (sda1) smaller (defrag first under Windows). Then reinstall Ubuntu, allowing the install program to reclaim all free space. In less than one hour, you will have a brand new clean system with all partitions in order.

If you let the install program handle things, you will probably have one system partition sda3 and one extended partition sda4 with the swap sda5. You still can partition yourself, e.g. creating a / (sda3, about 5 - 8 GB, and an extended partition including the /home (everything left minus 2 GB for the swap) and the swap (2GB). Then you need to choose manual partitioning and attach /, /home and swap to the respective partitions.

Also if you decide not to reinstall but to rearrange the partitions, we are available for advice and assistance: it can also work, only I would not prefer that route.

---

### Post by ajgreeny on 2008-06-23
If you've addedc lots of apps to your ubuntu install and don't want to bother downloading them all again, either use aptoncd from the repos to make a CD of all the packages or simply copy to a separate disk the contents of /var/cache/apt/archives.  Don't copy the "lock file, nor the /Partial folder  in there, as they are not needed.  Then when you've reinstalled you can either make aptoncd your first install and add the rest with that, or simply copy all the debs you copied from /var/cache/apt/archives back to the same place.  Now ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` should get you fully updated and ```
sudo apt-get install packagename
``` should install that package without having to download too much.

---

