---
title: "[SOLVED] Problems installing another distro on the same Hdd"
date: 2008-07-06
forum: General Help
---

### Post by Sn3ipen on 2008-07-06
I want to install Both Fedora and Mandriva on my computer. I already have Ubuntu but i want Fedora just for testing and playing with so i don't break anything in my beloved Ubuntu, and i want Mandriva or Open Suse as my KDE distrobution. I haven't decided yet.

Here's the problem:
I first installed windows, then Ubuntu. I have already partitioned my Hdd so i have about 120gb unused space. But when i try to install one of those distro's the partitioning program in the live Cd's tells me that i cant have more than one Root "/" partition or something like that.

How can i solve this issue?

Thanks for any reply

---

### Post by sayakb on 2008-07-06
Check that the mountpoint for the Ubuntu's / is set to /media/something
You should have one / and one /home from the 120GB space you have. You can use the Ubuntu's swap space as Ferdora's or Mandriva's or Suse's. (you can have a common swap. **Do not** go for common /home or you may mix up config files for each OS)

---

### Post by Sn3ipen on 2008-07-06
I opened Gparted just to check but i couldn't find it in the mountpoint column. The "/" is set as root if you know what i mean? It wasn't anything before. I also tried to click on the unpartitioned space to see what happened if i try to create a new partition but it just told me that i couldn't have more than four primary partitions.

Now i have media/windoze, /, /home, swap and unpartitioned space.

Is there any way to move the prtitions to another place so i can create a new mountpoint?

I don't want to lose all my settings and stuff when i have "tweaked" Ubuntu the way i like it.

---

### Post by Sn3ipen on 2008-07-07
If i take a backup of the home folder and reinstall Ubuntu. Can i simply just paste it back and everything will be fine?

---

### Post by angry_johnnie on 2008-07-07
It looks like all your partitions are primary, according to the error you're getting.

The only thing you could do is erase at least one partition, and then create an extended partition out of all the unallocated space.

The easiest way to go, keeping all your data, would be to get rid of swap.

You can then create a new, logical, swap partition, inside the extended partition, along with any other ext3 partitions you want.

To get rid of swap from gparted, right click on it, and select **swapoff**, then erase it.

Right click on the unallocated space and create a new partition, but be sure to make it **extended**, instead of primary.

Extended partitions can be further divided into as many logical partitions as you need.

---

### Post by plucky on 2008-07-07
> Now i have media/windoze, /, /home, swap and unpartitioned space.


Can you post the output of ```
sudo fdisk -l
```

You are allowed a maximum of 4 primary partitions on your disk,but you can have one of those primary partitions as an extended partition,into which you can put many logical partitions.

Assuming your swap partition is in an extended partition,you can resize the extended partition to encompass the unallocated space and then add the extra partitions for your new distros.

If it is not an extended partition,you can delete your swap partition and create an extended partition to encompass the whole of the unallocated space.Then recreate the swap partition within the extended partition and the other partitions for your other distros.

Because you have changed partitions,it is likely the UUID of the **swap** partition has changed from what is in fstab file,so you will have to manually change it to reflect the new partition.


Good luck

---

### Post by Sn3ipen on 2008-07-07
Thanks allot for the help:) I'll try that.

---

### Post by Sn3ipen on 2008-07-07
Here's my disk info:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe5a8e5a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       16278    48829567+  83  Linux
/dev/sda3           16279       22357    48829567+  83  Linux
/dev/sda4           22358       23335     7855785   82  Linux swap / Solaris

Thanks for the info. I think i will just go for a clean install of Ubuntu in an Extended Partition too because i have way to much space used on the root"/" partition. At that time i didn't know that 10Gb is plenty enough space. :p

But will i loose any of the settings in Ubuntu if I just copy my /home/user/ folder and replace it with the other that will be there at the end of the reinstall?

---

### Post by angry_johnnie on 2008-07-07
Well... I wouldn't know about just replacing your old /home folder.  But, if you really plan to just reinstall, [this]("http://www.remastersys.klikit-linux.com/") is a really handy tool.

And, while we're at it, I would advise to install the other distros first, and leave ubuntu at the end.

Ubuntu is a very polite OS, it will recognize every other system in your hard drive and add it to grub.

I can't say the same about the others.

But, really, I wouldn't think reinstalling is absolutely necessary.  Make a backup, sure.  It's always a good idea anyway.  But try to just make another partition first.

Unless you really want to reinstall. :-)

Edit:  Looking at your fdisk, it seems like they are, in fact, all primary partitions.

---

### Post by Sn3ipen on 2008-07-07
Thanks allot for the help. :)

Ubuntu is The best community ever! IMHO!

---

