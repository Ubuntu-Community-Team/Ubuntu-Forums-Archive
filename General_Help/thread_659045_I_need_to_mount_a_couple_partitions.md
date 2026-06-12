---
title: "I need to mount a couple partitions"
date: 2008-01-05
forum: General Help
---

### Post by onesojourner on 2008-01-05
I have 2 ext3 partitions I need to mount. The first is 
/dev/sdb4            8970       60801   416340540    5  Extended
and
/dev/sda1               1       19457   156288321   83  Linux


I have created the directories in media 
sudo mkdir /media/storage
sudo mkdir /media/storage2

I just need them to be mounted on start up and I need all users to be able to read and write from them.

---

### Post by taurus on 2008-01-05
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by onesojourner on 2008-01-05
peter@desktop:~$ sudo fdisk -l
[sudo] password for peter:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7cdb0844

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1959    15728640   af  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2            1959        5145    25598541    7  HPFS/NTFS
/dev/sda3            5146        8969    30716280   83  Linux
/dev/sda4            8970       60801   416340540    5  Extended
/dev/sda5           60550       60801     2024190   82  Linux swap / Solaris
/dev/sda6            8970       60548   414308254+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf46fb588

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux
peter@desktop:~$ 

AND

peter@desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ab26c842-3ae2-45ec-8201-edb57d500bdf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=ae84b8f7-abc1-44d0-af68-89f5cabfa7f2 /storage        ext3    defaults        0       2
# /dev/sdb1
UUID=17c6186e-affe-4fdd-a865-1f0ef6ac7158 /storage2       ext3    defaults        0       2
# /dev/sda2
UUID=F8147EE1147EA274 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=66f45ef6-a647-4ff5-9d46-06376694dbd6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
peter@desktop:~$

---

### Post by taurus on 2008-01-05
/dev/sda1 is an unknown partition so not sure how you get an ext3 from it.

```
/dev/sda1 * 1 1959 15728640 af Unknown
```

/dev/sda4 is an extended partition and you cannot mount extended partition.  The reason you have an extended partition is because you can only have four primary partitions.  If you need more than four partitions, you need to make one of those primary partitions into extended partition and then you can create more partitions, logical partitions, under that extended partition.

---

### Post by onesojourner on 2008-01-05
I meant sdb1 not sda1. sda1 is my leopard install. I need to mount sdb1. I had to creat 5 partitions for the swap partition. Could I move my swap over to my second drive and then mount my 4th partition on my big drive?

---

### Post by taurus on 2008-01-05
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   1
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```
Now, if you want to have a write permission to /media/sdb1, you need to change the ownership of /media/sdb1 from root to your login name, _assuming_ your login name is **journer**.

```
sudo chown -R **journer**:j**ourner** /media/sdb1
ls -la /media
```

---

### Post by onesojourner on 2008-01-05
I ran into a problem

peter@desktop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by taurus on 2008-01-05
What filesystem did you create/format for /dev/sdb1?  Is it really ext3?  Look at the output of this command to see if it's stated at all.

```
dmesg | tail
```

---

### Post by onesojourner on 2008-01-05
gparted lists it as ext3.

peter@desktop:~$ dmesg | tail
[ 9926.367190] end_request: I/O error, dev fd0, sector 0
[ 9926.367196] Buffer I/O error on device fd0, logical block 0
[ 9938.503560] end_request: I/O error, dev fd0, sector 0
[ 9938.503565] Buffer I/O error on device fd0, logical block 0
[ 9950.632084] end_request: I/O error, dev fd0, sector 0
[ 9950.632089] Buffer I/O error on device fd0, logical block 0
[ 9962.768473] end_request: I/O error, dev fd0, sector 0
[ 9962.768478] Buffer I/O error on device fd0, logical block 0
[ 9974.897018] end_request: I/O error, dev fd0, sector 0
[ 9974.897023] Buffer I/O error on device fd0, logical block 0

---

### Post by taurus on 2008-01-05
Is there anything on /dev/sdb1?  Maybe you can reformat it to ext3 again from a terminal with

```
sudo mke2fs -j /dev/sdb1
sudo mount -a
df -h
```

---

### Post by onesojourner on 2008-01-06
alright I think I have most of this worked out. I have moved my swap partition to the other drive. I deleted the extended partitions on the end of the 500 gig drive and created one primary partition. The partition is at sda4 I would like it so show up in my file browser/desktop as "storage" and I woudl like to have read write access. I tried to modify the the codes you gave me to get it mounted but I am not sure what they are all doing. I have it formatted as ext3.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1959    15728640   af  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2            1959        5145    25598541    7  HPFS/NTFS
/dev/sda3            5146        8969    30716280   83  Linux
/dev/sda4            8970       60801   416340540   83  Linux

---

### Post by taurus on 2008-01-06
Didn't we just go through this with /dev/sdb1 not that long ago?

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda4   /media/storage   ext3   defaults   0   1
```
Save it and close gedit.  Then, create a new mount point and mount it.

