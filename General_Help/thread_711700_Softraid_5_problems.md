---
title: "Softraid 5 problems"
date: 2008-02-29
forum: General Help
---

### Post by Muntted on 2008-02-29
Im having some problems with setting up a raid 5. I have 4 drives, three of which (sda. sdb. sdc) I want to have in the raid and the other (sdd) has my data. Ill post what goes in and out of terminal and see if you guys can spot the problem... Thanks

> ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000359e3

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f3534

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04fcf498

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x984b777e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       91201   732572001   83  Linux
root@ubuntu:/home/ubuntu# fdisk /dev/sda

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-60801, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-60801, default 60801): 
Using default value 60801

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): fd
Changed system type of partition 1 to fd (Linux raid autodetect)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
root@ubuntu:/home/ubuntu# fdisk /dev/sdb

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-60801, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-60801, default 60801): 
Using default value 60801

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): fd
Changed system type of partition 1 to fd (Linux raid autodetect)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
root@ubuntu:/home/ubuntu# fdisk /dev/sdc

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-60801, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-60801, default 60801): 
Using default value 60801

Command (m for help): 
Command (m for help): t
Selected partition 1
Hex code (type L to list codes): fd
Changed system type of partition 1 to fd (Linux raid autodetect)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.


So thats all done, now when I go to make the array, It seems to be picking up something wrong and does not rport correct size or something. Note, 2 of the drives have been in a raid before but have since been formatted.
> root@ubuntu:/home/ubuntu# mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: /dev/sda1 appears to contain an ext2fs file system
    size=488384000K  mtime=Thu Jan  1 00:00:00 1970
mdadm: /dev/sda1 appears to be part of a raid array:
    level=raid5 devices=3 ctime=Fri Feb 29 14:16:52 2008
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=488384000K  mtime=Thu Jan  1 00:00:00 1970
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid5 devices=3 ctime=Fri Feb 29 14:16:52 2008
mdadm: /dev/sdc1 appears to contain an ext2fs file system
    size=488384000K  mtime=Thu Jan  1 00:00:00 1970
mdadm: size set to 488383936K
Continue creating array? 


---

### Post by SpaceTeddy on 2008-03-01
i have not really worked with the commandline utility of mdadm, but i think you need to properly delete the old array before you can create a new one.
A different method would be to delete all partitions on the drives entirely (wipe them clean with DBAN or so) and try fresh.

Don't know if that helps...

---

### Post by fjgaude on 2008-03-01
I would continue to have the array build. Then after the assemble set the file system using:

```
sudo mkfs -t ext3 /dev/md0
```

If that doesn't work, then you might have to zero the superblocks using:

```
sudo mdadm --zero-superblock /dev/sda1
```

Do this to all three drives, one by one. Then create the array once more.

Let us know how you are doing.

---

### Post by Muntted on 2008-03-03
Ok, I managed to get the raid going. Pretty much by formatting and then trying to re raid the drives multiple times.
Then i proceeded to load my data onto the raid and format my other drive.
Now ubuntu is reinstalled I am trying to reassemble the raid... but Im having problems:
> matt@Prometheus:~$ sudo mdadm --assemble --scan
mdadm: failed to add 8:17 to /dev/md0: Device or resource busy
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.
matt@Prometheus:~$ sudo cat /proc/mdstat 
Personalities : 
md0 : inactive sdd1[2](S) sdc1[1](S)
      976767872 blocks
       
unused devices: <none>
matt@Prometheus:~$ sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0
matt@Prometheus:~$ sudo mdadm --assemble --force /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: no recogniseable superblock on /dev/sdb1
mdadm: /dev/sdb1 has no superblock - assembly aborted


So do I have to zero the superblocks on the drives and rewrite them? What happens to my data on the drives?

---

### Post by Muntted on 2008-03-03
should I?
> 
sudo mdadm --assemble /dev/md0 /dev/sdc1 /dev/sdd1
sudo mdadm --re-add /dev/md0 /dev/sdb1

Or should I zero the superblock first.
Can I recover the data on the drives?

---

### Post by fjgaude on 2008-03-03
> **Muntted said:**
> should I?

Or should I zero the superblock first.
Can I recover the data on the drives?

I don't understand why you had to do multiple assemble on the array before it worked?

When you first zeroed the superblocks on each drive and then created the array did you make sure the array was fully assembled before doing something to it? Did you do a 

```
sudo watch cat /proc/mdstat
```

Seems like your array is not really there with two or three of the drives not active.

---

### Post by Muntted on 2008-03-03
No where I read said anything about zeroing the superblocks on the drives. The raid better be there as it is where all my data is stored.

What can I do to recover from this?

---

### Post by Muntted on 2008-03-03
I have started the array in a degraded mode, but I still cant seem to mount it:
> matt@Prometheus:~$ sudo mdadm --assemble /dev/md0 /dev/sdc1 /dev/sdd1
mdadm: /dev/md0 assembled from 2 drives - need all 3 to start it (use --run to insist).
matt@Prometheus:~$ sudo mount /dev/md0 /media/raid/
mount: you must specify the filesystem type
matt@Prometheus:~$ sudo cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] 
md0 : inactive sdc1[1](S) sdd1[2](S)
      976767872 blocks
       
unused devices: <none>
matt@Prometheus:~$ sudo mdadm --run /dev/md0
mdadm: started /dev/md0
matt@Prometheus:~$ sudo cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid5 sdc1[1] sdd1[2]
      976767872 blocks level 5, 64k chunk, algorithm 2 [3/2] [_UU]
      
unused devices: <none>
matt@Prometheus:~$ sudo mount /dev/md0 /media/raid/
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

matt@Prometheus:~$ dmesg | tail
[55576.176000] raid5: device sdc1 operational as raid disk 1
[55576.176000] raid5: device sdd1 operational as raid disk 2
[55576.180000] raid5: allocated 3163kB for md0
[55576.180000] raid5: raid level 5 set md0 active with 2 out of 3 devices, algorithm 2
[55576.180000] RAID5 conf printout:
[55576.180000]  --- rd:3 wd:2
[55576.180000]  disk 1, o:1, dev:sdc1
[55576.180000]  disk 2, o:1, dev:sdd1
[55582.848000] JBD: no valid journal superblock found
[55582.848000] EXT3-fs: error loading journal.
matt@Prometheus:~$ 


---

### Post by fjgaude on 2008-03-03
> **Muntted said:**
> No where I read said anything about zeroing the superblocks on the drives. The raid better be there as it is where all my data is stored.

What can I do to recover from this?

I think when you re-read one of my early posts, msg #3, to you, I said to zero the superblocks, drive by drive, to get to create the array.

When and how did data get copied to the array?

---

### Post by Muntted on 2008-03-03
Yeah I read that, but I managed to get the array going as I posted earlier by just trying multiple times.
Since then I have copied my data onto the array.

I have been talking to cody-somerville on the irc forum and he got me to do the following:
[http://paste.ubuntu-nl.org/58307]("http://paste.ubuntu-nl.org/58307")
[http://paste.ubuntu-nl.org/58310]("http://paste.ubuntu-nl.org/58310")
[http://paste.ubuntu-nl.org/58311]("http://paste.ubuntu-nl.org/58311")
[http://paste.ubuntu-nl.org/58312]("http://paste.ubuntu-nl.org/58312")
This info shows that something has happened to the partition on the /dev/sdb drive. The data should be there but i guess some of the headers or somethign has gone missing

he has since admitted it goes over his head.

Could anyone else enlighten me
Is it safe or recommended to do an e2fsck on the degraded array?

---

