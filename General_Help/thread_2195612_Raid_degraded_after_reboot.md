---
title: "Raid degraded after reboot"
date: 2013-12-25
forum: General Help
---

### Post by mail10 on 2013-12-25
Hi,

after every reboot i get a warning that my raid is degraded. After pressing "y" to start with the degraded raid everything looks fine. No rebuild is running.

Can someone help me?

```
micha@homeserver:~$ cat /proc/mdstatPersonalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sda1[0] sdb1[1] sdc1[3]
      3906763776 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]


unused devices: <none>



```

```

micha@homeserver:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Tue Dec 24 00:04:55 2013
     Raid Level : raid5
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent


    Update Time : Wed Dec 25 15:12:04 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : homeserver:0  (local to host homeserver)
           UUID : 0fd15a6a:13326c41:4bbefc8b:e2e4d74f
         Events : 60696


    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       3       8       33        2      active sync   /dev/sdc1



```

---

### Post by mail10 on 2013-12-25
I reboot my system not very often so its hard to tell what i have changed. 

I recreated my raid some days ago (completely from scratch). 
One thing i know is that in my fstab I dont mount by UUID anymore.

First I wanted to mount by UUID but something is wrong.
Everywhere I got this uuid:
```
micha@homeserver:/media$ sudo mdadm --detail /dev/md0/dev/md0:
        Version : 1.2
  Creation Time : Tue Dec 24 00:04:55 2013
     Raid Level : raid5
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent


    Update Time : Thu Dec 26 00:27:26 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : homeserver:0  (local to host homeserver)
           UUID : 0fd15a6a:13326c41:4bbefc8b:e2e4d74f
         Events : 60696


    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       3       8       33        2      active sync   /dev/sdc1



```

```
root@homeserver:/dev/disk/by-uuid# cat /etc/mdadm/mdadm.conf# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=0fd15a6a:13326c41:4bbefc8b:e2e4d74f name=homeserver:0



```

If I'm trying to mount it in my fstab with this uuid it doesnt work.

mount -a says that the device does not exist.

I dont know how mounting with uuid internal works but there is no device with this uuid here
```
root@homeserver:/dev/disk/by-uuid# ls -l /dev/disk/by-uuid/insgesamt 0
lrwxrwxrwx 1 root root  9 Dez 26 00:26 98bf3a2b-80bb-47f0-9253-ba01b8a19740 -> ../../md0
lrwxrwxrwx 1 root root 10 Dez 26 00:26 b41952fc-9f2f-45ba-b216-5106a013c167 -> ../../sdd1

```

The first UUID here should be the filesystem uuid. That one works in fstab but i got still the degraded raid error.

But normally mounting by "0fd15a6a:13326c41:4bbefc8b:e2e4d74f" should work or am I wrong?

---

### Post by mail10 on 2013-12-26
I fixed this by editing the mdadm-functions. Look here:
[http://ubuntuforums.org/showthread.php?t=1861516&page=2&p=11388915#post11388915](http://ubuntuforums.org/showthread.php?t=1861516&page=2&p=11388915#post11388915)

I dont understand why there is no fix from ubuntu side because the thread was created 2011 and now I got the same error.

---

