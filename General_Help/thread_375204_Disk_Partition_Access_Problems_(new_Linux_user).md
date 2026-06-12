---
title: "Disk Partition Access Problems (new Linux user)"
date: 2007-03-03
forum: General Help
---

### Post by thorner on 2007-03-03
Hi.
Props to everyone here! I am new to Linux as of Nov'06, and Ubuntu along with this forum has helped make my transition from windows very smooth. Thanks again!

This far, I have always been able to do a search, and find a solution to my problem. Unfortunetly, I cant find any information regarding my current situation. So this has become my first request for help.....
___________________________________________________

When I first installed Ubuntu, I decided to make a partition (65GB) for music, videos, pictures, etc. It became hda6, and I mounted it on /media. However, I have never been able to use it. Access is denied for everything. I have tried changing permissions,  using 'gksudo nautilus' and even tried re-formating. None worked. It wont even let me un-mount it or change the mount path. 
Another odd detail; it claims to be empty, but there is about 4.5GB of space "missing" according to Disks Manager.

Partition Properties
Device:---------- /dev/hda6
Filesystem:------ Extended 3 (ext3)
Access Path:---- /media/hda6     *which it won't let me change*
Size:------------- 65.60GiB (61.17GiB Free)
Status:----------- Accessible

fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda6       /media/hda6     ext3    defaults        0       2
/dev/hda7       /usr            ext3    defaults        0       2
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```


System:

Ubuntu Dapper64 - Linux 2.6.15-28-amd64-generic
Athlon64 3000+  2.05GHz
1GB RAM
nVidia FX5500 128MB

Any help is greatly appreciated!
Cheers

---

### Post by taurus on 2007-03-03
What's the output of this command from a terminal?

```
sudo fdisk -l
```
And what's up with all those --------------------?

---

### Post by thorner on 2007-03-03
```

Disk /dev/hda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          13      104391   83  Linux
/dev/hda2              14        1145     9092790   83  Linux
/dev/hda3            1538       20023   148488795    f  W95 Ext'd (LBA)
/dev/hda4            1146        1537     3148740   82  Linux swap / Solaris
/dev/hda5            1538       10676    73408986   83  Linux
/dev/hda6           11460       20023    68790298+  83  Linux
/dev/hda7           10677       11459     6289416   83  Linux

Partition table entries are not in disk order

```

---

### Post by taurus on 2007-03-03
And

```
df -h
```

---

### Post by thorner on 2007-03-03
(I figured out the spacing....)

[HTML]Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             8.6G  908M  7.3G  11% /
varrun                503M  100K  503M   1% /var/run
varlock               503M     0  503M   0% /var/lock
udev                  503M  128K  503M   1% /dev
devshm                503M     0  503M   0% /dev/shm
lrm                   503M  8.1M  495M   2% /lib/modules/2.6.15-28-amd64-generic/volatile
/dev/hda1              96M   24M   68M  26% /boot
/dev/hda5              69G   14G   52G  21% /home
/dev/hda7             6.0G  2.8G  2.9G  50% /usr
/dev/hda6              65G  129M   62G   1% /media/hda6[/HTML]

---

### Post by taurus on 2007-03-03
What's the output of this command from a terminal?

```
ls -la /media/hda6
```

---

### Post by thorner on 2007-03-03
Output of: ls -la /media/hda6
```
 
total 12
drwxr-xr-x 3 root root 4096 2007-03-03 10:07 .
drwxr-xr-x 5 root root 4096 2007-03-03 09:26 ..
drwx------ 3 root root 4096 2007-03-03 10:07 .Trash-root

```

---

### Post by taurus on 2007-03-03
```
sudo ls -la /media/hda6/.Trash-root
-or-
sudo du -h /media/hda6
```

---

### Post by thorner on 2007-03-03
Output from: sudo ls -la /media/hda6/.Trash-root
```
total 24
drwx------ 3 root root  4096 2007-03-03 10:07 .
drwxr-xr-x 3 root root  4096 2007-03-03 10:07 ..
drwx------ 2 root root 16384 2007-03-03 09:59 lost+found

```

Output from: sudo du -h /media/hda6
```
16K     /media/hda6/.Trash-root/lost+found
20K     /media/hda6/.Trash-root
24K     /media/hda6

```

---

### Post by taurus on 2007-03-03
So, basically there is nothing on /dev/hda6 at this moment.  The drive is clean.

---

### Post by thorner on 2007-03-03
Thats what I concluded too.
However, I'm curious why Disks Manager Shows almost 4.5GB of this partition as being used.
(ps. I still can't place any thing in this partition)

---

### Post by taurus on 2007-03-03
The reason is that /dev/hda6 uses ext3 filesystem which the system will reserve 5% of the total space for root in case you fill up the drive/partition.

And if you want to be able to write to it, then you need to change the ownership of /media/hda6 to your username.  Assuming your username is **thorner**, do

```
sudo chown **thorner**:**thorner** /media/hda6
ls -la /media/hda6
```

---

### Post by thorner on 2007-03-03
STELLAR!

Props dude. I can write to that partition now. And I now understand why there is 4.5GB of disk space missing.

Thanks again.

Cheers.

(ps. before I load this partition with music/videos, in your opinion is ext3 the best filesystem for this type of media? )

---

### Post by taurus on 2007-03-03
Since you don't have any Windows on your AMD64, ext3 is what you should use.  All the partitions on my machines are ext3 and never have any problem with them so far.

In other words, load away...

---

### Post by thorner on 2007-03-03
Thanks again dude.

Have a stellar day.

Cheers.

---

