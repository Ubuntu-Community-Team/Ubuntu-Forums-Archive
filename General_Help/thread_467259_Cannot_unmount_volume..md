---
title: "Cannot unmount volume."
date: 2007-06-07
forum: General Help
---

### Post by strm on 2007-06-07
Hi,
I am attempting to unmount my NTFS partition in /media/disk and I am unable to do so.

When I right click on the "disk" icon on my desktop and click unmount, i get an error saying:
```

Cannot unmount volume.
An application is preventing the volume from being unmounted.
```

When I try to manually unmount the volume using **umount /media/disk** I get the following:
```

root@pavel-laptop:/media/disk# umount /media/disk
umount: /media/disk: device is busy
umount: /media/disk: device is busy
```

Finally when I try to see if anything is using the volume I try:
```

root@pavel-laptop:/media/disk# ps x | grep /media/disk
12425 pts/0    R+     0:00 grep /media/disk
```
Where the pid changes every time i run the command.
and lastly this is the output of lsof:
```

root@pavel-laptop:/media/disk# lsof /media/disk
COMMAND   PID USER   FD   TYPE DEVICE SIZE NODE NAME
bash     8239 root  cwd    DIR    3,1 4096    5 /media/disk
lsof    12450 root  cwd    DIR    3,1 4096    5 /media/disk
lsof    12451 root  cwd    DIR    3,1 4096    5 /media/disk
```

Some help would be great, thanks.
PS, the reason for doing this is I am currently fighting with ntfs-3g to let me enable writing on that internal drive partition.
Here's a link to my main problem:
[http://ubuntuforums.org/showthread.php?p=2799628#post2799628](http://ubuntuforums.org/showthread.php?p=2799628#post2799628).

---

### Post by init1 on 2007-06-07
Sometimes that happens to me. Try restarting and it should be fine

---

### Post by strm on 2007-06-07
I fixed it. I had to boot into windows and run a disk check on the NTFS partition, that fixed both the unmounting problem as well as the ntfs-3g problem.

Thanks.

---

