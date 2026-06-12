---
title: "Problems updating Ubuntu server 10.04.4 to 12.04. A lot of broken packages."
date: 2012-11-14
forum: General Help
---

### Post by the_X_files on 2012-11-14
The system was updated to 10.04 not a long time ago without any problems. I really can not understand why there are so many broken packages and how to fix them. I attached the log files. The current system is updated to the latest 10.04 packages. Any help would be appreciated.

```
# apt-get clean
# apt-get autoclean
Reading package lists... Done
Building dependency tree
Reading state information... Done
# apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
# apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Edit (log files removed):
```
Broken libssl1.0.0:amd64 Breaks on openssh-client [ amd64 ] < 1:5.3p1-3ubuntu7 -> 1:5.9p1-5ubuntu1 > ( net ) (< 1:5.9p1-4)
  Considering openssh-client:amd64 10007 as a solution to libssl1.0.0:amd64 128
  Holding Back libssl1.0.0:amd64 rather than change openssh-client:amd64
Investigating (0) libc6-dev [ amd64 ] < 2.11.1-0ubuntu7.11 -> 2.15-0ubuntu10.3 > ( libdevel )
Broken libc6-dev:amd64 Breaks on gcj-4.4-base [ amd64 ] < 4.4.3-1ubuntu4.1 > ( libs ) (< 4.4.6-2ubuntu2)
......

```

The problem was caused by openssh-client. It was the first held package during the update followed by libssl.. and ~250 more. After removing openssh-clint and openssh-server the upgrade went fine.

---

### Post by the_X_files on 2012-11-15
The problem is solved. Ubuntu 12.04 is up and running :)

---

