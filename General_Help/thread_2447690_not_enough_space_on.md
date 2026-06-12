---
title: "not enough space on /"
date: 2020-07-23
forum: General Help
---

### Post by kjendis on 2020-07-23
Please can someone help to figure out how to fix this issue. After ubuntu said not enough space on / , I tried to move /home to another partition which I thought had a lot of space. 
Now its on dev/sdb4 not sda1 where / is, or so I thought
But I stil get message  there is not enough space on /

```
df -H :

Filesystem      Size  Used Avail Use% Mounted on
udev            2,0G     0  2,0G   0% /dev
tmpfs           399M  1,8M  398M   1% /run
/dev/sda1        24G   23G   46M 100% /
tmpfs           2,0G  297M  1,7G  15% /dev/shm
tmpfs           5,3M  4,1k  5,3M   1% /run/lock
tmpfs           2,0G     0  2,0G   0% /sys/fs/cgroup
/dev/loop0      102M  102M     0 100% /snap/core/9289
/dev/loop3       58M   58M     0 100% /snap/core18/1880
/dev/loop2       58M   58M     0 100% /snap/core18/1754
/dev/loop1      102M  102M     0 100% /snap/core/9665
/dev/loop4      169M  169M     0 100% /snap/gnome-3-28-1804/116
/dev/loop5      170M  170M     0 100% /snap/gnome-3-28-1804/128
/dev/loop6      269M  269M     0 100% /snap/gnome-3-34-1804/33
/dev/loop7      6,7M  6,7M     0 100% /snap/gnome-clocks/261
/dev/loop9      2,4M  2,4M     0 100% /snap/gnome-system-monitor/145
/dev/loop8      2,4M  2,4M     0 100% /snap/gnome-system-monitor/148
/dev/loop10     7,0M  7,0M     0 100% /snap/gnome-clocks/257
/dev/loop11     269M  269M     0 100% /snap/gnome-3-34-1804/36
/dev/loop13     263k  263k     0 100% /snap/gtk2-common-themes/13
/dev/loop12      14M   14M     0 100% /snap/mojave-themes/2
/dev/loop14      14M   14M     0 100% /snap/mojave-themes/1
/dev/loop15     263k  263k     0 100% /snap/gtk2-common-themes/9
/dev/loop16      58M   58M     0 100% /snap/gtk-common-themes/1502
/dev/loop17      66M   66M     0 100% /snap/gtk-common-themes/1506
/dev/sdb4       296G   44G  238G  16% /home
tmpfs           399M   25k  399M   1% /run/user/1000
```

---

### Post by TheFu on 2020-07-23
Run away log files?

Helpful commands:
This command hides non-storage-impacting mounts:
```
 $ df -hT -x squashfs -x tmpfs -x devtmpfs
```

This command shows inode use:
```
 $ df -iT -x squashfs -x tmpfs -x devtmpfs
```

How do we figure out which?```

 $ cd /var
 $ sudo du -sh *|sort -h
```

Repeat```

 $ cd /var/lib
 $ sudo du -sh *|sort -h
```

Repeat ...  You get the idea.  

To find really big files
```
 $ find /var -type f -size +3G
```

Repeat.

See how using code tags helps?  Please do the same especially for output with columns.

---

### Post by kjendis on 2020-07-23
thanks

gonna post some output hoping it can lead to more pointers

```
kjendis@laptop:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda1      ext4   22G   21G   36M 100% /
/dev/sdb4      ext4  276G   41G  221G  16% /home

```

```
kjendis@laptop:~$ sudo df -iT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type   Inodes  IUsed    IFree IUse% Mounted on
/dev/sda1      ext4  1466368 235676  1230692   17% /
/dev/sdb4      ext4 18391040 158537 18232503    1% /home

```

```
kjendis@laptop:/var$ sudo du -sh *|sort -h
0    lock
0    run
4,0K    crash
4,0K    local
4,0K    mail
4,0K    metrics
4,0K    opt
68K    tmp
148K    snap
256K    spool
5,0M    backups
827M    cache
966M    log
2,5G    lib




```

