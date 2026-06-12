---
title: "[SOLVED] mdadm / RAID 5 woes"
date: 2007-08-31
forum: General Help
---

### Post by mkramer on 2007-08-31
I've been trying to get a RAID 5 array set up on my ubuntu server.  I've succeeded in creating the array multiple times.  However, when I copy data to it, the superblocks get overwritten, and mdadm forgets how to assemble it.

I've been using this HOWTO that I found somewhere: [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188).  I only deviated from his instructions in two ways.  The first, is that I am creating a 6 disk array with 5 disks and one hot spare.  The second, is that the disks have two partitions on them.  The first partition is 10 gigs as ext3 and the second partition is the rest of the drive (~460gigs) as ext3.  It is the second partition that I am trying to raid up.

```
root@dark-genius:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406   83  Linux
/dev/sda2            1276       60801   478142595   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1275    10241406   83  Linux
/dev/sdb2            1276       60801   478142595   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1275    10241406   83  Linux
/dev/sdc2            1276       60801   478142595   fd  Linux raid autodetect

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        1275    10241406   83  Linux
/dev/sdd2            1276       60801   478142595   fd  Linux raid autodetect

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4863    39062016   83  Linux
/dev/hda2            4864        6687    14651280   83  Linux
/dev/hda3            6688        9729    24434865   82  Linux swap / Solaris

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        1275    10241406   83  Linux
/dev/sde2            1276       60801   478142595   fd  Linux raid autodetect

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        1275    10241406   83  Linux
/dev/sdf2            1276       60801   478142595   fd  Linux raid autodetect

```

I've gotten it to create, synchronize, and mount.  It always looks fine, but when I start copying data to it, it gets borked.  It appears that the data is overwriting the superblocks and corrupting the file system.  For instance, I just created the array again.  I formatted it as ext3, no problems.  I wait until it is done synchronizing.  I restart, and it automatically assembles and mounts.  Then I copied ~10 gigs of video data to the drive.  At first, that the data went through fine.  In fact, it shows up in the file, and when I try to play a video that is being stored on the array, it plays fine.  When I restart the server, the array does not assemble.  cat /proc/mdstat shows no active arrays.  I try to assemble it manually:

```
root@dark-genius:~# mdadm --assemble --scan
mdadm: No suitable drives found for /dev/md0
root@dark-genius:~# mdadm --assemble /dev/md0 /dev/sda2 /dev/sdb2 /dev/sdc2 /dev/sdd2 /dev/sde2 /dev/sdf2
mdadm: cannot open device /dev/sda2: No such file or directory
mdadm: /dev/sda2 has no superblock - assembly aborted

``` 

Furthermore, now when I look at the sd* drives with gparted, it says that the raid partitions are of an unknown filetype.  I don't know if that is expected after they've been assembled as a raid level block and then had a file system created on top.

If anyone can help me, I'd really appreciate it.

