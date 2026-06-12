---
title: "Eliminating Windows 8 from dual boot"
date: 2013-10-12
forum: General Help
---

### Post by Alan_Furth on 2013-10-12
Hi all,

I started out with a dual boot on my brand new laptop and quickly realized that Ubuntu is definitely the thing for me, so I decided to eliminate Windows 8 alltogether.

I started by simply eliminating the partition where Windows 8 was located, which occupaied half of my hard drive, and expanded the Ubuntu partitition to take up the freed space. 

After a few days of operating without any problems, I went back to Gparted from a live USB and found that there were still three Windows-related partititions, which I deleted and now are available as unallocated space, as you can see in the screenshot attached.

I am now trying to allocate the unallocated space to my Ubuntu partitition, for which I understand I need to first move the unallocated partitions right next to the Ubuntu partitition so that I can resize the Ubuntu partition to take up the free space... but Gparted simply doesn't allow me to move any of the unallocated partitions!

Any help on how to solve this will be inmensly appreciated! (As well as any other suggestions you might have for optimizing the partition structure of my hard-drive, I am very new to all this stuff!)

Alan

---

### Post by Bucky Ball on 2013-10-12
Welcome. You need to boot from the LiveCD as partitions need to be _*unmounted*_ to manipulate. Impossible if you are trying to resize / (sda6 by the looks, which is exactly what you are trying to do).

So, boot from the LiveCD, 'Try Ubuntu', get to a desktop, open Gparted, right click and make sure partitions are unmounted (/swap = swapoff), delete /swap, extend sda6 over the free space leaving 4Gb at the end of the disk to recreate /swap. Done.

Be aware, you don't want more than four primary partitions or you are getting into other issues. What is sda3? (msftrs) Might be an idea to get rid of that and drag sda6 over that bit too, looks like it is Win related, but you better check before killing it. Someone who knows about these things might chime in. ;)

---

### Post by oldfred on 2013-10-14
The msftrs partition is for Windows to have space to write stuff. It must be before the first Windows data partition. It is somewhat like bios_grub partition as in gpt partitioning there is no space after the MBR for systems to write serial numbers or hidden data. We used to with MBR have grub2 write core.img after MBR sector and then Flexnet (manages DRM software) would write into sector 32 and conflict. 

All UEFI systems use efi partition or FAT32 partition with boot flag as place where boot files are. If you have a Windows folder you can remove it. Also UEFI firmware remembers entries and you may need to remove them with UEFI shell or efibootmgr.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

      
 # from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by Alan_Furth on 2013-10-18
Thank you guys! Now I have a new problem though, I can't boot my computer after upgrading to 13.04, here you have the link to the new thread in case you want to give me a hand on that one... cheers!

[http://ubuntuforums.org/showthread.php?t=2181567](http://ubuntuforums.org/showthread.php?t=2181567)

---

### Post by Alan_Furth on 2013-10-19
> **Alan_Furth said:**
> Thank you guys! Now I have a new problem though, I can't boot my computer after upgrading to 13.04, here you have the link to the new thread in case you want to give me a hand on that one... cheers!

[http://ubuntuforums.org/showthread.php?t=2181567](http://ubuntuforums.org/showthread.php?t=2181567)

In the end I was able to solve the boot issue (see linked thread) and afterwards I re-partitioned my hard drive as you recommended without major problems. I am attaching the a screenshot of the new partitions, I  a let me think I did a good job, but let me know what you think... thanks again y'all!

---

### Post by oldfred on 2013-10-19
Should work. 
But you have a Microsoft msftres flag on the / partition. I would be sure to remove flag so it is just a data partition. Partitioning with gpt uses long GUID codes to define partitions. The easier to understand flags or short codes are just for ease of use. And if GUID code is not correct it may cause issues later. I think just removing flag will revert it to a data partition.
Details if interested.
 [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)


I prefer smaller system partitions and separate /home or /mnt/data, but when I was a new user I just had / & swap for several years.

---

### Post by Alan_Furth on 2013-10-19
> **oldfred said:**
> Should work. 
But you have a Microsoft msftres flag on the / partition. I would be sure to remove flag so it is just a data partition. Partitioning with gpt uses long GUID codes to define partitions. The easier to understand flags or short codes are just for ease of use. And if GUID code is not correct it may cause issues later. I think just removing flag will revert it to a data partition.


Weird, when I use the live USB in order to launch Gparted and be able to modify the / partitition the flag does not show whatsoever. But if I boot normally without te live USB the flag reappears... am I supposed to remove it somehow without using the live USB?

---

### Post by Alan_Furth on 2013-10-19
> **Alan_Furth said:**
> Weird, when I use the live USB in order to launch Gparted and be able to modify the / partitition the flag does not show whatsoever. But if I boot normally without te live USB the flag reappears... am I supposed to remove it somehow without using the live USB?

Never mind! I just removed it without using the live USB, somehow it didn't occur to me I would be able to :redface:

---

### Post by oldfred on 2013-10-20
Glad that worked.

Yes you cannot edit a partition you have already mounted with gparted. I install it in my working system just for my other drives, but have to use live flash drive or another drive install to edit my working install.

---

