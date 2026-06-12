---
title: "/data is invisible"
date: 2013-01-01
forum: General Help
---

### Post by satimis on 2013-01-01
Hi all,

Ubuntu 12.04 desktop 64bit

I have 2 HDs, both with Ubuntu12.04 desktop 64bit running, connected in the same PC.

HD-1 traditional partitoning
HD-2 LVM volume partitioning.

On running the OS on HD-1, HD-2 can't be viewed automatically
On running the OS on HD-2, HD-1 can be viewed automatically.

On running the OS on HD-1, I have to mount HD-2 with LVM volume partitions.  Then I can view HD-2.  But I can't view the content of /data partition.

# ls -ald /mnt/data```

drwxr-xr-x 2 root root 4096 Dec 28 13:11 /mnt/data

```

# ls -al /mnt/data```

total 8
drwxr-xr-x  2 root root 4096 Dec 28 13:11 .
drwxr-xr-x 25 root root 4096 Jan  2 10:11 ..

```

However I can read other folders/directories;
# ls /mnt/```

bin   etc         initrd.img.old  media  root     srv  var
boot  folder      lib             mnt    run      sys  vmlinuz
data  home        lib64           opt    sbin     tmp  vmlinuz.old
dev   initrd.img  lost+found      proc   selinux  usr

```

I can't resolve why?  Pls help.  TIA

B.R.
satimis

---

### Post by steeldriver on 2013-01-01
*n/m - didn't read carefully*

---

