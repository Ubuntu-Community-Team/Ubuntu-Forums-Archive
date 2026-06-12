---
title: "Problems with MDADM and NTFS in large raid"
date: 2018-04-18
forum: General Help
---

### Post by nsby7c on 2018-04-18
Hello! This is my first post on the forums with a question. I hope I didn't just throw chum into the water!

The issue: I am trying to set up a new raid after I decided to move away from my previous mdadm RAID5 (ntfs) setup in Ubuntu. Instead, I am planning to create one RAID0 (NTFS) and one RAID1 (ext4) in Ubuntu 16.04. It was easy to get the RAID1 working with ext4 - a breeze actually. However, I am repeatedly encountering issues with creating the RAID0 with NTFS formatting. I need NTFS formatting for easy access from a Windows environment... 

 ](*,) 

The issue pertains to the way in which the disks are being partitioned. Basically, they aren't formatting like they should be - no matter how I slice it. I've used mkfs.ntfs and the Disks feature to format the partition, but I keep getting multiple partitions with extremely inefficient organizational structures. I didn't face this same issue with my last 5x4TB NTFS mdadm setup. I'll detail what I did, step-by-step, and hopefully we can figure this out for me and other people who come across this post.

First, I did the following to create and format the initial RAID0:

 ```
~$ sudo mdadm --create --verbose /dev/md0 --level=0 --raid-devices=2 /dev/sdc /dev/sdd
~$ sudo mkfs.ntfs /dev/md0
```

The result was this strange formatting [!after waiting all night for the slow way!]. I could not format the 6TB partition when attempting to do so in Disks. Here is a visual:

[IMG]https://s14.postimg.cc/nqjm3mzz5/disks_info1.png[/IMG]


Mind you, I previously had a RAID5 setup with five 4TB disks, which allowed me to create one huge (12TB or 16TB) NTFS partition. I don't remember doing anything special and used the default allocation units. I did some DuckDuckGo-ing and wasn't able to really come across any concrete answers. However, the best guess was perhaps there was an issue with the default disk/FS organization during formatting as it pertains to chunk/allocation/cluster sizes. So, I started over to give NTFS some breathing room for larger partitions:

```
~$ sudo umount /dev/md0$ sudo mdadm --stop /dev/md0
~$ sudo mdadm --remove /dev/md0
~$ sudo mdadm --zero-superblock /dev/sdd
~$ sudo nano /etc/fstab [to remove md0]
~$ sudo nano /etc/mdadm/mdadm.conf [to remove md0]
```
~$ sudo mdadm --create --verbose --chunk=4096 /dev/md0 --level=0 --raid-devices=2 /dev/sdc /dev/sdd
~$ sudo mkfs.ntfs -c 4096 --fast -L RAID0 -F /dev/md0
[/CODE]


Result? Things looked promising at first:

```
$ cat /proc/mdstatPersonalities : [raid1] [raid0] [linear] [multipath] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid0 sdd[1] sdc[0]
      7813767168 blocks super 1.2 4096k chunks
      
md1 : active raid1 sdb[1] sda[0]
      3906887488 blocks super 1.2 [2/2] [UU]
      bitmap: 0/30 pages [0KB], 65536KB chunk

unused devices: <none>

~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Wed Apr 18 17:31:15 2018
     Raid Level : raid0
     Array Size : 7813767168 (7451.79 GiB 8001.30 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Wed Apr 18 17:31:15 2018
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
     Chunk Size : 4096K

           Name : GUTh768yg:0  (local to host GUTh768yg)
           UUID : f7484498:717f688a:7409de56:b295df7e
         Events : 0

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd

~$ sudo mdadm --examine /dev/sdc /dev/sdd
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f7484498:717f688a:7409de56:b295df7e
           Name : GUTh768yg:0  (local to host GUTh768yg)
  Creation Time : Wed Apr 18 17:31:15 2018
     Raid Level : raid0
   Raid Devices : 2

 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : d6ccac79:e83d78bd:70327bde:fe2dc9fc

    Update Time : Wed Apr 18 17:31:15 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 1d35558d - correct
         Events : 0
     Chunk Size : 4096K

   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f7484498:717f688a:7409de56:b295df7e
           Name : GUTh768yg:0  (local to host GUTh768yg)
  Creation Time : Wed Apr 18 17:31:15 2018
     Raid Level : raid0
   Raid Devices : 2

 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : b962b3f4:27ab86b4:151a4f67:4536d52d

    Update Time : Wed Apr 18 17:31:15 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 492a489b - correct
         Events : 0

     Chunk Size : 4096K

   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)

```


