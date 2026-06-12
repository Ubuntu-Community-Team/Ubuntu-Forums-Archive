---
title: "Swap disappeared, suddenly formatted as hfs+"
date: 2014-01-04
forum: General Help
---

### Post by thommy3 on 2014-01-04
Hello everybody,


Today I noticed a somewhat weired problem on my Ubuntu 12.04 system.

Nautilus showed a 2GB hfs+ partition on the sidebar. But I don't have a hfs+ Partition on my system nor do I have any apple Devices or such stuff.

After checking the partition tables using 'blkid' command, I noticed this new partition had replaced my swap partition, which was exacly 2GB of size and had been setup together with the system.

I did not change any partion lately and the only thing I am aware of changing is the latest kernel update to 3.8.0-35


Can anyone tell me whats up with that or whether others have experienced this kind of bug before?

Thank you for any help

---

### Post by xangor on 2014-01-04
Same here. 
Even more. All my linux partitions disappeared. Only Windows partitions are existing. 
Also my GRUB is corrupted. 

As I remember yesterday I got Windows Update (I have dual system Windows 7 and Ubuntu 12.04 with grub). 
I read that Windows update might for some reason do that. Thank you windows for removing all my data from Linux partitions. 
Windows should not have right to do that !!!!!!!!!!  It is like removing Linux from my laptop (removing non-windows systems). 

Anyway, I am trying now to fix it. So far so good (almost half day of work now) 
After many google looking, I found this page: [http://answers.microsoft.com/en-us/windows/forum/windows_other-windows_update/how-to-fix-partitions-deleted-by-windows-update/1a879bcf-fceb-42f3-8e12-d23f4ff6d89c](http://answers.microsoft.com/en-us/windows/forum/windows_other-windows_update/how-to-fix-partitions-deleted-by-windows-update/1a879bcf-fceb-42f3-8e12-d23f4ff6d89c)

As I see I need to use program TestDisk 6.14 (thankfully it works under linux as I started Linux LiveCD) and it analyzes HDD cylinder by cylinder to find lost partitions :-)   [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Then I hope the MBR can be fixed. 
Then I hope boot-repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) can fix my grub. 

THANK YOU WINDOWS UPDATE for taking my saturday !!!!! and making me nervous that I lost my file. I hope I can still have it. !!!

and THANK YOU Christophe Grenier to make the testdisk program - thank you. And for guys who made boot-repair :-) 

I wrote this text as maybe someone else got this stupid Windows Update during new year eve 2014. 
I have nothing against Linux or Windows update - but please WINDOWS test it before launching !!!

---

### Post by sammiev on 2014-01-04
Is this with windows 8 or other?
Thanks

---

### Post by xangor on 2014-01-04
I have Windows 7 (I do not have Windows 8 and I do not want to)

And still did not recovered my linux partitions as the testdisk still cannot find LINUX SWAP partition. Still is scanning my HDD and I am learning the program how to use it.

---

### Post by deadflowr on 2014-01-04
> **thommy3 said:**
> Hello everybody,


Today I noticed a somewhat weired problem on my Ubuntu 12.04 system.

Nautilus showed a 2GB hfs+ partition on the sidebar. But I don't have a hfs+ Partition on my system nor do I have any apple Devices or such stuff.

After checking the partition tables using 'blkid' command, I noticed this new partition had replaced my swap partition, which was exacly 2GB of size and had been setup together with the system.

I did not change any partion lately and the only thing I am aware of changing is the latest kernel update to 3.8.0-35


Can anyone tell me whats up with that or whether others have experienced this kind of bug before?

Thank you for any help

Well the simple solution would be to reformat the newly made hfs parition as a linux-swap partition.
Then rerun the blkid command and copy the UUID for the new swap partition, then open the /etc/fstab file as root and replace the old UUID in the swap line with the new one.
Then load swap.
```
sudo swapon -a
```
should do.
I prefer to muck about my partitions with gparted, but others like the cli better.
I haven't ever had a swap partition change like that, but I have done new installs on a separate partition and then idiotically reformatted the swap partition, thus getting a new UUID which doesn't correspond to the one in fstab.

---

### Post by thommy3 on 2014-01-05
> **deadflowr said:**
> Well the simple solution would be to reformat the newly made hfs parition as a linux-swap partition.

Yes I know how to solve the partition issue. But I would like to know what caused it.

> **xangor said:**
> Same here. 
Even more. All my linux partitions disappeared. Only Windows partitions are existing. 
Also my GRUB is corrupted. 

As I remember yesterday I got Windows Update (I have dual system Windows 7 and Ubuntu 12.04 with grub). 


That is interesting. I have the same setup and was using Windows 7 yesterday, which is likely the time of the change.

And I also have experienced problems with grub, as it lists all entries twice. No other issues, it works though.

The link you provided is from 2010. Could be a simular problem, but I would really like to know for sure.


If you don't mind please tell us your exact partition setup.

Here is mine:

/dev/sda1: TYPE="ntfs"  <-- Windows 7 partition
/dev/sda5: TYPE="ext4"  <-- Ubuntu root partition
/dev/sda6: TYPE="hfsplus" <-- former swap partition
/dev/sdb: TYPE="ntfs" <-- Additional data disk/partition
/dev/sdc: TYPE="ntfs" <-- Backup disk/partition


It seems with my system, the only partition that was changed is swap partition.

---

