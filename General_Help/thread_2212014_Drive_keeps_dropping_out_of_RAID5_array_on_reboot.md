---
title: "Drive keeps dropping out of RAID5 array on reboot"
date: 2014-03-18
forum: General Help
---

### Post by pieter3d on 2014-03-18
Ok I have a RAID 5 array in 13.10 that is misbehaving. I built this machine with 13.10 off an SSD, everything was fine. Then I added four 3TB drives in raid5 (mdadm), that all worked fine. Later, I added a 5th drive (same make/model). I follwed steps here to add, resync and grow the file system: [http://zackreed.me/articles/48-adding-an-extra-disk-to-an-mdadm-array](http://zackreed.me/articles/48-adding-an-extra-disk-to-an-mdadm-array)
Except I used gparted to resize the partition on the array, instead of the command line. Anyway, it all worked fine, and the mdadm --examine shows something like this (except all active)

```
root@media:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Mon Mar 10 18:38:05 2014
     Raid Level : raid5
     Array Size : 11720540160 (11177.58 GiB 12001.83 GB)
  Used Dev Size : 2930135040 (2794.39 GiB 3000.46 GB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Tue Mar 18 18:12:23 2014
          State : clean, degraded, recovering 
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

 Rebuild Status : 12% complete

           Name : media:0  (local to host media)
           UUID : be18ab92:4b232876:4fe30c80:9722f050
         Events : 96262

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       8       48        2      active sync   /dev/sdd
       4       8       64        3      active sync   /dev/sde
       5       8       80        4      spare rebuilding   /dev/sdf

```
It is currently rebuilding, but when it completes, all 5 drives will be active and everything works.
I have it automount with fstab:
```
UUID=8c1a0353-202a-4765-b787-5f35e77b3b2c /storage ext4 nosuid,nodev,nofail,x-gvfs-name=RAID5-Storage 0 0
```
My mdadm.conf has this:
```
ARRAY /dev/md0 metadata=1.2 UUID=be18ab92:4b232876:4fe30c80:9722f050
```

Then when I reboot the following things occur (this has happened several times now):
[LIST]
[*]Blank purple screen, nothing happens, no reaction. All I can do is ctrl-alt-del, which does another reboot. 
[*]Grub bootloader shows up (didn't used to before adding the 5th disk), I select Ubuntu. 
[*]I get a bunch of text on initramfs, and how the array is degraded, do I want to assemble anyway? I say yes 
[*]Assembly fails, I can finally login 
[*]Then I open a terminal, stop the array. /def/sdf is missing (this is the newer disk). I cannot assmble with /dev/sdf because "no raid superblock". 
[*] I assmble with the remaining 4 disks and --run to force it to assemble with 4 out of 5 disks, this works. 
[*]I can then mount and see my data, mdadm --detail shows degraded state, missing disk. 
[*]I add the /dev/sdf disk using mdadm --add, this works fine and starts the resync recovery. (mdadm --detail outputs the info above) 
[*]When the resync completes, everything is fine again, until next reboot. 
[/LIST]

What the hell is going on?? It is like the 5th disk, /dev/sdf isn't being written to, or at least isn't permanently marked as part of the array.

---

### Post by pieter3d on 2014-03-19
Ok some new data. The 5th drive I've been trying to add came out of a different system, and it had a GPT partition table on it. Before adding the drive to the array, I had prepared it by simply deleting all partitions on it (there was just one anyway), thinking that effectively wiped the drive. Turns out GPT itself is kind of hard to get rid of. I managed to finally remove it completely using the instructions here: [http://askubuntu.com/questions/211477/how-to-remove-gpt-from-hdd](http://askubuntu.com/questions/211477/how-to-remove-gpt-from-hdd)

So now, once again I have started the array with the 4 out of 5 disks, and added the now properly wiped 5th disk. It is resyncing once again, so in about 5 hours I will know if anything is better this time around.

---

### Post by pieter3d on 2014-03-19
Alright, problem solved. Turns out it was indeed the GTP on the 5th drive. Apparently mdadm superblocks don't persist when writing to a drive with one of those. This could be due to the fact that I was using the entire disk instead of a partition as the array members. Lesson learned: When building an array, use empty disks, not even a partition table.

---

