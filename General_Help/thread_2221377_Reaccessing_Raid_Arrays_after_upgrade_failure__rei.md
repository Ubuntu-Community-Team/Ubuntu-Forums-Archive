---
title: "Reaccessing Raid Arrays after upgrade failure / reinstall"
date: 2014-05-01
forum: General Help
---

### Post by tim8 on 2014-05-01
Had a bad upgrade to 14.04 from 13.10 - had to reinstall a new version of 14.04. I have two large raid 1 arrays on this computer - but of course, they are not currently accessible by the computer. How do I install a raid array that already has data on it? I had originally used mdadm to build the arrays

---

### Post by tim8 on 2014-05-01
When I run mdadm --examine on two of the (matching) arrays, I get the following. So I think I just need a way to combine them back into a single raid array.

 sudo mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : e0345de1:cd7bb215:604aad7e:b6df1dad
           Name : chasm:1  (local to host chasm)
  Creation Time : Wed Dec 11 14:36:53 2013
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 5860268032 (2794.39 GiB 3000.46 GB)
     Array Size : 2930133824 (2794.39 GiB 3000.46 GB)
  Used Dev Size : 5860267648 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ca986d9b:60f19d91:fdd45111:7c0395a6

    Update Time : Wed Apr 30 17:24:26 2014
       Checksum : 84f4a3e1 - correct
         Events : 219


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)
chasm:/etc/ssh$ sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : e0345de1:cd7bb215:604aad7e:b6df1dad
           Name : chasm:1  (local to host chasm)
  Creation Time : Wed Dec 11 14:36:53 2013
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 5860268032 (2794.39 GiB 3000.46 GB)
     Array Size : 2930133824 (2794.39 GiB 3000.46 GB)
  Used Dev Size : 5860267648 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 7792986c:e885911c:160bdecd:e08ff759

    Update Time : Wed Apr 30 17:24:26 2014
       Checksum : 5101f494 - correct
         Events : 219


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)

---

### Post by tim8 on 2014-05-01
Figured it out. It's just

mdadm --assemble --scan

That was easy (if nervewracking)

---

