---
title: "Trouble with Partition"
date: 2006-08-30
forum: General Help
---

### Post by edoggydogg on 2006-08-30
Hello, my brother setup Ubuntu on my computer and he only formatted about 40gb of my 160gb HDD (no idea why). Anyways, I tried to format it by going to System>Administration>Disks, clicking on the second partition, and formatting it. Well, that worked, but I don't know how to access it. I formatted it as an ext3 file system. I also by curiosity put the access path as "/", which is the same as the first partition. When I did that it the first partition said 30GB used 10.85gb free, and the second partition said 118gb used **10.85gb free**. How is that possible? Help?

---

### Post by cleentrax on 2006-08-30
Only one drive can be the root drive. The mount point for the new drive will have to be a different directory on your computer. For example, create a folder in the root directory called "storage" and then the mount point for your new partition could be "/storage".

---

### Post by edoggydogg on 2006-08-30
Hmm, I tried that but it won't change the access point. It stays as "/". Maybe I need to do something else to change that?

---

### Post by cleentrax on 2006-08-30
I find it easier to use the command line for disk work. Use ```
sudo fdisk -l
```

to tell you what your partitions are called (i.e. hda1 and hda2).

If your second partition is hda2, then do:

```
sudo umount hda2
```

and then:

```
sudo mount hda2 /storage
``` (assuming that you have already created a folder called /storage)

Careful that you don't unmount your main partition! And you may need to reboot to see changes take effect. You may also need to add a line to your /etc/fstab file, so that the new partition is automatically mounted each time you boot.

---

### Post by cleentrax on 2006-08-30
Lots more good info here:

[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by edoggydogg on 2006-08-30
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3852    30941158+  83  Linux
/dev/sda2            4071       19457   123596077+  83  Linux
/dev/sda3            3853        4070     1751085   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601    7  HPFS/NTFS
enmar@enmar-desktop:~$ sudo umount hda2
umount: hda2: not found
enmar@enmar-desktop:~$ sudo umount sda2
umount: sda2: not found
enmar@enmar-desktop:~$ sudo umount sda2
umount: sda2: not found


Hmm, I think maybe I did something wrong earlier when I was trying to format it.

---

### Post by edoggydogg on 2006-08-30
Cleentrax, thanks for the help! That guide did the trick. :)

---