UPDATE:
As expected, sdf2, which was the hot-spare, has retained its superblock information.  When I tried creating a new array using the old partitions, I got this: ```
root@dark-genius:~# mdadm --create /dev/md0 --level=5 --raid-devices=5 --spare-devices=1 /dev/sda2 /dev/sdb2 /dev/sdc2 /dev/sdd2 /dev/sde2 /dev/sdf2
mdadm: Cannot open /dev/sda2: No such file or directory
mdadm: Cannot open /dev/sdb2: No such file or directory
mdadm: Cannot open /dev/sdc2: No such file or directory
mdadm: Cannot open /dev/sdd2: No such file or directory
mdadm: Cannot open /dev/sde2: No such file or directory
mdadm: /dev/sdf2 appears to contain an ext2fs file system
    size=478142592K  mtime=Wed Dec 31 19:00:00 1969
mdadm: /dev/sdf2 appears to be part of a raid array:
    level=raid5 devices=5 ctime=Thu Aug 30 15:08:22 2007
mdadm: create aborted

```
Something else that I don't understand.  mdadm says that sda1 and sda2 don't exist, whereas fdisk -l and gparted both see them.  Furthermore it looks like mdadm thinks that the physical device /dev/sda is what is part of the array, when really it should just be /dev/sda2.  Finally, it is clear that /dev/sd[abcde]1 are all corrupted, despite the fact that those partitions should have nothing to do with the raid array at all.  It seems like mdadm is treating the entire physical device as the raid device and writing data across the whole physical device, whereas when it created the array, it put the per-device superblocks just into the second partition, so they're all in the wrong place when it scans them.  If that makes any sense!  I honestly don't know much about hard drives and linux devices.
```

root@dark-genius:~# fsck /dev/sda1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: No such file or directory while trying to open /dev/sda1

root@dark-genius:~# fsck /dev/sdf1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sdf1: clean, 11/1281696 files, 78662/2560351 blocks

root@dark-genius:~# mdadm -Q /dev/sda2
mdadm: cannot open /dev/sda2: No such file or directory
root@dark-genius:~# mdadm --examine /dev/sda1
mdadm: cannot open /dev/sda1: No such file or directory
root@dark-genius:~# mdadm -Q /dev/sda
/dev/sda: is not an md array
/dev/sda: device 0 in 5 device undetected raid5 /dev/md0.  Use mdadm --examine for more detail.
root@dark-genius:~# mdadm --examine /dev/sda
/dev/sda:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 319a2e90:c54481ec:c21390a7:590b708d
  Creation Time : Fri Jul  6 13:23:42 2007
     Raid Level : raid5
    Device Size : 488386496 (465.76 GiB 500.11 GB)
     Array Size : 1953545984 (1863.05 GiB 2000.43 GB)     ##THIS IS NOT CORRECT, where did this superblock info come from?  
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Fri Jul  6 16:53:45 2007
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 65635bea - correct
         Events : 0.444

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        0        0      active sync   /dev/sda     ###This is not correct, I never (meant to have) specified any array with physical devices

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
   4     4       0        0        4      faulty removed
   5     5       8       64        5      spare   /dev/sde

##Examining the spare disk (which was not affected by the data copying test) reveals the desired array configuration
root@dark-genius:~# mdadm --examine /dev/sdf2
/dev/sdf2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a3bf904d:8d3842aa:46507cda:4bc69ba4
  Creation Time : Thu Aug 30 15:08:22 2007
     Raid Level : raid5
    Device Size : 478142528 (455.99 GiB 489.62 GB)
     Array Size : 1912570112 (1823.97 GiB 1958.47 GB)
   Raid Devices : 5
  Total Devices : 6
Preferred Minor : 0

    Update Time : Fri Aug 31 12:59:33 2007
          State : clean
 Active Devices : 5
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 1
       Checksum : 166a7c0c - correct
         Events : 0.60

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     5       8       82        5      spare   /dev/sdf2

   0     0       8        2        0      active sync   /dev/.static/dev/sda2
   1     1       8       18        1      active sync   /dev/.static/dev/sdb2
   2     2       8       34        2      active sync   /dev/.static/dev/sdc2
   3     3       8       50        3      active sync   /dev/.static/dev/sdd2
   4     4       8       66        4      active sync   /dev/.static/dev/sde2
   5     5       8       82        5      spare   /dev/sdf2

```

---

### Post by fjgaude on 2007-08-31
> Furthermore, now when I look at the sd* drives with gparted, it says that the raid partitions are of an unknown filetype. I don't know if that is expected after they've been assembled as a raid level block and then had a file system created on top

If anyone can help me, I'd really appreciate it.

I've looked over your approach and from what I see I don't see anything wrong. It is normal for Gparted to show raid drives as unknown filetypes, with or without files being copied to them.

So... where to go from here? I have a mdadm raid5 array working fine... the only difference is that I have only one partition for each drive, sda[b,c]1. I've been storing files on it for months, each drive is 300G. I don't boot from it but mount it in fstab on /home/raid, and everything sym linked to /home/frank. Works great with good speed.

If you are sure you followed the "approved" way to do it, then I don't have any suggestions, yet.

Oh, one thing... when you have a spare disk in an array don't you use the "missing" item in the array --create?

frank

---

### Post by mkramer on 2007-09-01
It appears that I have solved my own problem.  The problem seems to have been with mdadm.conf.  In the tutorial I read, these are the commands to generate the correct mdadm.conf file: 
```
sudo echo “DEVICE partitions” > /etc/mdadm/mdadm.conf
sudo mdadm –detail –scan >> /etc/mdadm/mdadm.conf
```.

I just copied them blindly without understanding them.  This was a gross display of laziness on my part and it bugged me at the time, but I went with it.  So when it went wrong, I remembered to check into that.  It was the "DEVICE partitions" directive that got me into trouble.  See, per the mdadm man page, if the config file contains that line, mdadm "will read /proc/partitions to find a list of devices to scan. "

Well, that works fine if you are using physical drives.  But in my case, it was scanning /proc/partitions and finding /dev/sd[abcdef] before it was found /dev/sd[abcdef]2.  Now, it is a bit puzzling that mdadm wasn't smart enough to get the correct raid data out of the per-device superblocks (I mean, I thought that was the point of per-device superblocks).  But I remade the array and generated a new mdadm.conf file using this single directive:
```
 mdadm --detail --scan --verbose > /etc/mdadm.conf 
```
The verbose form of --detail --scan also lists the correct devices and is conveniently  formatted to work as the mdadm.conf configuration file.   With the new, correct mdadm.conf, there is no problem when the array re-assembles (At least, after 24 hours and 150gigs of copied data, as well as dozens of restarts, the array seems to be just fine).  

I learned of the --verbose option from this[ mdadm howto]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Create_the_mdadm.conf_Configuration_File"),the best that I've seen while searching for solutions to problem.  Hoping this will be useful to someone,

Mason K

PS thanks for your interest, above poster.

---

### Post by fjgaude on 2007-09-01
So good to hear how you solved your problem... we are all learning as we go and the only way to really learn is to make mistakes. <smile>

Long live raid5 (and 6).

See you down the lines,

frank

---

