---
title: "Accessing NTFS Partition"
date: 2006-07-10
forum: General Help
---

### Post by Fatstink on 2006-07-10
Is it possible in Dapper Drake to access an NTFS Partition that holds my music and movies???  And if so How???

---

### Post by T700 on 2006-07-10
While Linux can read a NTFS partition, because MS has not released the specs, it can not write to it.

Paul

---

### Post by aysiu on 2006-07-10
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) will help you get read-only access.

---

### Post by Polygon on 2006-07-10
if you wish to have write access to your drive as well, you can backup everythin on that ntfs drive or partition, and reformat it as a fat32 partiton/drive, and then ubuntu will have read/write access to it

---

### Post by gruvsyco on 2006-07-10
[This]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only") worked wonderfully for me

---

