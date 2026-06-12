---
title: "trying to view contents of a harddrive."
date: 2007-04-25
forum: General Help
---

### Post by endo666 on 2007-04-25
im trying to view a ntfs hard disk that is hooked to my computer but when i try i get this.

error: device /dev/sdc5 is not removable

error: could not execute pmount

so what do i need to do?

---

### Post by taurus on 2007-04-25
You have to mount it first.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by endo666 on 2007-04-25
i have tried everything and i still cant get into the harddrive

---

### Post by endo666 on 2007-04-25
hello can anyone offer me some advice.

---

### Post by taurus on 2007-04-25
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by endo666 on 2007-04-25
Disk /dev/sda: 150.0 GB, 150038863360 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18240   146512768+   7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14338   115169953+  83  Linux
/dev/sdb2           14339       14946     4883760    5  Extended
/dev/sdb5           14339       14946     4883728+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdc5               2       60801   488375968+   7  HPFS/NTFS


and its the last hard drive i need to mount

---

### Post by taurus on 2007-04-25
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdc5   /media/sdc5   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sdc5
sudo mount -a
df -h
```

---

### Post by endo666 on 2007-04-25
ok this is what i did

endo@endo:~$ sudo mkdir /media/sdc5
mkdir: cannot create directory `/media/sdc5': File exists
endo@endo:~$ sudo mount -a
mount: mount point /media/windows does not exist
mount: /dev/sdc5 already mounted or /media/sdc5 busy
mount: according to mtab, /dev/sdc5 is mounted on /tmp/disks-conf-sdc5
endo@endo:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             109G  2.5G  101G   3% /
varrun               1006M   80K 1006M   1% /var/run
varlock              1006M  4.0K 1006M   1% /var/lock
udev                 1006M  180K 1006M   1% /dev
devshm               1006M     0 1006M   0% /dev/shm
lrm                  1006M   22M  985M   3% /lib/modules/2.6.15-28-amd64-generic/volatile
/dev/sda1             140G   61G   79G  44% /tmp/disks-conf-sda1
/dev/sdc5             466G   82G  385G  18% /tmp/disks-conf-sdc5

now i get this error
You do not have the permissions necessary to view the contents of "disks-conf-sdc5".

---

### Post by taurus on 2007-04-25
Can you post your /etc/fstab?

```
cat /etc/fstab
```

p.s.  Your /dev/sdc5 is already mounted to /tmp/disks-conf-sdc5.

---

### Post by endo666 on 2007-04-25
is this what you wanted

endo@endo:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
[SIZE="4"]/dev/sdb5       /media/windows  ntfs    umask=0222             0       0[/SIZE]
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdc5   /media/sdc5   ntfs   nls=utf8,umask=0222   0   0

it is the big one that i have on the list that is the problem rite

---

### Post by taurus on 2007-04-25
> **endo666 said:**
> is this what you wanted

endo@endo:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
[SIZE="4"]/dev/sdb5       /media/windows  ntfs    umask=0222             0       0[/SIZE]
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdc5   /media/sdc5   ntfs   nls=utf8,umask=0222   0   0

it is the big one that i have on the list that is the problem rite

I think you screw up your /etc/fstab.  /dev/sdb5 is your swap, NOT ntfs.  Therefore, you need to edit /etc/fstab and change it back to 

```
/dev/sdb5   none   swap   sw   0   0
```
Then, run

```
sudo umount /dev/sdc5
sudo mount -a
free
df -h
```

---

### Post by endo666 on 2007-04-26
ok i just installed ubuntu 7 and i can now see my hard drive but i cant save to it or if i edit documents i cant save the changes.

---

### Post by taurus on 2007-04-26
If you want to write to ntfs, you need to use ntfs-3g driver.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by endo666 on 2007-04-26
ok i tried what they did in that link and still nothing. i know you are probably getting tired of helping me but any other advice.

---

### Post by taurus on 2007-04-26
Can you post your /etc/fstab again?

```
cat /etc/fstab
```

---

### Post by endo666 on 2007-04-26
i didnt change anything in here except i added the last one to try to get things set up my self

endo@endo-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=eb44396f-5bdc-4148-b186-168722038138 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=9db9faa3-1352-4a01-8931-ec7f5d9365f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/[SIZE="4"]dev/sdc5    /media/windows    ntfs-3g     defaults,locale=en_US.utf8   0    0
[/SIZE]

---

### Post by endo666 on 2007-04-26
well thankyou for all the help but everything seams to be working now. just wish i knew what i did.

---

