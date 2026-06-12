---
title: "root LV seems too big"
date: 2012-10-26
forum: General Help
---

### Post by skinney6 on 2012-10-26
$ df -h
Filesystem                 Size  Used Avail Use% Mounted on
/dev/mapper/helios-root    294G  **5.6G**  273G   3% /

$ ls -sh
**total 97K**
4.0K backup  4.0K home        4.0K media     0 run         0 sys       12K webmin-setup.out
4.0K bin        0 initrd.img  4.0K mnt    4.0K sbin     4.0K tmp
1.0K boot    4.0K lib         4.0K opt    4.0K selinux  4.0K usr
   0 dev     4.0K lib64          0 proc   4.0K share    4.0K var
4.0K etc      16K lost+found  4.0K root   4.0K srv         0 vmlinuz

df -h says my '/' is 5.6G but ls -sh while in '/' is only 97K
I think i must have done something wrong when setting up LVM

---

### Post by vandorjw on 2012-10-26
Please use [ code ] [/ code ] without the spaces around your posts. It makes it much easier to read.

Here are my results
```

[root@phenom2 /]# df -h
Filesystem                          Size  Used Avail Use% Mounted on
[COLOR="Red"]rootfs                              110G  8.5G   96G   9% /[/COLOR]
dev                                 3.9G     0  3.9G   0% /dev
run                                 3.9G  500K  3.9G   1% /run
/dev/sdc2                           110G  8.5G   96G   9% /
tmpfs                               3.9G  676K  3.9G   1% /dev/shm
tmpfs                               3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs                               6.0G   20M  6.0G   1% /tmp
/dev/sdc1                          1021M  132K 1021M   1% /boot/efi
/dev/mapper/VolGroup00-lvolbackups  459G   84G  352G  20% /backups
/dev/mapper/VolGroup00-lvolstorage  621G  494G   96G  84% /storage
[COLOR="Red"]/dev/mapper/VolGroup00-lvolroot      30G   14G   15G  48% /old-root[/COLOR]
/dev/mapper/VolGroup00-lvolhome      30G   27G  1.7G  94% /old-home
[root@phenom2 /]# exit

```

```

[root@phenom2 /]$ ls -sh
[COLOR="Red"]total 80K[/COLOR]
4.0K backups  4.0K boot  4.0K etc      0 lib     16K lost+found  4.0K mnt       4.0K old-root     0 proc     0 run   4.0K srv         0 sys  4.0K usr
4.0K bin         0 dev   4.0K home     0 lib64  4.0K media       4.0K old-home  4.0K opt       4.0K root  4.0K sbin  4.0K storage     0 tmp  4.0K var

```

I hope that helps :)

EDIT:
I recently added an SSD drive, which is the reason for /old-root and /old-home.
```

[root@phenom2 /old-root]$ ls -sh
[COLOR="Red"]total 92K[/COLOR]
4.0K backup  4.0K boot  4.0K etc      0 lib     16K lost+found  4.0K mnt  4.0K proc  4.0K run   4.0K srv      4.0K sys  4.0K usr
4.0K bin     4.0K dev   4.0K home     0 lib64  4.0K media       4.0K opt  4.0K root  4.0K sbin  4.0K storage  4.0K tmp  4.0K var

```

---

