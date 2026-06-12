---
title: "rsync sent bytes more than expected?"
date: 2022-06-25
forum: General Help
---

### Post by David_Partridge on 2022-06-25
Using rsync to copy from ext4 with 5.4TB of data (according to df) to btrfs (empty).

```
root@charon:/home/amonra# rsync -ah -H -A -X --info=progress2 --stats /media/amonra/Seagate_16TB/. /shared/.
          5.83T  94%   98.05MB/s   15:45:32 (xfr#82268, to-chk=0/85332)    

Number of files: 85,332 (reg: 82,432, dir: 2,900)
Number of created files: 85,331 (reg: 82,432, dir: 2,899)
Number of deleted files: 0
Number of regular files transferred: 82,268
Total file size: 6.17T bytes
Total transferred file size: 5.83T bytes
Literal data: 5.83T bytes
Matched data: 0 bytes
File list size: 3.87M
File list generation time: 0.162 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 5.83T
Total bytes received: 1.61M

sent 5.83T bytes  received 1.61M bytes  102.84M bytes/sec
total size is 6.17T  speedup is 1.06
root@charon:/home/amonra# 

```

sent bytes seems a lot more that I would expect from df output?

---

### Post by TheFu on 2022-06-25
df doesn't work with btrfs.  Have to use a btrfs-specific command.  This is common with file systems that include complex volume management.

[https://superuser.com/questions/1290086/btrfs-no-diskspace-left](https://superuser.com/questions/1290086/btrfs-no-diskspace-left) tries to explain some ways that btrfs is different.

---