But, it was all a rouse! I was actually staring at horse manure. The disk was formatted the same as the other, with a huge 6TB partition that was unformatable "free space". It made multiple strange partitions on the disk - again:

```
~$ sudo mdadm -E /dev/md0/dev/md0:
   MBR Magic : aa55
Partition[0] :   1917848077 sectors at      6579571 (type 70)
Partition[1] :   1818575915 sectors at   1953251627 (type 43)
Partition[2] :           10 sectors at    225735265 (type 72)
Partition[3] :        51890 sectors at   2642411520 (type 00)

```



When running fdisk and lblk, it acknowledges the md0 size, but fdisk doesnt mention anything about the gargantuan amount of free space that is unable to be used. It mentions like 53MB of empty space or something - like >6TB missing is totally NBD.

```
~$ lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINTNAME                    
SIZE FSTYPE            TYPE  MOUNTPOINT
sdf                     3.7T                   disk  
sdd                     3.7T linux_raid_member disk  
&#9492;&#9472;md0                   7.3T ntfs              raid0 
  &#9500;&#9472;md0p2             346.1G                   md    
  &#9492;&#9472;md0p1             811.6G                   md    
sdb                     3.7T linux_raid_member disk  
&#9492;&#9472;md1                   3.7T ext4              raid1 
sde                   223.6G                   disk  
&#9500;&#9472;sde2                  488M ext2              part  /boot
&#9500;&#9472;sde3                222.6G LVM2_member       part  
&#9474; &#9500;&#9472;ubuntu--vg-swap_1     8G swap              lvm   
&#9474; &#9492;&#9472;ubuntu--vg-root   214.6G ext4              lvm   /
&#9492;&#9472;sde1                  512M vfat              part  /boot/efi
sdc                     3.7T linux_raid_member disk  
&#9492;&#9472;md0                   7.3T ntfs              raid0 
  &#9500;&#9472;md0p2             346.1G                   md    
  &#9492;&#9472;md0p1             811.6G                   md    
sda                     3.7T linux_raid_member disk  
&#9492;&#9472;md1                   3.7T ext4              raid1 

~$ sudo fdisk -l
Disk /dev/sdc: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sdd: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 7F72BF56-A8D4-43A8-BD8D-9D8E610615C1


Disk /dev/md0: 7.3 TiB, 8001297580032 bytes, 15627534336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4194304 bytes / 8388608 bytes
Disklabel type: dos
Disk identifier: 0x2052474d


Device     Boot      Start        End    Sectors   Size Id Type
/dev/md0p1         6579571 1924427647 1917848077 914.5G 70 DiskSecure Multi-Boot
/dev/md0p2      1953251627 3771827541 1818575915 867.2G 43 unknown
/dev/md0p3       225735265  225735274         10     5K 72 unknown
/dev/md0p4      2642411520 2642463409      51890  25.3M  0 Empty

```


Anyway, here are my questions:

1. Why the heck is NTFS eating up TERABYTES of space for the above md0p1 & mdop2? If it is for file system organization, that still seems incredibly excessive and definitely wasn't an issue with my huge NTFS 5x4TB RAID5 array from before. 

2. Why is it making a >6TB partition of "free space" that cannot be formatted?

3. Does this have anything to do with the organization of the RAID and disks during the mdadm or mkfs.ntfs process?

4. Is there any reason why an NTFS formatted RAID5 setup would differ compared to a RAID0/1 in relation to the disk organizational structures like clusters, chunks, etc?

Any help is greatly appreciated! I'm just trying to save my poor forehead from hitting the tabletop!

---

### Post by HermanAB on 2018-04-19
Err... if the disk drives are on a Linux system, then you should not use NTFS.  

If Windows connects to the Linux system over ethernet and a network file system such as SMB/CIFS/NFS, then Windows doesn't see which file system is used on the disks, so you can use Ext4, BtrFS, XFS, JFS... any reliable Linux file system.

---

