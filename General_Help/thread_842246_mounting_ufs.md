---
title: "mounting ufs"
date: 2008-06-27
forum: General Help
---

### Post by hirohitosan on 2008-06-27
Hi there
I have an HDD with UFS un it. It is possible to mount in Ubuntu?
Thanks

---

### Post by justleen on 2008-06-27
```
mount -t udf /dev/hdd1 /media/UDF 
```
?

---

### Post by hirohitosan on 2008-06-27
if I try ```
sudo mount -t udf /dev/hdd1 /media/UDF
```
it gives me
```
sudo: unable to resolve host ....
```

is something wrong with my network and I don't know how to handle it ...

---

### Post by hirohitosan on 2008-06-27
```
sudo mount -t udf /dev/sdb1 /media/data/
sudo: unable to resolve host horatiu
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

dmesg | tail givem my this:

```

[  371.217373] ufs was compiled with read-only support, can't be mounted as read-write
[  606.370458] ufs was compiled with read-only support, can't be mounted as read-write
[  614.898186] ufs was compiled with read-only support, can't be mounted as read-write
[  698.710490] UDF-fs: No partition found (1)
[ 1663.317502] UDF-fs: No partition found (1)


```

---

