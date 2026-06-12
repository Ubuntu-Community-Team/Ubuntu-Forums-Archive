---
title: "Help with mdadm"
date: 2012-12-26
forum: General Help
---

### Post by tobiasgardner on 2012-12-26
Hi, I have problems to get my raid5 working :/

I have created a raid5 array with 3 disks and it was named /dev/md0 when it was created however, now it always comes up as /dev/md127

How do I change this?

Currently there is no /etc/mdadm/mdadm.conf file at all...


```
root@nas:~# ls -l /dev/md*
brw-rw---- 1 root disk 9, 127 Dec 26 10:02 /dev/md127

/dev/md:
total 0
lrwxrwxrwx 1 root root 8 Dec 26 10:02 nas:0 -> ../md127

```

```
root@nas:~# mdadm --detail --scan
ARRAY /dev/md/nas:0 metadata=1.2 name=nas:0 UUID=bca128c7:dd841b96:26ce92d0:3bc40947

```

```
root@nas:~# mdadm --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Sat Dec 22 08:36:48 2012
     Raid Level : raid5
     Array Size : 4294702080 (4095.75 GiB 4397.77 GB)
  Used Dev Size : 2147351040 (2047.87 GiB 2198.89 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Wed Dec 26 08:46:17 2012
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : nas:0  (local to host nas)
           UUID : bca128c7:dd841b96:26ce92d0:3bc40947
         Events : 20

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       3       8       33        2      active sync   /dev/sdc1

```

---

### Post by tobiasgardner on 2012-12-26
I will add another question to the above... How come that the array size is 4TB? I have 3x 3TB disks in RAID5 setup... It should (?) give me around 6TB usable space?
Regards, Tobbe G

---

### Post by tobiasgardner on 2012-12-26
Alright, first issue solved! Second question moved to own thread...

I created a /etc/mdadm/mdadm.conf file looking like this:
```
DEVICE partitions
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR root
ARRAY /dev/md0 metadata=1.2 UUID=bca128c7:dd841b96:26ce92d0:3bc40947

```

Earlier versions of my mdadm.conf file included a "name=..." between the metadata tag and the UUID tag on the ARRAY line... By removing this, it works!

Executed the "update-initramfs" after the update, do not know if this made any difference.

Regards, Tobbe G

---

