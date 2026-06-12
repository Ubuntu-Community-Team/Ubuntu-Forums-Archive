---
title: "/ (root) partition filling up fast- 18.04"
date: 2018-06-13
forum: General Help
---

### Post by tororii on 2018-06-13
For a while now, my root directory has been filling up real fast, and I have no idea why. I don't have an absurd amount of programs (Steam, Gnome Tweaks, Spotify, and a few others) and I have even gone as far as to do a fresh install of Ubuntu, and I still have not figured it out. I designated a bit more than 10 GB, and 9 is already filled up.

---

### Post by yancek on 2018-06-13
A default install of the latest Ubuntu requires about 8GB of space so 10GB is not much.  Open a terminal and run:  df -h or sudo df -h and look at the output or post it here.  If it is taking up 90% of the partition or more, you will always have this problem.

---

### Post by QIII on 2018-06-13
Hello!

I usually give / 25-30GB, but then I also use a lot of stuff that can take up a bit of space.

Let's see where the space is being taken up.

See 

```
man du
```

for a detailed explanation.

We'll also do a numeric sort.

First

```
cd /
``` 

to get to /.

Then

```
du -d 1 | sort -n
```

Post the results back, please.

---

### Post by tororii on 2018-06-13
Ok- the results requested

sudo df -h yielded
```
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           790M  1.9M  788M   1% /run
/dev/sda5        11G  8.6G 1000M  90% /
tmpfs           3.9G   17M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0       15M   15M     0 100% /snap/gnome-logs/37
/dev/loop3       21M   21M     0 100% /snap/gnome-logs/25
/dev/loop1       15M   15M     0 100% /snap/gnome-logs/34
/dev/loop2      1.7M  1.7M     0 100% /snap/gnome-calculator/154
/dev/loop7      3.4M  3.4M     0 100% /snap/gnome-system-monitor/36
/dev/loop4      163M  163M     0 100% /snap/spotify/16
/dev/loop5      140M  140M     0 100% /snap/gnome-3-26-1604/64
/dev/loop6       13M   13M     0 100% /snap/gnome-characters/96
/dev/loop16     3.8M  3.8M     0 100% /snap/gnome-system-monitor/41
/dev/loop9      141M  141M     0 100% /snap/gnome-3-26-1604/59
/dev/loop8      2.4M  2.4M     0 100% /snap/gnome-calculator/178
/dev/loop10      13M   13M     0 100% /snap/gnome-characters/69
/dev/loop11     3.8M  3.8M     0 100% /snap/gnome-system-monitor/45
/dev/loop12      13M   13M     0 100% /snap/gnome-characters/101
/dev/loop14      87M   87M     0 100% /snap/core/4486
/dev/loop13      87M   87M     0 100% /snap/core/4650
/dev/loop15     2.4M  2.4M     0 100% /snap/gnome-calculator/170
/dev/sda2        95M   31M   65M  32% /boot/efi
tmpfs           790M   16K  790M   1% /run/user/120
tmpfs           790M   24K  790M   1% /run/user/1000
```


I ran cd / then sudo du -d 1 | sort -n  (because I got a lot of "permission denied"  when I didn't use sudo)      and got 

sudo du -d 1 | sort -n
```
du: cannot access './run/user/1000/gvfs': Permission denied
du: cannot access './proc/2314/task/2314/fd/4': No such file or directory
du: cannot access './proc/2314/task/2314/fdinfo/4': No such file or directory
du: cannot access './proc/2314/fd/3': No such file or directory
du: cannot access './proc/2314/fdinfo/3': No such file or directory
0    ./dev
0    ./proc
0    ./sys
4    ./cdrom
4    ./lib64
4    ./media
4    ./mnt
4    ./opt
4    ./srv
16    ./lost+found
16    ./root
104    ./tmp
1928    ./run
11236    ./sbin
12436    ./bin
13024    ./etc
171919    ./boot
810584    ./lib
2008256    ./var
2113900    ./home
2678615    ./snap
3265416    ./usr
11582646    .
```

---

### Post by QIII on 2018-06-13
We could have excluded /proc (it's a virtual directory anyway) but I kept the command simple.

Yeah.  Nothing at all unexpected with the storage used.  You simply gave too little room to your installation.  I think 8.6G is the absolute minimum and you didn't allow much more than that.  It's no wonder you've filled a good portion of that up.

---

### Post by tororii on 2018-06-13
Thanks! I'll just make it bigger.

---

### Post by SeijiSensei on 2018-06-14
Another option is to create a separate partition for /home or /var, which are the two locations that fill up most quickly.  I usually allocate something like 30-40 GB for the root partition these days because disks are so large and cheap, and my /home is on a separate 300 GB partition.

---

