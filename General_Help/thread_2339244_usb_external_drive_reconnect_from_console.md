---
title: "usb external drive reconnect from console"
date: 2016-10-06
forum: General Help
---

### Post by marchello_lippi2 on 2016-10-06
Hi all,

My need is to reconnect my usb external drive from console. 
For unknown reason it disappears from time to time (rarely) and restores after system reboot.
I'd like to know how do I restore it without need to reboot. 
Please tell me what additional details should I provide (if any).
Please advise.

---

### Post by ajgreeny on 2016-10-06
Is this USB disk included in and mounted by a line in your /etc/fstab file?

It sounds as if it may be, as a USB disk would not normally mount on boot or when you reboot.

Let's see the output of ```
cat /etc/fstab && echo mount && mount
``` in terminal.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**.  That will show us what should be mounted and what actually is mounted, and if run when the USB has unmounted itself may show us what has unmounted, though admittedly, not why.

If the disk is shown in your fstab file you should be able to remount it with command ```
sudo mount -a
```

---

### Post by marchello_lippi2 on 2016-10-07
```
$ sudo cat /etc/fstab && echo mount && mount
[sudo] password for user1: 
proc            /proc           proc    defaults          0       0
/dev/mmcblk0p5  /boot           vfat    defaults          0       2
/dev/mmcblk0p6  /               ext4    defaults,noatime  0       1
/dev/sda1       /mnt/wd         ntfs    defaults          0       0
/dev/sdb1       /mnt/wd1        ntfs    defaults          0       0
# a swapfile is not a swap partition, so no using swapon|off from here on, use  dphys-swapfile swap[on|off]  for that
mount
/dev/root on / type ext4 (rw,noatime,data=ordered)
devtmpfs on /dev type devtmpfs (rw,relatime,size=218416k,nr_inodes=54604,mode=755)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=44540k,mode=755)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /run/shm type tmpfs (rw,nosuid,nodev,noexec,relatime,size=89060k)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
/dev/mmcblk0p5 on /boot type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=ascii,shortname=mixed,errors=remount-ro)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda1 on /mnt/wd type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)

```

---

### Post by marchello_lippi2 on 2016-10-07
ok, I've commented **/dev/sdb1** in my **/etc/fstab** as it does not exist at a moment. 
Now **sudo mount -a** performed without any error / warning. 
The question is that sometimes system doesn't see my /dev/sda1, though it is plugged in. 
But I can't reproduce it by myself, will wait for this to happen and then will try to catch all details and post here. 
Thanks for now.

---

### Post by ajgreeny on 2016-10-07
I presumed sdb1 was your USB disk, but you now say it doesn't exist and the USB is sda1.

Normally your internal disk would be sda but you say that is the USB so I am confused.

Can you show us the output of ```
sudo parted -l
``` please which may confirm things for me a bit.

Incidentally it is much better to use **UUIDs** in the fstab file, not **dev/sdX** style nomenclature as the latter can change when other USB disks are attached and can totally confuse the system.

---

### Post by marchello_lippi2 on 2016-10-08
Today I can see this error and would like to fight it. I'm sorry, I did not say it is my raspberry pi, so the file system is organized in other way. 
Normally I can see the content on /mnt/wd folder, but today I can see only 

```
$ ls /mnt/wd
ls: reading folder /mnt/wd: Input/output error
```

```
$ df -h
File system      Size   Used  Available Use% mouned on
/dev/root       2,4G  1,4G  889M  61% /
devtmpfs        214M     0  214M   0% /dev
tmpfs            44M  516K   43M   2% /run
tmpfs           5,0M     0  5,0M   0% /run/lock
tmpfs            87M     0   87M   0% /run/shm
/dev/mmcblk0p5   60M   20M   41M  33% /boot
/dev/sda1       299G  268G   31G  90% /mnt/wd
```

```

$ sudo parted -l
Model: WD 3200BEV External (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  320GB  320GB  primary  ntfs


Model: SD SU04G (sd/mmc)
Disk /dev/mmcblk0: 3965MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  1275MB  1274MB  primary   fat32        lba
 2      1275MB  3932MB  2657MB  extended
 5      1279MB  1342MB  62,9MB  logical   fat16        lba
 6      1346MB  3931MB  2585MB  logical   ext4
 3      3932MB  3965MB  33,6MB  primary   ext4

```

Will try to google how to reset my usb and will update here.

---

### Post by colmax on 2016-10-08
Raspberry Pi
Wow that's a computer on a memstik which encourages programming
Do you find it very capable
Cheers

---

### Post by sudodus on 2016-10-08
I support ajgreeny's advice to use UUID instead of block device (/dev/sdxy) to identify your external drive, when you mount it (in /etc/fstab and manually with the mount command)

You can find the UUID with the following commands (use the one that you like best),

```
sudo blkid

sudo lsblk -fm  # in a wide terminal window
```

Example: I use the following line in /etc/fstab to connect an external drive

```
UUID=5ece9189-9a89-4076-a7ae-381890f4e3f6  /media/E1    ext4    defaults,noauto 0       0
```

noauto means that it does not mount at boot, but it is identified, and I can mount it easily by

```
sudo mount /media/E1
```

Some people prefer to use a mountpoint in the /mnt directory, when it is not automounted. In both cases you must create the mountpoint, so either

```
sudo mkdir /media/E1
# or
sudo mkdir/mnt/E1
```

and in the latter case this line in /etc/fstab

```
UUID=5ece9189-9a89-4076-a7ae-381890f4e3f6  /mnt/E1    ext4    defaults,noauto 0       0
```

and mount with this command line:

```
sudo mount /mnt/E1
```

-o-

***If you 'unmount' with the umount command, the drive will be connected and available for mounting again,***

```
sudo umount /mnt/E1
```

***but if you 'eject' it from a file browser, it will be turned off and no longer available for mounting.*** In this case you must either unplug it and plug it back again, or reboot the computer. But check very carefully, that no partition on the drive is mounted before you unplug it. You can use the df command for that purpose:

```
df
```

---

### Post by marchello_lippi2 on 2016-10-09
> **colmax said:**
> Raspberry Pi
Wow that's a computer on a memstik which encourages programming
Do you find it very capable
Cheers

It is great for my tasks, these are syncthing, transmission, samba. Well, it could work faster probably if I format my external hdd as ext4 filesystem. Also I bought it like 4 years ago and it is possible to buy faster sd card. But it is still great small pc.

---

