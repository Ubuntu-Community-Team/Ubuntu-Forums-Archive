---
title: "Invalid Partition Table - how to recover partition table?"
date: 2013-01-30
forum: General Help
---

### Post by marcXIchor on 2013-01-30
I have a laptop HP 550. It came with preinstalled Windows Vista. Because has just only 1GB RAM I installed XP Professional and kept vista recovery partition. I decided to install Ubuntu 12.04 as I have it on other laptop where is working fine. After installation I rebooted laptop
and automatically started Windows without screen with dual boot option.
Like Ubuntu was not installed at all. But on drive C: is Ubuntu folder with files ...
I could not figured out why it couldn't load dual boot screen. I 'played' with diskpart command for command prompt and I found partitions. I suggested that maybe because Ubuntu partition is not active. I activated and from then I lost access to boot. Non-System disk or disk error
                 replace and strike any key when ready
I did try fixboot and fixmbr but unsuccessful. I think boot sector been written to removable USB flash drive with fixboot and fixmbr under win XP recovery console. So I tried to preinstalled XP, I tried to install it to Ubuntu partition that maybe I will start everything again, (win XP and Ubuntu). Because I didn't want to touch C: drive. I'm afraid to tried fixmbr or fixboot again because HDD looks like 1 partition. Now I have:
                          Invalid partition table
 and I can boot Ubuntu just only from cd. I need to repair partition table back as it was. Or best as it possible. Or save data from drives.



ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?   218129509  1920119918   850995205   72  Unknown
/dev/sda2   ?   729050177  1273024900   271987362   74  Unknown
/dev/sda3   ?   168653938   168653938           0   65  Novell Netware 386
/dev/sda4      2692939776  2692991410       25817+   0  Empty

Partition table entries are not in disk order


ubuntu@ubuntu:~$ sudo sfdisk -l 

Disk /dev/sda: 14593 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   ?  13577+ 119521- 105945- 850995205   72  Unknown
                start: (c,h,s) expected (1023,254,63) found (368,111,45)
                end: (c,h,s) expected (1023,254,63) found (371,101,51)
/dev/sda2   ?  45381+  79242-  33861- 271987362   74  Unknown
                start: (c,h,s) expected (1023,254,63) found (67,115,32)
                end: (c,h,s) expected (1023,254,63) found (299,114,44)
/dev/sda3   ?  10498+  10498-      0          0   65  Novell Netware 386
/dev/sda4     167627+ 167630-      4-     25817+   0  Empty
                start: (c,h,s) expected (1023,254,63) found (0,0,0)
                end: (c,h,s) expected (1023,254,63) found (0,0,0)


ubuntu@ubuntu:~$ sudo cfdisk 

               FATAL ERROR: Cannot open disk drive
                  Press any key to exit cfdisk

---

### Post by dino99 on 2013-01-30
trying to repair (rebuilt) the partition table (with a formatting tool) first, then formatting again will drop your data (quite scary)

how/where is installed ubuntu ? is it a hard install (real) or inside windows (wubi) ?

---

### Post by marcXIchor on 2013-01-30
how/where is installed ubuntu ? is it a hard install (real) or inside windows (wubi) 

I prepared 29GB for Ubuntu. But it was under win XP so it was NTFS I think.
I runned installation from cd but after restart nothing happen just boot straight to win without any option for dual boot, so if I remember I tried to install it under windows again. same result.
but at the moment what I need to recover is win files. After that I will reinstall both systems.

---

### Post by Mark Phelps on 2013-01-30
Your original Wubi install was INSIDE C: -- because Wubi installs to a virtual file INSIDE a Windows partition.  There is NO Ubuntu partition.  Since you were running XP, it should have modified the boot.ini file to add a line for Ubuntu.  Had you stopped there, we probably could have fixed it.

Then, you did ANOTHER install, this time from CD, right?  This would require its own Linux partition.  You didn't say how you created space for that partition.

Your repeated installing and reinstalling basically hosed it up big time.  Hammering away like this nearly always hurts more than it helps.

But, what you SHOULD have ended up with is two Ubuntu installs, one inside Windows, the other to another partition.

When you moved the active flag, you BROKE Windows.  It requires that the boot partition be marked active in order to boot.  Once again, if you hadn't just hammered away, we could have fixed this.

Folks here may be able to tell you how to use Testdisk to get your partitions back, but you've pounded it so much, I doubt anything is going to be recoverable.

---

### Post by marcXIchor on 2013-01-30
I had working boot after unsuccessful installation of Ubuntu. After that I tried to fixboot and fixmbr but it wrote to flash drive. So when I tried to install it the HDD has messed size. there was abnormal high size of partitions inside of HDD.
so I tried to install XP to partition where was Ubuntu. And after that I have invalid partition table.
I broke win after installation of ubuntu. so there was just one unsuccessful installation of XP. HDD looks like is just one partition. but fdisk returned couple of partitions.
there were before: sda1 C: (win)
                              sda2 E: /ntfs
                              sda3 F: /ntfs
                              sda4  UBUNTU
                              sda5  UBUNTU

and I activated sda4

---

### Post by oldfred on 2013-01-30
As Mark Phelps stated, active partition or boot flag is used by Windows to know what partition to boot from. And if you install multiple copies of Windows all the boot files are in just the one boot partition.

Testdisk may be able to rewrite a partition table. But with all the changes you have made it will find multiple versions and you have to select a consistent version or one with no overlapping sectors. If you select NTFS correctly to what worked it may boot, but almost always requires Windows repairs as NTFS has to have correct partition size inside its partition boot sector.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

    
       Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by marcXIchor on 2013-01-30
thanks for help... I will have a look for TestDisk.
I believe there is way to recover it. fdisk can see partitions. 

but thank you anyway, for your time and effort.

---

### Post by Mark Phelps on 2013-01-30
Another suggestion to consider ...

Windows utilities are generally best at recovering Windows partitions ... so, you should Google for Minitool Partition Wizard Boot CD, download the ISO and burn it to CD.  Then boot from that CD.

If I remember correctly, there is an option to recover old partitions -- which may work.

---

### Post by marcXIchor on 2013-01-30
I found more live cd versions of TestDisk on

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)



start burning BootMed 1.1 but don't know what is going on, because is 2nd try to burn it and speed is around 1MB/2.5min ...
cd has 675 MB ... I'm on 117MB ...


so I'm going for your option ... Minitool Partition Wizxard Boot CD ... has 42.6MB
thanks a lot ... will see what can I do ...

---

### Post by Mark Phelps on 2013-01-31
Sorry ... misspelled the name.  It is Minitool Partition Wizard Boot CD.

---