```
kjendis@laptop:/var$ sudo find /var -type f -size +75M
/var/lib/snapd/snaps/gnome-3-28-1804_128.snap
/var/lib/snapd/snaps/core_9665.snap
/var/lib/snapd/snaps/core_9289.snap
/var/lib/snapd/snaps/gnome-3-34-1804_36.snap
/var/lib/snapd/snaps/gnome-3-28-1804_116.snap
/var/lib/snapd/snaps/gnome-3-34-1804_33.snap
/var/lib/snapd/cache/f2b3265e9914a116aa3797f3a99e6755ca628774d86b8be080f005d90d46a8a95e217ba6992778d8f75f66da258d5797
/var/lib/snapd/cache/14e04a69a63aff464372a58c6f9ece2785145cdba1749e5b18fb78d1e61f4049808287ca19409b0eab18cb5a46f95796
/var/lib/snapd/cache/047a079b88612d704414da7c3efee15569e6667974609066cf7811712d98ffaab0e4dbe7e1db2e54c6b60a28d1c41c16
/var/lib/snapd/cache/d6ca3cbbe316be011ef9919febad1ada33aec25387b7b938844179ebfe711bca408b04373bd39317dea6424e58fa8581
/var/lib/snapd/seed/snaps/core_7270.snap
/var/lib/snapd/seed/snaps/gnome-3-28-1804_67.snap
/var/cache/apt/archives/linux-firmware_1.187.2_all.deb
/var/cache/apt/archives/linux-firmware_1.187.1_all.deb

```

---

### Post by TheFu on 2020-07-23
Why did you choose /var/? I used that as an example only.  There's 23G used and /var/ doesn't have anywhere near 23G used.
Start in / .... run the commands, figure out what directories are using all the storage, move into those directories, repeat.  Move, run the commands, repeat.

BTW, so clean up old snaps, here's a script to make the commands to run.
```
#!/bin/sh
set -eu

snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
    echo   sudo snap remove "$snapname" --revision="$revision"
    done
```

---

### Post by rsteinmetz70112 on 2020-07-23
You can certainly loss some stuff in /var/log don't know if it will be enough.

---

### Post by HermanAB on 2020-07-24
You can delete everything in /var/log.  The system wil create new files again after a while.

After deleting schtuff and emptying the recycle bin, you may have to run a fsck to actually get the space back.

---

### Post by Impavidus on 2020-07-24
> **kjendis said:**
> After ubuntu said not enough space on / , I tried to move /home to another partition which I thought had a lot of space. 

This is a bit weird. You don't move /home to a partition that has a lot of free space, but you move it to a dedicated partition. But then, the new /home partition already has 44GB of data now, which is about twice the size of your root partition. So you didn't just create that by moving stuff from the root partition.

Are you sure that you really deleted the data from the old /home directory? If you haven't, the data may still be there, hidden underneath the data from the /home partition that you mounted on top of it.

If you boot in recovery mode, you can get to a root terminal without mounting the /home partition. Then you can see if anything is in /home.

How have you attempted to move your /home directory to a separate partition?

---

### Post by ActionParsnip on 2020-07-24
What is the output of:
```

dpkg -l | grep linux-image | grep -v extra

```

We can remove old kernels and free space easily.

---

### Post by HermanAB on 2020-07-24
My guess is that the old /home data is still there and wasn't deleted.

---

### Post by kjendis on 2020-07-24
No, didnt delete the old /home. I just edited /etc/fstab to mount /home to another partition. 
will this create a copy? , and you need to delete the old one? 
When I boot in recovery, it looks to be the same /home. A file I created in recovery on /home also appear there after normal boot.


edit; think i solved it by booting in recovery, then unmouting the partition and then deleting contents in /home

thanks all the feedback!

---

### Post by TheFu on 2020-07-24
> **kjendis said:**
> No, didnt delete the old /home. I just edited /etc/fstab to mount /home to another partition. 
will this create a copy? , and you need to delete the old one? 
When I boot in recovery, it looks to be the same /home. A file I created in recovery on /home also appear there after normal boot.

Changing the fstab just changes the fstab.  Nothing else.  If you want files to be moved, then you need to move them ... properly, retaining ownership and permissions.  If there's anything left over in the old /home/  and a new partition is mounted onto the same directory, then all those files, as Herman said above, will be hidden under that new mount. Inaccessible, but still using storage.

There are how-to guides for moving /home/ to a new partition.  In the old days, before snaps, it was really easy.  Now that snaps DEMAND/REQUIRE exactly "/home" to be the mount location for HOME directories, we have to do it the harder way.  "ubuntu move home partition" - as your web search and that how-to will be found.
Be absolutely certain you get the owner, group, permissions for the new storage correct or it will be a terrible day.

---

### Post by kjendis on 2020-07-24
yeah, like I said I followed your advice to boot in recovery. THen I unmounted the partition to which /home was mounted. After this, there was still a /home appeared, so I assumed thats the old /home and deleted it. 
so far all good. Thanks

---

