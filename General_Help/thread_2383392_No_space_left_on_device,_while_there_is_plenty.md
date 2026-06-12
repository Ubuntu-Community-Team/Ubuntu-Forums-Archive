---
title: "No space left on device, while there is plenty?"
date: 2018-01-24
forum: General Help
---

### Post by mcfurry on 2018-01-24
Hi all,
I'm on an Ubuntu 16.04 system with btrfs filesystem.
Recently I keep getting more and more "No space left on device" errors up to the point where even tab-completion fails.

When removing some big files the issues seem temporarily solved, however after some time the errors appear again.
So I'm afraid something is eating my diskspace? However I can't seem to figure out what's going on.
I searched some other forum posts but couldn't figure out what's the problem and how to solve it.
Some usefull command output:
df -h:
```
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           786M   12M  775M   2% /run
/dev/sda5       107G   70G   38G  66% /
tmpfs           3.9G   74M  3.8G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0       82M   82M     0 100% /snap/core/3887
/dev/sda1       496M   51M  446M  11% /boot/efi
/dev/sda5       107G   70G   38G  66% /home
tmpfs           786M   12K  786M   1% /run/user/121
tmpfs           786M   36K  786M   1% /run/user/1000
```

df -i
```
Filesystem      Inodes IUsed   IFree IUse% Mounted on
udev            999422   600  998822    1% /dev
tmpfs          1005991  1023 1004968    1% /run
/dev/sda5            0     0       0     - /
tmpfs          1005991   115 1005876    1% /dev/shm
tmpfs          1005991     7 1005984    1% /run/lock
tmpfs          1005991    17 1005974    1% /sys/fs/cgroup
/dev/loop0       12821 12821       0  100% /snap/core/3887
/dev/sda1            0     0       0     - /boot/efi
/dev/sda5            0     0       0     - /home
tmpfs          1005991    13 1005978    1% /run/user/121
tmpfs          1005991    25 1005966    1% /run/user/1000
```

---

### Post by TheFu on 2018-01-24
```
sudo btrfs filesystem df /mountpoint
```
Probably want to look at each problem file system/mount.
and
```
sudo btrfs balance start -m /mountpoint
```

where /mountpoint is the location on YOUR system like /, and /home.

Use **df -T** to show the type of file systems on each mount.

The Arch wiki on BTRFS is full of useful techniques for BTRFS and WHY they might be useful.

Redhat has deprecated BTRFS use, BTW.

---

### Post by mcfurry on 2018-01-24
Thx for your swift response!

Running *sudo btrfs filesystem df / *
```
sudo btrfs filesystem df /
Data, single: total=72.01GiB, used=65.64GiB
System, single: total=4.00MiB, used=16.00KiB
Metadata, single: total=4.01GiB, used=2.84GiB
GlobalReserve, single: total=160.39MiB, used=0.00B
```
Didn't show too interesting results I think.

In the meanwhile I continued searching and found this command:
```
sudo btrfs fi show
Label: none  uuid: 9d062f3f-8639-4ef0-b84e-88408f18b975
    Total devices 1 FS bytes used 68.48GiB
    devid    1 size 106.32GiB used 106.32GiB path /dev/sda5
```
Which indeed seems like the disk is full. I'm don't know exactly what the difference with the df command is though?

After that I tried your balance command. I had to free up some disk space for it to run properly but it was able to relocate some chunks and free some space.
I also tried
```
sudo btrfs balance start -dusage=66 -m /
```
which resulted in 104 of 210 chunks being relocated! Now the filesystem looks more like I was expecting:
```
sudo btrfs fi show
Label: none  uuid: 9d062f3f-8639-4ef0-b84e-88408f18b975
    Total devices 1 FS bytes used 68.79GiB
    devid    1 size 106.32GiB used 76.04GiB path /dev/sda5
```
So hopefully it will stay this way, if that's the case I will mark this thread solved, but I'm not too sure what the actual problem was and how to avoid this in the future?

---

### Post by TheFu on 2018-01-24
btrfs lies to df and du about true disk usage.  That's because of the merging of the file system, raid system and LVM into a single project. They were able to accomplish some cool things, but the old-school df/du don't understand those things.  For why, you can find some how-it-works articles on BTRFS.

Fun, different, capable.

Please mark the thread as solved in the thread tools to help others. Thanks for showing what you actually did. That helps others big time!

---