```
sudo mkdir /media/storage
sudo mount -a
df -h
```
Now, if you want to write to it, you need to change the ownership of /media/storage, _assuming_ your login name is **journer** again.

```
sudo chown -R **journer**:**journer** /media/storage
ls -la /media
```

---

### Post by onesojourner on 2008-01-06
yep I think I missed something along the way though. 
here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ab26c842-3ae2-45ec-8201-edb57d500bdf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=ae84b8f7-abc1-44d0-af68-89f5cabfa7f2 /storage        ext3    defaults        0       2
# /dev/sdb1
UUID=17c6186e-affe-4fdd-a865-1f0ef6ac7158 /storage2       ext3    defaults        0       2
# /dev/sda2
UUID=F8147EE1147EA274 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=143f8abc-1825-48a8-9c07-25398d4febda none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb2   /media/storage2   ext3   defaults   0   1
/dev/sda4   /media/storage   ext3   defaults   0   1


and It is telling me sda4 does not exist

 sudo mount -a
mount: special device /dev/disk/by-uuid/ae84b8f7-abc1-44d0-af68-89f5cabfa7f2 does not exist
mount: special device /dev/disk/by-uuid/17c6186e-affe-4fdd-a865-1f0ef6ac7158 does not exist
mount: /dev/sdb2 already mounted or /media/storage2 busy
mount: special device /dev/sda4 does not exist
peter@desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb3              29G  3.8G   24G  14% /
varrun               1014M   88K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M  524K 1013M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   24M  990M   3% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb2              25G  3.1G   22G  13% /windows

---

### Post by taurus on 2008-01-06
First, you don't have /dev/sda6 but somehow you have an entry in /etc/fstab to mount it to /storage!

Also, do you have /dev/sdb2 since you try to mount it to /storage2 and apparently, didn't work?

Can you post the output of this command?

```
sudo fdisk -l
```

---

### Post by onesojourner on 2008-01-06
no storage2 is not mounted. I can see the drive in my media file but I have to right click to mount it and it comes up as disk when I do it that way.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf46fb588

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         255     2048256   82  Linux swap / Solaris
/dev/sda2             256       19457   154240065   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7cdb0844

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1959    15728640   af  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb2            1959        5145    25598541    7  HPFS/NTFS
/dev/sdb3            5146        8969    30716280   83  Linux
/dev/sdb4            8970       60801   416340540   83  Linux

---

### Post by taurus on 2008-01-06
Can you also post

```
free
ls -la /dev/disk/by-uuid
```

Somehow, your harddrives switch around!  What used to be /dev/sda is now /dev/sdb.

---

### Post by onesojourner on 2008-01-06
peter@desktop:~$ ls -la /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 160 2008-01-06 10:52 .
drwxr-xr-x 6 root root 120 2008-01-06 10:52 ..
lrwxrwxrwx 1 root root  10 2008-01-06 04:32 143f8abc-1825-48a8-9c07-25398d4febda -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-01-06 04:32 ab26c842-3ae2-45ec-8201-edb57d500bdf -> ../../sdb3
lrwxrwxrwx 1 root root  10 2008-01-06 10:52 b7537a17-e444-412c-9a75-f80bb694031e -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-01-06 10:52 cf98be12-747e-4551-bffd-a2dc035808a8 -> ../../sdb4
lrwxrwxrwx 1 root root  10 2008-01-06 10:52 DDDA16CAA3B34BA5 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-01-06 04:32 F8147EE1147EA274 -> ../../sdb2

---

### Post by taurus on 2008-01-06
You need to modify your /etc/fstab big time.

First, you have to remove these entries since they don't exist or wrong.

```
UUID=ae84b8f7-abc1-44d0-af68-89f5cabfa7f2 /storage ext3 defaults 0 2
UUID=17c6186e-affe-4fdd-a865-1f0ef6ac7158 /storage2 ext3 defaults 0 2
/dev/sdb2 /media/storage2 ext3 defaults 0 1
/dev/sda4 /media/storage ext3 defaults 0 1
```

Now, you need to add these in at the end.

```
UUID=cf98be12-747e-4551-bffd-a2dc035808a8     /storage   ext3   defaults   0   2
UUID=b7537a17-e444-412c-9a75-f80bb694031e   /storages   ext3   defaults   0   2
```
See what happens when you try to mount them again.

```
sudo mount -a
df -h
```

---

### Post by onesojourner on 2008-01-06
alright that worked. they are both mounted as storage and storage2.
Will those both be mounted on start up from now on?

I ran sudo chown -R peter:peter /media/storage
but I still do not have write access. Would that require a restart?

---

### Post by taurus on 2008-01-06
> **onesojourner said:**
> alright that worked. they are both mounted as storage and storage2.
Will those both be mounted on start up from now on?

