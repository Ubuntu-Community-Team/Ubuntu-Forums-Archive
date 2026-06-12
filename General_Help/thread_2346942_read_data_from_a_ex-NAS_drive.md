---
title: "read data from a ex-NAS drive"
date: 2016-12-20
forum: General Help
---

### Post by nknfive on 2016-12-20
Hello, 

I had a QNAP-TS 251 NAS with 2TB drives configured in RAID1. NAS stopped working suddenly, and is being RMAed to manufacturer. Now I would like to access the disk and take a copy of the data on them using my PC. I use ubuntu 16.04. 

The disks are indentified as sda, sdb while the large partitions are sda3 and sdb3. 
```

nknfive@Linux-WS:~$ sudo mdadm --examine /dev/sda3
/dev/sda3:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : 0e503ed2:b6cde734:cdd8595a:d7a5030e
           Name : 1
  Creation Time : Sun Apr 24 04:33:05 2016
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 3887119240 (1853.52 GiB 1990.21 GB)
     Array Size : 1943559616 (1853.52 GiB 1990.21 GB)
  Used Dev Size : 3887119232 (1853.52 GiB 1990.21 GB)
   Super Offset : 3887119504 sectors
   Unused Space : before=0 sectors, after=272 sectors
          State : clean
    Device UUID : e7b00e48:c2de50ae:2a72edbf:78ae9dc2


    Update Time : Tue Dec 13 15:23:40 2016
       Checksum : f7d5980a - correct
         Events : 1013




   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)


```

```

nknfive@Linux-WS:~$ sudo mdadm --examine /dev/sdb3
/dev/sdb3:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : 0e503ed2:b6cde734:cdd8595a:d7a5030e
           Name : 1
  Creation Time : Sun Apr 24 04:33:05 2016
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 3887119240 (1853.52 GiB 1990.21 GB)
     Array Size : 1943559616 (1853.52 GiB 1990.21 GB)
  Used Dev Size : 3887119232 (1853.52 GiB 1990.21 GB)
   Super Offset : 3887119504 sectors
   Unused Space : before=0 sectors, after=264 sectors
          State : clean
    Device UUID : 3f316951:15a55085:9761e078:cda8d67b


    Update Time : Tue Dec 13 15:23:40 2016
  Bad Block Log : 512 entries available at offset -8 sectors
       Checksum : 4a63c872 - correct
         Events : 1013




   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)


```

I wanted to mount just one drive as the data should be available on both (set as RAID1). 
```

nknfive@Linux-WS:~$ sudo mdadm -A -R /dev/md1 /dev/sda3
mdadm: /dev/md1 has been started with 1 drive (out of 2).
nknfive@Linux-WS:~$ sudo mount /dev/md1 /mnt/nas
mount: unknown filesystem type 'LVM2_member'

```

I tried installing LVM2 but still get the same error when I tried to mount. Could you please assist me on reading the data?

---

