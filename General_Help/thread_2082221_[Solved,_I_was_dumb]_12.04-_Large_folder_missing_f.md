---
title: "[Solved, I was dumb] 12.04- Large folder missing from external hard drive"
date: 2012-11-08
forum: General Help
---

### Post by subtleparty on 2012-11-08
I have a Dell Dimension (I forget the model number, I'll edit it in later, because I'm not at home) that I use as a seedbox for torrents. It has a 3TB NTFS formatted external hard drive, which houses all my torrent data. I have 2 folders on this hard drive, one called "Tfiles", which contains all of my .torrent files.


The other folder, which has mysteriously gone missing, was called "Data", which contained everything that I was seeding. I noticed that it was gone when I tried adding a torrent in rtorrent, and was told that the "Data" folder didn't exist.


I was very surprised to learn this, since this folder was over 700GB in size, and I didn't issue any commands that would cause it to be deleted.
Rtorrent was also still uploading data when I got this error, so I don't understand why that was happening.

I used ```
df -h
``` to see if I really did accidentally delete this 700 GB folder, but this is what it returned:

```
/dev/sdb6        37G  3.6G   32G  11% /
udev            494M  4.0K  494M   1% /dev
tmpfs           201M  840K  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            501M   76K  501M   1% /run/shm
/dev/sdc1       2.8T  704G  2.1T  26% /media/bB
```

Obviously, the data is still there somewhere, I just can't see or access the folder at all.
Is there any hope for me?

A friend of mine is theorizing that it's a partition table problem, maybe due to the NTFS filesystem.

EDIT: I also have access to windows machines, if there are any recovery methods I can use there,

DOUBLE EDIT: I found the folder, it got moved into "Tfiles" somehow. Sorry for wasting your time.

---

