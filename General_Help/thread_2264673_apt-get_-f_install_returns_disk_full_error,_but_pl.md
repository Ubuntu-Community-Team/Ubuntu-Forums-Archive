---
title: "apt-get -f install returns disk full error, but plenty of space on the drive"
date: 2015-02-09
forum: General Help
---

### Post by Amadaeus on 2015-02-09
Hello Ubuntu gurus,

I'm running 12.04.2 LTS, and I've run into an issue with my server. I initially my machine running off of a 10Gb memory stick, but imaged it over to a proper drive a couple of years ago. 

A couple of days ago, my server sent me a missive to my inbox: 
```
/etc/cron.daily/apt:
Cache has broken packages, exiting
```

When running apt-get -f install to repair whatever package went awry, I receive the following error:

```
The following extra packages will be installed:
  tzdata
The following packages will be upgraded:
  tzdata
1 upgraded, 0 newly installed, 0 to remove and 126 not upgraded.
1 not fully installed or removed.
Need to get 0 B/439 kB of archives.
After this operation, 48.1 kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 644187 files and directories currently installed.)
Preparing to replace tzdata 2014i-0ubuntu0.12.04 (using .../tzdata_2015a-0ubuntu0.12.04_all.deb) ...
Unpacking replacement tzdata ...
dpkg: error processing /var/cache/apt/archives/tzdata_2015a-0ubuntu0.12.04_all.deb (--unpack):
 error creating symbolic link `./usr/share/zoneinfo/America/Dominica': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2015a-0ubuntu0.12.04_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

A check of disk space shows plenty of space, and 48.1 kB shouldn't be a problem:

```
r3lai@hargow:~$ df
Filesystem               1K-blocks       Used Available Use% Mounted on
/dev/mapper/hargow-root   10579232    8624180   1417660  86% /
udev                       2014992          4   2014988   1% /dev
tmpfs                       404852       2372    402480   1% /run
none                          5120          0      5120   0% /run/lock
none                       2024260          0   2024260   0% /run/shm
/dev/sdc1                   233191      51552    169198  24% /boot
/dev/md0                1922730680 1739242556  85819012  96% /media/raid1

```

Does anyone here on the internet have any idea what could be the problem?

Thanks,

Amadaeus

---

### Post by ian-weisser on 2015-02-09
> **Amadaeus said:**
> error creating symbolic link `./usr/share/zoneinfo/America/Dominica': No space left on device

Links don't take up much space. But they do take up an inode.
Check your inodes.
```
df -i
```

---

### Post by Impavidus on 2015-02-09
The partition is rather full, but it should be possible to squeeze a little more in. Maybe it's the inodes.```
df -i
```

---

### Post by ketoiloihp on 2015-08-15
I had the same problem when I updated my system.
I tried to remove some old libraries and old kernels and the problem's resolved.
You can read more about Inodes here: [http://www.yourownlinux.com/2014/01/inodes-in-linux-unix-filesystems.html](http://www.yourownlinux.com/2014/01/inodes-in-linux-unix-filesystems.html)

---

