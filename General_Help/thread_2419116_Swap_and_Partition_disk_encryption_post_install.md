---
title: "Swap and Partition disk encryption post install"
date: 2019-05-16
forum: General Help
---

### Post by grandadmiralthrawn2 on 2019-05-16
Hello,

I am currently running Ubuntu 19.04 and am interested in encrypting a swap partition as well as another "storage" partition.

The situation:

I have two disks, a SSD(where system is located) and a larger HDD (intended for storage). I opted to erase the entire disk and encrypt at install. Unfortunately, the installer only allowed to select one disk to erase and encrypt which was the SSD. On top of that, the swap partition that was created was only about 1GB in size ( this is a problem because I require one that is 8GB). It is rather too late to reinstall the system due to all of the work and configurations that will be lost if I need to reinstall so I would prefer to avoid reinstalling. 

What I would like to do:
Disable and/or delete the 1GB swap that is on my SSD and create an encrypted one on my HDD. Create an encrypted partition on my HDD and have it auto-mount on startup for easy access. 

Any help or opinions would be greatly appreciated. Please note that I am somewhere between a beginner to intermediate linux user and will require some patience.

Thank you

Sincerely,

Grand Admiral Thrawn

---

### Post by HermanAB on 2019-05-17
Regarding swap, everything you need to know is explained very nicely in 'man swapon'.

To sort out a problem like yours, I would grow the partition to encompass the whole disk, encrypt it, then make a swap file of 8 GB - which then will be encrypted since it resides on the encrypted disk.

---

### Post by Herman on 2019-05-19
I agree with HermanAB and would like to add a couple of further comments.
```
sudo apt install swapspace
```
You can just install swapspace by the above command. With swapspace, the swap files get created dynamically as needed and only a little bit more than the OS needs. I have been using it for years and it works great, I have never had any problems with it and performance is excellent. This not only saves a lot of space on SSDs, (they used to be very expensive), but I imagine it probably helps spread the wear out on the SSD, (I haven't read of anybody worrying much about that for a while though).
You can then edit your /etc/fstab and comment out your line for the swap area and delete your swap area.

That brings me to my next comment, if your installation is the standard LUKS encrypted LVM type that the Ubuntu installer offers, you will need LVM commands to remove your swap LV. The Ubuntu wiki is an excellent source of information on LVM, [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)  and there are plenty of other web pages and You Tubes on the subject.  It's best to learn LVM and practice with it on some disks with no data  and no operating system that you care about first though, and make sure  you back up your data before trying things on your real system, (as we  do with partition editors and so on). 

If you can learn how to use LVM, you will have no more problems with disk space and partitions because you can easily just delete all partitions on your other disk (hard disk) and create it as a PV, then extent your VG to include your HD, and finally extend  the LV your operating system is in over the hard disk as well. You can even add more hard disks later onif you want. Your encrypted file system in your LV will be able to span them all like one big partition.

---

