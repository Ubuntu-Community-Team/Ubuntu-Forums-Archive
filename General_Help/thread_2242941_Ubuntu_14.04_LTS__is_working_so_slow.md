---
title: "Ubuntu 14.04 LTS  is working so slow?"
date: 2014-09-05
forum: General Help
---

### Post by shamsat on 2014-09-05
It is few months i installed the ubuntu 14.04 LTS to the ext4 file system, i use the ext4 file system to the all disks, at the begening every thing was ok, but now it is working so slow specialy when i copy or rsync files for example i copy the 1.6 GB to the external hard disk and it took nearly 10 minutes , some applications hang and then asking to "Force quit" the application, i install the updates frequnetly and my ubuntu is upto date with the latest kernel installed from the ubuntu official repos.
Tthese are the my Desktop PC details:

> 
Memory or RAM 1.9 GB with 3 GB swap space.
Processor Intel® Core™2 Duo CPU E7500 @ 2.93GHz × 2
Greaphics Intel® G41 x86/MMX/SSE2
OS Type 32-bit
Disk 31.9 GB


---

### Post by papibe on 2014-09-05
Hi shamsat.

As most filesystems, ext4 can get very slow if the partition is almost full, or it's running out of inodes (both in the destination and the root filesystem).

Could you open a terminal, run these commands, and post back the results (you can copy/paste the text)?
```
df -h /

df -i /

df -h /path/to/slow_partition

df -i /path/to/slow_partition
```
Regards.

---

### Post by shamsat on 2014-09-06
> 
# df -h /
/dev/mapper/vg01-lv01   30G   24G  4.8G  83% /

> 
df -i /
Filesystem             Inodes  IUsed   IFree IUse% Mounted on
/dev/mapper/vg01-lv01 1966080 303900 1662180   16% /

> 
# df -h /media/user/464e4b00-6244-48c1-a169-8e7bf2148966
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc3       275G  113G  149G  44% /media/user/464e4b00-6244-48c1-a169-8e7bf2148966

> 
# df -i /media/user/464e4b00-6244-48c1-a169-8e7bf2148966
Filesystem       Inodes IUsed    IFree IUse% Mounted on
/dev/sdc3      18317312 95863 18221449    1% /media/user/464e4b00-6244-48c1-a169-8e7bf2148966

It is working slow for the all partions but very slow for the externail hard disk  /media/user/464e4b00-6244-48c1-a169-8e7bf2148966.

---

