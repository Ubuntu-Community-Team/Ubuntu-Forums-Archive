---
title: "Read Only"
date: 2007-12-29
forum: General Help
---

### Post by ThomasWii on 2007-12-29
Hi, i have a micro sd card and a thing that can read it, i was trying to copy a file and its read only, and then i found the whole disk (sd) was read only, is there a bit of code or something that can make it so i can remove the read only?

Thanks in advance,

Thomas.

---

### Post by taurus on 2007-12-29
Can you post the outputs of these commands from a terminal?  Changes are you need to remount it with the right permissions.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by ThomasWii on 2007-12-29
1st:```
Disk /dev/sdb: 2013 MB, 2013265920 bytes
16 heads, 15 sectors/track, 16384 cylinders
Units = cylinders of 240 * 512 = 122880 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       16384     1965952+   6  FAT16

```

2nd: ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              17G  4.8G   11G  31% /
varrun                347M  228K  347M   1% /var/run
varlock               347M     0  347M   0% /var/lock
udev                  347M   80K  347M   1% /dev
devshm                347M     0  347M   0% /dev/shm
lrm                   347M   34M  313M  10% /lib/modules/2.6.22-14-generic/volatile
/dev/hdc               69M   69M     0 100% /media/cdrom0
/dev/sdb1             1.9G  112M  1.8G   6% /media/disk

```

Should i make a backup?

---

### Post by taurus on 2007-12-29
Try

```
sudo umount /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
ls -la /media
```
Now, see if you can write to /media/sdb1.

---

### Post by ThomasWii on 2007-12-29
```
thomas@thomas-laptop:~$ sudo umount /dev/sdb1
[sudo] password for thomas:
thomas@thomas-laptop:~$ sudo mkdir /dev/sdb1
mkdir: cannot create directory `/dev/sdb1': File exists
thomas@thomas-laptop:~$ sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
mount: mount point /media/sdb1 does not exist
thomas@thomas-laptop:~$ ls -la /media
total 10
drwxr-xr-x  3 root root 4096 2007-12-29 18:24 .
drwxr-xr-x 21 root root 4096 2007-12-28 21:00 ..
lrwxrwxrwx  1 root root    6 2007-12-14 19:30 cdrom -> cdrom0
dr-xr-xr-x  1 root root 2048 2007-07-31 10:01 cdrom0
-rw-r--r--  1 root root    0 2007-12-29 18:24 .hal-mtab
-rw-------  1 root root    0 2007-12-29 16:31 .hal-mtab-lock
thomas@thomas-laptop:~$ 




```

---

### Post by taurus on 2007-12-29
Sorry, it's

```
sudo mkdir /media/sdb1
```

---

### Post by ThomasWii on 2007-12-29
nope still comes up with You do not have permissions to write to this folder.

---

### Post by ThomasWii on 2007-12-30
Bump

---

