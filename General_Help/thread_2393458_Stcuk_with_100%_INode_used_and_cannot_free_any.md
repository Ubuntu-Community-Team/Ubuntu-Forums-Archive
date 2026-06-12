---
title: "Stcuk with 100% INode used and cannot free any"
date: 2018-06-03
forum: General Help
---

### Post by MarcusL on 2018-06-03
Hi all,
I am running a Laravel app in a Ubuntu 16.04 server in AWS. The app today started failing and when looking at its log, I get a message of "out of space".

From [this thread]("https://ubuntuforums.org/showthread.php?t=2281539"), I ran the following:

```
df -h

df -i

uname -a

dpkg -l | awk '/-headers-/ {print $2}'

```

And I get:

```
root@auprodweb1:~# df -h
Filesystem        Size  Used   Avail Use%   Mounted on
udev              487M     0     487M   0%    /dev
tmpfs             100M  4.3M    95M   5%    /run
/dev/xvda1         7.8G  4.7G   2.7G  64%   /
tmpfs             496M     0    496M    0%   /dev/shm
tmpfs              5.0M     0     5.0M    0%   /run/lock
tmpfs             496M     0    496M    0%   /sys/fs/cgroup
tmpfs             100M     0    100M    0%   /run/user/1000

```

```

root@auprodweb1:~# df -i

Filesystem     Inodes     IUsed  IFree        IUse%  Mounted on
udev            124443        357     124086      1%  /dev
tmpfs           126768        465     126303      1%  /run
/dev/xvda1   524288  524288               0  100%  /
tmpfs           126768           1      126767      1%  /dev/shm
tmpfs           126768           4      126764      1%  /run/lock
tmpfs           126768         16      126752      1%  /sys/fs/cgroup
tmpfs           126768           4      126764      1%  /run/user/1000

```

```


root@auprodweb1:~# uname -a
Linux auprodweb1 4.4.0-124-generic #148-Ubuntu SMP Wed May 2 13:00:18 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

```

root@auprodweb1:~# dpkg -l | awk '/-headers-/ {print $2}'
linux-headers-4.4.0-104
linux-headers-4.4.0-104-generic
linux-headers-4.4.0-121
linux-headers-4.4.0-121-generic
linux-headers-4.4.0-124
linux-headers-4.4.0-124-generic
linux-headers-4.4.0-127
linux-headers-generic
linux-headers-virtual

```

So following the [steps here]("https://ubuntuforums.org/showthread.php?t=2312951") I did:

```

root@auprodweb1:~$ dpkg -l | grep linux-headers

```

And then deleted old kernel images (result is what you see above, as kernel versions went back to 52). But as I get to the install step:

```

root@auprodweb1:~# apt-get -f install
Reading package lists... Error!
E: Could not create temporary file for /var/cache/apt/pkgcache.bin - mkstemp (28: No space left on device)
E: The package lists or status file could not be parsed or opened.

```

I am really stuck. 

- How to free up INodes since the steps suggested fail as above?
- What has caused the usage of all INodes so to avoid this issue in future?

Thank you.

Any suggestions appreciated.

---

### Post by MarcusL on 2018-06-04
I managed to fix this issue by deleting old vershions of log to free up 20 or so INodes, then the above cleanup worked OK

---

