---
title: "Need help recovering partition D:"
date: 2013-05-09
forum: General Help
---

### Post by Reduced_Oxygen on 2013-05-09
OK so I was messing around in 'Disks' and I accidentally deleted my main partition. However I still have access to it as I have not restarted my computer, is there any way I might be able to recover it?


```

gilligan@ThinkPad-T430u:~$ sudo fdisk -l


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on a physical sector boundary.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdb: 24.0 GB, 24015495168 bytes
256 heads, 63 sectors/track, 2908 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x84a4d50e


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT


Disk /dev/mapper/ubuntu--vg-root: 991.3 GB, 991273418752 bytes
255 heads, 63 sectors/track, 120515 cylinders, total 1936080896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table


Disk /dev/mapper/ubuntu--vg-swap_1: 8422 MB, 8422162432 bytes
255 heads, 63 sectors/track, 1023 cylinders, total 16449536 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcdbb3411


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  1953523119   976760536    7  HPFS/NTFS/exFAT

```

---

### Post by oldfred on 2013-05-09
If not rebooted recover partition:
[http://ubuntuforums.org/showpost.php?p=10364557&postcount=34](http://ubuntuforums.org/showpost.php?p=10364557&postcount=34)


What does this show? with or without partition?
       sudo sfdisk -d /dev/sda

Once rebooted then testdisk.
      
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by Reduced_Oxygen on 2013-05-09
sudo sfdisk -d /dev/sda outputs:

```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.

# partition table of /dev/sda
unit: sectors


/dev/sda1 : start=        1, size=1953525167, Id=ee
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0

```

---

### Post by Reduced_Oxygen on 2013-05-09
the first link you sent me appears to be the solution to my problem, I'll try that and report back :D

---

### Post by Reduced_Oxygen on 2013-05-09
I am having the following probelm with fdisk:

```

Command (m for help): n
Partition type:
   p   primary (1 primary, 0 extended, 3 free)
   e   extended
Select (default p): p
Partition number (1-4, default 2): 3
No free sectors available

```

---

### Post by Reduced_Oxygen on 2013-05-09
OK i followed the directions in the first link of the first post in the thread except I used gdisk and set the partition to linux LVM which it was originally and i'm about to reboot...

wish me luck

---

### Post by oldfred on 2013-05-09
You show this:

   GPT (GUID Partition Table)

   Then all the fdisk tools will not work. You will have to use gdisk or sgdisk which is in repository.
In fact do not use Disks for creating nor deleting partitions, use gparted or gdisk. You can use disks for misc partition edits or other minor tasks.

three Linux partitioning tools: the fdisk family [fdisk, sfdisk, and cfdisk], the libparted family [GNU Parted, GParted, Palimpsest Disk Utility, and several others], and the GPT fdisk family [gdisk and sgdisk]. 

 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
      
 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

     


The post I linked you to, was from the author of gdisk, but he is not active in this forum anymore. So I do not know if from a gpt drive you can do something similar in seeing drives and then writing corrections with gdisk?

---

### Post by Reduced_Oxygen on 2013-05-09
I was using disks to format an sd card I do usally use gparted. 

gdisks works the same except you dont need -u as it uses sectors by default and instead of putting the length -1 after + you dont -1.

anyway as far as I know it should work, i'm just waiting for a backup to finish before i restart

---

### Post by Reduced_Oxygen on 2013-05-09
OK, so I rebooted a and nothing... not to be thwarted I booted a live CD and recovered my partition using test disk. I then rebooted to find grub missing. I booted my live CD again and found a nifty tool called boot-repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) it not only fixed the issue but also added secure boot support :D

However my laptop will no longer connect to the web via wifi or Ethernet, this may be unrelated though. I'll check again tomorrow as it is 4am

---

### Post by oldfred on 2013-05-09
I do not know Ethernet nor Wifi issues. Mine just work. Almost all have working Ethernet, but many have to download wifi drivers from System Settings, Software & Updates, Add'l Drivers tab. But that requires Ethernet connection.

If you still have issues start a new thread with the Ethernet chip & issue in title and attach this or search forum as there are many threads on wifi issues:
lspci > ~/abs-network.txt
lsusb >> ~/abs-network.txt
ifconfig >> ~/abs-network.txt
iwconfig >> ~/abs-network.txt
Attach (via the paperclip in advanced edit menu) the abs-network.txt file which will be in your home folder.

---

### Post by Reduced_Oxygen on 2013-05-10
i delete my networks and reconnected and now they work fine, all is well.

---

