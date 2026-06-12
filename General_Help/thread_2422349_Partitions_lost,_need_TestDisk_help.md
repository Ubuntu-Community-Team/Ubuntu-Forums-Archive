---
title: "Partitions lost, need TestDisk help"
date: 2019-07-05
forum: General Help
---

### Post by meetdilip on 2019-07-05
I lost boot option for my laptop with Windows 10 and 18.04 dual boot. I installed Windows 10 and now I can at least work on recovering the lost partitions. When I checked, only 2 partitions were lost. 1 NTFS and 1 Ubuntu partition. When I try using TestDisk, it listed all partitions. But when I try to get 5 NTFS and 1 Linux partition back, it says bad structure

My disk is MBR and maybe because of that it allows to proceed with 4 Primary or 3 Primary and a Logical drive. Is there any methods using which I can have all of them back (as it was before ) ? I can skip Ubuntu partition for now from recovery. 

[IMG]https://i.imgur.com/WRCxzRD.png[/IMG]

"This PC" and "Disk Management" screenshots so that you can know what I have now working

[IMG]https://i.imgur.com/FgSEbMs.png[/IMG]

[IMG]https://i.imgur.com/M1uUFtM.png[/IMG]

---

### Post by oldfred on 2019-07-06
If you installed Windows 10 after corruption, you overwrote your old configuration. You really need to make repairs only from live installer or repair disks, so as not to overwrite anything on internal drive.

Structure does not look at all correct. But with testdisk the partitions you select to restore must match old configuration and testdisk may find multiple old configurations, so you just select partitions that do not overlap.
Best if you have back up of partition table structure to know which partition is which.
But some rules are that Windows only boots from primary partitions, you are showing multiple NTFS as logical? You can have NTFS as logical and even the c: drive as logical, but only if Boot partition is primary. 
You can only have 4 primary partitions, and one must the extended partition. Testdisk will not show extended, but will put all the logicals inside an extended. And then all logical partitions must be next to each other. 

Normal Windows install has the 100MB Boot partition first & then a large c: drive as second partition. But you have a large data partition as first? Did you install Windows yourself with another partition on drive. Or did your Windows 10 install overwrite most of old configuration?

---

