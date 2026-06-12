---
title: "Removing Sabayon from Ubuntu / Sabayon Dual boot."
date: 2008-02-20
forum: General Help
---

### Post by poisonblack on 2008-02-20
Hi all.!

I recently installed Sabayon on my HDD which already has Ubuntu on it.They both exist on different partitions but share a common home partition.After trying it for a few days, I felt Sabayon isn't quite right for me and I would like to remove it.
I know that one way of doing it is reformatting the Sabayon partition.But I am bit skeptical about this method since sabayon shares /home with  Ubuntu.So can someone suggest a good method of removing sabayon from it's own partition as well as /home partition.?

Regards.
Poisonblack

---

### Post by ajgreeny on 2008-02-20
Run ubuntu and let's see the output of ```
sudo fdisk -l
``` which will let us know what partitions you have.  If, as you seem to be saying there are two / partitions, one for ubuntu and another for sabayon, plus a shared /home for both and of course at least one swap, it should be easy to delete the sabayon / partition and add it to the /home partition.  You would not need to uninstall sabayon, or anything like that, just delete the partition.  Your /home partition will then be used solely for ubuntu, and over time any changes made to config files or data files when using sabayon will be changed back to whatever you prefer in ubuntu.  This could be a salutary lesson in the inadvisability of sharing /home between different distros, but I hope all will work out for you.

---

### Post by njparton on 2008-02-20
If you don't have seperate /boot partitions then just delete the sabayon partition using gparted then remove the sabayon entries from menu.lst.

---

### Post by poisonblack on 2008-02-21
Here's the O/p of sudo fdisk -l
> poisonblack@poisonblack-PC:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37233722

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1421    11414151   83  Linux
/dev/sda2            2844        4865    16241715    5  Extended
/dev/sda3            1422        2843    11422215   83  Linux
/dev/sda5            2844        4801    15727603+  83  Linux
/dev/sda6            4802        4865      514048+  82  Linux swap / Solaris

Partition table entries are not in disk order
poisonblack@poisonblack-PC:~$ 


Here /sda1 is my Ubuntu partition  /sda3 is my Sabayon partition and /sda5 is my /home partition.[/sda2 is a container for /home and /swap.].So I will just go ahead and delete the Sabayon partition.But what needs to be done about the "sabayonuser" folder in my /home partition.?

Thanks.

---

### Post by plucky on 2008-02-21
poisonblack,

Before you delete your Sabayon partition, you might have to reinstall grub to point to the Ubuntu installation.If you installed Sabayon after Ubuntu,then the grub install is probably pointing to the Sabayon partition to find **menu.lst**.If you delete this partition, then you won't be able to boot.

Look [here](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD) for howto reinstall **Grub**.


Good luck

---

### Post by poisonblack on 2008-02-21
@ plucky:
 After I installed Sabayon, I restored back the Ubuntu-installed Grub since I wasn't very sure whether I would keep Sabayon.So no problems there:KS.

---

