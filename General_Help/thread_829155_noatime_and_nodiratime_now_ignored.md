---
title: "noatime and nodiratime now ignored?"
date: 2008-06-14
forum: General Help
---

### Post by chapterthree on 2008-06-14
Hi All,

The following seems kind of like a bug, but I wanted to toss it out for feedback first.

It seems that as of 2.6.24-12.18, noatime and nodiratime directives that are specified in /etc/fstab are 'ignored' and relatime is always enabled ([see bug 199427](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199427))

```
chapterthree@home:~$ uname -a
Linux home 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux
chapterthree@home:~$ grep " /data" /etc/fstab 
UUID=ec8df6c9-3e4b-43f1-b2c6-3a9cae3336b3 /data           ext3    noatime,nodiratime,data=writeback        0       2
chapterthree@home:~$ grep " /data" /proc/mounts 
/dev/sda3 /data ext3 rw,noatime,nodiratime,relatime,data=writeback 0 0

```

The above is true for all of my partitions that I have specified atime changes.

Why is the kernel ignoring the userspace over-ride setting in /etc/fstab and enabling relatime?

---

