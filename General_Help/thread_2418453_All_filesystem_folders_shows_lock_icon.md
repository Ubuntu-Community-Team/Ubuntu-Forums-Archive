---
title: "All filesystem folders shows lock icon"
date: 2019-05-07
forum: General Help
---

### Post by mohan10 on 2019-05-07
Few days before disk space full. User cannot login. From recovery mode, i deleted some files and logged into the system. After logged in, i see that many folders shows lock icon. Herewith attached the screen shot for reference. kindly help me to solve this.

Thanks,
mohan

---

### Post by sisco311 on 2019-05-07
Did you delete any system files?

Please open a terminal (Ctrl+Alt+t) and post the output of:
```
mount
```
and
```
ls -al /
```

---

### Post by mohan10 on 2019-05-07
Mount output as follows:

------------------------------------
```
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4075012k,nr_inodes=189996,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=820108k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=25,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=15649)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /run/user/1001 type tmpfs (rw,nosuid,nodev,relatime,size=820108k,mode=700,uid=1001,gid=1001)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=820108k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
```

---------------------------------------

ls -al / ---> output as follows
---------------------------------------------------------
```
reportingserver@reportingserver:~$ ls -al /
total 120
drwxrwxrwx  25 root            root             4096 Apr  5 11:48 .
drwxrwxrwx  25 root            root             4096 Apr  5 11:48 ..
drwxrwxrwx   3 root            root             4096 Jul 23  2018 Adempiere
drwxr-xr-x   2 root            root             4096 Apr 19 11:00 bin
drwxrwxrwx   3 root            root            12288 Apr 30 11:44 boot
drwxrwxrwx   2 root            root             4096 Sep 20  2017 cdrom
drwxr-xr-x  19 root            root             4000 May  7 11:47 dev
drwxr-xr-x 132 root            root            12288 May  7 11:26 etc
drwxr-xr-x   4 reportingserver reportingserver  4096 May  7 11:25 home
drwxrwxrwx   3 root            root             4096 Oct 17  2018 HQReports
lrwxrwxrwx   1 root            root               33 Apr  5 11:48 initrd.img -> boot/initrd.img-4.15.0-47-generic
lrwxrwxrwx   1 root            root               33 Apr  5 11:48 initrd.img.old -> boot/initrd.img-4.15.0-46-generic
drwxrwxrwx  22 root            root             4096 Jan 19  2018 lib
drwx------   2 root            root            16384 Sep 20  2017 lost+found
drwxr-xr-x   3 root            root             4096 Jan 17  2018 media
drwxrwxrwx   2 root            root             4096 Aug  1  2017 mnt
drwxrwxrwx   4 root            root             4096 Dec 28  2017 opt
dr-xr-xr-x 224 root            root                0 May  7 11:47 proc
drwx------   8 root            root             4096 Apr 29 17:44 root
drwxr-xr-x  27 root            root              860 May  7 12:34 run
drwxr-xr-x   2 root            root            12288 Apr 19 11:00 sbin
drwxrwxrwx   2 root            root             4096 Apr 29 10:06 snap
drwxr-xr-x   2 root            root             4096 Aug  1  2017 srv
dr-xr-xr-x  13 root            root                0 May  7 11:54 sys
drwxrwxrwt  12 root            root             4096 May  7 12:36 tmp
drwxrwxrwx  13 root            root             4096 Feb  8 10:13 usr
drwxr-xr-x  14 root            root             4096 Aug  1  2017 var
lrwxrwxrwx   1 root            root               30 Apr  5 11:48 vmlinuz -> boot/vmlinuz-4.15.0-47-generic
lrwxrwxrwx   1 root            root               30 Apr  5 11:48 vmlinuz.old -> boot/vmlinuz-4.15.0-46-generic
```

----------------------------------------------------------------

FYI
mount output  ------->   I compared with my systems, i found "nsroot=/" entry is missing in all lines starts with "cgroup".

---

### Post by Impavidus on 2019-05-07
When you run the nautilus file manager as an ordinary user, those locks seem nomal (I think, I have thunar file manager here, which doesn't do that. I rarely use the file manager anyway). You don't have write permission in those directories, therefore it shows a lock, as clearly seen on the /var directory in your output.

What is a problem is that some directories don't show this lock and are, according to ls, writable for all users. That's a huge security risk. An unprivileged program can store some arbitrary code in /lib, which may then be executed by a privileged program. It seems you have been a bit careless while messing with permissions. Also, your /home should be owned by root (unless you made /home itself your home directory, instead of /home/username).

If the damage doesn't extend to subdirectories and you still trust your system (I wouldn't), you can fix the permissions. It seems these need fixing:```
drwxr-xr-x   3 root root  4096 mei  3 20:01 boot/
drwxr-xr-x   2 root root  4096 okt 14  2016 cdrom/
drwxr-xr-x   4 root root  4096 sep 25  2015 home/
drwxr-xr-x  23 root root  4096 apr 24 11:55 lib/
drwxr-xr-x   2 root root  4096 feb 20  2017 mnt/
drwxr-xr-x   3 root root  4096 apr  9 10:28 opt/
drwxr-xr-x   2 root root  4096 apr 21  2018 snap/
drwxr-xr-x  10 root root  4096 dec 24  2017 usr/

```So all should have permissions 755 and ownership root:root. The Adempiere and HQReport directories aren't present on a standard system, but I find full permissions there a bit peculiar too.

---

