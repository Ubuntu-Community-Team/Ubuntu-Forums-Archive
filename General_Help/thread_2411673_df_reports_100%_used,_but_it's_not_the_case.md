---
title: "df reports 100% used, but it's not the case"
date: 2019-02-02
forum: General Help
---

### Post by ScorpioTiger on 2019-02-02
I'm having trouble with a server reporting out of disk space.

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            481M     0  481M   0% /dev
tmpfs            99M  9.2M   90M  10% /run
**/dev/vda1        25G   25G     0 100% /**
tmpfs           493M     0  493M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           493M     0  493M   0% /sys/fs/cgroup
/dev/vda15      105M  3.4M  102M   4% /boot/efi
tmpfs            99M     0   99M   0% /run/user/1000

df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
udev            122920    384  122536    1% /dev
tmpfs           126144    546  125598    1% /run
**/dev/vda1      3225600 214133 3011467    7% /**
tmpfs           126144      1  126143    1% /dev/shm
tmpfs           126144      3  126141    1% /run/lock
tmpfs           126144     18  126126    1% /sys/fs/cgroup
/dev/vda15           0      0       0     - /boot/efi
tmpfs           126144     10  126134    1% /run/user/1000

lsof +L1
COMMAND   PID     USER   FD   TYPE DEVICE SIZE/OFF NLINK NODE NAME
php-fpm7. 752     root    3u   REG  252,1        0     0 3592 /tmp/.ZendSem.vi0ANt (deleted)
php-fpm7. 826 www-data    3u   REG  252,1        0     0 3592 /tmp/.ZendSem.vi0ANt (deleted)
php-fpm7. 827 www-data    3u   REG  252,1        0     0 3592 /tmp/.ZendSem.vi0ANt (deleted)

[FONT=Courier New][SIZE=2]du -h --max-depth=1[/SIZE][/FONT]
0    ./proc
0    ./sys
15M    ./sbin
4.0K    ./mnt
11M    ./run
16K    ./lost+found
15M    ./bin
0    ./dev
3.3G    ./home
1.3G    ./usr
141M    ./boot
8.0K    ./snap
7.1M    ./etc
**25G    .**
```

I tried to fix using;```

touch /forcefsck
reboot
```

This made no difference. Any ideas?

---

### Post by CatKiller on 2019-02-02
That disk is full. 25 GB is not a generous allocation these days.

You seem confused about what your output is saying. There is no reason why you would run out of inodes when running out of space unless your filesystem consists exclusively of teeny tiny files.

Your du is only showing the disk usage visible to your user. In particular, it's not showing whether your disk space has been used up by something logging to root's home directory, which has caught people out here before.

---

### Post by SeijiSensei on 2019-02-02
As CatKiller says 25 GB isn't very much space, especially if you have content to serve as well.

Assuming you need whatever is in /home, I'd start looking in /var and particularly /var/log.

One easy way to identify large directories is
```

cd /
sudo du -s *

```

---