Yes, they are mounted automatically each time you boot.  That's why you added them to /etc/fstab.

> I ran sudo chown -R peter:peter /media/storage
but I still do not have write access. Would that require a restart?

Sorry to disappoint you but they are not mounted to /media.  Both are mounted to /storage & /storage2 since that was what you intended to do initially.  So, try

```
sudo chown -R peter:peter /storage
sudo chown -R peter:peter /storage2
ls -la /storage
ls -la /storage2
```

---

### Post by onesojourner on 2008-01-06
ok I have write access to storage. storage 2 was being funny but I have it working now. Thank you so much for all your help. Sorry to be such a pain on this one.

---

### Post by onesojourner on 2008-01-07
I rebooted today and all my partitions are missing again. Any idea why?

---

### Post by taurus on 2008-01-08
Can you post the outputs of these commands again?

```
sudo fdisk -l
cat /etc/fstab
df -h
ls -la /dev/disk/by-uuid
```

---

### Post by onesojourner on 2008-01-08
```
sudo fdisk -l
[sudo] password for peter:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf46fb588

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         255     2048256   82  Linux swap / Solaris
/dev/sda2             256       19457   154240065   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7cdb0844

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1959    15728640   af  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb2   *        1959        5145    25598541    7  HPFS/NTFS
/dev/sdb3            5146        8969    30716280   83  Linux
/dev/sdb4            8970       60801   416340540   83  Linux
```

```
peter@desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ab26c842-3ae2-45ec-8201-edb57d500bdf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=F8147EE1147EA274 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=143f8abc-1825-48a8-9c07-25398d4febda none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
UUID=cf98be12-747e-4551-bffd-a2dc035808a8     /storage   ext3   defaults   0   2
UUID=b7537a17-e444-412c-9a75-f80bb694031e   /storage2   ext3   defaults   0   2


```

```
peter@desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb3              29G  4.8G   23G  18% /
varrun               1014M   96K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M  120K 1013M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   24M  990M   3% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb2              25G   12G   13G  48% /windows
/dev/sdb4             391G   46G  326G  13% /storage
/dev/sda2             145G  4.5G  133G   4% /storage2

```

```

peter@desktop:~$ ls -la /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 160 2008-01-08 11:00 .
drwxr-xr-x 6 root root 120 2008-01-08 11:00 ..
lrwxrwxrwx 1 root root  10 2008-01-08 04:50 143f8abc-1825-48a8-9c07-25398d4febda -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-01-08 04:50 ab26c842-3ae2-45ec-8201-edb57d500bdf -> ../../sdb3
lrwxrwxrwx 1 root root  10 2008-01-08 04:50 b7537a17-e444-412c-9a75-f80bb694031e -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-01-08 04:50 cf98be12-747e-4551-bffd-a2dc035808a8 -> ../../sdb4
lrwxrwxrwx 1 root root  10 2008-01-08 11:00 DDDA16CAA3B34BA5 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-01-08 04:50 F8147EE1147EA274 -> ../../sdb2


```

---

### Post by taurus on 2008-01-08
> 
ilesystem            Size  Used Avail Use% Mounted on
/dev/sdb3              29G  4.8G   23G  18% /
varrun               1014M   96K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M  120K 1013M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   24M  990M   3% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb2              25G   12G   13G  48% /windows
[B][COLOR="Blue"]/dev/sdb4             391G   46G  326G  13% /storage
/dev/sda2             145G  4.5G  133G   4% /storage2[/COLOR][/B]


Are you talking about /storage & /storage2 because they are both there.

---

### Post by onesojourner on 2008-01-09
I am not sure where they are being displayed then.

---

### Post by taurus on 2008-01-09
```
ls -la /storage
ls -la /storage2
```

Do you actually want icons for those two drives on your desktop?

---

### Post by onesojourner on 2008-01-09
yeah, For example when a flash drive is mounted. It would even be fine if they stayed in the media folder. I just need and easy one click access to them.

---

### Post by taurus on 2008-01-09
Again, if you want icons on your desktop for those two partitions, you need to mount them to /media.  So, why don't you edit /etc/fstab and modify those two entries so they would look something like these now.

```

UUID=cf98be12-747e-4551-bffd-a2dc035808a8     /media/storage   ext3   defaults   0   2
UUID=b7537a17-e444-412c-9a75-f80bb694031e   /media/storage2   ext3   defaults   0   2

```
Save it.  Now, you need to create two new mount points for them.

```
sudo mkdir /media/storage /media/storage2
```
Reboot. 

You should see those two partitions now mounted to /media.  

```
df -h
```
Of course, you want to be able to write to them so you need to change the ownership of those two mount points from root to your login name, peter.

```
sudo chown -R peter:peter /media/storage
sudo chown -R peter:peter /media/storage2
```

---

### Post by onesojourner on 2008-01-09
Alright that worked great. thanks again.

---

