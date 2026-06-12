---
title: "How to Remove ~/.Private"
date: 2018-05-03
forum: General Help
---

### Post by Mark_in_Hollywood on 2018-05-03
When I did an install of this 16.04, I was using dd to bit copy from a metal to a silicon drive. The encryption was never used on the silicon drive.

How do I remove ```
.Private   10G  8.9G  576M  95% /home/mark?
```

```
mark@Lexington:~$ df -h
Filesystem           Size  Used Avail Use% Mounted on
udev                 3.9G     0  3.9G   0% /dev
tmpfs                793M  9.5M  784M   2% /run
/dev/sda1             10G  8.9G  576M  95% /
tmpfs                3.9G   26M  3.9G   1% /dev/shm
tmpfs                5.0M  4.0K  5.0M   1% /run/lock
tmpfs                3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0            87M   87M     0 100% /snap/core/4407
/dev/loop3           158M  158M     0 100% /snap/inkscape/4019
/dev/loop1            82M   82M     0 100% /snap/core/4206
/dev/loop2            87M   87M     0 100% /snap/core/4486
tmpfs                793M   88K  793M   1% /run/user/1000
/home/mark/.Private   10G  8.9G  576M  95% /home/mark
```

---

### Post by Xian on 2018-05-04
What is the output of this command:

```
ll ~/.Private
```

If output is a link to /home/.encryptfs then empty your DE's Trash folder.

---

