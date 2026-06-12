---
title: "Identify which drives belog in which arrays and voliume groups?"
date: 2019-04-29
forum: General Help
---

### Post by rsteinmetz70112 on 2019-04-29
I have a machine with 4 identical drives. They are configured in two arrays with lvm2 volumes on each.

I have a condition now where each array has only one drive in it and the other two drives are not part of any array. However since the dives are identical and have identical partition table of identical sizes I'm having trouble figuring out which of the two drives goes with which array. 
```
# madam --assemble --scan 
```
doesn't seem to do anything

lsblk shows the drives but not how to connect the, /etc/mdadm/mdadm.config has the UUIDs of the arrays but not the component drives.
```

#lsblk
sda                  8:0    0 931.5G  0 disk
&#9492;&#9472;sda1               8:1    0 931.5G  0 part
  &#9492;&#9472;md127            9:127  0 931.4G  0 raid1
    &#9500;&#9472;system-root  252:0    0   100G  0 lvm   /
    &#9500;&#9472;system-home  252:1    0 465.7G  0 lvm
    &#9500;&#9472;system-tmp   252:4    0    20G  0 lvm   /tmp
    &#9500;&#9472;system-var   252:5    0    20G  0 lvm   /var
    &#9500;&#9472;system-swap  252:6    0    20G  0 lvm   [SWAP]
    &#9492;&#9472;system-files 252:7    0 305.7G  0 lvm
sdb                  8:16   0 931.5G  0 disk
&#9492;&#9472;sdb1               8:17   0 931.5G  0 part
  &#9492;&#9472;md0              9:0    0 931.4G  0 raid1
    &#9500;&#9472;data-files   252:2    0 465.7G  0 lvm   /files
    &#9492;&#9472;data-home    252:3    0 465.7G  0 lvm   /home
sdc                  8:32   0 931.5G  0 disk
&#9492;&#9472;sdc1               8:33   0 931.5G  0 part
sdd                  8:48   0 931.5G  0 disk
&#9492;&#9472;sdd1               8:49   0 931.5G  0 part
```
 /etc/mdadm/mdadm.config has the UUIDs of the arrays but not the component drives.
```
# definitions of existing MD arrays
ARRAY /dev/md/127  metadata=1.2 UUID=62e8c83e:98d1093b:2a89aba2:44f9b1f1 name=louise:127
ARRAY /dev/md/0  metadata=1.2 UUID=ad32c1d1:9a121767:2cfa8c9a:b11ece14 name=louise:0
```

Mdadm shows the following detail:

```
# mdadm --detail /dev/md0
/dev/md0:
           Version : 1.2
     Creation Time : Sun May 20 10:59:09 2018
        Raid Level : raid1
        Array Size : 976629760 (931.39 GiB 1000.07 GB)
     Used Dev Size : 976629760 (931.39 GiB 1000.07 GB)
      Raid Devices : 2
     Total Devices : 1
       Persistence : Superblock is persistent

     Intent Bitmap : Internal

       Update Time : Mon Apr 29 11:27:36 2019
             State : clean, degraded
    Active Devices : 1
   Working Devices : 1
    Failed Devices : 0
     Spare Devices : 0

Consistency Policy : unknown

              Name : louise:0  (local to host louise)
              UUID : ad32c1d1:9a121767:2cfa8c9a:b11ece14
            Events : 254881

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       -       0        0        1      removed
# mdadm --detail /dev/md127
/dev/md127:
           Version : 1.2
     Creation Time : Sat Apr 14 12:45:49 2018
        Raid Level : raid1
        Array Size : 976629760 (931.39 GiB 1000.07 GB)
     Used Dev Size : 976629760 (931.39 GiB 1000.07 GB)
      Raid Devices : 2
     Total Devices : 1
       Persistence : Superblock is persistent

     Intent Bitmap : Internal

       Update Time : Mon Apr 29 11:29:38 2019
             State : clean, degraded
    Active Devices : 1
   Working Devices : 1
    Failed Devices : 0
     Spare Devices : 0

Consistency Policy : unknown

              Name : louise:127  (local to host louise)
              UUID : 62e8c83e:98d1093b:2a89aba2:44f9b1f1
            Events : 2806708

    Number   Major   Minor   RaidDevice State
       -       0        0        0      removed
       1       8        1        1      active sync   /dev/sda1
```

---

### Post by rsteinmetz70112 on 2019-04-29
Solved it 

```
# mdadm --examine <device> 
```
Provides both the UUID and Array name in it's output.
```
# mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : **62e8c83e:98d1093b:2a89aba2:44f9b1f1**
           Name : **louise:127  (local to host louise)**
  Creation Time : Sat Apr 14 12:45:49 2018
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 1953259520 (931.39 GiB 1000.07 GB)
     Array Size : 976629760 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 88518b98:87ad5aab:24bdc8d0:81e0afe7

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Apr 29 11:56:32 2019
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : eed51969 - correct
         Events : 2807213


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)

/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID :** 62e8c83e:98d1093b:2a89aba2:44f9b1f1**
           Name : **louise:127  (local to host louise)**
  Creation Time : Sat Apr 14 12:45:49 2018
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 1953259520 (931.39 GiB 1000.07 GB)
     Array Size : 976629760 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 6601b36e:7fa6a731:70038aa8:246c5908

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Apr 29 11:58:02 2019
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 43b49486 - correct
         Events : 2807213


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
```

At that point simply:

```
# mdadm /dev/md127 --add /dev/sdc1
# mdadm /dev/md0 --add /dev/sdd1
```

I created a file /etc/mdadm listing the devices and their UUIDs so if this happens again I know where to go. I don't understand how it happened. The missing drives were listed as "removed".

---

