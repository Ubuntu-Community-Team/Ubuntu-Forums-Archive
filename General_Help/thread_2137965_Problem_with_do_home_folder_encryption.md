---
title: "Problem with do home folder encryption"
date: 2013-04-22
forum: General Help
---

### Post by sysuser on 2013-04-22
Hello, I try do encryption follow tutorial [http://ubuntuforums.org/showthread.php?t=1987630](http://ubuntuforums.org/showthread.php?t=1987630)

```
INFO:  Checking disk space, this may take a few moments.  Please be patient.
INFO:  2.5x the size your current home directory is required to perform a migration.
INFO:  Once the migration succeeds, you may recover most of this space by deleting the cleartext directory.
ERROR:  Not enough free disk space.
```

```
/dev/sdb1       1,8T  512G  1,2T  30% /home
```

30%*2.5=75% - so why?

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       110G   11G   95G  10% /
udev            7.8G  4.0K  7.8G   1% /dev
tmpfs           3.2G  952K  3.2G   1% /run
none            5.0M  8.0K  5.0M   1% /run/lock
none            7.9G  456K  7.9G   1% /run/shm
/dev/sda1       190M  124K  190M   1% /boot/efi
/dev/sdb1       1.8T  513G  1.2T  30% /home
```

onb system HDD is not possible because this is small SSD HDD...

```
$ mount | grep home
/dev/sdb1 on /home type ext4 (rw)
/user1/.mozilla on /home/user1/.mozilla type none (rw,bind)
/user1/ssd on /home/user1/ssd type none (rw,bind)
gvfs-fuse-daemon on /home/user1/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=user1)
$ ls -la /home
razem 52
drwxr-xr-x   5 root   root    4096 kwi 21 13:56 .
drwxr-xr-x  26 root   root    4096 kwi  9 19:24 ..
drwx------ 148 user1   user1   20480 kwi 22 19:57 user1
drwx------  28 user2 user2  4096 kwi 21 17:56 user2
drwx------   2 root   root   16384 pa&#378; 24 00:16 lost+found
```

I try on user1

---

