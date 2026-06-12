---
title: "[SOLVED] problems with fsck"
date: 2008-05-16
forum: General Help
---

### Post by priegog on 2008-05-16
Hi, my problem is this. 
During one of the routine boot-time checks it gave me some error and told me to run it manually. So I got in and ran fsck, but I got this output.
```
~$ fsck
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=56237be6-1051-4a6d-b97e-08601376c239'

```

What should I do? Everything seems to be working just fine, but if nothing else it will keep bugging me at boot-time. Thanks in advance.

---

### Post by strabes on 2008-05-16
That is normal when you run fsck by itself with no parameters. Fsck shouldn't be run on a mounted filesystem so you could boot into the live CD and run "sudo fsck /dev/sda1" in a terminal on the live CD (assuming your root partition is located at /dev/sda1 - run sudo fdisk -l to find out).

---

### Post by zvacet on 2008-05-16
```
sudo blkid
```

```
gksudo gedit /etc/fstab
```

In fstab you will find your UUID and to which partition is related.Replace it with UUID you find runing **sudo blkid** command.

---

### Post by priegog on 2008-05-16
solved it, thanks a lot

---

