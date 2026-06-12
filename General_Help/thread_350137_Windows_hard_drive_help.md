---
title: "Windows hard drive help"
date: 2007-01-31
forum: General Help
---

### Post by abba567 on 2007-01-31
trying to mount my ntfs hard drive but i get the following problem

tiger@tiger-desktop:~$ sudo /dev/hdb /media/windows/ -t hpfs/ntfs -o nls=utf8,umask=0222
sudo: /dev/hdb: command not found

Please help

thanks

---

### Post by Waappu on 2007-01-31
Hi

It should be something like this
```
sudo mount /dev/hdb1 /media/windows/ -t hpfs/ntfs -o nls=utf8,umask=0222
```

---

### Post by housam on 2007-01-31
Try to use [this guide ]("http://doc.gwos.org/index.php/DapperGuide#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only")it may help

---

